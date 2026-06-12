---
title: "Can't boot with kernel 2.6.32-21 or 2.6.32-22 after upgrade to Lucid"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by nasevz on 2010-05-06
After upgrading from Carmic to Lucid, I tried to boot with kernel 2.6.32-21, but system hangs with garbled screen. Also can't boot in recovery mode. With older kernel 2.6.31.21 system is OK.
The same bug is mentioned in [http://ubuntuforums.org/showthread.php?t=1457176](http://ubuntuforums.org/showthread.php?t=1457176), but it is closed for posting I guess because it is forum for beta testing.
I would like to report a bug, but I can't get the information from the machine if I can't boot.

Any ideas?

---

### Post by vckeating on 2010-05-06
I just wanted to add that I have the same problem - 2.6.31-21 works fine (minus an error message), but 2.6.32-21 hangs before getting to the login screen.

---

### Post by rainserpent on 2010-05-06
I am having the same problem with the "32" kernels. I am also getting error messages like: can't find /dev and something chroot with a initramfs file in the "31" kernel. I'll post when I write it down next boot.

---

### Post by Catharsis on 2010-05-06
Do you know what graphics card you have?

The Ubuntu devs started blacklisting KMS for Intel chipsets starting with the -21 kernel, so re-enabling it might fix it if you have an Intel card.

1) Hold down SHIFT as you boot to enter GRUB.
2) Highlight the faulty kernel and hit 'e'.
3) Add "i915.modeset=1" to the end after "quiet splash".
4) Ctrl+x to boot.

---

### Post by rainserpent on 2010-05-06
> **Catharsis said:**
> Do you know what graphics card you have?

The Ubuntu devs started blacklisting KMS for Intel chipsets starting with the -21 kernel, so re-enabling it might fix it if you have an Intel card.

1) Hold down SHIFT as you boot to enter GRUB.
2) Highlight the faulty kernel and hit 'e'.
3) Add "i915.modeset=1" to the end after "quiet splash".
4) Ctrl+x to boot.

This did not work for me. Any other ideas?

---

### Post by Catharsis on 2010-05-06
So do the other kernels still get you to a desktop in Lucid?

Try playing with the Recovery Mode in the GRUB menu (select the kernel that has (recovery) at the end).

You can also continue playing with kernel parameters: "nomodeset", "i915.modeset=0", "xforcevesa", "xforcevesa noapic noapci nosplash irqpoll".

It would also be invaluable to know your Graphics Card. If you can get into a command prompt:
```
lspci | grep VGA
```

---

### Post by Superhuman on 2010-05-07
> **Catharsis said:**
> 
1) Hold down SHIFT as you boot to enter GRUB.
2) Highlight the faulty kernel and hit 'e'.
3) Add "i915.modeset=1" to the end after "quiet splash".
4) Ctrl+x to boot.

This worked 100% for me! Thanks Catharsis!

---

### Post by nasevz on 2010-05-07
I don't think that it is graphics related because in recovery mode system hangs in text mode. BTW my graphics card is Nvidia 8600GT.

---

### Post by agborne on 2010-05-07
Hi,

I have the same problem and i don't think it's the graphic card.

During boot the message is:
"Serious errors were found while checking the disk drive for /media/...

Press I to ignore, S to..."

/media/.. is a second HDD that shall be automatically mounted. There is a problem with the "mountall" command..

After I press I or S nothing happens

---

