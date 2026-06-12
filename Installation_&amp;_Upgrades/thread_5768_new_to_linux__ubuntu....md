---
title: "new to linux / ubuntu..."
date: 2004-11-22
forum: Installation &amp; Upgrades
---

### Post by erikhopp on 2004-11-22
i burned the ubuntu iso, installed it on my machine - it downloaded all the packages and seemed to install them.  when i restart i log in and all i get is a command prompt.  i see pics of the graphical interface all over the net and am wondering how i get there.

any help would be appreciated.

erik.

---

### Post by arctic on 2004-11-22
hi there.

it would be quite helpful if you would give us some information on your hardware (especially the graphics-card). it seems like your card settings need some minor tweaking to see ubuntu in all its splendour.

when you are at the prompt, please, after log-in, type "startx" and tell us, what information is given by the system. i think you will get some error messages referring to the x-environment which is controlled by xorgconfig. i am sure we can get your box up and running. the only thing you need is a little bit of patience and willingness to learn a bit.

:)

---

### Post by erikhopp on 2004-11-22
hey.  

thanks for the reply.

it is an ibm thinkpad with a rage mobility-m pci graphics card (i think)

when i type startx after i log in i get :

-bash: startx: command not found

thanks again for your help.

erik

---

### Post by erikhopp on 2004-11-22
here are the specs on my graphics processor: [http://www.ati.com/products/embedded/ragemobilitym/features.html](http://www.ati.com/products/embedded/ragemobilitym/features.html)

thanks!

---

### Post by Rui Pais on 2004-11-22
Bizare...

you can type:
**whereis startx **
to check if it is not installed or just a missing PATH environment.

give more information, like:
-did ubuntu installation gone well and nice till the end?
-do you have any error messages while boot?
-do you readed the howtos concerning the installations of ati drivers?
-can you apt (or have a working internet connection) in case you don't have X installed?

with a fast computer same times it's better reinstall if something was wrong at first trial. I install ubuntu in less than an 45 minutes... If things take long to fix you can try to re-install (you **sould** if something had gone wrong at installation time... unless you like aspirin taste:-D)

---

### Post by erikhopp on 2004-11-22
hi.  

ok.  i did a reinstall.

and this time i opted not to download the updates.

now i have the system working like it should, but i'll bee to update packages i assume.  

i have the synaptic package manager open, but i'm not sure which packages i should update - expecially since some of them ust break my graphics driver.

any suggestions?

thanks for the help.

erik

---

### Post by arctic on 2004-11-22
open synaptic. there you can set up your mirrors. after that is done, you can simply click on the updating tool. once this is done, you can view all packages ready for updating, selecting the personal filter tool &#8594;upstream on the left. read a bit what each package is good for and deactivate the files that you think  might harm your system.

i have ubuntu running on both desktops and notebooks and i have never had any problem after updating. i think that your problem simply arose from a bad "download" while installing. it is always safer to install the base system and then update everything. thus you can be sure that you have all relevant packages on your box.

i am sure that you can simply update all packages. once they are in place they won't go away automatically. they will only be gone once the superuser tells the package to go to hell. ;)

---

