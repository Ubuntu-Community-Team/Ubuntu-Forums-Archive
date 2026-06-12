---
title: "Grub boot problem after upgrade"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by Kansasguy on 2012-06-07
The short of it:   Can't boot a Linux (Ubuntu 12.04 box) after upgrade, probably not trying to boot to the right drive.

The Long of it:  (Any and all help welcome)


My friend came up to see me and brought his failing Windoze box, a Dell dimension 4400 with XP on 20gb HD   Wouldn't boot.  

Another friend added an 80gb hd, figuring the 20gb HD might be going bad, and mounted them "cable select"


Tried several times to load Ubuntu 12.04 from a disk (been a long time since I have mounted a Linux distro, because once on my computers, they work so well. Finally successful in loading it (BUT CAN'T REMEMBER WHETHER I PUT IT ON THE 20 OR THE 80 GB HD)

Worked great.  Sent him home with it and he loved it, just uses it to surf the web and email (via hotmail).  Got him to download LXDE desktop because it was easier for him.  Everything great so far.  

Then, after an upgrade it would no longer boot, so we had him surfing the web using the live CD.

boot-error

****************************
Then, after checking the web, found that boot problems after an update are very common, and followed the following steps:

***********************************************************
"If you just have the Ubuntu Live CD try these steps:

    Boot from Live CD
    Open a terminal from the Live CD, and run the following commands:

    sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update
    sudo apt-get install -y boot-repair
    boot-repair

    Follow the Recommended Repair option. Press "Advanced" to check what it will do.
    The stressful bit. Now reboot and you will be able to use Grub."
************************************************************

At the end of that, it said 

something about cutting and pasting  [http://paste.ubuntu.com/10189/boot.repair@gmail.com](http://paste.ubuntu.com/10189/boot.repair@gmail.com)

and something like (from his poor notes)

and make sure the bios boots on the sbd disk.

Now when we start the computer, it goes to the normal boot screen, something like:

Ubuntu 12.04  3.2.0-23 generic-pae
Ubuntu...............Recovery mode

and all the directions at the bottom

but now when he clicks on the kernel, it doesn't boot and gives the message:

************************
fisk -l yields:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd072

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    37005311    18501632   83  Linux
/dev/sda2        37007358    39100415     1046529    5  Extended
/dev/sda5        37007360    39100415     1046528   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       64259       32098+  de  Dell Utility
/dev/sdb2   *       64260   156232124    78083932+  83  Linux
ubuntu@ubuntu:~$
******************************

Dell site with how the bios works:

[http://support.dell.com/support/edocs/systems/dim4400/syssetup.htm](http://support.dell.com/support/edocs/systems/dim4400/syssetup.htm)

Thanks for any help!

---

### Post by wilee-nilee on 2012-06-07
Post the bootinfo summary that was intended for that pastebin link. Or run just that again from the boot-repair and post that HTTP address.

---

### Post by Kansasguy on 2012-06-07
Thanks so much for the quick reply.  The:

"   sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update
    sudo apt-get install -y boot-repair
    boot-repair" 

got us to a GUI.  Do I go thru all that again, or can I just do "boot-repair" in a terminal?   The computer is now 450 miles away from me, and my friend is not computer savvy.  Thanks for your patience, I've been away from terminal commands for a few years.

---

### Post by wilee-nilee on 2012-06-07
> **Kansasguy said:**
> Thanks so much for the quick reply.  The:

"   sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update
    sudo apt-get install -y boot-repair
    boot-repair" 

got us to a GUI.  Do I go thru all that again, or can I just do "boot-repair" in a terminal?   The computer is now 450 miles away from me, and my friend is not computer savvy.  Thanks for your patience, I've been away from terminal commands for a few years.

Here is the website, those commands just load the app, you would just open and click the bootinfo summary, it then gives the HTTP where the script is, it take a look at the screen shots on the site.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Kansasguy on 2012-06-09
Thanks again.   He left for a trip to California for 3 weeks, and stores virtually nothing on his computer.  While I am constantly (and enjoy) learning new things about Linux, might it not be better and easier for me to just send him a new disk (thinking Mint this time because I've used it and it's quite user friendly) and start all over again?  (he is getting a message that his "disk is unhealthy" with the live CD in)

---

