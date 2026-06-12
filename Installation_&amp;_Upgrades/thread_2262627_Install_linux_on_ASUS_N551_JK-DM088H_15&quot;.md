---
title: "Install linux on ASUS N551 JK-DM088H 15&quot;"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by yoramdavid on 2015-01-26
Hi all,

I need to buy a new laptop as my old one passed away.
I am interested in W-ASUS N551 JK-DM088H 15"
I went to the shop with a bootable usb linux mint distro that I used on my old laptop.
With the assistant of the shop we tried to run the live usb. No success.
The partition where the windows 8.1 is installed is not visible under windows file managet.
We deactivated fast boot but did not find where to deactivate safe boot.
We managed to load the menu from the live usb, but after selcting "start Linux Mint", there was a bkack screen.

I need to be 100% sure I will be able to install linux on this machine before I buy it. In dual boot with windows 8.1 until guarantee runs over. Just in case.
Can I buy this laptopIs there any chance I will not able to install linux?

Thanks a lot for any help.

---

### Post by kc1di on 2015-01-26
Hi yoramdavid, 

As I see it with that machine, the problem with the blank screen stems from the dual video cards present. Nvidia is sometime problematic  and you'll need to boot it using the nomodeset boot parameter.  info[ here]("http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso"). 

You may still have to disable safeboot though. 
Good luck :)

---

### Post by yoramdavid on 2015-01-26
> **kc1di said:**
> Hi yoramdavid, 

As I see it with that machine, the problem with the blank screen stems from the dual video cards present. Nvidia is sometime problematic  and you'll need to boot it using the nomodeset boot parameter.  info[ here]("http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso"). 

You may still have to disable safeboot though. 
Good luck :)

Thank you for your reply!

Nearly all the computers I saw had nvida.
If I boot with the nomodeset parameter, do I loose any performance, will I not take advantage of all the graphic capability?
What would be a good graphic chipset for linux, then?

David

---

### Post by ajgreeny on 2015-01-26
It's usually a case of first boot only with nomodeset, then using that GUI which may be low resolution, install the nvidia proprietary driver and reboot again; this second boot should not need nomodeset as the new driver should do all necessary graphics for you.

---

### Post by kc1di on 2015-01-26
The Nvidia Graphics cards work well with Linux once you get them install, 
the problem come in the fact that the drivers for them are not open source.  that is they are not released so that
ubuntu or any linux distro can modify them.  
There is an open source driver for nvidia call nouveau But it only works with some of their older cards and not well with some of the newer ones.
when you add nomodeseting it will default to a generic driver that works but at low resolution. 
after you install you will have to install the correct nvidia driver for your particular card. it's not that difficult. 

Good luck .

---

### Post by yoramdavid on 2015-01-26
Thank you both.

Within the very limited choices I have here, it is the laptop that seems best fit my requirements.

But... if the nvidia nouveau driver does not work with this new card, I have a big problem.

David

---

### Post by kc1di on 2015-01-26
it's really not a problem as ajgreeny  said once you install the correct driver it should work fine. 
the driver you will need is usually available in the repositories but can't be install on boot up 
you can install it by going to the additional driver tool found in Ubuntu Software Center /Edit tab /Software Sources /Additional Driver tab.  
then it should recommend a nvidia driver for your card and you install it from there. 

If the drivers there are not new enough there is a ppa that can be installed that has newer but untested versions available. 
in any event one of them should work, 
of course that machine also I believe has an Intel HD graphic card that should be able to be supported out of the box. 
just not sure how you select it on that model.

---

### Post by yoramdavid on 2015-01-28
Thank you.
I think I will buy it and have a try.
I can always give it back to the shop if I do not like it.

---

