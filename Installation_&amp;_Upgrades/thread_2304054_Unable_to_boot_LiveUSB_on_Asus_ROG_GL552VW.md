---
title: "Unable to boot LiveUSB on Asus ROG GL552VW"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by jayramj on 2015-11-24
Hello,

I have recently purchases an ASUS ROG GL552VW. It comes with NVIDIA® GeForce® GTX 960M with 2G/4G GDDR5 VRAM. I am trying to setup Dual Boot with Win10 being the other OS

I am trying to install Ubuntu Gnome 15.10 using a LiveUSB. Initially it used to hang with nouveau errors. Now I am booting with following options 
```
nouveau.modeset=0 nouveau.blacklist=1
```

With these options I am able to see the Gnome desktop loaded. After I click couple of times the system freezes & neither keyboard nor mouse responds. Same happens if instead of going into a "Live" session I go for installation. After clicking through first couple of steps the system freezes

Any ideas what I need to do to get myself up & running on this system

Your help much appreciated. 

Thanks,
- JJ

---

### Post by aschoerk on 2015-12-23
Hello,
I just installed Linux Mint-Mate 17.3 on ASUS ROG752VW. 
No version of 15.10 did work for me, sadly.
Did you get further meanwhile, does your touchpad work?

Greetings,
Andreas

---

### Post by ubfan1 on 2015-12-23
Try the Skylake options, below.  When running, immediately install the Nvidia driver from "Additional Drivers" tab from the software update/Settings.
For UEFI machines (with a black screen grub (grub-efi)  without any
function key options, like the older grub-pc, edit the grub menu and add
the below options on the "linux" line, then boot with F10 or ctrl-X.


Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

newer:
i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Skylake needs this (15.04...):
i915.preliminary_hw_support=1
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by jdelano on 2015-12-28
@[[COLOR=#000000]ubfan1[/COLOR]]("http://ubuntuforums.org/member.php?u=1256996")

I wanted to thank you for your post here.
I received this laptop for Christmas and I use Ubuntu to create ROMs for android phones. So its a must.

I used these parameters to boot "try Ubuntu"; I created a new menu item so as to not modify the default settings on grub.cfg.

```
menuentry "Try Ubuntu for ASUS GL552VW" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper i915.preliminary_hw_support=1 nouveau.modeset=0 nouveau.noaccel=1 nomodeset acpi=0 acpi_osi=linux acpi_backlight=vendor noalpic intel_idle.max_cstate=1 ---
    initrd    /casper/initrd.lz
}
```

I was able to install 15.10; after it completed I restarted from the USB stick one more time and modified the grub.cfg on my laptop using the same added options:
```
i915.preliminary_hw_support=1 nouveau.modeset=0 nouveau.noaccel=1 nomodeset acpi=0 acpi_osi=linux acpi_backlight=vendor noalpic intel_idle.max_cstate=1

```
Then restarted and used the grub menu on the hard drive, Ubuntu 15.10 started right up.

For completeness, the only option I changed to dual boot was fast boot in windows 10. Nothing was changed in the UEFI/BIOS settings. Matter of fact, I modified a bunch then did a reset defaults once I found these options to pass to linux in this post.

Thank you again for taking the time to answer the original question.

EDIT:
The better solution is to modify /etc/grub.d/10_linux to that any subsequent updates don't over write the grub.cfg file and thus your modifications.

So 
```
sudo gedit /etc/grub.d/10_linux 
```
look for line 177, it should start with 
```
linux    ${rel_dirname}/${basename}.efi.signed root=${linux_root_device_thisversion}
```
then after **ro** add 
```
nmodeset acpi=0 acpi_osi=linux acpi_backlight=vendor noalpic i915.preliminary_hw_support=1
```
save and close the file then update grub via 
```
[COLOR=#333333][FONT=monospace]sudo update-grub[/FONT][/COLOR]
```

is what worked for me.

---

### Post by g_j2 on 2016-02-08
Using the information above as a starting point, I finally managed to install Ubuntu 15.10 on an Asus ROG GL752V.

When booting the install medium the normal way, the system would just become completely unresponsive after having selected one of the options in the boot menu. The solution to this turned out to be as follows:
- In the boot menu, navigate to 'Try Ubuntu' and press 'e'.
- Add intel_idle.max_cstate=1 on the 'linux' line, before 'quiet splash'
- Press F10 to boot

The 'Try Ubuntu' system then booted just fine, with the intel graphics driver loaded. I then clicked 'Install Ubuntu'. On the reboot after installation I had to press 'e' when the boot menu appeared, and add  intel_idle.max_cstate=1 in the same way as described above.

After having logged in I then made the cstate option permanent by:
- modifying one line in /etc/default/grub : GRUB_CMDLINE_LINUX="intel_idle.max_cstate=1"
- executing the command: sudo update-grub

I then installed the nvidia drivers without any problems.

A couple of notes:
- I first made a go using all linux boot options suggested in the post above, but this prevented both the intel and nvidia drivers from working.
-  intel_idle.max_cstate=0 also works fine on my system.

---

### Post by jarek_s on 2016-02-27
Hi there,

Do you know if connecting GL552VW to external monitor via USB 3.1 works on Ubuntu?
I am considering getting this laptop for work (web-programming in Ubuntu) as it has really nice specs, but dual monitor support is a must for me, and it has only a single HDMI :-(


Thanks in advance,
Jarek

---

