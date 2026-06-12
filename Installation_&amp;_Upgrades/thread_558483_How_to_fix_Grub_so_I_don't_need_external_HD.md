---
title: "How to fix Grub so I don't need external HD?"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by bogoliubov on 2007-09-24
I have a laptop with Ubuntu (Feisty) on the internal HD. Now I installed a test-version of Gutsy onto an external USB HD. My motherboard have no problems booting from USB HD. 

But the installation of Gutsy changed Grub on the internal HD so that I need to have the USB drive connected in order to boot the OS from the internal HD. Obviously this is not very convenient. 

So how can I change Grub so that when the external drive is connected, I can boot this, and when it's not connected I can boot from the internal drive?

---

### Post by celettu on 2007-09-24
Boot in Feisty, fire up a terminal, do a grub-install :) Make sure your external HD is connected, so grub can find the OS there.

---

### Post by bogoliubov on 2007-09-24
> **celettu said:**
> Boot in Feisty, fire up a terminal, do a grub-install :) Make sure your external HD is connected, so grub can find the OS there.

Oh, sounds easy! Just 'sudo grub-install' ?? I'll have a go at it as soon as I can. Thanks

---

### Post by celettu on 2007-09-24
sudo grub-install should do it, yeah. When you installed Buntu on the external HD it told your grub the root was to be found on that HD. Doing a grub-install on your Feisty installation should change that back.

Small hint: if you install a second OS to test it, never allow it to overwrite the MBR. Just make it install the bootloader in the root partition, and edit your menu.lst on your original OS.

---

### Post by dabl on 2007-09-24
"Last Linux Wins!"

Remember that rule -- if Grub is allowed to overwrite the MBR, then each time a Linux OS is installed, it will set itself to be the default-booted OS, first on the menu list.

celettu is exactly right -- if you use the "Alternate Install" CD for a subsequent (K)Ubuntu installation, you can direct Grub to be installed in the "/" filesystem of the new OS, where it will not disturb your original boot menu.  Then you'll have to manually edit the /boot/grub/menu.lst file in your primary Linux, to tell it where to find the boot kernel for the later one.  :guitar:

---

### Post by bogoliubov on 2007-09-24
Ok, but what flags should I give to grub-install ?

And I checked the /boot/grub/menu.lst file (on the internal HD), and it doesn't contain anything about the external HD as far as I can see! Hmm, is there a command that one should run to transfer the menu.lst settings to the MBR?

---

### Post by celettu on 2007-09-24
You'll want to install it on your MBR, so most of the time you'll have to type this:

```
sudo grub-install /dev/hda
```

It'll take care of the menu.lst for you.

If it doesn't, mount the external drive, check the menu.lst on that one, and copy/paste the appropriate lines.

---

### Post by jnorthr on 2007-09-24
Just a question on this -

for some simple testing, i would like to install gutsy server on this same harddrive on the same machine that i am running feisty desktop. If i used gparted to carve out two further partitions of about 2Gb each and use the same swap file as the desktop to run the server, will this work ?

I already have a /home and /usr/local partitions for the desktop, but It seems to me that when the gutsy server is running, how will it know to use it's own '/home' rather than my desktop '/home' partition ? Does that mean i need to place some of the server partitions on a different drive ?

---

### Post by bogoliubov on 2007-09-24
> **celettu said:**
> You'll want to install it on your MBR, so most of the time you'll have to type this:

```
sudo grub-install /dev/hda
```

It'll take care of the menu.lst for you.

If it doesn't, mount the external drive, check the menu.lst on that one, and copy/paste the appropriate lines.

Worked perfectly! Thanks

---

### Post by celettu on 2007-09-24
> **jnorthr said:**
> Just a question on this -

for some simple testing, i would like to install gutsy server on this same harddrive on the same machine that i am running feisty desktop. If i used gparted to carve out two further partitions of about 2Gb each and use the same swap file as the desktop to run the server, will this work ?

Yes. I do it all the time.

> I already have a /home and /usr/local partitions for the desktop, but It seems to me that when the gutsy server is running, how will it know to use it's own '/home' rather than my desktop '/home' partition ? Does that mean i need to place some of the server partitions on a different drive ?

Not sure what you mean, but during the installation, simply don't don't give any mount points for the feisty partitions. That way they won't appear in your fstab.

---

### Post by bogoliubov on 2007-09-25
Hmm, I just realized something though. Now I can't boot the USB HD! Not sure why. If I connect it and start the computer it just "sits there". No Grub it seems, so how can I install Grub on this external HD?

---

### Post by bogoliubov on 2007-09-25
Perhaps I should also mention that the partition with Ubuntu on the external HD is not the first one. Not sure if this matters...

---

### Post by bogoliubov on 2007-09-25
bump...?

---

### Post by celettu on 2007-09-25
"sits there"? You mean there's no entry for it in grub?

If that's the case, boot feisty, mount the Buntu on your external HD, check the /boot/grub/menu.lst on that one, find the first entry, copy it in its entirety to the menu.lst on your feisty, reboot.

---

