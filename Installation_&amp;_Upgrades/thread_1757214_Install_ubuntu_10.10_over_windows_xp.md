---
title: "Install ubuntu 10.10 over windows xp"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by stribor40 on 2011-05-13
I am trying to install ubuntu over windows xp but after i reboot with livecd inside systems hangs with following.....

No init found
Init = bootargs

And it just hangs there......
Can anyone point me how to get arround this.i want to completely wipe windowsxp off and have only ubuntu on my laptop. 

Thanks for any input

---

### Post by Rubi1200 on 2011-05-13
Hi and welcome to the forums :-)

Please use the LiveCD to boot the computer and follow these instructions so we can try and figure out what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by stribor40 on 2011-05-13
Hi and thank you for quick response. 
This is what I did. I was prompted with 4 options
1 chose "try ubuntu without instalation" 
2. Full installation
3.Test hard drive (i am recalling this from my memory)
4. Dont remember this option

I have tried each of these options all of them do nothing but lead me to folowing.....

```
No inti founf. Try passing init = bootarg.

Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in-shell (ash)
Enter help for list of built in commands

(initramfs)_
```Chosing "try ubuntu without instalation" gave same error.
If you please have any other suggestions would love to try them.
I should mentioned i grabbed this image from torent.
Should i download it dirrectly from the ubuntu site?

---

### Post by wilee-nilee on 2011-05-13
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Please use the LiveCD to boot the computer and follow these instructions so we can try and figure out what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

What an excellent idea.
+1

OP make sure the ISO is good=MD5SUM and make sure it is burned as an image not data.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Run this script as well, if you get the cd working and have problems, run it before doing anything might be best.

---

### Post by varunendra on 2011-05-14
If the CD were burnt as a data disk, it wouldn't be bootable at all. So I think the CD is burnt in a correct manner, but still there are chance of errors during the burning process.

So first you have to make sure the CD itself is error-free. The best way to check this would be to try to boot another computer with it. Alternatively you may check its integrity using the methods suggested in the link that wilee-nilee provided above.

Another sure-shot way to check both the ISO/CD would be to boot a virtual machine with it, but if you don't already have VirtualBox (or something similar) installed on your Win XP, then wilee-nilee's method would be easier and quicker.

---

### Post by stribor40 on 2011-05-14
I downloaded mosr recent iso from ubuntu web site. This is what i get now....

Busybox v1.17.1 (ubuntu1:1.17.1-10 ubuntu1)built in shell (ash)
Enter help for list of build in commands

(initramfs) mount:mounting /dev/loop0 on //filesystem.squashfs failed:input output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs

Any suggestions....i made sure that iso is same size and also thatnit is not corupted

---

### Post by stribor40 on 2011-05-14
i got brand new  cd ..copied iso from ubuntu site again and it worked fine.
thank you guys for help

---

