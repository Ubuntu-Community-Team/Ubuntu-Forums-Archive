---
title: "Trying to upgrade to 10.04 from 9.10, cannot make it work"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by dissembly on 2010-08-08
Hi all,

In hopes that un-diagnosed problems with my wireless will be solved upgrading to Lucid Lynx, i've been trying to upgrade for quite a few days.

My computer has no ability to connect to the internet (wireless won't detect my network, ethernet causes a "kernel error" for some reason), and no CD drive (it is a 10" mini-laptop).

So, how do i go about upgrading?

On the advice of another forum dweller, i have gotten the iso image for the Lucid Lynx Alternate Install CD and copied all the data onto a flash drive.

However, i cannot figure out how to get the system to treat the flash drive as a CD. He said to boot from the flash drive, but i do not know how to do that.

I assume that i need to press F2 as the computer starts up to choose what to boot from (because there is a screen during boot-up that says "press F2 to access system utlities), but nothing (at all) happens when i do this.

I have tried the USB Startup Disk Creator program that comes with Ubuntu - it does not work. It never gets past the "Format" phase of creating the startup disk (i've tried it with two different brands of USB, a HP and a Sandisk, both 8GB - you click "Format", and nothing happens - no error message, just no response at all).

However, today, my computer was very low on battery (it was into the red). I clicked "Hibernate", but it must not have had enough power to hibernate properly, because when i started it up again just a few minutes ago, it began flashing through a whole sequence of different solid colour screens. It looked like a screen saver, but pressing keys and jiggling the mouse did nothing.

So i held the power button down to shut it off, and then started it up again. This time, it started up with the word "GNU GRUB version 1.97~beta", and has given me four different boot options.

I thought, oh my god, this is the screen i have wanted. But my USB with all the CD data on it was not installed! As soon as i pick an option and boot it, i assume i will be unable to get back to that screen without forcing a shut-down and starting up again (i really do not like doing this to my poor laptop).

So, i don't know what to do. I am completely stuck for ways to upgrade from 9.10 to 10.04. It feels like someone is continually throwing stumbling blocks in my path whenever i try to do anything with this machine. Can anyone help me?

---

### Post by dissembly on 2010-08-08
Oh dear. And now i have another problem: i clicked the option to boot up in recovery mode, because i thought, by analogy with Windows, that maybe this means that if i shut down and start up again, it will start up with the boot options.

So i plugged in my usb drive (so it would be there next time i booted up), and selected the "recovery mode" option, but i did not bank on it being a Terminal command line type interface.

So, i have no idea how to shut it down. I've entered "help" to get the list of command, and there is one called "exit". So i entered "help exit", but it says this "exits the shell". I assume the shell s the OS. So i am afraid that if i type "exit" it will exit the operating system but leave the computer on, or something like that - i wouldnt know how to handle that.

Edited to add:

I entered "sudo shutdown now" after looking around "help" for a bit, but all it has done is taken me back to the recovery menu, it hasn't actually shut the computer down.

:S

---

### Post by ajgreeny on 2010-08-08
From recovery mode, which is already root the command is ```
shutdown -h now
``` no need for sudo, you're already root.

However you could use ```
startx
``` to get a gui and shutdown from there.

---

### Post by dissembly on 2010-08-09
Thank-you - i got out of that confusing situation. Things seem to be good now, appreciate your advice.

---

