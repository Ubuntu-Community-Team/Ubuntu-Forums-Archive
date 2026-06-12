---
title: "yet another &quot;unable to find medium containing...&quot; bug"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by rgo on 2011-02-27
Hi together,

I have already read the related threads but unfortunately, none of the solutions works/ applies to my problem:
Having Ubuntu 10.10 as bootable DVD, I am trying to upgrade from Jaunty. When I do so however, after selcting "Install Ubuntu 10.10" in the installer menu I get the "[unable to find medium containing live file system" error. ]("http://forum.ubuntuusers.de/topic/unable-to-find-medium-containing/")
I already installed grub2 and set acpi=off, my DVD is on primary master and, obviously boots as well.

Do You have any suggestions?

Thanks a lot & kind regards

---

### Post by sikander3786 on 2011-02-27
Welcome to the forums :-)

If this is the regular Ubuntu desktop image, burning it to a CD-ROM disc might help you boot and install successfully.

Also, you should check the downloaded image's MD5SUM if not yet done.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And check the disc for defects. Burn the disc at the lowest possible speeds. (4x)

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by rgo on 2011-02-27
Hi Sikander3786,

thanks for the welcome & reply.

Actually, I purchased the CD ( contained within a reliable IT Magazine ) so I am very sure the source I am trying to install from is not the problem.( I didn't want to go through downloading an ISO. I have done that before and back then got stuck with burning errors or flawed Images)

Do you have another Idea?

---

### Post by sikander3786 on 2011-02-27
Check the disc for defects as mentioned in the link I posted above.

You can create an iso image from the DVD and later burn it to a USB drive and try installation from it. I know, DVDs have been causing some installation problems.

Please let us know if the disc is ok so we can proceed.

---

### Post by rgo on 2011-02-27
As I just found out, the DVD doesn't contain an Ubuntu iso file 

(but an ubuntu nebook -iso with correct Hash  6877bf8d673b87ba9500b0ff879091d0)

Instead, there is an "ubuntu" folder containg various files which I suspect are meant to install 10.10 Desktop. List:

file:///media/cdrom0/ubuntu/preseed/cli.seed
file:///media/cdrom0/ubuntu/preseed/ltsp.seed
file:///media/cdrom0/ubuntu/preseed/ubuntu.seed
file:///media/cdrom0/ubuntu/filesystem.manifest
file:///media/cdrom0/ubuntu/filesystem.manifest-desktop
file:///media/cdrom0/ubuntu/filesystem.size
file:///media/cdrom0/ubuntu/filesystem.squashfs
file:///media/cdrom0/ubuntu/initrd.lz
file:///media/cdrom0/ubuntu/vmlinuz


So, assuming the people publishing the source DVD knew what they where doing, and further assuming the DVD is free from defects, is there ,in your opinion, another way to solve that problem without getting 10.10 from another source and probalby running into the same issue again ?

---

### Post by rgo on 2011-02-27
The DVD also contains a Live Version of 10.10 which works nicely. I.e. I can boot and run 10.10 from the DVD, but installing doesn't work. Therefore to me the it seems very unlikely that the issue is  caused by the DVD.

---

### Post by sikander3786 on 2011-02-27
The hashes are good and the DVD is not defected, well I fear I don't have much thoughts left here.

The only option in my opinion is to download an Ubuntu iso and boot from a CD or USB drive.

Some other members might jump in with new thoughts.

---

### Post by rgo on 2011-02-27
Ok, thanks alot anyway for your efforts !

Pehaps someone else has got an idea?

---

### Post by rgo on 2011-03-05
Hi togehter,

sorry to come up again with the topi  :-( , but I downloaded the ISO & made a bootsable DVD and still get the same error. 

Do you have any suggestions?

Thanks a lot!

---

### Post by sikander3786 on 2011-03-05
Did you try with a CD or a USB drive? DVDs are known to cause problems, I know.

---

