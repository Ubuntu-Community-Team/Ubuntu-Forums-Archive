---
title: "Error removing initramfs tools (fresh install)"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by iaindcunningham on 2014-01-08
[FONT=arial](Also posted to: [http://askubuntu.com/questions/401391/error-removing-initramfs-tools-fresh-install](http://askubuntu.com/questions/401391/error-removing-initramfs-tools-fresh-install) )

[COLOR=#333333]I have seen a few other people with this issue, but they have an existing install that they can drop into to fix it. I don't!
[/COLOR]
[COLOR=#333333]So, I am trying to install Xubuntu 13.10 using a live USB, and in doing so I have intentionally formatted the installation partitions (all my data is safely floating in the sky). Everything seems to work until right at the very end I get the message:
[/COLOR]
```
Error removing initramfs-tools:
subprocess installed post-installation script returned error exit status 1
```

[COLOR=#333333]The only thing I can think of is that some partition somewhere isn't big enough... I have:
[/COLOR]
```
sda1 /swap   512MB
sda2 /boot   56MB
sda3 /home   32GB
sda5 /var    4GB
sda6 /opt    4GB
sda7 /       31GB
```

[COLOR=#333333]Any advice at all would be welcome as at the moment I have a totally unbootable system following the attempted install. Booting to GUI hangs at the splash screen. Trying Ctrl + Alt + F1 from there does NOT give a login prompt. Booting into recovery and dropping to root shell leaves me with no partitions other than sda7 and sda5 mounted, all the other partitions refuse to mount![/COLOR]
[COLOR=#333333]If I attempt to mount, for example sda2 then:
[/COLOR]
```
# mount -t ext4 /dev/sda2 /boot
mount: /dev/sda2 already mounted or /opt busy
```


[/FONT]

---

### Post by grahammechanical on 2014-01-08
Have you ever examined the Grub boot parameters by selecting a boot option and pressing E? That puts Grub into Edit mode. It also shows us the boot parameters. Pressing Esc will take us back to the Grub menu. Pressing F10 will boot what we are looking at. So, what is the difference between the boot parameters of Ubuntu/Xubuntu and Recovery mode?

Normal boot has this:

> ro quiet splash $vt_handoff

Recovery mode replaces that part of the boot parameter line with:

> ro recovery nomodeset

I am guessing that the recovery menu is sitting at the stage of the boot process where Linux has been loaded. For Linux to load, in your case, then the boot partition (sda2) would have to be mounted. That is why when you try to mount it you get the message saying it is already mounted. Likewise, the root partition (sda5) would also have to be mounted but in read only mode.

You do not say what error message you get when you try to mount the /home (sda3) partition. We can put the file system in read/write mode by running the recovery menu network option. Then when we select recovery>root we get to a root shell prompt with the ability to edit and save configuration files.

The script that runs when we select Recovery>Root is just a small script that runs sulogin in the sbin directory/folder. It could not do that if Linux was not loaded and the root partition not mounted.

Can I tell you what I think? And I am most likely completely wrong about this. I think you have not a problem with the partition sizes but a problem that many post about on this forum. Installing, rebooting and failing to load to a desktop. Have you tried Recovery>Resume? Have you tried installing without ticking Install Third Party Software? If we install third party software we also get a proprietary video driver. And it may that proprietary video driver that is causing the problem.

I also wonder if the installation error was a failure to write the post installation log to /var because it was only in read mode and not read/write mode.

Regards.

---

### Post by iaindcunningham on 2014-01-09
> **grahammechanical said:**
> For Linux to load, in your case, then the boot partition (sda2) would have to be mounted. That is why when you try to mount it you get the message saying it is already mounted. 

Yes, but unfortunately it's really **not **mounted, or at least ```
mount -l
``` and ```
df
``` don't show it as being mounted...

> **grahammechanical said:**
> You do not say what error message you get when you try to mount the /home (sda3) partition.

The example I gave is consistent for all the unmounted drives, "already mounted or busy".

> **grahammechanical said:**
> Have you tried Recovery>Resume?

Yes (just now), I get the message ```
Warning: Fake initctl called, doing nothing.
``` immediately and nothing else happens.

> **grahammechanical said:**
> Have you tried installing without ticking Install Third Party Software?

Not yet - I will try this - thank you!

---

### Post by iaindcunningham on 2014-01-09
> **iaindcunningham said:**
> [QUOTE=grahammechanical;12895170]Have you tried installing without ticking Install Third Party Software? If we install third party software we also get a proprietary video driver. And it may that proprietary video driver that is causing the problem.

Not yet - I will try this - thank you![/QUOTE]

I have now tried this too - no joy.

---

### Post by iaindcunningham on 2014-01-12
I'm going to try installing with the LTS ISO and see if that leads to a different result...  Please shout if you can think of a better idea!

---

### Post by iaindcunningham on 2014-01-13
In the end I 'solved' this by installing 12.04.3 LTS  instead of 13.10.  As part of this I also 'rejigged' my partitioning  schema:
  ```
sda1 /swap  swap 4GB
sda2 /boot  ext4 128MB
sda3 /var   ext4 8GB
sda5 /opt   ext4 4GB
sda6 /      ext4 16GB
sda7             16GB
sda8 /home  ext4 200GB
```
  sda7 is unformatted free space for test installations and is where I will eventually try installing 13.10.

  In any case, 12.04.3 LTS is installed and running quite happily.

---

