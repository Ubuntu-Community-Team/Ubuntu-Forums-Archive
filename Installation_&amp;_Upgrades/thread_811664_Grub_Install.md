---
title: "Grub Install??"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by bano6010 on 2008-05-29
Hello,

I have a version of Debian running on a machine right now with Grub installed from that distro and I also have a second partition set up to install Kubuntu. What I want to do is to install GRUB on another partition so it is separate from the operating systems I have installed. I have not yet installed Kubuntu and would like to get GRUB set up before I install that on the other partition I have set up. What would be the best way to create a new partition for GRUB and install it so it will boot both the Debian and Kubuntu distros?

Thanks a ton!

~bano6010

---

### Post by Irony on 2008-05-29
Just install kubuntu and accept the default grub install which will install it to the mbr.

Grub will now load up on starting the computer and will look for the grub list in kubuntu (/boot/grub/menu.lst). This list should also have an entry for your Debian install.

If for some reason you want grub to look at your menu.lst in Debian then you can boot up into kubuntu and from terminal do;

```
sudo grub
```

This opens up the grub program, with a prompt of grub>, now type;

```
find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit
```

This example installs grub to point at hda3, substitute where you want it to point to.

Here in detail is the output;

```
grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)

grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit
```

If debian isn't shown in your kubuntu menu.lst then add it manually (right click on the file choose actions open as root) for the correct entries just copy your current kubuntu entries (so you have 2 entries) then replace the second entry with the debian bits (look in your /boot folder in debian).

---

### Post by meierfra. on 2008-05-29
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by bano6010 on 2008-06-03
Thanks so much! That helped me get through it!

---

