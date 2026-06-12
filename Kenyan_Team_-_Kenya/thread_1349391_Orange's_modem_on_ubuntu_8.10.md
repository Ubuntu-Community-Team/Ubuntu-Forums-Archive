---
title: "Orange's modem on ubuntu 8.10"
date: 2009-12-08
forum: Kenyan Team - Kenya
---

### Post by githugunyi on 2009-12-08
Hey! Huawei eg162g usb modem is not working on ubuntu 8.10.
This is orange's mobile internet (PAP).
Please help.

---

### Post by dmugambi on 2009-12-26
try this article:
[http://www.ideacellular.com/ShowBinary/BEA%20Repository/idea/CorporateUser/GPRSApplicationNetSetterfaq.pdf](http://www.ideacellular.com/ShowBinary/BEA%20Repository/idea/CorporateUser/GPRSApplicationNetSetterfaq.pdf)
It has a small note on something to do with firmware update for your modem.

---

### Post by kensta87 on 2010-05-26
you can also try using pppconfig to configure your modem.. so that it can connect to the web just follow his simple steps and you are good to go..

step 1: go to terminal by applications >accessories>terminal or alt+F2 and type gnome-terminal.

step 2: in the terminal type sudo pppconfig then enter the roots password and then after that the pppconfig dialup utility will appear.
then select create connection . just write something like orange , then select next when it comes to configure nameservers just put dynamic then select OK . another window will appear askin for authentication method just select pap and  then input orange for username and orange for password then speed let it stay at 115200 select OK and then if it tells you to choose between tone and pulse leave at tone and select OK to continue then input the dialup number which is *99# continue untill you see Choose Modem Config Method and selct yes to enter the modem port manual  untill you see  Manually Select Modem port , input /dev/ttyUSB0 then select OK , it will then give a summery of the configuration just select Finished Write Files and return to main menu select it and thats all.
you have now configured orange [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

step 3: after finishing the setup above and exiting pppconfig . now its time to connect just enter this command pon orange <orange is the account name you made > it will just automatically start the dial up process and vowala you connected ,, to monitor the connection progress just input plog
and to disconnect just input poff. Thats all ... enjoy.

---

