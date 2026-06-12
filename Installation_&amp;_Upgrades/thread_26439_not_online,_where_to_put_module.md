---
title: "not online, where to put module"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by lmellen on 2005-04-12
[-o< During install the network portion failed. I was told to go back if I new the card module. Where was I supposed to put the module? I'm trying to set up Kubuntu 5.04 on a IBM T-22 Thinkpad. The card is a 3c556B Hurricane -- module
3c59x. I tried modprobe, that didn't do much. Thanks -- Larry

---

### Post by az on 2005-04-13
This may be the problem:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

### Post by lmellen on 2005-04-13
#-o  azz -  I put 3c59x in the modules file, and at boot up the next line after loading modules says:
                               "EEPHRM MAC address is invalid"
                               "3c59x: vortex probe fails  return -22"
I also have another error message later in boot up:
                               " ERROR: temp. failure in name resolution"
The only other problem is the clock, I'll fix that later. 
This seems to be a very nice system, But I'll need to get online. I know the card works, I removed Windows 2000 to install Kubuntu.
                                          Thanks for the reply -- Larry :grin:

---

### Post by az on 2005-04-13
I think the problem is with your driver for your PCMCIA controller, not your driver for your network card.


3c59x: vortex probe fails return -22
That is a network card driver, right?  Do you know what module is the pcmcia controller?
Is pcmcia-cs installed?

---

### Post by lmellen on 2005-04-13
:? Thanks  azz -- If I do a lsmod the network card is listed as 
3c59x-------------------37160--------0
yenta_socket---------19584--------0
pcmcia_core-----------53568--------2 pcmcia,yenta_socket

FindFiles/Folders says pcmcia-cs is in usr/share/doc/, read only 
                      Thanks for the reply -- Larry :grin:


? My stupidity -- If the network card is built in, not a pcmcia slot type, do I still need pcmcia??? :?

azz --If i go to info center and open PCMCIA both slots are shown as empty, as should be. Could the OS be looking in the wrong place? Again I have built in eth0 capacity, I'm not using the PCMCIA slots??? Is built in eth0 a PCMCIA slot??
 
I went througt that bugzilla site you referrenced, and it appears PCMCIA is working. lspci does show the 3c59x card.  -- I'll be around as long as necessary, want to get this working, this looks like an excellent system!!!!!!!!

---

