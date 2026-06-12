---
title: "Windows has taken over the MBR"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Alex Carroll on 2008-08-23
Hey, yesterday I tried to Dual Boot Windows with Hardy. Hardy was already installed, and had been for a few months, so I used a separate drive for Windows. In an attempt to preserve Ubuntu's GRUB loader, I unplugged both the Ubuntu drive and my 500GB tertiary hard drive, leaving a single 40GB hard drive readable by the Computer. Windows installed fine, my games ran, and I assumed all was well.

However, when I reconnected my other 40GB drive and my tertiary drive, I found that Windows booted as normal, with no GRUB in sight.

So my question is, how can I restore GRUB's rightful place as my bootloader? I understand I can use the Ubuntu Live CD to do it, but am unsure if this will result in me losing either my Ubuntu installation or my Windows installation.

Thanks in advance.
[U]
Some possibly relevant info:[/U]
The two 40GB hard drives are the same model, connected via IDE using a single cable with two IDE connectors.
The 500GB drive is a SATA one, used for all my data storage.

---

### Post by sandysandy on 2008-08-23
u can definitely do that.

see this thread

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or use super grub disk.

---

### Post by Alex Carroll on 2008-08-23
Another question: Will Windows be on the GRUB boot menu when I restore it or will I have to add it manually?

Super Grub Disk looks like a good option at the moment, so I'll probably try that.

---

### Post by Alex Carroll on 2008-08-23
Well, a lot has happened.

First, I was getting error 17: Cannot boot from partition. I manually edited the menu.lst file to boot the right drive and right partition, but now I am presented with:

```
*Checking file systems...
1244
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=398bcef7-834c-40b3-868d-22394dda40c5'
fsck died with exit status 8

* File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writeable.
Please repair the system manually.
* A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
```

Help!

EDIT: Ctrl+D lets me continue to boot successfully, but this message shows at each boot. I'd really appreaciate it if someone could shine a bit of light on what has gone wrong :)

---

### Post by Alex Carroll on 2008-08-24
Well I solved it :D

Turns out that I had left a couple of lines in the /etc/fstab file that said the drive with UUID 398bcef7-834c-40b3-868d-22394dda40c5 was ext3, back before I reformatted it for Windows. I removed this line and now reboots are clean.

---

