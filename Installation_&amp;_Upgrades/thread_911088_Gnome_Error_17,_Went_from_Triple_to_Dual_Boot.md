---
title: "Gnome Error 17, Went from Triple to Dual Boot"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by bdfoster on 2008-09-05
I have one drive with (really) 149GB on it, and I wanted to experiment with Kubuntu. I did my experimenting, then I was stupid and deleted that partition on my Ubuntu installation using GParted. Since Kubuntu was the last OS that was installed, that is where Grub pointed to. 

I have five partitions on this one drive. It tries to boot to an HP Recovery partition setup at the factory.

HP Recovery
Vista Installation
Swap File for Linux
Ubuntu Hardy
Unpopulated FAT32 (this is where Kubuntu was installed)

When I boot, it goes to Grub, tries to start, then gives me the Error 17.

Any suggestions as to how I can fix this? I've been all over the forums trying find someone with the same scenario.

---

### Post by ronnielsen1 on 2008-09-05
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

> Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

---

### Post by Crafty Kisses on 2008-09-05
Try SuperGRUB to repair the bootloader > supergrub.forjamari.linex.org

---

### Post by caljohnsmith on 2008-09-05
Ronnielsen1's method might still work, but it is not necessary as there is a simpler way to restore Grub. Just boot your Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That's all it should take, but if for some reason you get any errors or have any problems, let me know.

---

### Post by ronnielsen1 on 2008-09-05
Mepis has an excellent tool for repairing grub from the livecd that works on any debian system but unfortunately it's not released outside of Mepis

---

### Post by bdfoster on 2008-09-05
> **caljohnsmith said:**
> Ronnielsen1's method might still work, but it is not necessary as there is a simpler way to restore Grub. Just boot your Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That's all it should take, but if for some reason you get any errors or have any problems, let me know.

This solution I have done many times, and I can't get past the root (hdx,y) part. Will try again though.

---

### Post by bdfoster on 2008-09-05
> **ronnielsen1 said:**
> [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

I don't think this applies to Ubuntu Hardy... 

The options are not the same and when you are done mounting / it asks if you want to continue with installation or go back to partition editor. When I abort the install there is no way to install grub.

I appreciate you efforts though. This is something I hadn't tried.

---

