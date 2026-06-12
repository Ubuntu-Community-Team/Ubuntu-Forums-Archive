---
title: "Cannot boot into new install of ubuntu 13.04 dev/disk/by-uuid/... does not exist"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by dima6 on 2014-03-21
I did a fresh install, made with unetbootin on windows 7, USB 2.0 key (32GB) of Ubuntu 13.04 (64bit) install image, on to another USB 2.0 key (16GB).
In fact I did several installs, using default partition allocation and custom (selecting "something else" and allocating root and swap) but in all cases result is the same:
After prompt to reboot screen with flashing cursor comes up and then after a delay message (see attached screenshot) with the most important problem information in it being:

ALERT! /dev/disk/by-uuid/[COLOR=#000000]353f3494-0d06-4e7f-9e84-668893d2d1a0 does not exist,
[/COLOR]Dropping to a shell!

I have attempted the boot-repair tool as per official tutorial using my installation USB key ("Try Ubuntu without installing"), it ran through successfully and produced following url:
[http://paste.ubuntu.com/7128800/](http://paste.ubuntu.com/7128800/)

however it did not resolve the issue.
Looking at the output and looking at the grub script (accessed at boot) I can see that uuid being referenced is a correct one.
However I  do not have enough linux experience to even know if I am looking in the right places.

I have Gigabyte GA-990FXA-UD3 AM3+ MB with 8GB RAM, AMD FX-4300 CPU, Sapphire R9 280X video

As a background I installed Xubuntu 12.10 couple of month ago and it was working, then had to upgrade motherboard (to the one I have now) and the same problem happened. I do not remember what I did but somehow following one of the forums suggestions I fixed it. However so far 2 days of fighting on this issue did not result in the similar outcome :).
The important part though is I do have a working 12.10 USB key xubuntu that works fine on this machine, so if there is something that can be taken/referenced from it to assist in solving this problem - I can get it.

Appreciate any help or suggestions...

---

### Post by David D. on 2014-03-21
13.04 has reached end of life (as of January 27, 2014).  

Try downloading and installing 13.10.

---

### Post by grahammechanical on 2014-03-21
I am not clear on what you are trying to do. This

> [COLOR=#000000]I did a fresh install, made with unetbootin on windows 7, USB 2.0 key (32GB) of Ubuntu 13.04 (64bit) install image, on to another USB 2.0 key (16GB).[/COLOR]

This seems to say that you are trying to install Ubuntu onto a USB memory stick by installing it from a live session of Ubuntu running on another USB memory stick. If this is what you are doing then the question to ask is:

Where is the Grub boot loader being install to? Grub is starting to load and it looks for its configuration files in a /boot/grub folder on a designated disk (ijnternal, external, whatever) If it cannot find its configuration files then it goes to a Grub Rescue prompt. Grub is saying it cannot find the disk where it has been told to look. This is what is meant by the /by-uuid/etc., does not exist message.

Regards.

---

### Post by dima6 on 2014-03-21
I am installing from live session USB using Install Ubuntu option with the target of another USB key.
I am not loading live session (i.e. "Try Ubuntu without installing") as part of it. I only did it to run boot-repair after install to attempt to repair the installation.
Hope this clarifies it.

---

### Post by dima6 on 2014-03-31
So the solution to my problem that I found was to recreate the installer usb key of Ubuntu 13.04 LiveCD (or whatever the name) using unetbootin with .iso file instead of direct download on a different USB key (also 32GB) and install it again onto the same USB key (16GB).
This time it worked, no boot or any other issues.

---

### Post by bapoumba on 2014-03-31
Please mark your thread as solved (under Thread Tools menu), thanks.

---

