---
title: "how to reinstall grub..."
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by 12twelve12 on 2005-07-28
i know this has been covered countless times because i HAVE done searches on this all day. i'm still stuck tho. here's the deal, i have two partitions with ubuntu on the first partition and then i installed xp on the second, now grub has been erased. reading other posts i see stuff like, boot the ubuntu cd, type rescue, click on this and that. it's kinda hard to click on stuff at a command prompt, no? i just haven't found a good clear description of what to do. any help is greatly appreciated.

---

### Post by angkor on 2005-07-28
Have you tried this?

1. boot from your Ubuntu InstallationCD
2. type rescue at the boot prompt.
3. select your root partition
(4. mount /usr if it's on a different partition, like it is in my case)
5. type grub-install

---

### Post by 12twelve12 on 2005-07-28
ok, so /usr is not listed in /etc/fstab or /etc/mtab. so i just typed grub-install and i get "install_device not specified." then i tried grub-install /hda0 and it says something about format of install_device not recognized. thanks for the reply, btw. what should i try now?

---

### Post by 12twelve12 on 2005-07-28
ok after tons of more searching i finally got grub to install. for anyone who may be in the same boat this is what i did:

booted to the ubuntu cd
type "rescue"
after all the devices load hit "cntrl-alt-F2"  <---(what is that btw?)
then "mkdir mounted"
then "mount /dev/ide/host0/bus0/target0/lun0/part1 mounted"
(target0 being my first harddrive and part1 being the first partition)
then "chroot mounted /bin/bash"
then "grub-install /dev/hda"

that's it, i'm new to linux and i don't understand why the same solutions that others mention, don't work on other systems, even if i'm using the same distro.
ah well at least ubuntu is running again like nothing ever happened. now i'm wondering how to get windows, which is on the second partition, to show up in the boot loader so i can boot to it.?   thanksandpeace

---

### Post by albertomm on 2005-07-28
[QUOTE=12twelve12]ok, so /usr is not listed in /etc/fstab or /etc/mtab. so i just typed grub-install and i get "install_device not specified." then i tried grub-install /hda0 and it says something about format of install_device not recognized. thanks for the reply, btw. what should i try now?[/QUOTE]

grub-install /dev/hda1

I have just do it... and it works  \\:D/

Damn, linux gets a lot more easy every day!!!

---

### Post by Stallone on 2005-07-28
When I installed Ubuntu, it wouldn't install GRUB and I haven't bothered to since.

All you need is here mate:

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

You get a nice Graphical Interface come up once you boot, and you can set up icons for your partitions, and select which OS to boot by using your keypad.

---

### Post by 12twelve12 on 2005-07-28
> grub-install /dev/hda1

when i tried that it gave me something about not being able to recognize the format or file system or something like that.

so how do i get my windows partition to show up in GRUB?

---

### Post by angkor on 2005-07-28
You'll need to add the partition to /etc/fstab to have it automagically mounted during boot. 

Read the Ubuntu guide Windows section:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

edit: hrm, I need to read more carefully.

---

### Post by Sam on 2005-07-28
[QUOTE=12twelve12]when i tried that it gave me something about not being able to recognize the format or file system or something like that.

so how do i get my windows partition to show up in GRUB?[/QUOTE]
You need to edit the /boot/grub/menu.lst file and add at the end:
```
title           Microsoft Windows
lock
root            (hd0,2)
savedefault
makeactive
chainloader     +1
```
Change the line 'root (hdX,Y)', where X is the disk number (zero based) and Y the partition number (zero based).

---

### Post by 12twelve12 on 2005-07-29
many thanks  :grin:

---

