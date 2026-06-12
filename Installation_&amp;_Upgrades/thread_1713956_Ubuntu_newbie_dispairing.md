---
title: "Ubuntu newbie dispairing"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by stefanjan on 2011-03-24
Hi, I have a spare laptop so thought after using Windows for many decades I'd give Ubuntu a try.

My initial experience after a very smooth install have been very frustrating. Before ditching Ubuntu and restoring Windows from backup I thought I'd ask questions here in case there were solutions:

1.  Resolution too low - max available 800 x 600  I can't find any linux video drivers

2. I installed Ubuntu to dual boot with Windows Vista (version completely up to date). When I reboot and try to load Windows I get a message do I want to repair Windows?

3. When I try to install software updates in Ubuntu, I get a message 'Failed to download package files. Check your internet connection. In the details window there are a whole list of Failed to fetch ......... There is nothing wrong with my internet connection. I can browse internet fine within Ubuntu.

4. Ubuntu keeps asking me for my password. Is it possible to stop this?

My laptop details are as follows:

Fujitsu Siemens Esprimo Mobile V5515 Laptop Intel Pentium Dual-Core Processor T2130 1.86GHz 2048MB 120GB DVDRW 15.4" WXGA TFT Windows Vista Home Premium Edition

---

### Post by aeronutt on 2011-03-24
Which version of Ubuntu did you load?

For #4, go to Administration, Users & Groups, click on your login name (likely the only one shown), click on Pasword: Asked on login....change. Click radio button at the bottom.

---

### Post by mikewhatever on 2011-03-24
Hi there and welcome,

> **stefanjan said:**
> 
1.  Resolution too low - max available 800 x 600  I can't find any linux video drivers
We might be able to help if you provide info about the graphics card.

> 2. I installed Ubuntu to dual boot with Windows Vista (version completely up to date). When I reboot and try to load Windows I get a message do I want to repair Windows?
Sounds like you try booting the recovery partition. That may need some investigating, but is there only one option for Vista?

> 3. When I try to install software updates in Ubuntu, I get a message 'Failed to download package files. Check your internet connection. In the details window there are a whole list of Failed to fetch ......... There is nothing wrong with my internet connection. I can browse internet fine within Ubuntu.

Are you behind a proxy or something?

> 4. Ubuntu keeps asking me for my password. Is it possible to stop this?
No, sorry. Security is a feature of Linux.:D

---

### Post by stefanjan on 2011-03-24
> **aeronutt said:**
> Which version of Ubuntu did you load?


I loaded 10.10

---

### Post by stefanjan on 2011-03-24
> **aeronutt said:**
> For #4, go to Administration, Users & Groups, click on your login name (likely the only one shown), click on Pasword: Asked on login....change. Click radio button at the bottom.
Thanks that was easy!

---

### Post by aeronutt on 2011-03-24
You'll no longer need to type in your password to log in, but you will need to type in your password for all sudo operations (eg, software loads/updates, and system configuration changes).

---

### Post by smilingfrog on 2011-03-24
I would recommend not dual booting your machine while learning to play with linux. If your truly installed it on a spare laptop, don't keep switching back and forth by rebooting. You'll just drive yourself crazy.

There is a learning curve you have to follow to become familiar with the way things are done in linux. It's very different to Vista. Initially, things just don't make sense, and finding the ways to fix them can also drive you crazy. The best thing to do is leave it alone, and try to fix one problem at a time. Take notes. Learn to love your terminal.

To fix your screen resolution, the configuration file is likely in /etc/X11/xorg.conf ; google how to fix screen resolution, and read and take notes.

Windows NT couldn't read linux partitions; I don't know if Vista can, but I wouldn't let Vista try to repair your laptop, as it may blow your HD bootloader. If you want to run windows and linux together, use a virutal machine like VirtualBox.

Your best friend is Google while learning a new operating system. Cut and paste the error messages into the search bar, and then read what other people have done in the same situation. For instance, your repositories may not be up to date, and that might be why you aren't downloading updates.

Linux is for people who like to tinker. However, it is a very different way of doing things compared to Windows. I think it took me 2 years before I was comfortable enough to troubleshoot what was going on with my machine.

But seriously. Stick with it. Fix one problem at a time. Take notes so you can remember what you did. Search and read. Try stuff out, and if that doesn't work, post something here. And don't despair. Eventually it will be second nature.

---

### Post by stefanjan on 2011-03-25
Hi, I already came to the conclusion that dual booting was a terrible idea as Ubuntu trashed my laptop.

Happy that I didn't try this on my netbook! 

I have reinstalled Ubuntu 10.10.

I have searched many times using Google to find a solution to the screen resolution issue on a Fujitsu Siemens Esprimo Mobile V5515 laptop but all I find is unanswered questions or answers relating to an earlier command line version of Ubuntu. 

Also I can't work how out to identify the installed video card from within Ubuntu. I have explored all the menu options but it's not there.

I am not 100% but have an idea that the card is a SiS Mirage 3

I did find this thread [Re: SiS 771/671 Mirage 3 Video Drivers!?!?]("http://ubuntuforums.org/showthread.php?t=958967&page=38") 
How do I check whether this is suitable for my laptop from within Ubuntu.

Also the instructions say 'open a terminal' how do I do this?

