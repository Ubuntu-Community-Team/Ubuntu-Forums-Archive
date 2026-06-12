---
title: "Getting me all set up... help"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by acorn22 on 2006-06-10
moved from [http://ubuntuforums.org/showthread.php?t=193709](http://ubuntuforums.org/showthread.php?t=193709) to here becasue it was no longer about GRUB alone.

Welcome , and please read the the afore mentioned thread (it's only one page) to see where I'm at.

---

### Post by acorn22 on 2006-06-10
Ok, I'm re-installing and it's gonna take a while (the cd-rom is a 4x)

While I'm waiting though, I just found an ATI Rage 128 PCI card. Right now I'm using a 64mb AGP. Can I use both? And have dual monitor support, not just mirror)


oh, and before, I picked the password " " (space), whick probably caused problems.

---

### Post by acorn22 on 2006-06-10
mabey it is hopless for me! (lol) No, I won't give up, I need a :-#ing coputer (my mac is going back cuz my school owns it).

Anyways, I used the same disk and everything for this re-install, and it says it couldn't find a file. So It made me re do the whole damn thing. I'm thinking it my 4 spin cd rom. Mabye I'll go steal one from my dad's "spare" computer for half an hour :-k

---

### Post by acorn22 on 2006-06-10
ok, all good and insalled. So I'm sitting here staring at bash. ```
lowell@ubuntu:
```

I typed startx but it says command not found

---

### Post by Scunizi on 2006-06-10
Try sudo /etc/init.d/gdm start

---

### Post by acorn22 on 2006-06-10
[QUOTE=Scunizi]Try sudo /etc/init.d/gdm start[/QUOTE]


same error. Command not found. More specificaly " /ect/inti.d/gdm" not found

---

### Post by zhoux on 2006-06-11
[quote=acorn22]same error. Command not found. More specificaly " /ect/inti.d/gdm" not found[/quote] 
maybe try
```
sudo /etc/init.d/kdm start
```

---

### Post by acorn22 on 2006-06-11
nope, /kdm diddn't work either

---

### Post by acorn22 on 2006-06-11
ok, when I type ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` it says 'xserver-xorg' is not installed. I dunno, I a guy asked it in a similar thread. Mabye that will help. 

I installed from the alternate cd becasue this computer has low memory.

---

### Post by acorn22 on 2006-06-11
I tried installing gnome by typing ```
sudo apt-get install gdm
``` I had to put my cd in and it went fine, but right at the end it says ```
unable to fetch some archives, mabye run apt-get install
```

---

### Post by acorn22 on 2006-06-11
despite the waringin of not using the desktop cd on a machine with 64 mb ram, i did it anyways, and now it all works fine. Now All i have to du is figure out ndiswrapper and get on the net! :D

---

### Post by acorn22 on 2006-06-11
ok, I got everything so far set up for ndiswrapper (I have a linksys wusb54g v4 card) and i am following these steps [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) but wen i get to make and that whole part, i get an error. ```
bash: make command not found
```

what is that about?

---

