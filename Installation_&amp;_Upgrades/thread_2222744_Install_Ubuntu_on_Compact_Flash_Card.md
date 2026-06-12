---
title: "Install Ubuntu on Compact Flash Card"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by gunna999 on 2014-05-07
Is there a version of ubuntu available that I can install onto a 4gb Compact Flash Card?

---

### Post by sammiev on 2014-05-07
> **gunna999 said:**
> Is there a version of ubuntu available that I can install onto a 4gb Compact Flash Card?

I have installed lubuntu to a 16GB USB and it works rather good and updates well ( a little slow ). If you just want a boot-able live ISO then yes 4GB is good for testing different OS.

---

### Post by papibe on 2014-05-08
Hi gunna999. Welcome to the forum ):P

There's no version for a particular type of media. Ubuntu can be installed on a flash card just as like in a HD. You may need to fine tune your installation later, but that would depend on the rest of the hardware.

Another concern you may have is to choose the right version of Ubuntu that fit your current hardware.

What kind of computer are you going to install it on?
Is it able to boot from a flash card?
How much RAM do you have?

Regards.

---

### Post by gunna999 on 2014-05-08
Hi papibe,

Im not new to the forum. I lost my previous beans & profile when this forum changed a while back. Ive been using ubuntu since 7.04 after abandoning windows. I've been very happy with ubuntu & have various versions running on many pcs.

The reason I ask about the CF installation is that I want to build a NAS to replace the FreeNas installation I have on a shuttle pc. The 0.722 version of FreeNas Im using is no longer supported. Its been causing me a lot of grief, and I can't rectify the problem. Its a raid 5 setup with 3 x 2 TB drives, Ive lost my entire collection of media, I'm guessing I have a corrupt GPT or a dead drive thats irrecoverable even though I've tried to resync unsuccessfully. Now its just caught up in a loop, rebooting shutting down rebooting.

The shuttle pc has a 4yo VIA nano motherboard with an embedded 1.8Ghz processor. It has 4gb RAM. The FreeNas is installed onto a 4Gb CF. It sees the CF as just another HDD. My idea is to replace the FreeNas (based on FreeBSD) with ubuntu if possible. I know there are other linux distros that would probably work on the 4Gb CF but I would prefer to use ubuntu.

So I guess my only options are to buy a bigger capacity CF card and install ubuntu to it, or perhaps install ubuntu to a bootable usb thumb drive.

Cheers, m8

---

### Post by papibe on 2014-05-08
Ouch! Sorry to hear that.

I have a 10.04 server running on a 4GB partition. So far it is using just 2.1Gb. So yes, it is possible. You may not be able to install lots and lots of packages, but I guess for a NAS you would need just ssh, nfs, and samba.

Here's the hard disc requirements for 14.04: [System Requirements]("https://help.ubuntu.com/14.04/serverguide/preparing-to-install.html#system-requirements").

Hope it helps.
Regards.

P.S.: one of the thing that eats a lot of space (inodes actually) is the accumulation of linux-headers packages. I'd recommend cleaning the 'house' often.

---

### Post by gunna999 on 2014-05-08
You're right, just needs a few services, mainly samba.

---

### Post by sudodus on 2014-05-09
If you avoid a graphical desktop environment, just run the Ubuntu server, it should fit into a 4 GB flash memory without problems. You have space enough for a simple window manager like fluxbox or openbox, but a server should be as clean as possible from eye-candy.

This should be possible with any version of ***Ubuntu Server***. 10.04 LTS is getting old, 12.04 LTS is well polished, and 14.04 LTS is new, not yet debugged and polished. All of them have 5 years support. 10.04 means released year 2010 - month 04 (April 2010) etc.

You can also build the server from Ubuntu ***mini.iso*** by adding the packages you want.

---

