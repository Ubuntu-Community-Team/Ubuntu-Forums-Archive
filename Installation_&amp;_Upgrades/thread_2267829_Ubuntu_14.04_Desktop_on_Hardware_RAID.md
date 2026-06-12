---
title: "Ubuntu 14.04 Desktop on Hardware RAID"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by thiago-canaes on 2015-03-04
Hello.
I have a pc that will work as a normal desktop and a file-only server.
I created the RAID 1 group with 2x 500Gb HDs and named it RAIDHD.

Windows installation sees the RAID as single volume, as I expected, and install as normal.
Ubuntu too, sees only the RAIDHD. It even let me create partitions as a normal volume (/, SWAP, /HOME) , but when it start installing, I get a ??? ??? error. 
I searched google but all I could find was how to create a SOFTWARE RAID, and thats not what I want. I found in youtube an installation of Ubuntu Server on a Hardware RAID, but, since the PC will work as a normal desktop, I can't see why would I install a server driven OS.

The strange thing in Ubuntu installation, was that the RAID HD had a weird name.
/mapper/dsodhfshdf_sçdl_RAIDHD    (the "dsodhfshdf_sçdl_" part keeps changing after every reboot)
And the installation displayed a /dev/sda at the initialization devices list that didn't appear at the volumes list. I tried installing on /dev/sda and on /mapper//mapper/dsodhfshdf_sçdl_RAIDHD.
Both times I had the ??? ??? error.

My MOBO is a GA-H97M-UD3.

I'm considering installing the SERVER version and then installing Ubuntu-Desktop trough apt, but I would like to do that only if there is no other way.

Tnks in advance,
TC.

---

### Post by ajgreeny on 2015-03-04
This might help you either to install to RAID or figure out what to do about using the live desktop DVD/USBto do so.

I have no experience of RAID in any way, shape or form, so will leave you to sort out the details.

[http://askubuntu.com/questions/505446/how-to-install-ubuntu-14-04-with-raid-1-using-desktop-installer](http://askubuntu.com/questions/505446/how-to-install-ubuntu-14-04-with-raid-1-using-desktop-installer)

---

### Post by MAFoElffen on 2015-03-05
First observation-- Your mobo's chipset is Intel H97/Z97 (Series 9) which is new. So looking through the bug-reports, I see various on linux-firmware and this chipset.
[IMG]http://icdn2.digitaltrends.com/image/9-series-feature-chart-1200x800.jpg[/IMG]
So the question to go with that is if you are trying to install 14.04.1 or 14.04.2? I would make sure you at leats go with .2. What I know from installing Server Edition and testing... Is that the Server Editions are more up to date with hardware and firmware. I know with some newer 2-in-one notebooks, the wireless drivers are there on the Server ISO, and still not there to Desktop... so... draw your own conclusion about that. I may be bias, as I'm on the Server team... But I think the Server ISO gets a few backports as things get added.

If you can wait a few weeks, 15.04 is due for release real soon. Seems stable and would have the newest support from kernel and linux-firmware... For that chipset... even though 15.04 is not an LTS, that is what might be your best best for your hardware.

---

### Post by thiago-canaes on 2015-03-07
Hi! Tnks for the replies.

I'm trying to install Desktop 14.04.2.
I did some reading, and was able to understand a little bit more. 
I could understand that I should partition my harddrives equaly, and then, using mdadm, create a Raid Volume. but it seams like a software raid management.
I could not find how mdadm would work with the hardware raid controller.
I dont know how to set up the BIOS... If I should set the harddisks for RAID SATA MODE, and create the RAID volume in the raid controller, or just leave as a normal PC with 2 HDs (SATA MODE IDE/AHCI with nor RAID volume).
MDADM seams to not care about the hardware controller.

---

