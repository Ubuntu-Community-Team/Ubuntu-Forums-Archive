---
title: "Kernel panic on boot after upgrade"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Dark-Shot666 on 2011-01-25
So, I've been trying to get Ubuntu on my beloved 4 year old Acer desktop that's been chugging like a tank. However, after either a fresh install or upgrade, I would get the following error:

"**Kernel panic - not syncing: VFS: Unable to mount to root FS on unknown-block(0,0)**"

I've looked here and there, and one of the issues it would seem is the kernel not recognizing my hard drive if I'm correct. One of the suggestions was to upgrade the kernel however, I have no idea how to do such a thing if I can't get into the OS. On the flip side, I'm not even sure if that'll help.

The live disk boots fine for both 10.04/10.10

The drive is a 320Gig Western Digital WD3200AAJS.

Any assistance would be greatly appreciated.

---

### Post by mörgæs on 2011-01-26
Hi, can you install a minimal Ubuntu on the machine? That will help isolate the error.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Best is to try both 10.04 and 10.10.

---

### Post by mörgæs on 2011-01-26
Remember to have wired internet access while installing, by the way.

---

### Post by Dark-Shot666 on 2011-01-26
> **mörgæs said:**
> Remember to have wired internet access while installing, by the way.

Thanks for the quick reply.

I've tried to start the installation but my network settings cant be detected, and living at home with parents doesn't allow for freedom of information regarding our home network. So, I can't connect to the internet through that method.

Any possible other ideas? I'll try to connect my pc to the modem directly once I get the chance.
[B]
[update][/B]

So through using VM Ware I was able to install it using the minimal installer, but again, I get a kernel panic after the raid auto configure is run during a coldboot. Is there the option to update the kernel to the newest one on that add additional software packages list?

**[Second update]**

Through VM Ware I updated the kernel and still panics on native boot.

---

### Post by Dark-Shot666 on 2011-01-28
Bunping. Any assistance would be appreciated.

---

### Post by ronparent on 2011-01-29
Often the kernel panic occurs because you need a boot parameter added to the boot line to allow the installed OS to work with your specific hardware. I need the 'nolapic' for instance to boot my unit with an Asus MB. Often it is required for a graphic card incompatibility (ie nomodeset or others). The problem often shows up after an otherwise  successful boot. It is best to work it out with a live cd to find the needed parameter. Once found you have to edit to add it to install in the /etc/default/grub file to make it permanent.

---

### Post by Dark-Shot666 on 2011-01-29
I'm reasonably sure it has nothing to do with acpi as I've tried the few boot parameters to disable it and still haven't had a successful boot. I can boot the live distro but it gives me a hardware error before loading the desktop environment. The last actual successful install and boot was when I tried out 8.04 a couple years ago so its dissapointing that I can't get the latest and greatest on this machine.

Are there any other recommended parameters to try out?

Also, after the raid autodetection VFS says it can't open root device at my HD's UUID. Following that the message "*Please append the correct "root=" boot option; here are the available partitions*:" shows up and then I get the VFS error.

---

### Post by ronparent on 2011-01-29
'acpi' is different from 'apic' or 'lapic'. A more complete set of boot parameters is listed here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by Lordcorvin on 2011-02-13
Hey guys I have a problem similar to this but it happens after Installation and then nothing, tried on 2 totally diferent computers, I can`t load Ubuntu it shows 
Kernel Panic
What should i do?

Installed it from USB, and SD card, same result

P.S.
Live Ubuntu works fine it's in the installation itself something wrong.

---

### Post by sikander3786 on 2011-02-13
> **Lordcorvin said:**
> Hey guys I have a problem similar to this but it happens after Installation and then nothing, tried on 2 totally diferent computers, I can`t load Ubuntu it shows 
Kernel Panic
What should i do?

Installed it from USB, and SD card, same result

P.S.
Live Ubuntu works fine it's in the installation itself something wrong.
Welcome to the forums :-)

