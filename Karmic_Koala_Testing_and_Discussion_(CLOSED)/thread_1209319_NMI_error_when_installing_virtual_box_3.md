---
title: "NMI error when installing virtual box 3"
date: 2009-07-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-07-10
Got these in dmesg

[21762.450486] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[21762.450490] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[21762.450491] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

Is it OK to disable NMI? I didnt notice this prior to 2.6.31 kernel.

---

### Post by dinxter on 2009-07-10
i thought nmi watchdog was mainly for debugging kernels?. i've disabled it in /etc/default/grub myself but i couldnt tell you whether it's been deliberately enabled or not

---

### Post by jithin1987 on 2009-07-10
> **dinxter said:**
> i thought nmi watchdog was mainly for debugging kernels?. i've disabled it in /etc/default/grub myself but i couldnt tell you whether it's been deliberately enabled or not

Can you tell me what to add in /etc/default/grub for disabling nmi.

---

### Post by dinxter on 2009-07-10
was just reading [this article]("http://x86vmm.blogspot.com/2005/10/linux-nmis-on-intel-64-bit-hardware.html") about nmi's, doesnt seem essential, wasnt enabled in previous kernels
you can disable them in /etc/default/grub by changing
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nmi_watchdog=0"

and running "sudo update-grub"

---

### Post by dinxter on 2009-07-10
actually, i've just removed the nmi_watchdog=0 option and rebooted and vboxdrv is fine, maybe nmi watchdog is triggered by something else, like a previous bad shutdown or such

---

### Post by dinxter on 2009-07-10
yep, less /proc/interrupts |grep NMI shows nmi is disabled by default on a normal boot, you should maybe not disable it in grub and just try rebooting to see if the problem disappears

---

### Post by jithin1987 on 2009-07-10
> **dinxter said:**
> yep, less /proc/interrupts |grep NMI shows nmi is disabled by default on a normal boot, you should maybe not disable it in grub and just try rebooting to see if the problem disappears

Thanks. I noticed it when I was installing virtualbox. At kernel module compiling part it stopped cribbing about nmi being active. I will try without editing grub.

---

### Post by dinxter on 2009-07-10
i only checked it because you mentioned it, there it was, now i've tried a few different reboots and its always off, without needing to add the option to grub, strange

---

### Post by davinel on 2009-07-13
Got same error. Rebooting doesn't help, end, it's very strange, but i can't disable it via grub:
> menuentry "Ubuntu, Linux 2.6.31-2-generic" {
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 03ad87c1-d4e9-4bc1-8c3b-3244e9bb48bf
    linux    /vmlinuz-2.6.31-2-generic root=UUID=3ef4fbe3-291f-47b9-bfee-d5fa5f01548a nmi_watchdog=0 ro  quiet splash 
    initrd    /initrd.img-2.6.31-2-generic
}

do nothing.. mb this is because of grub2?
any suggestion?

---

### Post by jithin1987 on 2009-07-13
Actually I did disable it when booting, though I edited the boot options on grub screen to add nmi_watchdog=0. 

Later on I didnt use it, guess it was needed only for compiling vbox kernel module.

---

### Post by davinel on 2009-07-13
> **jithin1987 said:**
> Actually I did disable it when booting, though I edited the boot options on grub screen to add nmi_watchdog=0. 

Like i said before - for some unknown reason i can't disable it this way.. 
maybe should try grub1?

---

### Post by jithin1987 on 2009-07-13
That should not be necessaary. When on the grub screen during booting, select to edit the boot options and add nmi_watchdog=0 on the line with "linux"
In my case it looked like 

linux   /boot/vmlinuz-2.6.31-2-generic root=UUID=8671d387-76e3-44d7-8833-e55123e20022 ro nmi_watchdog=0 quiet splash  crashkernel=384M-2G:64M,2G-:128M

aftefr this choose to boot. It will work I guess.

---

