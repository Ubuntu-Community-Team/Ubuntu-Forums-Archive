---
title: "Can't  install .deb packages anymore"
date: 2023-03-14
forum: Installation &amp; Upgrades
---

### Post by claus on 2023-03-14
Hi all,

in 2020, I bought & installed CrossOver Linux 19 from CodeWeavers in order to run Windows software on Ubuntu MATE 20.04. So far, so good. All went well until this year, when I tried to remove CrossOver Linux, mainly because it was outdated. Unfortunately I made a a few mistakes, and now I am unable to install new software. :-( I still have a package 'crossover' which I cannot remove, neither with apt-get remove nor with Synaptic. Is there a way to fix this without having to install Ubuntu MATE anew?

Here's what I get when I try to remove 'crossover':

```
claus@ccyrny:~$ sudo apt-get remove crossover
[sudo] password for claus: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32z1 libc6-i386 libglu1-mesa:i386 libnss-mdns:i386 libopengl0:i386
  perlmagick
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  crossover
0 upgraded, 0 newly installed, 1 to remove and 234 not upgraded.
1 not fully installed or removed.
After this operation, 579 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 496985 files and directories currently installed.)
Removing crossover (20.0.4-1) ...
/var/lib/dpkg/info/crossover.prerm: 47: /opt/cxoffice/bin/cxtie: not found
dpkg: error processing package crossover (--remove):
 installed crossover package pre-removal script subprocess returned error exit status 127
dpkg: too many errors, stopping
Errors were encountered while processing:
 crossover
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help would be highly appreciated.

TIA,

Claus

---

### Post by ian-weisser on 2023-03-14
It's right there in your output:

/var/lib/dpkg/info/crossover.prerm: 47: /opt/cxoffice/bin/cxtie: not found
[FONT=arial]
Line 47 if the pre-removal script[/FONT] (/var/lib/dpkg/info/crossover.prerm) [FONT=arial]tells the system to remove a file[/FONT] (/opt/cxoffice/bin/cxtie), [FONT=arial]but that file isn't there.

You can edit the script.
You can tell apt to --force the removal.
[FONT=arial]You can create a dummy file for the script to remove. This option is often the easiest.[/FONT][/FONT]

---

### Post by ActionParsnip on 2023-03-14
could try:
```

sudo mkdir -p /opt/cxoffice/bin
sudo touch /opt/cxoffice/bin/cxtie
sudo apt --purge remove crossover

```

---

### Post by claus on 2023-03-14
ActionParsnip:

Thanks, I tried that, but got:

> dpkg: too many errors, stopping
Errors were encountered while processing:
 crossover
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Claus

---

### Post by claus on 2023-03-14
> **ian-weisser said:**
> It's right there in your output:

/var/lib/dpkg/info/crossover.prerm: 47: /opt/cxoffice/bin/cxtie: not found
[FONT=arial]
Line 47 if the pre-removal script[/FONT] (/var/lib/dpkg/info/crossover.prerm) [FONT=arial]tells the system to remove a file[/FONT] (/opt/cxoffice/bin/cxtie), [FONT=arial]but that file isn't there.

You can edit the script.
You can tell apt to --force the removal.
[FONT=arial]You can create a dummy file for the script to remove. This option is often the easiest.[/FONT][/FONT]

Line 47 includes '"$CX_ROOT/bin/cxtie" --unregister'. Where should the dummy file be, and what name should it have? Oh, sorry, '/opt/cxoffice/bin/cxtie'.

Claus

---

