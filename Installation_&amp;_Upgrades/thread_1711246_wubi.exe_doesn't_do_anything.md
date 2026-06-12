---
title: "wubi.exe doesn't do anything"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by gorellana09 on 2011-03-21
Hello guys,

First please excuse my total noobness. I have been reading about Ubuntu for a long time and now I finally decided to give it a try. I am now running Windows Vista Home Premium 32-bit SP2. I downloaded the Ubuntu 10.10 and the appropriate wubi for it. I wish to install using wubi as this is my first time using Ubuntu and I wish to see if it is the right thing for me. However after 4 hours I now give up. Both wubi and the .iso file are on the same folder yet when I click wubi.exe I get the usual windows permission prompt and after I click continue nothing happens, no installation, no prompts, just nothing happens. What is causing this? I really want to give Ubuntu a try. Thanks in advance for your help.

---

### Post by Rubi1200 on 2011-03-21
Hi and welcome to the forums :-)

Is there a logfile?

Windows side installation logs are in your user temp folder (%temp%).

If you find the file post the contents here please.

---

### Post by gorellana09 on 2011-03-21
Hello Rubi, thanks for your reply. In my first attempt to install Wubi I downloaded the file straight from the link given on the Wubi download page. I read that the version might be wrong so to be sure i had the right file I extracted the wubi.exe file that comes in the .iso file. 

How do I get the log to post it here? When I go to the Temp folder I am not sure what I am looking for, there are a lot of other folders inside it.

Thanks.

---

### Post by Rubi1200 on 2011-03-21
The logfile you are looking for should have this name:
wubi-10.10-r197.log

Just open it and post the contents here.

---

### Post by gorellana09 on 2011-03-21
Hello Rubi, Thank you for your great patience with a noob like me. I am afraid no such log file exists on machine.

ETA: everytime i try to run the installer a file called "pylA871.tmp.exe" or a variation of it is created, but no log file.

---

### Post by Rubi1200 on 2011-03-21
Since you downloaded the desktop ISO, why not burn it to CD and then install that way?

In other words, burn the image to CD and then run it like that from within Windows.

By the way, can you check in Disk Management and let us know if the disks are labeled as Basic or Dynamic please.

Thanks.

---

### Post by gorellana09 on 2011-03-21
Hi Rubi, The disks are labeled Basic. And I have tried to install with CD as well and it still does nothing, it's as if it just aborts. Btw looking through some old threads I saw some people having the same problem with earlier versions of wubi where it came into conflict with existing installations of python? I have python installed now.

---

### Post by Rubi1200 on 2011-03-21
> **gorellana09 said:**
> Hi Rubi, The disks are labeled Basic. And I have tried to install with CD as well and it still does nothing, it's as if it just aborts. Btw looking through some old threads I saw some people having the same problem with earlier versions of wubi where it came into conflict with existing installations of python? I have python installed now.
Aha!

What version of python do you have installed on the computer?

---

### Post by gorellana09 on 2011-03-21
Thanks again for your patience Rubi. It is Python 2.6

---

### Post by Rubi1200 on 2011-03-21
I found something in a bug report about this that might be worth trying:

INSTALL:

Create a new text file containing these two lines:
 
> SET PYTHONCASEOK=
wubi.exe
Save the file with the name wubi-install.bat in the same folder as your downloaded wubi.exe.
 
Double click the wubi-install.bat batch file to install.

---

### Post by gorellana09 on 2011-03-21
Still nothing. Only thing it accomplished is that now a folder pyl6B92.tmp exists.

---

### Post by Rubi1200 on 2011-03-21
Okay, I am going to ask forum member bcbc, an expert on Wubi, to take a look because I am out of ideas; sorry :-(

Meantime, post the contents of that file and when posted highlight the text and click on the # on the toobar to wrap with code tags; makes for easier reading.

Thanks.

---

### Post by gorellana09 on 2011-03-21
It is actually a folder with contents but still there is no log file.

---

### Post by bcbc on 2011-03-21
It looks like it's defaulting to the python runtime that you have installed. Not sure what you can do about that (I don't know a whole lot about python). You should create a bug on launchpad.net but that's unlikely to get a quick resolution.

---

### Post by gorellana09 on 2011-03-21
It's ok, thanks anyway I simply give up. Tried uninstalling Python but that didn't make a difference, wubi.exe just simply refuses to do anything.

