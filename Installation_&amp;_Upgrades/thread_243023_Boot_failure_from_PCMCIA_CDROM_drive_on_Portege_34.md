---
title: "Boot failure from PCMCIA CDROM drive on Portege 3440CT"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by DoubleL on 2006-08-24
Hi,

I have an elderly but faithful Toshiba Portege 3440CT. Being a tiny and slim laptop it has an external CD-ROM drive which connects via the PCMCIA slot. The laptop is capable of booting from this drive.

If I insert a Kubuntu 6.06.1 CD and select to boot from the disk, it does so and displays the boot menu. However if you choose the start/install option, it boots the kernel, but freezes when it tries to mount the root filesystem. After a while it goes back to the 'Uncompressing Linux...' message, and will sit there until turned off.

Does Ubuntu support booting from a PCMCIA device in the way this machine does, or will I have to extract the hard drive from the Portege and use another machine to do the install? I looked at the various boot parameters in the help screens but none seemed to be relevant to this problem.

Thanks for any advice.

---

### Post by zxee on 2006-08-24
What are the specs on the toshiba? It may not be able to run 6.06 if the memory is <256 but some users manage with less.
There is a complete installation guide here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
That link provides many different ways to install.

---

### Post by daenyth on 2007-01-16
I'm having the exact same problem on my Sony Vaio PCG-R505TS. If anyone has any updates on this, I would appreciate it. I did manage to get debian to boot and install, but I'd really like to get this up.

---

### Post by phuturism on 2007-01-22
I gave up on a cdrom install for my portege 3480ct and did a netboot install instead - which worked!  

Thread here [http://www.ubuntuforums.org/showthread.php?p=2050529#post2050529v](http://www.ubuntuforums.org/showthread.php?p=2050529#post2050529v)

---

### Post by jackdaw28 on 2007-02-19
I was able to boot the alternative install cd of 6.10 edgy on my portege 3440CT. Just do a text installation and all is well thereafter.

---

### Post by fishymark27 on 2007-03-10
I have a Portégé 3110CT, and I was able to load Xubuntu using the PCMCIA CDROM. I used the alternate cd image and did a text install, and it worked (The OEM one didn't) from here:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