### Post by dinxter on 2009-07-14
i'm still getting this error occasionally without any obvious pattern, the only syslog i've got from one of these boots shows that nmi_watchdog=0 was set but still vbox complained. i'll try to get some decent information next time it happens. can someone try,
'less /proc/interrupts |grep NMI' next time they get this, just to double check that nmi is actually running and its not some weird vbox bug (should return anything apart from a 0 if it is). has anyone filed a bug yet?
{EDIT] This isnt a bug on dkms module compilation but actually on modprobing so it could crop up again on at least some boots

---

### Post by jithin1987 on 2009-07-14
This is what less /proc/interrupts |grep NMI tell me

NMI:          0          0   Non-maskable interrupts

and I have not disabled nmi. 

I disabled nmi only for installing vbox, later on I did not disable.

---

### Post by dinxter on 2009-07-14
thats as it should be on a normal boot, i'm wondering whats there on a vbox failing on nmi boot though. i cant see anything that would trigger nmi happening

Jul 14 06:29:23 crystaltree kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-2-generic root=UUID=d460a66b-38ab-44ff-be28-ef7ba10f2720 ro nmi_watchdog=0

but then,

---

### Post by jithin1987 on 2009-07-14
Vbox is just checking is nmi is enabled or not and if yes it tires to disable it before compiling the kernel module. Thats where it's failing.

---

### Post by dinxter on 2009-07-14
yes, its fails on an nmi check, i'm just trying to double check that nmi was actually initialised ( though i suspect it is ) which means it isnt a virtualbox bug. the question is probably more likely to be what is triggering nmi on some boots rather than others. obviously it can be disabled but it could be a sign of some other problem

---

### Post by davinel on 2009-07-14
> **jithin1987 said:**
> When on the grub screen during booting, select to edit the boot options and add nmi_watchdog=0 on the line with "linux"

I don't see difference. Edit grub.cfg, or directly at boot - the same thing. But ok, I done it, and again - this do nothing. No wonder, though.
> **dinxter said:**
> 
'less /proc/interrupts |grep NMI' next time they get this, just to double check that nmi is actually running and its not some weird vbox bug (should return anything apart from a 0 if it is). has anyone filed a bug yet?
It return 0, that's very strange.
I don't think this is bug in vbox.. The same version running pretty well in debian.

Maybe.. just maybe.. NMI _was_ active(triggered by crash or something), and now system just "thinking" that watchdog in active state(because of some lock or.. dunno) ?

---

### Post by jithin1987 on 2009-07-14
> **davinel said:**
> 
Maybe.. just maybe.. NMI _was_ active(triggered by crash or something), and now system just "thinking" that watchdog in active state(because of some lock or.. dunno) ?

I suspect the same. I also notice that some times the virtual box is asking me to re run the set up.

---

### Post by jfernyhough on 2009-07-15
This is a bit weird, and I presume it's down to the kernel as I haven't had this problem before.

