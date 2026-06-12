---
title: "Can't Install ''usb-modeswitch',"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by emtiazemon on 2010-08-10
[FONT=Verdana][SIZE=2]Hello,

I'm a novice in ubuntu world. Recently I've installed Ubuntu 10.04. Now for detecting my modem I need to install **usb-modeswitch**. But I cant install it graphically. It shows an error that is,

[IMG]http://ubuntuforums.org/d:%5Cscreenshot.jpg[/IMG]

[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Red][B]Error: Dependency is not satisfiable:
usb-modeswitch-data(>=20100127-1)[/B][/COLOR][/SIZE][/FONT] [FONT=Verdana][SIZE=2]

I've downloaded the file from several mirror but the problem remains.

*I tried to use the terminal but failed.

Now what should I do? Without it I can't use internet and have to continue using my pirated version of win 7
[/SIZE][/FONT]

---

### Post by rollin on 2010-08-10
Hi and welcome to the forum!

I might be "jumping the gun" but it sounds like you are using a 3G  internet modem? If this is true it should work out of the box with  Network Manager !? Boot into the system wait a minute and then connect  the USB. You should see under the Network Manager Menu an item for "New  Mobile Broadband GSM Connection" or something similar... Follow the  steps with your APN and Network Name after the Wizard has completed and it should work when connected at boot.

---

### Post by StormNinja3 on 2010-09-16
Hey Emtiazemon,

I am having the same problem installing a BroadBand2Go USB modem on my 9.4 Jaunty  laptop.  The solution posted above may or may not work.  I tried to install through the Network Manager but --#1 did not have an option to select "Virgin" as the service provider and #2- selected Sprint, which is the actual network used by Virgin, but this made no difference. The device did not attempt to connect.

I believe we will have to solve the problem using USB-Modeswitch software and accompanying installation instructions.  Visit the link below to see an alternative solution.  I will attempt the same shortly.  Good Luck.

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=343&sid=cf173c241daba40d413a99fdc5ed13c4](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=343&sid=cf173c241daba40d413a99fdc5ed13c4)

---

### Post by uhuru83 on 2010-09-16
> **StormNinja3 said:**
> Hey Emtiazemon,

I am having the same problem installing a BroadBand2Go USB modem on my 9.4 Jaunty  laptop.  The solution posted above may or may not work.  I tried to install through the Network Manager but --#1 did not have an option to select "Virgin" as the service provider and #2- selected Sprint, which is the actual network used by Virgin, but this made no difference. The device did not attempt to connect.

I believe we will have to solve the problem using USB-Modeswitch software and accompanying installation instructions.  Visit the link below to see an alternative solution.  I will attempt the same shortly.  Good Luck.

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=343&sid=cf173c241daba40d413a99fdc5ed13c4](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=343&sid=cf173c241daba40d413a99fdc5ed13c4)

:)you are right ):P

---

### Post by StormNinja3 on 2010-10-16
**Thanks Uhuru83**! :)

I have successfully gotten Virgin Mobile Broadband2go Card to work on my Jaunty laptop.

Hopefully this update will  help others who are still having problems installing or understanding the install instructions. 

#1.  The website shown in my previous post will the most helpful to Ubuntu(and other Distros that use 'sudo') Users who are experienced installing software manually but for those who are not so advanced you may remained confused and frustrated.

#2.  So, for those who need simplified-plain English help there is Good News.  One of Ubuntu's very own Forums will help immensely.  Visit the Link Below to see the command line codes to install from the Draisberghof Site directly into your machine.

[http://ubuntuforums.org/showthread.php?t=1578311](http://ubuntuforums.org/showthread.php?t=1578311)

#3.  Simply Copy/Paste each line of Code into Terminal.  Take your time.  Do not rush.

The very first line with "sudo' will require your password.  Remember the PW will be invisible after you type it press Enter

Continue to Enter each line of Code>Followed by Enter

After you have completed the 5th Copy/Paste--You may not understand what the author means  by   "[COLOR=Red]**RULESDIR    = $(DESTDIR)/lib/udev/rules.d**[/COLOR] :"

Look at your screen.  You will that a Gedit(text editor) Document will have opened.

Copy/Paste the 2 lines of  Code Shown **below** the Red Text into the Gedit/Text Editior Document and Save. 

#4.  Enter the Final Line of  Code shown> Press Enter.

Do Not Insert the Broadband Card into the computer at this point.  Restart First then insert.  If you have followed the directions correctly  you will a Mobile Broadband Connection Category shown when you click on the Network Manager Icon.

I've added these tips as I have seen in many other forums where people having problems understanding and if I've made an error.  Please feel free to correct ASAP.

---

### Post by parkks on 2011-03-09
Thanks for help. I spent a couple of hours trying to get a Huawei E1752 (from CellC) the USB ID (obtained from the lsusb command in terminal) is 12d1:1446 working and this post was very useful.

For anyone struggling with this in future

You might need to have libusb-dev installed, not just libusb otherwise you get [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=592](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=592)

You might need to change a value for the TargetProductList usb-modeswitch config file.
See [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=585#top](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=585#top)
And [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=561&sid=b1fc4ab2946571296dc2042a4630ef21](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=561&sid=b1fc4ab2946571296dc2042a4630ef21)

Good luck

---

