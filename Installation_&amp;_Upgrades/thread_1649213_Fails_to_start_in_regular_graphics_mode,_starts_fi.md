---
title: "Fails to start in regular graphics mode, starts fine on failsafe graphics"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by m.dr on 2010-12-19
I installed 10.10 32-bit (via Minimal CD) on a Dell Optiplex and after install when it reboots - it gets stuck at the Xubuntu boot logo. Same thing happens with regular Ubuntu.

At the command output level it happens at the;
'Checking battery state ...'

However I can startup in 'Recovery Mode' and then then choose 'Failsafe Graphics Mode' and Xubuntu comes up fine. Same again with Ubuntu.

This machine has an AGP nVidia card with a VGA out and a s-Video out - but I have not had problems with installation and startup with 10.04. None whatsoever.

I am quite certain it is a graphics card issue as I have another exact box but without the graphics card.

However I have a 3rd different box as well with a dual-output PCI nVidia card (old yes) and 10.10 installs fine.

Any suggestions would be very helpful as i would prefer to run 10.10 on it.

Thanks.

---

### Post by Rubi1200 on 2010-12-20
Hi,
you could try the suggestions here:
[http://ubuntuforums.org/showpost.php?p=10191728&postcount=6](http://ubuntuforums.org/showpost.php?p=10191728&postcount=6)

---

### Post by m.dr on 2010-12-20
Thanks Rubi. I pretty much went the same route to boot up.

However, when I try and Install Additional Divers using the menu, no new drivers come up even after the search.

So unsure why the correct drivers are not getting installed in 10.10 while in 10.04 they are.

I wonder if I should try and mention it to the Ubuntu developers?

---

### Post by m.dr on 2010-12-20
Just wanted to mention I finally resolved this.

If someone faces the same issues you can use these two links on the nVidia cards for 10.10.

To start with you should look at Oldfred's startup notes:
[http://ubuntuforums.org/showpost.php...28&postcount=6](http://ubuntuforums.org/showpost.php...28&postcount=6) 

Then use these two notes:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Use the one above just for the command:
sudo apt-get --purge remove xserver-xorg-video-nouveau 

And then install new nVidia drivers using:
[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

Thanks.

---

