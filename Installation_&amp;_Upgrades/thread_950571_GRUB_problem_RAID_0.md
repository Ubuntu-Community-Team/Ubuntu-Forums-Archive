---
title: "GRUB problem RAID 0"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Sir Ali on 2008-10-17
Hi Folks,

I have 3 HDD's, 2 used for Windows Boot, Software and Games in RAID 0. The other is a 500GB used for storage. I assigned 100GB of that 3rd HDD for installing Ubuntu.

Now the problem is, I cannot boot to either Ubuntu or Windows because I assume GRUB was installed on the RAID array which is not read in the Live CD.

So what should I do now? I'm gonna re-install Ubuntu again so I'd appreciate someone to give me instructions of what I need to do to have GRUB boot my RAID array into Windows and the third HDD to Ubuntu.

Thanks,

Ali.

---

### Post by zero7404 on 2008-10-17
> **Sir Ali said:**
> Hi Folks,

I have 3 HDD's, 2 used for Windows Boot, Software and Games in RAID 0. The other is a 500GB used for storage. I assigned 100GB of that 3rd HDD for installing Ubuntu.

Now the problem is, I cannot boot to either Ubuntu or Windows because I assume GRUB was installed on the RAID array which is not read in the Live CD.

So what should I do now? I'm gonna re-install Ubuntu again so I'd appreciate someone to give me instructions of what I need to do to have GRUB boot my RAID array into Windows and the third HDD to Ubuntu.

Thanks,

Ali.

what version of windows are you using ? also, what version of ubuntu did you install ?

also, which device is set to boot first in your bios, raid ?

---

### Post by Sir Ali on 2008-10-17
> **zero7404 said:**
> what version of windows are you using ? also, what version of ubuntu did you install ?

also, which device is set to boot first in your bios, raid ?

Using Vista Business x64, Ubuntu 8.04 and yes RAID array boots first.

Is there some way to let GRUB only appear when I choose the 3rd HDD as the first boot device?

---

### Post by zero7404 on 2008-10-17
> **Sir Ali said:**
> Using Vista Business x64, Ubuntu 8.04 and yes RAID array boots first.

Is there some way to let GRUB only appear when I choose the 3rd HDD as the first boot device?

well, im no expert but i have installed 8.10 a few times, so i can tell you what i did that worked. your scenario is similar to mine, except i installed ubuntu on an external usb drive and i set my bios to boot first from cd, second from usb, third from raid.

prior to installing ubuntu, i unplugged the raid array completely. when i installed from the live cd, it found only the external drive. so i created 2 partitions on it at the beginning of the disk (you do this during the installation process), the first is the ext3 journaled partition, the second is linux-swap. the rest i left unallocated so that i can go back to windows and set it up as ntfs in order for both OS's to read and write from (shared area).

the reason why i unplugged the array was because ubuntu will use the MBR on it to write boot loader info. this way, it never touched my MBR for windows.

shut down, plug your raid back in, then in the bios, set your boot sequence to read the ubuntu drive first, raid second.
after you boot into ubuntu, you must install dmraid (you need to start synaptic package manager and search for dmraid, when you mark it for installation it will also mark any additional packages that are necessary--you may also want to install gparted while you're there). after install is done, to verify that it went down ok, start up gparted and you should be able to view the raid array. don't do anything to it, just verify it's there.

now, you must modify GRUB in order to include your windows installation. do so with this as a guide, it should work: [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

the above link should be all you need to make changes to GRUB so you can boot up to windows.
if you are willing to reinstall windows (if you have backups of your partition or files) then I would recommend doing as I did above. otherwise you can insert your windows cd, and attempt a repair of windows to see if that overwrites the MBR back to the way it was. after than, you can follow what I did and reinstall ubuntu.

---

### Post by zero7404 on 2008-10-17
in GRUB there are options to change the default OS on bootup and timeout before it executes the boot into the OS.

everything in GRUB with an # to the left is just reading material.
near the bottom you will see a list of booting options, that is where you need to add Windows to. by default GRUB will load the 0 entry (or the first entry). you can add your windows OS to be the first if you wish to boot windows first, or you can add it last and it will appear as a choice when you hit esc. @ the GRUB menu (during boot)

---

### Post by Sir Ali on 2008-10-18
Thanks a lot mate. I think this should work out without any problems. I'll download the BETA of 8.1 and try your method. :)

---

### Post by zero7404 on 2008-10-18
> **Sir Ali said:**
> Thanks a lot mate. I think this should work out without any problems. I'll download the BETA of 8.1 and try your method. :)

there are lots of tools that you can use to backup your data and partitions...Mocrosoft's robocopy (see here [http://blogs.techrepublic.com.com/window-on-windows/?p=777](http://blogs.techrepublic.com.com/window-on-windows/?p=777))
or you can search around the linux world for backup utilities.

i use acronis disk director 10 (for partition management in windows) and true image 11 to back up partitions and data.

your windows partition is still there, so you may want to back it up in case you need a quick way to restore...

---

