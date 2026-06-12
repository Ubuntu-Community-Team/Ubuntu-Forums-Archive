---
title: "Installing nvidia graphics drivers reliably causes kernel panic- borks boot process"
date: 2017-12-20
forum: Installation &amp; Upgrades
---

### Post by phildo2 on 2017-12-20
I have a windows machine with a partitioned hard drive. I install ubuntu-17.10-server-amd64.iso (w/ a USB stick formatted by roofus, w/ UEFI).
I just do a stock installation- nothing special at all. I have an NVidia 1080 Ti graphics card.

Then, I run `sudo add-apt-repository ppa:graphics-drivers/ppa`, `sudo apt-get update`, then `sudo apt-get install nvidia-381`. It installs a bunch of stuff, and then kernel panics, and restarts, and then on boot it fails with an error in /boot/uefi (or something like that), and launches into "emergency mode". if I try to "apt-get" anything in emergency mode, it says "it's borked- run apt-get --configure -a to resume"- I do so, and it again kernel panics, and we're back to square 1.

Also, I've tried switching out the previous commands with `sudo apt-get install nvidia-latest` - same results.

Edit: I've also installed NVIDIA-Linux-x86_64-340.32.run from the nvidia website- this installed fine (once it made me blacklist nouveau) [and by "installed fine" I mean "The monitor blacked out half way through and it restarted, and the only way I could resume the install was to ssh in"]. But shortly after, when installing another program that makes use of the graphics drivers (hashcat), it kernel panicked, and screwed up the boot process.

I want to install the drivers for use with OpenCL- hence using ubuntu server instead of ubuntu.

1. Why is this failing?
and
2. How do people w/ ubuntu install nvidia drivers?

---

### Post by Bashing-om on 2017-12-21
phildo2l Hello - Welcome to the forum .

UEFI system often times is secure boot . Have you checked in bios and disabled secure boot ?
The graphic's driver is 3rd party and will not install properly if that secure boot is enabled..

Be aware that only one driver may be installed to the system at any time.
```

dpkg -l | grep -i nvidia*

```
[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by phildo2 on 2017-12-21
secure boot _is_ disabled on my system. that is, 

mokutil --sb-state

displays "SecureBoot disabled"

what is the common procedure for downloading nvidia drivers?

---

### Post by Bashing-om on 2017-12-21
phildo2; Well:
> 
what is the common procedure for downloading nvidia drivers?

answer:
```

sudo ubuntu-drivers autoinstall

```

But ! All other graphic's drivers are properly removed -
if present config files are removed for the old driver -
and
the system is updated .

[INDENT][INDENT]easy as falling out of bed wide awake
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2017-12-22
I usually install the drivers with
```
sudo apt install nvidia-current
```

If you want a specific version, first run
```
apt-cache search nvidia
```
and you'll see a list of available drivers like nvidia-384.  I'm currently using that with my GTX 750.

---

