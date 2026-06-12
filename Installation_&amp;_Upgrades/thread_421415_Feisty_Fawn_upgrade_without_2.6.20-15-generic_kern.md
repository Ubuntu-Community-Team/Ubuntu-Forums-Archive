---
title: "Feisty Fawn upgrade: without 2.6.20-15-generic kernel"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Bernhard001 on 2007-04-24
I have Ubuntu 6.10 installed and updated. Two Grub-Entries: 2.6.17-10-generic and 2.6.17-11-generic kernel.

1. The actual Feisty Fawn Live-CD stopped immediately the starting procedure. Changing the options in the text menu leads to nothing.

2. Upgrading by synaptic. First of all i had to remove clam.. stuff. After the successful installation process the restart stopped:
 - Running the the 2.6.20-15-generic kernel: Only the words "Starting up..." are visible on the "freezen" screen.
[LIST]
[*]Running the 2.6.17-11-generic kernel: The ubuntu start-screen freezes immediately. 
[*]Running the 2.6.17-11-generic kernel a second time: Before starting Ubuntu the second time  i started ubuntu by running the 2.6.17-10-generic kernel without problems surprisingly. The terminal command "sudo update-initramfs -k 2.6.17-11-generic -u" brought a small success. After this was done i could start Ubuntu by running the 2.6.17-11-generic kernel[/LIST].

And now the strange result: I have installed Ubuntu 7.04, but only the start procedure with the both older kernels works. I can only run Ubuntu 7.04 with the older kernels!!!! 

What ist the problem with the 2.6.20-15-generic kernel?

My old PC:
[LIST]
[*]512 MB RAM (SDRAM 133 MHz)
[*]Intel Celeron processor 1200 MHz
[*]Intel Chipset i815(or 815?)
[*]Matrox millennium 450AGP Dualhead (perhaps the real name ist a little bit different to the name before)
[/LIST]

Other stuff: Real Networks 10/100 Ethernet adapter (standard), SCM SPR532 Card Reader (usb), Samsung scf-4216f (parallel port, switched off during the installing and checking process).

What puzzles the 2.6.20-15-generic kernel. BIOS Setup? The matrox dualhead graphic card? What else?

Older Knoppix Live-CDs run, but the new Knoppix 5.11 Live-CD doesn't.

---

### Post by Big Ed on 2007-04-24
Try closing Synaptic (and any other package manager), opening a terminal and using this command:

sudo apt-get dist-upgrade

I _should_ get you the new kernel (and any other held-back packages).  You'll have to reboot after it's done.

HTH,
Ed

---

### Post by Bernhard001 on 2007-04-24
Hi Ed,

"sudo apt-get dist-upgrade" is nice, but the 2.6.20-15-generic kernel is already installed. Therefore: Nothing to update (upgrade).

But i read other posting in this forum. Perhaps i forgot one important point: I use two harddisks. The first has the grub-bootloader in the boot sector and the second contains Ubuntu. This fact could be forgotten by writing the install scripts - but only perhaps (There are three other partitions on the second harddisk: hdb2, hd3 and hd7.)?

Do you know the configuration-files, which are responsible that the boot process recognize the ubuntu partition on the second harddisk? 

:confused: Remember Ubuntu 7.04 runs fine with an older kernel. :confused: 

Best regards

Bernhard

---

### Post by snakecharmer on 2007-04-24
Hi 

after upgrade to feisty i still using the old kernel 2.6.17.10 because with the new kernel 2.6.20 the boot time it's incredibly slow (i wait 3 min. only to starting ACPI daemon) and when the gnome has started, the system look like a picture, but i cant use anything, my mouse is incredibly slow and i cant execute any application.

---

### Post by kthardin on 2007-04-24
Yeah, I have the same problem.  I upgraded to Feisty Fawn, but the newer kernel does not work.  I get to the part where the login screen typically pops up, and it hangs.

Here's the odd thing.  I start in recovery mode for the new kernel and type in startx which starts the X windows session, and it runs fine.  Sure, I'm running as root, but it's running fine.  Obviously this is not exactly what you'd call a fix.

Now, when I drop down to 2.6.17-10-generic kernel, everything runs fine.  Trying to load the 2.6.17-11-generic, which I was able to do using Edgy, exhibits the same behavior as I'm currently experiencing with 2.6.20-15-generic.

I'm rather new to ubuntu and linux in general, so I'm not certain where or even HOW to proceed from here.

---

### Post by Big Ed on 2007-04-24
> **snakecharmer said:**
> Hi 

after upgrade to feisty i still using the old kernel 2.6.17.10 because with the new kernel 2.6.20 the boot time it's incredibly slow (i wait 3 min. only to starting ACPI daemon) and when the gnome has started, the system look like a picture, but i cant use anything, my mouse is incredibly slow and i cant execute any application.

OK, you've  different problem than I had.  My server had 35 packages held back, including the kernel.  So I was on the old one until I sorted it out.  Do you have packages held back?

I still suggest "sudo apt-get dist-upgrade" and "sudo apt-get upgrade" to see if that loads more updates and fixes your system.  Check for messages after you run each command.

Ed

---

### Post by Bernhard001 on 2007-04-25
> **kthardin said:**
> 
Now, when I drop down to 2.6.17-10-generic kernel, everything runs fine.  Trying to load the 2.6.17-11-generic, which I was able to do using Edgy, exhibits the same behavior as I'm currently experiencing with 2.6.20-15-generic.

 
_@kthardin: _ start the 2.6.17-10-generic kernel and try ```
sudo update-initramfs -k 2.6.17-11-generic -u
```

