---
title: "New kernel (linux-image-2.6.30-10-generic) does not boot"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-06-23
I did an update to linux-image-2.6.30-10-generic a view minutes ago. Unfortunately this kernel does not boot on my notebook (Macbook Pro, first model from 2006) ... I just get 
a blank screen. 

The version 2.6.30-9 boots without any problems .. Anybody else out there with the same problem?

---

### Post by moomex on 2009-06-23
same problem here with HP Pavilion.

---

### Post by geojorg on 2009-06-23
Same problem with Dell Inspiron 1420, Intel X3100.

But writting exit in initramps i get to boot normaly is just that it takes a lot to boot.

With 2.6.30 -9 it's working fine.

---

### Post by philcamlin on 2009-06-23
hmm interesting my grandma has an hp but no issues so far...

---

### Post by geojorg on 2009-06-23
I think is related to Intel's graphics cards and KMS, because in my HP DV6000 laptop I just finish upgrading and it's work fine, it has an NVIDIA graphic card.

---

### Post by wayne_cat on 2009-06-23
my Macbook  has an ATI Technologies Inc M56P [Radeon Mobility X1600] :(

---

### Post by Reiger on 2009-06-23
I've had similar issues (including kernel segfaults). None of 'em can be reproduced using the recovery mode -> resume boot. So, there you go. :P

---

### Post by graaant on 2009-06-23
Getting scared to reboot! :P

---

### Post by ronacc on 2009-06-23
on my system (amd64 desktop) apt-get upgrade shows many packages held back including the -10 headers and image . it is not advisable to do a dist-upgrade or partial upgrade under these circumstances , so beware .

---

### Post by wayne_cat on 2009-06-23
> **Reiger said:**
> I've had similar issues (including kernel segfaults). None of 'em can be reproduced using the recovery mode -> resume boot. So, there you go. :P

I had added a vga option to menu.lst ... booting looks better on 1440x900 screen.

/boot/vmlinuz-2.6.30-10-generic root=/dev/sda3 ro quiet [COLOR=Red]vga=0x354

[COLOR=Black]Without the vga option my system boots. The 2.6.30.-10 kernel seems to have a problem
with this.
[/COLOR][/COLOR]

---

### Post by graaant on 2009-06-23
I upgrade with aptitude safe-upgrade.
Still holding back all the mono packages, hopefully they'll come down soon.

Seems to boot 50% of the time with -.10 - sometimes will hang, If I hard-reboot it'll then work.
I'll try the vga option and see how we go.

---

### Post by psyke83 on 2009-06-23
Folks,

The issue is KMS. To get around this issue, boot the kernel with the boot parameter "nomodeset". Just tested it on my 855GM chipset.

---

### Post by ghindo on 2009-06-23
The "nomodeset" parameter doesn't seem to work for me.  Has anybody filed a bug report yet?

---

### Post by doctordruidphd on 2009-06-24
There are a number of issues appearing as a result of today's kernel upgrade. The most serious ones appear to be connected with the fact that the c-compiler was recently upgraded to 4.4, while the kernel was compiled with 4.3. This is causing multiple problems, since kernels often will not work with modules compiled with a different version of the c-compiler.  There is a workaround for this. 
Another problem appears to be that something has broken the boot-by-uuid process. There is a workaround for this, too.

To boot your system if it will not boot, there are two things you can try. If you use the standard grub menu system, simply boot from an older kernel. If you are unable to do this, an alternative method is to let grub start, type c to enter the command line mode, and then enter the following commands:
```
kernel  /vmlinuz.old root=/dev/sda1 ro
initrd  /initrd.img.old
boot
```
Replace the '/dev/sda1' with whatever partition your system is on.
This should get you up and running on an older kernel with minimal fuss.
If you are using a proprietary video driver, it will most likely not work, so you may need to boot into recovery mode by adding "single" (without the quote marks) to the end of the kernel line.
To revert to the older version of the c-compiler:
```
greenman@Wolfenstein:/usr/bin$ ls -al gcc*
lrwxrwxrwx 1 root root      7 2009-06-23 17:30 gcc -> gcc-4.3
-rwxr-xr-x 1 root root 238664 2009-06-20 17:28 gcc-4.3
-rwxr-xr-x 1 root root 255104 2009-06-22 23:06 gcc-4.4

```

where the 'gcc' entry is actually a symbolic link, probably to 4.4. You can delete that link, and create a link to the older compiler, this way:
```
sudo ln -s /usr/bin/gcc-4.3 gcc
```

This is what I have done on my system, and I was able to boot and reinstall the NVIDIA drivers, which will not install with gcc-4.4.

These are only temporary workarounds, until the problems are straightened out.

---

### Post by autocrosser on 2009-06-24
After I got past the sleep & busybox errors (used the PPA posted to update busybox & then modified my grub.cfg for /dev/sdx)--I just typed "exit" at the busybox stop & got into the rest of the boot. I'm running Dual nVidia cards & it took two x-server starts, but I got to GDM & am in Karmic with the -10 kernel---felt a bit like a fight---but is working for now.....'nite all-------

Note--I'm using the proprietary driver & that was the least of my problems---looks like nVidia is the only one not affected with this bug......

---

### Post by nhasian on 2009-06-24
You make your grandma run ubuntu+1?  dont you love her?

> **philcamlin said:**
> hmm interesting my grandma has an hp but no issues so far...

---

### Post by davideotape on 2009-06-24
Everything's fine over here :D

---

### Post by ronacc on 2009-06-24
here on my 64bit install the kernel stuff still shows held back using either the US server or the main .

---

### Post by ayates on 2009-06-24
> **ghindo said:**
> The "nomodeset" parameter doesn't seem to work for me.  Has anybody filed a bug report yet?

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/391215](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/391215)

