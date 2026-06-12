---
title: "Help, Compaq Armada m300 won't boot anymore!"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by sideshowme on 2008-06-27
hi,
first post... just as i thought i was getting the hang of this ubuntu business this came along...

my spare laptop is a compaq armada m300 on which i installed xubuntu 7.10 using unetbootin (no cd drive).  it worked fine. i upgraded to 8.04 and somehow my desktop was changed to gnome but as it seemed to work just as well as xfce i didn't really mind.  i recently did a load of updates as i hadn't been online for a while, and all was still working.

then yesterday i switched on and ubuntu simply wouldn't boot.  the progress bar on the xubuntu splash screen goes 95% of the way across, and then the only way i can do anything with the laptop is to unplug it or remove the battery.  when i tried to boot into "recovery mode" (whatever that is) the system prompted me to download some more upgrades, and then the normal boot messages went through everything OK until it got to the "Hardware Abstraction Layer (HALD)", at which point the laptop freezes and outputs the message "BUG: soft lockup detected in CPU#0" basically until i pull the plug or remove the battery.

the bug has a message which seems to be something related to irda, but this is a completely new development so i can only put it down to one of the sets of upgrades.  is there anything i can do to resolve this problem, short of reinstalling (as that will involve downloading the whole install over a 2mb broadband with a 600mhz cpu and 192mb ram...AGAIN... eeek)?  i've tried all the kernel versions that show up in grub, with no success.

the laptop is not faulty, as i can boot into windows 98 without a problem.  also, on ONE of my forays through recovery mode, i got into ubuntu, but it has not worked since then.

any thoughts? thanks, hopefully, in advance!

---

### Post by VMC on 2008-06-27
> **sideshowme said:**
> hi,
first post... just as i thought i was getting the hang of this ubuntu business this came along...

my spare laptop is a compaq armada m300 on which i installed xubuntu 7.10 using unetbootin (no cd drive).  it worked fine. i upgraded to 8.04 and somehow my desktop was changed to gnome but as it seemed to work just as well as xfce i didn't really mind.  i recently did a load of updates as i hadn't been online for a while, and all was still working.

then yesterday i switched on and ubuntu simply wouldn't boot.  the progress bar on the xubuntu splash screen goes 95% of the way across, and then the only way i can do anything with the laptop is to unplug it or remove the battery.  when i tried to boot into "recovery mode" (whatever that is) the system prompted me to download some more upgrades, and then the normal boot messages went through everything OK until it got to the "Hardware Abstraction Layer (HALD)", at which point the laptop freezes and outputs the message "BUG: soft lockup detected in CPU#0" basically until i pull the plug or remove the battery.

the bug has a message which seems to be something related to irda, but this is a completely new development so i can only put it down to one of the sets of upgrades.  is there anything i can do to resolve this problem, short of reinstalling (as that will involve downloading the whole install over a 2mb broadband with a 600mhz cpu and [COLOR="Red"]192mb[/COLOR] ram...AGAIN... eeek)?  i've tried all the kernel versions that show up in grub, with no success.

the laptop is not faulty, as i can boot into windows 98 without a problem.  also, on ONE of my forays through recovery mode, i got into ubuntu, but it has not worked since then.

any thoughts? thanks, hopefully, in advance!

I don't think ubuntu 8.04 will run with just 192 meg of ram. Someone else will have to confirm this. That's why I haven't loaded it on my old Compaq Armada.

---

### Post by sideshowme on 2008-06-28
> **VMC said:**
> I don't think ubuntu 8.04 will run with just 192 meg of ram. Someone else will have to confirm this. That's why I haven't loaded it on my old Compaq Armada.

hi,
thanks, but the point is, ubuntu 8.04 DID work, actually very smoothly and well - in fact, probably better than xubuntu had worked and almost as fast as windows 98 on such old hardware.  i was really impressed until it suddenly stopped booting altogether for no apparent reason.  

is there perhaps any way to roll back upgrades, as that is the only possible cause i can think of? or any way of diagnosing the actual fault other than that obscure microsoft-style error message?

anyone?  i really don't want to have to format and start again, for a newbie, this linux experience is looking suspiciously like windows all over again... :P

---

### Post by sideshowme on 2008-06-28
curiously, by dropping to the root prompt during the "recovery mode" boot, i was able to use "startx" to get me onto the root desktop, and ubuntu works just as well as it ever did (typing this on my 8.04 desktop).  but i'm logged in as root, which isn't ideal, and it still won't boot up automatically. weird.

---

### Post by Partyboi2 on 2008-06-29
what happens if you boot without splash? To do this when you boot and see the grub loading... part press Esc, then choose the kernel you normally boot into and press "e" to edit then select the line starting with "kernel" and press "e" again then change splash to nosplash, finally press enter and then "b" to boot.

---

### Post by ergosteur on 2008-07-14
I've got a similar issue on a Toshiba Satellite A40 (P4 2.4, 512, i852, Intel Extreme Graphics, 40GB). When I try to boot the 8.04 livecd (a pressed one from shipit) the computer hangs after the hald loading message (i pressed F6 and disabled the silent and splash flags). but in my case, the cursor stops blinking and there's no message about the CPU. any ideas?

---

