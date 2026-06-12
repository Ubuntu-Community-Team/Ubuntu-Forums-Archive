---
title: "Ati Radeon 9550 problems"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2008-06-03
I keep having problems with my ATI Radeon 9550 graphics card driver. The stock standard Ubuntu driver (Mesa?) gives me a usable desktop but if I install the Ati driver I get a white desktop after reboot and logon. I got back to my desktop with the ALT-F2 and entering "metacity --replace".
I have tried installing the later driver from ATI but that resulted in lost connections and a full re-install (I am getting to be an expert at re-installing!! and could lead newbies blindfolded through that:))
Is it just my computer, just me or is there something amiss with the drivers?
At the last install attempt a check told me that the Mesa driver was still active which would appear to be case this time.
Any suggestions please.

---

### Post by wpshooter on 2008-06-03
1) Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

2) Have you tried installing in safe graphics mode.

3) Have you considered installing using the ALTERNATE (text based) CD, if you have not already done so ?

4) I generally have found that changing the video driver from anything other than what is installed by the Ubuntu O/S is USUALLY a mistake but having said that, have you tried installing the driver thru ENVY ?  But let me say that on several occassions that I have tried installing thru ENVY, I did not wind up with the proper screen resolution level. i.e. on some occasions (not all) the resolution was lower than desirable.

Good luck.

---

### Post by Stolea on 2008-06-03
will give it a go, but am not very hopeful.
Thanks

---

### Post by Stolea on 2008-06-05
I went through the entire installation procedure as set out the the Ubuntu insructions [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
when i run 
peter@shop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
it tells me that the mesa driver is still in charge.
When I go to the how to remove the mesa driver section
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)
I don't understand what to do. How do I remove the package xserver-xgl? And will that possibly blow the display away again?
Can anyone shed some light on this?

---

### Post by dslax27 on 2008-07-07
Any luck Stolea?

---

