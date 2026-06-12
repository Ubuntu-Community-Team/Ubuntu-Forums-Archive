---
title: "Cannot install Xubuntu. GPU issue?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by curambar on 2010-08-29
As the title says, I cannot install xubuntu. So far I tried 8.04, 9.10, 10.04, alternate and desktop versions.

Technical data: I have a Packard Bell Easynote R9201 (oldie), 1.6 GHz Centrino, 1GB RAM, Nvidia GeForce Go 6200 128MB.
I have already double checked the MD5 of all distros, I already tried USB flash drive install...

Symptoms: With 10.04, I have nothing, either I select Live CD or Install, I got a black screen.
With 9.10 alternative, it starts installing, but then it says files are missing from the CD-flash drive. I used this same CD in another computer afterwards and it installs xubuntu perfectly, so it's not the CD.
With 8.04, I tried Live CD, and after a progress bar, i get flashing color screens, and nothing else.

I pressume it's the gpu. Is there a way to tell the installer not to use the geforce? Like, use only the built-in graphics card.

Thanks in advance!

---

### Post by oldfred on 2010-08-29
I have a newer Nvidia card and the monitor would just to to sleep. Because I was installing from a USB flash drive I could still see activity, it was still installing.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by curambar on 2010-08-29
Thanks, oldfred, it worked :P

Just installed Ubuntu 8.04 with Safe Graphic mode, and it installed (FINALLY). Then, once inside hardy, I checked the nvidia drivers (it said there were not free soft, or something like that), and everything is just peachy.

Now I will leave this thing updating to lucid all night (low speed internet U_U) and tomorrow, I'll be posting here again, 'cause I'm sure some problem will arise ^_^

---