---

### Post by Rubi1200 on 2011-03-21
Please don't give up yet.

Either try Ubuntu as a LiveCD to see if you like it and consider installing in a dual-boot configuration.

Alternatively, install it in something like VirtualBox:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

The other thing to try with Wubi (at least this is what I would do) is get another version of it and try with that. Keep trying with various versions to see if the issue really is related to the python runtime as bcbc suggests (most likely).

If I find more information that might help, I will let you know.

---

### Post by gorellana09 on 2011-03-22
@Rubi & bcbc. Thank you both for your patience and help. After having giving up it is exactly what I did Rubi, I booted from USB and it worked, played around with it a little bit and decided to take the chance and install it! :) I am posting from it right now. I am updating drivers and it is updating atm. I am both excited and scared because I do not know what will happen after reboot but we will see!

---

### Post by gorellana09 on 2011-03-22
Ok done installing all the updates and everything it asked. I am happy everything seems to be working out of the box, even my wireless is working. BUT...here is comes the problems I was afraid of:

1) After installing the drivers it asked for my ATI card the graphics seem to have gone from ok to bad. All the text everywhere keeps getting jumbled up everywhere.

2) And what I was most afraid if is that now I cannot boot to Windows Vista.  On the boot screen I now have two options that say Windows Loader (on/dev/sda1) and Windows Loader (on/dev/sda2) I pick the first one and it goes to the Microsoft Vista Home Premium progress bar screen and it stay there forever and never moves.

How can I fix these two problems please?

---

### Post by bcbc on 2011-03-22
Regarding windows, boot Ubuntu and run "sudo fdisk -l" (lower case L) or open gparted. Check which partition has the boot flag set. That's the one you want to boot. Grub2 isn't very good at distinguishing vista from the vista recovery.

Try that and see if you can get windows to boot.

---

### Post by Rubi1200 on 2011-03-22
For the graphics, you may have to install the fglrx driver. See here for more details:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by gorellana09 on 2011-03-22
UPDATE: Windows boots just fine I guess the first reboot I just had to wait a while and give it time. Now it boots perfectly I even managed to make Windows Vista the default OS :D

I temporaily uninstalled the ATI graphics drivers that was the defualt and is ok again for now but nonethe less I still need the drivers for my card so I will give that link you give a try 

Once again thanks you two have been great help to get a Linux noob like me get started. I must tell you though the dual boot installation was much easier than trying to figure out why wubi.exe did not want to run.

---

### Post by Rubi1200 on 2011-03-22
Great news about booting Windows and I am sure you will find a solution for the graphics drivers.

Let us know what happens or if you need help with anything else.

---

### Post by gorellana09 on 2011-03-22
Rubi, I have followed everything on that link you provided, however at #16 
sudo aticonfig --initial

it returns a no comand found or something of the sort and the drivers do not get installed. 

Other than still needing the graphics card drivers everything else seems to be working fine. I love the messaging capabilities, I can finally be loged in to all my messaging accounts all at once! :) Linux is new to me but looking forward to become comfortable with it.
Just wish I could get the graphics drivers to work :(

---

### Post by Rubi1200 on 2011-03-22
I have no experience with ATI drivers, as my laptop uses Intel graphics.

But, when you get to the login screen, before entering your password, there is an option at the lower part of the screen to use Safe Graphics Mode; try it and see if it makes a difference.

---

### Post by gorellana09 on 2011-03-22
UPDATE: Everything is 100% Operational. Thank you Rubi and bcbc for all your help. 

The Graphics drivers for my ATI card that came out of the box with the Ubuntu installation works fine when I log in using the Ubuntu Desktop option rather than the Ubuntu Notebook. Seems the problem is only on notebook mode, and that is fine Desktop is just fine anyway. :)

Moral of this story is to use USB to boot directly into Ubuntu, play with it a bit see if you like it and then Install it. Installation is easy and you cannot mess up your Windows OS as long as you read the screen carefully. Forget the wubi cos its more complicated. 

And now to learn about linux and to get used to it! Thanks again!

---

### Post by Rubi1200 on 2011-03-23
Excellent! You are more than welcome too for the help. I am sure bcbc will also be pleased.

Please mark this thread Solved using the Thread Tools near the top of the page.

If you need more help with other issues, start another thread and we will try and help if we can.

---

