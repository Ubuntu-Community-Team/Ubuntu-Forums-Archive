---
title: "Can't install any version of Linux"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by heiowge on 2008-02-26
Can't install Kubuntu (my preference).

I have a Sony Vaio Fx702 laptop.

256MB Ram
1.2 GHZ Athlon Processor (1400+)
20GB HD
2 x USB 1.1

CD/DVD drive very problematic.
I have an External USB 2.0 DVDRW drive that I can connect via Belkin USB 2.0 PCMCIA card.

Tried various flavours of Linux before coming to the conclusion that I didn't have enough Ram.  So I've downloaded Kubuntu 6.06 and Ubuntu 7.04 (both 256 MB or less required).

Burned to CD, set BIOS to boot from CD, No Operating System Found.

Repeated several times.  Put files on a flash drive.  Managed to get system to load the install menu for the programs (but not the OS, as it required to boot live).

Discs booted on fine wife's PC (WinXP).

My problem is that the only options the BIOS gives for boot are:

HD, CD-ROM (the internal one only), Floppy, Network, ATAPI removable, IDE Removable and User.

It doesn't give the option of USB or other CD drives.

I either need a method to boot without using the CD or a way to get it to boot from the external DVD drive or a flavour of linux that will install while windows XP runs.

Any help?

---

### Post by heiowge on 2008-02-26
Or another option - a way to boot from another machine.

I have access to a Dell PC (another 256mb Ram machine unfortunately), and an Asus eeePC 2G surf running WinXP.

---

### Post by jken146 on 2008-02-26
There are some options here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by heiowge on 2008-02-26
Cheers.  Gives me a few ideas....

---

### Post by heiowge on 2008-02-27
Well it took long enough, but I'm now on Kubuntu 7.04 Feisty, installed over the net.  I used that link, and installed using wubi installer.

Took about 5 hours, but it's done now.

Cheers.

Only issue is that it's installed to a 10GB partition of my hd.  The rest is windowsXP.

Is there a way to get rid of the dual boot, and the winXP partition, and thus free up the other 10GB of hd space for Kubuntu?

---

### Post by jhenager on 2008-02-27
You can use Gparted to remove the xp partition. Note that Gparted only works on unmounted volumes. This means if you are booting off the hard disk, it is mounted, and you can't modify it. Create a Gparted CD-ROM and boot from that.
If that is not possible, delete all partitions using something like Aefdisk and reinstall Kubuntu again. Also, why not go with Gutsy?

---

### Post by heiowge on 2008-02-28
Usually good advice.  Problems are:

Gutsy needs too much ram (only have 256MB), so I had to go with feisty.

CD-Rom is a problem as it's broken.

I don't want to wipe the HD and start over as it took 4 weeks to get any version of linux to work on the laptop, and then only went on with a wubi install through windows.

As for unmounted volumes... huh?  Major linux newbie here!  Sorry not a clue.

---

### Post by jken146 on 2008-02-28
You don't need 256 MB of RAM to run Gutsy.  Use a lighter WM such as XFCE and you'll be laughing.

A mounted partition is one that is in use by the operating system.  In the terminal, you can find out which partitions are mounted by typing ```
mount
```  In gparted, you can unmount partitions by right clicking on them and selecting "unmount".

---

### Post by heiowge on 2008-02-28
I considered Xubuntu, but I wanted the KDE desktop that Kubuntu offered rather than the xfce or Xubuntu (just a preference).  Gutsy Kubntu needs over 300MB ram, wherease Feisty needs 256.

I'll look at Gparted later (laptop is packed up for work at the moment - on Wifes XP machine now) and see if I can sort it all.

If I unmount windows, will it affect Kubuntu? - it was installed using wubi from an XP partition and I heard it runs with windows in the background (true or not I don't know, but it gives me pause.)

---

### Post by jken146 on 2008-02-28
Sorry, I don't know much about Wubi.  If you'd like us to take a look at your partitions, please post the output of this command from the terminal:
```
sudo fdisk -l
```

---

### Post by Voland on 2008-02-28
If you have your Kubuntu installed and you can boot into it you can freely unmount Windows partition.

---

### Post by heiowge on 2008-03-01
Done.  Here's the results.  Hope it's helpful.

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by heiowge on 2008-03-04
bump

---

### Post by K.Mandla on 2008-03-04
> **heiowge said:**
> I considered Xubuntu, but I wanted the KDE desktop that Kubuntu offered rather than the xfce or Xubuntu (just a preference).  Gutsy Kubntu needs over 300MB ram, wherease Feisty needs 256.
That number seems a bit high. Are you saying it's sluggish when you run it with 256Mb, or did someone tell you that?
> **heiowge said:**
> I'll look at Gparted later (laptop is packed up for work at the moment - on Wifes XP machine now) and see if I can sort it all.
Look for the GPartEd live CD and boot the machine to that. You'll be able to make as many changes as you like, without worrying about which one is mounted or where. 
> **heiowge said:**
> If I unmount windows, will it affect Kubuntu? - it was installed using wubi from an XP partition and I heard it runs with windows in the background (true or not I don't know, but it gives me pause.)
I'm afraid I've never worked with Wubi, so I can't help there. It's unusual to me to think that Ubuntu runs with Windows in the background. I don't think it's impossible, it just seems odd for some reason. :-k

---

### Post by heiowge on 2008-03-04
> **K.Mandla said:**
> That number seems a bit high. Are you saying it's sluggish when you run it with 256Mb, or did someone tell you that?

Am just quoting the numbers wiki gave me for the installs.  Was going to go with Dapper (192MB needed) to give me a little leeway, but wubi didn't seem (at the time) to support it, and although feisty is a little sluggish, it's no more than winXP was on the machine!

---

### Post by Papa-san on 2008-03-04
EDIT:

OOPS... I posted this before I read the second page...

You can install 7.10 on a machine with 256 mb of ram. (I'm writing this on one) You just have to use the alternate install CD. It goes through the installation process via a text based interface. It's pretty self explanatory, but you will prolly want to modify the partitions. Go to the manual option. change the "/media/..." entries to "/" and "/home" 10-15% for root ( / ) 900mb to 1GB for swap and the rest for your /home partition.

---

