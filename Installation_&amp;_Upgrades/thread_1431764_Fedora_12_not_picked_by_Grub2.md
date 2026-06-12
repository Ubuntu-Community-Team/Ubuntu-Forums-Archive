---
title: "Fedora 12 not picked by Grub2"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by maddy_in65 on 2010-03-17
I am Quad booting my lappy with Fedora 12, Opensuse Karmic and Vista.
Grub2 is not picking Fedora even after i had done Grub update command.
I never edited Grub 2 thing and even /boot shows menu.lst. 
sda6 contains opensuse and sda7 having fedora 12. Please let me know how can i edit Grub2 for fedora 12 entry



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5253    42194691    7  HPFS/NTFS
/dev/sda2            5254        9169    31455270    7  HPFS/NTFS
/dev/sda3            9170       13085    31455270    7  HPFS/NTFS
/dev/sda4           13086       19457    51183090    5  Extended
/dev/sda5           13086       13216     1052226   82  Linux swap / Solaris
/dev/sda6           13267       15094    14683378+  83  Linux
/dev/sda7   *       15095       16922    14680063+  83  Linux
/dev/sda8           16922       17053     1048575+  82  Linux swap / Solaris
/dev/sda9           17054       19457    19310098+  83  Linux

---

### Post by maddy_in65 on 2010-03-17
After googling, i have done some changes in my 40 custom file and executed following commands in terminal

sudo chmod 666 /boot/grub/grub.cfg
sudo grub-mkconfig > /boot/grub/grub.cfg
sudo chmod 444 /boot/grub/grub.cfg

still Grub doesnt show Fedora entry.


Here's my 40 custom file:
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora 12 Constantine" {
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set 9405aab3-dc86-493a-a501-101a1c8d6c14
linux /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=9405aab3-dc86-493a-a501-101a1c8d6c14 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img

*****set root=(hd0,8) Please read as (hd0,eight)
It shows smiley above :P

---

### Post by oldfred on 2010-03-17
You should not edit grub.cfg but /etc/grub.d/40_custom, if grub does not find it automatically. Then run sudo update-grub to copy it into grub.cfg.

Your (hd0,8) or  sda8 is swap, grub2 counts partitions now the same as fdisk starting at one where grub legacy started at zero.

[http://ubuntuforums.org/showthread.php?t=1370222](http://ubuntuforums.org/showthread.php?t=1370222)

---

### Post by maddy_in65 on 2010-03-17
Now Grub2 is able to pick up Fedora 12 entry after adding following lines to D40. But after selecting Fedora 12 it shows error message "Please load kernel first". I have edited below entry correctly. Please let me know how should i solve this issue.



menuentry "Fedora 12 Constantine" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 9405aab3-dc86-493a-a501-101a1c8d6c14
linux /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=9405aab3-dc86-493a-a501-101a1c8d6c14 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by oldfred on 2010-03-18
Does not Fedora have a separate boot partition as standard? Is your hd0,7 refer to the boot partition?

Run this script to see the entire set up:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by maddy_in65 on 2010-03-18
> **oldfred said:**
> Does not Fedora have a separate boot partition as standard? Is your hd0,7 refer to the boot partition?

Run this script to see the entire set up:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Thanks for this code. yes hd07 refers to fedora 12 partition. I dont have seperate boot partition as i am Quad booting the system. I have attached result.txt for your reference. it clearly find Fedora partition. Please let me know what to do next. thanks.

---

### Post by maddy_in65 on 2010-03-18
Anyone please help me to sort out this issue

---

### Post by tom4everitt on 2010-03-18
Try pressing 'c' in the grub menu, to get a shell.

Then execute command by command of your fedora entry, and you'll see where it goes wrong. 

You can also use the ls command in the grub shell:

ls (hd0,7)

lists the content of your fedora partition, and

ls (hd0,7)/boot

should list your kernels etc.

Hope it helps.

---

### Post by oldfred on 2010-03-18
Your Fedora boot stanza has /boot/... which is missing in your 40_custom??

title Fedora (2.6.31.5-127.fc12.x86_64)
    root (hd0,6)
    kernel [COLOR=DarkRed]/boot[/COLOR]/vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=9405aab3-dc86-493a-a501-101a1c8d6c14 nomodeset LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd [COLOR=DarkRed]/boot[/COLOR]/initramfs-2.6.31.5-127.fc12.x86_64.img

menuentry "Fedora 12 Constantine" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 9405aab3-dc86-493a-a501-101a1c8d6c14
linux /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=9405aab3-dc86-493a-a501-101a1c8d6c14 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by maddy_in65 on 2010-03-18
> **oldfred said:**
> Your Fedora boot stanza has /boot/... which is missing in your 40_custom??

title Fedora (2.6.31.5-127.fc12.x86_64)
    root (hd0,6)
    kernel [COLOR=DarkRed]/boot[/COLOR]/vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=9405aab3-dc86-493a-a501-101a1c8d6c14 nomodeset LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd [COLOR=DarkRed]/boot[/COLOR]/initramfs-2.6.31.5-127.fc12.x86_64.img

menuentry "Fedora 12 Constantine" {
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 9405aab3-dc86-493a-a501-101a1c8d6c14
linux /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=9405aab3-dc86-493a-a501-101a1c8d6c14 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}

Hi Oldfred, this solves my issue thanks. But now i am facing another issue, after selecting Fedora from grub menu, i cant get login window. I can see fedora sign at the bottom right corner of Laptop LCD. I think this is due to resolution. How can i change resolution.
[[IMG]http://img510.imageshack.us/img510/5906/18032010083.th.jpg[/IMG]](http://img510.imageshack.us/i/18032010083.jpg/)

---

### Post by oldfred on 2010-03-19
I know nothing about Fedora. This may be better to ask on a Fedora forum as we are primarily Ubuntu except for those like you who are dual booting and have some knowledge of other systems.

---

### Post by maddy_in65 on 2010-03-19
> **oldfred said:**
> I know nothing about Fedora. This may be better to ask on a Fedora forum as we are primarily Ubuntu except for those like you who are dual booting and have some knowledge of other systems.


No issues but still i am wondering about the exact cause of this problem. After fedora installation which is before karmic installation i am able to boot fedora without any issues. But after Karmic i got this issue. Is it related to Grub2

---

### Post by tom4everitt on 2010-03-19
> **maddy_in65 said:**
> Hi Oldfred, this solves my issue thanks. But now i am facing another issue, after selecting Fedora from grub menu, i cant get login window. I can see fedora sign at the bottom right corner of Laptop LCD. I think this is due to resolution. How can i change resolution.
[[IMG]http://img510.imageshack.us/img510/5906/18032010083.th.jpg[/IMG]](http://img510.imageshack.us/i/18032010083.jpg/)


Notice that there were other differences between fedoras grub entry and the grub2 entry. 

In fedoras version some more kernel arguments were passed, try adding those to your 40_custom entry if you haven't already done so! This might well be the cause of the problem.

---

