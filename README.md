# orangeHRM
My first repository on Github
package orangeHRM;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;


public class loginAndRecruitment {

	public static void main(String[] args) throws InterruptedException {
		
		WebDriver driver = new ChromeDriver();
		
		driver.get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");
		driver.manage().window().maximize();
		
		Thread.sleep(5000); 
		
		WebElement userName = driver.findElement(By.name("username"));
		userName.sendKeys("Admin");
		WebElement password = driver.findElement(By.name("password"));
		password.sendKeys("admin123");
		WebElement loginButton = driver.findElement(By.xpath("//button[@type='submit']"));
		loginButton.click();
		
		Thread.sleep(3000);
		String actualUrl = driver.getCurrentUrl();
		String expectedUrl = "https://opensource-demo.orangehrmlive.com/web/index.php/dashboard/index";
		if(actualUrl.equals(expectedUrl))
		{
			System.out.println("login success");
		}
		else
		{
			System.out.println("login failed");
		}
		
		
		WebElement recruitmentField = driver.findElement(By.linkText("Recruitment"));
		recruitmentField.click();
		
		Thread.sleep(3000);
		
		WebElement jobTitleDropdown = driver.findElement(By.xpath("//div[@class='oxd-select-text-input']"));
		jobTitleDropdown.click();
		Thread.sleep(3000);
		Actions actionTitle=new Actions(driver);
		for(int i=0;i<=18;i++) {
			actionTitle.sendKeys(Keys.DOWN).perform();
		}
			actionTitle.sendKeys(Keys.ENTER).perform();
	
		System.out.println("Job Title selected");
		
		WebElement vacancyDropdown = driver.findElement(By.xpath("//div[@class='oxd-select-text oxd-select-text--active']"));
		vacancyDropdown.click();
		Thread.sleep(3000);
		Actions actionvacancy=new Actions(driver);
		for(int i=0;i<=7;i++) {
			actionvacancy.sendKeys(Keys.DOWN).perform();
		}
			actionvacancy.sendKeys(Keys.ENTER).perform();
	
		System.out.println("Vacancy selected");
		
		
		WebElement hiringManagerDropdown = driver.findElement(By.xpath("//div[@class='oxd-select-text oxd-select-text--active']"));
		hiringManagerDropdown.click();
		Thread.sleep(3000);
		Actions actionhiring=new Actions(driver);
		for(int i=0;i<=1;i++) {
			actionhiring.sendKeys(Keys.DOWN).perform();
		}
			actionhiring.sendKeys(Keys.ENTER).perform();
	
		System.out.println("Hiring Manager selected");
		
		//driver.quit();
	
		
		

	}

}
