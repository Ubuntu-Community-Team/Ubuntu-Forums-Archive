---
title: "Install 6.10 (edgy) from CD fails to load X server"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by IanVaughan on 2006-11-21
When booting from a Verifyied copy of an Edgy Install CD, both Normal and Safe Graphics Mode fail to start the X server.

Interestingly, 6.06 (Dapper) did manage to load the X server (i.e. fully loaded the Live CD) albeit from the Safe Graphics mode option!

So, re other posts, I tried the Alternative CD.
Dont know why it should help? To use the Text Install mode?

Ok, so I get it installed via Text based install, should I then be able to dpkg-reconfigure xserver-xorg? But I run that a few times with lower capabilities each time, and it still doesn't work.

I have a ATI graphics card : xorg.conf reads :
"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"

I think what Dapper does that Edgy doesn't (and I need to check this), is when using Safe Graphics Mode, Dapper sets xorg.conf Driver to vesa :
   Driver		"vesa"
Whereas Edgy, sets it to...? Does it set it to ATI? Even in safe graphics mode.  I know I would and DO when I reconfigure.

So should Edgy (or next release, as I dont want this again) set all cards to "vesa" in Safe Graphics Mode? 


Any in any case why doesn't the ATI driver work "out of the box"?


(I have reinstalled as I messed up something else, know its lame to reinstall, but there you go)

---

### Post by Jimmey on 2006-11-21
Try this.

When you get your system installed, X will probably fail. So, you could try switching to another TTY console (CTRL + ALT + F1), and logging in.

Once you've done that, like you say, > sudo dpkg-reconfigure xserver-xorg

From the driver selection menu, select "vesa" (for the time being).

Once that's done:
> sudo /etc/init.d/gdm restart

If that works, and you're able to get onto the internet, follow the guides describing how to install the ATI binary drivers (search for "ATI" at help.ubuntu.com).

---

### Post by IanVaughan on 2006-11-21
I was sort of doing this anyway, but thanks for the follow up!

I was more sort-of annoyed that a "newer" version of Ubuntu failed worse than the older version.

Both versions successfully failed to load the X server (from Live CD) and only on the older version could I get the Live CD to automaticly pick the vesa driver (but only when loaded from Basic Graphics mode.

I wont give up, but soooo many other people do, how can I promote Ubuntu if it doesnt run out-of-the-box? my machine is not old or that new!

---

