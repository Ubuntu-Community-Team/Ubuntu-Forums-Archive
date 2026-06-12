---
title: "Trying to upgrade kernel from 386 to 686-smp"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by mrtaber on 2005-04-18
I'm getting ready to upgrade my kernel (using Synaptic) from the 386 to the 686 version.  Of course, the 386 kernel is running just fine, but I can never leave well enough alone :)  

So, I go into Synaptic, and I find, under Base Systems, these files:
     linux-image-2.6.10-5-686.smp
     linux-image-686-smp

And under Base Systems Restricted I find:
    linux-686-smp
    linux-restricted-modules-686-smp

All I can say is, d'oh?  Which of these do I install? And is order important?

Thanks in advance for you help,
Mark Taber

---

### Post by soul_rebel on 2005-04-18
you probabli need all those. however one of those is a dummy package that depends on everything you need.

---

### Post by Leif on 2005-04-18
linux-686-smp. This will install everything you need and keep it updated.

---

### Post by mrtaber on 2005-04-18
Just wanted to say, it worked like a charm!  Thanks, all.

Mark Taber :-D

---

### Post by rejser on 2005-04-19
does it work right after the install or is there a bunch of other things to do? I just wan't to know if I or my system have a syntax error

---

### Post by mrtaber on 2005-04-19
After you install, go ahead and reboot the machine.  I didn't have anything unusual happen.

Mark :)

---

### Post by rejser on 2005-04-20
Don't need to update grub and so on?

After I installed nothing happened, editet /etc/boot/menu.lst to edit to contain the new kernel (k7).
When I tried to boot it it said
(kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

---

### Post by soul_rebel on 2005-04-20
you shouldn't be editing that file to add a new ubuntu kernel, that's done automatically by update-grub

---

### Post by rejser on 2005-04-20
oohh, shall try that :)

---

### Post by rejser on 2005-04-20
[QUOTE=soul_rebel]you shouldn't be editing that file to add a new ubuntu kernel, that's done automatically by update-grub[/QUOTE]
 then I get

/sbin/update-grub 
Searching for GRUB installation directory ... found: /boot/grub .
/sbin/update-grub: line 69: awk: command not found

---

### Post by strawberry on 2005-04-20
Do you really need the -smp kernel image? I found this:

'Package: linux-image-2.6.10-5-686-smp (2.6.10-34)
Linux kernel image for version 2.6.10 on PPro/Celeron/PII/PIII/PIV SMP.
This package contains the Linux kernel image for version 2.6.10 on Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV with SMP support, the corresponding System.map file, and the modules built by the packager. **SMP (symmetric multi-processing) is needed if you have multiple processors.** It also contains scripts that try to ensure that the system is not left in a unbootable state after an update.'

---

### Post by Leif on 2005-04-20
SMP also works if you've got a p4 with hyperthreading. Otherwise you'll be losing out on quite a bit of its performance.

---

### Post by rejser on 2005-04-20
I'm not after the smp kernel, I'm after the k7 kernel.
I have 1.5 Gb of ram, and with the 386 kernel I can only use about 900.
So I'm trying to install the k7

---

### Post by emmet on 2005-04-20
[QUOTE=Leif]SMP also works if you've got a p4 with hyperthreading. Otherwise you'll be losing out on quite a bit of its performance.[/QUOTE]
 Oh wow! That is the quickest kernel upgrade I have **ever** done! Updated to the SMP processor in under 10 minutes (reboot included).

I've only been using Ubuntu for three days, and this is - so far- the most *user friendly* distribution I've ever had. I was using Mandrake/Mandriva for three years and this is a lot nicer. I converted all my web server, IMAP server and SSH/VNC servers in just 36 hours...

I just hope it stays this simple!

Thanks to all the developers/documenters/designers/gurus (and everyone else) who worked hard to get Ubuntu to where it is today!

Emmet

---

### Post by rejser on 2005-04-21
Why don't it work for me to install?
Can install, but I don't get the boot-option.
And if I edit menu.lst to contain the info for the files in /boot/
I get kernel sync panic, unable to mount root fs

---

### Post by Leif on 2005-04-21
[QUOTE=rejser]Why don't it work for me to install?
Can install, but I don't get the boot-option.
And if I edit menu.lst to contain the info for the files in /boot/
I get kernel sync panic, unable to mount root fs[/QUOTE]

What happens if you try to reinstall linux-k7 ? Does grub get updated then ? 

Looking at your previous post, maybe you should reinstall awk before trying this.

---

### Post by tumpy on 2005-04-21
thanks to this thread starter for asking this Q, i did the kernel 686 smp update from 386 and it work i've notice the increase in speed also,  i am useing kubuntu  love ubuntu but dont like gnome  prefer kde so kubuntu is my choice after trying about nine other distro's, this is the only distro that work out of the box with my smc2532w-b wireless adapter on my Evo N160 laptop..
thanks to leif your suggestion on how to work for me..

