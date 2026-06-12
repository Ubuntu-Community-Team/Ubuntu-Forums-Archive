---
title: "Ubuntu 11.04 doesn't like me"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by kecskepasztor on 2011-04-30
[FONT=Arial][SIZE=3]Hi.

Today I decided to upgrade my ubuntu 10.10 to Ubuntu 11.04, so I did it. but after I restarted it, it went to hell. After it starts boot comes the standar purpleish screen but that flashes out and comes a black screen that flashes a few times, then comes a black screen with a text:

> * Cheking battery state... [OK]
* Starting CUPS printing spooler/server [OK]
* Stopping System V runlevel compatibility [OK]
fsck from util-linux-ng 2.17.2
/dev/sda2: clean, 224483/24420352 file, 82407519/9765808 block
* Starting configure network device [OK]
.
.(it continous like this)
.
.
* Stopping automatic crash report generation [fail]
.
.(again continouing)
.
* Starting Userspace bootsplash [OK]
* Stopping Userspace bootsplash [OK]

This is the message I got every time I restarted the laptop(
[/SIZE][/FONT][FONT=Arial][SIZE=3]Toshiba Satellite L670-16M[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Intel  Core i3-350M, 4GB, DDR3, 500GB, Ati Radeon HD5650, WEBCAM, Bluetooth,  Kártyaolvasó, 17,3", 1600x900, Win 7 HP, HDMI, eSATA, 2xUSB, WLAN,  10/100Mb, AUDIO, DVD Super Multi, 2,8Kg, LED, Black, 6cella, D-SUB,  4400mAh)[/SIZE][/FONT]


[FONT=Arial][SIZE=3]I would apreciate if someone could help me...
[/SIZE][/FONT]

---

### Post by tigrita on 2011-04-30
I am having this issue too. I was trying to upgrade ubuntu to the newest version and everything was working perfectly until the next day when I turned on the computer and got an error similar to yours. I am trying to installing ubuntu again with the original cd, but have no success because it stays stuck in the "Preparing to install Ubutu" window. I only can use ubuntu in try out mode.

---

### Post by kecskepasztor on 2011-04-30
I managed to open the GRUB there I choose Older Linux versions, there I choose the most recent one, and it booted me the 11.04. After that I tried the normal way,but it just gave me a normal empty black screen.

---

### Post by PopeZaphod on 2011-05-07
Yeah, I have done something horrible to my netbook and it's stopping at this point as well.  Can't get it to recognize my USB drive to try reinstalling.  ><

---

### Post by wilee-nilee on 2011-05-07
To get the help a personal thread is needed, with a header that is relevant, and the graphic video card identified, it seems to be a driver needed in the first post. You can just post the out put of 
lspci 
in the terminal

Possible getting in strategies in safe mode.....

A safe boot from the second kernel in the grub menu, or a edit of the quiet splash to nomodeset at the grub menu by hitting e on the first kernel in the grub menu, ctrl-x to boot, login then startx to get to the desktop.

---

### Post by tgguadarrama on 2011-05-07
I already installed, ubuntu 11.04 using the option install with win7, the process was successful, when the laptop boot, the grub menu appears, then I chose "start with windows 7" option, the grub menu refresh. In ubuntu I can see the files of win7. What is wrong? And How can fix it?

---

### Post by a1r on 2011-05-11
Had the same issue too (boot stuck after "Stopping bootsplash" message). Seems nvidia driver is malfunctioning. I've booted in safe mode and deactivated nvidia driver. Reboot went ok.

PS I've installed "recommended" version of nvidia driver.

PPS I have nvidia 9800gtx video card.

---

### Post by Vallard on 2011-06-03
> **kecskepasztor said:**
> [FONT=Arial][SIZE=3]Hi.

Today I decided to upgrade my ubuntu 10.10 to Ubuntu 11.04, so I did it. but after I restarted it, it went to hell. After it starts boot comes the standar purpleish screen but that flashes out and comes a black screen that flashes a few times, then comes a black screen with a text:

This is the message I got every time I restarted the laptop(
[/SIZE][/FONT][FONT=Arial][SIZE=3]Toshiba Satellite L670-16M[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Intel  Core i3-350M, 4GB, DDR3, 500GB, Ati Radeon HD5650, WEBCAM, Bluetooth,  Kártyaolvasó, 17,3", 1600x900, Win 7 HP, HDMI, eSATA, 2xUSB, WLAN,  10/100Mb, AUDIO, DVD Super Multi, 2,8Kg, LED, Black, 6cella, D-SUB,  4400mAh)[/SIZE][/FONT]


[FONT=Arial][SIZE=3]I would apreciate if someone could help me...
[/SIZE][/FONT]

I was using Ubuntu 11.04 normally, but then I updated and I get the same(or looks like the same). And I can't start Ubuntu. Why? I just updated by the Update manager and get this error...

Can anyone help? *posting by express gate*

---

### Post by Vallard on 2011-06-03
Posting more about the problem:

I BELIEVE it is only something with the graphics, so I installed Ubuntu 11.04 I received an error screen with the jockey-gtk stopped working. With that my screen was slow, as a kind of graphical slowdown. I installed the ATI driver (the aditional drivers) and it did not work, I downloaded the driver from ATI for this site and did not work either. I decided to use it anyway and over time (and I gain more experience) to get. Then upgraded the system. And relauch, these screens began exactly as quoted on the topic that I link.

I have access to the terminal by ctrl+alt+f1 on that fsck screen, so I can make changes and everything (because I'm the root). The problem is that I am without access to liveCD so far ... and I'm really not an expert user to do everything by terminal yet (so I came to ask for help).

When I tried to startx from the terminal before, the PC said it could not connect to the X and quit.

With the problem more detailed, I think it might be easier that we find a solution.
For the record, the specs of my PC (which can help, do not know)
4TB HD
6GB ram
5850HD Black Edition
i7 930

Thank you for your attention.

---

### Post by brunolopes446 on 2012-02-23
> **a1r said:**
> Had the same issue too (boot stuck after "Stopping bootsplash" message). Seems nvidia driver is malfunctioning. I've booted in safe mode and deactivated nvidia driver. Reboot went ok.

PS I've installed "recommended" version of nvidia driver.

PPS I have nvidia 9800gtx video card.

If it is a problem with nvidia drivers, as I had, try this link:
[http://ubuntuforums.org/showthread.php?t=1556967](http://ubuntuforums.org/showthread.php?t=1556967)

---

### Post by LinuxFan999 on 2012-02-23
> **Vallard said:**
> I was using Ubuntu 11.04 normally, but then I updated and I get the same(or looks like the same). And I can't start Ubuntu. Why?** I just updated by the Update manager** and get this error...

Can anyone help? *posting by express gate*
Upgrading Ubuntu through the update manager is not recommended and can break your installation. You will need to reinstall Ubuntu using a CD containing Ubuntu 11.04. Make sure to back up your data first.

---

