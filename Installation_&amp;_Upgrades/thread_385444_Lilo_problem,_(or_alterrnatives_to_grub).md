---
title: "Lilo problem, (or alterrnatives to grub)"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by brettg on 2007-03-15
Hi

I have struck a bug in grub which results in grub disabling my optical drive due to it detecting a purported ACPI problem.

I can workaround by using acpi=off kernel directive but this doesn't help me as far as dual booting Windoze.

So, I need an alternative to grub it seems.

Lilo is the obvious choice, but I am having mucho difficulty getting lilo working. Firstly, liloconfig doesn't like the new format that Ubuntu uses in /etc/fstab with all the UID string thingies that are at the start of the device lines. I fixed that by manually editing fstab to the old  dev  mount  type format and got past that hurdle.

Next thing is that at the end of running liloconfig, an error is given;

ERROR: install-mbr failed! Your system may not be bootable.

hmmm, OK, so I run /sbin/lilo -v and that goes through without error.

It's not necessary for me to tell you that when I reboot lilo does not start as the bootloader, grub still does the job.

I've also googled for alternative bootloaders and tried gag, OSL2000 and XOSL2. They all work fine loading WIndoze, but none of them will load Ubuntu, I just get a screen full of "9" chars.

Aargh, I need a solution here. 

Making grub work properly would be the best option obviously, if there is a way to do an equivalent workaround to acpi=off that would work with windoze then that would be excellent.

Alternatively, any ideas on how to get lilo working would be appreciated as well.

Finally, a pointer to a good alternative boot loader that could be used to boot Linux and Windoze would be acceptable too. 

Here is the partial output of df -h;

/dev/sda4             9.7G  3.1G  6.1G  34% /                        
/dev/sda2              60G   13G   45G  22% /home
/dev/sda1             3.5G  2.7G  798M  78% /media/sda1

Any help would be highly appreciated. Thanks in advance!

---

### Post by Cariboo1938 on 2007-03-15
[HERE]("http://http://users.bigpond.net.au/hermanzone/") is a guy who is an expert.....
[CHECK]("http://users.bigpond.net.au/hermanzone/p4.html") it maybe it helps..

---

### Post by brettg on 2007-03-15
Cool, thanks for that Cariboo

I got it working by using Lilo on the linux partition and chainloading it from GAG. Works a treat.

Thanks for the urls, that lilo site was the best I've seen

---

