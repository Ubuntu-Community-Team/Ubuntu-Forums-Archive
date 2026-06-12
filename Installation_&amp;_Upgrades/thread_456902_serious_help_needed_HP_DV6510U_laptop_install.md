---
title: "serious help needed: HP DV6510U laptop install"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by nobodie on 2007-05-28
Ok, this thing is new, very new, just out. I've run into some biggies on install. If I have asked about some of this in other posts (I've been struggling alone on this so far) I apologize in advance, but I am completely knocked down by this one.

Machine: HP Pavilion Entertainment PC laptop DV6510U. MOBO Intel w/ 965GM chipset. Processor, core 2 duo 7300. The chipset is the problem I think, as well as the xorg support on the video display.

On install everything goes fine. I used the FF7.04 alt install disc rather than the live CD. Lives wouldn't even start up on this. It is preloaded with Windoze home basic some kind of vista thingy so the hardware works in an inferior OS.

On boot however, the damn thing will not load the screen drivers: 

EE VESA 0 No matching modes found
EE screen(s) found but none have a matching configuration

Looking for drivers on the Intel site I discovered a curious thing. The flavor for the sound adapter on this thing doesn't seem to be in their database for Linux. The show ICH4, ICH5, ICH7 but this is ICH8, which is not shown. 

How does this relate? It has been suggested that I use the 915resolution tool to get it to work, but that tool fails with the message that it is only suitable for 800 and 900 series chipsets. It won't load.

In desperation I tried to load my last year's copy of fedora core 6 and..... the screen works fine. What??? but I have no network connection, which i had on the FF install. It doesn't recognize the ethernet card in fedora and not only that, it doesn't even allow hand loading since it refuses to admit it exists, no drivers for the ethernet controler. 

In great desperation I DLed the latest fedora 6.93 as a live CD, but it won't load. It fails to recognize the DVD player (or at least the "rc" is normally the cd-rom drive that is bootable) and therefore can't mount a file system.

xorg is running 7.2.0, 7.3 will be out any day now, but will it solve the problem? 

fedora 7 will be out soon, but will take weeks to DL right after it comes out, and it will need a dvd burner which I only have on the lappie. I suppose i could load lynx and graphical internet to the DL site and get the current Dvd and burn it using, jeez I am getting to be such a geek and i don't wanna be.

this is my daughter's lappie and she is leaving for the US to go to university, i reallly want it right for her righht now and I need help

so, if anybody has some ideas we can't go wrong by trying.

thanks

---

### Post by handband2 on 2007-06-05
nobodie,

I have a Dell Latitude D630 and had problems with the intel 965 graphics chipset.  The following helped me to solve my graphics problem:
[http://ubuntuforums.org/showpost.php?p=2754506&postcount=4]("http://ubuntuforums.org/showpost.php?p=2754506&postcount=4")

Note* - I chose the video driver "intel" and until the driver is upgraded ([http://www.intellinuxgraphics.org/download.html]("http://www.intellinuxgraphics.org/download.html")) the resolution appears blurry.

---

