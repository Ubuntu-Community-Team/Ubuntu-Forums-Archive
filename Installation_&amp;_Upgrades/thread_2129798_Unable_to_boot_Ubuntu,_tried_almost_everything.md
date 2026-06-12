---
title: "Unable to boot Ubuntu, tried almost everything"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by sevteen on 2013-03-27
I had dual-boot configuration on ma PC: windows7 and ubuntu. Ubuntu was installed after windows7 and everything was working perfectly... But one day I was installing **MonoDevelop** from Ubuntu Software Center and suddenly every icon dissapeared (sometimes Nautilus errors appeared before) and system got **unresponsive**, I couldn't even **log out** or **shutdown**, so I forcibly restarted pc from restart button.  After reboot I end up with this message:

     [COLOR=#0000FF]error: file '/boot/grub/i386-pc/normal.mod'[/COLOR][COLOR=#0000FF] not found.
     grub rescue>[/COLOR]

after that I followed these [https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Restore-Grub-e.g.-because-the-Windows-DVD-has-overwritten-Grub-](https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Restore-Grub-e.g.-because-the-Windows-DVD-has-overwritten-Grub-) instructions, afterwards Windows7 was booting automatically;

Then I used boot-repair utility which cause promting "Minimal BASH-Like line editing is supported.." message at every startup, I thought it's almost done but... not too fast..
I followed several instructions, but they all share same procedure which I can not execute, e.g. can't run command 'find' or 'root'...
Anyways here is BootInfo created by boot-repair: [http://paste.ubuntu.com/5652017/](http://paste.ubuntu.com/5652017/)

Thanks!

---

### Post by darkod on 2013-03-27
First I would try to run fsck on sda3 to repair any errors in the filesystem. Boot into live mode with your ubuntu cd and in terminal do:
```
sudo fsck /dev/sda3
```

I hope it's only some small corruption with the partition which makes it not show all the files, because it doesn't show many important system files as present. If they are really missing, it would be difficult to solve this. The better way would be to backup the data and do a new clean installation.

But do the fsck first and see if it changed anything.

After the fsck run the boot info again and post the new link.

---

### Post by sevteen on 2013-03-27
> backup the data and do a new clean installation

I did so, could not wait anymore :) 

Thanks

---

