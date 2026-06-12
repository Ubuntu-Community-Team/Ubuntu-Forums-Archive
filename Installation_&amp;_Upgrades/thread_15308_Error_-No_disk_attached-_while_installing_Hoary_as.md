---
title: "Error -No disk attached- while installing Hoary as guest on VMWare 4.5.2"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by vitol on 2005-02-13
I have followed the instructions on [http://www.omegatower.com/library/ubuntu-warty-on-vmware.htm](http://www.omegatower.com/library/ubuntu-warty-on-vmware.htm) but to install Hoary from ISO cd as a VMWare Worstation guest OS.

There is Hard Disk (SCSI 0:0) configured in VMWare.

I can not pass step 9 because of Partition disk problem:
No partitionable media
No partitionable media were found.
Please check that a hard disk is attached to this machine.
](*,)

In terminal 3 I can read
inmod /lib/modules/2.6.10-2-386/kernel/fs/isofs.ko
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No volume groups found
  Reading all physical volumes.  This may take a while...
:confused:
  
Does anybody experience similar problems?
Please let me know.
Vitol

---

### Post by kamoku on 2005-03-15
This looks exactly like what I just experienced, with Hoary as a guest on VMware 4.5.2.  Were you able to move beyond this?  If anyone can provide any suggestions or assistance, that would be most appreciated!  Thank you.

---

### Post by lfrossati on 2005-03-17
I did it choosing IDE disk when creating the virtual machine. Maybe there is some problem to recognize scsi disks with ubuntu.

---

### Post by dillweed on 2005-03-17
I've also tested Ubuntu as a guest on Vmware as well as other distros.  Before I install I always make sure to change the default scsi hd to an ide HD .  For some reason vmware doesn't agree with me and scsi and linux even though vmware says that it recommends scsi.  This was cause with Slackware, gentoo, mandrake and it looks like Ubuntu.

---

### Post by kamoku on 2005-04-02
Thank you.  That worked!  I made another attempt to install it by selecting IDE instead, and Hoary installed like a charm.  (Hoary as guest OS on Windows XP PC)

---

### Post by grahamt on 2005-05-05
Spot on advice.  I'm running VMWare 4.5.2 Build 8848.  I got exactly the same symptoms.  Had to build the virtual machine in Custom Mode rather than Typical.  Typical insists in presenting the Hard Drive as a SCSI drive and you can't change it.  You can only make it an IDE drive in a Custom build.  After that, the install works.

---

