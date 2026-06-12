---
title: "Nouveau call for testing."
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-02-06
There was this call for testing a few days ago, but dont see any replies to that email:

See [https://lists.ubuntu.com/archives/ubuntu-devel/2010-February/030165.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-February/030165.html)

Basically install the xorg-edgers/nouveau PPA with:

```

sudo add-apt-repository ppa:xorg-edgers/nouveau

```

Then do a safe update and install "xserver-xorg-video-nouveau" package.

Also, I needed to ensure I set gfxpayload in GRUB2 for PLYMOUTH to at least show up.

KMS switching between KDE and console is certainly smooth now. :D

But Note:

> 
You should not expect to work:
 * The nvidia binary drivers.  The nouveau kernel module will bind to
the hardware and there is no mechanism for handing off to nvidia
kernel module.
 * 3D acceleration.  Brave souls can build mesa from source (and may
well find that they can run compiz), but we will not be shipping the
3D component in Lucid.


NVIDIA users please help with testing/feedback (even if you eventually want to just use the proprietary drivers) because this is planned for Alpha 3 which will be used to test whether to really include it in lucid release or not I believe.

If this works well enough for me, I think I can drop proprietary drivers once and for all since I dont do 3D/gaming nor care too much for compiz 3D effects - stuff like transparency and some KDE UI animations already work smooth without 3D.

---

### Post by autark on 2010-02-06
Is there any chance that suspend/hibernate and resume will work with nouveau?

---

### Post by kklimonda on 2010-02-06
suspend works fine for me but not hibernation. of course YMMV.

---

### Post by vishalrao on 2010-02-06
I'm having some trouble getting plymouth to show up during boot. It seems to work during shutdown though. I'm following this plymouth theming thread: [http://ubuntuforums.org/showthread.php?t=1381109](http://ubuntuforums.org/showthread.php?t=1381109)

Tried the default ubuntu-logo, solar and space-sunrise themes and I get this in my /var/log/syslog file:

```

Feb  7 01:24:50 thunderbird init: plymouth main process (322) killed by TERM signal

```

Not sure if its normal or a symptom of my problem... it was working well with regular vesafb (before nouveau PPA) in that plymouth thread.

---

### Post by kklimonda on 2010-02-06
well, the current state of plymouth is that it shows up pretty late in the boot process. If your system if fast you may simply not see it because X already starts up.

---

### Post by vishalrao on 2010-02-06
It looks like you may be right. Even though I thought I was calling an init script to sleep for 10 (to 30) seconds my KDM login screen shows up real fast during boot (I have an SSD too you see :D) but shutdown is long and slow where I do see the plymouth theme...

I will search around for proper setting of my script location, but would anyone know what runlevel/name to put the script?

I have a /etc/init.d/plymouthsleep script with just a "sleep 30" which works during shutdown but not during bootup.

For bootup I have links named "S85plymouthsleep" from all the /etc/rcX.d folders where X is 2,3,4,5 and S but no joy...

---

### Post by MacUntu on 2010-02-06
Plymouth 0.8.0~-7 started a lot earlier, I hope it goes back to that state. Also this ugly enter key bug got its high priority: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412)

---

### Post by vishalrao on 2010-02-06
I'm using plymouth version "0.8.0~-10~nouveau" from the xorg-edgers nouveau PPA.

This looks like a nice wiki: [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)

The link was printed as a warning by update-rc.d :D Lets see if I can figure out the plymouth starts-late-while-my-PC-boots-too-damn-fast issue :D

---

### Post by MacUntu on 2010-02-06
I'll test my 6600 GT now. Never got KMS working there but that system is a "xorg-edgers vs. BLOB vs. Nouveau git"-mess. :D

---

### Post by vishalrao on 2010-02-06
whooo great, thanks for joining in!

---

### Post by phenest on 2010-02-06
Plymouth does not work for me with nVidia binaries, and doesn't with nouveau drivers neither. Didn't look any different to the nv driver. Maybe I did something wrong. I'll have another go tomorrow.

Does the nouveau driver support compositing? Gnome Shell wouldn't start up.

---

### Post by vishalrao on 2010-02-06
i cant enable compositing in KDE - it does not support 3D - well by default. the mailing list post linked previous post in this thread says "brave souls" can try building mesa from source or something like that - not for me :D

---

### Post by phenest on 2010-02-06
When I tried it, I only got 16bpp colour depth, and a resolution way below native 1920x1200, on a GeForce 7950GTX.

---

### Post by kklimonda on 2010-02-06
Support varies from one chipset to another - the best you can hope for is basic compositing and 2d acceleration. Nothing close to what gnome-shell and compiz require. Those who are blessed by lady luck may get compiz to work but only if they build mesa themselves.
I'd definitely report lower depth and resolution though - those are things that should be fixed.

---

### Post by vishalrao on 2010-02-06
are you using the nouveau PPA (and updated?) and "set gfxpayload=xxxxxx" in grub? the PPA includes not just nouveau patch but also plymouth and kernel too... so ensure you have all those installed and you are booting from that kernel ( version 2.6.32-12-generic ) after setting gfxpayload in grub2...

I found:

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
and
[http://www.netsplit.com/category/tech/upstart/](http://www.netsplit.com/category/tech/upstart/)

I have disabled the rc scripts because the sleep starts too late (plymouth already started by upstart)... so plymouth gets killed quickly....

I'm now trying to make a simple upstart job/script to sleep for 30 seconds starting after mountall job starts... lets see how it goes... gotta do a few reboots and be back...

---

### Post by LKjell on 2010-02-06
Remember to install an extra kernel incase an update bork your system. I have 2.6.31 installed. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.12/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.12/)

@vishalrao do you really have to set gfxpayload? I do have plymouth when I boot.

---

### Post by vishalrao on 2010-02-06
im not sure about needing to set gfxpayload now. i probably assumed that because i was (am) having plymouth problems :)

