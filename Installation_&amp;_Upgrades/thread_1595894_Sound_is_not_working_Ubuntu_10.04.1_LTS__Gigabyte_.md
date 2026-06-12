---
title: "Sound is not working Ubuntu 10.04.1 LTS / Gigabyte H55M-S2H / Core(TM) i3 CPU 530"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by papitu769 on 2010-10-13
p { margin-bottom: 0.21cm; }  Hi all,
 I have the following install situation:
  Ubuntu 10.04.1 LTS in Desktop
Motherboard: Gigabyte H55M-S2H [http://www.gigabyte.com/search/search.aspx?kw=H55M-S2H](http://www.gigabyte.com/search/search.aspx?kw=H55M-S2H)
Procesor 4x Intel(R) Core(TM) i3 CPU 530 @ 2.93GHz.  
 I sound is attached to the motherboard. It works fine in windows so hardware is fine.
 With Hardinfo i get the next information:
 Audio Adapter HDA-Intel - HDA Intel
 

I have followed a few tutorials trying to fix the problem without success.
  I have just downloaded the driver is in
  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false) 
  I run  ./install and i get the next error:
 ./install: 109: Syntax error: "fi" unexpected
 

 Any idea what is the problem?  
 
Thanks.

---

### Post by mörgæs on 2010-10-13
Hi, welcome to the forum.

Have you tried this?
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by papitu769 on 2010-10-17
> **mörgæs said:**
> Hi, welcome to the forum.

Have you tried this?
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)


Thanks, I think i did it. Anyway i did it again with another instlation. I had the nexto message:

sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
**E: No se pudo encontrar el paquete linux-alsa-driver-modules-2.6.31-22-generic**

I tried bye the **[B]via Synaptic Package Manager**[/B]. I got nothing when i searched the driver,
 
[LIST]
[*]Open up the "Synaptic Package Manager" if it isn't already open: 
[LIST]
[*]System -> Administration -> Synamptic Package Manager 
[/LIST]
[*]Search for the "linux-alsa-driver-modules" package: 
[LIST]
[*]Edit -> Search 
[*]
[/LIST]
[/LIST]

¿?

---

### Post by monarchheels on 2010-10-17
I'm not sure if this will work for you, but it's quick and worth a shot.


[LIST=1]
[*]Open Terminal
[*]type **[FONT=System]alsamixer[/FONT]**
[*]look if all your levels are up. use the arrow keys on your keyboard to move across each one and increase as needed.
[*]hit **[FONT=System]esc[/FONT]** to exit
[/LIST]

---

### Post by papitu769 on 2010-10-17
> **monarchheels said:**
> I'm not sure if this will work for you, but it's quick and worth a shot.


[LIST=1]
[*]Open Terminal
[*]type **[FONT=System]alsamixer[/FONT]**
[*]look if all your levels are up. use the arrow keys on your keyboard to move across each one and increase as needed.
[*]hit **[FONT=System]esc[/FONT]** to exit
[/LIST]


I have just tried. They werent up. I put them up but dint improve the sound. It is still no sound.

Thanks anyway

---

### Post by mörgæs on 2010-10-18
Then trying this forum might help:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by papitu769 on 2010-11-04
> **mörgæs said:**
> Then trying this forum might help:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)
 
Thanks for de advise. I have been cheking without sucess. To be honest i will stop cheking anymore and go for windows. In the future i will try it again.

---

### Post by mörgæs on 2010-11-04
One last (and quick) test you could do is a live boot of 10.10. 

Else keep an eye on what **lidex** is posting - he knows about sound!

---

