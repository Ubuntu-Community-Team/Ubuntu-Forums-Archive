---
title: "Resizing Woes"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by harrykh on 2008-04-10
Hi, I rcently resized my ext3 partition in Windows using Paragon PM (yes, I'm aware how stupid that was but please bear with me). After which when I try to boot back to Ubuntu it gives me this error:
 
Resize inode not valid
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY

on /dev/sda5

It gives me the CLI, now I'm hopelessly confused on what to do.

I downloaded GParted LiveCD after searching some posts, but right now when I'm trying to "check and repair filesystem" it just sits there on

"calibrate /dev/sda5" and hasn't gone to the 2nd part of the check which is the actual checking itself.

it's been like this for a long time now. should I just exit and try somethng else?

thanks for any info

edit: [http://kb.paragon-software.com/paragon/include/templ/object2.jsp?catId=2124&objId=1359&statId=1028013&foLang=en](http://kb.paragon-software.com/paragon/include/templ/object2.jsp?catId=2124&objId=1359&statId=1028013&foLang=en) tells me that I need to make changes to boot manager. But this seems outdated somehow.

---

### Post by harrykh on 2008-04-10
noone can help me? do i have to reinstall ?

---

### Post by Partyboi2 on 2008-04-10
have you tried maunally running fsck?
From the terminal you can
```
 sudo fsck /dev/sda1
``` (you may need to change sda1 to your correct linux partition. You can view the linux partitions by typing
```
sudo fdisk -l 
``` (Thats a small L)

---

### Post by ZALMAN on 2008-04-11
Experienced the same problem a couple months ago. PM is an excellent partition manager under an MS platform but using it in/for linux does not work. Use PM to create your required free space, do not format the space, then re-install Ubuntu giving yourself enough space for you programs ie: ext3 at around 10G, swap 1 to 2 G. Originally I had been able to run Ubuntu by repairing Grub, but frequently received error messages or false starts (hanging). 
Although you would be starting from scratch, you would be performing a clean install. Have done about a half dozen trouble free installs since then by simply planning the space before actually installing.
Hope this helps and good luck. By the way I think linux Ubuntu is great, had I worked with it years ago, I'm not sure that I would be using windows today, but old habits die hard.

---

