---
title: "gnome init freezes in Ubuntu 9.10 on new Intel DH55TC"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by oreomike on 2010-01-13
I just purchased a new Intel DH55TC motherboard, a Core i5-661 processor, a WD Caviar Green 640GB drive, and a Linksys WMP110 card.

I was able to successfully install 9.10, but every time it loads to the desktop it freezes.  It seems like it may be an ACPI problem with the built-in H55 graphics card on the CPU.  

I hit 'e' at the grub prompt, and added 'noacpi' to the end of both the kernel (or linux?) line and the initrd line.  WHen I did that, I was able to get to a point that it was fully loaded and I could move the mouse around, but as soon as I opened a menu, like 'Applications', the desktop froze again.


(NOTE: I have today's daily 10.04 on a USB, and will try that next as a live disk)

---

### Post by oreomike on 2010-01-14
Removing the WMP110 WiFi card didn't improve anything.

Not exactly a fix, but I've added acpi=ht to the kernel boot command, and it boots successfully (and quickly.)  All other suggestions on the [https://wiki.ubuntu.com/Debugging/ACPI](https://wiki.ubuntu.com/Debugging/ACPI) page did not work. 

Next step, I'll update the BIOS firmware.

---

### Post by oreomike on 2010-01-14
Updating the BIOS firmware to version 028 (2009.1205) did not correct the problem.

Opened [bug 507770]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507770") in launchpad. :(

---

### Post by jpules on 2010-01-17
I was thinking of buying one of these motherboards to put together a mythbuntu frontend (built-in HDMI was main reason.)

This thread appears to be one of the only reporting issues with compatibility. Is there generally a problem with the linux driver for these chipsets? Should I consider a platform with more mature drivers?

Has anyone had success using the HDMI output on the Intel H55 chipset under Ubuntu?

Thanks for any help and good luck with this issue.

---

### Post by oreomike on 2010-01-17
> **jpules said:**
> This thread appears to be one of the only reporting issues with compatibility. Is there generally a problem with the linux driver for these chipsets? Should I consider a platform with more mature drivers?

Still somewhat new, so you won't find too many people reporting it yet.  I had seen a site, here: [Intel DH55TC]("http://www.systemadminihater.com/linux/intel-dh55tc-linuxvirtualization-tests/"), that said he/she had luck.

Seems though that after I upgraded, my stability has degraded.  Now I get 'System has halted' messages when shutting down.  Grr.

---

### Post by achiav01 on 2010-01-27
I set up a wiki page about this board at:
[https://wiki.ubuntu.com/Intel_DH55TC](https://wiki.ubuntu.com/Intel_DH55TC)

---

### Post by Kanna2412 on 2010-03-31
> **oreomike said:**
> Still somewhat new, so you won't find too many people reporting it yet.  I had seen a site, here: [Intel DH55TC]("http://www.systemadminihater.com/linux/intel-dh55tc-linuxvirtualization-tests/"), that said he/she had luck.

Seems though that after I upgraded, my stability has degraded.  Now I get 'System has halted' messages when shutting down.  Grr.

Hi buddy,

I also have the same problem with **Intel DH55TC motherboard**. It is freezing after booting to **Ubuntu 9.10**. Keyboard and mouse are not working. But it is working in CLI mode.

I contacted Intel support regarding the same. They emailed me the below link and suggested me to install the drivers by going to CLI mode so Ubuntu 9.10 will work. As per them, the problem is with Keyboard and Mouse drivers.
[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)

Now my problem is that I don't know how to install the drivers through CLI mode.

If you know that above please let me know.

Regards,
Kanna,
**Indian**.

---

### Post by oreomike on 2010-03-31
> **Kanna2412 said:**
> Hi buddy,

I also have the same problem with **Intel DH55TC motherboard**. It is freezing after booting to **Ubuntu 9.10**. Keyboard and mouse are not working. But it is working in CLI mode.

I contacted Intel support regarding the same. They emailed me the below link and suggested me to install the drivers by going to CLI mode so Ubuntu 9.10 will work. As per them, the problem is with Keyboard and Mouse drivers.
[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)

Now my problem is that I don't know how to install the drivers through CLI mode.

If you know that above please let me know.

Regards,
Kanna,
**Indian**.

All I had to do was add acpi=ht to the kernel boot options in GRUB, then update the kernel to a development Kernel.([https://wiki.ubuntu.com/Intel_DH55TC?action=recall&rev=17](https://wiki.ubuntu.com/Intel_DH55TC?action=recall&rev=17)) Once I did that, everything worked.

I haven't had any trouble with USB KB/Mouse.

(Note: Rev 17 had instructions on how to use a beta kernel level)

---

### Post by Kanna2412 on 2010-04-03
> **oreomike said:**
> All I had to do was add acpi=ht to the kernel boot options in GRUB, then update the kernel to a development Kernel.([https://wiki.ubuntu.com/Intel_DH55TC?action=recall&rev=17](https://wiki.ubuntu.com/Intel_DH55TC?action=recall&rev=17)) Once I did that, everything worked.

I haven't had any trouble with USB KB/Mouse.

(Note: Rev 17 had instructions on how to use a beta kernel level)


When my computer is booting, it is asking me to choose "Ubuntu Linux 2.6.31.14-generic". Do I need to install "v2.6.33/" or "v2.2.6.31"?

I am new to Linux. I just downloaded the files, went to CLI mode, entered the command "sudo dpkg -i linux-image...........". But I got error message as below.
"error processing Linux-image-2.6.33...............
cannot access archive: no such file or directory
errors were encountered while processing
Linux-image-2.6.33................."

After that I rebooted the system. It did not work. Please Help!

Indian

---

### Post by wolfmyst63 on 2010-04-05
I found a solution. I too have the DH55TC motherboard, and with 9.10 it was locking up at various stages up to the first click on the desktop. 

After trying many things, I honed the problem to a bios option.

To fix:
Disable the CPU C STATE option in the POWER section (right side) in the BIOS. Press F2 right after powering the computer on to access the bios.

I have not updated ubuntu yet, or upgraded the firmware FYI.

---

### Post by wolfmyst63 on 2010-04-05
Update: upgrading firmware from 2009.1019 to 2010.0327 did NOT fix the problem. That firmware is only a week old. Ubuntu kernel is not latest version however, so I will see if getting the new kernel fixes the CPU C State issue.

---

### Post by achiav01 on 2010-04-06
I believe the problem was fixed in 9.10 by a kernel update was it not ?
It is also completely fixed in Ubuntu 10.04.
The beta1 is out already. beta2 is due 8 April and final release is due 29 April.
Having CPU C State enabled is a good feature that will make the CPU produce much less heat.

---

### Post by wolfmyst63 on 2010-04-07
I agree, CPU C State is useful, especially for laptops. 
If a kernel update does indeed fix the problem, then disabling the CPU C State just enables you to boot into the desktop and run a system update and after the reboot re-enabiling it. This would really be the easiest way to accomplish a kernel update for someone not familiar with linux. Alternatly you could load up another tty session when you reach the login prompt or select single user (recovery) mode and update the kernel that way.

> **achiav01 said:**
> I believe the problem was fixed in 9.10 by a kernel update was it not ?
It is also completely fixed in Ubuntu 10.04.
The beta1 is out already. beta2 is due 8 April and final release is due 29 April.
Having CPU C State enabled is a good feature that will make the CPU produce much less heat.

---

### Post by Kanna2412 on 2010-04-09
> **wolfmyst63 said:**
> I agree, CPU C State is useful, especially for laptops. 
If a kernel update does indeed fix the problem, then disabling the CPU C State just enables you to boot into the desktop and run a system update and after the reboot re-enabiling it. This would really be the easiest way to accomplish a kernel update for someone not familiar with linux. Alternatly you could load up another tty session when you reach the login prompt or select single user (recovery) mode and update the kernel that way.

Yes, it is really working. Thank you very much dear Wolf. 

Video is pausing and skipping in Media player and even in VLC player. Do I need to install graphic driver for the board? If so Please let me know the commands for installation.

Indian

---

### Post by ashishkg on 2010-04-12
Thanks. I could also get the same problem corrected on my new system.

However The machine hanged in the same way while further trying to reference one website for LAMP installation. 
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)

The problem happened while trying to view one of the screenshots.

Not sure if this problem has same root cause... But the hang problem does not seem to be solved completely in Kernel 2.6.33.

---

