---
title: "Grub problem - No Win xp option"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2009-12-22
I have ubuntu 9.10 installed on the same partition as win xp on C:\ drive thru Wubi. Everything was working fine. But After one of the reboots, I could not load ubuntu. Just got to the grub prompt with minimal bash support. 
 
Till here, the boot options are fine - Both win xp and ubuntu are shown.
 
After browsing thru a few forum posts, I rebooted the pc with a ubuntu 9.10 live usb drive. Opened a terminal window and ran a cmd to install grub (not update-grub2). Rebooted the pc again and no longer see the 2 options to boot into either Win xp or ubuntu. I just see Grub loading and it goes straight to the grub prompt.
 
I am handicapped now. Neither windows nor ubuntu:-( 
 
plz help me restore the original boot options for dual boot!

---

### Post by darkod on 2009-12-22
Lesson 1: when you install wubi you DO NOT HAVE FULL UBUNTU!
Do not perform instructions for full ubuntu install because most of them do not work on wubi. Wubi is just a virtual ubuntu working from inside your windows.

Boot with your XP cd and restore windows bootloader as per the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

As for the sh:grub> error in wubi, to get it going again at the sh:grub prompt execute one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

If wubi is in your C: partition most probably the second command above will work with /dev/sda1. After you manage to boot wubi, open terminal and execute:
sudo update-grub2

That should get you going.

---

### Post by GeorgeOfTheBush on 2009-12-23
Thanks a lot darkod for a clear explanation.

I was able to solve the windows bootloader issue.

However, unable to solve the ubuntu boot issue. I am not able to find the "/boot" folder with vmlinuz entries to be used with the "linux" command on the sh:grub prompt. What could be wrong?

---

### Post by GeorgeOfTheBush on 2009-12-23
Any suggestions plz?
 
I dont have vmlinuz-* entries in my /boot directory when checked from the sh:grub prompt.
 
Could you please help me boot ubuntu?

---

