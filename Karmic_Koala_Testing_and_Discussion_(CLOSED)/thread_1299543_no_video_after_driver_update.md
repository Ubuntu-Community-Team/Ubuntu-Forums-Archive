---
title: "no video after driver update"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kylegio on 2009-10-24
i decided to give 9.10 a try and it has been headache after headache. i realize its still technically "beta" but ive run into trouble on every aspect of it. might have to just go back to 9.04 and forget about 9.10 all together maybe someone here can help me with my latest problem however. 

so got it all set up (for the 4th time today) seems to finally be working fine ... it gives me a message telling me i should install the proper drivers for my video card (nvidia 7800-gtx-oc) so i just go with whatever driver says recommended and tell it to install, it does it then says restart required... ok... restarts, loads to the first boot screen where its just the little white ubuntu symbol on black background, then display goes black, output to my display hasn't stopped completely because the display hasn't auto shut itself off like it normally does when its not getting any signal. but the video never comes back, im looking at a black screen, im pretty sure the computer is still functioning normally, but i dont have any services running on it that i can log into remotely, however pressing the power button once waits about 20 seconds and then shuts down, which is about how long it would take normally to shut down. 


can anyone think of a way to revert my drivers back? i cant seem to find a grub boot option like in previous versions of ubuntu? normally i can hit escape and it shows the grub menu where i can select to go into recovery mode and at least get to terminal, has this been changed in the new version of grub? it seems no matter what i press when starting up it just goes headlong into a full boot, which obviously does not work. anyway, any help would be appreciated, i can get a live cd to boot up so if theres somewhere i can edit and change back to just some generic video driver ?



thanks in advance for any help/thoughts

---

### Post by Elfy on 2009-10-24
esc has changed - Shift

though I believe that holding esc while it boots will get you the menu

You should be able to get to a recovery menu once you can see the menu, there should be a xorg or video fix there

Moved to Karmic

---

### Post by kylegio on 2009-10-24
well shift worked to bring up the recovery menu, however the recovery menu is broken, i think this might be a bug its done the exact same thing on 2 computers, brings up the recovery menu i start to arrow down through the options and then the screen goes all screwy,

ive been able to get into bash,is there a command i can run from here to fix my video or just switch it back to standard drivers?
thanks

---

### Post by kylegio on 2009-10-24
i think ive got it just about solved, i will mark the thread solved but i have a couple questions first.


how i solved it:  got into bash, tryed to do a dpkg-reconfigure on xserver-xorg  then startx. 
noticed startx actually spit out the error, video card power connector not connected, it had said this before in 9.04 but just warned me and said it would be reduced performance, i guess in 9.10 it couldn't handle it? so i specified a NoPowerConnectorCheck option in my xorg.conf file.

now questions:
i plan on replacing the power connector for my video card it appears some of the wires are kinda loose, but until it gets replaced is there a risk of damaging it running the video card without the power connector and using the NoPowerConnectorCheck option?  
is there a different driver i should switch to until i can get the wire replaced?

thanks.

---

