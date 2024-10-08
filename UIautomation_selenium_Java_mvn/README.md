
<h1>Java Selenium Testing Framework: </h1>
 
This project is a Selenium-based UI testing framework built with Java. It uses TestNG for structuring tests, and Log4j2 for logging. The framework is designed to be robust, scalable, and easy to maintain.

<h2> Project Structure:</h2>

```plaintext
.
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── yourcompany
│   │               └── projectname
│   │                   ├── pages       # Page Object Model (POM) classes representing web pages
│   │                   └── utils       # Utility classes for configuration, WebDriver management, etc.
│   ├── test
│   │   └── java
│   │       └── com
│   │           └── yourcompany
│   │               └── projectname
│   │                   └── tests       # Test classes written using TestNG
├── pom.xml
└── README.md


 ```

pages: Contains the Page Object Model (POM) classes that represent the web pages.

utils: Utility classes, such as those for handling configuration, web driver management, etc.

tests: Contains test classes written using TestNG.

<h2> Prerequisites : </h2>

1.Java 8 or higher

2.Maven 3.6.0 or higher

3.Browser Drivers (e.g., ChromeDriver, GeckoDriver)

<h2> Installation: </h2>

<h4> Clone the repository: </h4>
git clone https://github.com/swatidhoke/UIautomation_selenium_Java_mvn.git

Navigate to the project directory:

cd UIautomation_selenium_Java_mvn

<h2>Install dependencies:</h2>
 
mvn clean install

<h2>Configuration:</h2>  
Logging Configuration
The project uses Log4j2 for logging. The configuration file is located at src/main/resources/log4j2.xml.

**WebDriver Configuration:**
WebDriver binaries (e.g., ChromeDriver) should be placed in the drivers directory or set up using WebDriverManager in the test initialization.

**Test Configuration:**
TestNG configuration is handled by testng.xml, which is located at the root of the project. This file is used to configure test suites, groups, and parallel execution.

Usage
<h2>Running Tests:</h2>
To run the tests, execute the following Maven command:
mvn test

**Generating Reports:**

TestNG generates a default report after the test execution, which can be found in the target/surefire-reports directory.

**Logging:**

Logs are generated by Log4j2 and can be found in the logs directory. The log level, format, and file rotation policies can be configured in the log4j2.xml file.

<h2>Example Test Case</h2>

Below is a simple example of a test case:

java
import org.testng.annotations.Test;
import org.testng.Assert;

public class LoginTest extends BaseTest {

    @Test
    public void testLogin() {
        LoginPage loginPage = new LoginPage(driver);
        HomePage homePage = loginPage.login("username", "password");

        Assert.assertTrue(homePage.isLoggedIn(), "User should be logged in");
    }
}
Page Object Example
 
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;
```
public class LoginPage {

    private WebDriver driver;

    @FindBy(id = "username")
    private WebElement usernameField;

    @FindBy(id = "password")
    private WebElement passwordField;

    @FindBy(id = "loginButton")
    private WebElement loginButton;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    public HomePage login(String username, String password) {
        usernameField.sendKeys(username);
        passwordField.sendKeys(password);
        loginButton.click();
        return new HomePage(driver);
    }
}
```

<h2>Dependencies:</h2>

Key dependencies used in this project:

Selenium WebDriver: For browser automation.

TestNG: For test execution and structuring.

Log4j2: For logging.

Maven: For dependency management and build automation.

These dependencies are defined in the pom.xml file.

<h2>Contributing:</h2>

Fork the repository.

Create a feature branch (git checkout -b feature-branch).

Commit your changes (git commit -am 'Add new feature').

Push to the branch (git push origin feature-branch).

Create a new Pull Request.
