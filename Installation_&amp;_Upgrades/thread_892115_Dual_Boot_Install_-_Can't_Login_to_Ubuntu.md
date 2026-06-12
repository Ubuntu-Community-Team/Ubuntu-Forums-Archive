---
title: "Dual Boot Install - Can't Login to Ubuntu"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by civiccentral on 2008-08-16
So i used the Ubuntu wizard and did a dual boot install with Windows XP and Ubuntu. I can log into Windows fine. I can also load Ubuntu fine. I get to the user name with no problem and then I enter my password no problem. Then when its starting to load there seems to be an error box that pops up in red and grey in the top left corner of my screen, but it goes away to fast to read what it says. Then the screen goes garbled for a second and then goes back to the Ubuntu login prompt all over again. I guessing maybe a video driver issue, but I not well seasoned in Linux command line in order to diagnose. Any suggestion on what would cause this?

---

### Post by jualin on 2008-08-16
Try reconfiguring xorg. When you are in the log in window press CTRL-ALT-F3 and then log in and type > sudo dpkg-reconfigure xserver-xorg and follow the instructions.

---

### Post by jualin on 2008-08-16
I forgot to tell you how to go back, :). Press CTRL-ALT-F7 to go back to the Graphic User Interface. Hope this helps!

---

### Post by civiccentral on 2008-08-16
I reconfigured the package however it didn't remedy the problem.

---

### Post by jualin on 2008-08-17
Try running the command I suggested but choose the "Vesa"(generic) drivers instead.

---

### Post by the_baer on 2008-08-17
Hi all, well finally i decided to install Ubuntu as dual boot on my XP machine i have c drive which is partition into 2 and i have another drive i use to store files. i have installed Ubuntu from a cd and did the partition made windows very small all went well and good, until it reboot and then window log in come up and i cannot see option for the dual boot. i checked the boot menu and it is all about ubuntu and still cannot have the dual option; anyone can help please i need ubuntu for my work and i have to keep window for the wife./ thank you all

---

### Post by jualin on 2008-08-17
> **the_baer said:**
> Hi all, well finally i decided to install Ubuntu as dual boot on my XP machine i have c drive which is partition into 2 and i have another drive i use to store files. i have installed Ubuntu from a cd and did the partition made windows very small all went well and good, until it reboot and then window log in come up and i cannot see option for the dual boot. i checked the boot menu and it is all about ubuntu and still cannot have the dual option; anyone can help please i need ubuntu for my work and i have to keep window for the wife./ thank you all

Can you please go to the terminal and post the output of > sudo fdisk -l That command will list all the partition you have on the machine.

---

### Post by the_baer on 2008-08-18
My original installation went all fine using the actual Ubuntu CD. the BOOT.ini is fine and the boot from Ubuntu installation all good for data. What i did now i have Ubuntu installed again using .exe source (wubu) with all honestly this worked like a charm. If some one want to skip all the hard work and the sweat to get Window to accept other operating system i advise them to use this method.It basically creates Ubuntu as virtual machine and use all it's benefit.

Note: i am not on my desk now but i will give you the output of the fdisk.

---

### Post by jualin on 2008-08-18
> **the_baer said:**
> My original installation went all fine using the actual Ubuntu CD. the BOOT.ini is fine and the boot from Ubuntu installation all good for data. What i did now i have Ubuntu installed again using .exe source (wubu) with all honestly this worked like a charm. If some one want to skip all the hard work and the sweat to get Window to accept other operating system i advise them to use this method.It basically creates Ubuntu as virtual machine and use all it's benefit.

Note: i am not on my desk now but i will give you the output of the fdisk.

The Wubi installer doesn't create a Virtual Machine it creates a Hard disk image for Ubuntu inside of Windows. I agree with you Wubi installations are very user friendly since you can install or uninstall Ubuntu whenever you want using Windows control Panel, however performance is a little bit affected when using a Wubi installation, and also since Ubuntu is installed within Windows, if windows has a major problem then Ubuntu may be affected. 
The Wubi installer idea still pretty good since it gives users a good taste of what Ubuntu is without running Ubuntu in a Virtual Machine, however whenever you feel ready you should upgrade that Wubi installation to an standard installation which can't be affected by Windows.  If you ever have any questions with Wubi, the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide") is really good at answering many FAQs. Good luck and Welcome to Ubuntu!:)

---

### Post by the_baer on 2008-08-19
Thank you,

I would love to have Ubuntu on my system all alone, but i still have to have Windows (unfortunate for the wife). If wasn't for the amount of trouble to have it installed that would not be a problem. As i mentioned i have Ubuntu installed First (b4 wubu) on my window xp machine, but i couldn't get to the log in screen for the dual boot, i have followed all the hints and tricks even i re-install it twice to see if i missed something even so all was good and i was still unable to get to the boot option. i have 3 HDD on my system do you think if i install Ubuntu (full) on the slave would that solve the issue do you think?
Or if you have any better idea then the one that i was following i would be much appreciated to try it.

Thank you again
All Linux users and admin seems to be very nice. Glade to join this faboulus group.

cheers

---

