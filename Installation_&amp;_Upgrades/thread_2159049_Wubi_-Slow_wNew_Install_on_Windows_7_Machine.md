---
title: "Wubi -Slow w/New Install on Windows 7 Machine"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by nlmaster on 2013-07-01
I have recently installed Ubuntu 12.04 LTS on my laptop from within Windows 7. I set aside 30GB of the hard drive for Ubuntu.

The issue I am having is that Ubuntu runs extremely slow. It sometimes takes around 90 seconds for Firefox to open or for the software center window to open. 

First thing I tried was uninstalling Ubuntu and reinstalling but I have the same issue still. 

Any help and/or suggestions much appreciated.

nl

---

### Post by nlmaster on 2013-07-01
I forgot to mention that it is a Windows 7 Home Edition with 500GB hard drive and 4 GB of RAM.

In total there is only about 20 GB of the HD used.

nl

---

### Post by oldfred on 2013-07-01
When you say inside, is this a wubi install?
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

But even wubi should not be that slow.  It may be the underlying NTFS if you have wubi. Try chkdsk from Windows.

---

### Post by nlmaster on 2013-07-02
Yes it is a wubi install. I have run chkdsk from Windows and everything is fine.

nl

---

### Post by oldfred on 2013-07-02
NTFS gets really slow if it does not have lots of room, or 30% free. Do you have less than 30% free space?
The Linux system is really running on its file system inside the NTFS, so I do not know if that still applies.

Edited title to add wubi, so those who know it more may see thread.

---

### Post by bcbc on 2013-07-03
What graphics card do you have? Sometimes if you have e.g. nvidia or radeon and are running it with the open drivers (default) it can cause sluggishness. This can also result in corruption of the Wubi root.disk.

The other thing is if you've 'set aside 30GB' I assume you mean you created a partition. In which case, installing directly makes more sense than using Wubi. This won't fix the sluggishness if it's e.g. graphics card related, but it's better for long term use of Ubuntu.

A quick check for the graphics issue is to boot with nomodeset:
1. Hold down the Shift key after selection Ubuntu until the Grub menu appears
2. Select Advanced options
3. Select the second "Recovery Mode" entry
4. Select "Resume normal boot" from the recover mode menu

---

### Post by nlmaster on 2013-07-03
> **oldfred said:**
> NTFS gets really slow if it does not have lots of room, or 30% free. Do you have less than 30% free space?
The Linux system is really running on its file system inside the NTFS, so I do not know if that still applies.

Edited title to add wubi, so those who know it more may see thread.

I have almost 80% free space.

nl

---

### Post by nlmaster on 2013-07-03
> **bcbc said:**
> What graphics card do you have? Sometimes if you have e.g. nvidia or radeon and are running it with the open drivers (default) it can cause sluggishness. This can also result in corruption of the Wubi root.disk.

The other thing is if you've 'set aside 30GB' I assume you mean you created a partition. In which case, installing directly makes more sense than using Wubi. This won't fix the sluggishness if it's e.g. graphics card related, but it's better for long term use of Ubuntu.

A quick check for the graphics issue is to boot with nomodeset:
1. Hold down the Shift key after selection Ubuntu until the Grub menu appears
2. Select Advanced options
3. Select the second "Recovery Mode" entry
4. Select "Resume normal boot" from the recover mode menu

I will have a look at this sometime today and let you know what happens. 

nl

---

### Post by nlmaster on 2013-07-03
> **bcbc said:**
> What graphics card do you have? Sometimes if you have e.g. nvidia or radeon and are running it with the open drivers (default) it can cause sluggishness. This can also result in corruption of the Wubi root.disk.

The other thing is if you've 'set aside 30GB' I assume you mean you created a partition. In which case, installing directly makes more sense than using Wubi. This won't fix the sluggishness if it's e.g. graphics card related, but it's better for long term use of Ubuntu.

A quick check for the graphics issue is to boot with nomodeset:
1. Hold down the Shift key after selection Ubuntu until the Grub menu appears
2. Select Advanced options
3. Select the second "Recovery Mode" entry
4. Select "Resume normal boot" from the recover mode menu

Alright so I tried this. However, upon selecting "Resume Normal Boot" the system tried to reboot but nothing happened. I let it go for 10 minutes but nothing. I had to power down the system and reboot the laptop again.

nl

---

### Post by bcbc on 2013-07-03
Important, never "power down" a linux system (especially Wubi) without first trying this: [http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

It's very likely that you could corrupt the Wubi root.disk by doing this - and it's possible to corrupt any filesystem depending on what is being written at the time you power off.

Please supply the brand, model, graphics card, wireless card, .... anything else you can think of (any devices you have plugged in to your computer). Maybe we can find out what's causing this issue.

---