yup i have the "stock" lucid kernel to fall back on i trust... :)

still no success getting the sleep to happen as init scripts - even ran update-initramfs and also tried putting a sleep script inside the /etc/initramfs-tools/scripts folder to no avail...

---

### Post by MacUntu on 2010-02-06
*) NV43
- KMS: ok
- Plymouth: ok (kinda, at least runs fine when started manually)
- Monitor detection: fails (blanks during boot, I end up with 1024*768@60Hz on a CRT).
- Suspend: Not porperly waking up
- Hibernation: yes

*) G73M
- KMS: ok
- Plymouth: ok
- Monitor detection: ok
- Suspend: yes (panel stays black when waking up the system but that's thanks to a damaged GPU)
- Hibernation: yes

---

### Post by vishalrao on 2010-02-06
I have an 8800 GT which I believe is NV50 ? ... anyways - continuing to try to get that stupid sleep enabled ...

---

### Post by MacUntu on 2010-02-06
Perfectly organized disaster: no bootable kernel. Good night! :D

---

### Post by LKjell on 2010-02-06
> **MacUntu said:**
> Perfectly organized disaster: no bootable kernel. Good night! :D


SysRq + R
SysRq + K

might help sometimes if that does not work then try this to have a clean reboot:

Hold SysRq 
then press R E I S U B

---

### Post by MacUntu on 2010-02-06
Thanks, but I simply booted into single mode and purged all the nouveau bits. Back to the BLOB on this machine for now. :(

---

### Post by vishalrao on 2010-02-06
I'd gone off to sleep and just woke up. While I managed to *not* bork the kernel, I fail to figure out how to get that blasted 30 second sleep in there... tried upstart, initramfs, tried looking at existing confs/scripts and tried Reading The Fine Manpages too. I think I'll just wait for any package updates to see what happens...

In any case, the main purpose of this thread was not plymouth, rather nouveau testing. I hope the alpha3 release is a good/stable one for nouveau, I would prefer a nice KMS-ified display over 3D bling/perf... :)

EDIT: BTW Those who prefer the proprietary drivers (NVIDIA or ATI) there is also another call for testing there! See [https://lists.ubuntu.com/archives/ubuntu-devel/2010-February/030154.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-February/030154.html)

---

### Post by phenest on 2010-02-07
> **vishalrao said:**
> are you using the nouveau PPA (and updated?) and "set gfxpayload=xxxxxx" in grub?

Yes and no. What am I supposed to set xxxxxx to in gfxpayload?

EDIT: I set gfxpayload to 1920x1200. Is that right?

Also, I still get the freeze with plymouth when I hit the ENTER key. Suspend and hibernation not working.

---

### Post by ikt on 2010-02-07
Installed, updated, working fine, plymouth still showing np.

```
ikt@ikt-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by MadeVr on 2010-02-07
Well I just tried this. I'm using a GeForce 8800GT and a dual head setup here.

I just added the ppa, did an upgrade and installed xserver-xorg-video-nouveau. Everything went fine so far.

After a reboot I get to the login screen, which has the highest resolution both screens support. After logging in I'm able to adjust the resolution of both screens (after unchecking the mirror option) and now one monitor runs at its native resolution. Unfortunately, though the resolution of the second screen is detected correctly in the Display-settings window, my second screen just stays black (no signal).

I hope that gets fixed because otherwise everything works really good here!

---

### Post by vishalrao on 2010-02-07
Sweet, and yes I've set gfxpayload=1920x1200 too (my native resolution)...

---

### Post by SevenMachines on 2010-02-07
works fine on a gtx 260, best nouveau yet in fact! i still get mode switching though, hence the late startup of plymouth in the boot i suppose

---

### Post by vishalrao on 2010-02-07
I got a full hang/freeze early this morning - UI "stuck" but music still playing in the background... didn't know what to do except hard reset. Has been working okay since then...

Next time, what can I do to collect useful info for the devs? (assuming it was a nouveau issue)...

---

### Post by rubenverweij on 2010-02-07
This is my card: 01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

I have two monitors attached to it and nouveau is working great here. Only plymouth freezes my kernel (that has got something to do with plymouth and not with nouveau I think) and there is some noise now and then in the text. (bug has already been reported)

But: the display settings correctly detect my monitors and I'm able to rotate them independently! Something I hadn't managed so easily with the nvidia binary drivers, let alone nv.

Hibernate just shuts down the computer but that's the same behaviour as the binary nvidia drivers. All in all, I'm quite happy with nouveau and I hope it will be included in 10.04.

---

### Post by bladerunner6 on 2010-02-07
i was using the ppa on lucid system using the daily builds from mainline kernel (2.6.33.999 xx) however todays addition of the kernel 2.6.32 stuff has borked this, how do i use nouveau with 2.6.33?

---

### Post by donniezazen on 2010-02-07
I am not even able to get to GDM with Nouveau drivers.

---

### Post by vishalrao on 2010-02-07
those folks who are reporting failures/issues, could you also send email to the ubuntu developer/list linked in the first post? it will help the devs fix issues.

anyways its great overall that nouveau seems to be working okay for most :) plymouth is still under more heavy development, i think we wait til next weekend to pick up the testing tempo again! :D

---

### Post by kklimonda on 2010-02-07
@bladerunner6 xorg edgers nouveau ppa doesn't support 2.6.33 kernel so you have to do it a hard way using documentation from nouveau wiki.

---

### Post by bladerunner6 on 2010-02-08
I was able to use them with the mainline 2.6.33.999 builds prior to the backports thing,

---

### Post by AndersAA on 2010-02-08
Would love to use em with 2.6.33 as well...

---

