---
title: "So far, so good!"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by michaelzap on 2010-03-24
I upgraded to Lucid beta the day that it came out with some trepidation, given the many issues that I'd had on my main laptop with Karmic. On the whole, Lucid seems to me to be a much more solid release. So far the beta is running dramatically better on this computer than Karmic ever did.

I have much less fan activity, which was starting to really concern me in Karmic. Battery life is much longer. The annoying Pulseaudio memory leak is fixed, so I don't have to kill that every hour or so. All of the other major gripes that I had in Karmic seem like a bad dream now that I'm using Lucid.

I do get some minor crashes (plymouthd and panel applets mostly), but nothing all that disruptive. I expect some issues running a beta. So far Lucid is restoring my faith in Ubuntu, which had been weakened a bit after Karmic (and Jaunty, which was also a bit rough on me due to my Intel video card).

---

### Post by michaelzap on 2010-03-27
Some minor issues I'm still working around and wondering if others have resolved:
[LIST]
[*]GVFS mounting often hangs (CPU goes to as much as 200% per process until it's killed), but if I kill and retry it eventually it works fine
[*]Panel applets crash rather often on boot (perhaps one out of every three reboots)
[*]Still can't suspend (or hibernate, but I don't have a swap partition)
[*]All of a sudden my custom xsplash background is not showing up - anyone know why?
[/LIST]
Overall Lucid is a dream compared to Karmic (or Jaunty) - reminds me of how much I loved Ubuntu when I first installed Feisty!

---

### Post by amano on 2010-03-27
> **michaelzap said:**
> Some minor issues I'm still working around and wondering if others have resolved:
[LIST]
[*]GVFS mounting often hangs (CPU goes to as much as 200% per process until it's killed), but if I kill and retry it eventually it works fine  [COLOR="Red"]Might be this bug --> [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/538764](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/538764)[/COLOR]

[*]Still can't suspend (or hibernate, but I don't have a swap partition)
[COLOR="Red"]--> Hmm. Is that a regression? Suspend and hibernate are STILL a problem for any linux. It will not work for all users, most probably not even in lucid[/COLOR]

[*]All of a sudden my custom xsplash background is not showing up - anyone know why? [COLOR="Red"]--> Hmm. Is Xsplash even being used? It should be substituted by Plymouth[/COLOR]
[/LIST]


My comments are in the quotations.

---

### Post by michaelzap on 2010-03-27
I thought Plymouth was substituting usplash, but I admit that I haven't investigated further. In any case my custom background was working in Lucid until an update this week. Now all I get is the standard purple haze image.

Suspend didn't work for me on this laptop in Karmic either, so it's not a regression (but I can dream of putting my laptop to sleep like a normal person someday).

I'll check out that GVFS bug - I saw it in another thread also.

---

### Post by michaelzap on 2010-03-29
> **michaelzap said:**
> 
[LIST]
[*]GVFS mounting often hangs (CPU goes to as much as 200% per process until it's killed), but if I kill and retry it eventually it works fine
[/LIST]

This seems to have been fixed by the gvfs updates today! \\:D/

---

