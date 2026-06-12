---
title: "I need help on several install issues please"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by Yehudah on 2010-06-03
I have installed Ubuntu 10.4 LTS onto my Dell 1536 AMD laptop.  I've been struggling for two weeks with several issues.  I'm not a newbie to Ubuntu, but I've become very frustrated with this version and I'm close to needing to go back to W7 (yeck).

I have surfed these and other forums for almost two weeks now and have used workarounds and supposed fixes that don't work.  Here are my issues:

1) My sound settings will not save.  When I go into Alsa Mixer and up the volumes and quit, they are saved after I reboot.  I have run: alsactl store, and variants of it, to no avail.  Every time I reboot, I have to go into Alsa Mixer to adjust the sound.

2) I have no 3D video.  I activated the ATI drivers that came with this distro and it worked fine, until I rebooted.  Then the video defaulted to the original setting (which work but are only 2D).  I have d/l'd drivers, uninstalled, installed, reinstalled the broken packages, yada yada yada, and now I am unable to active the drivers at all.  Not very happy with that.

3) When I attach my blackberry curve 8530, it charges which is sweet, but I cannot mount the media card or the phones memory.  I did lsusb and it sees the "RIM" device... but no matter what I try, it won't see the cards.  I don't need to use Barry or sync or backup, I just want to be able to transfer files.

4) It won't shut down.  When I shut it off or reboot it, it beeps, gives me a blank screen, then gives me a multicolored screen.  Then the screen fades back to white, and does not shut off.  Not very happy with that.

Anyone want to assist me with this?  I want to get this stuff fixed and run Ubuntu forever.... but if I can't get stuff to work (forget out of the box), then I'll have to go back to W7 (grrr).

Thanks all.

---

### Post by Yehudah on 2010-06-06
I know this is a lot to swallow!  Anyone?  Please?

---

### Post by ugm6hr on 2010-06-06
I would suggest you re-post in General Help, with 1 post per problem. Use a sensible title for each thread, so that knowledgeable people in each arena will be able to assist.  While you title here makes sense to you, the number of people who will look at the post will be reduced, since there is no suggestion of what the problem is, and then the actual post is very large,

As for your actual problems, I would suggest posting with the output of:
```
lspci
lshw
```

At least we will then know your exact hardware.

Also, please link to any workarounds etc - it may be that a little tweaking will help get them to work - and it will save us time when trying to help you.

I apologise if this doesn't move you any closer to solving the problem, but I think my advice will at least put your problem in front of people who might have a solution.

---

### Post by PGScooter on 2010-06-07
I agree with ugm6hr -- one topic per post helps to keep things clean.

Regarding the blackberry, check out "barry"
apt-cache search barry

I don't have any experience using it

---

### Post by Yehudah on 2010-06-07
Barry isn't going to work for me... all I want to be able to do is mount the microSD card to transfer files.  I don't need to sync anything, or backup anything, or use the calendar, yada yada yada.  Thanks though.

I did as the forum moderators asked and opened separate threads for each problem.

I'm not at my laptop right now, so I couldn't execute those commands and post the outputs.  I'll do that when I get home.

Thanks for your assistance thus far.

Yehudah

---

