---
title: "Cannot install Ubuntu 16.04"
date: 2017-03-10
forum: Installation &amp; Upgrades
---

### Post by wvphysicist on 2017-03-10
I tried installing Ubuntu 16.04 using the following materials:
File on a DVD:   ubuntu-16.04.0-desktop-amd64.iso
Motherboard Asus A88XM-A/usb 3.1 RTL
CPU:   AMD KA10 7700K 3.8G 4M FM2+ 95W

The DVD spun fast but the screen blanked before any non-trivial display and remained blank for a half hour.
The DVD later installed Ubuntu on a Optiplex GX520 correctly so it is good.

I bought this tower for Ubuntu 16.   It appears I am out of luck.
Nothing on the download web page warned me about this problem.
I have since read notes that suspect the video circuit is not being properly driven.

Is there any solution?

---

### Post by howefield on 2017-03-10
Not a chat thread, so moved to the "*Installation & Upgrades*" forum.

---

### Post by oldfred on 2017-03-10
UEFI or BIOS boot?
Best to use newest Ubuntu 16.04.2 or even the still in testing 17.04, to be final next month.

What video card/chip? Or internal video.
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

Have you tried nomodeset? Or you may need other boot parameters also?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by wvphysicist on 2017-03-12
Thanks for the many links and ideas most above my level but interesting.

I got a fix, likely not the best, using a video card that was in the junk box.
I put it into the extended PCI slot.   It had the letters GTX745DE and I suppose that is the INVIDIA part number.
Some changes got made to the UEFI section under North Bridge:

IGFX       Enabled
Primary video     PCIE/PCI Video
Integrated Graphics      Force
UMA Frame Buffer        Auto

I lost track of the defaults and have no way to find them.

During the install I believe Secure Boot was disabled.  

Now everything is normal, with the output from the card.  I have no idea why this worked or even what each step did.

The boot process is taking a long time compared to Ubuntu 14.04 on an Optiplex GX520.

I hope to download the other versions in the links and try them.

---

### Post by wvphysicist on 2017-05-06
There was an issue with the UEFI and the motherboard was returned for repairs.
When I got it back the Video card was no longer needed and the previously installed Ubuntu 16.04 worked normally.

Now I want to see more than a blank screen during boot.
I miss the thousand scrolling messages that Mandrake used to show years ago during boot.
I modified the grub menu to remove "quiet" and so now the grub menu appears for a short time.
That was useful but not completely satisfied.
Using the "e" for edit I tried adding NOMODESET but it had no effect. 

Is there anything else that I can try?

---

### Post by ubfan1 on 2017-05-06
Try removing the "splash" argument also, or just type Esc during the boot to switch to the text screen with messages.

---

### Post by oldfred on 2017-05-07
You can test options when booting, by editing linux line. Use e to edit at grub line.

To permanently change:
sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by wvphysicist on 2017-05-07
As usual nothing works.  This is Ubuntu 16.04.  Escape has no effect.  Just removing quiet only enables the grub menu to flash for a moment.  Then it is a black screen again for 30 seconds.  Then the desktop appears.

---

