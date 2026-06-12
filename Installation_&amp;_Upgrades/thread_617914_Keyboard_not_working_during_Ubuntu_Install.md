---
title: "Keyboard not working during Ubuntu Install"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by theluddite on 2007-11-19
When I try to boot Kubuntu 7.1 (or Ubuntu 7.1 or SUSE 10.3) from a live CD, my keyboard doesn't work at the main installation page.  I've got a Dell Dimension 9200; Intel Core 2, x86_64.  I've tried using the alternate .iso image; I've checked the hash with md5sum; I've burnt the CD at the lowest speed (4x); and I've even tried installing the i386 version and encountered the same problem.  My keyboard is usb and there's no PS/2 port.  If the installation continues automatically, the installation hangs at "*  Running local boot scripts (/etc/rc.local)  [OK]".  Does anyone know what the problem is?

---

### Post by theluddite on 2007-11-20
OK.  So I reinstalled Vista over Ubuntu, formatting the entire drive.  Then I burnt a new .iso image of Kubuntu 7.1 (the ninth CD I've wasted during this process) using InfraRecorder (at the slowest possible speed) and still... The same f*ing problem!!!  It can't be a problem with the image, and it can't be a problem with the disk right?  So what's the f*ing problem?  I liked ubuntu when I had it installed on this system before, but it looks like I'll have to rely on windoze if I can't get any linux distro to install.

---

### Post by confused57 on 2007-11-20
There might be a setting for USB Legacy in your bios setup that you could try...I've seen this help others with a USB mouse.

---

### Post by theluddite on 2007-11-22
Well, it seems like my problem was with the Gutsy live CD.  For whatever reason, my hardware didn't like Ubuntu or Kubuntu 7.1 or Suse 10.3 but worked with Ubuntu 7.04 and Kubuntu 6.06.

I have a Dell Intel Core 2 Duo (4MB L2 Cache,2.4GHz,1066 FSB), 2GB Dual Channel DDR2 SDRAM,  300GB Serial ATA Hard Drive, 128MB ATI Radeon X1300.

It seems that this was specifically a problem with the live CD.  I had Feisty previously installed on this system and upgraded to Gutsy without a problem.

---

### Post by doc75 on 2008-01-06
Hello,

I have a Dell Dimension 6200 and I successfully installed gutsy on a second partition about 2 monthes ago.
But yesterday I tried again and the first panel of the boot CD (where you can choose language for example), the keyboard refuses to do anything.....
I really don't understand why it worked a couple of weeks ago and not anymore.
The feisty live cd is still working fine.....

Any idea ?

---

### Post by theluddite on 2008-01-06
I'd try the alternate CD first.  If that doesn't work, I'd try switching your usb keyboard with a ps2.  If neither of those work, I'd try what I did and install Fiesty and then upgrade to Gutsy.

---

### Post by parisj13 on 2008-01-06
It appears that I have a similiar problem.  I have a new Dell and it is currently "infected" with Vista.  I'm trying to put Ubuntu 7.10 Server on it, but can't get past the first screen because my USB Keyboard isn't working.  I only have USB ports.  Any idea how I can get the USB keyboard to work?:confused:

---

### Post by Paul Hoogsteder on 2008-01-10
> **parisj13 said:**
> It appears that I have a similiar problem.  I have a new Dell and it is currently "infected" with Vista.  I'm trying to put Ubuntu 7.10 Server on it, but can't get past the first screen because my USB Keyboard isn't working.  I only have USB ports.  Any idea how I can get the USB keyboard to work?:confused:

Found this workaround (on a Mandriva-related site if I remember correctly), which worked for me with a number of recent Ubuntu (text-based) cd's on a Dell Optiplex GX620:
Just after the Dell bios screen, keep the shift key down. A prompt will come up asking you for graphics mode (no thanks), then at the command line type "linux" and enter.
This will get you directly to the installer.

Please post whether this works for you - I've spend a lot of time talking with Dell technical support without any results...

regards,

Paul.

---

### Post by doc75 on 2008-01-10
Hello,

I just tried the workaround mentioned by Paul, and it seems that I could launch the Ubuntu CD in command line mode.
I did not check the re-install since I did finally an upgrade from Feisty to Gutsy.
Thanks for the tip.

Bye

---

### Post by 4ms on 2008-02-14
Hello,

I also have this keyboard problem.  I will try holding down the shift key tomorrow.  

I've been trying everything - various distros - desktop, server, jeos, alt and on everyon e of them there is no input accepted from the keyboard on the first screen where you dan hit "install on HD" or whatever.

It's frustrating because if I could just kickstart that one item, them if might keep doing.

I have tried other keyboard also.  In all cases, they work on setup / select boot menu (from bios) and then do not work at all.

I did get freespire 2.0.8 installed with no problem, so I can only assume that somethingcommon across all ofe ibutustart scritps is unhappy.

I welcome any thoughts as to how to get gutsy on my skipjakc-feisty fresspire.  I even tried /cdrom/cdromupgrade, as suggested  - but upgrade is not supported from skipjack...

I much appreciate any help,
joseph

---

### Post by 4ms on 2008-02-15
thank you Thank You THANK YOU
holding down the shift key WORKS!
much thanks,
joseph

---

### Post by jbindel on 2008-03-20
> **Paul Hoogsteder said:**
> 
Just after the Dell bios screen, keep the shift key down. A prompt will come up asking you for graphics mode (no thanks), then at the command line type "linux" and enter.
This will get you directly to the installer.
This worked perfectly on a Optiplex GX620 with latest bios (A11).  Thank you for sharing this.

---

