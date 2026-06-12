---
title: "Grub: Problems after installing"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by markmb on 2011-06-14
I've got a problem: I've installed Ubuntu with the minimall install (I've got an old computer), but now I can't load it: It shows me a grub error.

Error: out of disk
grub_rescue>

I went here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) but while checking this prompts:


[LIST]
[*]The *grub* folder must exist and contain the necessary GRUB 2 files. 
[*]The proper path must be set via the *set prefix* command. 

[LIST]
[*]Many GRUB 2 commands will not work until the correct path is set. If the path to the *grub* folder (normally */boot/grub*) is not correct, an *unknown command* or *file not found* message is likely. 
[/LIST]
[*]The necessary modules must be loaded. 
[LIST]
[*]The kernel cannot be loaded until the 'linux' module is loaded. 
[/LIST]
[*]A Linux kernel and  initrd.img must be located and loaded.
[/LIST]
And when I execute this command:

ls (hd0,1)/boot/

It shows me: out of disk

What can I do?

If I execute ls, it shows:
(hd0) (hd0,1) (fd0)

Thank you in advance

---

### Post by mörgæs on 2011-06-14
Does this help?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by markmb on 2011-06-14
I'll try, but my internet connection is slow and I'll need few hours to try it :(

Thank you!

---

### Post by markmb on 2011-06-15
I tried with Lubuntu, because is lighter, but it throws me an error:

```
This kernel requires the following features not present on the CPU:
cmov
Unable to boot - please use a kernel appropiate for your CPU
```

I'll try with Ubuntu 10.04, but I'm not sure that the computer can load it because it has a small RAM memory

While I try with Ubuntu 10.04, have you got any other solution?

Thank you

---

### Post by mörgæs on 2011-06-15
This is old hardware... which machine exactly are we dealing with?

---

### Post by markmb on 2011-06-15
The motherboard is:

EPOX EP-MVP35G

And the HDD is:

Western Digital WD 1600 AAJB (I think is this, 1600 is sure, but the leters no. It's an IDE HDD)

If you need any other info, tell me

Thank you!

---

### Post by mörgæs on 2011-06-15
I don't know this motherboard, but it is indeed old stuff, if the processor does not have CMOV. 

Anyway, my suggestion (provided you have 192 MB memory or more) is Lubuntu 10.04. It still has support for older processors.

---

### Post by markmb on 2011-06-16
That's what I'm trying to install. I'm using this:

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

But after installed, it throws me the GRUB error, is an installing problem, and I can't solve it!

Thank yous

---

### Post by markmb on 2011-06-16
I can't solve it!!!! With the LiveCDs with Boot Repair but the computer isn't able to load them, and all the solutions on the web, need a LiveCD.

I'd be very grateful to you, if you could help me!!

Do you think reinstalling is an appropiate option?

Thank you!

---

### Post by mörgæs on 2011-06-16
Yes, a reinstall would be fine, if possible.


These guys have managed to get a Lubuntu 10.04 running without CMOV. You could ask there (hoping that some moderator does not close the thread):
[http://ubuntuforums.org/showthread.php?t=1595646](http://ubuntuforums.org/showthread.php?t=1595646)


Else you could search here for an alternative light distro:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)


Finally, maybe the best option is to get some younger hardware :-)

---

### Post by markmb on 2011-06-18
I tried with one of the light distros you showed me, and I have more problems: After installing, GRUB shows me error 18. After searching the web, this problem is caused by diferent HDD sizes between Linux and the BIOS. I have a 160 Gb HDD, and my BIOS detects 8 Gb.

This is the explanation. As well as this, on the web, I found a thread in a forum, which shows how to solve this problem, repartitioning the disk. I reinstalled again the distro, repartitioning the HDD, but it showed an error.

This is annoying!!! I think I'll try with another distro, and then, if it doesn't work, I'll leave it.:(

---

### Post by gabrielshier on 2011-06-18
this will probably fix it but will take some time off your Internet connection;

get the linux distro named Super-GRUB and run it through a disk or DOK. yes, it's big (4 MB) but it will repair any damaged BOOT weather it's in the MDR, boot sector or system boot itself. Used it at work and it saved me a few times :)

Good luck.

---

### Post by markmb on 2011-06-18
I know that program. And I tried to use. But it doesn't work. If you read the full thread, you'll see the first problem: grub wasn't installed properly and I couldn't use LiveCD. This couldn't be solved by SuperGrubDisk.

As well as this, the second problem, wasn't caused by GRUB, it was caused by problems between HDD and BIOS.

Thank you equally

---

### Post by mörgæs on 2011-06-18
Have you upgraded the BIOS?

---

### Post by markmb on 2011-06-18
No, and I won't do it because the motherboard is so old that it hasn't got website, and the FTP official site hasn't got an update for the model I have.

---

