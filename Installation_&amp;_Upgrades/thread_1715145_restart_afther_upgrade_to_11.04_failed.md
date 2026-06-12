---
title: "restart afther upgrade to 11.04 failed"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by masodin on 2011-03-26
hello all,

i am an ubuntu nooby, out of curiosity i installed ubuntu 11.04 alpha3 last night.
Yes, i will definitely never install an alpha version unless i wish to test it!
Frankly said, i first installed 386 version on a notebook which runs  just fine. So I thought why not install the 64 bit version on my pc.

Unfortunately, the system did not finish the first reboot in order to  complete the installation. First it always stopped at "checking battery  state". There, I read that this bug is already fixed:

[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/735805]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805")

I came across this thread: [B][http://ubuntuforums.org/showthread.php?t=1707879&highlight=heads+hose+system](http://ubuntuforums.org/showthread.php?t=1707879&highlight=heads+hose+system)

[/B]So I pressed Alt +F2 in order to log in and performed sudo apt-get  update followed by sudo apt-get upgrade. Everytime there was a new  update I hoped, that this will fix the issue. But when I shutdown the  system with sudo shutdown now -h and restart again there is no progress.

The only thing that changed is that the system no stops at "Stopping userspace bootsplash", whatever that means? 

Can anyone of you PLEASE tell me what to do in order make ubuntu 11.04 apha3 running?

Again, i promise as a nooby i will never run an alpha version!

Thanks.

masodin

---

### Post by Bucky Ball on 2011-03-26
You are definitely in the land of testing as Natty hasn't been released yet!

You will learn plenty about Ubuntu trying to fix the problems and updates will help. Enjoy the steep learning curve. 

You might like to install the super stable 10.04 LTS (long term support) on one partition and 11.04 on another. You can then select either at boot; one stable, the other for learning and tweaking (although you will also learn plenty from the stable release). You can use the same /home and /swap for both installs. 

Usually an idea to get to know the Ubuntu ropes on a stable release if you are unfamiliar before leaping onto the cutting edge. If you want the bleeding edge, install the nightly builds. 

This thread should have been posted in the Natty Narwhal Testing forum but not to worry. ;)

---

### Post by phoenixpb on 2011-03-26
i have 10.10 installed in one hard drive
i have 11.04 installed in a second hard drive
so i don't care if i scrach the 2 nd ubuntu it's just for testing
but so far 11.04 is very impressive works very fine :)
(fresh install from DVD and regular updates)

---

### Post by IraKane on 2011-04-28
I'm actually having the same problem now.  Originally, I upgraded to 11.04 from 10.10 via updates.  After it failed to restart as explained above, I figured I'd try a different method and reinstalled via CDROM.  As expected I have the same problem.  I really like the interface so if there is any way around this issue I'd love to here it.

---

### Post by postlude on 2011-06-12
Same problem here with regular (non-alpha) 11.04. Steps:

- Upgraded via the graphical update manager
- Booted into new system but warned Unity would not work
- Started nvidia driver center, which advised me to update my X config, which I did using nvidia-xconfig
- Rebooted, and the system now hangs on "Stopping Userspace bootsplash"

---

