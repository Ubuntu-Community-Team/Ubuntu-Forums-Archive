---
title: "Kernel 2.6.27-4"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-09-22
Well, here we are. I'm using kernel 2.6.27-4 and all is good.

---

### Post by olskar on 2008-09-22
And 2.6.27-rc7 was released today :)

---

### Post by beercz on 2008-09-22
> **phenest said:**
> Well, here we are. I'm using kernel 2.6.27-4 and all is good.
Same here - so far :-)

---

### Post by ronacc on 2008-09-22
ok here on 64bit

---

### Post by liquidfunk on 2008-09-22
Any tips on how to compile my own? I've googled it so many times, and not found one that doesn't look insanely confusing.

---

### Post by retrow on 2008-09-22
^
kernel.org has a nice step-by-step guide on how to compile your own kernel. Its not a good idea to use a kernel if you don't know how to add kernel patches for specific hardware applications (like audio, wifi, etc.).

---

### Post by psyke83 on 2008-09-22
> **retrow said:**
> ^
kernel.org has a nice step-by-step guide on how to compile your own kernel. Its not a good idea to use a kernel if you don't know how to add kernel patches for specific hardware applications (like audio, wifi, etc.).

Not to mention that it doesn't help Intrepid development. If you file a bug against *any* package while running a custom kernel, the developers will consider your report null & void.

Anyway, I find overall performance is much, much better than with the older -3-generic kernel. I'm happy :).

---

### Post by Sef on 2008-09-22
Have 64-bit and all seems well.

---

### Post by caryb on 2008-09-22
It doesn't make my speaker beep madly till it's booted now! Previously I had to remove the splash & quiet in the menu.list but I still don't have a splash screen.


Cary

---

### Post by nanog on 2008-09-22
I'm very bored here in 64 bit. No "ubuntu" bugs. Just upstream...sigh.

---

### Post by OutOfReach on 2008-09-22
Everything appears to be fine here.

---

### Post by 1cewolf on 2008-09-22
So far, so good here on Kubuntu. Another step forward!

---

### Post by jlacroix on 2008-09-22
My gamepad won't work as of 2.6.27-4. If I press the D-Pad it moves the mouse cursor instead. No game will respond to the joystick as it appears its being seen as a mouse.

Very frustrated here - I'd like to play a few rounds of ZSNES before bed, now I don't get to. :(

Edit: Oh, and if I press any action button on the gamepad, X dies.

---

### Post by Nullack on 2008-09-22
Im in a total mess after doing this kernel update along with the new nvidia beta. Im diagnosing.

---

### Post by ghindo on 2008-09-23
The kernel's working splendidly for me :)

---

### Post by blakamin on 2008-09-23
> **Nullack said:**
> Im in a total mess after doing this kernel update along with the new nvidia beta. Im diagnosing.
Mine too... I have no x

---

### Post by Nullack on 2008-09-23
Mate have a look at the nvidia thread I responded too for the fix

---

### Post by MALEADt on 2008-09-23
Working great in here too. Only one minor regression: usplash shows artefacts at boot now (you know, the regular progress bar duplicated some times across the screen). Nothing serious though :)

---

### Post by plun on 2008-09-23
OK also for me....

Remember that a new Kerneloops version is available.

[http://packages.ubuntu.com/intrepid/kerneloops](http://packages.ubuntu.com/intrepid/kerneloops)

---

### Post by blakamin on 2008-09-23
> **Nullack said:**
> Mate have a look at the nvidia thread I responded too for the fix

Cheers anyway Nullack, but [this]("http://ubuntuforums.org/showpost.php?p=5839354&postcount=13") solved it. My device wasn't supported... Moment I rolled back driver, BINGO!

---

### Post by jbernardo on 2008-09-23
Here, on a Aspire One, it broke wifi, with a "unable to attach hardware" error. Madwifi's latest snapshot fixed it.

---

### Post by roberine on 2008-09-23
Kernel works great. This was the first time for long that the nVidia drivers kept working after the kernel upgrade. It looks like they're getting it right after all :)

---

### Post by canga on 2008-09-23
> **jbernardo said:**
> Here, on a Aspire One, it broke wifi, with a "unable to attach hardware" error. Madwifi's latest snapshot fixed it.

I updated my Aspire One today and wifi worked without having to re-compile the madwifi drivers, which is a first since replacing linpus with 8.10 a few weeks back.  Well done kernel team. :)