### Post by kansasnoob on 2010-05-07
> **nasevz said:**
> After upgrading from Carmic to Lucid, I tried to boot with kernel 2.6.32-21, but system hangs with garbled screen. Also can't boot in recovery mode. With older kernel 2.6.31.21 system is OK.
The same bug is mentioned in [http://ubuntuforums.org/showthread.php?t=1457176](http://ubuntuforums.org/showthread.php?t=1457176), but it is closed for posting I guess because it is forum for beta testing.
I would like to report a bug, but I can't get the information from the machine if I can't boot.

Any ideas?

Go ahead and boot into the old Karmic kernel and please post the output of:

```
ls /boot
```

---

### Post by grupotux on 2010-05-07
The `Startup Manager' GUI allows the user to choose a kernel for reboot among those on hand. On the lucid servers, this program is listed as `startupmanager'. Its use avoids the risk of leaving kernel-related files as orphans in the boot directory upon direct removal of an offending kernel. Removing files directly in sensitive directories such as /boot or others where file contents are modified automatically during upgrades is never a good practice.

My experience on a Compaq Presario 2200 has been that all alpha and beta-supplied kernels worked through 2.6.32-20. Both 2.6.32-21 and 2.6.32-22 show a dark screen with backlight on, followed by zero disk activity once dark. As reported elsewhere, the flaw is severe. Not even log files are created.

If you start again based on a Beta 2 image, as I did, the running kernel will be 2.6.32.19. Upgrade to 2.6.32-20 should then be possible by way of Synaptic, apt-get or aptitude. A straightforward reboot will then render 2.6.32-20 as the active kernel. At this point, install `startupmanager' as follows:

sudo aptitude install startupmanager  [ENTER]

Once downloaded and installed, raise the program (System -> Administration -> Startup Manager)and examine the choices. 

The middle bar should read "menuentry ... 2.6.32.20 ...". Pressing the bar should result in the additional display of 2.6.32.19 as a fallback option. 

There's no need to fall back to 19, we're only verifying that all is well. Dismiss the Startup Manager GUI.

From here onward you should be safe in upgrading to new kernels beyond 2.6.32.22, but please read on:

When 2.6.32.23 appears, feel free to download and install it from the repositories. If the fault has been found and corrected by then, all shall be well. But should 23 also prove addled, reboot and hold the `SHIFT' key as soon as the BIOS message appears on screen (or just before). This will cause the boot list to appear moments later. Then, scroll down to 2.6.32.20 (or 19 if you wish, but not to either of the`recovery' kernel lines), then press ENTER. Your machine should now boot normally.

As soon as it does, summon Startup Manager (System -> Administration -> Startup Manager) and choose a working kernel, say 20. This will ensure that your next boot will not again bring forth an addled kernel.

Repeat the above as appropriate until a working kernel is issued. It should not take very long. Remember, this is Linux, not Windows!

¡Buena suerte!

---

### Post by nasevz on 2010-05-08
ls /boot

```
abi-2.6.31-21-generic         memtest86+.bin
abi-2.6.32-21-generic         System.map-2.6.31-21-generic
abi-2.6.32-22-generic         System.map-2.6.32-21-generic
config-2.6.31-21-generic      System.map-2.6.32-22-generic
config-2.6.32-21-generic      vmcoreinfo-2.6.31-21-generic
config-2.6.32-22-generic      vmcoreinfo-2.6.32-21-generic
grub                          vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.31-21-generic
initrd.img-2.6.32-21-generic  vmlinuz-2.6.32-21-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic

```

This is the section from menu.lst which I use for booting. It was originally created from the upgrade and there was kernel 2.6.32.22. I replaced all occurrences of 32-22 with 31-21 to be able to boot.

```
title           Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=66b4a7d9-9237-4d0d-beb
e-478a841ef85f ro quiet splash vga=791 
initrd          /boot/initrd.img-2.6.31-21-generic
quiet
```

---

### Post by andreasj80 on 2010-05-08
> **rainserpent said:**
> I am having the same problem with the "32" kernels. I am also getting error messages like: can't find /dev and something chroot with a initramfs file in the "31" kernel. I'll post when I write it down next boot.

Not sure if this helps anyone, but I've had the same problem when booting after upgrade to 10.04 and selecting kernel 2.6.32.22 from grub. 
After trying some fixes regarding the graphics driver (booting with xforcevesa/i915.modset=1 etc) without any luck I tried to boot with my manually mounted external driver attached to the usb-port. This time it started as normal.

