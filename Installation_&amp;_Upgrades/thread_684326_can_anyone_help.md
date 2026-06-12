---
title: "can anyone help?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by yazuki101 on 2008-02-01
I was hoping someone out there could give me a hand. If you were to look at my messages you would see I am having all kinds of issues installing all kinds of Linux based operating systems.

Now, I am not asking for a multitude of different OS suggestions, as I have researched plenty of distros and have no better luck with them (including but not limited to Fedora, ZW, Xubu). I have decided I am going to make my stand with Gutsy x64bit. 

Now as to what I am asking the ubunutu community, would it be possible for some to post (step by step) how to download and configure both my NVIDIA driver, and my 'X' server. 

I don't know that much about debian-based OS's in particular. Most of what I know, I will have to relate from my little bit of experience with the other OS's I have tried. (Mainly Zenwalk 5.0). So the more detailed, the better it would be I think.

Here are my specs:
-ASUS M2N mobo with NVIDIA nforce 430 chipset
-AMD x64 bit 2.01GHz Processor
-NVIDA gforce 8600 GT GPU
-3.0GB DDR2 RAM
-LG DVD/CD-RW
-320GB SATA HDD 
-80GB SATA HDD
My Connection:
-onboard network adapter
-wired ADSL connectio
-SIEMENS Gigaset SE567

---

### Post by oldos2er on 2008-02-01
Once you have Gutsy installed, go to (menu) System, Administration, Restricted Drivers Manager. and enable the video driver from there. You shouldn't need to download or configure anything beyond that.

---

### Post by yazuki101 on 2008-02-01
unfortunately I am unable to load the GUI, hence the need to do it in Recovery Mode

---

### Post by zvacet on 2008-02-01
Did you try in recovery mode 

```
dpkg-reconfigure xserver-xorg
```

and when it comes to drivers select **vesa** and continue to the end.Restart and you should have basic graphic.Let me know if it works and after that we  can go for your inernet connection wich has to be set.

---

