---
title: "Trouble Installing"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by N3PT00n on 2009-12-10
Hello Guys and Gals,

Last weekend I committed myself to trying to learn Linux and install it as a server on my aging Desktop Computer. I burnt Ubuntu 9.1 and 8.04 LTS 32bit editions. Both of these the checksum turned out fine.

The problem is sometimes I would get a Buffer I/O error, sometimes nothing, and only got it to boot 2x. I did a CD disc check, and a memory Test for my computer. Everything checks out. arggg.

Anywho I finally got to the install screen and figure spent all this time getting here. I might as well install at this point. So I did and when I rebooted I got to a blank screen with blank command prompt. I think that was at the GUI screen, when I hit ALT+CTRL+F1 I can get to the 'command prompt.' 

I can do commands from there(this is for the Desktop edition). I am really stuck, i think it may have something to do with the motherboard but I am not sure. 

The specs on my computer are as follows:
Motherboard: IC7-G
HDD: 80GB
Memory: 2GB
CD/DVD R/W

---

### Post by darkod on 2009-12-10
The I/O error might have been the cd drive not reading the cd nicely, or worse, your hdd reporting errors which might mean it can soon fail.
After you installed, getting only command prompt is OK because it's server edition. Ubuntu Server doesn't install desktop GUI and it's even discouraged to do it.
If you just wanna play around, get desktop edition and it has gnome desktop GUI. You can also add server services to desktop version later I think.

---

### Post by N3PT00n on 2009-12-10
hey

thanks for the reply. yea i figured out that the server edition doesnt have a gui. so i installed the desktop gui and i got that weird prompt. I was able to get to a terminal but was stuck on that portion of it. could it be that the motherboard is incompatible with ubuntu?

windows works just fine. oddly enough

---

### Post by thestig_992 on 2009-12-12
I've been having a very similar problem; I can do everything normally in cli only mode, but anything in gui just turns off my screen. This includes the live cd, the initial part where you choose whether to try or install ubuntu displays, but nothing after I select an option. I think this might be the same problem as n3ptoon, since s/he installed with the server version. 

Similarly, I have a perfectly good windows install on the same HDD. (And I know the live cd isnt broken since it has worked perfectly on other PCs).

Motherboard is an MSI one, dont know the exact model of the top of my head, integrated gfx card.

---

