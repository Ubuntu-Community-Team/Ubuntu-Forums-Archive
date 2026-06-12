---
title: "/bin/sh can’t access tty; job control mode off"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by qwak on 2007-09-16
Yep, the title is self explanatory, I'm having trouble installing Ubuntu for the first time. 

**Note that I tried installing it on another machine, it got past the screen where mine broke, so CD works.**

It's displaying this error and another error every 30 seconds. I don't understand why, so I hope someone could help me with this, Ubuntu looks neat.

[I]
Specs:

Intel P4 2.64GHz, codename Northwood
Windows XP build 5.1.2600
Mobo socket 478
Mainboard: i845
BIOS: Award Soft. International inc., version 6.00, date 08/01/02.
[/I]


PS: I have been a Windows user since the day I had my first computer, so if you're gonna get all Linux techy please explain. :)

---

### Post by Pumalite on 2007-09-16
Here is a collection of fixes for your problem:

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.
ust a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

This is as simple as I can get.

The other thing you can do is to try a reinstall with the  Alternate CD.

---

### Post by qwak on 2007-09-17
Um, excuse me but I don't even get past the Ubuntu loading screen, after that it's a MS-DOS style of thing with that error as the thread title.

---

### Post by Shocklance on 2007-09-17
try downloading and installing from the alternative cd, it worked for me, now i just need to get me graphics working...

---

### Post by qwak on 2007-09-17
Yeah, tried that. Same thing... :confused:

---

### Post by dcarpenter on 2007-09-17
I tried following these instructions however I got this error 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 target
ubuntu@ubuntu:~$ sudo chroot target
chroot: cannot run command `/bin/bash': No such file or directory

```

---

### Post by Pumalite on 2007-09-17
> **dcarpenter said:**
> I tried following these instructions however I got this error 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 target
ubuntu@ubuntu:~$ sudo chroot target
chroot: cannot run command `/bin/bash': No such file or directory

```

It means you don't have a system installed.

---

### Post by Pumalite on 2007-09-17
> **qwak said:**
> Um, excuse me but I don't even get past the Ubuntu loading screen, after that it's a MS-DOS style of thing with that error as the thread title.

Try Ctrl+Alt+F1 to see if you can get a command line. The Alternate CD is not a bad idea, but you might get to the same situation, and in that case, that is the combination of keys you'll have to hit.

---

### Post by kebes on 2007-09-17
> /bin/sh can’t access tty; job control mode off

Questions:
-What version of Ubuntu are you trying to install?
-What is the exact manufacturer and model number of your motherboard?

I've seen that error in the past, where the installer can't even load. If you are not using the most recent version of Ubuntu, try the most recent one instead. (The suggestion of the alternate CD is a good one, too.) If you are using the most recent Ubuntu, try using "Ubuntu 6.06 LTS (Dapper Drake)" instead.

This problem can sometimes also be fixed by passing "boot flags" to the kernel before booting. Instead of picking "install" from the initial screen, you press the key for "other options" and pass additional parameters like "noapic" or whatever. The exact parameters depend on the exact motherboard. Check your hardware on this list:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
That wiki describes what special tricks had to be used to get hardware to work.

---

### Post by qwak on 2007-09-17
My motherboard manufacturer is Intel, and the model number is (i think) i845. I tried the latest version off the site.

---

### Post by Pumalite on 2007-09-17
Here you have a collection of boot parameters that you can try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

---

### Post by qwak on 2007-09-17
How do I enter grub? Is it that command prompt where the errors are?

---

### Post by Pumalite on 2007-09-17
Hit F6

---

### Post by qwak on 2007-11-25
Hey, sorry I haven't checked back in a while. so, when i hit f6 at the ubuntu menu it shows a string of text. What now?

---

### Post by Pumalite on 2007-11-25
Read the first link in post #11

---

