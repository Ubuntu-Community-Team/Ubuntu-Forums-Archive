---
title: "How to create a Windows 7 Installation USB Within Ubuntu?"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by Pougnet on 2011-07-04
Hello, my friend wants me to make him a usb install media for Windows 7. I have tried multiple methods from within Ubuntu to create it. But, they all have failed. Please note that I do not have an optical drive on any of my computers. Here is what I have tried so far.

[LIST]
[*]NTFS format the USB drive then proceed with dd to copy the iso files.
[*]Use Unetbootin to install the iso to the drive
[/LIST]
Using the first method, it would not boot. Using the second method, I got the following error ```
[FONT=Arial][SIZE=2][LEFT]File: \Boot\Bcd[/LEFT]
 [LEFT]Status: 0xc000000f[/LEFT]
 [LEFT]Info: An error occurred while attempting to read the boot configuration data.[/LEFT]
[/SIZE][/FONT]
```Does anyone know the correct way of creating it?
P,S If this is in the wrong thread, I apologize.

---

### Post by gigenieks on 2011-07-24
[Need help here:]("http://ubuntuforums.org/showpost.php?p=11079460&postcount=5")

[QUOTE=gigenieks]


2. it is probably the best solution - [COLOR="Navy"]**but how I do this (make bootable Win7 installation on USB) in Kubuntu??**[/COLOR] 
[/QUOTE]

Can someone help us?
Really need that!
I'm beginner, so, please steb-by-step instructions.

---

### Post by Quackers on 2011-07-24
I haven't used it myself, but method 2 in the thread below seems to work for a Win 7 repair disc - maybe it will for an installation disc.

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by gigenieks on 2011-07-24
Tnx, but I used that link already (when I could load in Windows 7). The thing is my Win 7 is installed on [COLOR="DarkGreen"]SATA hard drive[/COLOR].

[Why I need bootable Win7 installation USB]("http://ubuntuforums.org/showpost.php?p=11076875&postcount=3")

[QUOTE=Mark Phelps]
The Repair CD **does not contain drivers**; instead, it only contains the minimal files needed to regenerate the Win7 boot loader files.
It expects to see a Win7 INSTALL DVD for drivers (or, driver CD).
[/QUOTE]
That is why I need INSTALLATION Win7 USB stick! I _don't need_ it for install, but instead I need those [COLOR="Purple"]**Recovery utilities**[/COLOR] which I can only use if it "sees" Windows, if I load with that bootable repair USB I get this:

[[IMG]http://i1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/th_IMAG0094.jpg[/IMG]](http://s1200.photobucket.com/albums/bb335/cleverman89/Win%207%20USB%20repair%20issue/?action=view&current=IMAG0094.jpg)

In short I need Win 7 installation USB stick. And it has to be **made from Kubuntu** 11.04!


When I get to those Recovery utilities I will do chkdsk /r /f and I'm quite sure it would fix my dual-boot issue! 

Hope I was clear enough about my situation. :)

---

### Post by Quackers on 2011-07-24
That's what you get when you run a recovery cd. You want the tools from a repair cd. They are different, even though Microsoft actually calls a repair disc a recovery cd. You can download repair discs for your system and architecture from certain sites (though some have been removed because of "copyright issues" - supposedly). Google for them.
Very confusing.

---

### Post by gigenieks on 2011-07-24
[QUOTE=Quackers]
You want the tools from a repair cd.
[/QUOTE]
Yes!!

**_BUT_** the thing is my Windows was installed on **SATA** HDD. Repair disks **dont have [COLOR="DarkRed"]drivers[/COLOR]** that equals to it doesn't "see" my Windows and that equals to "no repairing" (because there is nothing to repair or function with)
Hoping that I was clear enough..

---

### Post by Quackers on 2011-07-24
Not at all!
You can run chkdsk from the command prompt, which is available in repair disc and installation disc, but not recovery disc.

---

### Post by gigenieks on 2011-07-25
OK you can **run** [COLOR="DarkRed"]BUT[/COLOR] you can't actually do chkdsk because there is no HDD to do that "chkdsk".

---

### Post by georg5030 on 2011-07-25
I have found a much easier way to **install Windows 7 from a USB Flash drive**.  Unlike other methods where you have to write complicated commands, this  method can be completed even by those who have very little computer  background. The whole process takes only two steps, run UNetbootin, load the  Windows 7 ISO file, and finally restart your computer.


 Before you begin, you will require the following:
 
[LIST]
[*]USB Flash Drive (4GB minimum)
[*]Windows 7 ISO Image file
[*]UNetbootin
[/LIST]
 
 **Note:** If UNetbootin doesn’t work, try out the Microsoft’s official tool called Windows 7 USB/DVD Tool.
 Now insert the USB drive, run UNetbootin, and select Disk Image as  ISO. Browse your local drive for Windows 7 ISO that you downloaded and  click Open. Now Select Type as USB and choose the drive. Once done, it  will look like a bit similar to the screenshot shown below.
 [IMG]http://cloud.addictivetips.com/wp-content/uploads/2009/05/unetbootinmainwindows7.png[/IMG]
 Click OK and it will begin extracting all installation files to the  USB drive. The whole process will take some time(10-15 minutes), so have  patience.
 [IMG]http://cloud.addictivetips.com/wp-content/uploads/2009/05/unetbootininstallingwindows7iso.png[/IMG]
 Once the installation is complete, reboot your computer. Now while  your system is starting up press the appropriate button(usually F1, F2,  F12, ESC, Backspace, or Escape) to bring up Bios Boot Menu. Change the  startup order to boot USB by default, usually you will have to press F6  to move the selected USB device on top. Once done, save changes and  restart the system.
 [IMG]http://cloud.addictivetips.com/wp-content/uploads/2009/05/windows7installscreenboot.jpg[/IMG]
 ***Windows 7 installation screen on my HP Dv5t laptop.***

 Wasn’t that easy? Enjoy!

