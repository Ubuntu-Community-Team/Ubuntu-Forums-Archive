---
title: "libdbusmenu-glib1"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-02-13
Hiyas, don't know if anyone else has experienced this ....

My list of packages awaiting installation had been steadily growing... in amongst them Tomboy notes (which has, of late been here, then gone, then back...) RythmBox (Which I do actually use) and newer linux kernels amongst many.

With Tomboy having been a little 'un-stable' I decided to use synaptics to get it - and it worked fine :p

Enboldened, I decided to have a go with Rythmbox - It said I needed libdusmenu-glib1, so - I went and installed it.... Then a lot of things happened very quickly !!!!

Woosh - all those packages waiting in Update Manager suddenly wanted to install themselves - So, one re-boot later, here I am - lots of updates, new kernel.

Still puzzled as to why libdbusmenu-glib1 didn't go get itself, so - not sure if I did something wrong in manually getting it - but all seems well :popcorn:

Just a little note of caution - on my 1st re-boot, the system hung. I re-booted back into the 32-12 linux, then back to 32-13 and all was well with the world.

Regards,

Phill.

---

### Post by SevenMachines on 2010-02-13
the apt 'smart upgrade' is only slightly smart. the problem you had was a quite common one, an application upgrade requires an old library to be removed and replaced with a new one with a slightly different name, in this case

1. rhythmbox depends on  libdbusmenu-glib0

2. new rhythmbox depends on  libdbusmenu-glib1

3. 'smart' upgrade doesn't understand its safe to remove  libdbusmenu-glib0 since its being replaced by an upgraded (but renamed) library libdbusmenu-glib1

4. automatic upgrade doesnt proceed and backlog of upgrades develops!

Usually if you look manually at whats holding the upgrade back you can see thats its safe to proceed or not

---

### Post by phillw on 2010-02-13
Thanks, I am wary of instigating partital updates, only time I borked my 10.04 !! - Then re-read **carefully** the sticky on partial updates ;)

At least by just allowing libs to be replaced when an app is asking for them seems a safer way forward - for me, at least.

As to finding out manually what is holding things back - I only found that one out because I was prepared to let RythmBox update itself as I do use it & am happy to test new releases - Had I been using one of the other music players, it would have languished. 
Is there a fairly straight-forward way to see what is holding things back ?

Thanks,

Phill.

---

### Post by SevenMachines on 2010-02-13
simplest way is to use synaptic and try to upgrade the package manually, itll tell you what its going to install/remove and you can cancel if its going to be bad.
i think apt-get upgrade <package> does the same but i cant remember whether or not it gives you a choice to abort before you do it, think it does :)

---

