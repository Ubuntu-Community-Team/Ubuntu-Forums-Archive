---
title: "If you have an HP help:"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by twist2b on 2007-11-25
OK, well ive successfully put ubuntu 7.10 on my hardrive and i can use vista becuase im dual booting. BUT

i cant get ubuntu to work.. im not even going to try 7.4 anymore cuase i know it doesnt really work with hps but 7.10 is not working resolution wise.... when runnung live cd mode i have to change the resolution to get it working at all and then when its on my hard drive it just boots then doesnt work at all after that becuase it black screens and ive pushed buttons........ i forgot what peeps said i think it was control F2 or somethign and that doesnt work..... im giving up :P if anyone can help i would appreciate that!

---

### Post by LaRoza on 2007-11-25
What error messages are you getting?

What graphics card do you have?

What have you tried?

---

### Post by Pumalite on 2007-11-25
If you didn't allocate space for Ubuntu first from within Vista, you have to start again.

---

### Post by twist2b on 2007-11-25
the dual boot was fine... i had plenty of space for it, 20 GB and i pre-setup the space with vista. The problems basicly only the graphics card is not working with ubuntu im guessing. i get a BIOS BUG 83. nowones been able to find a solution so far as i know.

---

### Post by Pumalite on 2007-11-25
As LaRoza asked: what card is it?

---

### Post by twist2b on 2007-11-25
Im very sorry, im tired so i missed a few things. but yes i have
NVIDIA GeForce Go 6150
oo and i messed with sudo configure or something like that i lost the code and now my graphics card is completely dead even for Vista... whats the exact code so i can fix that on GRUB cause id like vista games to work again :P oo and no i only messed the graphics card up recently after trying a ton of things...

but whats the exact code again i relaly really need to know.

---

### Post by Pumalite on 2007-11-25
NVIDIA GeForce Go 6150
I'm not sure it's supported. I don't use Windows. What 'code' are you talking about.
(you might need 'Legacy' drivers. Not sure)

---

### Post by twist2b on 2007-11-25
i found the code:
dpkg-reconfigure xserver-xorg
or its
sudo dpkg-reconfigure xserver-xorg

anyways yea then i have to choose Vesa THEN startx
(in grub)
but yea cuase i changed it off of VESA because i was just testing it withought putting it back.
and what are legacy drivers? do i put them on a cd while im downloading Ubuntu? also wheres a list of all the supported graphic cards?

---

### Post by Pumalite on 2007-11-25
Look in the Nvidia site what kind of driver your card needs.

---

### Post by twist2b on 2007-11-25
yea but if i cant even boot Ubuntu... how can i implement it?

---

### Post by Pumalite on 2007-11-25
Are you now in Ubuntu with 'vesa'?

---

### Post by twist2b on 2007-11-25
> **Pumalite said:**
> Are you now in Ubuntu with 'vesa'?

i havnt done that yet... though i started out with VESA... but let me fix that first and ill be back.... though i found out you can update the card and such in recovery mode which is awsome but i cant get my internet to work either so that wont work otherwise i would be out of this sitch... unless you guys know how to my internet to work..... (Broadcom 802.11b/g WLAN)

---

### Post by gdselzer on 2007-11-25
What model computer are you trying to install this on?  I assume it's a laptop, but what model?

---

### Post by twist2b on 2007-11-25
i have a pavilion tx 1000
and i tried dpkg-reconfigure xserver-xorg then choose VESA
it loaded up good and fine and i could use ubuntu BUUUUUUUUUUUTTTTTTTTTTTT when i shutdown and turned it on again none of the settings i added saved and so when i booted the OS it just didnt work again......

---

### Post by gdselzer on 2007-11-26
Try sudo dpkg-reconfigure xserver-xorg.  If you only entered dpkg-reconfigure xserver-xorg you ran it as a non-root user.

With that said, I'm a little amazed that you're having these problems.  My nvidia geforce go 6150 ran right out of the box.  Maybe you should try wiping the partition and re-installing.  Sorry to not be of more help.

---

