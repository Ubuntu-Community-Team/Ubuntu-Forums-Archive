---
title: "hoe do i boot win 7 xubuntu kubuntu ubuntu"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by jmate24 on 2011-07-30
hi i have searched the forums to find out how i can install win 7, xubuntu, ubuntu, and kubuntu i have 3 drives 1 160gb and 2 1.5tb drives and i am wondering how i would be able to install all 4 oses  with out grub2 not seeing one of them.

---

### Post by Megaptera on 2011-07-30
_buntu is the operating system, K X and U are desktop environments -

Ubuntu, Xubuntu, Kubuntu, Lubuntu etc

Much better explanation here: [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

so you don't need to install 4 operating systems.

---

### Post by jmate24 on 2011-07-30
well what if i wanted to mess around and test them on my hardware to see which one i like better?

---

### Post by garvinrick4 on 2011-07-30
Make partitions in gparted that you want to install them in. Download iso's of Operating Systems, Burn them to a disk. Install in partitions already pre-made. Put grub (boot manager) into whatever drive it is, sda, sdb, sdc, sdd, and so on and on. Find which drive
has what sd[COLOR=Red]x[/COLOR] by running "sudo fdisk -l" in terminal, without quotes. 
When you boot into any Ubuntu operating system run "sudo update-grub" in terminal and
a package called os-prober will go out and fetch other operating systems and include them
as menu entry and in comfig file. Drive with only windows will only boot windows as their
grub does not have an os-prober. You have to select which drive you want to boot before grub hits in Bios or you can set in Bios to which drive you want to boot from.
A how to from Ubuntu below:
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
Grub site:
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")
How to for grub:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
A bit about gparted illustrated:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by critin on 2011-07-31
> **jmate24 said:**
> well what if i wanted to mess around and test them on my hardware to see which one i like better?

Have you thought about installing the various desktop environments from Synaptic?  You could log out and choose another from the login screen.  I experiment with them that way and it works for me.  That way you don't have to worry about the grub at least.  ;)
critin

---

