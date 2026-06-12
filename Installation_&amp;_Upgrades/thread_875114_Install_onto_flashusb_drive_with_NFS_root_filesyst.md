---
title: "Install onto flash/usb drive with NFS root filesystem?"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Skyline77 on 2008-07-30
Hi

I have a computer already setup with a 40gig drive and ubuntu 8.04 installed working fine. This is the client (Dynamic IP from a router)

I have a second computer with lots of drive space and again running 8.04. This is the server. (static IP)

Both machines working fine. Samba is running and no problems on the network.

I'd like to make the client diskless. I don't want to go down the PXE path because I don't want the server to take over DHCP and install a TFTP server. Instead I have a cheap usb key and a cheap ata<->compact flash adapter. I also want it to support updates without having to manually copy over kernal images to the usb key or compact flash.

I've done a fair amount of reading and searching. So here is what I've learned (not an expert).

1. Choose either the USB flash key or ATA <-> compact flash adapter.
2. Install just the bootable kernal image to the flash device.
3. Make the kernal pick up its root filesystem from nfs.
4. Install NFS on the server and copy over from the working system on the 40 gig drive.

If this is right.. I need some help because I haven't a clue what I'm doing with the kernal stuff. I can just about get my head around NFS on my own but need help with setting up the rest..

Thanks for any advise.

---

### Post by jimv on 2008-07-30
If the USB drive is 4 gigs or more, you can install Ubuntu on it like any other HD.

---

### Post by Skyline77 on 2008-07-30
> **jimv said:**
> If the USB drive is 4 gigs or more, you can install Ubuntu on it like any other HD.


Its only 512mb. 

Also I want to get NFS working so that I don't ware out the USB key with repeated read/writes. It will also be a lot faster being gigabit.

---

### Post by Skyline77 on 2008-07-31
Any guides about?

---

### Post by Skyline77 on 2008-07-31
OK I've found this thread but no solution and is basically what I need to do.

[http://ubuntuforums.org/showthread.php?t=473711&highlight=nfs+boot+root+diskless](http://ubuntuforums.org/showthread.php?t=473711&highlight=nfs+boot+root+diskless)

Any ideas?

---

### Post by Skyline77 on 2008-07-31
bump

---

