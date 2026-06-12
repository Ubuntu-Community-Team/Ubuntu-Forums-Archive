---
title: "Lubuntu 12.10 new install will not reboot"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by cblxub on 2012-12-25
hello.

I have installed lubuntu 12.10  32 bit  on  a new  Netbook:
Acer Aspire One 257-13473  w/   dual core intel atom n550.   with 2G RAM.  and it is dual boot.

everything is working fantastic  except two issues (that I think might br related.)

**1. **_ Reboot does not work._
I installed twice but reboot hangs with a blank screen,
power off and logging out are fine, when I cold start it up GRUB works  find I can log into Lubuntu 12.10  and my small windows 7 starter partition fine.

**2.** I either don't  have or _can't find a swap partition_ for lubuntu.
In fact when I start up I get a message says:

"  /dev/mapper/cryptswap1   is not present yet.. wait or...."

I am presuming that the install failed to complete, maybe because the machine won't reboot
I am installing from a pen drive, with the encrypted home folder option ticked.
I have already:    sudo apt-get update && sudo apt-get upgrade
installed and ran progams... everything is working great except these to issues,.

---

### Post by Comodín on 2013-01-20
I seem to have a [**similar problem**]("http://ubuntuforums.org/showthread.php?t=2106597"). Have you already found a solution?

---

### Post by cblxub on 2013-02-25
I have not found a solution.
the swap part.   is there.
The (gui) Disk Tool lists  the partition " /dev/mapper/cryptswap "  as  a device.
I will still get message and prompt from time to time when I boot up.
Next time it happens I will just report it as a bug.

---

### Post by JLeon85 on 2013-02-25
I used GParted to make a swap drive on Lubuntu and it seems to be working fine. 

As for the restart issue, maybe you could try Boot Repair? 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cblxub on 2013-03-12
well, i had a grub error after logging into my small windows 7 partition, since i never use windows on this machine anyway,
i did a total reinstall of lubuntu 12.10... no more dual boot.
since the reinstall - the swap is working fine,  and the restart works, no hanging.

---

