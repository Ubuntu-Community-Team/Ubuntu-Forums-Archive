---
title: "Ubuntu is inaccessible after F8 installation"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by hemajith on 2008-06-29
I have a dual boot system with windows and Hardy. I needed a Fedora installation for a study. So I installed F8 in another partition of my hard drive. Now I can't get my Ubuntu to work. I can work in Fedora 8 and in Windows, but can't go in to Ubuntu. Is there anyway that I can get my Ubuntu installation to work? 
I tried fixing the Ubuntu Grub with the live CD, but it detects only the F8 Grub!
I need F8 still for the study but need Ubuntu a it gives me more freedom with Multimedia and day to day operations. Please help!

---

### Post by dominiquec on 2008-06-29
Are you still able to see your Ubuntu partition from Fedora?

If that's so, the likely case is that Fedora has overwritten your previous Grub installation and ungraciously left out Ubuntu.

Try to add the Ubuntu into the menu.lst of your Fedora's grub.  You can copy it from your Ubuntu partition's boot/grub/menu.lst file.

It should look something like this:

title           Ubuntu 8.04, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=ce8aeb1e-e5f1-4b3c-b6ee-167a764fd5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic

Careful: do not follow these lines exactly.  Your own setup may differ.

---

### Post by paulmilliken on 2008-06-29
The easiest solution may be to manually edit your grub configuration in Fedora.  I'm not familiar with Fedora but if you boot it up, then go to /boot/grub (or similar) and look for a file called menu.lst.  You can open menu.lst in a text editor and add a menu item for Ubuntu.  You can use the F8 menu-item as a template and google for more help.  Of course, you'll also need to know which partition Ubuntu is installed on so you can point grub in the right direction.

Paul

---

### Post by hemajith on 2008-06-30
> **dominiquec said:**
> Are you still able to see your Ubuntu partition from Fedora?

If that's so, the likely case is that Fedora has overwritten your previous Grub installation and ungraciously left out Ubuntu.

Try to add the Ubuntu into the menu.lst of your Fedora's grub.  You can copy it from your Ubuntu partition's boot/grub/menu.lst file.

It should look something like this:

title           Ubuntu 8.04, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=ce8aeb1e-e5f1-4b3c-b6ee-167a764fd5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic

Careful: do not follow these lines exactly.  Your own setup may differ.

I added this to the F8 Grub loader. F8 does not us ea Menu.lst. Everything is on the grub.conf. But after rebooting when Ubuntu is chosen from the boot menu, it says 

file system type unknown
partition type 0x82
kernel /boot/vmlinuz blah..blah...

error 17: cannot mount selected partition

will I have to reinstall Ubuntu?

---

### Post by upchucky on 2008-06-30
im pretty sure 0x82 is the swap file partition.

do,    sudo fdisk -l 

post the results here

if ubuntu is there it should be on 0x83 as primary partition

---

### Post by hemajith on 2008-06-30
Nothing actually worked! F8 Grub would not let me access Ubuntu. So I just reinstalled it! Luckily I had all my mails and data in back up. But the bad thing is I had to install all the downloaded software and updates previously, again! Ubuntu grub loader has recognized my Windows partition as well as F8 too! 

By the way I was able to get Skype using apt-get before but when I tried today, it said "package not found"! any one know why? I have .deb package but what you get through apt-get is reliable and doesn't get stuck.

---

