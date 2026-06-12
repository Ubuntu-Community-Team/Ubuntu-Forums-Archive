---
title: "Uninstalled Beryl But Still SLOW!!"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Sparrow3D on 2008-06-08
Hi guys.. I am new to this forums, and im totally loving Ubuntu. But after searching for days on end i can not find any help on why my ubuntu is still slow. I have only install linux Ubuntu about 6 days ago and im totally blown away with the speed and power of linux. Iv heard so much about Linux but scared of trying it years ago. Now im worried of going back over to the dark side (MS-XP or Vista same thing kinda), cos im finding problem after problem that i could fix under MS.

My problems are, after installing Beryl or even CompizFusion. My system has become extremely slow. Moving windows around has become a chore, moving at about 10fps. Ive follow the directions.

So if somebody could direct me in the right direction to a more understandable process even for a dummy like me, i would be so great full. Iv also been following the online vids as close as possible. If somebody could explain the process such as Lennart Handsen [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
Please remember i do know about the command prompt under doss even though under Linux it's called the terminal? i think. But knowing doss doesnt help at all.

Specs:
Laptop: Acer Aspire 4310 64bit Capable
Processor: Intel Celeron 1.60GHz
Mem: Ram 1.Gig
Video Card: Graphics Mobile Intel(R) 945GM Express Chipset Family
Total available graphics memory 251 MB.
wireless: broadcom 802.11g network adapter.

Im certain its a nidiva board, cos the linux drivers were installed correctly.

I hope this is enough information..  Thanks so much guys. i wouldn't know what i would do with out you.

---

### Post by overdrank on 2008-06-08
> **Sparrow3D said:**
> Hi guys.. I am new to this forums, and im totally loving Ubuntu. But after searching for days on end i can not find any help on why my ubuntu is still slow. I have only install linux Ubuntu about 6 days ago and im totally blown away with the speed and power of linux. Iv heard so much about Linux but scared of trying it years ago. Now im worried of going back over to the dark side (MS-XP or Vista same thing kinda), cos im finding problem after problem that i could fix under MS.

My problems are, after installing Beryl or even CompizFusion. My system has become extremely slow. Moving windows around has become a chore, moving at about 10fps. Ive follow the directions.

So if somebody could direct me in the right direction to a more understandable process even for a dummy like me, i would be so great full. Iv also been following the online vids as close as possible. If somebody could explain the process such as Lennart Handsen [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
Please remember i do know about the command prompt under doss even though under Linux it's called the terminal? i think. But knowing doss doesnt help at all.

Specs:
Laptop: Acer Aspire 4310 64bit Capable
Processor: Intel Celeron 1.60GHz
Mem: Ram 1.Gig
Video Card: Graphics Mobile Intel(R) 945GM Express Chipset Family
Total available graphics memory 251 MB.
wireless: broadcom 802.11g network adapter.

Im certain its a nidiva board, cos the linux drivers were installed correctly.

I hope this is enough information..  Thanks so much guys. i wouldn't know what i would do with out you.

HI and welcome, the link you gave is a "how to" for beryl and ATI graphics. You should need no drivers for the intel graphics. What did you install? 
I have a laptop with intel graphics and all runs well so you may have installed something you do not need. If you installed via the terminal then you are in luck as you can open a terminal and use the arrow keys to review the commands you used to install.

---

### Post by Sparrow3D on 2008-06-09
Hello, thanks for your reply. Well i installed a ati driver as i didn't know my laptop wasn't an ati graphics board. So i un-installed it from the Software Sources menu. Iv also un-install (removed) the  xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx from the Synaptic Package Manager window. I found advice on another page as they just reinstall the OS. but that was about early last year since that was posted. Im very sure theres been improvements since then. 
Im using vista right now, as i miss my Ubuntu.. lol.

---

### Post by RESID3NT on 2008-06-09
you have an Intel board, not a nvidia.

---

### Post by Sparrow3D on 2008-06-12
yeah... but knowing what kinda board i have still wont get me out of this mess.  Iv only installed those those xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx Synaptic Package's. 
If anyone has a solution i will try my best to follow.
Thankyou

---

### Post by overdrank on 2008-06-12
> **Sparrow3D said:**
> yeah... but knowing what kinda board i have still wont get me out of this mess.  Iv only installed those those xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx Synaptic Package's. 
If anyone has a solution i will try my best to follow.
Thankyou

Hi and I would start by uninstalling the ati components that you installed. As I stated previously if you installed via the terminal then you can use the up arrow key to review the commands that you used. Then just replace the install with remove. If you installed via synaptic manager then jsut back track you installations steps.

---

