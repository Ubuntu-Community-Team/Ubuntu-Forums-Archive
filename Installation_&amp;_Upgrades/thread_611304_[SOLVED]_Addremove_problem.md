---
title: "[SOLVED] Add/remove problem"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by Donnie Darko on 2007-11-12
After I installed compiz fusion and AWN, I've had problems with my add/remove programs box. It gave me a code for terminal, but that didn't work either. [IMG]http://img.photobucket.com/albums/v451/ska7245/Screenshot5.png[/IMG]

Can anyone help me here?

---

### Post by rsambuca on 2007-11-12
What did it say when you ran

sudo apt-get install -f

---

### Post by Donnie Darko on 2007-11-12
That's whats in the terminal to the left there

---

### Post by Donnie Darko on 2007-11-12
sudo apt-get install -f
[sudo] password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
2 not fully installed or removed.
Need to get 0B/63.1kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libawn-bzr
Install these packages without verification [y/N]? y
(Reading database ... 122953 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr141-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr141-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr141-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rsambuca on 2007-11-12
I assume you have added some outside repos in there.  Try disabling those and running the command.

---

### Post by Donnie Darko on 2007-11-12
how do I do that?

---

### Post by lel on 2007-11-14
hi, i was facing the same problem too.
first, u have to go to the synaptic package manager at system>administration
then, if u see the broken dependencies category on the left side click it
uninstall avant-window-navigator-bzr, awn-core-applets-bzr, python-libawn-bzr.
while removing those three, ignore the error caused by the libawn-bzr trying to auto install.
also uninstall the libawn-0 or libawn0.

if all goes well, it should be back to normal.
unless if ur case is different than mine.

after that u can install awn again, at least mine was ok

---

### Post by Donnie Darko on 2007-11-16
thanks, it was AWN.

---

