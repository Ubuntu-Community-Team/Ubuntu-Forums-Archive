---
title: "Enable nVidia Driver from Live CD"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NoFearDJB on 2010-04-22
Is it possible to install the nVidia driver from the live CD? I've enabled the driver through System->Administration->Hardware Drivers and it asks me to restart, which I can't do since I'm in a live session and it will just blow away my changes. I've attempted various things myself but would like to know if there is a correct way to do this. Thanks!

---

### Post by CryptoPaul on 2010-04-22
I don't know about being 'correct' - but I've used this method to check that the proprietary driver works.

At initial boot from the live cd add "nouveau.blacklist=true", without the quotes, as a boot option (f6) - we don't want the nouveau driver to load.

Then install the Nvidia driver through System->Administration->Hardware Drivers.

Enable ctrl/alt/backspace to kill x-server (system > preferences > keyboard > layouts > options)

Then kill x-server and it should restart using the nvidia driver.

Regards - Paul

---

### Post by cariboo on 2010-04-22
You could try logging out and then back in again.

---

### Post by NoFearDJB on 2010-04-25
Haven't tried either yet, but thank you for your suggestions!

---

### Post by Sylslay on 2010-04-25
Thanks for replay.
I was wondering some day aobut this.
THX again. I will try some time on my home desktop.
Just connet to wi-fi , enable nvidia drivers and logout and login.
2 months ago I just spnet one day to see if 3d comipiz is working on machine and install windows back for may freind. Becouse I'd like to see compiz working.

---

