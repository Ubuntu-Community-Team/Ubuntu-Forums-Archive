---
title: "[SOLVED] Live cd install problem - (k)ubuntu 7.10 - using usb cd drive"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by rikdeek on 2008-04-04
Hello there,
  I'm trying to get something to boot on a pico itx system which has no cd-drive.

So when booting the live cd (on a usb cd drive) it goes ahead until it gets to the part below:

"Starting K Display Manager: kdm.

* blah - [OK]
* blah - [OK]
* blah - [OK]
* Running local boot scripts (/etc/rc.local) - [OK]"

.. Then the cursor just blinks underneath and nothing happens.

Any ideas?
Is it because the live cd is not expecting to be running on a usb cd-drive? is there a boot command to use to make it work?

I just need a way to boot something that can see/use the hard drive on the system.

Many thanks in advance.

Ubuntu is awesome!

- Rik

---

### Post by dstew on 2008-04-04
Are you sure the CD is intact? Do a CD integrity check (should be a menu item on the opening screen).

---

### Post by Pumalite on 2008-04-04
Can you get a command line with:
Ctrl+Alt+F1
Does it go to Low Graphics Mode after a while?

---

### Post by rikdeek on 2008-04-04
The CD is verified, no errors found, I can get to another terminal - this is what it says:

----------------------------------------------------------
* blah - [OK]
* Starting ACPI Services...
[: 94: ==: unexpected operator
* Starting System Log Daemon - [OK]
* blah - [OK]
* blah - [OK]
* Starting Hardware Abstraction Layer hald
grep: etc/default/locale: no such file or directory
* blah - [OK]
Starting K Display Manager: kdm.
* blah - [OK]
* blah - [OK]
* blah - [OK]
* Running local boot scripts (/etc/rc.local) - [OK]     <--this is where it stops
----------------------------------------------------------

Thanks for your reply,
Any ideas?
Many thanks, again.
- Rik

---

### Post by az on 2008-04-04
> **rikdeek said:**
> Hello there,
  I'm trying to get something to boot on a pico itx system which has no cd-drive.

So when booting the live cd (on a usb cd drive) it goes ahead until it gets to the part below:

"Starting K Display Manager: kdm.

* blah - [OK]
* blah - [OK]
* blah - [OK]
* Running local boot scripts (/etc/rc.local) - [OK]"

.. Then the cursor just blinks underneath and nothing happens.

Any ideas?
Is it because the live cd is not expecting to be running on a usb cd-drive? is there a boot command to use to make it work?

I just need a way to boot something that can see/use the hard drive on the system.

Many thanks in advance.

Ubuntu is awesome!

- Rik

It doesn't sound like it's a media or a boot problem.  Perhaps the video card is not being properly detected?

Can you boot into a safe graphics mode?

If you just need access to your disk from the command line, use the Ubuntu-Rescue-Remix usb image.  It boots from USB drive:

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by dstew on 2008-04-04
Do you get a graphical desktop at all? Usually, after it starts kdm, you should get a desktop. After it stops, do you get a command line? If you hit return, do you get a command line? If you hit ctrl-alt-F2 do you get a command line?

---

### Post by rikdeek on 2008-04-07
It now boots ok in safe graphics mode.
It doesn't give me kde though, terminal 1 (alt+F1) just stays black, when you hit return it gives a command line, other terminals have command lines and are fine.
(I wonder if you can get a gui going from an ubuntu live cd on a pico-itx system - without any configuration!?)

I don't really need a graphical desktop environment, I just need to mount the hard drive on the system to copy an OS onto.

I tried the Ubuntu Rescue Remix. It won't let me use some of the programs, it says I don't have permission even if I run them using sudo.

I am more or less a beginner in the world of linux, but I have quite a good idea of how to get things done, if I don't have to mess around configuring stuff.

using rescue remix I tried:

dmesg | grep -i hd  
it didn't work, wrong permissions for grep. I tried:
sudo dmesg | grep -i hd 
sudo dmesg | sudo grep -i hd  (and other combinations) <-- is this wrong, how do I do it?

I also tried:
ls /dev | grep -i hd

I also tried:
dmesg | vim
(wrong permissions for vim also)

nothing works, I just need to find what the harddrive is, mount it and copy some files on to it.
I can mount a usb pendrive fine using rescue remix, i am having trouble with the harddrive.

This is off topic, I'm sorry. If anyone has the time to help I'd be very grateful!

Thanks again everyone.
- Rik

---

### Post by rikdeek on 2008-04-07
School-boy Error!

I was typing the pipe button - "|" but I guess it had a US keyboard selected and it used ">", I thought nothing of it and thought it was the same thing. I found the correct key for pipe.

Also, embarrassingly, I did not format the hard drive before mounting it.

its formatting now, It should be plain sailing from here on.

Does anyone know if there is a repository for pico-itx stuff?

Thanks everyone

- Rik

---

