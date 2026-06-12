---
title: "Downgrade back from 10.04 LTS to 8.04 LTS?"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by Seine_Lordschaft on 2010-11-05
Hi,

I upgraded from ubuntu 8.04 to 10.04 LTS using the update manager and the result is that ubuntu boots into a black screen.

Unfortunately I did not test 10.4 before with the Desktop CD, which I tried now, with the same result: black screen. So most likely a hardware screen card issue... which I did really not expect since 8.04 was running very well and the update was coming from the update mananger. Never change a running system.

I assume my only chance is to re-install version 8.04 with the iso CD. But before doing so, is there any must-not to keep an eye on?

Thanks for your advice!

---

### Post by kansasnoob on 2010-11-05
It's quite likely a graphics card issue so please boot any working Ubuntu Live CD (8.04 is fine) and post the output of this command:

```
lspci | grep VGA
```

That will give us specific gpu info. No point in giving up if it's just a graphics issue. 99% of the time these can be fixed fairly easily :)

---

### Post by dino99 on 2010-11-05
downgrading: no way

as its a dist-upgrade, your blackscreen issue is mostly due to your previous xorg.conf
now the kernel directly deals with X, so remove xorg.conf (or rename it if you need special crt config)

sudo rm -f /etc/X11/xorg.conf

then reboot, it should work, then check driver activation (system admin additional driver)

---

### Post by kansasnoob on 2010-11-05
> **dino99 said:**
> downgrading: no way

as its a dist-upgrade, your blackscreen issue is mostly due to your previous xorg.conf
now the kernel directly deals with X, so remove xorg.conf (or rename it if you need special crt config)

sudo rm -f /etc/X11/xorg.conf

then reboot, it should work, then check driver activation (system admin additional driver)

I would NOT do that. It would be best to know what specific graphics chip is being used.

Aside from that an upgrade from Hardy to Lucid should still have legacy grub so if no working Live CD is available, and if Ubuntu is the only OS on the machine, I'd reboot - press the Esc key just after the BIOS/system screen passes to display the boot menu - select the Recovery mode for the newest kernel - then select FailsafeX from the options and see if it works.

I find it much preferable to rename an old file with the "mv" command than to remove it until I've studied more, and why use the "-f" suffix for a single file?

Bad things can happen doing that :(

---

### Post by Seine_Lordschaft on 2010-11-05
thanks very much for these hints.

I booted with 8.04 and the graphics chip is a Intel 82852/855GM Integrated Graphics device.


Booting in recovery mode: that is the first that I tried. And curiously, the first time I could boot in the 2.6 32-25 generic recovery mode.

That was however the last time. After there was only a black screen with a blinking cursor. And for the normal boot process, the Ubuntu logo appears shortly and then follows the black screen.

Afterwoods I selected the 2.624-28 generic recovery mode, which is the second and only remaining boot modus (except a mem test, which seems all right). What happens then is that the message 'initramfs' appears.

Right now I am booting again in the 2.6.32-25 generic recovery mode. And this time - curiously - I arrive at that screen where you can select failsafe.

The protocol of the X-Server says: X.org x server 1.7.6, current version of pixmen 0.16.4. I can choose to edit the configuration file. Can we fix the problem that way?

---

### Post by kansasnoob on 2010-11-05
OK with that chipset you're effected by this:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

That's not uncommon. I'm too tired ATM to make any personal recommendations beyond what it says there but many of the "work-arounds" reference grub2 and since you upgraded from Hardy to Lucid you have legacy grub!

Editing the boot parameters is different in legacy grub but I'm having trouble even keeping my eyes open :(

Can this wait until tomorrow?

Actually since you have an 855GM chip Daniel Vetter's patch may be all you need, I'm just too tired to be useful ATM.

---

### Post by coffeecat on 2010-11-05
> **kansasnoob said:**
> Editing the boot parameters is different in legacy grub but I'm having trouble even keeping my eyes open :(

I sympathise, but having legacy grub surely makes it easier. Just edit menu.lst and no update-grub to run afterward.

@Seine_Lordschaft, if you look at the link kansasnoob posted, one of the fixes/workarounds is to add 'i915.modeset=1' after 'quiet splash' in the kernel line. You should be able to boot up in recovery mode and when you get to the # prompt in the root console, do:

```
nano -w /boot/grub/menu.lst
```... and add the option to the kernel line of the first stanza. Ctrl-O to save and ctrl-X to exit, and then...

```
reboot
```.. and hopefully you should boot into a GUI.

I have to get some shuteye now too, so I'm logging off, but good luck.

---

### Post by Seine_Lordschaft on 2010-11-06
It seems the Glasen bug fix package was all I needed. This boot problem seems solved!

I just booted the first time normally and can now start exploring how the rest is still funcioning after the upgrade... :)

Thanks so much for your help and advice!

---

