---
title: "Driver Problems."
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by cozadaman on 2007-12-16
So the basics for this are, i cannot install my Nvidia GeForce 8800GT graphics driver and the resolution i have is unusable (not being fussy i really cannot se anything at all, one bug blur).

Ive tried closing the GDM and and running an nvidia.run file but it keeps telling me "command not found". thats exaclty how i did it on Fiesty and on Gutsy with a differnet computer but now its just decided to pack the shits. any other commands i should know about?

just incase it helps my monitor is 1680 x 1050.

I've also tried editing my xorg.conf file. but it wont work either. Just a big ol' blur.

Much appriciation.

---

### Post by cozadaman on 2007-12-16
Okay i fiddled around with xorg.conf file some more and got my resolution to work good n dandy. but the driver problem is still at large. Forgot to mention, that restricted drivers says i have to restricted drivers available.

---

### Post by cozadaman on 2007-12-16
Okay i cant spell, i have "NO" restricted drivers available. Are there possibly some .deb files arround?

---

### Post by Partyboi2 on 2007-12-17
you could try giving envy ago to install the restricted drivers.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cozadaman on 2007-12-17
Envy wont install :'(.  Something to do with not being able to install packages to do with openoffice? not sure what thats about but update has error with them too. Does Nvidia-glx-new support 8800GT yet or do i still have to use the beta 64bit drivers?

---

### Post by cozadaman on 2007-12-17
okie dokie got it working.

i was using the command
sudo /home/coza/Desktop/nvidia.run

when i should have been using
sh /home/coza/Desktop/nvidia.run
or 
cd /home/coza/Desktop
sh nvidia.run

ty 4 helping.

---

### Post by drmaxmad on 2007-12-17
i have run the same command as you mentioned but it said NVIDIA driver must be run from root....
any ways i am using ubuntu on virtual box...

---

### Post by cozadaman on 2007-12-17
okay well im currently, as we speak trying to learn virtual boxes except the other way around, putting windows on linux. Anyways boot into your recovery mode of ubuntu and when it all loads type

passwd root

then it will prompt you for a password and then again to clarify. This is setting up your root account.  after this is done boot back into linux basically getting to the text part only when it asks you for your username and password type root for your username and the password you just setup.

let me know how it goes

out of curiosity, what virtual software are you using?

---

