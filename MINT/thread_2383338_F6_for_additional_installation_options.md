---
title: "F6 for additional installation options"
date: 2018-01-23
forum: MINT
---

### Post by o770 on 2018-01-23
Hello there!

The F6 key is broken on my old notebook Dell Latitude D500 now with Mint 18 XFCE and Forcepae is unfortunately needed. What could I do?

Edit: This concerns Lubuntu installation menu where the F6 key exposes the command line for user inputs.

---

### Post by howefield on 2018-01-23
Thread moved to the "*MINT*" forum.

---

### Post by #&amp;thj^% on 2018-01-23
Can you access your Grub Menu?
If so press your tab key when grub appears and enter the below without the quotes.
```
"forcepae -- forcepae"
```
You can make that perment if this works for you.
EDIT I should say this should go on 'quiet splash --' at the end. Add 'forcepae' to the string before and after the two dashes ("forcepae -- forcepae").

---

### Post by o770 on 2018-01-23
> **howefield said:**
> Thread moved to the "*MINT*" forum.
Dear Sir
Hi. This question concerns Lubuntu installation as I have originally tagged my message.

> **1fallen said:**
> Can you access your Grub Menu?
If so press your tab key when grub appears and enter the below without the quotes.
```
"forcepae -- forcepae"
```
You can make that perment if this works for you.
EDIT I should say this should go on 'quiet splash --' at the end. Add  'forcepae' to the string before and after the two dashes ("forcepae --  forcepae").

Yeah, I read that before and did it on Mint installation hitting the Tab key. Thanks! However Lubuntu installation menu doesn't actually seem to load Grub... I don't know. Tab, E, both don't work. 
What about the other methods of installation for Lubuntu - anything like these [here]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods")? Could they help me?

---

### Post by QIII on 2018-01-23
Whatever tag may have been present not withstanding, have we missed where your post mentions Lubuntu?

---

### Post by oldfred on 2018-01-23
If booting installer in BIOS boot mode, then you do not have grub but syslinux.
You can edit the syslinux boot files if on flash drive.

Where the quiet splash boot parameters are:
/isolinux/txt.cfg

---

### Post by o770 on 2018-01-23
Ok, I'm gonna try that out. Thanks, oldfred!

> **QIII said:**
> Whatever tag may have been present not  withstanding, have we missed where your post mentions Lubuntu?
No, yes, I haven't mentioned it in my message except for tagging the thread accordingly with Lubuntu prefix, but I have it fixed now.

---

### Post by o770 on 2018-01-23
> **oldfred said:**
> You can edit the syslinux boot files if on flash drive.
Where the quiet splash boot parameters are:
/isolinux/txt.cfg

Yes, it's USB but I can't edit the file because the volume mounts as read-only. I have tried su, sudo, gksudo with xed, and then found [this]("https://askubuntu.com/a/922717"). Is it how Mint's USB Image Writer makes the disk? So is it impossible?

What if I tried mkusb?

---

### Post by oldfred on 2018-01-23
Any of the live creators that use dd or dd under the hood, make a hybrid DVD/flash drive image, that is not a standard formatted nor editable image.
You need an installer that just formats flash drive, extracts ISO, and installs syslinux boot loader. It is possible to do all that manually.
I have not kept track of which installers do that anymore. Most seem to use dd.

---

### Post by o770 on 2018-01-24
Ok, I could find that out and probably do all as you say, oldfred. Thanks for your time! Today I woke up and had the simplest idea of an external USB keyboard! ...So I'm gonna try that first.

---

