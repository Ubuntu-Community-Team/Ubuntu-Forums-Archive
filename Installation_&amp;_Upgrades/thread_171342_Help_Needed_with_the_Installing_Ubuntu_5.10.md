---
title: "Help Needed with the Installing Ubuntu 5.10"
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by Muggi on 2006-05-06
When i install the Ubuntu 5.10 cd from Ubuntu i get the first screen where i can choose Desktop or Server but after that it loads some stuff in a dos like mode and then the screen goes black for a while and then it slowly turns white and when i try the Live version the same stuff comes up. CAN ENYBODY PLEASE HELP ME???.:confused: 

My Laptop is:
HP Pavilion zd8000 / zd8303ea
10 GB to install Ubuntu
ATI Mobility Radeon X600
ACPI Multiproessor PC
Intel(R) Pentium(R) 4 CPU 3.00GHz
512 Ram
:-(

---

### Post by killua_kd on 2006-05-06
where exactlly does the loading stop? try the no acpi option but I am not sure if it can do any good

---

### Post by Sef on 2006-05-06
These are possibilities of what it can be

1) Bad CD (if you have a pack, there may be a number of bad cds.)

2) Bad Burn

3) Did you md5sum the download?

---

### Post by BrandNuUbantu on 2006-05-07
How do you use "md5sum" ?

TIA
BNU

---

### Post by Sef on 2006-05-07
> How do you use "md5sum" ?

Here's a link to using md5sum.

[https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29]("https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29")

Basically it is this:

1) At the download site, there should be a link for md5sum. click on it and save the alpha-numeric line that comes up.

2) After finish downloading, 

a) open the terminal

b) cd download_location

c) md5sum name_of_program

d) After it brings up an alpha-numeric line.

e) that should be the same as the one from the site.  If not, redownload.

---

### Post by Muggi on 2006-05-08
thanks but i got it with whit this line:

server or
expert or
linux apci=off, hw-detect/start_pcmcia=false, vga=771
:D

---

### Post by Sef on 2006-05-08
Great!  It's always a good feeling to achieve what you wanted to accomplish.

---

