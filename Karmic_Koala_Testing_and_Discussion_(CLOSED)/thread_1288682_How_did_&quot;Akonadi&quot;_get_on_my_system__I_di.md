---
title: "How did &quot;Akonadi&quot; get on my system?  I didn't install it."
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-11
It's some deeply threaded PIM/search too that I surely have no use for!
Strange.

---

### Post by emarkay on 2009-10-11
Now THIS is really strange - In Synaptic, I selected it for "complete removal"  (akonadi-server) and another akondi file that is installed, and I find it's going to remove K3B, the DVD burner.  So I go to K3B and select "Reinstall this package" and then go see if akonadi is still deselected - and IT'S GONE!  It's not found in Synaptic search, either.  I didn't do anything but reenable K3B and Synaptic AUTOMATICALLY removed something without my approval!

Now this is a BUG!

Please check this on your machines.

---

### Post by emarkay on 2009-10-11
Waitaminute - it's still there on my system, the Akonadi Console.   Now with another Synaptic session, it's there, too.  ans yes it DOES remove K3b.  Even though K3b does not show "akonadi-server" as a dependency, it is automatically installed...

Grrrrr.  :confused:

---

### Post by jocko on 2009-10-11
> **emarkay said:**
> Waitaminute - it's still there on my system, the Akonadi Console.   Now with another Synaptic session, it's there, too.  ans yes it DOES remove K3b.  Even though K3b does not show "akonadi-server" as a dependency, it is automatically installed...

Grrrrr.  :confused:
Relax. This is not a bug. K3b depends on kdebase-workspace-bin, which depends on plasma-widgets-workspace, which depends on akonadi-server.

---

### Post by Zorael on 2009-10-11
n/a

---

### Post by emarkay on 2009-10-11
Thanks - I was more worried about the thing "disappearing" from Synaptic w/o my action.

I have K3b on my Jaunty system and all the akonadi files are this is listed in Synaptic, but NOT installed, so this is  a Karmic issue.

Still, strange.  :)

---

### Post by hikaricore on 2009-10-11
In the future when you want to update your post use the edit button.
Spamming a thread by replying to yourself just to bump is annoying and considered rude.

---

### Post by emarkay on 2009-10-11
> **hikaricore said:**
> In the future when you want to update your post use the edit button. Spamming a thread by replying to yourself just to bump is annoying and considered rude.

I was NOT TTTing it, my friend.  If I wanted to get attention I'd say LOOK AT MEEEEEEE!

It was as sequence of events on a remote PC and therefore I wanted to separate the events.

Rude when one assumes before validating, but I'd never make any accusations - that's just not my style.  

Thanks.

---

