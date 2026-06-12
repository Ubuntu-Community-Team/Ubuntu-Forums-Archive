---
title: "My laptop won't boot from the linux cd"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by kakashi on 2007-03-02
i just bought a used compaq armada e500. i won't to install ubuntu on it but i can't get it to boot from cd. however i can boot from the windows cd

i've been thinking about it and one solution that  just struck me was what if i could install grub (or another boot loader) from windows and use that to boot from the cd. i know its far fetched but i am stuck here. 

i think can install grub by using vmware server and mounting the whole hdd under vmware and using grub from there. i know its a complicated thing but i really wanna get ubuntu working. 


ps. are any of my idea worthwhile and can please suggest some more ideas.

---

### Post by invalid on 2007-03-02
If your system is setup properly to boot from a cd (via bios settings), perhaps it is the cd that is bad. Did you burn this yourself, or is it a shipit copy? If you burned it yourself, did you burn it as an image, after checking the signature?

---

### Post by kakashi on 2007-03-02
> **invalid said:**
> If your system is setup properly to boot from a cd (via bios settings), perhaps it is the cd that is bad. Did you burn this yourself, or is it a shipit copy? If you burned it yourself, did you burn it as an image, after checking the signature?

it always possible but i double checked the cds on my desktop and all of them boot.

---

### Post by warjowuch on 2007-03-03
maybe you need extra boot options, like -irqpoll? My oldy acer travelmate 212txv boots until a certain moment and then stops. It needed certrain extra bootoptions. With one cd it was irqpoll that did the job, on an older one it was something like noapic = off (or so)...

---

### Post by kakashi on 2007-03-03
> **warjowuch said:**
> maybe you need extra boot options, like -irqpoll? My oldy acer travelmate 212txv boots until a certain moment and then stops. It needed certrain extra bootoptions. With one cd it was irqpoll that did the job, on an older one it was something like noapic = off (or so)...


how do i set those without reaching the menu where you type those. i can't even reach the menu. or do i edit the iso before burning.

---

### Post by jmagsho on 2007-03-21
What version of Ubuntu are you trying to install?   I believe that Edgy had a minimum requirement of 192 mb of Ram for the live CD to install.    I know this because I tried it on a E500 with only 128mb and it hung in the middle of the install.   

I picked up some more Ram on Ebay and upgraded to 512 mb and the install went flawlessly.    Either that or try 6.06 instead.

---

