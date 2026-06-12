---
title: "upgrade from edgy to feisty"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by STREETURCHINE on 2007-04-24
well my upgrade seemed to go ok but i run into this little problem

> uncompressing linux... ok, booting the kernel.
bog1_init failed:setting screen size:cannot allocate memory
screen init failed

ubuntu 7.04 rex-desktop tty1

rex-desktop login

when i login i get 

> last login on etc etc 2007 on tty1
the programs included with the ubuntu system are free software
etc...etc...
ubuntu comes with absolutely no warrenty, etc etc
then i am back to rex@rex-desktop but still at the command line screen

if i type in startx
no screen found fatal I0 error 104

so i take it i have no driver install for the nvidia card, although when i reconfigured my xorg it asked about the card and driver .

so where do i go from here 

thank you

---

### Post by will_in_wi on 2007-04-24
Try to run ```

sudo dpkg-reconfigure -phigh xserver-xorg

```
from the command line. Then try startx.

---

### Post by STREETURCHINE on 2007-04-24
thanks that was one command i did not even think of ,i think i just about tried all the rest

---

