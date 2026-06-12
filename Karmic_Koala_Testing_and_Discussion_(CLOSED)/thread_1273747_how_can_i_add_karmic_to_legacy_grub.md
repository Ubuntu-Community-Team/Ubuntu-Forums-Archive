---
title: "how can i add karmic to legacy grub?"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chriskin on 2009-09-23
grub 2 just won't work on my pc, how can i add karmic on jaunty's grub?

i tried
title 		Ubuntu 9.10 64bit
root (hd0,3)
chainloader +1
and thought it was right, but apparently it isn't

---

### Post by QIII on 2009-09-23
What do you mean by "just won't work"?

I doubt that the computer itself is the issue.

---

### Post by oldfred on 2009-09-23
You need to have Grub2 installed in the partition that Karmic is in (not MBR). You then chainboot from old grub to new grub. I put Grub2 in the partition as I installed it as that is what I wanted to do and it worked fine for me.
When I did that the install told me not to but I do not know why? since it works.

---

### Post by chriskin on 2009-09-23
> **oldfred said:**
> You need to have Grub2 installed in the partition that Karmic is in (not MBR). You then chainboot from old grub to new grub. I put Grub2 in the partition as I installed it as that is what I wanted to do and it worked fine for me.
When I did that the install told me not to but I do not know why? since it works.

what are your lines for chainloading?

---

### Post by chriskin on 2009-09-23
> **QIII said:**
> What do you mean by "just won't work"?

I doubt that the computer itself is the issue.

i don't know why, i have installed grub2 before and it didn't work then either
i installed it with karmic today and it's dead as well

---

### Post by QIII on 2009-09-23
When you first boot, are you getting GRUB2 or GRUB?

Is the issue that you don't get a choice for all of your OSs?

---

### Post by chriskin on 2009-09-23
> **QIII said:**
> When you first boot, are you getting GRUB2 or GRUB?

Is the issue that you don't get a choice for all of your OSs?

i don't get all the OSs but that's not an issue, it's karmic i wanted
when i choose karmic it doesn't boot - that's the issue
so i got a live cd of jaunty, got legacy grub back and i would like to get karmic there, since it works while 2 doesn't 
(i have both jaunty and karmic)

---

### Post by oldfred on 2009-09-23
I just went back and rebooted to check that it still works and it does. I have had 32 but Ubuntu running on 2 drives dual boot for almost 3 years. I have always update and plan on a clean install for Karmic. I just added a new drive so I wanted to test 64 bit and learn about Karmic and Grub2 before it comes out. 
I boot into my standard grub for ubuntu 32 bit and chainboot to a grub partition (old grub) that lets me choose Jaunty 64 bit or Karmic 64 bit.
I believe it works because I installed Grub2 boot to my partition. My chainboot is just a standard old grub chainboot entry.

My entry in the grub partition:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


default        0

timeout        10



# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Grub Chainload Menu
root
title        -
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title       Ubuntu 9.04 Jaunty 32 bit @ sdb1
root        (hd1,0)
chainloader +1

title       Ubuntu 9.04 Jaunty 64 bit @ sdc5
root        (hd2,4)
chainloader +1

[COLOR=DarkRed]title       Ubuntu 9.10 Karmic 64 bit @ sdc7
root        (hd2,6)
chainloader +1[/COLOR]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


title   Reboot
reboot

title   Halt
halt

```Partition for Karmic

/dev/sdc7  ext4             (not mounted)  b25bf02c-299a-4ae8-a5b2-3d3bd49e95ee
( this from my fdisk in my 32 bit  Ubuntu)

---

