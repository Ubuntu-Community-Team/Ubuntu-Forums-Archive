---
title: "Xserver wont start"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by lowebb on 2006-11-02
Ok upgraded from Dapper to Edgy and as I expected it didnt go smoothly. Xserver wont start running

sudo dpkg-reconfigure xserver-xorg didnt help at all and thats whee my knowledge ends.

When I tr to boot it simply says Xserver didnt start; asks if I wanna see reports and then does zip. I can get in through recovery but i've no idea how to fix it. HELP!!!!

The Fatal Error is "no screens found"

---

### Post by PrinceArithon on 2006-11-02
Try sudo apt-get install xserver

It seems to be a suggestion in the upgrading thread that has been stickynoted at the top of the page

---

### Post by lowebb on 2006-11-02
tried that, 'xserver-xorg is already installed' 

I'm going to try and remove it and reinstall it. Anymore thought?

---

### Post by lowebb on 2006-11-02
I dont believe that I am the only person with this problem, come on anyone got an idea

---

### Post by lowebb on 2006-11-02
To ensure atleast i am being helpful the solution to this problem was to reinstall the savage driver for my video card

sudo apt-get install xserver-xorg-video-savage

---

