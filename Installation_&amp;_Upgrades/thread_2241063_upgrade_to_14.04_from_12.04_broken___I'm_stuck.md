---
title: "upgrade to 14.04 from 12.04 broken   I'm stuck"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by btodd012 on 2014-08-23
I just got the notice that upgrade from 14.04 was available and I decided to wait a few weeks. Unfortunately I didn't wiat long enough I guess. 

I upgraded from the check for updates and selected the upgrade to 12.04. Everything went fine seemingly. I realized now that I goofed at the last step when it says "remove unneeded software" and I replied yes.

After the system restarted, I realized that I didn't have my older version to go back to. There are 2 choices  with 2 recovery modes.. I tried both and the same thing happens.

After restarting I get to the splash screen. I can l look at the top bar and see network info. As soon as I log in, I see a whit box at the top of the screen that says...
System Program problem detected. Do you want to report the problem now?  [OK] or [Cancel]

both options close the wind and the system sits that 14.04 spash screen with nothing on it except 14.04 LTS   and no activity anywhere. 

I did try the recovery option and I do get a menu. Not sure wht to do with any of it...

I'm stuck and don't know where to go from here....

thanks

---

### Post by kansasnoob on 2014-08-24
Hopefully you won't have to reinstall but if you do, and if you're running a dual-boot or a machine with multiple drives/partitions beware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

> the system sits that 14.04 spash screen with nothing on it except 14.04 LTS and no activity anywhere

At that screen if you right click on the desktop do you get the Change Desktop Background dialog? 

If yes you can click on that, then click on All Settings in the upper left hand corner, then click on Software & Updates, and then select Additional Drivers and let it search. That may offer a proprietary or recommended graphics driver which may help.

If not we'll have to possibly try booting with the ***nomodeset*** [boot parameter added to grub]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

---

### Post by btodd012 on 2014-08-24
> **kansasnoob said:**
> Hopefully you won't have to reinstall but if you do, and if you're running a dual-boot or a machine with multiple drives/partitions beware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)



At that screen if you right click on the desktop do you get the Change Desktop Background dialog? 

If yes you can click on that, then click on All Settings in the upper left hand corner, then click on Software & Updates, and then select Additional Drivers and let it search. That may offer a proprietary or recommended graphics driver which may help.

If not we'll have to possibly try booting with the ***nomodeset*** [boot parameter added to grub]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

Hi - thanks for answering. More info. My initial problems was System Program problem detected. I found a post that got me past that by removing the crash file in /var/crash and editing /etc/default/apport. 

Now - I am back to where you are talking about. When I re-boot I get to the GUI login prompt. I have a top menu bar that shows me clock, network and fery few other limited items. 

I cannot right click and get a menu. If I login in, I get the 14.04 spalsh screen - hear some disk activity then all is dead.

If I power off, I can start again and get to the boot menu and start Ubuntu in recovery mode. From there I can get a root console. I looked at various logs in /var/log and don't see any significant errors - I looked in dmesg, syslog, messages, kernel, and a few others that sound interesting.

The last thing that comes up in one log is "the Nvidea GE Force MX 440 with AGP8x GPU  is supported through the Nvidea 96.43.xx legacy drivers. Please visit nvidea.co/object/unix.html.

Then it says - the Nvidea driver will ignore this GPU. No Nvidea graphics adaptor found.

I'm not sure if this is killing me or not? I do get a graphics 14.04 LT screen. Why would the upgrade remove my legacy driver? Why wouldn't a generic one work?

Anyway - I can't right click or do anything on this screen. But - I can reboot in recovery mode and get a console.

I saw in one post that it suggested running sudo update-manager -d

I assume that will re-install, but I am not sure that it will help????

Not sure where to go from her at all.
thanks for helpinng

---

### Post by kansasnoob on 2014-08-24
> I saw in one post that it suggested running sudo update-manager -d

Yikes!!!!!!!!! Now that you're on Trusty that would upgrade you to 14.10 which is still in development until October and will only be supported for nine months thereafter.

---

### Post by Bashing-om on 2014-08-24
btodd012; Hello ;

Maybe a proprietary graphics driver that was broke in the release upgrade ?
get to a terminal
what results:
```

ubuntu-drivers list

```

Maybe just (re-)install the graphics driver ?

[INDENT][INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-24
According to [this thread]("http://ubuntuforums.org/showthread.php?t=2208523") it looks like 14.04 will not work with that graphics chip.

I assume that it did work with the original Precise kernel series and Xstack which you can still get if you reinstall Precise using the [archived 12.04.1 images]("http://old-releases.ubuntu.com/releases/12.04.1/"). While [the original Precise kernel series and Xstack are supported until April 2017]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support") they are only available using either the 12.04 or 12.04.1 images for installation. The 12.04.2, 12.04.3, and 12.04.4 images must NOT be used to avoid [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL"). And the 12.04.5 images use the Trusty kernel series and Xstack which you already know does not work.

---

### Post by btodd012 on 2014-08-25
> **kansasnoob said:**
> According to [this thread]("http://ubuntuforums.org/showthread.php?t=2208523") it looks like 14.04 will not work with that graphics chip.

I assume that it did work with the original Precise kernel series and Xstack which you can still get if you reinstall Precise using the [archived 12.04.1 images]("http://old-releases.ubuntu.com/releases/12.04.1/"). While [the original Precise kernel series and Xstack are supported until April 2017]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support") they are only available using either the 12.04 or 12.04.1 images for installation. The 12.04.2, 12.04.3, and 12.04.4 images must NOT be used to avoid [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL"). And the 12.04.5 images use the Trusty kernel series and Xstack which you already know does not work.


I am going to see if I can find another video card that isn't as bad... I know I have an ATI Radeon card in in a computer that I am junking. I'll see if that is supported. I assume if I plug in the card and reboot, 14.04 will detect the card and try and load driver?????

My problem is that I have lots of configured software that  I am upgrading from and it would be really hard to start over.... Apache, php, joomla, postfix, samba etc. I am pretty weak on the OS side and am not too sure of what to do beyond basics. If that seems like it would work, I'd appreciate an response.

My long term plan will be to get new PC and install 14.04 fresh once I have all my configurations working on the older machine.

I assume there is no apt-get downgrade.... and if I re-install 12.04 , I don't think it will pick up my data that is on my 14.04 installation?????
Thanks again for your help and if you can verify that what I am saying makes sense I will try that.

---

### Post by btodd012 on 2014-08-25
Thanks to kansasnoob and all others for info. I resolved my problem(s). The problem with the Nvidea GE Force MX440 was the killer. Once it was clear that this was the problem, I tried a newer video card and I am up and running in 14.04!!

Thanks again.

---

