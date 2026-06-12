---
title: "After update system unable to find /home"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by tron^qld on 2011-03-10
Yesterday did a fresh install of UNR 10.10, all went well with that.

After the first log in it found the Wifi and checked for updates. 

Updated the system and then it went to restart the system due to a Kernel upgrade. 

Once I did this, that is when the issues started. Firstly when booting up, it just sat at the Ubuntu boot up screen saying:

"The disk drive for /home is not ready yet or not present"

'Continue to wait; or Press S to skip mounting or M for manual recovery'

So firstly I hit S, this presented me with several error boxes (as expected due to setup/config files sitting in my /home folder), I then found that I wasn't able to connect to my wifi (not that it can't see it, just that it won't connect) each time I try and connect it just comes up saying that the wifi is disconnected. Of all the things to fail I was expecting the Bluetooth to and it didn't...

Anyway the computer specs are: MSI Wind U100, upgraded to 2 Gig Ram, 320Gig HDD, and wifi card is the Realtek RTL8187SE. 

HDD is setup as:

4Gig for Swap (/dev/sdb1)
6Gig for / (/dev/sdb5)
Remainder is /home (/dev/sdb6) (I did make this an encrypted partition)

Sorry can't do any screen shots as I am not able to connect to the internet on that machine (having to use another computer in the house).

I have tried to view the fstab file and I am not able to.

Any help would be great. 

Thanks for reading...

---

### Post by Hedgehog1 on 2011-03-10
Hey there tron^qld!

Well, we do need to see the fstab file, so here is a sneaky trick (hedgehogs are good at 'sneaky'):

On the misbehaving laptop/netbook, after you get past the error messages, do a **[cntl]+[alt]+[t]** (all three keys at once).  This will bring up a terminal session.

Put in your USB drive, and then:

```
gksudo gedit /etc/fstab
```

The 'Save As' the fstab file to the USB stick, and bring the USB stick to the computer you are posting from. You can put the text of the file into your next post.

***The Hedge***

:KS

---

### Post by tron^qld on 2011-03-11
> **Hedgehog1 said:**
> 
The 'Save As' the fstab file to the USB stick, 
***The Hedge***

:KS

Ok so I can't even open/access a USB stick on the netbook...

So I will just type it out here...

[CODE]

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the unversally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>     <dump>  <pass>
proc             /proc           proc   nodev,noexec,nosuid 0     0
/dev/sda5        /               ext4   errors= remount-ro 0     1
/dev/sda6        /home           ext4   defults        0        2
/dev/sda1        none            swap   sw             0        0

[CODE]

sorry for the formatting....

I was thinking that the '/dev/sdaX' should be reading '/dev/sdbX' where X=partition number.

---

### Post by tron^qld on 2011-03-11
> **tron^qld said:**
> 


I was thinking that the '/dev/sdaX' should be reading '/dev/sdbX' where X=partition number.

OK so I just thought that I would update the fstab file to show sda to be sdb...

And it all works...

So all fixed... 

Feels good when I work it out myself...

Hope this helps someone in the future...

---

### Post by Hedgehog1 on 2011-03-11
> **tron^qld said:**
> OK so I just thought that I would update the fstab file to show sda to be sdb...

And it all works...

So all fixed... 

Feels good when I work it out myself...

Hope this helps someone in the future...

[SIZE="4"]*Well Done!*[/SIZE]

***The Hedge***

:KS

p.s. Hedgie Snacks all around!

---

### Post by conata on 2011-08-19
> **tron^qld said:**
> OK so I just thought that I would update the fstab file to show sda to be sdb...

And it all works...

So all fixed... 

Feels good when I work it out myself...

Hope this helps someone in the future...

Hi, i have the same problem and i don't understand what do you doing, please, can you help me? :confused:

---

### Post by Elfy on 2011-08-19
Please start your own thread - direct new thread link - [http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)
The OP has not been here since MArch.

Thread closed.

---

