---
title: "System restart interrupted"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by big-macca-d on 2010-05-04
Hello, 

I just updated from Ubuntu 9.10 to Ubuntu 10.04. The installation was complete and my system was restarting, however while restarting my laptop battery dies and so teh restart was interrupted. After charging my battery i tried turing my laptop back on. I get the ubuntu startup screen, but before i get to log-in the screen goes completely blank and nothing happens. Does anybody have any idea how i can fix this?

Cheers, Macca

---

### Post by kansasnoob on 2010-05-04
> **big-macca-d said:**
> Hello, 

I just updated from Ubuntu 9.10 to Ubuntu 10.04. The installation was complete and my system was restarting, however while restarting my laptop battery dies and so teh restart was interrupted. After charging my battery i tried turing my laptop back on. I get the ubuntu startup screen, but before i get to log-in the screen goes completely blank and nothing happens. Does anybody have any idea how i can fix this?

Cheers, Macca

Do you get the grub boot menu at startup? If Ubuntu is the only OS you'll need to press and hold the Shift key right after the System/BIOS screen passes to display the boot menu.

If you can get that to display try selecting the Recovery Mode option. It may give you some clues, regardless when it completes you'll see the following options:

Resume
Clean
Dpkg
FailsafeX
Grub
Netroot
Root

I'd first try resume which will resume the normal boot, if that fails I'd then try FailsafeX.

---

### Post by big-macca-d on 2010-05-04
Hello, 

I followed your advise. I got to the menu you mentioned and selected Resume. It then prompted me to enter my username and password. After doing this i just get a command line flashing. Any ideas what commands i could enter that coudl get me back into my desktop?

Cheers, Macca

---

### Post by big-macca-d on 2010-05-04
Hello, 

I managed to get back into my desktop by going through Failsafex mode. Do yopu have any idea how i can resolve my start up problem. I ran the update manager and installed the updates this didn't help thou. Any ideas?

Thanks again, Macca

---

### Post by kansasnoob on 2010-05-04
> **big-macca-d said:**
> Hello, 

I followed your advise. I got to the menu you mentioned and selected Resume. It then prompted me to enter my username and password. After doing this i just get a command line flashing. Any ideas what commands i could enter that coudl get me back into my desktop?

Cheers, Macca

Sorry I should have said it goes: username > password > startx :(

So what you needed to do next was type **startx** and hit enter.

---

### Post by kansasnoob on 2010-05-04
> **big-macca-d said:**
> Hello, 

I managed to get back into my desktop by going through Failsafex mode. Do yopu have any idea how i can resolve my start up problem. I ran the update manager and installed the updates this didn't help thou. Any ideas?

Thanks again, Macca

Try resume again only after entering your username and password type **startx**. If that fails then it has something to do with X and we'll need to know some GPU info:

```
lspci | grep VGA
```

---

### Post by big-macca-d on 2010-05-04
Hello, 

Thanks for your help. Typing startx didn't seem to work, i just get the same blank screen as before. The only way i can seem to get back to my desktop is by going through Failsafex. This works fine, but doesn't solve my start-up problem. Is there anything i can do from my desktop to fix my start up?

Thanks again, Macca

---

### Post by big-macca-d on 2010-05-04
> **kansasnoob said:**
> Try resume again only after entering your username and password type **startx**. If that fails then it has something to do with X and we'll need to know some GPU info:

```
lspci | grep VGA
```

Hello, 

Sorry i just seen this post. I tried this again, so it must be something to do with X. How do i find out GPU info? When i type the command you posted in the command line the output i get is

'00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integratred Graphics Device (rev 02)'

Not sure if this is what you were reffering to. As i'm sure you've noticed i'm pretty new to this, lol.

Thanks again, Macca

---

### Post by kansasnoob on 2010-05-04
> **big-macca-d said:**
> Hello, 

Sorry i just seen this post. I tried this again, so it must be something to do with X. How do i find out GPU info? When i type the command you posted in the command line the output i get is

'00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integratred Graphics Device (rev 02)'

Not sure if this is what you were reffering to. As i'm sure you've noticed i'm pretty new to this, lol.

Thanks again, Macca

Yes, that 'Intel 82852/855GM' is what's needed.

I have 'Intel 82945G/GZ' and it's working fine, not that that's helpful for you :(

At least we've narrowed things down, now to find a solution. Lets google "Ubuntu Intel 82852/855GM" and see if we find something.

---

### Post by kansasnoob on 2010-05-04
Maybe already finding something:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/477256](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/477256)

Particularly:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/477256/comments/78](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/477256/comments/78)

> The need to use "i915.modeset=0 xforcevesa" still exists in 10.04 final. I hope that there's a note somewhere for people who are likely to encounter this problem.

Do you think you can figure it out from there?

Regardless be sure to comment on that bug report! This is something that should be fixed!

One other note: you might try right clicking the desktop, selecting Change Desktop Background > Visual effects, and select None.

Obviously since I haven't encountered this identical problem I can only be of limited use going forward :(

---

### Post by kansasnoob on 2010-05-04
All that said, I'm sorry you encountered this problem. I do iso testing and we try hard to eliminate as many bugs as humanly possible.

Sadly the number of testers (and therefore hardware) is limited :(

---

### Post by big-macca-d on 2010-05-04
Kansasnoob, 

Thank you for all your help. I'll have a look at the links you posted and see if i can make some progress. If i don't make progress, is there a problem with me just running my desktop using failsafex? Although it is a slight inconvenience am i likely to encounter any issues by doing this?

Cheers, Macca.

---

### Post by kansasnoob on 2010-05-04
I'd monitor system temperatures.

---

