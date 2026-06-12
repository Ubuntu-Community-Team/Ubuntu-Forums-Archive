---
title: "No GRUB2 menu at boot"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by mlittlej on 2013-04-26
Hi all,

I'm trying to install Ubuntu (I've tried both versions 12.04LTS and 13.04) onto my work laptop, in a dual-boot scenario with Windows 7.

Currently I have something that looks like this:

```
/dev/sda
    /dev/sda1    ntfs    Windows 7 (loader)     75 GB
    /dev/sda5    ext4    Ubuntu 13.04           80 GB
```

However, when I boot the system, I'm not presented with a GRUB2 menu like I have previously. I'm instead dumped directly into my Windows 7 boot sequence.

I would completely remove the Windows parition if it weren't for the fact I do need to use it from time to time, so that's not an option.

I was wondering if anyone would be able to either tell me what I'm doing wrong during the installation, or point me to some steps that would allow me to recover the GRUB2 menu into a use-able state.

Also, if you need/want any further debugs or system info, would you tell me which commands you want me to run. I'm definitely in the "beginner" category so far as Linux use is concerned.

Much obliged,

NB: Just before I post; I just tried installing 13.04 again and it's killed the Windows MBR. To the recovery disk! I'm certain this is a user-problem.

---

### Post by darkod on 2013-04-26
Do you maybe have one of those hybrid setups of hdd + ssd for caching?

Sometimes grub2 doesn't install correctly on the MBR but in most cases you can only add it, provided the rest installed fine.

Let us know how it goes after you restore windows and try to install ubuntu again.

---

### Post by mlittlej on 2013-04-26
Hi Darkod,

No, it's a single SSD drive in the laptop (Lenovo ThinkPad W520, if that helps at all). I've restored the Windows entry to the MBR at least and tried the installation again, but I'm simply not getting anything.

Got any suggestions?

---

### Post by oldfred on 2013-04-26
Lets see all the details:

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by mlittlej on 2013-04-28
Thanks for the links oldfred.

I didn't know about the boot-repair  tool (like I said; I'm a fresh faced, intelligence-proof idiot when it  comes to Linux) so that's a useful piece of knowledge to have gained. I  ran the tool at it seems to have sorted out all my GRUB problems for me.

I  couldn't garner any information from the BootIfno outputs though, maybe  you'd be able to tell me where I have been going wrong?

Pre-fix: [http://paste.ubuntu.com/5613030/](http://paste.ubuntu.com/5613030/)
Post-fix: [http://paste.ubuntu.com/5613045/](http://paste.ubuntu.com/5613045/)

Marking as solved, thank you for the help.

M

---

### Post by oldfred on 2013-04-28
There must have been another internal change to grub2. I just ran bootinfoscript which is the first part of BootInfo and it also says the MBR is looking for partition 94. So that is an error in the script.

I do not see what may have been wrong. Sometimes grub2 just does not install its boot loader to the MBR. And sometimes there are reasons like RAID, dyamic Windows partitions, gpt left over data, partition table corruption,  or other issues where grub then gets confused. If you were able to install, then you did not have any of those technical issues.
If you can boot then it is good.

---

