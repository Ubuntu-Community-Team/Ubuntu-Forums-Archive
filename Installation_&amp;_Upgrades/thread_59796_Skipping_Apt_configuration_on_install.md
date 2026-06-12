---
title: "Skipping Apt configuration on install"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by gordonbp on 2005-08-25
When I install Ubuntu, the "configuring Apt" section takes over three-quarters of an hour. The reason for this is that  my router uses DHCP and is not accessible to edit (it is supplied pre-configured by my Wife's Company who also pay the broadband costs <VBG>) and after installation, I have to edit the resolv.conf file to add my ISP DNS. Of course that is not there during install, so that's why the "configure apt" part hangs for so long.

So my question is, is there a key (or something) I can press to skip the "configure apt" stage?

thanks

---

### Post by akcanadianeh on 2005-08-25
On the networ detection screen, select "Do not configure network". (If the DHCP has already gone through, click go back to get to that option) This way, it will only configure the APT on the CD, and not over the network since it has no network connection configured. Once the system is installed, setup the network connection in System > Administration, "sudo gedit /etc/apt/sources.list", uncomment the lines for the repositories you want (all non-universe repositories are the defaults, add the universe ones if you want), and you're good to go!

---

### Post by gordonbp on 2005-08-25
I don't recall seeing an option "not to configure network" on the install...... I'll have another look!

Thanks!

---

### Post by Gordonbp531 on 2005-08-29
[QUOTE=akcanadianeh]On the networ detection screen, select "Do not configure network". (If the DHCP has already gone through, click go back to get to that option) ![/QUOTE]

tried that - didn't work - the install STILL tried to configure network repositories. I suppose the only answer is to disconnect from the router before installing.....

---

