---
title: "Intel Blank Screen Help"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by Lyrica42 on 2010-07-13
Hi all.  I am a total noob at this.  I have tried everything I can to get Ubuntu on my Dell Optiplex sx270 desktop computer.  This of course has Intel chipsets all the way.  I am very aware of the Intel chipset problems with Lenny.  I have not gotten very far before hitting the blank screen wall every way I have tried to install Ubuntu (10.04 live cd blank screen every which way, installed 9.04 which worked, upgraded to 9.10 and got blank screen at reboot.)  I finally downloaded and burned Maverick and was able to get to desktop by using nomodeset (this or the i915.modeset=1 =0 values have not worked before.)  This is the first time this has worked on any version of Ubuntu for me.  I can boot into the desktop but it is in low graphics mode.  Can anyone spell out like for a 5 year old what to do next?  If I can get 10.10 to install in nomodeset, how do i then solve the problem once and for all?  If anyone can understand a frustrated noobs first post and can step by step help me fix this it would be appreciated.   If I can supply info, please paste the commands.  Thanks.

(btw, the only Debian based distro I have been able to get on this machine to stick is Dream Linux.)

Intel Corporation 82865G Integrated Graphics Controller

---

### Post by tommcd on 2010-07-13
First, disable all desktop effects:
Go to system > preferences > appearance. Click the visual effects tab. Set visual effects to None. 
If that does not help, then boot to recovery mode. If you do not see the grub menu on boot up, hit the **shift** key when the computer boots to see the grub menu, then select recovery mode.
When in recovery mode, run the option **xfix fix video** or whatever it says exactly. Then reboot.

If Maverick 10.10 does not fix the problem I am not sure what else you could do. Keep getting the updates though. Maverick is still in alpha, so there will be a lot of updates. Perhaps a kernel update may fix the problem when one comes along.
There was an article on installing the latest intel driver on 10.04 on How To Forge:
[http://howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)
However, that article mentions installing the 2.6.35.6 kernel. According to Phoronix, Maverick is using the 2.6.35 kernel, so that may not help you:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_maverick_netbook&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_maverick_netbook&num=1)
 To check the kernel version you are using, open a terminal (applications > accessories > terminal) and run:
```
uname -a
```
That Phoronix article mentions intel xf86-video-intel 2.11.0. The How to Forge article mentions intel 2.12.
Post the top part of the output of:
```
 aptitude show xserver-xorg-video-intel
```
This will show the version of the intel driver you are using.

And welcome to the Ubuntu forums!

---

### Post by Lyrica42 on 2010-07-13
Thank you for getting back to me.  I am so frustrated.  I will try what you said and see if that helps.  cheers!

---

### Post by tommcd on 2010-07-14
The only info I have seen relating to this issue involves using the **i915.modeset=0**or **1**, which you said you had tried. 
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Here is something that may help. It is based on Lucid, but I suppose you could try it on Maverick. Or go back to Lucid and try it if all else fails. It mentions the intel 8xx series of graphics cards:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Let me know if any of this helps.

---

### Post by Lyrica42 on 2010-07-15
The Glasen fix?  If I remember correctly I do not get the option of booting into safe graphics mode after install.  Is there any boot options I can enter that will take me to root?

---

### Post by tommcd on 2010-07-16
> **Lyrica42 said:**
> The Glasen fix?  If I remember correctly I do not get the option of booting into safe graphics mode after install.  Is there any boot options I can enter that will take me to root?
You can try booting to recovery mode. This will give you a root terminal with only minimal services running.

---

