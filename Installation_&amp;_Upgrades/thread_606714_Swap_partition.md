---
title: "Swap partition"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by MarsmanA on 2007-11-08
Hi!
I have a problem. I tried to install Ubuntu on a VM, but when partitioning starts I get this message:

The creation of swap space in partition #5 of SCSI1 (0, 0, 0) (sda) failed.

I tried the Guided and Manual way but the result is the same. Can somebody help me please? Thank you.

---

### Post by slowmo on 2007-11-08
Hi 

I have just been trying the same thing myself I was getting the same error message. 

The following manual changes got me past the error message: 

Partition 1 (Root "/")

Primary Partition
Ext3 (File Type)
Mount at /
Placed at the beginning

Partition 2 (Swap)

Logical Partition
Swap (File Type)
No option to choose place to mount
Placed at the end

Partition 3 (Home)

Logical Partition
Ext 3 (File Type)
Mount at /home
Placed at the beginning

This got me past the error message but I have not yet managed to install it as it seems to get stuck when 'Scanning the mirror' at 82%. I haven't worked out what the problem is from there but if you are using a different VM program than me this might work for you. I'm using Virtual Box. 

Good luck, hope this helps.

---

### Post by MarsmanA on 2007-11-09
Hi slowmo and thank you!

I just changed the swap partition from Primary to Logical and all went smooth. I didn't need the home partition. Ubuntu is now installed and running. Strange because I used the same VM - VirtualBox.

Hope you will resolve your problems, good luck

---

