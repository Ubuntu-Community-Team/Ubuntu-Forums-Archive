---
title: "WARNING: Can't boot new 2.6.12-10 686 kernel"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by christian.convey on 2005-11-22
Hi guys, FYI...

I haven't had a chance to look into it much yet, but I'm not able to successfully boot under the new 2.6.12-10 686 kernel.   I could boot under all of the previously released Breezy kernels without any problem.

I've got an nForce4 motherboard (I forget which one), an Athlon64 3500+ processor, and a PCI nVidia video card.

The symptom is that the system freezes at various points in the boot process. The first time this happened, tapping my power button on the CPU successfully got the system to gracefully reboot. The second time I had the problem, I had to hold down the power button for a number of seconds to force a powerdown - tapping didn't work.

---

### Post by tokyovigilante on 2005-11-22
Why don't you try one of the -k7 kernels? This would be the closest (32 bit) match for your processor, or you could try the amd64 (-k8) version, however that introduces a new set of challenges, and would require a full reinstall rather than just a kernel upgrade.

Also, do you have the proprietary nForce chipset driver installed? You might find they're more stable/featureful.

[EDIT] - k8 defaults to a smilie if they're enabled. Annoying!

---

### Post by blakzer0 on 2005-11-22
Its your NVIDIA driver. Every time you install a new kernel you have reinstall kernel modules for your nvidia card. Check this topic for more info: [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917). Otherwise:

If you can get to the command line try this:
```
sudo apt-get install linux-restricted-modules-2.6.12-10-k7-nvidia-legacy
sudo /etc/init.d/gdm restart
```

If this doesn't work and you just want to get your system up and running try this:

1. First backup your config (Just incase)
```
cd /etc/X11/
sudo cp xorg.conf xorg.conf_backup
```

2. Now, open your xorg.conf file with vi or something similar and find the line
> Section "Device"
	Identifier	"NVIDIA Corporation NV6 [Vanta/Vanta LT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

3. Change nvidia to nv, save, and reboot. :D

---

### Post by christian.convey on 2005-11-22
Thanks. I tried the K7 kernel image, and I get the same problem. It seems to generally stop at the "Checking battery state" step.

---

### Post by christian.convey on 2005-11-22
Thanks, but I'm not quite sure that's right.  I've let Breezy install numerous new kernel images, and I've never had to do the steps you describe.  I think this is the beauty of the way Ubuntu packages the restricted modules: when you install a new kernel image, the package has a dependency on the related versions of the nVidia drivers.

---

### Post by tokyovigilante on 2005-11-22
OK, I'd suggest checking your video card driver as a next step as blakzer0 suggested. Try the nv driver, as it's open source and included with the kernel, and should be up-to-date. 

You might want to make sure your system has pulled in the new version of restricted-modules, and building the nvidia driver from source if the nv driver works.

---

### Post by daller on 2005-11-24
Just to inform you, it also happens on my desktop machine, which has a Matrox G400 gfx...

---

### Post by tokyovigilante on 2005-11-24
Why don't you give the new 2.6.15-4 kernel in the dapper repositories a try? I've just installed 2.6.15-3 and experienced the same symptoms, but only one out of every 2-3 boots. I'd say the culprit is a shared Ubuntu patch that has been applied to both kernels. I'm going to try the -4 kernel when I get home today.

---

### Post by daller on 2005-11-24
[QUOTE=tokyovigilante]Why don't you give the new 2.6.15-4 kernel in the dapper repositories a try? I've just installed 2.6.15-3 and experienced the same symptoms, but only one out of every 2-3 boots. I'd say the culprit is a shared Ubuntu patch that has been applied to both kernels. I'm going to try the -4 kernel when I get home today.[/QUOTE]

Oh sorry, my desktop machine is running Breezy!

---