---

### Post by Quackers on 2011-07-25
Ah! So unetbootin can make Windows iso's work! Excellent, thanks :-)

---

### Post by Mark Phelps on 2011-07-25
WOW -- Unetbootin CAN create Win7 bootable USB sticks??

That's good news.  

Wish that the Unetbooting folks would update their website to tell folks that.  Checked just a few minutes ago, and it STILL says the following:

> UNetbootin allows you to create bootable Live USB drives for Ubuntu, Fedora, and other Linux distributions ...

However, the screen shot implies that this was done from inside Windows, not from inside Ubuntu.  So, if that was true, then it's likely that you STILL can not create bootable Win7 USB sticks from inside Ubuntu.

---

### Post by Quackers on 2011-07-25
Ah, watch this space :-)

---

### Post by gigenieks on 2011-07-26
> **Mark Phelps]
Unetbootin CAN create Win7 bootable USB sticks??

However, the screen shot implies that this was done from inside Windows, [COLOR="Purple"]**not from inside Ubuntu.**[/COLOR]  So, if that was true, then it's likely that you STILL **_can not_** create bootable Win7 USB sticks from inside Ubuntu.
[/QUOTE]
I can confirm that [COLOR="DarkRed"]**_you can_**[/COLOR] create Windows 7 bootable USB stick [COLOR="DarkGreen"]**from Kubuntu!**[/COLOR]



[CENTER][SIZE="4"][COLOR="Navy"]**Instructions for Kubuntu 11.04**[/COLOR][/SIZE]


[SIZE="4"]Step 1[/SIZE][/CENTER]

1. Opened KPackageKit typed "unetbootin" - installed it.
2. Installed GParted via Terminal
```

**sudo apt-get install gparted**

```
3. Tried to open GParted using KMenu (*dunno if it is called like that*) > Applications > System > Partition editor GParted

a. Kubuntu asked "Enter the administrative password" so, I entered. Wrong. Tried again - wrong. (_100% sure_ I didn't mistype or something..)
So, I used [Googl Ubuntu]("http://www.googlubuntu.com/") and found following --->
[LIST]
[*][URL="http://kubuntuforums.net/forums/index.php?action=printpage said:**
> description of problem 1[/URL]
[*][description of problem 2]("http://ubuntuforums.org/showthread.php?t=1767218")
[/LIST]

Basically to summ up:
[QUOTE=kubicle]
Since gparted recommends gksu, it will get installed by default with gparted. And gparted will likely use gksu by default **to gain root privileges**. And if gksu hasn't been configured to use sudo it will likely expect the root password (literally) rather than a sudo password.

[COLOR="DarkGreen"]**So either enabling sudo for gksu or using kdesudo explicitly should do the trick**[/COLOR].
 
[how to successfully open GParted by ankspo71 using terminal:]("http://ubuntuforums.org/showpost.php?p=10860967&postcount=2")
```

**kdesudo gparted**

```
Asked password. Entered - voila! GParted.

4. Using GParted

a. Formated USB to NTFS
b. Then right click "Manage flags" > boot
c. Mount USB - I just removed & inserted again to my PC. And clicked on it in Dolphin.

[CENTER][SIZE="4"]Step 2[/SIZE][/CENTER]

1. Open UNetbootin.
Same error about "wrong password" (again it was 100% right!) 
So I did again:
```

**kdesudo unetbootin**

```
Voila!

2. Select ISO image of your Windows 7.
3. Select your USB drive.
**_Important:_** by default it was for me dev/sdc5 had to change dev/sdd1!
(You can check how that USB is named in GParted)

[CENTER][SIZE="4"]Step 3[/SIZE][/CENTER]

1. Press OK when all is configured. (ISO image selected & right USB)
2. Wait it will do the job. 
P.S. Screen 'frozed' (*I think its called that*), that is I just stopped on 5% and stayed like 3-5min. Then it went till 52% and again frozed (I could move around with mouse close software etc; but sometimes I couldn't even move mouse for few secs or min..). This time I [COLOR="DarkRed"]**had to wait 15-20min!!**[/COLOR]

After that it finished.
I rebooted, configured BIOS.
Viola USB booted.
Hadn't yet installed Win 7, but don't think something is wrong.


P.S. Since I have problems with image hosting sites (Photobucket etc.) I upploaded important things in attachments. Check them out.


Thank you georg5030.
Here is what I found --->

[LIST]
[*][post #4]("http://ubuntuforums.org/showthread.php?t=1523239")
[*][**amedac!!**]("http://ubuntuforums.org/showpost.php?p=9458199&postcount=6")
[*][ankspo71 about opening GParted]("http://ubuntuforums.org/showpost.php?p=10860967&postcount=2")
[*][[COLOR="Purple"]**Also read this - instructions!**[/COLOR]]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html")
[/LIST]


Hope I did good post and it will help someone.

---

### Post by Quackers on 2011-07-26
Thanks for that info gigenieks :-)
So now we know!

---

