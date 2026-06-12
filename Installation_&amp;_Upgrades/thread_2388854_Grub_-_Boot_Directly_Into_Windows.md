---
title: "Grub - Boot Directly Into Windows"
date: 2018-04-08
forum: Installation &amp; Upgrades
---

### Post by mark425 on 2018-04-08
My laptop boots directly into Windows.
In the past I experienced a similar problem and I solved by changing a parameter in a filesytem as proposed in one of the discussions in the forum. But I do not manage to find the topic. 

I have tried with boot repair, but with no result.

The problem returned because I manually changed the BIOS order with F9 to boot into a usb.

---

### Post by yancek on 2018-04-08
> 
The problem returned because I manually changed the BIOS order with F9 to boot into a usb

Change it back?  If you ran boot repair, it should have given you a link to some output using the Create BootInfo Summary option.  If you didn't use that, run it again and do so and post the link here.

---

### Post by mark425 on 2018-04-08
[http://paste.ubuntu.com/p/VnBY5tp35z/](http://paste.ubuntu.com/p/VnBY5tp35z/)
(I think that I also created some unwanted boot paths...)

> Change it back?

I have just changed the order by pushing F9: I did not make any change to the "default" order.

---

### Post by mark425 on 2018-04-13
up

---

### Post by oldfred on 2018-04-13
What brand/model computer?

Original default was a hard drive boot. See line 755, and booting 3000.
But then it was updated to boot Ubuntu entry.
line 1096 show it defaulting to 0001 or the Ubuntu entry.

You also have this:
      >  The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume 



Grub only boots working Windows. That is Windows that does not need chkdsk nor is hibernated. In those  cases you have to directly boot Windows from UEFI boot menu and resolve issue in Windows or use a Windows repair flash drive.

Some systems will not boot an ubuntu entry. They violate UEFI standard that says NOT to use description and only valid description is "Windows Boot Manger". 
Many work arounds, you may have been using the fallback or hard drive entry that normally also works.

You now have several hard drive entries 3000, 3001, 3002 & 30003.
You probably only need one and can use your UEFI to remove or efibootmgr.
See this and the sudo efibootmgr -b command.
man efibootmgr

---

