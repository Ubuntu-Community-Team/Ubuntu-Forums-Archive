---
title: "installation package failure"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by peeb61 on 2006-06-24
Hi Newbie here!
After 5 attempts at installing Ubuntu, I think I just about given up.

After it successfully installs the base installation, it then goes on to install the packages, this gets to 96% and stops with an error something to the like:

"Cannot continue, insufficient disk space/ clean cd / packager install failed"

It then asks me to try and copy the packages files to the hard drive and then mid way fails again.

I've tried different hard drives and different CD drives but still the same error.

I am able to install the server setup version without a problem but this just boots to a command line prompt asking for user name and password, I do this and nothing just sits there with the $ waiting for instructions.

Any ideas before this PC ends up like a torpedo!  ](*,) 

Peeb

---

### Post by hegenious on 2006-06-24
boot the server and type this command at the "$"
startx
this should start your gui environment.

does the hdd you are installing to hold enough free space? can you post the disk size here? and the amount of RAM that is in your computer?

---

### Post by peeb61 on 2006-06-24
Thank you for you prompt reply hegenious.

The harddisk is 20gig with 256mb ram.
CPU - Pentium 2 400 (Is this enough?)

Thanks in advance

Peeb

---

### Post by peeb61 on 2006-06-24
Further to that last thread:

I typed in 'startx' like you suggested at the peeb@ubuntu:~$ prompt.

The error line I got back was: -bash: startx: command not found.

any other suggestions? Many thanks

Peeb

---

### Post by peeb61 on 2006-06-25
Again further to this saga......

I've actually done a new default install with some success.
The error message was still there trying to install the extra packages at 72% so I configured the install to look for updated files from the cdrom when it was rebooted after it was finished.

It did this and found the extra packages on the installation disks and installed them from there, with a couple of minor errors it appears to running fine after logging into the GUI, the only item it appears that didn't install was openoffice!

I've just downloaded a copy off the website and I'll give that a go.

I'll let you know how it goes.

Peeb

---

