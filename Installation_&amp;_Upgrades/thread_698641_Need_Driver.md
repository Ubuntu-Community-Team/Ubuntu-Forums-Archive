---
title: "Need Driver"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by Techfizzle on 2008-02-16
Did a fresh install of linux :) I got all off the bugs worked out of it, yet the sound doesnt work. It worked when i had 98 on the copmuter so i know it's not the copmuter, i guess i need a driver. I have a dell optiplex gx110. It is a tower version. The sound,network,video,etc is in the mianboard. So in short words i need a sound driver!

---

### Post by Pumalite on 2008-02-16
Post:
lshw -C sound

---

### Post by Techfizzle on 2008-02-16
I ran it and it didn't detect the sound card. It's not a hardware issue as sound worked when i had 98 on here. The sound card is crystal chipset.

---

### Post by Pumalite on 2008-02-16
It would be easier for us to help you if you copied and pasted the output here.

---

### Post by Techfizzle on 2008-02-16
I cant really cut and paste becuase i am on a diffrent pc. It just didnt show up.

---

### Post by Pumalite on 2008-02-16
Well; you might want to try this:
sudo apt-get install linux-backports-modules-generic
Then run lshw -C sound to see if your card is recognized. You have to reboot.

---

