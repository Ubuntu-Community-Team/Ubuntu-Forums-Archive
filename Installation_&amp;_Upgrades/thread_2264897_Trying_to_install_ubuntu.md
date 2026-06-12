---
title: "Trying to install ubuntu"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by damion2 on 2015-02-11
I have been trying to install linux on my computer for a while and it just doesn't work, I get error screens all the time and I have tried different distros. I really need help and I'd love to have my computer run Linux instead of windows I do in fact want to completely replace my system with linux. I have tried to install it both ways LiveUSB & LiveCD.

here is the error I get:

[IMG]http://s6.postimg.org/8kiiap23l/IMG_0355.jpg[/IMG]

My computer Specs are:

[COLOR=#070F14][FONT=Verdana]12gb Ram[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]4 Disks 250gb - 500gb[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Nvidia Gforce Gaming MSI 750 ti[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Intel i5 4440 3.1 ghz[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Gigabyte motherboard b85m-d3h

Please help, thanks in advance.[/FONT][/COLOR]

---

### Post by damion2 on 2015-02-11
here are more images of errors with other distros.

ElementaryOS:
[IMG]http://s6.postimg.org/pj8648lwh/IMG_0351.jpg[/IMG]

Linux Mint:
[IMG]http://s6.postimg.org/59pjx2msh/IMG_0352.jpg[/IMG]

---

### Post by ubfan1 on 2015-02-11
Looks like a video problem.  Have you tried the "nomodeset" option when booting (the live media)?  (or edit the word in the grub boot commands on the linux line, there are many questions/answers about Nvidia driver setup). When you get it running with the noveau driver, you can then look around for proprietary drivers for improved performance (Additional Drivers under the launcher).  Maybe search for "hybrid" or bumblebee for other solutions for your type of hybrid video.

---

### Post by damion2 on 2015-02-11
ubfan1 you are a Saviour it was my video card after all. I am very thankful for your help. I posted this same question for 2 other sites and they were mean or said it was my kernel. 2 months suffering because I couldn't run linux and now I have made it, very honestly thank you very much. :KS

---

