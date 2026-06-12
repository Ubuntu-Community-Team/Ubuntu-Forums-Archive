---
title: "Assistance for HD cradle with 1TB HD not being detected"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by danny-1ee on 2018-04-23
Hi Forum,

This is my first time posting and my first understanding Linux so please bear with me :).  I recently setup an ESXI box with Ubuntu server on it and attached HD cradle with a 1Tb and 2 Tb drive on it.  When I performed the fdisk -l, nothing is being detected or shown like how I would see when I google other people doing it.  I'm at lost, I'm not sure what it is I'm doing wrong.  I've formatted these drives with NTFS, but originally tried with ext4 cause I read ext4 is usually a better fit with linux, but I had to use a physical harddisk tool to repave both drives instead of doing it with gparted which I don't  think it would of worked since drives are being detected at all.  Any support would be much appreciated.

Thank you all,

Danny

---

### Post by oldos2er on 2018-04-23
Perhaps you could show us the output of sudo fdisk -l, whatever it might be? Also Linux cannot be installed on NTFS partitions.

Which server version did you install? And what are the full hardware specs of this computer?

---

### Post by danny-1ee on 2018-04-24
Hi Oldos2er,

Thanks for your response.  Here's a snapshot of it.[IMG]https://imgur.com/a/hSAp5DM[/IMG]

[https://imgur.com/a/hSAp5DM](https://imgur.com/a/hSAp5DM)
[IMG]https://imgur.com/a/hSAp5DM[/IMG]

---

