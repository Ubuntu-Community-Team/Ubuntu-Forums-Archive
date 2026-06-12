---
title: "xubuntu no display (ati x1250)"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by letsgojuno on 2008-04-28
hey im new, thought id try xubuntu on my laptop.
its a samsung r60 with the ati x1250 onbord graphics, i'm having the same problems others seem to have had with this card.

after the install I can't get the gui to run. i get 
> (EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

so far ive tried tried this tutorial 
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) 
but once i type "sudo aticonfig --initial" i get an error saying > Device Section "configured video device must have a driver line"
aticonfig parsing the config file failed
 

can anyone point me in the right direction, really wana get this setup

---

### Post by beN..87 on 2008-05-30
> **letsgojuno said:**
> hey im new, thought id try xubuntu on my laptop.
its a samsung r60 with the ati x1250 onbord graphics, i'm having the same problems others seem to have had with this card.

after the install I can't get the gui to run. i get 


so far ive tried tried this tutorial 
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) 
but once i type "sudo aticonfig --initial" i get an error saying  

can anyone point me in the right direction, really wana get this setup

I have the same machine, its a powerful little beast so why do you want to install xubnuntu? might aswell get ubuntu?

anyway below are the steps needed to install ubuntu 8.04 on a samsung r60plus (ATI Radeon 1250 Graphics / Aetheros Wlan 5007 )

my assumption would be its pretty much the same for xubuntu

the reason you're having problems is there is a I/O error in displaying the install menus on your screen when using the normal i386 CD

you need to use the ALTERNATE install CD (i386) --- that way the install menus can display on your screen


insert the alternate install CD
press F6
noapic (just type that and press enter to start boot - it adds it like --noapic to the boot paramater to prevent the I/O error and let the screen work.)

after install you will need to install the ATI graphics drivers 


i have outlined the whole process here - [http://ubuntuforums.org/showthread.php?t=800152&highlight=samsung+r60](http://ubuntuforums.org/showthread.php?t=800152&highlight=samsung+r60)

hope this helps -if it does feel free to press the button to thank me! :)

any questions just ask

---

