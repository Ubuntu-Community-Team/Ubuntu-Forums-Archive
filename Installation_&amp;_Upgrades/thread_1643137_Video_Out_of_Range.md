---
title: "Video Out of Range"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by Pletsch on 2010-12-11
While installing, I get to the point where I need to select a language for installation, then click next, and the screen goes blank. After a few seconds my display tells me

"Signal Out of Range
H: 61.9 KHz  V: 118.0 Hz
Mode should be below:
1280 x 1024 75Hz"

Is there a way to manually set display output during Installation ?
I am installing the Server Ubuntu 10.10 (32 bit)
This machine is an older server Stratus FT 3300

---

### Post by sikander3786 on 2010-12-11
Welcome to the forums :-)

Are you sure your are installing Server Edition and not the Desktop one? There shouldn't be any graphics problems with Server Edition.

If desktop you can try putting in the 'nomodeset' parameter by pressing F6 at the boot screen.

[https://help.ubuntu.com/community/LiveCDBootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options)

---

### Post by Pletsch on 2010-12-12
Thank you for the welcome :) And the reply.

It is the server version. I don't know what kind of video controller is in this thing, it has what looks like an SCSI connector on the back which goes from both cpu modules to a riser board that has VGA USB and serial connectors. I will be trying it again tonight after work, and the boot options was exactly what I was looking for. I guess I used the wrong search terms trying to find it. If I have to I will switch editions, but figured this one was safest try for this machine. Thank you for your help :)

---

### Post by mxw on 2010-12-13
Are you using a TV screen? I get this problem when i hook up my box upto my TV. It just doesnt want to display that resolution even though it flashes up for a second it seems to think there isnt anything to display hence "out of range". Try searching your monitor/tv make and model with out of range on when connected to PC. I know some have firmware upgrades to fix this problem.

---

