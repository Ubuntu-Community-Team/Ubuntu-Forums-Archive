---
title: "Installation problem: Gnome?"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by pauljwells on 2005-07-27
I've just installed 5.04 on my HP media centre PC (I already have a working install on a mac)

I get to the login screen, can emter username and password but then the system hangs.

I can login to failsafe terminal, but I get a screen about 10 lines deep and once I've typed past the end it hangs. The text doesn't scroll.

There are no error messages during bootup and the install seemed to go OK.

I have an ATI X600 graphics card running dual monitors. Could the problem be related to this?

Many thanks in advance for any hints

---

### Post by Shiven on 2005-07-27
can you paste the output of dmesg & cat /var/log/Xorg.0.log (preferably on other sites linked across, but pasted here will do)?

and is your /etc/X11/xorg.conf file correct? (post that too if you're unsure ^-^)

never hurts to try everything... ^-^

---

### Post by pauljwells on 2005-07-27
[QUOTE=Shiven]can you paste the output of dmesg & cat /var/log/Xorg.0.log (preferably on other sites linked across, but pasted here will do)?

and is your /etc/X11/xorg.conf file correct? (post that too if you're unsure ^-^)

never hurts to try everything... ^-^[/QUOTE]
 How?
I can only get to the root command line. I can cat xxx | less or cat xxx > file, but I don't know how to get this file even onto another machine on my network. ubuntu doesn't have ssh in the base install so can i even login from another machine? 
I did cat xorg.* and it showed up reams of errors. Any pointers as to what's important to look for?

---

### Post by pauljwells on 2005-07-28
[QUOTE=pauljwells]I've just installed 5.04 on my HP media centre PC (I already have a working install on a mac)

I get to the login screen, can emter username and password but then the system hangs.

I can login to failsafe terminal, but I get a screen about 10 lines deep and once I've typed past the end it hangs. The text doesn't scroll.

There are no error messages during bootup and the install seemed to go OK.

I have an ATI X600 graphics card running dual monitors. Could the problem be related to this?

Many thanks in advance for any hints[/QUOTE]
 Hello Readers!

I don't have the time to mess with this anymore. I just need a very basic linux installation NOW to work on c++ code and don't care about anything else right now. I think my machineis very linux unfriendly, I couldn't get ubuntu, suse or fedora to install. Even MS Virtual PC couldn't cope! Finally, VMWare has worked, and I have ubuntu running in a slightly compromised form, but with a 3.2GHz proc and a Gig of RAM I can live with this. Just in case anyone is thinking of buying an HP Media Centre PC (Mine is M7081UK)  DON'T!! Not unless you want a challenge . That said, it's actually not too bad a machine if you can live with XP....

---