After this I commented out my mounted drive in /etc/fstab, removed it and restarted. Now everything is back on track.

Like I said, perhap this is a none-issue, but it solved things for me.

---

### Post by nasevz on 2010-05-09
I guess you are suggesting that the problem is associated with mounting drives. If I start in repair mode, system stops right after error in mounting or checking drives, but the error was with drives that are not critical to the system and I already tried to comment them in fstab. After commenting them the error is gone, but system still not bootable so I concluded that that error was not the reason for not booting.

---

### Post by reubeni on 2010-05-09
I had the same problem when upgrading live, could not get video for love or money to work tried everything but that kernel would not work, the best I got was a continues flickering screen just about to give up when I found [this]("http://beyondteck.blogspot.com/") followed the instructions and now everything is fine hope this works:guitar:


p.s works for intel cards too.

---

### Post by vckeating on 2010-05-10
> It would also be invaluable to know your Graphics Card. If you can get into a command prompt:
```
lspci | grep VGA
```

Here's the info:

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

And someone else asked for ls /boot:

```

abi-2.6.28-11-generic         System.map-2.6.28-13-generic
abi-2.6.28-13-generic         System.map-2.6.28-14-generic
abi-2.6.28-14-generic         System.map-2.6.28-15-generic
abi-2.6.28-15-generic         System.map-2.6.28-16-generic
abi-2.6.28-16-generic         System.map-2.6.31-21-generic
abi-2.6.31-21-generic         System.map-2.6.32-21-generic
abi-2.6.32-21-generic         System.map-2.6.32-22-generic
abi-2.6.32-22-generic         ubnfilel.txt
config-2.6.28-11-generic      ubninit
config-2.6.28-13-generic      ubnkern
config-2.6.28-14-generic      ubnpathl.txt
config-2.6.28-15-generic      vmcoreinfo-2.6.28-11-generic
config-2.6.28-16-generic      vmcoreinfo-2.6.28-13-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.28-14-generic
config-2.6.32-21-generic      vmcoreinfo-2.6.28-15-generic
config-2.6.32-22-generic      vmcoreinfo-2.6.28-16-generic
grub                          vmcoreinfo-2.6.31-21-generic
initrd.img-2.6.28-11-generic  vmcoreinfo-2.6.32-21-generic
initrd.img-2.6.28-13-generic  vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.28-14-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-15-generic  vmlinuz-2.6.28-13-generic
initrd.img-2.6.28-16-generic  vmlinuz-2.6.28-14-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.28-15-generic
initrd.img-2.6.32-21-generic  vmlinuz-2.6.28-16-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.31-21-generic
memtest86+.bin                vmlinuz-2.6.32-21-generic
newinstall                    vmlinuz-2.6.32-22-generic
System.map-2.6.28-11-generic

```

I should mention that in the boot I get no graphics whatsoever after GRUB.  The hard drive grinds away for a bit, and then just stops.

---

### Post by vckeating on 2010-05-10
In addition, when I attempt to edit the startup kernel selection as was suggested, it never seems to save the new settings - I have to go back and change it each time.  Is this usual?

---

### Post by Catharsis on 2010-05-10
> **vckeating said:**
> ```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

> **vckeating said:**
> In addition, when I attempt to edit the startup kernel selection as was suggested, it never seems to save the new settings - I have to go back and change it each time.  Is this usual?

Yes this is normal. If you find a kernel parameter that works, you can make it permanent by adding it to this line in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and then running
```
sudo update-grub
```

---

### Post by vckeating on 2010-05-11
> **Catharsis said:**
> [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)


Thanks!  Tout va bien!  :)

---

### Post by nasevz on 2010-05-13
I solved the problem. :P
After 2.6.31-21, kernels switched my disk names (sda become sdb). My system drives were listed in fstab by their uuid, so system started, but when it tried to mount other drives by name, error occurred and it couldn't go on. I don't know why it was such fatal error because those drives were for data storage, not critical to the system.

---

