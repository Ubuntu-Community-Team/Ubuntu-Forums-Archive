---
title: "Partial upgrades - Intrepid"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Victormd on 2008-10-10
I've just installed the Beta version and after installing the updates I get a partial upgrade option. I start the partial upgrade (assuming it's a kernel thing) and once it reaches "cleaning up", the process just hangs. No option to cancel, stop or anything. I've restarted the comp. a couple of times and the partial upgrade is there and the same thing happens every time.

Has anyone else run into this problem?

---

### Post by mister_pink on 2008-10-10
These problems are quite common. Most people suggest just not doing the partial upgrades. When you see one, cancel it and go to synaptic and mark all upgrades from there. 

Do check what it wants to remove too, there's been some problems with very important things going missing!

---

### Post by solitaire on 2008-10-10
Victor

It's happened to me a few times this week (this usually happens close to the release date.)

I just stop the process after 5 mins and ignore it for a day. Hopefully by the time i check again they have sorted out all the issues.

Think this current "partial" upgrade removes all the Gnome desktop stuff if you run it in Synaptic (well it does in mine!) so BE CAREFUL!! :D

---

### Post by rekado on 2008-10-10
Same here. It hanged for ten minutes. Then I aborted and restarted. Haven't had the chance to test if everything is okay still... It's probably because I removed Evolution and some of the programs that come with the Ubuntu meta-package. I will just install it again, upgrade and remove the programs I don't use. Should work then.

---

### Post by solitaire on 2008-10-10
I ran the update again 30 mins ago.

Looks like the problems been sorted out!

use: ```

sudo apt-get update && sudo apt-get upgrade

```

and it should work itself out now...

---

