---
title: "System failed file-system check"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by dukemaru on 2007-03-08
I've had this problem happen with the last few installs I've done using Ubuntu. Let me give you a little background on my system. I run an AMD 64 and have two physical HD. One I keep windows on and the other is my Linux HD. I have four partitions on my linux HD. hdb1 is my Edgy 32 bit partition, HDB2 is my swap, HDB3 is my Home partition, which I usually share with any other stable Ubuntu versions and HDB4 is my 64-bit ubuntu (currently testing 7.04, which I do allow to share my home partition as it is still testing). The problem is when I install a new ubuntu, I will usually do a complete install and not just an upgrade (I've had upgrade problems before and would just prefer to simply do a clean install instead). The last two clean installs I have done have worked great for the new installed version of Ubuntu, but the other partition of Ubuntu gets an error on startup as having failed a file-system check and that I need to repair it manually. It also states that it has saved a log of the error and that I should take a look at it. When I go to the file and look at it, there is never any information about the error, so I changed the file to being writable, but there is still no record of it even after rebooting and experiencing the same warning everytime. The file system check is always mandatory in on this partition once the problem starts (just after installing the other ubuntu version on the other partition) and after the error I get kicked out to a command line prompt. If I type 'exit' it will leave the command line and continue to boot me into Ubuntu with no further apparent problems. 

Three questions: What is going on here? How do I repair it? And how do I prevent it from happening in the future?

Much appreciation for any help on this issue.
Richard

---

### Post by Herman on 2007-03-09
Hello dukemaru,
I think, if I have understood correctly, that you just need to edit your /etc/fstab file. 

The problem likely is that your operating system is looking at your existing fstab file is trying to find an old filesystem that used to be there but has been deleted, and probably replaced with a new one. Since it searches for a filesystem with a 'UUID' ([Universally Unique Identifier - Wikipedia]("http://en.wikipedia.org/wiki/UUID")).
The operating system want to do a filesystem check on the missing partition, but since it cannot find it, it stops booting with an error message.

Here is a link that should explain to you what you can do about that.                       [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added.]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

If you still have any trouble after reading the link and trying what it says there, let me know and I'll help you more.

Regards, Herman :)

---

### Post by dukemaru on 2007-03-09
Thank you for your help, Herman. I checked the fstab file and there is an error recorded there for partition1 which is the one giving me the problem, so I tend to think you hit the ball on the head with this. I'll check out your link and get it fixed in no time, I'm sure! Will let you know how it goes :popcorn:

---

### Post by Herman on 2007-03-09
Okay, good then, dukemaru. I'm right here if you need any help. :)

---

### Post by dukemaru on 2007-03-09
Herman, 

Thank you! It worked like a charm!
And now I learned a bit about fstab and how to search my comp for information on the different UUID's. Thanks!

---

### Post by Herman on 2007-03-09
Great, dukemaru. We'll need to know the same commands in the future because they are bringing in those UUID numbers for use in the new menu.lst files for grub too, so we'll need to know those for working with the bootloaders too.
Well done,
Regards, Herman :)

---

### Post by m.d. on 2007-09-17
@dukemaru..

how did you do it?

---

### Post by bne on 2008-03-22
Worked for me too - thanks for that.

Been trying to do a clean install of Ubuntu 8.04 beta over Gutsy. Just replaced the UUID numbers in fstab with the commented out partition designator.

top!

---

