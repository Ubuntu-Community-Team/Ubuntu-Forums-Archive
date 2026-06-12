---
title: "How do I install NVidia Drivers?"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by EYALf on 2007-12-04
I'm trying to install NVidia 8400 GS drivers.

Have no clue how to do this.
I'm new to Ubuntu, please help ..

Also, How can I lower the speed of the mouse scrolling?

---

### Post by PmDematagoda on 2007-12-04
Open up the Restricted Drivers Manager in System>Administration, then install the Restricted Driver for your Nvidia card.

---

### Post by madnarg on 2007-12-04
I enabled the restricted driver for my Nvidia and when i restarted my screen went black.  I was able to press Ctrl+Alt+F1 and bring up terminal (i think?? sorry still very new at this) but had no clue what to do from there.

Any help would be greatly appreciated!

---

### Post by r3skyline on 2007-12-04
im needing some help on this as well. im running ubuntu 7.10 (NO INTERNET CONNECTION FOR THIS COMP THO!) i downloaded the drivers from nvidia. i have a 256 8600gt pci-e. when i log in as root and whatnot to install i get the "appears your running an X server....disable it before continuing"...however, when i do the ctrl+alt+F1, it still gives me that error. someone else told me at another forum that i have to use the command "sudo init3" to finish installing the drivers, but when i did that, it just gave me an unknown command error. i have no idea how to install these drivers and its really frustrating. note tho i have no internet connection and am typing this from my colleges computers so envy/any other method is out of the question because i cant download the dependencies/packages/w.e it is it needs. :(

---

### Post by YRU12 on 2007-12-04
I used envy which found the drivers. Before that I tried wine with the cd that came with the motherboard. Now getting this starter daemon error that says the system will start up right the next time. Envy does get the restricted drivers though. Running Gutsy Gibbon 7.10.

---

### Post by Drate on 2007-12-04
For the one who is stuck at the terminal try: ```
sudo dpkg-reconfigure xserver-xorg
```
oh and uh... good luck with that. ;-)  There should be some documentation or how-to's online.  The most important thing to watch for is going t be the driver and then later the vertical refresh rate.  If you want to skip the command above... you can always try: ```
vim /etc/X11/xorg.conf
```
then find the section labeled monitor and adjust the vertrefresh to whatever your monitor says (on the back usually if it's an old CRT like mine, look for some number in "hz", it *should*) be the vert refresh.

For the one with the daemon... bummer.  I have no idea.

for the rest of you crazy cats, perhaps Automatix would be of help?

---

### Post by KiwiDalang on 2007-12-07
>for the rest of you crazy cats, perhaps Automatix would be of help?

Maybe it would, but what on earth is it?

---

### Post by Pumalite on 2007-12-07
Download driver from here:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Place in /home/username
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /home/username/NVIDIA.run
Accept license
Let driver compile module
Let driver reconfigure xorg.conf
sudo /etc/init.d/gdm start
Make sure you have:
sudo apt-get install build-essential

---

