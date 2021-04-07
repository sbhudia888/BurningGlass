# Test Automation boilerplate with BDD and Selenium

## When Test failures, cucumber HTML report not generated

When there is test failure, then cucumber HTMl report will not generate becuause surefire plugin stops the execution and throws error, which is responsible to write cucumber html report.
Basically user can see something like below error 

"Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.19.1:test (default-test) on project burningGlass: There are test failures.
.."

To fix this issue, we should say surefire plugin to ignore when there is a test failure.
update the plugin in pom.xml file as below.

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.19.1</version>
                <configuration>
                    <testFailureIgnore>true</testFailureIgnore>
                    <suiteXmlFiles>
                        <suiteXmlFile>testng.xml</suiteXmlFile>
                    </suiteXmlFiles>
                </configuration>
            </plugin>
