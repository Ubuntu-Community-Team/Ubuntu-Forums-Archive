---
title: "Grub Error on Raid 0 + USB HD's, first time linux experiance"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Syntax Terror on 2008-01-22
Hello Linux community, my first post here is a problem, sadly, I have been excited to dive into Linux after seeing and hearing much about it. 

I'm at work atm so dont know the exact specs, but my pc is a Dell Workstation 470. It has an onboard RAID controller (I believe all is Intel chips)

In it are 2 x 250 SATA drives in RAID 0, I run Windows XP pro on this. 

To give Linux a try, I attached a portable USB HD of 10 GB (BIOS supports booting from this device ) 
Downloaded the live CD, and selected to install Linux on the portable HD.

I was very carefull to select the proper HD, wanting to leave windows alone. Ubuntu went on to resize the 10 GB HD into a 3.7 GB partition, all seemed fine, after the proces was done and the CD ejected, I rebooted the PC and got a "Missing OS" error from the portable HD. Calling it a night I went to bed... (slightly annoyed but maybe I missed something, im noob when it comes to linux)

This morning I wanted to boot into Windows, (just the compulsory morning-check-my-mail routine ;)) I detached the portable HD, and turned on the PC, eek! "GRUB error" and system hangs!

What happened to my RAID? I can't boot into windows now, booting from the USB drive doesnt work, I inserted the live CD in slight panic as the possibility of all files being gone creaped up my spine. The live CD sees the USB drive fine, showing a swap partition, a linux partition and some unused space.

It gives a mounting error when trying to acces the disks.. I really at this point am a bit panicing, with the RAID not being seen... what happened? Why did GRUB mess with one, or both, of my SATA drives when I installed only on the USB drive? 

More important for me at this moment, can I get to my Data on these HD's, or is all lost?

Thank you for bearing with me on this, if I can get to my data, I'll be one happy guy and I wont give up on Ubuntu (I'm tired of Windows and Vista was the last drop) , so far tho this has been one nervewrecking experiance.. I hope someone can help me :)

ps: Searched the forums, tho a lot of GRUB questions I havent found anything useable for me, if I have overlooked a solution my excuse.

---

### Post by Pumalite on 2008-01-22
Fix you Windows MBR with your Installation CD os use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If reinstalling in USB, disconnect all internal drives.
(Stage 1 was left in your USB and stage2 in your sda or viceversa)

---

### Post by Syntax Terror on 2008-01-22
> **Pumalite said:**
> Fix you Windows MBR with your Installation CD os use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If reinstalling in USB, disconnect all internal drives.
(Stage 1 was left in your USB and stage2 in your sda or viceversa)

Thank you, I have downloaded Super Grub, burning it as I write.. thx for shedding some light on what went wrong, seeing how neither the USB nor the HD boots, this makes sense.. 

I will give Super Grub a try, do I have to take any special measures as it concerns 2 SATA disks in RAID-0?

I dont know if the MBR is also striped on RAID-0.. in fact if I get it working again I will step down from striping, to much risk  :) 

Thanks in advance Pumalite!

---

### Post by Pumalite on 2008-01-22
I have disable all my software Raids. They are a headache. But if you want to know, read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
And here are a couple of links that might be helpful:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Syntax Terror on 2008-01-23
> **Pumalite said:**
> I have disable all my software Raids. They are a headache. But if you want to know, read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
And here are a couple of links that might be helpful:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Thx Pumalite. Going to read thru it all this weekend and restore those disks, in the meantime I have disconnected to HD's and happy using my first linux finally. After a clean install, all is fine on Ubuntu front :) 

Thx for your time

---

### Post by Pumalite on 2008-01-23
You are welcome. Good luck.

---

### Post by wcorey on 2008-04-29
> **Pumalite said:**
> You are welcome. Good luck.

The problem is not with your hardware, it is not with bios RAID, it is not with Linux. The problem is with Ubuntu, pure and simple. Fedora 8, for one, honors the firmware raid just fine. Windows honors the firmware raid just fine. For the Ubuntu community to write articles on how to set up some other kind of "fake" RAID, or denigrate its use altogether, misses the entire point and is tantamount to saying, "If it doesn't work, don't use it". 

I am still waiting and searching for an article that explains why it is a bug in Ubuntu and what package needs to be updated to fix it. But before that happens Ubuntu has to acknowledge it is a bug, not a feature.

---

