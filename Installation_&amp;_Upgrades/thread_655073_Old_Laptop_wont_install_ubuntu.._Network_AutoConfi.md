---
title: "Old Laptop wont install ubuntu.. Network AutoConfiguration Failed..."
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-12-31
Ok heres my problem i have an old laptop that i want to install Ubuntu on badly.... ive tried the regular live cds... and those didnt work... i then thought to try the alternative non live cds... those didnt work.. and now ive tried the server install alternative cd.. i was going to then proceed to install gnome desktop through apt-get... the reason why all these cd's dont work for me is because my laptops system specs are low... however i had the most sucess with the server alternative install... but it wont finish because it needs a network connection and although i do have my linksys wireless pcmia card in the laptop i will get an error.. Network AutoConfiguration Failed..... and i dont know what else to try... my hard drive is 4 gigs roughly and i have i think 128 mb of ram and a pentium 1 process operating at i think 233 MHz...  please help! ive tried damn small linux and hate it.... vector linux wont install either.... any ideas? I love ubuntu......

---

### Post by foolsh on 2008-01-01
there is no dhcp server giving out ip addresss
this is not a show stopper

you can 
1.  manually enter the network info 
ie
address 192.168.0.2
broadcast 192.168.0.255 
netmask 255.255.255.0
gateway 192.168.0.1

2. skip this step and continue anyway

3.  use a wired connection for install not wireless

---

### Post by zvacet on 2008-01-01
You can try Xubuntu alternate CD.Download it from [here](http://www.xubuntu.org/get#gutsy).

---

### Post by Pumalite on 2008-01-01
If still having problems ( 128 RAM minus graphics):
Try Puppy or DSL

---

### Post by sent17inel on 2008-01-01
well sadly enough... my laptop doesnt have an ethernet port.... and  the install will hang when it says retrieving kernal or something....

---

### Post by angelsguitar on 2008-01-01
I have an old laptop computer similar to yours.  Mine is a Pentium II 266Mhz, 192 RAM.  Tried to install Ubuntu, Xubuntu and Fluxbuntu, but didn't like how it ran.  Finally I ended installing Puppy Linux.  It's a lightweight but incredibly complete distro.  I'm very happy with it.

I would recommend that you try out Puppy Linux.  The live CD is like 100 MB and, once installed in the hard drive, won't take a lot of space.

---

### Post by sent17inel on 2008-01-03
Okay i downloaded the ubntu 7.10 alternate install cd desktop version and two steps failed... one step was something called retrieving and instalilng packages or something... and the other was Network Autoconfiguration.... either way it sorta half finished because it will turn on and i can log in without a graphical user interface... now i think i should install gnome-desktop and go from there but i cant without an internet connection...  i have a linksys wireless internet pcmia card so how would i go about getting that to work? i did iwconfig and it only showed etho and something else... no ath0 connection so how do i get my wireless pcmia card installed?

---

### Post by Pumalite on 2008-01-04
Without being wired you'll have a rough time.

---

### Post by sent17inel on 2008-01-04
Well if someone knows what i would need to do i would much appreciate them if they told me how to go about doing it... im not afraid of a rough time....
And does anyone know why those two steps failed? or would fail?

---

### Post by sent17inel on 2008-01-04
bump

---

### Post by sent17inel on 2008-01-05
bump

---

### Post by tgalati4 on 2008-01-05
Your laptop is really too old for a workable Ubuntu installation.  Damn Small Linux will run fine on it.  It was suggested that you try it in an earlier post.  You can find it at damnsmalllinux.org.

---

### Post by Pumalite on 2008-01-05
Your installation gets stuck in trying to load a driver for your wireless and it wont work.

---

### Post by sent17inel on 2008-01-06
damn ok... sorry for posting in another thread... ive tried damn small linux and dont like it... ubuntu has always been my favorite but oh well... ill have to install windows 2000 again....    :(

---

