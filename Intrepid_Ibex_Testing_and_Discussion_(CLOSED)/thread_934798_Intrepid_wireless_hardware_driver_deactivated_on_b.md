---
title: "Intrepid wireless hardware driver deactivated on bootup"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by the real omni on 2008-10-01
Updated from 8.04 to 8.10 alpha 5 yesterday.

A strange issue seems to have arisen: every time I boot, the hardware driver for my Broadcom wireless network adapter is deactivated.

I can activate it by going into system -> administration -> hardware drivers but I'd obviously like it to be activated by default on boot up like the other hardware drivers (eg, my nvidia driver).

Anyone know why this would be de-activating itself on boot up (or shut down, for all I know) and how to stop it from doing so? 

(Or how to force it to activate on bootup even if it's been deactivated...)

---

### Post by dcstar on 2008-10-01
> **the real omni said:**
> Updated from 8.04 to 8.10 alpha 5 yesterday.

A strange issue seems to have arisen: every time I boot, the hardware driver for my Broadcom wireless network adapter is deactivated.

I can activate it by going into system -> administration -> hardware drivers but I'd obviously like it to be activated by default on boot up like the other hardware drivers (eg, my nvidia driver).

Anyone know why this would be de-activating itself on boot up (or shut down, for all I know) and how to stop it from doing so? 

(Or how to force it to activate on bootup even if it's been deactivated...)

Alpha software is ALPHA software, it is supposed to be used for people to test it and report problems JUST LIKE THIS to the appropriate development forum, not here.

Do not use Alpha software for general use, and do not post problems with pre-release software anywhere else but the development forum for that software.

---

### Post by the real omni on 2008-10-01
> **dcstar said:**
> Alpha software is ALPHA software, 


Ooooohhhhhh now I see... #-o

Thanks for stating the blatantly obvious, I was posting in here because a LOT of people read the ubuntu forums compared to the ubuntu dev launchpad, and just because I've recently updated to 8.10 doesn't specifically mean this bug is related to the update, it could just be something along the lines of having to put a command into modprobe or session startup to automatically start the driver (or there may be a workaround that a non-dev user could point out so the devs can spend their time actually working on the LTS release).

> it is supposed to be used for people to test it and report problems JUST LIKE THIS to the appropriate development forum, not here.

If I was 100% positive that it was due to the update, then you'd be correct. But I'm not, and you're wrong. ;) There have been a lot of crash reports that I've submitted to the launchpad - those are situations where we know it's due to the update. (ie, dependencies on libffi4 when 8.10 uses libffi5, etc) 

THOSE are the kind of error reports that should be passed directly to the devs, whose time is very valuable and shouldn't be frittered away on problems that could be otherwise solved by the community at large (provided the individuals in the community don't get self righteous and start preaching that help requests don't belong in a "general help" forum).

> Do not use Alpha software for general use

I'd say you're 30% to 50% right on that one. Do not use Alpha software on production or work-related systems (unless your work involves the alpha testing, heh). 

However, the more people that use the alpha software, the more chance there is of update-related error reports coming in to the devs to fix problems before the LTS rollout, and thus potentially save hundreds (or thousands) of "stable" users the same frustration.

As the old song goes, "the more we get together, the happier we'll be." :)

Let's try to keep the egos down and stick to constructive things like general help in the General Help forum, eh? :) We're all on the same team.

---

### Post by Ryadt on 2008-10-01
> **the real omni said:**
> Ooooohhhhhh now I see... #-o

Thanks for stating the blatantly obvious, I was posting in here because a LOT of people read the ubuntu forums compared to the ubuntu dev launchpad, and just because I've recently updated to 8.10 doesn't specifically mean this bug is related to the update, it could just be something along the lines of having to put a command into modprobe or session startup to automatically start the driver (or there may be a workaround that a non-dev user could point out so the devs can spend their time actually working on the LTS release).



If I was 100% positive that it was due to the update, then you'd be correct. But I'm not, and you're wrong. ;) There have been a lot of crash reports that I've submitted to the launchpad - those are situations where we know it's due to the update. (ie, dependencies on libffi4 when 8.10 uses libffi5, etc) 

THOSE are the kind of error reports that should be passed directly to the devs, whose time is very valuable and shouldn't be frittered away on problems that could be otherwise solved by the community at large (provided the individuals in the community don't get self righteous and start preaching that help requests don't belong in a "general help" forum).



I'd say you're 30% to 50% right on that one. Do not use Alpha software on production or work-related systems (unless your work involves the alpha testing, heh). 

However, the more people that use the alpha software, the more chance there is of update-related error reports coming in to the devs to fix problems before the LTS rollout, and thus potentially save hundreds (or thousands) of "stable" users the same frustration.

As the old song goes, "the more we get together, the happier we'll be." :)

Let's try to keep the egos down and stick to constructive things like general help in the General Help forum, eh? :) We're all on the same team.
That's why there is an Intrepid section on this forum.;)
Please post in the Intrepid section on the forum.

---

### Post by the real omni on 2008-10-01
> **Ryadt said:**
> That's why there is an Intrepid section on this forum.;)
Please post in the Intrepid section on the forum.

Really? The very first thing I did was to go to [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php), hit CTRL+F, and searched for "intrepid" with no success. 

Is the Intrepid forum named something else?

Please do post a link to the section you're referring to, I'll make sure to post there for any issues that I suspect might be intrepid-related but aren't sure enough to bother the devs with. :)

---

### Post by Ryadt on 2008-10-01
Here: [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by the real omni on 2008-10-01
Awesome thanks!! Will post there.

---

