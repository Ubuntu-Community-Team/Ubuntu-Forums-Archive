---
title: "GRUB error after partition modification"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by sficciolo on 2011-04-02
Hello everyone,

i apologize if this is not the right section of the forum to write. 
I have a 250GB hard disk, that I partitioned to install Natty Alpha.  The installation went on smoothly, but after having rebooted GRUB was not able to load Natty, though Maverick - that is the system I normally use- was loaded smoothly.  
I think Natty also installed its own version of GRUB (GRUB2?).

After couple of days, very stupidly, I decided to get rid of Natty and so booted from GParted live and erased the partition containing Natty (without formatting it). The joined it with the partition containing Maverick.  This has probably messed everything up, and now:

1. When I start my netbook all I get is 'error: unknown filesystem', and the a 'grub rescue>' command line is shown

2. I 've made a bootable usb disk (both alternate and Live)and tried to boot from it. Didn't work, all I got is 'boot error'. and it doesn't go further.

3. I have tried some command from GRUB rescue shell.
'ls' shows me all the partition in the format: (hd0) (hd0,msdos1)....
However, when I try 'ls (hd0)/' (with and without slash) all i got is 'unknown filesystem'.
Moreover, why does it show (hd0,msdos)? What is that MSDOS?

Sorry, I'm one of those people who always mess up with things because are stupid newbies.  Learnt lots of things this way, though.

Hope someone can help,

sficciolo

---

### Post by Hedgehog1 on 2011-04-02
As a note for next time:  Before removing Natty (or 11.10 or 12.04), always boot the Ubuntu you are keeping and then do:

```
sudo update-grub
``` The sets grub to run from the remaining Ubuntu install, and then you can delete the 11.04/11.10/12.04 partitions.

To rescue your current system, please boot from your 10.10 LiveCD/LiveUSB, select 'TRY'.

Figure out what partition & drive Ubuntu is on (Usning gparted or Disk utility) - and swap that for the **sda5** & **sda** in the following two commands:

```
sudo mount /dev/**sda5** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/**sda**
```

grub will now come up when you reboot.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-02
> **sficciolo said:**
> Sorry, I'm one of those people who always mess up with things because are stupid newbies.  Learnt lots of things this way, though.

The main reason I know answer is because I too have made most every mistake in the book.  It is part of learning; don't worry about it.

We were all newbies once. :D  And with each new Ubuntu release, we all get to be newbies again for a while!


***The Hedge***

:KS

---

### Post by sficciolo on 2011-04-02
Thank you for the answer The Hedge, but my problem is that the system doesn't boot from the USB stick.  All i got is 'boot error' and it doesn't go further.
I have tried with a SuperGrubDisk usb stick, but things haven't changed!

Is it possible that, as I can't do a proper formatting on the USB stick because the pc i'm writing from doesn't let me do so, when I install the live image something goes wrong and it's not bootable?

Ps.
You do learn a lot of things when you make mistakes, but then end up in the Uni lab at saturday night with a usb stick and a very locked WinXp on wich the only software to be allowed to run is Unetbootin ( a miracle).

---

### Post by Hedgehog1 on 2011-04-02
I didn't realize your situation...

If you created the USB using Unetbootin, there is a good chance the USB is OK and the reason you are not booting from it is your boot order on the netbook needs to be changes to try USB first.

When you boot, the BIOS has some text that flashes quickly on the screen.  One of the messages will be how to get to the BIOS (pressing F9, F10, F11, F12 are common, but every manufacturer is a little different)  You want to change your boot order to try USB first.

Then the netbook should boot from the USB.

***The Hedge***

:KS

---

### Post by sficciolo on 2011-04-02
Ok.

For some reason, I can't boot from usb stick.  
I'm a newbie, but I know how to boot from usb :)
Neither the F12 key wich opens the boot menu nor setting usb as first boot option have worked. 

I'm into grub prompt right now, the only human interface I've been able to access so far. Re-setting grub root parametres to the partition containing /boot/grub I managed to bring GRUB prompt from the rescue to the safety mode.  However, the arrows on my keybord don't seem to interact with grub, and I cannot chose to load an OS different from the first one.
Also, when I press enter the system start to boot but then I get this error message:

> error: invalid extent.
error: symbol not found: 'grub_os_area_addr'

Press a key to continue...

When I press, GRUB prompt is loaded again.

This after three hours of work.
Getting crazy.

---

### Post by oldfred on 2011-04-02
IF keyboard is not working in grub, it may be a BIOS setting. Windows & Ubuntu seem to ignore BIOS and work, but grub follows BIOS and you have to turn on USB mouse & keyboard by USB support. Check BIOS.

---

### Post by sficciolo on 2011-04-04
I'm in the BIOS panel, but can't see any voice pointing to keybord settings.
Any suggestion?

---

### Post by oldfred on 2011-04-04
On mine it just refers to USB keyboard, see bottom listting in attached.

---

### Post by sficciolo on 2011-04-04
Keybord was enabled.
Just brought the netbook to the (apparently only in London) pc store doing ubuntu/linux support.
First time that someone else is repairing my pc in 4 years! First time spending money for that!
That's a defeat.

Thanks everyone for your help,

sficciolo

---

