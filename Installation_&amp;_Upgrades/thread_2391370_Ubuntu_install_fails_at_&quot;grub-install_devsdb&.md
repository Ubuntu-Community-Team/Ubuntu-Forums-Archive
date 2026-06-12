---
title: "Ubuntu install fails at &quot;grub-install /dev/sdb&quot; step with Software RAID"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by Imran-UK on 2018-05-09
Hello all,


I've been having a frustrating time installing Ubuntu Server 18.04 with software RAID on my hardware. I had a quick forum search but did not find anyone with exactly the same issue.


Hardware = HP ProLiant MicroServer G7 N54L
Discs = 2 x WD 4Tb Red (brand new)


I want to set it up with RAID1 with the two drives.


The installation proceeds smoothly but always fails on the "Install the GRUB bootloader on a hard disk" step.


It always mentions /dev/sdb and not /dev/sda.


Assuming /dev/sdb refers to the second disk, I've tried moving it to another of the four bays inside but I still get the same issue.


I've tried software RAID installation several times and have also re-installed the ISO image to my USB drive just in case - I always get the same issue. As an experiment I also tried Debian 9 and got the same issue.


I then tried installing Ubuntu in non-RAID configuration on each disk independently on the same hardware and that succeeds just fine.


What could the problem be? I include photos of the error and also the partition summary. 


One odd thing is that the partition summary includes some free space before and after the RAID partition. Does that look OK?


I wonder if there is a way to get more details on why the "grub-install" command failed.


Any help appreciated, thanks


(For some reason the forum will not allow me to attach photos, maybe because I just registered. Here they are)


[https://imgur.com/a/oUtAl5V](https://imgur.com/a/oUtAl5V)

---

### Post by Imran-UK on 2018-05-30
[FONT=sans-serif]I solved it.

Turns out the installers of CentOS, Debian and Ubuntu will not[/FONT]
[FONT=sans-serif]automatically create a BIOS GRUB partiton on the second disc when[/FONT]
[FONT=sans-serif]software RAID is chosen. Only the first disc gets this partition.[/FONT]

[FONT=sans-serif]This might be a edge-case bug, since it occurs when GPT and software[/FONT]
[FONT=sans-serif]RAID is used. I'll report it to the respective upstream Bugzilla's.[/FONT]
[FONT=sans-serif]In CentOS the the graphical [/FONT][FONT=sans-serif]installer displays a detailed partition summary and from checking that[/FONT]
[FONT=sans-serif]I was able to see the missing "create BIOS GRUB partition" command for[/FONT]
[FONT=sans-serif]the 2nd HDD.[/FONT]

[FONT=sans-serif]What I did was to boot into a system rescue USB and use parted to[/FONT]
[FONT=sans-serif]remove the partition table, create a new GPT one on each afresh and[/FONT]
[FONT=sans-serif]then manually add a 1M BIOS GRUB partition to both discs.[/FONT][FONT=sans-serif] This partition[/FONT]
[FONT=sans-serif]is where GRUB installs some crucial 2nd stage boot-loader files when[/FONT]
[FONT=sans-serif]using GPT partition tables. You need to use GPT to use discs >2T in[/FONT]
[FONT=sans-serif]size.[/FONT]

[FONT=sans-serif]Anyway, I then proceeded with an Ubuntu Server 18.04 install. I chose[/FONT]
[FONT=sans-serif]to manually create the partitions I needed and proceed with[/FONT]
[FONT=sans-serif]configuring my software RAID array and then install went off without a[/FONT]
[FONT=sans-serif]hitch.

These screenshots show the parted commands and the final Ubuntu partition scheme: 

[/FONT]https://imgur.com/a/1jyWFkU

---