---

### Post by rejser on 2005-04-21
[QUOTE=Leif]What happens if you try to reinstall linux-k7 ? Does grub get updated then ? 

Looking at your previous post, maybe you should reinstall awk before trying this.[/QUOTE]


I did reinstall, tried this a couple of times before, but for some reason update.grub worked this time, really glad I rebooted the computer, only to recieve this message

"Kernel panic - not syncing: VFS: Unable to mount roott fs on unknown-block (0,0)"

---

### Post by rejser on 2005-04-21
[QUOTE=rejser]I did reinstall, tried this a couple of times before, but for some reason update.grub worked this time, really glad I rebooted the computer, only to recieve this message

"Kernel panic - not syncing: VFS: Unable to mount roott fs on unknown-block (0,0)"[/QUOTE]
 If I trie to install by apt-get I get

Följande ytterligare paket kommer att installeras:
  linux-image-2.6.10-5-k7 linux-image-k7 linux-restricted-modules-2.6.10-5-k7
  linux-restricted-modules-k7
Föreslagna paket:
  lilo linux-doc-2.6.10 linux-source-2.6.10 avm-fritz-firmware-2.6.10-5
Följande NYA paket kommer att installeras:
  linux-image-2.6.10-5-k7 linux-image-k7 linux-k7
  linux-restricted-modules-2.6.10-5-k7 linux-restricted-modules-k7
0 uppgraderade, 5 nyinstallerade, 0 att ta bort och 1 ej uppgraderade.
Behöver hämta 0B/21,6MB arkiv.
Efter uppackning kommer 61,9MB ytterligare diskutrymme användas.
Vill du fortsätta [J/n]? J

Preconfiguring packages ...
Väljer tidigare ej valt paket linux-image-2.6.10-5-k7.
(Läser databasen ... 76671 filer och kataloger installerade.)
Packar upp linux-image-2.6.10-5-k7 (från .../linux-image-2.6.10-5-k7_2.6.10-34_i
386.deb) ...
Väljer tidigare ej valt paket linux-image-k7.
Packar upp linux-image-k7 (från .../linux-image-k7_2.6.10-7_i386.deb) ...
Väljer tidigare ej valt paket linux-restricted-modules-2.6.10-5-k7.
Packar upp linux-restricted-modules-2.6.10-5-k7 (från .../linux-restricted-modul
es-2.6.10-5-k7_2.6.10.5-1_i386.deb) ...
Väljer tidigare ej valt paket linux-restricted-modules-k7.
Packar upp linux-restricted-modules-k7 (från .../linux-restricted-modules-k7_2.6
.10-7_i386.deb) ...
Väljer tidigare ej valt paket linux-k7.
Packar upp linux-k7 (från .../linux-k7_2.6.10-7_i386.deb) ...
Ställer in linux-image-2.6.10-5-k7 (2.6.10-34) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: 254:0: Cannot find LVM device
Failed to create initrd image.
dpkg: fel vid hantering av linux-image-2.6.10-5-k7 (--configure):
 underprocess post-installation script gav felkod 2
dpkg: beroendeproblem förhindrar konfigurering av linux-image-k7:
 linux-image-k7 beror på linux-image-2.6.10-5-k7, men:
  Paket linux-image-2.6.10-5-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-image-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av linux-restricted-modules-2.6.1
0-5-k7:
 linux-restricted-modules-2.6.10-5-k7 beror på linux-image-2.6.10-5-k7, men:
  Paket linux-image-2.6.10-5-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-restricted-modules-2.6.10-5-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av linux-restricted-modules-k7:
 linux-restricted-modules-k7 beror på linux-restricted-modules-2.6.10-5-k7, men:
  Paket linux-restricted-modules-2.6.10-5-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-restricted-modules-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av linux-k7:
 linux-k7 beror på linux-image-k7, men:
  Paket linux-image-k7 är ännu ej konfigurerat.
 linux-k7 beror på linux-restricted-modules-k7, men:
  Paket linux-restricted-modules-k7 är ännu ej konfigurerat.
dpkg: fel vid hantering av linux-k7 (--configure):
 beroendeproblem - lämnar okonfigurerad
Fel uppstod vid hantering:
 linux-image-2.6.10-5-k7
 linux-image-k7
 linux-restricted-modules-2.6.10-5-k7
 linux-restricted-modules-k7
 linux-k7
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rejser on 2005-04-24
During the kernel-install it complains about lvm, and it can't find root fs after reboot.

Ran lvmdiskscan
It resulted in. 
0 disks
6 partitions

Shouldn't it at least find 1 disk (have 3)

Could this be a part of my problem, and how do I add a disk to lvm? (never botherd about lvm before)

---

### Post by rejser on 2005-04-26
Strangly it was an error in my /etc/fstab file (had kept my old from slackware, and there where obviusly something missing)

After I got a fresh fstab I could install a new kernel just like the almighty ubuntu-creator intended

---

