---
title: "Installing grub after windows"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by quarkhirad on 2014-10-18
Hi i have a dual boot between windows and ubuntu 14.04. After updating my windows i realized my grub was lost and windows would directly boot. Something that i am familiar with and know. So i then downloaded the 14.04 iso. Then created a boot able pendrive and ran the live version. I clicked on install but i was supprise to find that i can only remove ubuntu 14.04 and install fresh or remove everything and install ubuntu. But there was no option to repair grub something i remember from way back :(. So i searched online and found the following site  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I followed the second option in the page. Hence i opened terminal and typed all the command one after another and boot repair started. After clicking on recommended repair in boot repair i followed the commands and installed grub successfully[ATTACH=CONFIG]257326[/ATTACH][ATTACH=CONFIG]257327[/ATTACH] (see attached screenshot). After that i restarted the system and voila i had my grub menu. I could boot windows successfully but when i tried to boot linux i got an error message (see attached photo DSC_389). Please help me solve this error so that i can start using ubuntu.

---

### Post by TheFu on 2014-10-18
This happened to me this week too.

**boot-repair** fixed it. see my signature for links.

---

### Post by quarkhirad on 2014-10-18
Hey hi I used boot repair. in your signature i clicked on boot repair and it takes me to the page  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) that is the place i started. I have used boot repair and see the screenshot in first post. It shows that i ave used boot repair and in terminal it shows that grub has been successfully installed. Yet i cant boot my linux it gives me an error. So  TheFu please tell me something new

---

### Post by yancek on 2014-10-18
The bootrepair software usually has an option to output a text file which shows information on your system and what it does or recommends be done.  Posting that here would be helpful as would posting which release of windows your are using as you don't mention it.  It does make a difference.

---

### Post by quarkhirad on 2014-10-18
yancek 

Hi i have windows 7 installed and how do i enable the text file which shows the information in bootrepair

---

### Post by yancek on 2014-10-18
I think you need to run it from Ubuntu or go to the site below and download it as an .iso file then burn it as an image to a CD, when finished reboot the computer with the CD drive set to first boot priority.  I've never actually used bootrepair so just from what I've read here.

[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

---

### Post by quarkhirad on 2014-10-26
Hey hi. Sorry got a little busy. I still cannot boot my linux. yancek i tried that and tried repairing my grub it said failed and gave me a url. I have pasted the url below please can someone read it and tell me what to do so that i can repair my grub and start using linux. 

> [http://paste.ubuntu.com/8690534](http://paste.ubuntu.com/8690534)


thanks

---

### Post by yancek on 2014-10-26
At the end of the boot repair script it is telling you to enable repositories containing linux packages.  Just below that you will see:

> grub-install: error: install device isn't specified.  

You need to specify the device.  I'm not familiar with the boot repair as I've never used it so don't know where that option is.

---

