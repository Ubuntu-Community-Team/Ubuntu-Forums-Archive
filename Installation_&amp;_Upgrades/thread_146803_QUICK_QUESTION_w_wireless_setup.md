---
title: "QUICK QUESTION w/ wireless setup"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by elaspeinreason on 2006-03-19
i am nearly finished setting up my wireless card im just unsure as to what to do on a certain step , heres the way i followed : 
* after ndiswrapper was installed

1. Once ndiswrapper is installed remove your ubuntu cd and 
2- Forget about the driver that came with your card. Use driver for RTL8180L for Windows XP from [http://www.realtek.com.tw/downloads/...x?Keyword=81802](http://www.realtek.com.tw/downloads/...x?Keyword=81802). 

3 Open a terminal and get the the new directory and then
4. run this sudo ndiswrapper -i NET8180.INF
5. Then run ndiswrapper -l and see if both hardware and driver/software show up as restent.
6. If so then run sudo modprobe ndiswrapper from a terminal
7. Use the network control panel to set it up


i installed ndiswrapper , i downloaded the drivers to a flashdrive and moved them to the desktop of the ubuntu computer , i ran the sudo mentioned above and i get this message as a reply  : unable to create directory /etc/ndiswrapper/net8180. Make sure you are running as root

im really stumped on what to do , please ANYONE help if you can !
thank you.
-e :confused:

---

### Post by elaspeinreason on 2006-03-19
in going back to the problem i didnt type in sudo before ndis
now i tried it and it gives me this response :

installing net8180
cp:cannot stat 'NET8180.INF' no such file or directory

---

### Post by Titus A Duxass on 2006-03-19
I use the NETR8180.inf XP Driver that came on the CD for the wireless card.
Make sure you have installed the kernel headers.

Are you doing "sudo ndiswrapper -i /home/yourname/desktop/net8180.inf" ?

---

### Post by elaspeinreason on 2006-03-19
the wiki entry for my Linksys card told me not to use the driver that came on the cd , but to download the NET8180.INF one instead.

after entering the following " sudo ndiswrapper -i /home/yourname/desktop/net8180.inf " i get the message that i have already installed the driver ,
when i check for the driver i get the message 
" installed ndis drivers : 
net8180 invalid driver! " 

i attempted to erase it , but got the message "rm: cannot remove `/etc/ndiswrapper/net8180' : permission denied. 

thanks again
-e

---

### Post by Titus A Duxass on 2006-03-19
Don't forget "sudo ndiswrapper -r

---

