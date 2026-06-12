---
title: "A (possible) Challenge?"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Tyrmatt on 2008-02-21
Hello there.
 My flatmate recently persuaded me to try out Ubuntu as an alternative OS and I'm impressed with the slickness, so kudos there. 
But to the challenge. Said flatmate also has an ageing P3 700mhz laptop that's riddled with ageing versions of Ubuntu. He's not really interested in using it, so I thought I'd turn it into a kitchen machine so I can read recipes there and watch streaming video etc while I'm cooking.  So I finally got it to turn on and boot up. And it's a mess. The networking systems seem to be missing entirely and all sorts of things don't work. So obviously a fresh install of the newest Xubuntu is in order to make my having recipes in the kitchen dreams come true.
The catch? It's a completely driveless ultra-portable (yes, I laughed too) with one USB slot (that has no booting capability) and a PCMIA WLAN card. And thus my problem is that I can't figure out a way to prepare the hideously partitioned drive (about 4 seperate Ubuntu installs plus a Windows partition and God knows what else) so I can either use a USB stick or a LAN lead to install the new Xubuntu release. While I'm a relatively new Linux user, I'm fairly savvy in terms of tech so don't pull any punches in complexity if it's possible to do this in some archaic ritual from the nether-times.
Much obliged folks.

EDIT: Additionally we just found an ancient PCMIA LAN card and there is an option to boot from network in the (most limited I have ever seen) BIOS. So if that helps

---

### Post by zvacet on 2008-02-21
Look [here.](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by Tyrmatt on 2008-02-22
Hmm, I've had a shot of that tutorial from both the Windows and Ubuntu sides and neither seems to make the laptop want to boot from the network. I presume therefore that the LAN card is NOT PXE compatible due to it being PCMIA.  Well at least I've learned something from that.
Any fresh strategies in light of this evidence? I guess I'm gonna need some way of loading a driver to make the card PXE compatible without using a floppy or CD...

---

### Post by chewearn on 2008-02-22
In the first place, how was your flatmate able to load multiple ubuntu in there, if the laptop is unable to boot off anything?

The solution could be as simple as asking him?

---

### Post by Tyrmatt on 2008-02-22
I asked him about a week ago when I first began this project and  he apparently did it an age ago and has no recollection of how exactly he did it (or even if he did it at all) and I'm guessing by the hideous mess of installs that it wasn't him doing a lot of it.  The laptop when I unearthed it from underneath a pile of coursework wouldn't boot any of the 6 OS's it apparently has and required "fsck"(I think?)  to be run in order to try and rebuild it. I think this is probably what wiped out the networking.  It is possible to boot into the hard drive and the BIOS claiims it can boot from HDD, FDD, Network and Default Boot Device (presumeably the HDD) but from what I can tell, pressing any key results in the HDD loading it's GRUB loader.
The laptop itself is a Toshiba Portegé 3480CT (or possibly one model higher, as it's had the screen replaced) and after having a look at some articles on the laptop itself, I seem to be rather screwed without a PCMIA CDROM. 
I wonder if[ this ]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe")  and [this]("http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install") are perhaps more in the vein of what I'm looking for. I think what I'm really after here is a way to alter the GRUB loader to give me the option to boot from PCMIA LAN as opposed to PCMIA CDROM.
It seems the PCMIA CDROM if it still exists is somewhere down in Wales and his parents are in New Zealand for the foreseeable future so I'm relying on the few tools I have.
Much obliged

---

