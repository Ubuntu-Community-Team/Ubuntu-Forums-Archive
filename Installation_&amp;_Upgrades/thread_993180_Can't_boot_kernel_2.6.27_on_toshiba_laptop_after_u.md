---
title: "Can't boot kernel 2.6.27 on toshiba laptop after upgrade to Intrepid"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2008-11-25
I've upgraded my three machines to Ubuntu 8.10 Intrepid.  The two desktop machines are fine.

But, my Toshiba laptop cannot boot kernel 2.6.27.  It does boot kernel 2.6.24 and everything seems to be fine when running under that kernel.

Is this a known problem?  Or, is a configuration error on my machine?

Should I be reporting it?  Where?  And, what information should I provide?  The results from dmesg?

- Dave

---

### Post by buckrodgers on 2008-11-25
Hi, 

I have a similar issue on a desktop PC (MB ASUS M3N78)

When trying to boot after the update to 8.10 I get a kernel pannic : VFS Unable to mount root fs on unknown-block(0,0)

It seems that the upgrade has made a total mess in the ETC config files since when i try to boot with kernel 2.6.26, I have no KB (usb), no mouse (usb), graphic card is not recognised

Not the smosest upgrade I've seen :(

---

### Post by buckrodgers on 2008-11-25
I' ve booted with 2.6.26 in rescue mode and ran dpkg

It seems to have fixed at least part of the problem :), now it goes up to the logon screen but when u log on it seems stuck on a brown screen mouse mooving, disks working hard, it's been 10 min like that...  I'l wait a bit in case it is trying to update something.

Cheers

---

### Post by dkuhlman on 2008-11-25
> **buckrodgers said:**
> Hi, 

I have a similar issue on a desktop PC (MB ASUS M3N78)

When trying to boot after the update to 8.10 I get a kernel pannic : VFS Unable to mount root fs on unknown-block(0,0)


I had a similar symptom.  But, I got past that one (I believe) by adding the following line: 

```
    initrd          /boot/initrd.img-2.6.27-7-generic

```

to both of the 2.6.27 stanzas, so that it looks like the following:

```

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=4923aaab-b667-4a1e-b9a8-106a438874d8 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, kernel 2.6.24-21-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=4923aaab-b667-4a1e-b9a8-106a438874d8 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

```

That got rid of the kernel panic, but later during the boot-up process, it freezes.

The system seems mostly OK.  When it stalls there, I can switch to a tty screen/prompt and can log on and do stuff.

- Dave

---

### Post by buckrodgers on 2008-11-30
I think i understand now

it probably crashed during the install (I was not present) & when i tryed to reboot it was on a half finished upgrade 
it finnaly worked fine using :
 
```
dpkg --configure -a
apt-get -f update
apt-get -f upgrade
```

---

### Post by thecarpy on 2008-12-24
I had this very problem, mkinitramfs is your friend here!

my /boot/grub/menu.lst did not contain an initrd line, that has to be there, but before you need to create the file.

I had no initrd.img for the kernel that was not working.

```
sudo mkinitramfs -o /boot/initrd.img-2.6.XX-YY-generic 2.6.XX-YY-generic
sudo update-grub
sudo reboot && echo "Good luck!"
```

---

### Post by dkuhlman on 2009-02-16
I believe that I've solved my problem.  Basically, what I did was disable enhanced visual effects, deactivate the fglrx drivers, then booted kernel 2.6.27 (which now boots), then re-activated fglrx (which downloaded new drivers, I believe), then re-activated enhanced visual effects.

And, here are details:

1. I booted with kernel 2.6.24.

2. Under Gnome, I used menu System-->Preferences-->Appearance-->Visual Effects to disable enhanced video effects (Compiz.

3. I used System-->Administration-->Hardware Drivers to deactivate fglrx.

4. Shut down and booted with kernel 2.6.27.  Yes! Now, I can.

5. I used System-->Administration-->Hardware Drivers to re-activate fglrx, which I believe, forced down-load of new drivers.

6. Used menu System-->Preferences-->Appearance-->Visual Effects to re-enable enhanced video effects.

7. Shut down and booted with kernel 2.6.27, just to make sure that I still can.

Hope this might help someone.

- Dave

---

