---
title: "Running Ubuntu10.4 on my old Win7 HDD in a slow 1.3Ghz1GRAM notebook?"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by lumumba2 on 2015-02-02
Hi friends

I intent running Ubuntu10.4 on an old 500GB HDD (with still an WIN7installation on it and huge new data, not completely backed up otherwise) on my slow OLD ULV Celeron 1.3Ghz 1GRAM notebook. 

1. IS JUST CHANGING THE HDDs and inserting an Ubuntu USBstick with BIOS starting the stick first ok?   
1. can I install Ubuntu directly on the HDD without damaging old data? A few free GBs are still available.  I.e. does in this case Ubuntu make a new partition automatically? or must I first run Ubuntu only from the stick, saving anything and than HDD installation of Ubuntu?

2. Can I than access the former data and files on the WIN7 disk from Ubuntu and save & transfer them?

[U]
**Taking Ubuntu 10.4 or the newest Ubuntu?**[/U]
Despite running excellently with Ubuntu 10.4 after installing Ubuntu 14... this slow notebook became extremely slow when opening two progs or 3/5 browser windows, so the many HDD accesses did slow it and obviously finally crash the HDD of my Ubuntu notebook. 

Possibly I can upgrade the notebook to 2GB RAM would this be sufficient with the new UBUNTU ? 
However, I was very happy with Ubuntu 10.4. it allowed me to run a TV USB stick HD film in a window on an external Monitor and simultaniously running  a youtube video just with a slow Celeron and 1GB RAM. An excellent performance on this weak system.

Any advice?  Did I forget any issue related to this?

Best regards
Patrice

---

### Post by Bashing-om on 2015-02-02
lumumba2; Hi Welcome to the forum .


Release 10.04 for the desk top is End-Of-Life and has no support, the server edition is EOL in 2 months.

Try:
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

1) Yes, there is that option in the installer "install along side of" .
2) Yes, ubuntu will recognize Windows and you can access Windows from ubuntu.

3) ubuntu is resource intensive so a lighter desktop (lubuntu for instance) will perform better .... and yes 2 Gigs of ram will certainly help. But the processor is still a bit slow. A lot depends on what graphics unit is installed.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mörgæs on 2015-02-02
Using the old 10.04 install please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

