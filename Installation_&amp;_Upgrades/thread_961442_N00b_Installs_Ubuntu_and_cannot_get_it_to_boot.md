---
title: "N00b Installs Ubuntu and cannot get it to boot"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by birchii on 2008-10-28
Hey, I have messed around with Ubuntu in the past but am still a complete n00b.

I have:
AMD athlon 64 3500
Gigabyte GA-K8N Ultra-SLI motherboard
2gigs of RAM
80 SATAII Hardrive, 60gb partitioned for vista ultimate, 20gb for Ubuntu
40gb IDE hard drive for storage

I installed Ubuntu 8.04.1 LTS AMD 64, I was told it was a successful install and to restart, after restart it automatically boots to vista, i have no GRUB menu. My boot priority in BIOS is CD-ROM and then my SATA II Hard drive. I have looked at quite a few posts which direct me to 
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
But the common theme in these threads is that Ubuntu was installed first and worked fine until windows was installed and overwrote the mrb and automatically booting to windows.

So anyway i follow the link above and go to terminal and type:
```
Sudo grub
```
```
find /boot/grub/stage1
```
which gives me (hd1,4)
```
root (hd1,4)
```
```
setup (hd0)
```
then tells me it is successfull
```
quit
```
restart, take out live cd, but then still gives no grub menu and automatically boots to vista...arrrrg getting frustrated.

Some help would be VERY aprreciated

Sorry for posting in wrong place :)

---

### Post by birchii on 2008-10-28
lol, ok i figured out i should have typed ```
setup (hd1)
```
Now i have a grub menu, but when i select ubuntu i get "error 22: No such Partition"

What do i do now?

---

### Post by birchii on 2008-10-28
another point to note, is that now i can't even boot up vista..."bootmgr is missing"

i need help desperately

---

