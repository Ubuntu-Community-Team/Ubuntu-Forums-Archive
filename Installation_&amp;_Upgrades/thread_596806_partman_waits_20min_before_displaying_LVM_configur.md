---
title: "partman waits 20min before displaying LVM configuration screen"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by najevi on 2007-10-29
Target system has a 2.2GHz P4 with 533MHz FSB and 256MB DDR266 system memory. Objective is a clean install of ubuntu to a blank 120GB HDD (/dev/sda) using Feisty Fawn (DVD version).   

I have previously boot from the ubuntu DVD into a liveCD desktop and installed **LVM2 **to create and format partitions using a combination of **fdisk**, **pvcreate**, **vgcreate**, **lvcreate**, **mkswap **and **mkfs**.  (ref. [http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem) )

Having completed that preparation step I have now rebooted from the DVD and started the ubuntu text-mode install.  
At the Disk Partitioning step I select "Manual" and verify that I have physical partitions as follows: 
** /dev/sda1** primary partition formatted as **ext2 **and mounted as **/boot** 
** /dev/sda2** primary partition initialized for use as **Physical Volume **for LVM  

I select "Configure LVM" and when asked whether or not to activate the existing Volume Group I answer **Yes**.  

OK, so _from this point I must patiently wait 22 minutes_ (with no feedback other than a blue screen) until finally the "Summary of current LVM configuration" window appears!

[B]What is partman doing all this time?

[/B][COLOR=Navy]... found the related bug report at[/COLOR]  [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623)
[COLOR=Navy] and read that this undue delay in activating existing LVs has been fixed in Gutsy Gibbon so I plan to use Gutsy instead.[/COLOR]

---

