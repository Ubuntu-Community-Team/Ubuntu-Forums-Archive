---
title: "HELP! Windows wont boot after install"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by rippon on 2005-10-01
Ok. So I had 1 harddrive, windows partition of 60GB, had a FC4 partition of 25GB. 

I wanted ubuntu instead of Fedora, so I struggled getting the partitions setup in ubuntu install. I was goign back and forth, exiting, re-configuring, trying to get the "no root configured" , until I fixed it. It installed fine, it works (except for wireless). Now It wont let me boot into windows (which works on wireless), I am using grub. It told me that MS windows was detected.... Click next to install bootloader....etc. Now when I try to boot into Windows XP, I get this after tell grub to boot into windows:
```


Booting 'Microsoft Windows XP'

root (hd1, 0)
   Filesystem type unknown, partition type 0x7
savedefualt
makeavtive
chainloader +1

```

I dont know what this means, or what to do.
I was thinking somehow copy the partition onto my 120GB drive, to back up and re-install XP? Could I do this wit ha boot disk like knoppix?

If you need anymore info, I am here.
Thank you in advanced.
Dan Rippon

----Something to add in from sudo gedit /boot/grub/menu.lst

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```
is the last part right, it looks bad... but I have no Idea what I am doing, just wandering around the forums....

---

### Post by aysiu on 2005-10-01
I don't know how to solve your problem, but [this may be a good start](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22Filesystem+type+unknown%2C+partition+type+0x7%22&btnG=Google+Search)

---

### Post by rippon on 2005-10-01
Hmmm, I have been looking around. I still cant seem to fix it. I was hoping I wouldnt lose the XP partition with all my important documants on it. Ubuntu is a fresh install, and can be sacrificed without losing any important data of mine. 

Is there a way to do that? 
I was thinking maybe windows recovery disk, to overwrite grub.
I am a newb, help me out :)

Thanks,
Dan Rippon

---

### Post by aysiu on 2005-10-01
[QUOTE=rippon]I was hoping I wouldnt lose the XP partition with all my important documants on it.
Is there a way to do that?[/quote] To recover your documents, use a live CD distro like Knoppix. Your Windows partition will appear on the desktop. You can then copy those documents to an external hard drive, CD, a bunch of floppies, or a zip drive.

> 
I was thinking maybe windows recovery disk, to overwrite grub.
I am a newb, help me out :) You can also do this by following [Microsoft's instructions](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

---

### Post by rippon on 2005-10-01
Thanks.
I will probally just do that. Seems that it is the easiest since I have 80gb free on ide1.

***off topic:
How many reformats can a hd take?

---

### Post by aysiu on 2005-10-01
[QUOTE=rippon]
***off topic:
How many reformats can a hd take?[/QUOTE] I have no idea, but I've reformatted my hard drive at least twenty times, if not thirty, and it works just fine.

---

### Post by rippon on 2005-10-01
Ok, that is reassuring. Thought I broke my old harddrive by reformatting it 4-5 times. I guess it was just fualty. Didnt matter becuase I got a new one. Being able to running off the Ubuntu Live CD helped alot while it was getting replaced (almost a month). I ran the live cd for a month, it gets like windows after a while, wants to be restarted every few days. Must eat away at memory.

---

