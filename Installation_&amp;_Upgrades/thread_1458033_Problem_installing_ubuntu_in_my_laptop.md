---
title: "Problem installing ubuntu in my laptop"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by ace_ventura on 2010-04-19
hello guys. i am very 1st time user of Linux, installed ubuntu in my desktop, working fine. now i tried to install ubuntu in my Asus laptop to dual boot along with windows 7, but couldnt go further. installed it, then it asks to reboot. when it reboots, i select ubuntu from boot menu, it says finishing installation, but after that, blank screen. i tried every other options pressing esc, but same story, blank screen. as i am completely new to Linux, i am lost. what am i doing wrong?
the laptop is Asus K52F which has intel onboard graphics Intel Graphics Media Accelerator HD. is this causing the problem?
i desperately need help.

---

### Post by ace_ventura on 2010-04-19
no help yet? i tried every possible thing given in this forum but no solution yet. my desktop is running fine, but my problem is with the laptop.
thnx.

---

### Post by nexes128 on 2010-04-19
Can you boot into recovery mode?

---

### Post by 2hot6ft2 on 2010-04-19
> **ace_ventura said:**
> i **tried to install ubuntu** in my Asus laptop to dual boot along with windows 7, **but couldnt go further. installed it**, then it asks to reboot. **when it reboots, i select ubuntu from boot menu, it says finishing installation.**
That doesn't sound right at all.
Did the installation fail or complete before the reboot?
It should not say finishing the install after the reboot.
I would say a re-installation was in order.

---

### Post by tommcd on 2010-04-20
> **ace_ventura said:**
> ... when it reboots, i select ubuntu from boot menu, it says finishing installation, but after that, blank screen. ...
Yes, as 2hot6ft2 said, there is definitely something wrong there. When you reboot after the install it should just  reboot into your newly installed Ubuntu desktop.
 (There are some linux distros that go through some post install configuration after you first reboot, but Ubuntu is not one of them).
Did you check your Ubuntu install CD for defects after you burned it? If not, then you need to do that now. This is always the first thing you should do, especially when you end up with a failed install like this.
Boot up your Ubuntu CD. On the main menu there is an option to "check the CD for defects". Choose that and let it run. It will take a couple of minutes to run. If it passes without errors, then the CD is good. 
Write back if you need more help with this.

---

### Post by ace_ventura on 2010-04-20
thnx guys for the response.
@nexes128...it does the same in recovery mode, blank scree.
@2hot6ft2 & tommcd....i have already done 3/4 time install & uninstall. the CD is good, it did install in my desktop perfectly, though i am using ubuntustudio in my desktop now.
with my laptop, i tried the Cd, also tried the windows installer from ubuntu site, result is same.
what i found out today is that i can hear the sound of ubuntu starting, but nothing on the screen, not even the ubuntu startup logo. is it anything wrong with the graphics?
my laptop is i5 with intel graphics media accelerator & 64bit windows 7 installed. 
thnx againg for the response.

---

### Post by tommcd on 2010-04-20
So did you run the option to *check the CD for defects* when you first boot the Ubuntu install CD?
This is important. The install may appear to go off ok without a hitch. It is only after you reboot that you find that you have all sorts of problems. Even if you manage to install Ubuntu from the CD, and it appears to install ok, that does not rule out the possibility  that one or more files on the install CD may be corrupt. Checking the CD for defects (which checks each and every file on the CD) is the only way to assure that the CD is good.

---

### Post by ace_ventura on 2010-04-24
i tried every suggestions given to me, tried the recovery mode, no help. checked the CD for defects, it does the same. when i click on to check for defects, the screen goes blank, nothing happens. i even tried to install it from USB using UNetbootin, it starts then the screen goes blank. is it happening because of any conflicts with graphics? my desktop is running fine with ubuntu, just the laptop i am having problem with, any more suggestions pls?

---

### Post by tommcd on 2010-04-25
> i have already done 3/4 time install & uninstall. the CD is good, it did install in my desktop perfectly ...
Can you run the "check CD for defects" option then from your desktop computer then? Just boot from the CD on your desktop computer and run the check. This will not make any changes at all to your desktop system.
> **ace_ventura said:**
> i tried every suggestions given to me, tried the recovery mode, no help. checked the CD for defects, it does the same. when i click on to check for defects, the screen goes blank, nothing happens. ...
This could possibly be a problem with your graphics card. Intel graphics are pretty well supported in linux though. I would think that your intel graphics *should* just work fine; but you never know...
To rule out a graphics related problem, I would try installing from the alternate CD. This is a text based installer that should avoid any graphics related problems:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
Here is a guide to using the alternate install CD. It is based on Hardy 8.04 LTS, but the procedure is essentially the same for the 9.10 alternate CD:
[http://members.iinet.net.au/~herman546/p3.html](http://members.iinet.net.au/~herman546/p3.html)
Are you trying to install 32bit or 64bit Ubuntu on the problematic Asus laptop? I would use the 32bit alternate install CD for the most fail safe installation.
And be sure to *check the alternate install CD for defects*!!
The alternate CD is not hard to use. It is essentially the same as the desktop CD, but without the graphical desktop. I always use the alternate install CD to install Ubuntu.

If all else fails, note that Ubuntu 10.04 LTS will be available April 29th. There may be some quirky (for lack of a more technical term) on the Asus laptop that could be better supported with the newer kernel that will be on 10.04.

**BIG FAT EDIT**:
I just found this! According to this your Asus laptop uses the Intel HM55 chipset:
[http://reviews.cnet.com/laptops/asus-k52f-a1-core/4507-3121_7-33971419.html?tag=mncolBtm;rnav](http://reviews.cnet.com/laptops/asus-k52f-a1-core/4507-3121_7-33971419.html?tag=mncolBtm;rnav)
This bug report on Launchpad describes your exact problem:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/518938](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/518938)
And here is quote from post #6 on the bug report:
> Installing the newest kernel from your 1st link has enabled the boot to complete. Xorg and all.
So either try that kernel on 9.10, or (probably a better and easier option) just wait for 10.04 to come out on Thursday.

Hope this helps!

---

### Post by ace_ventura on 2010-04-30
hey Tommcd'

last night i successfully installed the latest ubuntu on my laptop without any problem. 
used the windows installer rather than burning ISO.
THNX VERY MUCH for the support.

---

