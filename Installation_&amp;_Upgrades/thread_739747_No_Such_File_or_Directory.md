---
title: "No Such File or Directory"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by chandrakant11 on 2008-03-30
Hi I m Ubuntu 7.10 User (Acer Aspire , Turion , 1.5GB Ram) 
I m using broadband Internet connection . I have to logged on the server thru crclient, A executable file. 
When I reinstall Ubuntu 7.10 and try executing this crclient file , I get "No Such File or Directory " Message . Don't know why .
Here how i exe. the file 
# cd crclient
#crclient ls 
 crclient CyberConf.conf
#crclient ./crclient -u csc -f /home/crclient/CyberConf.conf 
#bash No Such File or Directory 

Also I m running ubuntu in Failsafe mode because normal gnome is not working properly. When i login in normal gnome session , login window flikers and goes bak to login window .

---

### Post by Oldsoldier2003 on 2008-04-01
> **chandrakant11 said:**
> Hi I m Ubuntu 7.10 User (Acer Aspire , Turion , 1.5GB Ram) 
I m using broadband Internet connection . I have to logged on the server thru crclient, A executable file. 
When I reinstall Ubuntu 7.10 and try executing this crclient file , I get "No Such File or Directory " Message . Don't know why .
Here how i exe. the file 
# cd crclient
#crclient ls 
 crclient CyberConf.conf
#crclient ./crclient -u csc -f /home/crclient/CyberConf.conf 
#bash No Such File or Directory 

Also I m running ubuntu in Failsafe mode because normal gnome is not working properly. When i login in normal gnome session , login window flikers and goes bak to login window .
Is crcclient the username of your user? Because the path you are using makes it look like you are user crc client. I'm guessing the command should be ./crclient -u csc -f /home/<user_name>/crclient/CyberConf.conf

---

