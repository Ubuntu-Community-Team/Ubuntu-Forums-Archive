---
title: "Nvidia driver installation"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by pandu_iitg on 2008-04-01
I have Nvidia Gforce Go 7200 graphix card....in my  LAPI  .. i HaVe recently installed ubuntu 7.10 ..now i want to enable my graphix card...so how can i do this..?? PLZZ  helP mE..:confused:

---

### Post by PmDematagoda on 2008-04-01
Go to the Restricted Drivers Manager in System>Administration>Restricted Drivers Manager and then enable the Nvidia driver.

---

### Post by pandu_iitg on 2008-04-05
ThaNk U SIr...But DIs IS Nt Working.....following message popups when i enable that  :-  
     The software source for the package 
        nvidia-glx-new  
       is not enabled....
the same thing happens when i try to install  GStreamer plugins...i m tooo upset...not able to listen songs  movies...pLZZZZ Plzzz heLP

---

### Post by manishr on 2008-04-05
You need to add a software source to your list of servers you pull updates from. 

System->Administration->Software Sources

You will have to check the box for "Proprietary drivers for devices (restricted)" checkbox.

---

### Post by StOoZ on 2008-04-05
you might want to check this:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by pandu_iitg on 2008-04-05
Thank u !! but i  already hv done thaT..After a lot of searches i came to know that for my Nvidia gFORCE go caRD i mUst hv To INstALl "nvidia-glx-new"..But ThErE is AgaIN A problem....:-s...when i try to intall that package [already downloaded ].. following error comes :-    ERROR : conflicts with the installed package "nvidia-glx"..aNd there no such package installed ..when i searched in synaptic   package manager...:confused::confused::confused::confused::confused::confused:

---

### Post by pandu_iitg on 2008-04-05
OOOOPs   ohhh my god...!!  stoooz  ...  i m nt able to install EV Legacy package tooo....:mad:  following error comes  :-  Error : dependency is not satisfiable : module - assistant   ..:(:(:(:(:(

---

### Post by pandu_iitg on 2008-04-05
now  i think  linux is nt made for noOOOooooobz  like me....i must hv to reinstall windows XP   [which,  i think is made for uneducated ppls]..:icon_frown::icon_frown::???::(:(

---

### Post by pandu_iitg on 2008-04-05
:confused:

---

### Post by PmDematagoda on 2008-04-05
If you are still willing to try using Linux(Ubuntu) then I can help you install the Nvidia drivers manually which may be more effective than installing them automatically.

---

### Post by Deety on 2008-04-05
Thanks Pm, you solved a problem for me with this post.
Deety

---

### Post by pandu_iitg on 2008-04-09
Yaaah ..thanks for ur  cooperation  pmdematagota [:)]...I really want to accept this challenge of installing Nvidia Card in My SucKIn LAPi [:P]..actually now i hv both OS in mY    laPi  [VisTa   And uBuntu ]..So tEll mE what To dO nEXt ..

---

### Post by piotrwoj on 2008-04-09
7200 with compiz work fine ;))

---

