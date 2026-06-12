---
title: "Bricked GRUB after boot-repair"
date: 2020-08-07
forum: Installation &amp; Upgrades
---

### Post by hagemeister on 2020-08-07
Dear all,

I'm running Ubuntu 18.04LTS since a while next to my windows 10. Out of the blue, GRUB did not seem to boot into my Ubuntu anymore; it got stuck in GRUB's command-line interface (it seems more people had this problem over the past days). It was still possible to boot using the sequence:

set prefix=(hd0,gpt5)/boot/grub
set root=(hd0,gpt5)
insmod linux
insmod normal
normal

Yet, running sudo update-grub after booting did not fix the issue. I then decided to use boot-repair to try to fix the problem, and followed the instructions of [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) using a bootable stick. This was not successful; boot-repair threw an error with the message: locked-nvram detected. At this point I'm even unable to boot into Ubuntu using the sequence above. Before I'm trying other stuff and really mess up my system beyond repair I'd like your input on my situation. Pastebin is available on: [https://paste.ubuntu.com/p/Ddq6jCfq2t/](https://paste.ubuntu.com/p/Ddq6jCfq2t/)

What would be the best way to proceed from here?

---

### Post by oldfred on 2020-08-07
Windows updates turn fast start up back on, which sets hibernation flag. Even if you originally turned it off, you need to turn it off again.
> Windows is hibernated, refused to mount.

A few systems also have settings in UEFI that may lock the ESP for security reasons. Check UEFI settings. You may from Windows also had an UEFI update which may change some settings back to defaults. You may also want to check if UEFI Secure Boot is on or not. 

A sudo update-grub just updates menu, often you have to do the full chroot or use Boot-Repair's advanced mode to do a full grub reinstall. But Windows fixes need to be done first.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by hagemeister on 2020-08-07
Thanks oldfred, this indeed seemed to be the solution. Though I'm surprised; secure boot and fast start were off... Maybe something else update-related? GRUB still has some problems so I guess I'll going to look towards a full grub reinstall.

---

### Post by pbear42 on 2020-08-07
> **hagemeister said:**
> ... guess I'll going to look towards a full grub reinstall.
Before you do that, try manually installing Grub from a live session.  Can't recall seeing that NVRAM-locked error before, so maybe this won't go through, but it's a normal procedure and can't hurt.  Boot the live session, set up an internet connection, open Terminal, and run the following commands, one line at a time.  First line needed because those packages aren't installed by default in the live session (rather they're added by the installer only if needed).
```
sudo apt install grub-efi-amd64-signed shim-signed
sudo mount /dev/nvmeOn1p5 /mnt
sudo mount /dev/nvmeOn1p2 /mnt/boot/efi
sudo grub-install /dev/nvmeOn1 --boot-directory=/mnt/boot --uefi-secure-boot
```
If this doesn't work, the live session is a good way to make sure you've copied out any files you want/need before reinstall.  Good luck.

By the way, in future, if you find yourself in this fix, it's easy to reinstall Grub if you're able to boot at the Grub prompt.  All it takes is sudo grub-install /dev/nvmeOn1.  When booted to the system you want in charge of Grub, the grub-install script is able to figure out everything else.  Indeed, more reliable than the Boot Repair app.

---

### Post by hagemeister on 2020-08-07
> **pbear42 said:**
> By the way, in future, if you find yourself in this fix, it's easy to reinstall Grub if you're able to boot at the Grub prompt.  All it takes is sudo grub-install /dev/nvmeOn1.  When booted to the system you want in charge of Grub, the grub-install script is able to figure out everything else.  Indeed, more reliable than the Boot Repair app.
Thanks for the tip. That's indeed a more elegant approach.

Yet I have found out that the remaining problems were actually not caused by grub. There were some errors related to initramfs that made only one of my three (?!) kernels boot, but these seemed to be fixed using fsck. This introduced a new boot problem where the screen kept stuck on a nice purple wallpaper. Eventually I uninstalled the ROCm driver and reverted that to amdgpu-pro, as that was the last big change I made to my system a week ago. That eventually fixed everything.

Now I'm just left wondering whether it was Windows, the driver or some other factor that set this all in motion... Anyways, thanks for the help guys :)

---

