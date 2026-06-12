---
title: "Unable to locate grub after dual boot"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by chinmayzen on 2012-09-12
Hi,

I wanted to dual boot Win7 and Ubuntu 12.04LTS. So, I installed Win7 first.
Then I installed Ubuntu 12.04LTS, using the "side by side" option and it went through fine and I got the grub loader asking for which i wanted to boot.

Then, there was around 100gb or unallocated space which I made as a partition of windows. After performing that operation (I don't know if that is consequential), I'm unable to boot to any of the operating systems.

I get this error message-
error: no such parition
grub rescue>

I can view the Linux filesystem and the Windows Drives and Data when i boot through the USB (and am composing this post hence).

I think the grub menu.lst (??) or an equivalent of it in 12.04 file is lost. I'm new to this "new" Ubuntu. 

Thanks for the help.

---

### Post by oldfred on 2012-09-12
Welcome to the forums.

We need to see details. Run the BootInfo report and post the link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by chinmayzen on 2012-09-12
Thanks oldfred. I had created this account way back, I was surprised when I entered my universal login credentials- they were accepted! The problem of getting stabilized with LTS releases is that you get rusted with settings and solving bugs yourself- including other external factors which squeeze time out of my favorite OS. :D Anyways.

I did try boot-repair and it worked. I was able to boot to Win7, and re-installed Ubuntu12.04.

However I am inclined to learn more about this new grub loader that is there in 12.04LTS. I'll google and sniff around. I couldn't find the menu.lst (in the interim stage when i actually had the problem). Maybe it's there now, but I've heard things about something called "grub2" coming in which maybe means it won't be.

Thanks for the interest! I'll keep checking this place now and then if i may be of any assistance to people and also stay updated with the latest developments- so I don't get caught off-guard the next time (or have to yield to laziness). :D

PS- This new UI "Unity" ? doesn't feel nice. I'd better see if i can get the old GNOME with 12.04LTS.

---

### Post by oldfred on 2012-09-12
Some that have stuck with Unity have posted they like it.

Some of us  stuck in the mud old timers just default to what we know.
gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

Grub2 does not have menu.lst. The old menu.lst had parts that you could edit and parts that were auto-updated. With grub2 those parts are now separated and on a sudo update-grub all the parts are combined into one file grub.cfg which is not editable. 

 Grub2 wiki page - also see links to additional pages 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by KMilburn on 2012-09-13
I too have the same problem of grub not working after a dual boot install.
Boot-Repair created the following:
   [http://paste.ubuntu.com/1201849](http://paste.ubuntu.com/1201849)

I was able to recover Win7 by cleaning its MBR.  After Ubuntu installation the boot goes directly to Win7.  I used live to generate the above report.

All this started while trying VirtualBox.  I lost the use of my passwords.
Trying to fix that caused me to re-install.  Things went from bad to worst.  It's been a long day.

I hope someone can help.

---

### Post by YannBuntu on 2012-09-13
Hello
> **KMilburn said:**
> Boot-Repair created the following:
   [http://paste.ubuntu.com/1201849](http://paste.ubuntu.com/1201849)

Boot-Repair's final window told you:
> The boot files of [Ubuntu 12.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


Have you tried this suggestion?

---

