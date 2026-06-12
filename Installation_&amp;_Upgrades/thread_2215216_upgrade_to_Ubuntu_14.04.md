---
title: "upgrade to Ubuntu 14.04"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by yash_pal2 on 2014-04-05
I have Ubuntu 13.04 on an extended partition dual booting with Windows 7 with Easy BCD 2.2.  
 

 There are 4 logical partitions in the extended partition of  Ubuntu 13.04. First is boot - about 1Gb, second is root - about 12.5Gb, third is home - may be 200 Gb and fourth is Swap - 2 Gb. Grub is loaded on boot partition (Sda5- as per GParted).

 

 I would like to upgrade to 14.04 through live DVD but would not like to lose data in &#8220;Home&#8221; partition of Ubuntu.
 

 So can I install 14.04 in the following manner:
 

  1. With GParted, format 'boot' and 'root' partitions only, to ext4 and install 14.04, again load grub on boot partition (sda5- as per Gparted)

  

  2. Go to Windows and check in EasyBCD if Ubuntu can be booted; otherwise add Ubuntu to easy BCD.
  

 I understand risk of data loss and have already started backing up critical data.

Any help/ explanation as to whether I am right or can upgrade in the above manner will be gratefully acknowledged.

 

 The question could belong to absolute beginner section, but I thought this is more appropriate section.

---

### Post by sudodus on 2014-04-05
It is a very good idea to backup critical data before this risky operation :KS

It is possible to keep the /home partition, many people do it like that.

If you don't want to boot via grub, write the bootloader to a partition instead of to the head of the drive, (Otherwise do the opposite: Most people would boot via grub so they would write the bootloader into the head of the drive **/dev/sda** (without any partition number).)

-o-

Remember that 14.04 LTS is still being developed and might break during the last few week before it is released. I would recommend that you wait to install it as your main or production system until some week after it is released.

---

### Post by Double.J on 2014-04-05
Hi there!

Yes you can absolutly reuse your existing /home.

There's basically two ways. The first is during install set the mount point of your existing /home partition to be /home BUT DO NOT FORMAT it.

The second is to install as usual, keeping /home in the / partition, then back up the old /home,  the fstab to mount your old home partition at /home, use the 'defaults' option then restart. 

Note that when reusing a /home partition, if you use the same username, all desktop settings and other such files will apply to the new system, if you do not use the same username, then although all your old data will still be accessible, you won't be using your old directories, but the new ones. It is seldom advisable to use the same username if sharing a home partition with another distro.

You can also do an 'apt-get dist upgrade' then run update manager, although this does cause more bugs on average than a clean install.

personally I share my home partition with four distro's. each has a unique username and links between the folders.

But yes, do not  replace your only ubunutu system with 14.04 for at least a week - month after release!

---

### Post by yash_pal2 on 2014-04-06
Thank you sudodus and gnu/mirow.

I think my approach has been validated and I will try it, of course not formatting the /home partition but keep the same username and password

I will delay installation of 14.04 as much as I can.

Thanks once again.

---