Good luck!

What's about the bug i reported here before?

Bernhard

---

### Post by xoom on 2007-04-25
I believe I have a similar issue the received no replies yesterday.

[http://ubuntuforums.org/showthread.php?t=421478](http://ubuntuforums.org/showthread.php?t=421478)

---

### Post by kthardin on 2007-04-25
> **Bernhard001 said:**
> _@kthardin: _ start the 2.6.17-10-generic kernel and try ```
sudo update-initramfs -k 2.6.17-11-generic -u
```

Good luck! 

That was one of the first things I tried, having read the troubles and the solution for the 2.6.17-11-generic kernel at the beginning of this thread.  Unfortunately, this did nothing for me.

---

### Post by Bernhard001 on 2007-04-26
> **kthardin said:**
> That was one of the first things I tried, having read the troubles and the solution for the 2.6.17-11-generic kernel at the beginning of this thread.  Unfortunately, this did nothing for me.

Try this:

```
sudo mkinitramfs -o /boot/initrd.img-2.6.17-11-generic

sudo update-grub
```

or / and this 

```
sudo aptitude reinstall linux-restricted-modules-2.6.17-11-generic
```

Eventually it could be neccessary to repeat
```
sudo update-initramfs -k 2.6.17-11-generic -u
``` or the commands above.

@kthardin: Perhaps the commands work with the  2.6.20-15-generic kernel in your case (Please, replace the kernel-numbers in the commands) . Please drop some lines here. 

Remark: If you try this, perhaps the 20-15 kernel won't run, but the 17-11 runs (perhaps). Mixing the commands with both kernels? It's simpy trial and error. And Don't forget the restarts of ubuntu after each step or after each correction of some installed package stuff because of error messages.

*Good luck again, kthardin.*

I tried the commands with the 2.6.20-15-generic kernel without success. I repeat: The new-Live-CD doesn't work. There is something wrong.

Best regards

Bernhard

---

### Post by mardawi on 2007-04-26
Hi,

I'm having a similar problem.

before upgrading to feisty i used to boot with Kernel 2.6.17-11-386

now i have 2 new kernel versions available; 15-386 and 15-generic

when booting with 15-386 or 11-386 version i get

```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)
```

and when boot with the 15-generic or 11-generic i get a "File system check failed" error and when i continue GNOME restarts after i login (even in fail-safe mode), but fluxbox works. :confused: 

Can someone please help? :(

---

### Post by kthardin on 2007-04-27
> **Bernhard001 said:**
> Try this:

```
sudo mkinitramfs -o /boot/initrd.img-2.6.17-11-generic

sudo update-grub
```

or / and this 

```
sudo aptitude reinstall linux-restricted-modules-2.6.17-11-generic
```

Eventually it could be neccessary to repeat
```
sudo update-initramfs -k 2.6.17-11-generic -u
``` or the commands above.

@kthardin: Perhaps the commands work with the  2.6.20-15-generic kernel in your case (Please, replace the kernel-numbers in the commands) . Please drop some lines here. 

Remark: If you try this, perhaps the 20-15 kernel won't run, but the 17-11 runs (perhaps). Mixing the commands with both kernels? It's simpy trial and error. And Don't forget the restarts of ubuntu after each step or after each correction of some installed package stuff because of error messages.

*Good luck again, kthardin.*

I tried the commands with the 2.6.20-15-generic kernel without success. I repeat: The new-Live-CD doesn't work. There is something wrong.

Best regards

Bernhard

Well, for the 17-11 kernel, no love there.  Tried all commands and rebooted after each one.  Actually after this command:

```
sudo aptitude reinstall linux-restricted-modules-2.6.17-11-generic
```

There was a message stating it couldn't find the package.  Any repositories I need to add?

I'll try it with the 20-15 kernel in a bit.

---

### Post by Saubazi on 2007-04-27
> **snakecharmer said:**
> Hi 

after upgrade to feisty i still using the old kernel 2.6.17.10 because with the new kernel 2.6.20 the boot time it's incredibly slow (i wait 3 min. only to starting ACPI daemon) and when the gnome has started, the system look like a picture, but i cant use anything, my mouse is incredibly slow and i cant execute any application.

I would also like to use 2.6.17.10 because 2.6.20 seems to cause problems here and there. However, I have the boot option but when I boot I get bollocking from wrong NVIDIA modules vs. the ones required by xorg. Now when I still had 2.6.17.10 I was using the older nvidia from edgy repo, but now with 2.6.20 there is a newer one. Can I do something to solve the dilemma?

---

### Post by Bernhard001 on 2007-04-27
> **kthardin said:**
> Well, for the 17-11 kernel, no love there.  Tried all commands and rebooted after each one.  Actually after this command:

```
sudo aptitude reinstall linux-restricted-modules-2.6.17-11-generic
```

There was a message stating it couldn't find the package.  Any repositories I need to add?


...could be.

---

### Post by Bernhard001 on 2007-04-27
> **Saubazi said:**
> I would also like to use 2.6.17.10 because 2.6.20 seems to cause problems here and there. However, I have the boot option but when I boot I get bollocking from wrong NVIDIA modules vs. the ones required by xorg. Now when I still had 2.6.17.10 I was using the older nvidia from edgy repo, but now with 2.6.20 there is a newer one. Can I do something to solve the dilemma?

You can run 2.6.20-15, but we can't run 2.6.20-15. That's a big difference. I don't know whether your problem is identical... or not.

---

