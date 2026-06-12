---
title: "windows 7 and ubuntu 10.4 dual boot problem"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by GordonBooker on 2010-09-12
I install windows 7 ultimate. I then shrink the windows partition in windows.
I then restart windows a couple of times to ensure everything is ok with windows.
I then install ununtu 10.4 into the unallocated space.

When I restart, I can select the Ubuntu OS fine.
If I select Windows 7 (loader), the machine appears to restart and just go back to GRUB.

I did this process with a netbook using ubuntu nbr and it was fine.
I have tried this a few times.

The windows startup repair does not seem to change matters.

I would be glad of any help I am fairly new to dual booting.

Gordon

---

### Post by deepblue80 on 2010-09-12
Hi
I have the same issue except I dual boot XP and Ubuntu 10.4 for quite a few months without problems! After this instance I did run Ubuntu upgrade manager and it came up with an error mesg about GRUB. i reinstalled GRUB based on what came on screen at that point, I reinstalled it in the partition holding all of Ubuntu i.e didnt select a logical partition.
Now I am still unable to log into Xp and thinking of reformatting my system to use just Windows 7 - any ideas?



> **GordonBooker said:**
> I install windows 7 ultimate. I then shrink the windows partition in windows.
I then restart windows a couple of times to ensure everything is ok with windows.
I then install ununtu 10.4 into the unallocated space.

When I restart, I can select the Ubuntu OS fine.
If I select Windows 7 (loader), the machine appears to restart and just go back to GRUB.

I did this process with a netbook using ubuntu nbr and it was fine.
I have tried this a few times.

The windows startup repair does not seem to change matters.

I would be glad of any help I am fairly new to dual booting.

Gordon

---

### Post by Mark Phelps on 2010-09-12
> **GordonBooker said:**
> The windows startup repair does not seem to change matters.

So, I take it that the machine giving you problems is NOT the netbook, right?

Did you try running Startup Repair three times? It takes that many passes to make the needed corrections.

---

### Post by GordonBooker on 2010-09-13
Hi,
Thanks for replying.
The problem was not with the netbook machine but with the desktop machine.
I did try the windows repair 5 times, but it kept saying something about "if you have recently added hardware then remove it" (sorry I can't remember exactly).
I had not made any hardware changes though.

I have now changed tack and am going to try to install windows in a virtual machine within Ubuntu.

---

### Post by garvinrick4 on 2010-09-13
On page 8 of install you have to click advanced button and put in sda if using internal drive. Not sda1 or sda5 but sda
Somewhere along the line you do not have grub in the mbr of your drive. It is not hard to put it there. Download this script to desktop in Ubuntu and copy and paste this line of code and it will put a file on your desk with your whole boot arrangement. To DESKTOP
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

Post results in this thread.

---

