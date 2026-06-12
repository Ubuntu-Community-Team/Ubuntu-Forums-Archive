---
title: "Windows Installer launch error message"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Craig H on 2011-02-01
I want to download and install Ubuntu to run alongside Windows 7 in a dual boot configuration. I went to this page: 

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) 

   .....and downloaded the Windows Installer, but when I try to launch it I get an error message which I captured and attached to this post. What's really wierd is that once the message is displayed, I can't get rid of it. Even running the Task Manager to try to close the message doesn't work. I literally have to restart the computer to get rid of the message!

Am I suppose to be downloading the Windows Installer (Wubi) to a CD first where I run it from there? If so, the instructions don't mention that. Can't I download it directly to my C: drive and then run it from there? If so, why am I getting the error message?  Thanks!

---

### Post by Frogs Hair on 2011-02-01
I have used Wubi 10 times on windows 7 and never seen this . Wubi is supposed to start the download and no disk is required . I would remove your current Wubi and download another or download the Ubuntu ISO and which includes Wubi on the disk and install that way.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you have the disk you can test Ubuntu from the cd to see if it works with your hardware . Ubuntu will run slower from the cd.

---

### Post by Craig H on 2011-02-01
> **Frogs Hair said:**
> I have used Wubi 10 times on windows 7 and never seen this . Wubi is supposed to start the download and no disk is required . I would remove your current Wubi and download another or download the Ubuntu ISO and which includes Wubi on the disk and install that way.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you have the disk you can test Ubuntu from the cd to see if it works with your hardware . Ubuntu will run slower from the cd.

I went to  [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)    and re-downloaded Wubi.exe from there. When I hit the "Run" button..... same thing happened.  The message popped up and I had to restart my computer to get rid of it.

I just reinstalled Win7 on this Dell laptop (i7 820QM with 8gb ram), so the OS is fast, clean, and smooth. Can't imagine what could be happening.... guess I will have to go buy a blank DVD-R.

---

### Post by bcbc on 2011-02-02
Running it off a DVD or CD won't make a difference. This is an error that python gives (Wubi uses python) when it finds a drive letter assigned to an empty drive. Usually a MMC card reader. So just disable/remove that and any other extraneous peripherals you have.

It actually can install if you keep clicking Continue, but it's a pain (it's not the endless loop it appears to be). Also, you can kill it from task manager rather than having to restart windows.

PS if you install wubi, make sure you lock grub-pc and grub-common as soon as you get it booted. See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.

---

### Post by Craig H on 2011-02-02
> **bcbc said:**
> Running it off a DVD or CD won't make a difference. This is an error that python gives (Wubi uses python) when it finds a drive letter assigned to an empty drive. Usually a MMC card reader. So just disable/remove that and any other extraneous peripherals you have.

It actually can install if you keep clicking Continue, but it's a pain (it's not the endless loop it appears to be). Also, you can kill it from task manager rather than having to restart windows.

PS if you install wubi, make sure you lock grub-pc and grub-common as soon as you get it booted. See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.


Thanks bcbc..... I did as you said and kept hitting the Continue button about 8-10 times and the Ubuntu Installer dialogue box came up to start the download.  

Before I get this started, I have another question...... You said to lock grub-pc and grub-common as soon as I get it booted.  I went to the wubi megathread and it states: [COLOR="Red"]"Go to System > Administration > Synaptic Package Manager and select the grub-pc and grub-common packages. Click on Package > Lock Version."[/COLOR]  Is this the "System" within the Control Panel?  If so, I cannot find an "Administration" option on the "System" page.  I just want to make sure I have all of this completely understood before I install the Ubuntu OS.  Thanks..... Craig

---

### Post by bcbc on 2011-02-02
> **Craig H said:**
> Thanks bcbc..... I did as you said and kept hitting the Continue button about 8-10 times and the Ubuntu Installer dialogue box came up to start the download.  

Before I get this started, I have another question...... You said to lock grub-pc and grub-common as soon as I get it booted.  I went to the wubi megathread and it states: [COLOR="Red"]"Go to System > Administration > Synaptic Package Manager and select the grub-pc and grub-common packages. Click on Package > Lock Version."[/COLOR]  Is this the "System" within the Control Panel?  If so, I cannot find an "Administration" option on the "System" page.  I just want to make sure I have all of this completely understood before I install the Ubuntu OS.  Thanks..... Craig

Locking the grub-* packages has to be done in Ubuntu. So, let the Windows install complete... then reboot, select Ubuntu. Then let the Ubuntu installer complete - once complete it reboots automatically. Then boot into Ubuntu again, sign in. Now you can lock the packages.

---

### Post by Rubi1200 on 2011-02-02
Just to add to what bcbc already said; 

if you are using the regular version of Ubuntu, which has Gnome installed by default, then the menu is located on the top panel, so System > Administration > Synaptic

If you are using another desktop, such as KDE: ```
gksu synaptic
``` in the terminal

---

### Post by Craig H on 2011-02-02
> **Rubi1200 said:**
> Just to add to what bcbc already said; 

if you are using the regular version of Ubuntu, which has Gnome installed by default, then the menu is located on the top panel, so System > Administration > Synaptic

If you are using another desktop, such as KDE: ```
gksu synaptic
``` in the terminal

Got it..... thanks!  Will return to the forum if I have any problems.

---

### Post by Rubi1200 on 2011-02-03
No problem, let us know if everything works out for you.

---

### Post by Craig H on 2011-02-03
> **Rubi1200 said:**
> No problem, let us know if everything works out for you.

Installed smoothly and easily, then locked the grub-pc and grub-common packages w/o any problems......  Now it's just a matter of learning this new OS.  Like it so far..... very fast.  Thanks Guys!:guitar:  ):P

---

### Post by Rubi1200 on 2011-02-03
No problem, you are more than welcome :-)

Enjoy and don't forget to drop by and ask questions if you need more help.

---

