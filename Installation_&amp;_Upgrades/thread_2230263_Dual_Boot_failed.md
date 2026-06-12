---
title: "Dual Boot failed"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2014-06-18
Attempted a dual boot of my mom's pc. Win 7 Home Premium 64 bit (already installed).
Installed Ubuntu Lucid Lynx (10.04). But I chose the manual setup, thought I knew what I was doing.
There is only one drive in the pc. I chose the new partition and create a swap partition of 8 GB, then an ext4 partition of the remaining 240 GB.
Chose to put swap at the end.
After install and reboot, GRUB2 showed ONE TIME ONLY.
I chose Windows 7 (and it rebooted).
Then I just got GRUB RESCUE. Then, I couldn't boot to either OS.
So, I ran Boot Repair, which allowed me to get BCD back and not GRUB.
But even then, I still can't boot Windows. I can ran Recovery partition, but it after it runs it just says "can't complete".
At this point, I'm not even going to attempt to dual boot anymore. Either BCD got fried or the 100 MB partition got fried.
Can someone tell me what I did wrong? Should I have gone with Automatic dual boot install? It didn't work last time I did it.

For now, I'm just going to wipe the drive complete and put ONLY Linux on it. They don't use Windows anyways, they just go online.
Will wiping the drive, wipe MBR and GRUB to make it fresh BEFORE i re-install Ubuntu?

Thanks.

---

### Post by yancek on 2014-06-18
The obvious first, Ubuntu 10.04 is not supported any longer.
Clarification, after the Ubuntu install you rebooted and selected windows 7 and were able to boot to it, correct?
Did you then reboot and select Ubuntu and it did not boot?
Posting more information such as the bootinfoscript output might help someone to help you.
If you want to just reinstall and start over, select the Erase disk option and install Grub to /dev/sda if you get the option.

---

### Post by kakashi_12 on 2014-06-18
If I install fresh, will it wipe MBR and grub for me to start fresh?
should i bother with creating a swap? Will the automatic install create one for me?
It already has 4 GB of RAM and a 2 or 4 core at 2.47 GHz.

No, I selected Win7 and it never did boot. It rebooted. Then went to GRUB rescue screen not being able to boot anything at all. Not even GRUB itself.

---

### Post by oldfred on 2014-06-18
Please see this sticky thread in the Installation sub-forum.
       Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.
    [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

The automatic new install with full system overwrite erases everything, but only creates / (root) and swap with some sort of default sizes. I prefer to use Something Else but then you have to specify partitions sizes, mounts like / or /home and formats like ext4.

If hard drive is larger it is better just to have a smaller / of 20 or 25GB and use the rest of drive as /home or data partitions.

If you want to post the BootInfo report from Boot-Repair we can see where you are at and if it is easily repaired or not.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kakashi_12 on 2014-06-18
Installed with default settings. But FireFox and Chrome are both failing to work. I can open up a new thread if necessary (since this is a different issue now), but need help. Unless you have an idea.

---

### Post by oldfred on 2014-06-18
Please start a new thread.

Check this first.
Is Internet working? Did you install with hard wired Ethernet as sometimes it has to install wireless drivers as there is a variety and Live installer does not have all.

---

### Post by kakashi_12 on 2014-06-18
[http://ubuntuforums.org/showthread.php?t=2230319&highlight=firefox](http://ubuntuforums.org/showthread.php?t=2230319&highlight=firefox)
NEW THREAD

Yes, I have an internet connection. no problem. I can get to the home page. The browsers just keep freezing up.

---