Thanks for your help

---

### Post by Dutch70 on 2011-03-25
applications > accessories > terminal or (Cntrl + Alt + T) 

Type in "lspci" without the quotes to get your video card. 

btw, Ubuntu is yet to trash a machine that I'm aware of. If you trashed your machine by doing something wrong, is it really fair to blame the OS?

---

### Post by stefanjan on 2011-03-25
> **Dutch70 said:**
> applications > accessories > terminal or (Cntrl + Alt + T) 

Type in "lspci" without the quotes to get your video card. 


Thanks for that....

> **Dutch70 said:**
> applications > accessories >
btw, Ubuntu is yet to trash a machine that I'm aware of. If you trashed your machine by doing something wrong, is it really fair to blame the OS?
If Windows trashed my machine, I would blame Bill Gates even if it was my fault!

---

### Post by stefanjan on 2011-03-25
Hi, this is my video card

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS]
771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by Dutch70 on 2011-03-25
LOL, nice response to my last post.

I haven't had the pleasure of needing drivers in Ubuntu, so I know nothing about it. 
However a quick google search for "sis video card ubuntu" brought this up.
Among other things if you want to have a look for yourself.

[[COLOR="RoyalBlue"]http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html[/COLOR]]("http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html")
*Edit: be sure to read the comments in that link.*

---

### Post by hakermania on 2011-03-25
I have a solution for the password requests.
If you want to open up Ubuntu Software Center or Synaptic and constantly asks for password listen what you should do.
1) Go to /home/user/Documents and make a file named open_without_passwd (where user is your username (e.g. /home/alex/Documents)
2) Open the file with gedit and type in:
```

#!/bin/bash
if [ X"$1" = X"U" ]; then
echo "YOUR_LOGIN_PASSWORD_HERE" | sudo -S software-center
else
echo "YOUR_LOGIN_PASSWORD_HERE" | sudo -S synaptic
fi

```
At YOUR_LOGIN_PASSWORD_HERE place your login password within the quotes (")
3) After saving the file, right click on it->properties->permissions->check "Allow executing file as program"
4) Right click to your panel (the one at the top)->add to panel->Custom Application launcher->At the Name field type: **Open Ubuntu Software Center**, at the command field:[B] /home/user/Documents/open_without_passwd U
[/B]At the comment field place whatever you want.
5) Choose an icon if you want (by clicking the button at the Right). Click at the OK button.
6) Repeat from step  **4  **to create a launcher for Synaptic **but **in the Name field type Synaptic and at the command field remove the **U **at the end.

Hope I helped a bit with your problem.

Please, mention that this way is completely secure. Your password is only shown at the file in your Documents folder!

As for your problem with the packages which you cannot download, have you tried **apt-get update **?

---

### Post by VanillaMozilla on 2011-03-25
Look, guys, logging in without a password is one thing, but eliminating the password for sudo or gksudo is quite another, and unnecessary.  There's no need to throw ALL security out for the sake of a tiny convenience.  Notice also that the sudo password stays operational for a few minutes, so it's hardly ever necessary to type it twice.  OK?

And don't forget that this user has SERIOUS problems.  Eliminating the password for sudo is not one of them.

P.S. I'm a little fearful the Windows boot problem might be the dreaded ext4 problem or a problem with the new grub.  There is a problem with byte boundaries on certain hard drives that conform to an older(?) standard, and it can mess up Windows.  Don't ask me any more.  I don't know more about it.


P.S. Note to original poster.  When trying a Linux distribution, it's usually a good idea to boot from a live CD.  Then if there are obvious major problems, like bad video resolution choices, don't install it.  Too late, I know.

On the bright side, I can tell you that sometimes stuff like that just gets fixed for you in the next release.  I've had several minor nuisances that got fixed without me lifting a finger.

---

### Post by stefanjan on 2011-03-28
Thanks for your advice.
 
I followed most of those instructions but got lost towards the latter part. I think I probably need to start again. 
 
Problem is that I seem to have lost the GUI interface.
 
Now when I start up my laptop I boot into a login screen which when I input user id and password opens a command line screen.
 
How do I get my GUI interface back?

---

### Post by Dutch70 on 2011-03-28
When it opens the command line screen. Type in...
```
sudo startx
```

---

### Post by stefanjan on 2011-03-28
> **Dutch70 said:**
> When it opens the command line screen. Type in...
```
sudo startx
```

Oh dear, I did that and get a long error message which includes following:

(==)Using config file: "/etc/X11/xorg.conf"
(==)Using system config directory "/usr/share/X11/xorg.conf.d"
(EE)open /dev/fb0: No such file or directory
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by stefanjan on 2011-03-29
> **stefanjan said:**
> Oh dear, I did that and get a long error message which includes following:
 
(==)Using config file: "/etc/X11/xorg.conf"
(==)Using system config directory "/usr/share/X11/xorg.conf.d"
(EE)open /dev/fb0: No such file or directory
(EE) Screen(s) found, but none have a usable configuration.
 
Fatal server error:
no screens found
 
Can anyone help me with this error message?
[INDENT]Is there a way to recover from this?
 
Should I reinstall Ubuntu and start again?
 
Should I conclude that Ubuntu is not compatible with my laptop?
[/INDENT]

---

