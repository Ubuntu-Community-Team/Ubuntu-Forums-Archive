---
title: "Installation Hangs"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by snowjunkie on 2005-08-28
Hi,

I have a Dell Inspiron 6000 laptop.  The LiveCD works just fine.  So I decided to install Ubuntu on it (and be able to select xp still from the menu).

I've created partitions as explained in [http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html) and started the ubuntu installation...

It gets right through to "Configuring Apt..." "Setting up primary installation respositry" 25%.

I've tried installing twice now and it stops at this point every time?  Is it just that this is a particularly lengthly procedure?

When I reboot the laptop, it doesn't boot xp anymore either which is a bugger.

Please help!

---

### Post by essexman on 2005-08-28
[QUOTE=snowjunkie]Hi,

I have a Dell Inspiron 6000 laptop.  The LiveCD works just fine.  So I decided to install Ubuntu on it (and be able to select xp still from the menu).

I've created partitions as explained in [http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html) and started the ubuntu installation...

It gets right through to "Configuring Apt..." "Setting up primary installation respositry" 25%.

I've tried installing twice now and it stops at this point every time?  Is it just that this is a particularly lengthly procedure?

When I reboot the laptop, it doesn't boot xp anymore either which is a bugger.

Please help![/QUOTE]


You have a fast machine, faster that mine, and so 'long' to you is going to be a shorter amount of time than is is to me.  The partition creation guidance you have followed looks good to me.

It may be a problem with the installation disc, if you have access to another machine and can burn a disc, it might be worth downloading a standard 5.04 install cd.

Have you tried to erase and reformat the partition you are installing into?

I havn't tried the live CD and I don't know if it gives an option to boot into windows, like a rescue CD.

Have you backed up you windows data?

---

### Post by snowjunkie on 2005-08-28
Hi,

It was a standard install disk I was using.  I downloaded the iso after playing around with the LiveCD.

I haven't backed up my windows data.  There was nothing important on it as I mainly use it for vnc'ing unto other boxes.  Or working on code from source safe.  So that's ok.

One thing that was different from the tutorial is that the dell laptop has like a hidden partition on it with the dell restore files on it (2.5 GB).  When I created a partition for Ubuntu, it squeezed it inbetween the active partition and the hidden Dell partition.  Would that make a difference?  I didn't think it would.

I'm going to try to burn the image again to rule out a faulty disk.  I might go from scratch and remove those partitions and start from the beginning.

Thanks,

Alastair.

---

### Post by snowjunkie on 2005-08-28
Just a quick update on this.  I reburnt the image on a new disk and it flew past the section it kept sticking at.  Installed GRUB no problem and I'm now in the second stage of installation.

Thanks for your help.

Update:

Ubuntu up and running.  In fact I'm editing this post from it now.  Still haven't tried to see if xp boots though!  ;-)

---

### Post by essexman on 2005-08-28
[QUOTE=snowjunkie]Just a quick update on this.  I reburnt the image on a new disk and it flew past the section it kept sticking at.  Installed GRUB no problem and I'm now in the second stage of installation.

Thanks for your help.

Update:

Ubuntu up and running.  In fact I'm editing this post from it now.  Still haven't tried to see if xp boots though!  ;-)[/QUOTE]
This is good news.

XP should boot ok; if there is no line in the grub menu, come back and we should be able to make one.

---

### Post by snowjunkie on 2005-08-28
Hi,

xp works ok!

I have also set up wireless on ubuntu and it seems to work very well.  Everything seems to work well.  I'm impressed.

Thanks for your help.

Alastair.

---

### Post by essexman on 2005-08-29
[QUOTE=snowjunkie]Hi,

xp works ok!

I have also set up wireless on ubuntu and it seems to work very well.  Everything seems to work well.  I'm impressed.

Thanks for your help.

Alastair.[/QUOTE]
Well done!

Keep posting.

---

