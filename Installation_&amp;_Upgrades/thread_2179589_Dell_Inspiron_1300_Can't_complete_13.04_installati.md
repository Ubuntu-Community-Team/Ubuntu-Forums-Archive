---
title: "Dell Inspiron 1300: Can't complete 13.04 installation"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by ddubbz1979 on 2013-10-09
After a successful installation of Ringtail on my desktop pc, I thought I would breath some life back into an old Inspiron 1300 I had laying around.  Want to get rid of XP on it and go for Ubuntu.  Try Ubuntu works fine.  But when I install, I get to the screen that asks to check to install updates and third party software... then it either freezes there, or I get a black screen with tons of code that freezes.  Any ideas appreciated.

---

### Post by carl4926 on 2013-10-09
Could your machine have limited RAM if it's 'old'
Rather than Try ubuntu
Go right to the installer, it uses less resources
You might also want to check the media from the boot menu

---

### Post by ddubbz1979 on 2013-10-09
I installed a RAM upgrade to 2gb.  Also tried going straight to installer.  Hardwired LAN by ethernet.  I am using a USB.

---

### Post by carl4926 on 2013-10-09
> **ddubbz1979 said:**
> I installed a RAM upgrade to 2gb.  Also tried going straight to installer.  Hardwired LAN by ethernet.  I am using a USB.

I've had a USB that will boot to the desktop and appear fine
Then install fails
A check of the media revealed the media was bad
Re-wrote it and it was fine.
Only ever happened once though.

---

### Post by ddubbz1979 on 2013-10-09
How did you check the media?

---

### Post by carl4926 on 2013-10-09
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/Ubuntu-boot-menu.jpeg](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/Ubuntu-boot-menu.jpeg)

---

### Post by mörgæs on 2013-10-09
Ubuntu is likely too heavy, but you could try the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").

---

### Post by ddubbz1979 on 2013-10-09
> **carl4926 said:**
> [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/Ubuntu-boot-menu.jpeg](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/Ubuntu-boot-menu.jpeg)

I did not get the option to check for defects.  only the other 4 options.  Looks like its disconnecting me from the internet as soon as I start the installation.  green check mark before I click and turns to an x immediately after I click to continue.  Through my research I have found some issues with the broadcom.  I am trying a hardwired installation, but haven't had any change.  Not sure how to get around this.  Found something about hitting f6 to blacklist the broadcom in the grub, but not sure when to hit f6 to make changes.  Or if this is necessary at all.  Still looking for help nonetheless.  Thanks.

---

### Post by ddubbz1979 on 2013-10-09
I have a Dell Inspiron 1300 I'm trying to install 13.04.  Getting hung up during installation on the 2nd screen with choosing updates and 3rd party software.  When I hit continue, it seems to immediately disconnect from the internet.  I have tried a hardwired connection.  From my research, I have found the broadcom card has some issues.  However, I found one fix [COLOR=#333333][FONT=UbuntuRegular]by hitting f6 and [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]typing in b43.blacklist[/FONT][/COLOR][FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]=yes[/FONT][COLOR=#333333][FONT=UbuntuRegular] before selecting to install.  I can't find where to type this.  I have hit f6 during computer booting and when ubuntu boots and can't find an option for this.  I need linux on this old laptop if anyone can help me out.  heard Mint may work better on this system but I don't know anything about it.  Any help much appreciated.  [/FONT][/COLOR]

---

### Post by chili555 on 2013-10-09
Have you already installed and need to get the wireless going? Or are you trying to complete the install? If installed, please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn -d 14e4:
```

---

### Post by ddubbz1979 on 2013-10-09
> **chili555 said:**
> Have you already installed and need to get the wireless going? Or are you trying to complete the install? If installed, please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn -d 14e4:
```


Trying to get the install going.  Cuts internet connection and freezes on 2nd screen.

---

### Post by mörgæs on 2013-10-09
Please don't double-post.
Threads merged.

---

### Post by ddubbz1979 on 2013-10-09
> **mörgæs said:**
> Please don't double-post.
Threads merged.

While I appreciate the good intention, I saw my first post disappear into oblivion with no recent activity.  Which led me to believe I should've posted in Networking forum to begin with.  Just looking for a solution to my problem.  Couldn't figure out how to move my other one over.

---

### Post by mörgæs on 2013-10-10
> **ddubbz1979 said:**
> Couldn't figure out how to move my other one over.
You can't. If you think a thread should be moved you have to report it, also if it's your own.
Besides you already have a (possible) solution here: Alternate Lubuntu.

---

### Post by ddubbz1979 on 2013-10-10
Others have successfully installed Ubuntu on this machine.  Got to be a way to get it done.  Internet is getting cut off at beginning of install.  Even hardwired.  Not sure a different distribution will work any different.  The solutions I have found are just a little too vague for me to figure it out.  If I can find that f6 function to type in the blacklist I may have a shot.  That's the help I'm seeking at this point.

---

