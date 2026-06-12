---
title: "New kernel problems - kernel panic - dpkg-gencontrol: error - 10.04 Lucid Lynx"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by foolishchild on 2010-08-26
This is what I had to do to get a new kernel compiled on Lucid Lynx 10.04. I hope it helps somebody.

[LIST=1]
[*]Follow this instruction
[INDENT]The basic instructions at [wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") worked pretty well but...[/INDENT]

[*]Problem one

I followed steps 1 to 8. Step eight failed with
```
dpkg-gencontrol: error: package linux-image-2.6.36-rc2-custom+ not in control info
``` 
I found [this wonderful person's post]("http://art.ubuntuforums.org/showpost.php?p=9638461&postcount=1488") which told me that I had to **edit debian/control while the compile was running**, and change the name of the image and headers by adding a '+' to the name. That worked - for some reason the compiled kernel name had a '+' appended, and I needed to tell the control file.


[*]Problem two

I then completed steps up to 11, but when I re-booted I got a kernel panic, and the boot stopped, very quickly. To overcome that I had to:
[LIST]

[*]boot into the old (working) kernel
[*]```
sudo update-initramfs -c -k 2.6.36-rc2-custom+
```
[*]```
sudo update-grub2
```
[/LIST]
[/LIST]

All of this was because I wanted to get bluetooth working so I can sync my Nokia phone with the PC - possibly using evolution. On my Lucid Lynx system with kernel vmlinuz-2.6.32-24-generic, bluetooth is extremely unreliable, using a generic bluetooth USB dongle. First impressions are that this new kernel (which was a swine to install) has sorted out the basic bluetooth timeout problems. Now all I need is a decent sync solution to something I can easily edit on the PC.

---

