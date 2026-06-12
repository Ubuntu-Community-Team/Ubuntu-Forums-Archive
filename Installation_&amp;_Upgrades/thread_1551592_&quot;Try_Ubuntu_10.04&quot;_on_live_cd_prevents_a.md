---
title: "&quot;Try Ubuntu 10.04&quot; on live cd prevents all further boots of anything"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by lanzcc on 2010-08-12
Greetings,

The same problem has happened on two entirely different machines: one machine houses 480 nVidia cores hosted by some Xeon or other and runs Ubuntu 9.04; the other machine is the frontend of a rocks mini-cluster (it's a plain vanilla university computer-lab pc, running Centos as installed by the Rocks installer.)

Yesterday I tried to upgrade the Ubuntu 9.04 to 9.10 (because 9.10 is the latest version supported by nVidia CUDA). The installation appeared to go normally, but on reboot it failed. Different attempts at reboot brought slightly different failure points.

So I decide to boot the machine from a Ubuntu 10.04 live cd (this very cd has worked perfectly before).
It booted up, and I ran disk-checking stuff to confirm that no fatal hardware damage had happened. Everything seemed normal.

So I then tried a 9.10 iso cd, to see if it would install from there. The boot sequence thereafter never got to the point of letting me into BIOS, no matter what cd I put in the drive (or none), and no matter how I forced the restart.

Then, before I show the messages, since they are the same on the other system, here's the cluster story.

I came in after a power failure. The Rocks frontend had tried to reboot, but got stuck at "GRUB reloading: stage 2...". Nothing would persuade it to boot or let me in to BIOS. So I tried the 9.10 iso I have made. It worked fine. Then I tried the 10.04 iso live cd, and it worked fine. Then when I tried to begin a re-installation of Rocks, suddenly I was unable to Boot, stuck again, exactly as with the other machine, before even allowing a BIOS entry.


The messages were (literally - left side of screen cut off)

it:alsa-mixer-save main process (4376) terminated with status 1
ecking for running unattended upgrades:    *Asking all remaining processes to terminate...
All processes end within (1) seconds
.
.
.
.   (many errors like this: 850.291533] SQUASHFS error: squashfs_read_data unable to read fragment-cache entry (269a66bd]
.
.
le: error while loading shared libraries: usr/lib/libmagic.so.1: cannot read file: Input/output error
ease remove the disk and close the tray (if any) then press ENTER:



at this point everything I try brings up the same 4 lines:


Will now restart
850.291533] SQUASHFS error: squashfs_read_data failed to read block 0x269a66bd
    <three similar messages total>
tc/rc6.d/S90reboot: 38: reboot: Input/output error

After all these errors, an attempt to boot again the 10.04 live cd gets exactly nowhere, printing out (what are as far as I can tell by eyeballing it) the very same error messages.


DOES anybody know how I can get these two machines back?

THANKS and if it's convenient, please respond to my email address also...

Chris Lanz
[email]lanzcc@potsdam.edu[/email]

---

