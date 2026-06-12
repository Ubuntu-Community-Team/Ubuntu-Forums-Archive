---
title: "Upgraded eeePC from 11.10 to 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by nariub on 2012-04-27
she reported a bork on rsyslog install, which I am not real worried about 
something about a debconf file that was busy or inaccessible, I will be more worried if this one crops up during my server upgrade but the eeePC ... not so much..

Online upgrade took forever, :) prompted me a couple of times and waited patiently for hours while I was ignoring it.

I have a custom unity-greeter background image, and this is still set in 
/etc/lightdm/unity-greeter.conf
but she doesn't seem to be using it.

Only problem so far, admittedly I did not get to play with it as much as I wanted over breakfast this morning.

So anyone want to explain the new unity greeter background thing?

---

### Post by nariub on 2012-04-27
[http://askubuntu.com/questions/121373/etc-lightdm-unity-greeter-conf-file-missing/121381#121381](http://askubuntu.com/questions/121373/etc-lightdm-unity-greeter-conf-file-missing/121381#121381)

dang it, they dont use the greeter.conf file anymore

and you have to be the lightdm user now..
[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594)

sudo xhost +SI:localuser:lightdm 
sudo su lightdm -s /bin/bash 
gsettings set com.canonical.unity-greeter background '/path/to/the/wallpaper.png' 
exit 
exit


and you have to turn off the 'new feature' to display the users background

sudo xhost +SI:localuser:lightdm 
sudo su lightdm -s /bin/bash 
gsettings set com.canonical.unity-greeter draw-user-backgrounds false 
exit 
exit


I will try this, but I gotta say,  I prefer config files.

---

### Post by newbemac on 2012-04-27
I have an eeepc also 4 gig model (901) I have ubuntu 10.04 installed I have tried to install 11.04 and 11.10 with no succsess I think there is not enough space I'm not sure, I have reinstalled ubuntu 10.04 and it runs fine.
I'm leaving well enough alone

---

### Post by nariub on 2012-04-28
my apologies, but you have 4G of HD?
I have fit Ubuntu into small places before, (USB sticks) 
but it will have to be stripped down.. 

good luck

---

