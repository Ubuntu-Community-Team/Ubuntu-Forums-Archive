---
title: "installing ubuntu 8.10 on a compaq PC"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by Jo21 on 2008-11-20
my specs are: compaq presario PC Sr1215la
HD 40gb
intel celeron 2.52ghz
ram: 512mb DDR 2700
Main video card PCI: nvidia fx 5500 
onboard: Intel 845.


okay there is a problem when i try to boot the live CD from the nvidia card.

the progress bar freeze up and i can't pass not even 20% of the installation can't load the live CD. after some time i get many weird errors: too many [·$"·$"·12312 random that doesn't tell me anything of what's wrong

if i try doing it using the onboard intel i get it to load screen.
even the start sound but then the screen turns black and i can't get pass that.

i tried turning ACPI off like i did with previews versions.
before to install the nvidia driver i had to blacklist intel AGP.
it worked up until ubuntu 7.10
in ubuntu 8.04.1 i don't have any problems i can install with the nvidia card  using the default live CD.
no black list is needed.

the 8.10 works on my notebook an HP PV2325LA without a problem thought
redownloaded from both direct download and  bittorrent.
burned 2 and checked the CDS for defects.

right now i am using 8.04.1 not sure if i upgrade i will get a broken OS.

so either way i can't install ubuntu 8.10 help please =(

---

### Post by logos34 on 2008-11-20
what about trying the (text-mode) [alternate install cd]("http://releases.ubuntu.com/8.10/")?

---

### Post by Jo21 on 2008-11-22
i managed to install it

from 8.04.1 i blacklisted intel_agp and agpgart.

when i upgraded i could boot without a problem.

---

