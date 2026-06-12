---
title: "Problem starting Karmic using grub from old install"
date: 2009-05-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-05-05
I have updated a second partition on my machine to run Karmic. After installing a fresh 9.04 the update all went fine. The problem is that when I update my menu.lst on my main install to include Karmic I get a grub error 15. The entry is just coppied from the .lst file from the Karmic install, with a little adjustment to point to the new partition as shown 

> title 		Karmic Koala - Pre Alpha
root (hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ea478011-6b94-49d7-81a0-9ed38809aa6a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot

title		Karmic Koala - Pre Alpha (recovery mode)
root (hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ea478011-6b94-49d7-81a0-9ed38809aa6a ro single
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


I have checked all the file names and uuid number and they are all fine, the only other difference is that I am using ext4 on the Karmic install and ext3 on Jaunty. Any ideas.

---

### Post by ronacc on 2009-05-05
try commenting out the root (hd0,4)  line . also try installing the 2.6.30-2 kernel .  I went through a bout with my karmic install doing the same thing , no idea why .

---

### Post by snowpine on 2009-05-05
What version is your main install? You need Jaunty or newer to boot to ext4.

---

### Post by ronacc on 2009-05-05
that explains why mine corrected itself after I let karmic install its own grub even though the boot stanzas were identical .

---

### Post by celticbhoy on 2009-05-05
My main system is Jaunty, so ext4 should be ok. Icant get access to my software sources to change anything so there are just as a standard install. How would I go about updateing the kernel?

---

### Post by autocrosser on 2009-05-05
Look in Synaptic for 2.6.30 (do a search)--You have to manual install it right now---make sure you get the headers, image & restricted (if you need it) 30-1 has the restricted, 30-2 needs them still, so if you need a 3rd party driver--don't use 30-2 yet.

---

### Post by ronacc on 2009-05-05
the ppa nvidia 185.18.04 driver is working fine for me with 2.6.30-2 .

---

### Post by celticbhoy on 2009-05-06
Upgraded the kernel on Karmic - still the same error 15.

---

### Post by ronacc on 2009-05-06
if you are willing to try something a little risky , get a copy of super grub disk for rescue operations if necessary . [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)  . and then install grub from within karmic , that worked for me . first make a copy of your working menu.lst incase you need to add back your other installs , karmic found my other installs ok but that hasn't always happened in the past which is why I usualy keep my old grub and add new installs to it .

---

### Post by celticbhoy on 2009-05-06
The problem is not that Karmic did not find my other installs, it did and the grub menu.lst works fine. It is just that I would rather use the grub & menu.lst from my main install. At the mo, I can switch between the two using the root & setup commands in grub. It is a small annoyance rather than a problem, I just wondered what was causing it.

---

### Post by ronacc on 2009-05-06
at what point did you install jaunty ? I installed pre-alpha as I always do ( on my dedicated test box) and the ability to boot from ext4 wasn't added until later in the cycle ( about a4 I think ) so that is why my jaunty grub wouldn't boot karmic ( my jaunty install was ext3 ) . if you installed jaunty from the release version I am at a loss .

---

### Post by Gina on 2009-05-07
Generally I have no problems with grub but when I installed 9.04 on my P4 it found all my other OSs but a couple of the other Ubuntu systems wouldn't boot - with a grub error 15 - file not found.  I couldn't see anything wrong with the menu.lst - the stanzas looked fine - uuids, partition numbers etc. all OK.  I got round the problem by changing the main (new) menu.lst to use **configfile** to point to the menu.lst of the other systems rather than the boot section itself.  That fixed it :)

---