Are you sure your HDD is healthy? And the HDD cables? I would recommend to check your HDD for bad sectors, and also run a memtest on your RAM.

---

### Post by Lordcorvin on 2011-02-13
Everything is healthy, if it wasn't Windows 7 would not load either

---

### Post by Lordcorvin on 2011-02-13
Hey guys does anyone know why I can't load Ubuntu 10.10 after Installation, I get an error of
Kernel Panic
Does anyone know what's wrong?
I tried to install it from Sd card and USB, same error
Is it Ubuntu itself?
Because previous versions work same, only Ubuntu 8 worked fine untill updates

I'm installing on 64bit computer and tried it on 2 totally diferent computers

Please help!!!

---

### Post by Lordcorvin on 2011-02-13
Hey guys, same problem on my computer, don't know what's wrong, win 7 loads fine while Ubuntu has a Kernel Panic, I tried the install on 2 tottaly diferent computers, using both sd card and USB.

Previous Ubuntu won't work either.

Only ubuntu 8 worked untill updates

---

### Post by An Sanct on 2011-02-13
> **Lordcorvin said:**
> Hey guys does anyone know why I can't load Ubuntu 10.10 after Installation, I get an error of
Kernel Panic
Does anyone know what's wrong?
I tried to install it from Sd card and USB, same error
Is it Ubuntu itself?
Because previous versions work same, only Ubuntu 8 worked fine untill updates

I'm installing on 64bit computer and tried it on 2 totally diferent computers

Please help!!!

The most common problem when you get a kernel panic is, using wrong architecture (32bit/64bit) or memory problems.

Can you post the contents of this log?
```
/var/log/kern.log
```

(just the last lines, please post it in a code section for readability.)

---

### Post by Lordcorvin on 2011-02-13
how to get the log, because i'm a noob here?

---

### Post by An Sanct on 2011-02-13
You can access it through
System -> Administration -> Log File Viewer

Those are all the logs your machine writes.
And then on the left, find "kern", it can also be kern1 or something like that.

---

### Post by mörgæs on 2011-02-13
Double- (or multiple-) posting will not bring you closer to an answer.

---

### Post by CharlesA on 2011-02-13
Please don't make multiple threads on the same issue. I've merged all three of your threads together.

---

### Post by YumaJim on 2011-03-19
I have the same Kernel panic error message. Can't mount root fs.
This started after upgrading to kernel 3.6.35-37. I can boot up the
previous 2.6.35-27 just find - no problem. The UUID is the same only diff
in the grub memu is the kernel version. I tried adding the 'noacpi' option
and that did not help. BTW - I using Ubuntu version 10.10.

---

### Post by uRock on 2011-03-19
From the bootable kernel, have you tried running **sudo update-grub** in a terminal?

---

### Post by YumaJim on 2011-03-20
URock,

I just tried the grub-update but, that did not solve the problem - no change. What's the best way to re-install a fresh update of the -27 kernel?

---

### Post by uRock on 2011-03-20
Synaptic Package Manager can reinstall it. just search the full kernel number and select to reinstall all three of them.

Hopefully that will fix the problem.

---

### Post by YumaJim on 2011-03-20
Urock,

Reinstalling fixing it. Yea! Reinstalling did not do a download, it just
used the files in the cache. I had thought about re-installing the files 
before but, I thought I might need to clear the cache and re-download the 
files.

Looking back I think I may have not restarted the computer after the
first upgrade to 2.6.35-27 and therefore that installation was not completed correctly.

Urock thanks for the help.

Yumajim

---

### Post by uRock on 2011-03-20
> **YumaJim said:**
> Urock,

Reinstalling fixing it. Yea! Reinstalling did not do a download, it just
used the files in the cache. I had thought about re-installing the files 
before but, I thought I might need to clear the cache and re-download the 
files.

Looking back I think I may have not restarted the computer after the
first upgrade to 2.6.35-27 and therefore that installation was not completed correctly.

Urock thanks for the help.

Yumajim

I am glad it worked, you're welcome.:P

---

