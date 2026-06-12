---
title: "multiboot"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by sskraju on 2010-07-28
I'm completely linux newbie. I got a PC(32 bit) from my friend that has Fedora & Ubuntu on single HDD.Now I need to install  Suse on the same HDD without destroying other distros.Please let me know what are the prerequisites for this? & how to do this step by step.

I'm not sure how the before installation is done?? I'm not sure about grub editing/tweaking.Plz guide me clearly.If you need any additional information plz let me know.At present installation of SUSE is very important

Ubuntu 10.04
Fedora 13
OpenSuse 11.3


Thanks in advance
Raju

---

### Post by oldfred on 2010-07-28
Partitioning is the main issue. Do you have space to install it now or do you have to change partition sizes, then it is a lot more difficult.

Also which boot loader will be in charge. I like Ubuntu's grub2 but some want another system. Grub2 is very good at adding boot for other systems. Others based on old grub may need help adding the boot info to the menu.

---

### Post by theozzlives on 2010-07-28
I'd say use gparted, make some space and install. If you foobar your GRUB2, it's easily installed with a live CD.

---

### Post by sskraju on 2010-07-28
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004944b

Device Boot Start End Blocks Id System
/dev/sda1 * 1 25 200781 83 Linux
/dev/sda2 26 662 5116702+ 83 Linux
/dev/sda3 663 793 1052257+ 82 Linux swap / Solaris
/dev/sda4 794 1538 5980161 5 Extended
/dev/sda5 794 806 97280 83 Linux
/dev/sda6 806 1414 4881408 83 Linux
/dev/sda7 1414 1538 999424 82 Linux swap / Solaris

i will use ubuntu grub2 only

---

### Post by sskraju on 2010-07-28
default options what i got for partitioning in suse is

/dev/hdc2 (4.8G) for /home with reiserfs
/dev/hdc6 (4.8G) for / with reiserfs

/dev/hdc3 as swap
/dev/hdc7 as swap

will these settings erase previous distros??? how to proceed

---

### Post by oldfred on 2010-07-29
You do not have a lot of room for 3 installs, but it may work. We cannot tell what is where but this script will:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

