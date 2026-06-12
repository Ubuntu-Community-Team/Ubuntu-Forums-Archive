---
title: "Help with new installation/Recognizing video"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by Guthdog on 2007-10-10
Hello all,

My 14 year old son and I are trying to learn more about linux so we took a homebuilt box with an Intel MB and started loading linux, first Debian now Ubuntu.  I have been a gui guy for a long time, so the CLI is a challenge for me. but the boy seems to be picking it up OK.

I was able to eventually load Debian and use it successfully for several weeks before I downloaded an update and it wrecked the system.  I heard from a number of people that Ubuntu is a little more user freindly, so we bought a book on Ubuntu and loaded it as well.  We came up with the same issue as with Debian.

The Xserver fails upon startup when we do a fresh load.  The issue is identical with both Debian and Ubuntu as far as I can see. 

I tried to use "Dpkg-reconfigure xserver-xorg", the machine finds the onboard video on the motherboard and not the NVIDIA MX4000 that was installed for this purpose.  It does not offer me the opportunity to change the video card.  The next task is to specify the PCI address of the video device which is defaulted to 0:2:0.  I attemped to change the PCI address that I found for the MX4000, (using "lspci"), 0000:1:0.0, but I get an error message telling me that I have an incorrect format for the address, (I tried several different variation on that address, 0:1:0, 0:01"0 etc.), but it gave the same error.

The funny thing is that this was very similar to the issue I had when I first loaded Debian, and I was able to fix it.  When I got to the video device screen in "Dpkg-reconfigure xserver-xorg", I was given the correct video device but the wrong PCI address.  All I had to do was change the PCI address and it worked.

I have been in the bios to see if there is a way to shut off the onboard video and I have been unable to do so.

Any good ideas out there?

Stewart

---

