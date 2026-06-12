---
title: "just installed on dual boot, no boot or grub; why?"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by idiotprogrammer on 2012-05-23
I have a install boot problem with Ubuntu 12 Precise Pangolin. I installed  64 bit ubuntu  on a system which is 8 years old. I'm installing it on a separate partition natively (i.e., no wubi)   I'm unclear about what I should be doing to solve the problem.

First, I do not have a working INternet connection. I cannot get my wireless card to work. That is a side issue, but affects my ability to download utilities. 

I have installed Ubuntu on an older machine with Vista 64 on it. After I installed, when it rebooted, it did not boot into ubuntu at all, but just went straight into windows. No grub, no nothing. 

sdb1 contains Windows system (and I think this partition is bootable). 
sda5 contains my linux boot
sda6 contains swap. 
I also also have a sdc. with personal files on it. 


Let me say that I've had problem with mbr in Windows in the past, so the MBR on the hard drives  might be finicky. Maybe  only sdb1 mbr is working (and not corrupt). I honestly don't remember, but that is a possibility. 

If I remember, I had to play around in the bios to set which drive will boot the system up.  I just rearranged the boot order in the bios. When I change the order (in all variations), I can error messages in all cases except when the partition with Vista 64 is being given top priority. 

Possibly I might want to add a reference to linux in the windows boot loader. (I'm not sure how to do that, but I remember it being possible). 

the only thing I can do is boot into the live cd, mount the linux partitoin in the file manager and read config files. When I ran gparted, I changed the flag for sda5 to be "boot"

I haven't figured out how to run grub within a Live CD environment or if I even should. I can sudo into root in LiveCD

I'm not sure if grub is configured correctly to load upon startup. I don't even know how to check. 

What kind of steps would I need to do to get linux running? Would I be required to run grub to get it to start up. 

What are some possible reasons why Windows Vista would prevent grub from first starting? 

Thanks for your help.

---

### Post by wilee-nilee on 2012-05-23
We use a script to look at boot issues, using a Ubuntu live cd down load it from the link and extract it to your desktop. Then run the command and open the generated results.txt and copy and paste all the text to a reply.
 
When you open the reply click on the # in the reply panel and paste that text between the code tags.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```There is also a boot-repair app that can be used from its bootable cd, you would just run the recommended repair. I suggest this as well as there seems to be a limited net access if I read this correctly

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by idiotprogrammer on 2012-05-23
Willee-Nilee, thanks for your help. Boot Repair Live CD might be the answer. 

I'm working on upgrading my wifi adapter, so maybe I might have Internet access again before I solve this problem.

---

### Post by darkod on 2012-05-23
If you used one of the auto methods to install, grub2 should be on a MBR on one of the disks. In this case it's just a question of booting from the correct disk.

If you installed manually and selected to install grub2 to a partition, like sda5, then it's normal you don't see grub2 since it should be on a MBR.

If you can, run the script as wilee said.

Can't you connect to the internet with a cable? It's always best to start off with a wired connection especially when you need drivers so your wifi can work.

---

### Post by idiotprogrammer on 2012-05-23
Can't you connect to the internet with a cable? It's always best to start off with a wired connection especially when you need drivers so your wifi can work. 

Practically speaking, I can't use a wired connection in my room, but I have a linux-friendly wifi usb, so I should be able to troubleshoot this problem while online.

---

### Post by idiotprogrammer on 2012-05-26
this problem was solved after I installed with an internet connection. grub worked -- no problem. Awesomeness!

---

