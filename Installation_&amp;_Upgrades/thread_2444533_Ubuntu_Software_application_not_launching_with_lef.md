---
title: "Ubuntu Software application not launching with left click on Ubuntu 20.04 USB"
date: 2020-05-31
forum: Installation &amp; Upgrades
---

### Post by alvaro.ballesteros2 on 2020-05-31
Hi, 
I have just created a bootable USB drive on a 32 GB sandkisk unit.  The installations has been working, I used Rufus and clicked on persistent partition and give it 9 GB space.   Selected MBR partition sheme.

I have performed  all udates and upgrades, and it is working fine.

I have been detected two issues with two applications:  Ubuntu Software and also with installed Shotcut application.  

With the first one, it is only launched if I right click and select show details.   The Shotcut application does not starts even with the right click and show details.

Do you have any suggestion?  :confused:

Thank you.

---

### Post by Dennis N on 2020-05-31
'Show details' in the right-click menu takes you to an application's page in the Ubuntu Software Store. 'Ubuntu Software' in Ubuntu 20.04 is a snap package with the name 'snap-store'. If it doesn't start normally, remove it and install the package 'gnome-software' from the Ubuntu repository. You may have better luck with that and it looks the same to the user. After installing gnome-software, the icon will be called 'Software'. 

Remove Ubuntu Software
```
snap remove snap-store
```

Install Software 
```
sudo apt install gnome-software
```

---

