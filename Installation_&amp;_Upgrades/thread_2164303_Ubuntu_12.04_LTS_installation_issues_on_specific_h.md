---
title: "Ubuntu 12.04 LTS installation issues on specific hardware"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by hMB7sdx on 2013-07-31
Hi,

I'm a relatively new user and I am facing some issues with the installation of Ubuntu 12.04 LTS on a desktop, if someone could help me out that would be great. Some information -
 
The ISO image - [COLOR=#000000] [/COLOR][ubuntu-12.04.2-desktop-i386.iso]("http://releases.ubuntu.com/precise/ubuntu-12.04.2-desktop-i386.iso")[COLOR=#000000]     [/COLOR]
I've done the installation on different hardware configurations. It has failed on three different computers with identical hardware configuration. Funny thing is I tired installing Linux Mint 13 instead it gets stuck at exactly the same point, after I hit continue at the "Who Are You?" screen. The continue button changes color, the username doesn't have capital letters or spaces. Tried to remove ubiquity slideshow before installing, no luck. MD5 sum matched so its not that...

The configuration on which it fails - IBM Think Centre, Intel Pentium IV 530 processor, 3.00 GHz Frequency, 800 MHz FSB, Intel 915 Chipset Motherboard, 1GB DDR2 RAM, 80 GB SATA HARD DISK. Philips 16x 48x DVD R DVD Drive, Intel 915G video card.

Found this - [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/950952](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/950952)
The description -  "[COLOR=#333333][FONT=Ubuntu Mono]Your name, Your computer's name, Pick a username, and Confirm your password all have green ticks. The Installer doesn't hang until you press the "continue" button. Waiting for the progress bar along the bottom to complete before pressing continue also results in a freeze." [/FONT][/COLOR]seems to match perfectly with the problem I'm facing. 

Hope I can get some help regarding this.

---

### Post by grahammechanical on 2013-07-31
I do not know if this will help or not. There are three ways to launch the installer. Try a different way.

1) Allow the disk to run and wait until is shows a TRY - INSTALL dialog - click INSTALL.
2) Allow the disk to run until it shows a TRY - INSTALL dialog - click TRY and at the live session desktop click the Install icon.
3) At the first purple screen press Enter. At the second (language) screen press English or select a language and press Enter. At the underlying screen (TRY - INSTALL) select install.

I have found when testing development ISO images that sometimes an install will crash. In my case at the copying files section claming that there is not enough disk space, but when I try installing through one of the other methods, the install completes.

Regards.

---

### Post by gordintoronto on 2013-07-31
Did you choose to use the entire hard drive? I once messed up an install by choosing a partition size in MB when I meant GB...

---

### Post by hMB7sdx on 2013-08-02
Thank you for your replies. grahammechanical, tried all three, no luck. gordintoronto, yes I made sure to not overlook this, no luck.

So I was just playing around and found a way to get it done but I'm not sure if its a healthy practice. I pulled out the hard disk from the troublesome hardware configuration, then put it in a different combination of hardware that I know Ubuntu installs on. After installing it, I transferred back the hard disk onto the troublesome hardware, worked like a charm. Do you think I will have any problems in the future because I did this?

---

### Post by hMB7sdx on 2013-08-02
Also, do you know if I can follow the same principle for Windows? Someone told me its not possible to do this with Windows.

---

### Post by gordintoronto on 2013-08-02
In my experience, something might not be quite right with different wireless adapters, or video cards from different families. (Intel, Nvidia, ATI/AMD) Or perhaps it was something else when I tried it. (This was installing [really installing] onto a flash drive, and trying to use it on different computers.) The difficulties showed up right away.

I can't comment on Windows, other than to mention that I tried to install the 8.1 Preview onto a flash drive, and Windows absolutely would not allow it.

---

