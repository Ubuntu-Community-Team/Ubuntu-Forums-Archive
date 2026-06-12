---
title: "Play .DAT files in Ubuntu 11.04"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by reddylast on 2011-07-05
Hi,

Is there any way play .DAT files (VCD files) in Ubuntu. Whenever I try to play .DAT files I get some errors and even ubuntu does't allow me to copy .DAT files to any Ubuntu folder from CDs.

Regrads,
Reddy

---

### Post by nomko on 2011-07-05
Which program did you use? Normally Vlc can play anything without problems. Did you try Vlc?

---

### Post by reddylast on 2011-07-05
Yes, I tried to play it on VLC, Mplayer and Xine, but none of them are supporting these files. More weird things are happening when I'm trying to copy them. is this mean Ubuntu can't read/copy .DAT files ?

---

### Post by nomko on 2011-07-05
In your first post you mention it is a vcd file. Normally i think you should have a mpg file as well. A .dat file is normally a data file. Try to locate a mpg file or something like that.

---

### Post by agkrish on 2011-10-27
there are some VCDs which come only with .dat files + 1 .exe file. These run on Windows & VCD players. However am neither able to play or RIP them using Transcoder, v0.0.5 or Transmageddon v0.16 or RipOff 0.8.3 or dvdRIP 0.98.11. VLC could not read the file.

---

### Post by kareempharmacist on 2011-11-10
install k3b
choose tools then choose Rip Video CD and Enjoy
other option install vcdxrip with the following command 
```
sudo apt-get install vcdxrip
```
then go to your home directory ....your home directory not anywhere else then type 
```
vcdxrip --nofiles -v -p
```
again enjoy

---

### Post by kareempharmacist on 2011-11-10
I forgot to mention ..you will find the files in your home directory

---

### Post by xsyne on 2013-01-06
Thank you for the information about **vcdxrip** :) Works perfectly!

---

