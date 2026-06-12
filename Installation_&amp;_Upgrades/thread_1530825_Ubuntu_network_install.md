---
title: "Ubuntu network install"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by winxpuser on 2010-07-14
Hello,

On my network I have 2 computers

1 Desktop Machine that has Ubuntu and WinXP on it
1 Laptop that has a broken video card in it and no OS on it as of right now.

What I would like to do is install ubuntu onto the laptop and use it as a server for my desktop machine but since I cannot see the screen on the laptop I cannot install ubuntu onto it in the conventional way and so I am thinking a network install would work but most of the guides I have seen so far do not really fit my situation so I was hoping someone here had done something similar and could share their knowledge with the rest of us facing the same situation.

To clarify EVERYTHING would have to be done from my desktop machine since I cannot even see the screen on the laptop and even using tv out on the laptop is not an option in this situation so am I just out of luck or can I still get this working by some miracle and if so, how ?

TIA,
Dave

---

### Post by ghost_may_cry_ on 2010-07-14
does you laptop only have a tv-out or does it hav a vga port aswell?
you can connect you desktop monitor to to vga port (if the monitor uses vga)

EDIT: thats if the vga port still works

---

### Post by winxpuser on 2010-07-14
I have tried connecting my desktop monitor to the laptop using the vga out (it has s-video, and dvi outputs as well) and have tried all methods but since the problem is with the video card itself the display is the exact same as it is on the laptops monitor (ie. un useable) so as I said everything will have to be done from the desktop. I am not sure if the preeseeding method would work or not for me since the install would have to basically be 100% automated (ie put unbutu and my preseeding cfg file on a usb stick and put it in my laptop and press the power button and walk away and have it installed that way) but I am sure there is atleast 1 or 2 steps that I would need to do manually so not sure this would work either but I am certainly open for suggestions. 

Thx Again,
Dave.

---

### Post by iponeverything on 2010-07-14
grab a cheap adapter to put the laptop drive into the desktop system and then do the server install onto the drive. Then transfer the drive back to the laptop.

---

### Post by winxpuser on 2010-07-14
Thanks but I am aware I could do that but I am wanting to do this without spending any cash as times are tight around here (had to pay for my aunts funeral long unrelated story) which is why I am re-servicing the laptop in the first place instead of just scraping it and getting a  new one.  Any other suggestions.

Dave

---

### Post by winxpuser on 2010-07-15
I managed to get it installed after hours n hours from a usb stick and basiclly just using the keyboard to fill in the values I needed to get the install to finish which was a PITA considering I had no idea where I was typing and if I was making typing errors because I had no screen to look at but the point is it's installed and I even managed to upgrade it and install a ssh server on it so I can atleast now administrate it from my other computer which does have a screen so thank god for that. Anyway onto the next item (securing ssh).

Dave

---

