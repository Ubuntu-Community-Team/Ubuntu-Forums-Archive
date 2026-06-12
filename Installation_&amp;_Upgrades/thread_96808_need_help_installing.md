---
title: "need help installing"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by guardian65 on 2005-11-29
when i boot up with the ubuntu 5.04 install disc it will start a couple lines then reboot and start over. what am i doing wrong?

---

### Post by linbetwin on 2005-11-29
Have you checked in you BIOS to see if CD-ROM is the first boot option?

---

### Post by guardian65 on 2005-11-29
yes i did. set that first.

---

### Post by linbetwin on 2005-11-29
Do you have another OS installed? What do you mean when you say it starts over? Doesn't it boot into your installed OS?

---

### Post by linbetwin on 2005-11-29
Also, your CD may be corrupted.

---

### Post by guardian65 on 2005-11-29
i have xp installed. it reboots and brings up the initial ubuntu splash screen with the install options.

---

### Post by linbetwin on 2005-11-29
It reboots when you press ENTER to install Ubuntu?

---

### Post by guardian65 on 2005-11-29
yes. it'll run 2 lines and reboot back to the cd.

---

### Post by linbetwin on 2005-11-29
As I said earlier, maybe you have a corrupt CD. What software did you use to burn it?

---

### Post by guardian65 on 2005-11-29
i didn't burn it. it's an ordered cd.

---

### Post by linbetwin on 2005-11-29
Your probably received more of them. Try with another one.

---

### Post by guardian65 on 2005-11-29
i only got one. i'm going to play with it some , see what i can do.

---

### Post by linbetwin on 2005-11-29
Are you sure you have the right CD for you processor? Some people here reported they have ordered i386's and received PPC's, or vice-versa.

---

### Post by guardian65 on 2005-11-29
ok..got it installed. now i have a new problem. the screen resolution only gives me 640x480. how do i fix it?

---

### Post by Xian on 2005-11-29
[QUOTE=guardian65]ok..got it installed. now i have a new problem. the screen resolution only gives me 640x480. how do i fix it?[/QUOTE]
Run the following command and set the default resolution.

$ sudo dpkg-reconfigure xserver-xorg

---

