---
title: "Acer TravelMate 8100"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by uk_chris on 2007-01-29
Hi,

I would like to install Ubuntu onto my Acer laptop, unfortunately I cannot seem to get it to play ball. I have tried installing with the option of vga=711 noapic but this doesn't seem to work. 

I get to the point that I see the ubuntu splash screen and then I hear the start up sound, but I do not get a display on screen. I thought that maybe it had defaulted to the external output, but I do not get a display on that either. 

I've also tried, noacpi acpi=off but these options do not work either. 

I've searched the net as much as I can, lots of people offer suggestions on how they got it to work. But so far, I am unable to get as far as them. 

Any help would be great full. 

Many thanks.

Chris

---

### Post by strandlooper on 2007-02-23
Hi,
Ubuntu works out of the box on a Acer Travelmate 8100 Series. The only thing to do is to edit your xorg.conf  in a way like discripted below:

When the screen goes black you press: ctrl+alt+F2.
log in (if necessary)
type: sudo vi /etc/X11/xorg.conf

add line

Code:
Option "MonitorLayout" "LVDS,AUTO"

to end of Device section.
save and exit.

type  sudo /etc/init.d/gdm restart
or
ctrl+alt+backspace

It should work.

On my Acer TM 8100 no boot options were needed.

of course you can use any editor. vi is the one I use.

---

### Post by uk_chris on 2007-02-23
Hi strandlooper,

I've tried that after spending hours reading up on it online. When I press ctrl + alt + F2 the screen corrupts and will not allow anything to be displayed. I booted into "safe mode" and edited the xorg.conf file as posted around the internet but it still will not boot correctly. 

any other suggestions would be great.

thanks. 

chris

---

### Post by strandlooper on 2007-02-23
I  have exerienced the same several times special on latest Ubuntu releases. To switch from ctrl+alt+F1 to F8 helped for me. At least one terminal worked and editing xorg.conf was possible.
I hope that helps

---