---

### Post by ooZAFLE on 2008-09-23
updated, broke my display, once i corrected that problem  via the xorg gui tool that popped up after 4 tries i got back  into my sytem. but nvidia was broken so had to install and restart several times before it would allow me to run desktop-effects. Sadly after that my sound was broken...

now i know that wasnt all because of this kernel but  i thought id post my experience after  upgrading... ouch.

seems stable now though minus the sound part that i'm working on:)

---

### Post by karolbe on 2008-09-23
> **liquidfunk said:**
> Any tips on how to compile my own? I've googled it so many times, and not found one that doesn't look insanely confusing.

1. grab the kernel source, ungzip untar 
2. cd to the dir with sources
3. copy your existing kernel config:
   cp /boot/config-`uname -r` .
4. type to configure the kernel:
    make menuconfig
5. type:
   fakeroot make-kpkg --initrd  kernel-image kernel-headers
6. install your new kernel image and headers packages and reboot

This is what I do to compile a kernel.

---

### Post by Kerilk on 2008-09-23
Updated to 2.6.27-4 and sound on integrated Intel shipset is not working anymore.

Two affected computers :

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

and

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

Both were working yesterday.
Edit : first is 32 bit, second is 64 bit
Edit 2: both machines are 64 bit

---

### Post by OrangeCrate on 2008-09-23
> **Kerilk said:**
> Updated to 2.6.27-4 and sound on integrated Intel shipset is not working anymore.

Two affected computers :

<snip>

Edit : first is **32 bit**, second is 64 bit

I'm assuming this thread is about the 64 bit version. At least for me, the 32 bit kernel upgrade is being held back. Did you install the 64 bit version on that machine, or am I missing something here?

---

### Post by rbmorse on 2008-09-23
The Update Manager delivered the 32-bit -4 to me last night without any drama at all. In fact, I would not of noticed the kernel update at all except for the dialog box that popped up asking what I wanted to do about GRUB's menu.lst

---

### Post by OrangeCrate on 2008-09-23
> **rbmorse said:**
> The Update Manager delivered the **32-bit -4** to me last night without any drama at all. In fact, I would not of noticed the kernel update at all except for the dialog box that popped up asking what I wanted to do about GRUB's menu.lst

I don't normally use the Update Manager, but opt for apt-get to do all my upgrades. I just checked from the terminal, and it's still being held back. Checking with Update Manager, the kernel upgrade is grayed out, so at least for me, it's still unavailable. Oh well, not unexpected. It'll catch up eventually...

---

### Post by Kerilk on 2008-09-23
> **OrangeCrate said:**
> I'm assuming this thread is about the 64 bit version. At least for me, the 32 bit kernel upgrade is being held back. Did you install the 64 bit version on that machine, or am I missing something here?

You are correct, the first computer used to be using 32bit ubuntu, I forgot I put it in 64 bit. So both are 64 bit machines indeed.

---

### Post by Kerilk on 2008-09-23
The later update of pulse audio corrected the problem.
Some channels were muted though so I did not get sound back immediately.

---

