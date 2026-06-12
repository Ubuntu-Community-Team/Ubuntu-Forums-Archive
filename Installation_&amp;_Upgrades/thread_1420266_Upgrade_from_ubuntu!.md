---
title: "Upgrade from ubuntu!"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by tuxman7 on 2010-03-02
Hi,

I recently set up my machine with ubuntu Karmic and i just discovered Ubuntu studio which is exactly what i need it for...

I was thinking about just upgrading what i have now, i have my home directory on a separate partition so it should be affected.... but when i ran this command which is listed in the support section of the ubuntu studio site i got an error about 'Super Cow Access' or something along those lines.

```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop
ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics
ubuntustudio-video linux-rt
```

I dont understand why.

Also, i know that if i do an upgrade instead of a clean install then i will have to run alot more commands because changes will be made to apps already installed that would be affected by the upgrade.

Would it be easier just to try a clean install?

If i do another clean install and have both ubuntu and studio in separate partitions do i need a swap for each or just the one swap do?

Thanks

---

### Post by cchhrriiss121212 on 2010-03-03
I'd recommend a separate install for studio, you can share the swap and home partitions.

---

### Post by kellemes on 2010-03-03
Take it slow..

```
sudo apt-get update
sudo apt-get install ubuntustudio-desktop
```

Now post the output if anything went wrong..

---

### Post by tuxman7 on 2010-03-06
Sorry for the late reply, but i decided to forget the install and just install the programs i want in regular ubuntu, i know it wont be as real time as studio but i aint going to be recording from a mic or anything so im not too bothered.

I did try to install studio and use the same swap for ubuntu but the swap ended up getting corrupted and i had problems doing stuff in both OS's so i just wiped again and put karmic on.

I think i will just get the theme package from the repository as i find it more attractive than the regular ubuntu one :P

Thanks anyway guys :)

---

