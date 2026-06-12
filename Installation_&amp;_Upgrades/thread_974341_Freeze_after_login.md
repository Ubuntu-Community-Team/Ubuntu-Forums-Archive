---
title: "Freeze after login"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by maddentim on 2008-11-07
Hello,

I did not find any threads that matched my issue and hardware.  

My hardware: 
Toshiba Satellite A135-S2386
32-bit dual core Intel processor
ATI 200m video
Intel HDA sound
2G ram
dual boot with vista

I upgraded (Not much an upgrade! that was dumb) from 8.04 to 8.10 via the update manager.  It went fine until about half way through the install and then just sat there, utterly frozen.  I let it go over night to see if it was just busy, then reboot.  On reboot, the new kernel failed and I went into the old one.  That didn't work great either and I ended up going through many attempts to get the upgrade to complete with dpkg and apt-get from the command line.  Finally, it seemed to complete, but when i login into gnome, it just hangs on the beige screen with the pointer.  ctr+alt+backspace gets you back to the login.  I can go in under failsafe-gnome, but no regular.  tried removing compiz and telling it to use metacity via the gnome configuration editor.  no use.  

My suspicion is that the ati fglrx driver is at fault as it has been a thorn in the side of this laptop from the start with gnome.  

Unfortunately, this has been the worst upgrade experience of my involvement with ubuntu.  it is a shame. I really prefer it to windoze, but frankly windoze just plain works better with this hardware.  I guess i am stuck on windows for this laptop until a fix comes out...

Oh, and i have not heard it make any noise, so i suspect that the upgrade broke my sound too.  nice.  good thing it was free or i'd be asking from my money back :)

---

### Post by giacomo.c on 2008-11-10
this happens to me too!  but i get a black screen after logging in.... it might not be your ati driver as i also have ati.  it think it's just gnome... i can use my fluxbox session no prob, albeit, none of the gnome applications work (gnome-terminal).

but it's true, windows does look like a better idea when i major release ends in such failure.

i'm going to keep looking on the forums and see if anyone else has had this problem and if there's a fix.

---

### Post by frodon on 2008-11-10
If what you're looking for is stable and rock solid release only use LTS versions. This release is not a LTS version.

---