At the moment, Vbox complains about NMI being enabled, despite my specific disabling of it on the GRUB line (and even if I didn't disable it things would still work, e.g. on 2.6.28 and 2.6.30).

Even stranger, when I try to do the setup the first time it will fail, the second time normally fails, and the third time it works fine. I can then run vbox as normal.

```
[  951.349864] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  951.349868] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  951.349869] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[ 1070.920499] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 1070.920503] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 1070.920504] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[ 1844.413656] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 1844.413665] vboxdrv: Successfully done.
[ 1844.413670] vboxdrv: Found 2 processor cores.
[ 1844.413789] VBoxDrv: dbg - g_abExecMemory=ffffffffa109e1e0
[ 1844.413824] vboxdrv: fAsync=0 offMin=0x30c offMax=0xec4
[ 1844.413832] Platform driver 'vboxdrv' needs updating - please use dev_pm_ops
[ 1844.415339] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 1844.415345] vboxdrv: Successfully loaded version 3.0.2 (interface 0x000e0000).

```

---

### Post by dinxter on 2009-07-15
i've put a bug report in [here]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/399732"), though i agree it may not really be a virtualbox bug. shame its difficult to reproduce, makes the bug description seem a bit vague so if anyone can add something more solid to it that would be appreciated

---

### Post by neferty on 2009-07-21
hmmm, for me, setting NMI to 0 in grub didn't work either.
However, after running ```

sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv start
``` I was able to start the virtual machine without problems.

Can somebody try and confirm this solution?

---

### Post by dinxter on 2009-07-21
i'm using the repository version so theres no vboxdrv start for me but i suspect you'll find you still randomly get the problem when the module is loaded. i sat on the command line rmmod and modprobe the vboxdrv module to see if it was as random as it seemed, 8 times there was no problem, twice it failed on nmi! absolutely no reason for the difference, bizarre. seems to be a problem with the way vbox detects nmi on 2.6.31 kernels i'm guessing but i really have no idea

---

### Post by kwr2k on 2009-07-22
> **neferty said:**
> hmmm, for me, setting NMI to 0 in grub didn't work either.
However, after running ```

sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv start
``` I was able to start the virtual machine without problems.

Can somebody try and confirm this solution?

Yes, I can confirm that the same thing happened on my Karmic installation.
I got the nmi_watchdog error in the output of 'dmesg' but doing a /etc/init.d/vboxdrv start worked. My XP VM came up without any issues.

---

### Post by waster on 2009-07-23
I've tried with and without nmi_watchdog=0 and tried multiple invocations of modprobe vboxdrv on 2.6.31-3, but I can never get it to load (it can't deactivate NMI according to dmesg).

What is stopping NMI deactivation? Or what is causing NMI activation???

---

### Post by deresh on 2009-07-24
there seems to be a regresion in latest vbox ( 3.0.2) with our 2.6.31-3 kernel

it works with 2.6.31-1 and 2.6.31-2.

and vbox 3.0.0 works with all kernels ( with or withouth setting nmi_watchdog=0 in kernel boot options)

---

### Post by waster on 2009-07-24
Same here. There is a little bit of stuff in the rc2 to rc3 kernel changelog about NMI, but it seems to relate to oprofile which I don't have installed.

I cannot find an old 31-2 deb, and I'm rapidly getting pissed off.

The 31-4 kernel also doesn't work.

---

### Post by davinel on 2009-07-24
I compiled a custom kernel from source and problem disappeared (:

---

### Post by waster on 2009-07-25
great - will try that.
I also found that virtualbox 3.0.0 and 3.0.2 fail for ubuntu karmic kernels 2.6.31-2, 3,4

---

### Post by aamukahvi on 2009-07-25
(whoops sorry... didn't read the subject properly)

---

### Post by jithin1987 on 2009-07-25
I am not finding any issues. I just now had the 2.6.31-4 kernel upgrade installed and everything it is working fine.

---

### Post by neferty on 2009-07-25
Same here, with the *-4 kernel everything seems back to normal

---

### Post by dinxter on 2009-07-25
still get it with the -4 kernel on and off, seems to be fine more times than the earlier kernels but still happens every so often

---

### Post by daflame on 2009-07-28
I have the latest Karmic Kernel and still receive the NMI error EVERY time I try to start the virtualbox kernel module.  I have never got it to start yet.

---

### Post by jithin1987 on 2009-07-28
Hmm. I no longer experience this issue. I experienced it only once and at that time I disabled nmi during boot time and had vbox modules compiled. But that was during the 2.6.31-2 kernel and now I am at 2.6.31-4 and no longer experience this.

---

### Post by jithin1987 on 2009-08-10
I started getting nmi errors again. Found another way of dealing with it.

sudo /etc/init.d/vboxdrv force-reload

Initially vitual box refused to start becaue vboxdrv was not loading because of nmi set. But this force reload took care of things.

---

### Post by lazka on 2009-08-10
virtual box 3.0.4 fixed it for me.

---

