---
title: "boot HDD not reconised by pc"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by doja on 2013-03-30
Hi, I don't know what I messed up, but my booting is damaged.

 Now I started pc via live cd, opened  GParted, but it find no device there. ( I have now only one HDD with the OS's connected). On the terminal the command "sudo blkid" find only the live cd.
The "sudo fdisk -l" doesn't react.

 I get this problem yesterday. I think after playing with GPrted, even if I didn't change anything at the end.
The monitor gets unexpected frozen at first. After restart I couldn't boot. Get the messige about NTLDR. Then I restarted with live CD, where I couldn't see the HDD with OS in GParted at first. At the end it worked for a while again, even if I didn't change anything, and now I get the same problem. 

Thanks for helping.

---

### Post by dabl on 2013-03-30
> **doja said:**
> 
 I get this problem yesterday. I think after playing with GPrted, even if I didn't change anything at the end.


GParted is nothing to play around with -- especially if all your data are not securely backed up first.

If you didn't wipe out something essential, you should be able to recover with the Boot Recovery tool here: [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Also note that some motherboards need the "boot" flag set on the bootable partition.

---

### Post by darkod on 2013-03-30
Looks like hardware failure. Even if you messed up the partition table completely, fdisk should report the disk as present in any case.

Try with parted too, from live mode:
```
sudo parted -l
```

If that doesn't report /dev/sda, most likely it's the disk itself.

---

### Post by doja on 2013-03-30
The hardware failure came up in my mind after I posted my problem.
I checked the connections of the HDD and switched a plug in on Motherboard. Now I can boot again.
But I** thought** that even if I use live CD I'm still using the HDD. That if there would be no connection to HDD
I couldn't start even from the Live CD.

Dabl you are right Gparted is nothing to play around. :-) But I'm carefull with my data.
I tried the repair tool you made a link to before my posting but after starting this tool it
 gave me no option  ' Recommanded repair' There was only the button 'create a bootinfo summary'. 
But I will try it now  when I can boot again, maybe it find some bug.

My status quo is that I can now boot from my HDD where I have 3 OS. XP and then 2 Ubuntu.
I wrote that I get screen freze. I found out that this freeze is given by using Firefox. Before starting this application everithing is ok.
After trying to start browser I get screen freeze. I deinstall and reinstall Firefox. I additionally install chrome. And both browsers cause a freeze.

If I start my second Ubuntu installation broswer is running fine. There are no problems.

I don't know if there is still some bug in booting that can appear maybe again or if it was really only a connection.
I would like also repair the browser problem in my standard ubuntu installation.

Can you give me some links for commands or tools that can check it?

---

### Post by dabl on 2013-03-30
When you boot a Live CD, there is no involvement of the hdd -- there doesn't even need to be a hard drive on the computer.

If your system is booting and running reliably, then it sounds like maybe there is a video issue or maybe only a Firefox issue.  In that case, you should start a new thread in the multimedia or desktop forum to deal with that issue.

---

