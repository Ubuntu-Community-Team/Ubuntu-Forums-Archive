---
title: "Troubleshooting unreliable booting-up process"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2011-11-23
I have a computer that came with Windows 7. I used Wubi to install Ubuntu 10.04 on the computer and use Linux as my operating system almost exclusively.

I was recently invited to update my kernel from 2.6.32-34-generic to 2.6.32-35-generic. I did.

That change has been causing me problems, because the boot process now sometimes stalls.

I've been overcoming that by powering off my computer and starting it up again. Sometimes, that works, sometimes it doesn't. If it doesn't I've been starting the computer yet again and selecting kernel 2.6.32-34-generic. That usually works.

Today, however, I had a far more serious problem. Powering off my computer caused crucial Wubi files to be moved and renamed in Windows, so that, until I moved them back and renamed them (using a Knoppix live CD), I couldn't boot up in Linux at all.

That scare's made me realise how important it is to find out why 2.6.32-35-generic sometimes fails to work.

I assume that some log file will tell me why the boot-up process fails. Can someone please tell me which is the log file that I should be looking at and what I should be looking for in that file?

Leslie

---

### Post by darkod on 2011-11-23
Wubi is only for a short try. If you started to use ubuntu almost exclusively I think it's time to consider a proper dual boot instead of wubi inside windows.

Things will keep popping up in wubi.

---

### Post by lesliek on 2011-11-23
Thanks for the quick reply, Darko.

Yes, I've been reading about that too.

The first thing I'd have to do there is to repartition my hard drive. Something I read about that, however, suggested that I'd need my Windows 7 installation CDs to complete that process successfully and I didn't get any installation CDs with my computer, just some hidden partition on my hard drive about which I understand nothing.

It was that that made me think that the first thing to try to achieve was just to stabilise the boot-up process. If you have any further thoughts about my original questions, I'd be very grateful.

Thanks again,

Leslie

---

### Post by darkod on 2011-11-23
I don't know much about wubi and what might be causing this.

But if it helps your future plans, just to tell you that you don't need the win7 dvd to resize partitions (make unpartitioned space for ubuntu).

You should use the Windows Disk Management which can resize partitions. First make a plan how you would like your disk to look like, and then resize accordingly. Boot win7 few times to do its disk checks if it wants. Do not create any partitions in the newly created unpartitioned space, ubuntu doesn't use NTFS.

After that you are free to install ubuntu when ever you want. You can choose to either install manually creating partitions or use one of the automatic methods.

---

