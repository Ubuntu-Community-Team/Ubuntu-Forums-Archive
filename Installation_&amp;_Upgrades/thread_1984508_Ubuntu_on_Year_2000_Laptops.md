---
title: "Ubuntu on Year 2000 Laptops"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by Living2007 on 2012-05-21
I have just recieved a tone of old laptops from a company scrapping their old hardware. I put Ubuntu 4.10 on one of them, due to requiring 128MB of RAM to run effectivaly.
 
NOTE: The machine has 256MB RAM.
 
I wanted to update the repositroies (and knowing that it is no longer supported), they don't work. Is there a list where I can update to a repository that still works for updating (and maintaining) the 4.10 version?

---

### Post by jadtech on 2012-05-21
> **Living2007 said:**
> I have just recieved a tone of old laptops from a company scrapping their old hardware. I put Ubuntu 4.10 on one of them, due to requiring 128MB of RAM to run effectivaly.
 
NOTE: The machine has 256MB RAM.
 
I wanted to update the repositroies (and knowing that it is no longer supported), they don't work. Is there a list where I can update to a repository that still works for updating (and maintaining) the 4.10 version?

you might be able to install Lubuntu 11.04 on them ram need is 256mb

---

### Post by mastablasta on 2012-05-22
Lubutnu 12.04 is the latest LTS and should work fine with 256MB ram. Though you might need to use alternate install disk (text based installer) to install succesfully..
 
Other options you might want to explore:
Debian LXDE
Chrunchbang (based on debian stable, uses Openbox, but old XFCE version is good on ram consumption =80MB on idle)
Bodhi Linux (uses E17, needs 128MB ram and 800Mhz CPU) based on Ubuntu
Puppy linux (has a version with Ubuntu repositories)
Slitaz (can run on 64MB ram)
Tiny core ( very "basic" OS, but can run on a really low ram)
...

---

### Post by Living2007 on 2012-05-22
What is Lubuntu, or more likly, what is the "L" short for.
 
My priority is to keep the Gnome interface as I am more familiar with it and it's accmpling features.

I've also noticed that Ubuntu 4.10 does not allow the option of removing extra software (ie. evolution and Xchat) without removing "ubuntu-desktop". Will Lubuntu allow for removal of "bloatware" just so I can run all terminal releated programs and the Gnome interface?

---

### Post by mastablasta on 2012-05-23
> **Living2007 said:**
> What is Lubuntu, or more likely, what is the "L" short for.
 
My priority is to keep the Gnome interface as I am more familiar with it and it's accmpling features.

 
it stands for LXDE. (ight X desktop environment (so no it' snot Gnome). If oyu like Gnome then 10.04 might work ok with 256MB ram but XFCE on a lighter distro would be fine. XFCE is actually like light Gnome (uses GTK libraries mostly). and fully configurable. it is also very intuitive. for example most stuff you need or want to change is just right click on it and select propperties.
 
> 
I've also noticed that Ubuntu 4.10 does not allow the option of removing extra software (ie. evolution and Xchat) without removing "ubuntu-desktop". Will Lubuntu allow for removal of "bloatware" just so I can run all terminal releated programs and the Gnome interface?

yes it allows to remove it or you can use minimal install iso and install basics and then add only what you need. : [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
for example you can install only DE if you do:
sudo apt-get install LXDE
 
for Lubuntu
sudo apt-get install lubuntu-desktop
 
second command will install full desktop including all programmes and such (that you call bloatware :-P ). while the first one will only install desktop environment.
if you are running terminal related programmes why do you need gnome interface then? wouldn't it be better to go with something lighter like only a windows manager (e.g. IceWM).

---

