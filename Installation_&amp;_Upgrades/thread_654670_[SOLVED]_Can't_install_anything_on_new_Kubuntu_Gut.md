---
title: "[SOLVED] Can't install anything on new Kubuntu Gutsy install"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by nirpius on 2007-12-31
Argh!

I have been having a recurring problem for about 2 weeks. Once I install Kubuntu Gutsy, everything works fine but after I have run any installation program, I can't run any more. This happens no matter which program I run. I have tried Gdebi package whatever it is, adept Manager, the adept add or remove thing and the adept upgrade thing. Also, trying to do it in the command line.

I have restarted the laptop numerous times but it won't let me run any of the above programs, I always get the following message:

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.

And no matter what I do from here, I can't get anything to run. I have reinstalled Kubuntu a few times with different discs (all checked for consistency and apparently fine) and on two different laptops - I always get the same problem.

Does anyone know how to fix/avoid this?

Many thanks

---

### Post by raffytaffy on 2007-12-31
When it tells you another process is using it, try this in terminal
sudo killall kio_file

then re-try to run your package management

---

### Post by nirpius on 2007-12-31
Thanks raffytaffy for the quick reply.

Tried that but it didn't work, still got the same message.

---

### Post by doug1212 on 2007-12-31
Try,
```
sudo dpkg --configure -a
```
usually does the trick.
Doug.

---

### Post by nirpius on 2007-12-31
Will try in a sec. I just had to restart and now my laptop has got stuck. It's given me this message:

[	19.517002] VFS: Cannot open root device "UUID=36e8826b-5b99-407a-92a0-3d9c70b49348" or unknown-block(0,0)
[	19.517076] Please append a correct "root=" boot option; here are the available partitions:
[	19.517146] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

but obviously, that's off topic so I'll post it elsewhere - just keeping you in the loop.

Thanks again btw

---

### Post by raffytaffy on 2007-12-31
> **nirpius said:**
> Will try in a sec. I just had to restart and now my laptop has got stuck. It's given me this message:

[	19.517002] VFS: Cannot open root device "UUID=36e8826b-5b99-407a-92a0-3d9c70b49348" or unknown-block(0,0)
[	19.517076] Please append a correct "root=" boot option; here are the available partitions:
[	19.517146] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

but obviously, that's off topic so I'll post it elsewhere - just keeping you in the loop.

Thanks again btw
Its not finding your root partition via UUID, you could try to run live cd...
step 1 make a temp mount
sudo mkdir /temp/mnt
step 2 mount your root partition ( i will use /dev/hda1 for example, use your own )
sudo mount /dev/hda1 /temp/mnt
step 3 edit your menu.lst ( grub )
sudo gedit /temp/mnt/boot/grub/menu.lst
step 4 change the UUID like this
root=UUID blah blah to root=/dev/hda1
save and reboot. should work.

If it does not, you can put in UUID back the same way

---

### Post by nirpius on 2007-12-31
> **raffytaffy said:**
> 
step 1 make a temp mount
sudo mkdir /temp/mnt

It said mkdir: cannot create directory '/temp/mnt': No such file or directory

I tried to simply mount my root partition using

```

sudo mount /dev/sda1
```

and I got told

```

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
```

---

### Post by nirpius on 2007-12-31
It's working now. I typed mkdir /tmp/mnt instead of /temp/mnt but now I've got to step 3 and it says

Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/kde-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/ksocket-ubuntu" is owned by uid 999 instead of uid 0.

It opened up Kate though, so I'll press ahead with step 4

---

### Post by raffytaffy on 2007-12-31
Yeah reason I told you to try this, is because when i compiled custom kernels, they would panic on UUID also, so I had to use root=/dev/hda. Hope it works for you.

---

### Post by nirpius on 2007-12-31
> **doug1212 said:**
> Try,
```
sudo dpkg --configure -a
```
usually does the trick.
Doug.
Got my laptop rebooting now and tried Doug's trick and everything is working fine.

---

