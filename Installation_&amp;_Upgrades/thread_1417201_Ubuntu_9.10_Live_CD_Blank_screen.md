---
title: "Ubuntu 9.10 Live CD Blank screen"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by talhaguy on 2010-02-27
Hello everyone,

I recently got a new laptop and am trying to install Ubuntu 9.10 on it. I have installed it on my two other computers without any problems, but there seems to be a hitch with my new one.

So I boot up using the live CD and then am presented with the option to test Ubuntu or install it. If I choose either of these the screen just goes blank. If I go with the first option of testing Ubuntu before installing, I can hear the intro drumbeats but the screen is still blank.

I have searched in some forums and tried some people's advice, like pressing Ctrl+Alt+- or Ctrl+Alt+Backspace to change the resolution and restart X windows, respectivley. But it doesn't seem to work.

I'll list my laptops specs just in case my problem has anything to do with them:

MSi
Windows 7 Home Premium 32 bit
Intel Core i3 M 330 2.13GHz
4GB DDR3 RAM
Intel Graphics Media Accelerator HD

Any help would be appreciated as I really want to use Ubuntu!

Thanks,
Talha

---

### Post by talhaguy on 2010-02-27
Just an update.

I burned a new Live CD, but I still have the same issue.

---

### Post by jswoods7 on 2010-02-27
I would give a go at the 'alternate cd' (does not have the live option, and usually works better with laptops).

---

### Post by talhaguy on 2010-02-27
Will I still be able to keep Windows 7 if I use the alternate CD? If you have any links to instructions could you post them? I really don't want to screw anything up. Thanks.

---

### Post by jswoods7 on 2010-02-27
The alternate installation is essentially the same as the Live CD install, things will just look a little different. There will be the same level of risk involved in overwriting or misconfiguring your system to the point of rendering your Windows 7 system unusable, so I'd recommend a backup either way. With the alternate install, you will be presented with the same options regarding the partitions you will be using for the new system, just like the Live CD install.

[https://help.ubuntu.com/9.10/installation-guide/i386/boot-installer.html](https://help.ubuntu.com/9.10/installation-guide/i386/boot-installer.html)

---

### Post by talhaguy on 2010-02-27
So in the middle of my alternate CD installation the DHCP network authentication failed. Should I be worried about this right now? Also, I cannot use the unallocated space on my disk that I set up to install Ubuntu on. It just says unusable. I could use the Windows NTFS partitions, but I want to keep those. Any suggestions?

This was a piece of cake to install on my old laptop...

---

### Post by bmuluu on 2010-02-27
DHCP network authentication should not cause any problems.
I don't see why the unused space should not be usable, isn't there any option for formatting that space?

---

### Post by talhaguy on 2010-02-27
No, there is no option to format it. I am going to try to format it in Windows 7 and then try to install Ubuntu again.

---

### Post by Frogs Hair on 2010-02-27
Hi,

I installed Ubuntu this week and was losing monitor signal at boot after 4 or 5 restarts
I was able to get Ubuntu running . The problem was resolved by updating the video card
driver. There was no problem with Ubuntu or the install , but like you I could here it but
not see it.

---

### Post by talhaguy on 2010-02-27
A video problem seems to make sense, thanks!

Just to clarify, should I be formatting the partition I want to install Ubuntu on to NTFS or FAT? Or should be leaving it unallocated? And should I be doing this through Window's partition manager or the one that comes with the alternate CD?

I think the problem I was having before, about the unusable disk space, had something to do with more than 4 primary partitions.

---

### Post by darkod on 2010-02-27
> **talhaguy said:**
> A video problem seems to make sense, thanks!

Just to clarify, should I be formatting the partition I want to install Ubuntu on to NTFS or FAT? Or should be leaving it unallocated? And should I be doing this through Window's partition manager or the one that comes with the alternate CD?

I think the problem I was having before, about the unusable disk space, had something to do with more than 4 primary partitions.

Yes, you can't have more than 4 partitions, either all primary or primary + extended.
The blank screen issue is usually video driver related.
Do NOT format any partitions for ubuntu in windows, it can only format as ntfs or fat32 and ubuntu uses neither to install on them.
You should be able to create partitions fron unallocated space using the alternate cd, as long as you already don't have 4 of them.
But if it was the video issue stopping you from using the standard live cd, boot it again and at the main menu hit F4 first for advanced options. Select Safe Graphics, then Try Ubuntu after that. That should load the live desktop OK.
You can click on the Install icon on the desktop to start the install process while in safe graphics mode if the GUI installer is easier for you.

---

