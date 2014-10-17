USHE-Auto-test
==============

package appModules;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;

import pageObjects.ApplicationLinks;
import pageObjects.LogIn_Page;
import pageObjects.Product_Creation_Page;
import utility.ExcelUtils;
import utility.Log;

public class ProductCreation_Action {
	
	public String title;
	
	public static void prodCreate(WebDriver driver) throws Exception{
		
			
		Actions action = new Actions(driver);
	    action.moveToElement(ApplicationLinks.link_Store(driver)).click().perform();
	    action.moveToElement(ApplicationLinks.link_Product(driver)).click().perform();
	    action.moveToElement(ApplicationLinks.link_CrtProd(driver)).click().perform();
	    
	    driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
		
	    driver.switchTo().frame(driver.findElement(By.cssSelector("iframe[title='Create Product dialog']")));
		
		String prodTitle = ExcelUtils.getCellData(1, 2);
		Product_Creation_Page.txtbx_ProdTitle(driver).sendKeys(prodTitle);
		
		//driver.switchTo().frame(driver.findElement(By.cssSelector("iframe[title='Rich Text AreaPress ALT-F10 for toolbar. Press ALT-0 for help']")));
				 
//        String prodDesc = ExcelUtils.getCellData(1, 3);
//        Product_Creation_Page.txtbx_ProdDesc(driver).sendKeys(prodDesc);
        
        //driver.switchTo().defaultContent();
        
        String prodSize = ExcelUtils.getCellData(1, 4);
        Select size = new Select(Product_Creation_Page.list_ProdSize(driver)); 
	    size.selectByVisibleText(prodSize);
        
        String prodColor = ExcelUtils.getCellData(1, 5);
        Select color = new Select(Product_Creation_Page.list_ProdColor(driver)); 
	    color.selectByVisibleText(prodColor);
        
        String prodSku = ExcelUtils.getCellData(1, 6);
        Product_Creation_Page.txtbx_ProdSKu(driver).sendKeys(prodSku);
        
        String prodPrice = ExcelUtils.getCellData(1, 7);
        Product_Creation_Page.txtbx_ProdPrice(driver).sendKeys(prodPrice);
        
//        String prodImage = ExcelUtils.getCellData(1, 8);
//        Product_Creation_Page.txtbx_Prodimage(driver).sendKeys(prodImage);
//        
//        Product_Creation_Page.btn_Save(driver).click();
//        
//        driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
//        
//        String prodCateg = ExcelUtils.getCellData(1, 9);
//        Select categ = new Select(Product_Creation_Page.list_ProdCateg(driver)); 
//        categ.selectByVisibleText(prodCateg);
//        
//        String prodModstatus = ExcelUtils.getCellData(1, 10);
//        Select modstat = new Select(Product_Creation_Page.list_ProdModStatsu(driver)); 
//	    modstat.selectByVisibleText(prodModstatus);
//        
//        String prodLogmes = ExcelUtils.getCellData(1, 11);
//        Product_Creation_Page.txtbx_ProdLogmes(driver).sendKeys(prodLogmes);
//        	    
//	    Product_Creation_Page.btn_Submit(driver).click();
//	        
//	    driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
//	    
//	    driver.switchTo().defaultContent();
       		
		
	}

}
