---
title: "System locks up for no reason? 9.04"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hufferd on 2009-04-18
Has anyone else had this issue - Everything with Junty has been going along fine.  until it seems Friday's updates did something.. MY system seems to "lockup" for no reason.  The first time it happened I had left the computer on over night and of course I did have it set to turn off my screen after 40  min. of being idle. But when I came back to the computer the next morning I moved the mouse and my blue indicator light on my monitor indicated it came back on but the screen stay blank. This has now happened 4 more times. all since Fridays updates were installed. or at least that's when I can trace it too.  

I have also set the screen to NEVER turn off when idle. All that did is the system still locks up with the screen saver frozen in place on the screen. The only way to get it to restart when this happens is to do a hard shut down and then restart.  It seems to happen after the computer has been sitting idle for at least an hour or so.   

I have NO power management features turned on the only thing I am using is cpu scaling - It cuts the CPU back when not in heavy use.  The thing that bugs me is all seemed to work fine till the last round of updates. :)

---

### Post by olskar on 2009-04-18
Sadly this has been reported by others too :(

[http://ubuntuforums.org/showthread.php?t=1127591](http://ubuntuforums.org/showthread.php?t=1127591)

---

### Post by eyelessfade on 2009-04-18
yes my ******* laptop keeps doing this to me :/

---

### Post by eyelessfade on 2009-04-18
hehe funny censoring, what is this the kindergarten?

---

### Post by eyelessfade on 2009-04-18
> **eyelessfade said:**
> hehe funny censoring, what is this the kindergarten? And my word wasn't even swearing. A child of parents which is not married :)

---

### Post by hufferd on 2009-04-18
> **olskar said:**
> Sadly this has been reported by others too :(

[http://ubuntuforums.org/showthread.php?t=1127591](http://ubuntuforums.org/showthread.php?t=1127591)

Ah thank you I will take a look :(

---

### Post by manuelb on 2009-04-18
I wonder if its related to the way my pc freeze: i just have to

```

strace gedit

```

and it lookups completely and the mouse still moves. REISUB works, but that's odd.
(i had a problem with gedit that i solved another way)

---

### Post by KingArthur10 on 2009-04-19
> **manuelb said:**
> I wonder if its related to the way my pc freeze: i just have to

```

strace gedit

```

and it lookups completely and the mouse still moves. REISUB works, but that's odd.
(i had a problem with gedit that i solved another way)

I was able to TTY to another term and sudo killall Xorg to get X to reboot.  It's not pretty.  Have you reported it yet?

---

### Post by FuturePilot on 2009-04-19
> **manuelb said:**
> I wonder if its related to the way my pc freeze: i just have to

```

strace gedit

```

and it lookups completely and the mouse still moves. REISUB works, but that's odd.
(i had a problem with gedit that i solved another way)

Heh, that's funny. I've been getting weird lockups when running straces too. Though the mouse still moves and everything seems to be working in the background, I can't click on anything. I can still get to a tty and then I have to kill the program I'm running an strace on.

---

### Post by Reiger on 2009-04-19
I've had that twice yesterday. All I have to do is open Firefox and look up my actual preferences/settings under Edit.

Conspiracy mode ON:

I do not have Ext4. Still:
Firefox *was* changed to fsync() everything to hell and back again (which is how some complaints about ext4 came to be heard)...
Ext4 was changed to alleviate other problems (code that didn't fsync() enough basically)
Power-savings modules *were* changed, w.r.t. file system behaviour (delayed fsync() IIRC).
Laptops use those modules...
... Therefore: Firefox plots to take over laptops by means of a cleverly prepared `fsync() bomb' using the power-savings behaviour!! :(

Conspiracy mode OFF:
As with any good conspiracy theory: its worthless. :P Solution: use Opera (or other non-mozilla browsers)! ;)

---

### Post by ktp on 2009-04-19
funny I just rebooted from a lockup.

---

### Post by hufferd on 2009-04-20
follow up I turned off ALL Desk top effects and this step seems to have fixed my issue :) 

For now that is

D

---

### Post by manuelb on 2009-04-20
> **KingArthur10 said:**
> I was able to TTY to another term and sudo killall Xorg to get X to reboot.  It's not pretty.  Have you reported it yet?

Not yet, today i was able to "strace firefox" since i wanted to test out the new improvements but couldn't get it to work (segmentation fault just after copying the ff3.0 profile), strace worked fine this time, anyway i think we may report it since i've 2 different machines hanging on "strace gedit".

---

### Post by olskar on 2009-04-20
> **FuturePilot said:**
> Heh, that's funny. I've been getting weird lockups when running straces too. Though the mouse still moves and everything seems to be working in the background, I can't click on anything. I can still get to a tty and then I have to kill the program I'm running an strace on.

Exactly what happens to me too

---

### Post by olskar on 2009-04-21
Please confirm and add info to [https://bugs.launchpad.net/ubuntu/+bug/364524](https://bugs.launchpad.net/ubuntu/+bug/364524)

---

### Post by biji on 2009-04-21
hahhaha........ funny.. i just tried: 
strace gedit
and.......... my system locked up! i can't figure out why by just strace-ing gedit would lock up system :D can someone smarter explain this ^^ oh btw im using ext4

---

### Post by manuelb on 2009-04-21
> **olskar said:**
> Please confirm and add info to [https://bugs.launchpad.net/ubuntu/+bug/364524](https://bugs.launchpad.net/ubuntu/+bug/364524)

I reported the behavior i'm experiencing and wondering what "strace `strace gedit`" would lead to.. can't wait to get home for trying it out, i feel my lunch break could be longer than usual ;)

---

### Post by ELD on 2009-04-21
I get hard lockups, i am using nvidia not intel so don't say it's the intel bug :P
And this is without using whatever this strace thing is.

---

### Post by konas on 2009-04-21
Hi , I used to get system lock ups too, and they just stopped when I dissabled the tracker indexing. 

I tried to resolve the problem by reinstalling and doing tracker-process --hard-reset, but then the tracker finds errors during the indexing. Bugs are already reported about this.

---

### Post by olskar on 2009-04-21
> **ELD said:**
> I get hard lockups, i am using nvidia not intel so don't say it's the intel bug :P
And this is without using whatever this strace thing is.

And I am using ATI so it's propablo not cardrelated :)

I get random lockups too just like you but when using the command ```
strace gedit
``` I can force the machine to lock up. 

Does your computer lock up when issuing that command too? It always good to know what makes something crash if you want to fix it.

---

### Post by olskar on 2009-04-21
> **konas said:**
> Hi , I used to get system lock ups too, and they just stopped when I dissabled the tracker indexing. 

I tried to resolve the problem by reinstalling and doing tracker-process --hard-reset, but then the tracker finds errors during the indexing. Bugs are already reported about this.

Hi, I have disabled and removed tracker but I can still make the computer lock up with strace gedit

---

