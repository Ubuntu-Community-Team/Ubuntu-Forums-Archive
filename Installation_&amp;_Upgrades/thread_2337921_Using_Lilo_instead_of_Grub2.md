---
title: "Using Lilo instead of Grub2"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by damtor on 2016-09-22
This is my first time installing Ubuntu.   I would like to use Lilo (instead of
grub or grub2) as my boot loader.   As far as I can tell, there is no option
to select a boot loader when installing 16.04: it's grub2 or nothing.

If I allow the installer to continue and set up grub2, can I boot up
for the first time (using grub2) and then change to using lilo?
How would one do that?

---

### Post by oldfred on 2016-09-22
Why Lilo?

If system is newer UEFI, I do not think Lilo will work.

But lilo is in the repository. I sometimes suggest it to repair a Windows boot loader as it works like Windows. It has boot code in MBR and then more boot code in PBR or partition's boot sector.

sudo apt-get install lilo
But I do not know details of installing it as boot loader.

> You can use LILO to manage your Master Boot Record (with a simple text
screen, text menu or colorful splash graphics) or call LILO from other
Boot-Loaders to jump-start the Linux kernel.


 LILO Boot-Loader Development To Cease At End Of Year 2015
[http://lilo.alioth.debian.org/](http://lilo.alioth.debian.org/)

---

### Post by damtor on 2016-09-22
> Why Lilo?

I've used lilo since Slackware 1.0, so it's been over 20 years (hard to believe).
I'm very familiar with it, and I personally find it much easier to configure 
and understand than grub or grub2. 

> If system is newer UEFI, I do not think Lilo will work.

It is a UEFI system where I have 2 other distributions already installed
and booting fine with lilo.     As long as lilo keeps working, I'll keep using it.
I'm a dinosaur I guess.

---

### Post by damtor on 2016-09-22
In case someone is following along, I continued the installation but told the
installer to install grub2 in the root partition (where I was installing Ubuntu,
in my case /dev/sda12).    When I booted up for the first time, I got my
normal lilo bootloader menu which (understandably) didn't include any 
option for Ubuntu.   I booted into a different distribution.
I added these 2 lines to my /etc/lilo.conf file:

other=/dev/sda12
label=Ubuntu

and ran /sbin/lilo

I rebooted, and now my lilo bootloader menu options included the
option to (chainload) boot into Ubuntu.    By selecting Ubuntu,
lilo passed control to /dev/sda12/boot, and I got the normal
grub menu, which booted up Ubuntu just fine.

I consider this just a work around, not a solution.      

I'd really like to skip the chain loading, and if anyone knows if 
there's anyway to  bypass grub completely, I'd sure like to know how.

---

### Post by Herman on 2016-09-24
Hey Damtor,

From one old dinosaur to another:
I don't know anything about EUFI. I haven't built myself a new computer since 2010. There's nothing wrong with my old computer.
 I have found my old web page about LiLo in my old backups and I have re-uploaded if for you, here: [http://members.iinet.net/%7Eherman546/p4.html](http://members.iinet.net/%7Eherman546/p4.html)

From re-reading that old web page of mine, (also dated sometime in 2010), it looks like the main problem I experienced with LiLo back then was editing /etc/fstab a little. I had to edit it and revert to the traditional Linux device naming, like /dev/sda1 /dev/sda2 and so on rather than using file system UUIDs like we do now. The web page explains it all and has all the old LiLo commands, error messages and other information I was able to round up back then. I hope you enjoy it and LiLo is a nice boot loader. It's simple to configure and play with and customise with your own custom made splash screens and so on. 

Regards from Herman :)

---

