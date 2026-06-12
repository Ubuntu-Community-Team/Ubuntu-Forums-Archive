---
title: "Xubuntu cd(s) not bootable"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by bradenn on 2011-09-13
I am trying to install Xubuntu (11.04) on an older laptop with ~1Ghz and 256 M RAM. Seems like this should be sufficient resources to install (and operate) Xubuntu, but it isn't working. I have tried the 32 bit desktop and 32 bit alternate cds. I have burned iso images onto cd for both installs, and in both cases
a) had valid checksums
b) burned successfully as images (verified by booting on a higher-resource machine)
c) tried to boot from cd on my target machine (netbios is configured to boot from cd first)
d) got message that the cd was not bootable before the machine reverted to the former hard-drive Windows XP boot.
(I had the exact same problem with #!, but not looking for support for that at the moment)

I have since burned a DOS bootable cd and the target machine (the one that considered all of the Xubuntu cds not to be bootable) boots from that cd fine. Any idea what my problem could be and how to resolve it?

FWIW, it is an HP Pavillion ZT 1000.

Thanks!

---

### Post by mörgæs on 2011-09-13
Xubuntu is getting quite big - it is still my favourite among the Buntus, but not because it is light. 

With 256 MB memory I would go for Lubuntu. If the regular install does not work, you could try this:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by bradenn on 2011-09-13
Well, I tried the lubuntu iso and had the exact same response; my machine indicated that it was not a bootable cd. So then I tried the mini.iso from the link in the above post on this thread. At first, it looked like it was going to work. It acknowledged that it was a bootable cd and started to read from the cd, then I got a prompt that the checksum was not valid and a prompt to press any key to try again. However, I got no response when I pressed keys at that point. Even more frustrating, when I tried again to boot from the mini.iso cd I could not re-create the failed boot. Instead, I got the same response that I had from all the other bootable cds--the machine said that is was not a bootable cd. Uggggh. Could this be a cd hardware issue (even though the DOS bootable cd works)? Oh yeah, forgot to mention that I did do a checksum on the mini.iso and it looked fine. Why would I get a checksum error when I appear to have a matching checksum (I am clueless what the checksum is really doing).

---

### Post by JD8182 on 2011-09-13
Does the CD drive that you are using on that machine read CD-R or RW media by chance? I know some of the older CD drives did not read burned CD-Rs or RWs. Just a thought..




> **bradenn said:**
> I am trying to install Xubuntu (11.04) on an older laptop with ~1Ghz and 256 M RAM. Seems like this should be sufficient resources to install (and operate) Xubuntu, but it isn't working. I have tried the 32 bit desktop and 32 bit alternate cds. I have burned iso images onto cd for both installs, and in both cases
a) had valid checksums
b) burned successfully as images (verified by booting on a higher-resource machine)
c) tried to boot from cd on my target machine (netbios is configured to boot from cd first)
d) got message that the cd was not bootable before the machine reverted to the former hard-drive Windows XP boot.
(I had the exact same problem with #!, but not looking for support for that at the moment)

I have since burned a DOS bootable cd and the target machine (the one that considered all of the Xubuntu cds not to be bootable) boots from that cd fine. Any idea what my problem could be and how to resolve it?

FWIW, it is an HP Pavillion ZT 1000.

Thanks!

---

### Post by bradenn on 2011-09-13
Yeah, it reads both--at least when they do not have a bootable ubuntu iso of some sort :(  During the process of all the failed attempts, I did a test by burning a bootable DOS cd (same rack of cd-r, same burner, same lowest speed setting, etc.), which then booted fine.


I am now getting a repeatable error message when I try to boot the mini.iso cd

"1200 Mhz Mobile Pentium III /m CPU
Intel Processor Update Rev 01Dh Complete
External cache 512k installed
Boot CD-ROM Type: Non-Emulation Booting

Isolinux 4.02 debian 20101016 ETCDisolinux: Image checksum error, sorry...

Boot failed: press a key to retry..."

(and no response if i try to retry)

---

### Post by JD8182 on 2011-09-14
Right.. Sorry I missed your statement about booting from DOS CD..Have you tried any other versions besides those two? Have you considered Puppy linux or Slitaz? Maybe even try booting from a USB thumb drive if you have access to another PC to create the bootable USB. Just another thought.





> **bradenn said:**
> Yeah, it reads both--at least when they do not have a bootable ubuntu iso of some sort :(  During the process of all the failed attempts, I did a test by burning a bootable DOS cd (same rack of cd-r, same burner, same lowest speed setting, etc.), which then booted fine.

---

### Post by bradenn on 2011-09-14
o.k., I think my problem may be my bios. I checked for updates and found that there is an HP update that has a fix for "FIXED: Unable to boot from CD's recorded using the El Torito standard". 

Great, so I just update the bios then. Not so easy, HP (in their infinite wisdom???) only offers an update (as far as I can find) that is an executable file requiring a floppy drive. However, this laptop has no floppy drive (and never did). 

Can anyone tell me if the El Torito standard would be the standard for the ubuntu iso files? If so, then I bet this is my problem. If so, any advice on how to get the bios update to work without a floppy? I am hesitant to run the wizard from the executable because I don't want to kill the old bios only to have no way to finish install of the updated one. Thanks.

---

### Post by mörgæs on 2011-09-14
If you don't want to mess with the BIOS, you could take out the hard drive and insert it into another computer. Here you install Lubuntu (a plain vanilla without closed-source drivers) and after that you move the hard drive back.

---

