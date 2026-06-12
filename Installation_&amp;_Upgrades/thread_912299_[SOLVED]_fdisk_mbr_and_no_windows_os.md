---
title: "[SOLVED] fdisk /mbr and no windows os"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by nneedrelief on 2008-09-06
so i'm installing ubuntu, happily connected to internet and finally got all the updates. After restart the computer gives me an error 22... grub. 

Now i like the whole recon for info and learn to do it yourself method... i found a site that was talking about fdisk /mbr and i didn't realize it was for windows dual booters. I don't have windows. I'm running a computer than used to have xandros (until i formatted it away) and after installing ubuntu i was just about to install xubuntu because all this is happening on my little eee 900 20gb computer.:lolflag:

Now i feel like i'm screwed, no windows install cd on hand, its not letting me do anything that is not windows, and all i want is my grub back. 

things i've done to correct problem

- super grub disk
- aio pendrivelinux08
- run the cursed 98 boot disk floppy that did this to me in the hope that there was an option in the help file

the furthest i've got was ntldr is missing
i only have a usb of 4gb, 30gb, and external usb floppy drive

---

### Post by pytheas22 on 2008-09-06
fdisk /mbr almost never really works anyway, especially if there are Linux partitions thrown into the mix.

Can you try reinstalling Ubuntu a second time?  That should replace the current grub bootloader with one that works, allowing you to boot to Ubuntu on the hard drive.  Since you know that grub installed correctly the first time, presumably it would work a second time as well.

---

### Post by caljohnsmith on 2008-09-06
As pytheas22 mentioned, reinstalling Ubuntu might do the trick, but if you want to make an effort to get your Ubuntu working without a reinstall, first try the following from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you get any errors doing the above, post the full output. Also, please post the output of:
```
sudo fdisk -lu
```

---

### Post by nneedrelief on 2008-09-11
thanks guys, really helped

i used a live cd from a usb stick to just load ubuntu and went from there. didnt have to use the live cd's ability to make grub but that was very useful

thanks!

:KS

btw if you're reading this and have more questions feel free to leech on my thread. i pretty much have my comp all ready now but i love to see what other people are running into 

and sorry you two who already wrote something, i was 4 days late because i thought i subscribed (heck i wrote the darn thing) but i never got email notifs so hah im here now

---

