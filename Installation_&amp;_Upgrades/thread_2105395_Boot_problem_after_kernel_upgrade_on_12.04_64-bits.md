---
title: "Boot problem after kernel upgrade on 12.04 64-bits server"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by RuralHunter on 2013-01-15
Hi,

I have a newly installed ubuntu 12.04 64-bits server on a Dell R720. There was no problem after the installation from the original installation image. Recently, I upgraded the kernel by using the command: "aptitude safe-upgrade".  After that, I got random boot problem. The boot hung at some step with this kind of message:
```

WARNING: at /build/buildd/linux-3.2.0/kernel/watchdog.c: 241
Hardware name: PowerEdge R720
Watchdog detected hard LOCKUP On cpu 31
Modules linked in: vesafb usbhid hid tg3 megaraid_sas wmi
Pid: 0, comm: swapper/31 Tainted: G D W 3.2.0-35-generic
Call Trace:
<NMI> [<ffffffff81067f0f>] warn_slowpath_common+0x7f/0xc0
[<ffffffff81068006>] warn_slowpath_fmt+0x46/0x50
.......

```

The problem is also a bit weird. If I encounter the boot problem, the system can not boot up on the same day, whatever it's a reboot or power off/up. But on the next day, it will boot up. 
Since this is a newly installed server, I also made other changes on the system before/after the upgrade. So I'm still trying to find the root cause. The first thing I want to check is the kernel upgrade. So I want to boot into the old kernel to see if the problem still persists. I have these files in /boot:
```

-rw-r--r-- 1 root root   791281  7&#26376; 28 01:44 abi-3.2.0-29-generic 
-rw-r--r-- 1 root root   792715 12&#26376;  6 02:22 abi-3.2.0-35-generic 
-rw-r--r-- 1 root root   140432  7&#26376; 28 01:44 config-3.2.0-29-generic 
-rw-r--r-- 1 root root   140505 12&#26376;  6 02:22 config-3.2.0-35-generic 
drwxr-xr-x 3 root root     8192  1&#26376;  9 21:50 grub 
-rw-r--r-- 1 root root 17294149  1&#26376;  9 21:49 initrd.img-3.2.0-29-generic 
-rw-r--r-- 1 root root 17297382  1&#26376;  9 21:51 initrd.img-3.2.0-35-generic 
drwx------ 2 root root    12288  1&#26376;  4 18:54 lost+found 
-rw-r--r-- 1 root root   176764 11&#26376; 27  2011 memtest86+.bin 
-rw-r--r-- 1 root root   178944 11&#26376; 27  2011 memtest86+_multiboot.bin 
-rw------- 1 root root  2882108  7&#26376; 28 01:44 System.map-3.2.0-29-generic 
-rw------- 1 root root  2885822 12&#26376;  6 02:22 System.map-3.2.0-35-generic 
-rw------- 1 root root  4960752  7&#26376; 28 01:44 vmlinuz-3.2.0-29-generic 
-rw------- 1 root root  4968400 12&#26376;  6 02:22 vmlinuz-3.2.0-35-generic

```

Is there a quick way I can boot into the old 3.2.0-29 kernel?

---

### Post by Herman on 2013-01-16
Since you don't have other operating systems in the same computer to choose from, your GRUB Menu isn't normally needed, so it doesn't normally show. 
I'm fairly certian you can get it to show up if you keep tapping your  'Esc' key during boot-up. 
Once you can see your GRUB Menu it will be simple to just use a down-arrow key to move the selection bar down a few lines and boot by an older kernel.

---

### Post by Herman on 2013-01-16
Another really good trick, but one that will take a bit longer to get set up with for the first time is to create an auxilliary Ubuntu installation in a USB flash memory drive.
This should be a real Ubuntu installation, which boots with GRUB, not a 'persistence' type, which uses syslinux for the boot loader.
You can boot the auxilliary installation and run update-grub in that. It will automatically scan your computer and give you a menu including itself and all your computer's kernels to boot with.  Then you can reboot once again and boot your computer from the USB's GRUB Menu. 

If you ever end up with really bad problems and even that doesn't work, you can use the USB auxilliary Ubuntu for [chrooting]("http://ubuntuforums.org/showthread.php?t=1156240") in and fixing your server installation. (apt-get update or whatever).
You need a 64bit architecture auxilliary installation to chroot into 64bit hard disk installed system or 32bit for chrooting into 32 bit hard-disk installed system.

---

### Post by RuralHunter on 2013-01-16
Ok, thanks for the detailed reply. I will try to get into the boot menu first

---

### Post by RuralHunter on 2013-01-16
Bad luck....boot into old kernel failed too. Any suggestion for that kind of cpu hard lock error?

---

### Post by Herman on 2013-01-17
I don't know. 

A quick google returned a few links that might be of interest or at worst may be red herrings,

In this particular instance they thought it was likely caused by a CPU heatsink installed improperly, [Watchdog detected hard LOCKUP on cpu <any>]("https://bugzilla.redhat.com/show_bug.cgi?id=837889") - fedora

This one's listed in Ubuntu bugs (although not confined to Ubuntu), and seems to be occurring after waking a computer from sleep, [watchdog detected hard lockup on cpu 1]("https://bugs.launchpad.net/ubuntu/+bug/1004313")

Then there's this one from Bugzilla, OpenVZ where they resolved it by patching the kernel, [**Bug 2041** -]("http://bugzilla.openvz.org/show_bug.cgi?id=2041")[        [039.x] Kernel crashes / hard LOCKUP]("http://bugzilla.openvz.org/show_bug.cgi?id=2041")

In this one from Suse it's thought to be triggered by a cpu thermal event, [[Bug 755731] New: Kernel panic, hard lockup on cpu when on heavy load]("http://lists.opensuse.org/opensuse-bugs/2012-04/msg00545.html")


Here's an interesting page that explains a bit about kernel lockups and watchdog daemons,[1  Debugging Linux Kernel Lockup / Panic / Oops]("http://www.av8n.com/computer/htm/kernel-lockup.htm")

---

