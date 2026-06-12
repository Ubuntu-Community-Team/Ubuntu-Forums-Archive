---
title: "A variation on the &quot;waiting for root filesystem&quot; problem"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by sesquipedality on 2006-06-10
OK, so I have what seems to be a common problem with 6.06, but none of the solutions appear to apply to my system.

I'm running Ubuntu on an ASUS A7M266 motherboard with an Athlon 1400 chip.  There are two hard drives, hda and hdb on ide0.  hdc on ide1 is a DVD drive.  I did an upgrade from breezy (actually from hoary via breezy, but don't get me started on that one), and the 2.6.15 kernel won't boot, hanging at the "waiting for root filesystem" message, and eventually announcing it can't find /dev/hda1.

I've tried booting with ide=nopci, lapic (for some reason my BIOS has disabled this), acpi=off.  No joy from any of these options.  Looking at the ramfs, there are no /dev/hd* devices at all present, despite the fact that the last kernel messages before the dreaded "waiting ..." indicate that the kernel has correctly recognised my IDE interfaces and my drives.  2.6.12 from Breezy does manage to boot.

Anyone got any ideas?  I'm rapidly running out of them,

---

### Post by peaceful_dragon on 2006-06-14
I need to bump this thread, I am experiencing the same kind of problems. Only, for me, I have only two drives!

In breezy:
/dev/hda on ide0 (hard disk)
/dev/hdc on ide1 (CD-RW drive)

Ubuntu is installed on /dev/hda3 (3rd partition)

But dapper wants to boot from /dev/hdc3 for some reason.

> ALERT! /dev/hdc3 does not exist. Dropping to a shell!

Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off

---

### Post by sesquipedality on 2006-06-14
I'm still just as stuck.  None of the documented solutions for similar problems seem to be working for me.

Interestingly the Dapper Install/Live CD boots on the same system, although there is a delay at bootup with seek errors on the DVD drive.  My hard disk partitions are mountable from the install disk, just not when I boot from the kernel installed on the system.

I've tried both with the K7 optimised kernal and the standard 386 one.

Someone please help - I need this system back.

---

### Post by Gerr on 2006-06-15
I had a similar problem. It's hard to tell how similar because you haven't posted much information about the problem, so I'll give you some info from what I did to see if it provides you with any help.

When booting off of the harddriver, I told grub to load the recovery image. This boots and doesn't display the splash screen. You can watch the detailed messages. On my system, my harddrives were never detected because I have two sata II drives and apparently, sata II modules aren't loaded for device detection right now. 

After I found that this was the problem (and searches came up with no easy fixes -- or easily found fixes ;) I decided that what I needed was a kernel image that I could boot from. I loaded the live CD again (in my case, I'm using 6.06). Once this loaded, I mounted my root filesystem in a gnome-terminal session and performed the command chroot /mnt. Then I downloaded a recent kernel from kernel.org. I took the config from /boot/ and placed it in the new kernel's root directory as .config. After using apt-get to obtain the tools necessary to build a kernel (a quick solution might be to do apt-get build-dep <linux-source-current-image> -- find out what the current kernel source is by using apt-cache search). I then did a make oldconfig on the kernel to get the new items addressed. Follow this with make (and wait ... wait ... wait ... wow, there sure are a lot of modules enabled in the base kernel, but I guess that's necessary when dealing with so many different systems). This step will take a very long time. Even with my dual core 3.8Ghz CPU, it took longer then I had expected. Once this is done, copy the bzImage to /boot/, make modules_install, then mkinitramfs -o /boot/<name> <kernel-ver> ... Take the file names and edit the /boot/grub/menu.lst file and perform a grub-update. After this, I rebooted, selected my new kernel from the grub menu and the system easily found my sata II drives.

I realize that's a lot of work and there may be a better way to do it. I think the key thing here is to first try booting with the rescue mode so that you can see more of the error reports. Read them very closely to see if/what it has to say about the hardware in your system. Your milage may vary because your problem may be unrelated to mine. Anyway, I hope this helps even if just a little.

---

