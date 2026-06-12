---
title: "upgrading from karmic to lucid"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by amnite on 2010-03-28
i am currently upgrading from karmic to 10.04 lucid beta. Im running a wubi install (vista) and it seems to be stuck, ive been waiting for almost an hour and its been stuck on Found Linux image: /boot/vmlinuz-2.6.32.17-generic any help i dont want to restartd my machine afraid ill mess things up. is this normal is it just taking a long time or has it hung up?

---

### Post by Mark Phelps on 2010-03-29
If you're not a seasoned, experienced Ubuntu user, you should NOT be messing with an OS version that just entered Beta testing.  Wubi works poorly with 9.10.  It may not work at all (yet) with 10.04.

You should direct your beta-version related questions to the proper forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.

---

### Post by tom.swartz07 on 2010-03-29
> **amnite said:**
> i am currently upgrading from karmic to 10.04 lucid beta. Im running a wubi install (vista) and it seems to be stuck, ive been waiting for almost an hour and its been stuck on Found Linux image: /boot/vmlinuz-2.6.32.17-generic any help i dont want to restartd my machine afraid ill mess things up. is this normal is it just taking a long time or has it hung up?

+1 to mark phelp's response. Unfortunately, it seems that almost every version of WUBI cannot handle the upgrade, nor was it meant to. 

WUBI is meant to be a windows based installer for people who want to use Ubuntu on a very temporary basis.

The best advice I could give you is to just restart the box and see what happens. If you have a broken grub bootloader, theres a link in my signature to help with that...

In the future, I would highly recommend actually, physically installing it in a separate partition. This way, your data is safe on your windows partition, and you wont run in to problems from the WUBI installer. 


Let us know what happens when you hard reset and we could help walk you through a remedy to fix it. Who knows? Maybe its perfectly fine?

---

### Post by shindou01 on 2010-03-29
> **Mark Phelps said:**
> If you're not a seasoned, experienced Ubuntu user, you should NOT be messing with an OS version that just entered Beta testing.  Wubi works poorly with 9.10.  It may not work at all (yet) with 10.04.

You should direct your beta-version related questions to the proper forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.

It took a lot of courage for a noob like me to try lucid lynx and well Lynx has a lot of appeal on it that I couldn't resist...I always failed to upgrade from karmic thus I did a clean fresh Install from the cd which was really terrifying for me but it succeeded somehow so I suggest you (amnite) do the same thing and just do a clean install if you're ready to wet your pants (j/k lol), I almost did though.....

---

### Post by tom.swartz07 on 2010-03-29
> **shindou01 said:**
> It took a lot of courage for a noob like me to try lucid lynx and well Lynx has a lot of appeal on it that I couldn't resist...I always failed to upgrade from karmic thus I did a clean fresh Install from the cd which was really terrifying for me but it succeeded somehow so I suggest you (amnite) do the same thing and just do a clean install if you're ready to wet your pants (j/k lol), I almost did though.....

Definitely. Ive been using Linux for years now, and I have Lucid on my big desktop, and thats fine- I only use it to surf the net and last.fm. Its very nice, but it DEFINITELY is still beta. There are around 20-25 updates a day, and at times it can be very unstable. It is getting better, but its not there yet. Once it is finally released, it will be VERY stable.

That being said, I'm itching to install it on my laptop here, but I do not want to have to fight with it until it gets there. 

If worse comes to worst, you will just have to re-install. While that is the most drastic measure, it shouldnt be that much of a problem if you properly backed everything up (home folder, sources list, and synaptic markings).

---

### Post by Frogs Hair on 2010-03-29
Hi,
 
I have done 6 Wubi installs of 9.10 for myself and others without problems. I too tried the update to 10.04 prior to my real installation of 9.10, and it stalled in the final stage with 12 minutes to go.
 
The restart resulted in kernel panic and I had to abort. If you want to use Wubi wait until  10.04 is listed as an option .

---

### Post by P4man on 2010-04-29
> **Mark Phelps said:**
> If you're not a seasoned, experienced Ubuntu user, you should NOT be messing with an OS version that just entered Beta testing.  Wubi works poorly with 9.10.  It may not work at all (yet) with 10.04.

Well, it does seem this bug slipped through and now "human beings" are having the exact same problem with the released LTS. Not good.
[http://ubuntuforums.org/showthread.php?p=9195665#post9195665](http://ubuntuforums.org/showthread.php?p=9195665#post9195665)

next time we should push for reporting such critical bugs on launchpad.

---

