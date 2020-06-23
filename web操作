# -*- coding: UTF-8 -*-

import time
import os
import sys
from selenium import webdriver
from selenium.common.exceptions import NoAlertPresentException
from selenium.webdriver.common.keys import Keys
import traceback
import codecs
import urllib.request


cur_time = time.strftime('%Y-%m-%d',time.localtime(time.time()))
pic_path = cur_time

chromedriver = r"C:\Users\test\AppData\Local\Google\Chrome\Application"
os.environ["webdriver.ie.driver"] = chromedriver
basepath = sys.path[0]
addlist = basepath+'\\'+'list.csv'
log = open("log_%s.log" %(str(cur_time)),'w')

#p = input("暂停：")




'''
def test():
    try:
        file = codecs.open(basepath+'\\'+'list.csv')
    except FileNotFoundError:
        print("列表文件不存在")
    else:
        contents = file.readlines()
        for i in contents:
            print(i.split('=')[0])
'''

def test1():
    url = "http://%s" %("10.162.154.114:20001")
    opener = urllib.request.build_opener()
    opener.addheaders = [('User-Agent','Mozilla/5.0')]
    try:
        opener.open(url)
        var = "url is ok"
        print(var)
    except urllib.error.HTTPError:
        var = "error"
        print(var)
    except urllib.error.URLError:
        var = "error"
        print(var)
    except urllib.error .ContentTooShortError:
        var = "error"
        print(var)





def mkdir_path():
    if os.access(pic_path,os.F_OK):
        print(basepath+'\\'+pic_path+" ok")
    else:
        os.mkdir(pic_path)

#    p = input("暂停：")

def open_web():
    url = "http://%s/StatisticChart" %(ip)
    
    driver = webdriver.Chrome()
    driver.get(url)
#   driver.maximize_window() #窗口最大化
    
#解决弹窗问题
#
#    try:
#        alert1 = driver.switch_to.alert  #switch_to.alert点击确认alert
#    except NoAlertPresentException as e:
#        print("no alert")
#        traceback.print_exc()
#    else:
#        at_text1 = alert1.text
#        print("at_text:" + at_text1)
#    
#    time.sleep(1)
#    
    
    driver.find_element_by_id('username').click()  #点击输入框
    driver.find_element_by_id('username').clear()  #清空输入框
    driver.find_element_by_id('username').send_keys("%s" %"admin")    #输入用户名
    
    
    driver.find_element_by_id("password").click()  #点击输入框
    driver.find_element_by_id("password").clear()  #清空输入框
    driver.find_element_by_id("password").send_keys("%s" %"123")    #输入用户名
    
    driver.find_element_by_class_name("pure-button").click()

    driver.get(url)
    time.sleep(2)
    driver.find_element_by_class_name("el-button--default").click()
    time.sleep(1)
    #opencity = driver.find_element_by_xpath('//*[@valuekey="value" and @placeholder="请输入城市"]')

    try:
        opencity = driver.find_element_by_xpath('//*[@valuekey="value" and @placeholder="请输入城市"]')
    except NoSuchElementException:
        print(opencity)
        driver.find_element_by_xpath('//*[@valuekey="value" and @placeholder="请输入城市"]').send_keys("%s" %city)
    #driver.find_element_by_xpath('//*[@valuekey="value" and @placeholder="请输入城市"]').send_keys(Keys.ENTER)
    time.sleep(2)
    driver.find_element_by_class_name("el-autocomplete-suggestion__list").click()
    #p = input("pause")
    time.sleep(2)
	
    pic_shot = driver.get_screenshot_as_file(pic_path+r"\%s.jpg" %(city))
    print(city+"_"+ip,file=log)
    print("%s:截图OK" %(pic_shot),file=log)
    if pic_shot=="False":
        pic_shot = driver.get_screenshot_as_file(pic_path+r"\%s.jpg" %(city))
        print(city+"_"+ip,file=log)
        print("%s:截图OK" %(pic_shot),file=log)

        
    driver.quit()



if __name__ == "__main__":
#    test1()
    

    mkdir_path()
    try:
        file = codecs.open(addlist)
    except FileNotFoundError:
        print("列表文件不存在",file=log)
    else:
        contents = file.readlines()
        for i in contents:
            city = str(i.split('=')[0])
            ip = str(i.split('=')[1])
            user = str(i.split('=')[2])
            password = str(i.split('=')[3])

            url = "http://%s" %(ip)
            opener = urllib.request.build_opener()
            opener.addheaders = [('User-Agent','Mozilla/5.0')]
            try:
                opener.open(url)
                var = "url is ok"
            except urllib.error.HTTPError:
                var = "error"
            except urllib.error.URLError:
                var = "error"

            if var=="url is ok":
                open_web()
            elif var=="error":
                print("%s:http error" %(ip),file=log)
            

    

