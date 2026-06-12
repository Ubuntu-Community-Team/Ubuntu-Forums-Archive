---
title: "installation questions can't find an answer"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by 84loops on 2008-05-02
I am able to load the live desktop off of the cd-rom, I am able to install and reboot, I have disabled the floppy disk, and all I get is a busybox dos like prompt that says [initframs] or something like that. I have ran the check disk for errors and I get none. I don't know what else to do. Will gutsy gibbon work better for me. My system is: Asus A7N8X with AMD athalon XP 3200+, 1GB Ram, 80GB HD. I got onboard video and have it set to 128MB. I had it set to 32MB, 64MB and nothing works. I am in the live CD desktop right now. What can I do to get this to work?

---

### Post by Pumalite on 2008-05-02
Use the Alternate CD to install and configure your xserver at the end of the installation.

---

### Post by 84loops on 2008-05-02
how do I do that? sorry, I am new to linux. I just wanted to use something that sounded better than XP. But I am having a hard time. I am trying to install with the install option from the live cd desktop. I was using the install ubuntu from the start-up options.

---

### Post by dstew on 2008-05-02
The problem is when you boot your installed system, and not on the Live CD, correct? That is, you remove the CD and reboot, get the grub menu, or the grub countdown, then the error. Is that right?

---

### Post by hal8000 on 2008-05-02
You're not alone with this problem. There is a rather large thread:
[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

I also have the same problem as you, the live CD works, but a permanent install drops into an initramfs shell.
The thread quoted above is long but has some solutions that work for some people including changing BIOS settings and also appending boot options.

I am about to copy the kernel from the live CD and paste it into my installed 
Ubuntu system. If this works, it may be a solution (though possibly not for everyone). If it works I will type some instructions, meantime try looking through the posts and see if they help.

---

### Post by Pumalite on 2008-05-02
> **84loops said:**
> how do I do that? sorry, I am new to linux. I just wanted to use something that sounded better than XP. But I am having a hard time. I am trying to install with the install option from the live cd desktop. I was using the install ubuntu from the start-up options.
Don't worry; you have to learn to use Linux like you had to learn to use Windows.
You can download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box below the sign 'Start Download'
For your CD, follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less, on CD-R, check CD integrity before install.

---

