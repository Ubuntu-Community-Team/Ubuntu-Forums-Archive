---
title: "Trouble installing Skype - new user to Linux"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by nemov on 2010-03-01
Hi guys and girls, I come to you for your help! 

I've just bought a new laptop (Acer 3810T - which has a "Core 2 Solo Processor) - so I have installed Linux for the first time in my life.... Ubuntu 9.10-desktop-amd64.iso - so far so good, I'm very very impressed and the operating system seems to be working fine. I assume that I have chosen correctly the AMD64 version then. 

Fastforward to Skype installation, and I download the version (skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb) - which is the best match as far as I can tell from Skype's website. However when I come to install it, I get the follwoing error: Error: Dependency is not satisfiable: lib32stdc++6 (>= 4.1.1-21)

PLease note I am not an expert, so any simple advice or instructions you can give much appreciated!! 

Cheers, 

Nemov - UK

---

### Post by gradinaruvasile on 2010-03-01
Install the lib32stdc++6  package:

Open a terminal and type (copy-paste from here):

sudo aptitude install lib32stdc++6

---

### Post by nemov on 2010-03-01
It worked a treat thank you! 

For newbies like me, just follow the advice above from gradinaruvasile and if like me you have no idea what terminal is, follow the link that was provided in the reply above. Basically you have to open something called the Terminal, which in my version of Ubuntu could be found under Applications> Accessories , then just copy and paste the words: 

sudo aptitude install lib32stdc++6

then just hit enter. I then answered yes or "y" to everything, and then went back to my downloaded software from Skype website and opened that again to install the software...and this time no error message - just successful installation :o))

Brilliant, thank alot.

---

### Post by sveta_hoffman on 2010-11-17
Couldn't find any package whose name or description matched "lib32stdc++6"
Couldn't find any package whose name or description matched "lib32stdc++6"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
:confused:

---

### Post by Meepz on 2010-11-24
Try sudo apt-get update before u get that library. worked for me
Ps: this is my very first HELPING post and not one thats searching for help :D
<<< proud

---

### Post by jarviser on 2010-11-24
Why not just go to System - Administration - Synaptic Package Manager - then type in Skype, and mark for installation? Any required libs will be picked up. Worked for me anyway.

---

