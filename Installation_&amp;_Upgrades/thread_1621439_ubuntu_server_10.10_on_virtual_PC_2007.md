---
title: "ubuntu server 10.10 on virtual PC 2007"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by sanjayeds on 2010-11-14
Hi all,
 
I have installed Ubuntu server 10.10 on virtual PC 2007.My OS is windows XP.
I am totally new to linux OS, but wish to get acquainted and addicted to..
 
My installation is successful as followed the steps carefully and able to see the login prompt.
 
PROBLEM: I am seeing green vertical lines blocking the display partially..so, whatever i type gets buried underneath it..
 
Attached image for clarity..
 
Could some one help me on this.
 
Thanks much in advance,
sanjayeds.

---

### Post by sanjayeds on 2010-11-20
Hi all,
 
Finally i found solution myself..I list it here for the use of community
During boot, 
1. Press 'e' when you see the grub screen
2. Again press 'e' to edit the boot command
3. Move the cursor next to the 'quiet' word and add these phrases 'noapic nolapic vga=791'
4. Now press CTRL+X
 
Thats it. My green lines are gone and am able to see the cool ubuntu server login prompt with full display.
 
Next step is to find the right file and edit to make this boot settings permanent, so that i need not have to edit everytime on boot.If any folks know this already post me a reply

---

### Post by NightwishFan on 2010-11-20
run: sudo nano /etc/defalt/grub, place after "quiet", and then run sudo update-grub. Enjoy. :)

---

