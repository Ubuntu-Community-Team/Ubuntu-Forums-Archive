---
title: "xubuntu install pkg"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by m4ttd on 2008-03-23
'lo all,

Hope this is the right place to post this.
Sorry for the rambling description but unsure as to what germain

Bckgrd:
mi == LINUX newB.
Old PC (from memory test):
Viglen Genie 2
Pentium II 232.7MHz
L1 Cache:	32K	2281MB/s
L2 Cache:	512K	334MB/s
Memory:		64M	104MB/s 
Chipset:	i440fx

HDD 4.4 GB

Also the box is sitting on an active internet connection and I have seen successfull HTTP calls in Alt F4 screen

Decided to try xubuntu 7.10 alternate install CD
Download via torrent (2008.03.21).
Burnt (x4).
(verified this at xubuntu front menu as previous fast burn disc no good when I did a verify CD)
Booted into CD
F6 (cos on previous attempt with ubuntu 7.10 I was getting old bios... pre 2000 ... set... acpi=force) for boot options.
just before the "--" at the end of the boot options string I added "acpi=off apm=on"
(NB have also successfully got into install via acpi=force but, when doing so I get:
[     0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
ACPI unable to load the system description tables.)

Have got past partition successfully several times.
Currently main partition ~3.9 GB, swap 190 MB (was ~ 300 MB but on last partition did the LVM option which dropped swap down to ~190)

anyway...
I have failed several time on installing base system.
On retry I have got past this by selecting either of the other 2 options (generic linux image | image <version number>)
on successive fails of "Select and install software" I always seem to get same sort of message from Alt F4 terminal
someting similar to
pkgsel not found| not on disk
&
couldn't find package language-pack-c

:On my last attempt
(please forgive typos)

<datetime> Buffer I/O error on device sr0, logical block 352243
...
<datetime> in target: Failed to fetch cdrom[Xubuntu 7.1 _Gutsy Gibbon_ -
release i386 (20071016)]/pool/restricted/r/restricted-manager/restricted-manager
-core_0.33.1_all.deb Hash sum mismatch
<datetime> in target: 0 upgraded, 556 newly installed 0 to remove and 0 no
t upgraded
<datetime> in target: need to get 0B/301MB of archives
<datetime> in target: sfter unpacking 1095MB of additional disc space will
be used
<datetime> in target: E:
<datetime> in target: Unable to fetch some archives maybe run apt-get upda
te or try with -- fix missing?
<datetime> in target: 
<datetime> in target: tasksel: aptitude failed (100)
<datetime> main menu[2145]: WARNING**: Configuring 'pkgsel' failed with er
ror code 1
<datetime> main menu[2145]: WARNING**: Menu item 'pkgsel' failed

NB unsure how to scroll back in this screen

On last atempt I guessed this may have someting to do with languages so I left default (us) options, though I did do autodetect on my gb keyboard.

Any suggestions??

thnxmatt

---

