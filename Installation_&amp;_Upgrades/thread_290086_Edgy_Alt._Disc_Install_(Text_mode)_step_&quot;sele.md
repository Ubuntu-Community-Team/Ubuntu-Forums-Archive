---
title: "Edgy: Alt. Disc Install (Text mode) step &quot;select and install software&quot; fails"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by akijikan on 2006-10-31
System specs:
AMD Athlon X2 4200 (2.2 ghz)
Biostar TForce 550 motherboard
2 GB DDR2-800 Corsair Ram
160 GB (Hitatchi?) SATA2 HD
ATi Radeon x800 XL w/ 256 mb RAM
Encore ENLWI-SG 802.11g (super g) - Atheros Chipset

I'm installing edgy (my first ever ubuntu installation) and I was unable to use the Live CD because of X Server errors originating with my ATi card.

I'm now using the Alternate disc and the Text Install.  Everything went okay until the "Select and Install Software" step.  I get a message saying it has failed and it takes me to the the install menu.  There I tried to select it again with the same results.  Then I proceeded to install grub and that was the end of the installation cycle.

I rebooted and I guess I have a ubuntu installed without any software since I can still load the kernel and get a command line interface.

Any suggestions as to how I can go about selecting and installing all of the software that was originally going to be installed as part of the process?  My wifi was configured and DHCP'd correctly so I have network access.

---

### Post by Elshadii on 2006-10-31
> **akijikan said:**
> System specs:
AMD Athlon X2 4200 (2.2 ghz)
Biostar TForce 550 motherboard
2 GB DDR2-800 Corsair Ram
160 GB (Hitatchi?) SATA2 HD
ATi Radeon x800 XL w/ 256 mb RAM
Encore ENLWI-SG 802.11g (super g) - Atheros Chipset

I'm installing edgy (my first ever ubuntu installation) and I was unable to use the Live CD because of X Server errors originating with my ATi card.

I'm now using the Alternate disc and the Text Install.  Everything went okay until the "Select and Install Software" step.  I get a message saying it has failed and it takes me to the the install menu.  There I tried to select it again with the same results.  Then I proceeded to install grub and that was the end of the installation cycle.

I rebooted and I guess I have a ubuntu installed without any software since I can still load the kernel and get a command line interface.

Any suggestions as to how I can go about selecting and installing all of the software that was originally going to be installed as part of the process?  My wifi was configured and DHCP'd correctly so I have network access.

Maybe you should try starting your graphical environment by issuing the command:

$ init 2

if you see errors talk about there is no x server then you need to install some things in order to do that from the prompt then you use apt-get install

---

### Post by meng on 2006-10-31
One wonders if the select and install software step failed because of a bad CD burn. That was my experience - when I reburned the CD it completed just fine.

---

### Post by Elshadii on 2006-10-31
> **meng said:**
> One wonders if the select and install software step failed because of a bad CD burn. That was my experience - when I reburned the CD it completed just fine.

good call 8)

---

### Post by akijikan on 2006-10-31
> **meng said:**
> One wonders if the select and install software step failed because of a bad CD burn. That was my experience - when I reburned the CD it completed just fine.

I need to get in the habit of checking my checksums...checked the image I downloaded earlier (with a download accelerator) and it was bad.  Thanks.

---

### Post by akijikan on 2006-10-31
well I downloaded without the accelerator and still CDC doesn't match.  I don't know what to do.

---

### Post by meng on 2006-10-31
Is this the md5sum you are checking against?
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso

---

### Post by akijikan on 2006-10-31
No I'm checking against:

549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso

the md5 sum provided by the download mirror I used ([http://ftp.osuosl.org/pub/ubuntu-releases](http://ftp.osuosl.org/pub/ubuntu-releases))

and I'm getting 9fe67ce319670301a35addf96d04b9ce.

---

### Post by meng on 2006-10-31
Whoops, sorry I posted the 6.06.1 md5sum by mistake. I can't explain why your md5sum is consistently wrong.

---

### Post by akijikan on 2006-10-31
I've now downloaded using both firefox and IE.  I'm going to try another mirror.

---

### Post by lerrup on 2006-10-31
If you have a console, a user and a network try sudo apt-get ubuntu-desktop, enter your password and then go and have a nice cup of tea while you wait.

---

### Post by akijikan on 2006-10-31
that sounds good.  only issue I see with that is that since my install disc came back faulty, then some installed aspects of the system might be faulty.

---

### Post by lerrup on 2006-10-31
I think it is probably worth a shot - in my experience if it installs it's most probably okay.

If by now you've downloaded a new alt-cd you can use that as the repository when you apt-get install.

good luck!

---

### Post by osarusan on 2006-12-01
I'm having the same exact problem, only this disc has installed on other systems... so it can't be the disc. Is there any other problem that could be causing this error?

---