### Post by xlinuks on 2008-09-23
On 22 september I updated Intrepid to 2.27-4 and after reboot I got a blank screen which tells me the nvidia or xorg configuration (can't remember which one) is broken and asked me to configure it but the popped up dialog didn't work/solve anything either, so I'm back to 2.27-3.

---

### Post by forcotton on 2008-09-23
Sound here does not work. it's ICH6 chip set, intel integrated sound.
Is the new pulseaudio in the repo yet? Or do I have to refresh some config file?

---

### Post by rbmorse on 2008-09-23
> **OrangeCrate said:**
> I don't normally use the Update Manager, but opt for apt-get to do all my upgrades. I just checked from the terminal, and it's still being held back. Checking with Update Manager, the kernel upgrade is grayed out, so at least for me, it's still unavailable. Oh well, not unexpected. It'll catch up eventually...

try sudo apt-get dist-upgrade

and see if that frees the kernel upgrade.

---

### Post by jfernyhough on 2008-09-23
> **xlinuks said:**
> On 22 september I updated Intrepid to 2.27-4 and after reboot I got a blank screen which tells me the nvidia or xorg configuration (can't remember which one) is broken and asked me to configure it but the popped up dialog didn't work/solve anything either, so I'm back to 2.27-3.Assuming 27-4 is still installed (including headers), if not install (and probably reboot):

Go into Synaptic, search by name for nvidia and select all those currently installed for reinstallation.

This will install the necessary files for DKMS to install the module for 27-4.

Now reinstall linux-image-2.6.27-4. This should trigger DKMS to install the nvidia module. If it doesn't work, reboot and try again.

There's bound to be an easier way, but this worked for me.

---

### Post by OrangeCrate on 2008-09-23
Confirm that 32 bit kernel 2.6.27-4 is installed, and working fine.

---

### Post by Swarms on 2008-09-23
I told the popup by a mistake that it should keep Grub settings, I have the menu.lst file open, but can't see anything about 2.6.27-4, anyone who could copy their info in so I could put it in my?

---

### Post by BackwardsDown on 2008-09-23
> **Swarms said:**
> I told the popup by a mistake that it should keep Grub settings, I have the menu.lst file open, but can't see anything about 2.6.27-4, anyone who could copy their info in so I could put it in my?

You can just copy paste the -3 entry and edit into -4. It should just work.

---

### Post by caryb on 2008-09-23
> It doesn't make my speaker beep madly till it's booted now! 
I spoke way too soon, I booted this morning & my PC speaker went mad & I had to shutdown before it woke the inhabitants of my house:( Then had to boot into recovery mode & remove the quiet & splash again! It's ironic that I have to remove the quiet to get peace & quiet:)


Cary

---

### Post by BanjoBoy on 2008-09-23
Not working in kernel 2.6.27-4 (and all previous 2.6.27)!

After upgrading to Intrepid Ibex my Hauppauge WinTV USB2 device stopped working (using v4l and pvrusb2 kernel modules). If I attach the Hauppauge device the boot hang/freezes at "Starting bluetooth", if connecting it after the boot the pvrusb2 module never loads the device firmware and does not get the devices (/dev/video0 or /dev/radio0) up and running.

If I boot into kernel 2.6.26-5 it works.

---

### Post by rbmorse on 2008-09-23
> **Swarms said:**
> I told the popup by a mistake that it should keep Grub settings, I have the menu.lst file open, but can't see anything about 2.6.27-4, anyone who could copy their info in so I could put it in my?

open a terminal and run

sudo update-grub

should take care of things

---

### Post by wilbur.harvey on 2008-09-23
Kernel 2.6.27-4 (64-bit) installed just fine on my Intel Quad Core Shuttle, but of course the Nvidia stuff was totally broken.
The only way I could get it working was to re-create my xorg.conf file which it had deleted, not very nice.
The nvidia-settings would core dump when trying to write the xorg.conf file.

On my MacBook Pro (Gen2) the kernel (64-bit also) still won't install due to missing dependencies.

Of course vmware is still broken as well.

---

### Post by yakumo9275 on 2008-09-24
2.6.27-4 fails for me. Gives me something about corrupt ACPI andd then it fails to find root either with guid/or directly as /dev/sda4 etc.

2.6.27-3 works fine.. but I cant run 2.6.27-4 in any shape or form.

I too still get all that beeping if I leave splash on.. this is on x84-64 edition

(asus p5q-e, intel q9550, nvidia 9800gt, 8gb ram)

-stu

---

### Post by xlinuks on 2008-09-24
> **jfernyhough said:**
> Assuming 27-4 is still installed (including headers), if not install (and probably reboot):

Go into Synaptic, search by name for nvidia and select all those currently installed for reinstallation.

This will install the necessary files for DKMS to install the module for 27-4.

Now reinstall linux-image-2.6.27-4. This should trigger DKMS to install the nvidia module. If it doesn't work, reboot and try again.

There's bound to be an easier way, but this worked for me.

Thanks, today from 2.6.27-3 there was another wave of updates of like 100MB and after applying them I booted to 27-4 and this time it worked/works fine.

---