Will someone confirm ?

---

### Post by psyke83 on 2009-06-24
> **ayates said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/391215](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/391215)

Will someone confirm ?

You should probably also remove the vga=XXX line to avoid problems with KMS.

---

### Post by tad1073 on 2009-06-24
just updated this morning, got a status 1 and status 3 error, but 2.6.30-10 seems to boot fine other than the parameter "vga=795" that doesn't work

:~/Desktop$ uname -a
Linux tad 2.6.30-10-generic #12-Ubuntu SMP Mon Jun 22 16:30:32 UTC 2009 x86_64 GNU/Linux

---

### Post by Therion on 2009-06-24
I'll pass this along in case it helps someone else...

I was booting to a blank screen as well last night after updating (actually a kind of odd reddish orange colored screen for whatever reason).  To troubleshoot the issue I booted using the Recovery kernel (verbose boot).  When the startup procedure stopped the last message had to do with device /sdd (the removable CF card in my HP Printer that Ubuntu labels a removable drive).  

I turned on my printer, rebooted using the generic kernel, and everything booted correctly.  At this point everything is fine.  I guess Ubuntu snagged when it couldn't mount /sdd or something.  Once it could, all was fine again.

---

### Post by moomex on 2009-06-24
Now I got a completely GREEN screen when I try to boot from the new kernel (linux-image-2.6.30-10-generic). I have an nvidia graphic card and linux-image-2.6.30-9-generic boots just fine.

this is weird, (wonderful weird)!!!

---

### Post by jerrylamos on 2009-06-24
Boots on my Intel i845 tower with modeset=1.  Do note GtkPerf from Synaptic takes 48 seconds to run with KMS while if Driver "vesa" is used, GtkPerf takes only 28 seconds.  This is a medium speed 2.0 gHz Celeron 1 gb memory.

KMS does appear to be on for example Ctrl-Alt-F1 shows a graphic font on the command line.


Does NOT boot on my Intel i830 Thinkpad unless I add nomodeset after quiet splash.  KMS isn't on, for example Ctrl-Alt-F1 shows the old typewriter style font.

Jerry.

---

### Post by wayne_cat on 2009-06-24
Does anybody know where I can find the change log of Karmic kernels?

---

### Post by celticbhoy on 2009-06-24
I have a different kind of problem after the updates. I get to GDM fine then login and everything looks as it should, until I try and run anything. It doesn't matter what I run, even if I try to change workspace in compiz its the same result - logged out and back to GDM.

---

### Post by zoomy942 on 2009-06-24
mine did the same thing.

here is another thread about it

[http://ubuntuforums.org/showthread.php?t=1195504&page=2]("http://ubuntuforums.org/showthread.php?t=1195504&page=2")

---

### Post by wayne_cat on 2009-06-24
> **celticbhoy said:**
> I have a different kind of problem after the updates. I get to GDM fine then login and everything looks as it should, until I try and run anything. It doesn't matter what I run, even if I try to change workspace in compiz its the same result - logged out and back to GDM.

any errors in ~/.xsession-errors?

---

### Post by nystire on 2009-06-26
I get a lockup right after selecting the kernel. It shows the partition it is booting off and then hangs. Nothing has allowed me to continue past that point in 2.6.30-10.

This is on a Toshiba P105-S9337, GeForce 7900.

---

