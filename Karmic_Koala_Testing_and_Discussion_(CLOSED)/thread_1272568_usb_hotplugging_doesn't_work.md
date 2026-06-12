---
title: "usb hotplugging doesn't work"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jon.reeve on 2009-09-22
My Karmic system won't recognize anything plugged into the USB ports, unless it was there at boot. That means if I unplug my mouse and plug it back in, it won't work, and neither will any flash drives or printers or anything else. Dmesg doesn't return anything, either. 

Any ideas on what might be causing this, and perhaps how to fix it?

---

### Post by scragar on 2009-09-22
Try running```
modprobe -l | grep fuse
```To see if the fuse module is loaded.

EDIT: I doubt this is your problem at all, but until someone with a better understanding of this comes along I'll try what I can :p

---

### Post by jon.reeve on 2009-09-22
```
$ modprobe -l | grep fuse
kernel/fs/fuse/cuse.ko

```

---

### Post by scragar on 2009-09-22
OK, try running ```
lsusb
```See if that picks it up.

---

### Post by waspbr on 2009-09-22
same issue here,  though the usb driver shows on lsusb

---

### Post by jon.reeve on 2009-09-22
First with the mouse plugged in (from boot), then with the mouse unplugged and plugged back in: 

```
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

So lsusb doesn't recognize it, either.

---

### Post by scragar on 2009-09-22
Dude, it completely lost the device? That's way beyond me, sorry.

---

### Post by kansasnoob on 2009-09-22
Not sure this will help with a mouse or keyboard (I just never use USB), but so far both pmount and usbmount seem to be working for me with external drives.

They're both in synaptic. NOTE: only one of the two should be installed at one time!

Note #2: I say "working so far" because I know that hal is being deprecated so expect pmount to stop working at some point, I don't know if usbmount will be effected or not.

Note #3: Reboot is required after installation.

---

### Post by forumache on 2009-09-23
I've just tested and it works here like it used to be: insert USB Stick, detected, mounted, nautilus window open.

Are you the first user on this computer? I mean, you should be in the following groups:

```
dan@shuttle:~$ id
uid=1000(dan) gid=1000(dan) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),105(scanner),107(fuse),109(lpadmin),115(admin),124(vboxusers),1000(dan)
```

Otherwise, you need to add yourself.
P.S. I don't have pmount or usbmount installed.

---

### Post by froggyswamp on 2009-09-23
> **scragar said:**
> Try running```
modprobe -l | grep fuse
```To see if the fuse module is loaded.

Sorry a bit offtopic, did I get it correctly that "modprobe -l" lists all **loaded** modules?

---

### Post by scragar on 2009-09-23
> **froggyswamp said:**
> Sorry a bit offtopic, did I get it correctly that "modprobe -l" lists all **loaded** modules?

You're right, it doesn't list loaded modules, it lists all modules available, I must have gotten it confused with something else(which now eludes me).

---

### Post by froggyswamp on 2009-09-23
Thanks, I actually asked for another reason :) "modprobe -l" revealed a lot of intel and ati video stuff and since I have nvidia one I was worried that all that needless stuff also gets loaded and if so, suggest to the Ubuntu devs to only load what's needed.

---

### Post by scragar on 2009-09-23
> **froggyswamp said:**
> Thanks, I actually asked for another reason :) "modprobe -l" revealed a lot of intel and ati video stuff and since I have nvidia one I was worried that all that needless stuff also gets loaded and if so, suggest to the Ubuntu devs to only load what's needed.

Yeah, I just looked it up, lsmod lists modules loaded. I should have realised that right away.```
[scragar @ sbox working in ~]
$ lsmod
Module                  Size  Used by
pcspkr                  3088  0 
vboxdrv              1723340  0 
nls_cp437               7056  1 
vfat                   13520  1 
fat                    59032  1 vfat
usb_storage            64320  1 
fuse                   70096  2 
radeon                382016  2 
drm                   190080  3 radeon
**##...**

```

If anyone is still having trouble with USB hotplugging it might be worth checking if the modules **usbcore** and **usbhid** are loaded using the above command.

---

### Post by danwood76 on 2009-09-23
Still off topic:
lsmod lists loaded modules.

Back to the OP,

I have a feeling this is to do with the device-kit integration, on my laptop it will work fine one day and then play up. Not really sure what causes it as on my desktop its fine.

---

### Post by ajackson on 2009-09-23
> **jon.reeve said:**
> First with the mouse plugged in (from boot), then with the mouse unplugged and plugged back in: 

```
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

So lsusb doesn't recognize it, either.
Try that again but run lsusb under sudo, my guess is that it will be there that time but the device block (or whatever they are called) in /dev/bus/usb doesn't allow all users read/write access so it is in effect invisible to your user. I get something similar with my Brother all-in-one printer/scanner, only root can access it unless I change the file permissions manually.

---

### Post by victor9098 on 2009-09-27
I am having the same problem, plugging in my USB stick does not do anything, the LED does not even flash on it. Though my 3G Mobile broadband dongle seems to work fine. All was ok under 9.04 so this is only something that has been affecting me since going to Karmic Alpha 6.

I have run lsusb, under sudo as well, but still no sign or flicker from the USB stick.

Any thoughts?

---

