---
title: "Installation or upgrade - mission impossible"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2011-05-18
I have tried to upgrade from ubuntu 10.10 to 11.04 but something failed and screwed my system...now I am using xubuntu that seems to work...

however, when trying to create a USB with the release...I did like always but did not succeed...

I tried with 3 computers (3 ubuntu and on this xubuntu) and 2 different USB keys...something must be wrong

I download the ISO image (that, as far as I know, is the same for laptops and desktops in 11.04) and open the startup disk creator

the only unusual thing is that the system sees my USB as both sb and sb1 (so I see the same information twice after launching the startup disk creator

Then the result (and failures) are several

a) the process gets stuck when finalising the disk
b) it reads that the codes do not correspond
c) it finishes the start-up disk but when I reboot the computer with the USB in I am asked to insert a device to start the installation (like there was no USB)

....

The only explanation is that when the upgrade failed it affected the start up disk creator that cannot create disks anymore...

any ideas?

---

### Post by tommcd on 2011-05-19
> **abelito8 said:**
> 
The only explanation is that when the upgrade failed it affected the start up disk creator that cannot create disks anymore...

You could try using Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
I always do clean installs of Ubuntu. I never do dist-upgrades. Clean installs are the best way to avoid problems like this.

---

### Post by abelito8 on 2011-05-19
I agree, I also never do release updates but this time something went wrong with the USB
thank you for the advice, I've downloaded Unetbotin and will try tomorrow...hope everything will go ok

---

### Post by MBybee on 2011-05-19
> **abelito8 said:**
> 
I download the ISO image (that, as far as I know, is the same for laptops and desktops in 11.04) and open the startup disk creator

the only unusual thing is that the system sees my USB as both sb and sb1 (so I see the same information twice after launching the startup disk creator



If you're seeing both, you can attempt to choose the 'erase' option. The destination you want, otherwise, is the one without the number IIRC. That's the 'device'. The other is the 'partition'.

I made several this last couple weeks from 11.04, using a couple different ISOs to two different USB devices, and it seemed to work well.

---

