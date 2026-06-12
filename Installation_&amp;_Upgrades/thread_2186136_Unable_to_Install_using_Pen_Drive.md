---
title: "Unable to Install using Pen Drive"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by arun.manuel14 on 2013-11-06
I have window 7 on my hp dv 6 laptop. I created a bootable USB stick using unetbootin.
I then booted my laptop using usb stick and chose "Install Ubnutu without trying"
I selected the language and everything and after i selected "Install ubuntu within windows"
it would say "terminating all remaining processes " and reboot . When it reboots it just enters windows as usual 
and the ubuntu installation doesn't continue.
Then i changed the Boot device priority so that after it reboots it boots from the USB , that was of no use either ,
 as it would just show me the unetbootin menu again.

Can anyone please help me sort this out .

---

### Post by mastablasta on 2013-11-06
did you check the md5sum of the image after download?

how is your disk partitioned? is it GPT or MBR? do you have a free primary partition available (means that you have only 4 primary parittions?) if it's the old way of partitioning?

also install ubuntu "within windows"? is that wubi? wubi is not supported anymore.

---

### Post by arun.manuel14 on 2013-11-06
Yes , the md5 hashes match .
No , i'm not referring to wubi . I'm trying to install Ubuntu 13.10 which has no support for wubi anyways. 
When i'm installing i get several options like install on a new partition etc , one of the options was install within windows.

My disk is partitioned as MBR

---

### Post by mastablasta on 2013-11-06
ok i don't know the UBuntu installer so much since i use Kubuntu. but i think they are very similar.

for MBR - you need to have 1 free primary parittion. you can see in windows disk manager how they are formated. 
problem: HP + Win7 usually has all 4 primary occupied. boot, System (C), hp_tools, recovery. 
solution: use the free *mini tool partition wizzard *to convert system partition (the C:\ drive) into secondary/logical. defragment it 2 times (second time it will be faster). shrink the partition and create free disk space for ubuntu.

then during install select something else. choose to format the free disk space into ext4 and select / as mount point. also create another partition in that space called formated as /swap (about the size of RAM) and mounted as /swap. i think the option is swap as i remmeber i got confused with that part (sorry but it's been a while since last dualboot install and my memorry is filled with other things). anyway once past this it's all self explanatory and should proceed well. 

on boot grub will give you various options including booting windows and windows recovery as well as Ubuntu.

---

### Post by bcbc on 2013-11-07
If you only get the "Install Ubuntu Inside Windows" option it means that your hard drive has 4 primary partitions already and therefore the installer cannot partition. This option you see is actually offering Wubi (believe it or not they forgot to remove it from Ubiquity) and it does nothing other than copy wubi.exe to the C: drive Startup folder so that Wubi runs the next time you boot Windows.

Anyway, if you want a normal dual boot, then you have to remove one of those partitions first. Probably some OEM tools partition and then do some resizing to get some space.

Ref: [http://askubuntu.com/questions/69481/why-dont-i-have-the-option-install-ubuntu-alongside-with-them]("http://askubuntu.com/q/69481/14916")

---

