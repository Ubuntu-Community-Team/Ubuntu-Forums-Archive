---
title: "How to disactivate Compiz"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by Jayhawker on 2011-12-23
In 11/10 Ubuntu, I have activated Compiz (rotating cube and all those things), and once I've rebooted, all the lateral bar (the workspace) allowing to activate programs has desappeared. I can't browse, use the evolution e-mail program, etc

Please, how to deactivate all this mess?

Maybe If I can get a terminal which I don't see how to activate without the workspace

Thanks

---

### Post by Paddy Landau on 2011-12-23
[LIST=1]
[*]Log in.
[*]Open a terminal with *Ctrl-Alt-T*.
[*]Type *ccsm* and press Enter. This will start *CompizConfig Settings Manager*.
[*]Press *Desktop* (on the left).
[*]If *Ubuntu Unity Plugin* (on the right) is ticked, untick it.
[*]Tick *Ubuntu Unity Plugin*.
[*]You will receive one or more requests to resolve conflicts. In every case, tick the right-hand button (to resolve).
[/LIST]
Your launcher and panel should reappear. Log out and log in again.

Let me know if you hit any problems.

---

### Post by EvanF on 2011-12-23
Paddy, you're the MAN.  Thanks for this.  Been playing a bunch with 11.10 and with Compiz, lot's to mess with (and mess up).  But your reset is what I've needed.

EvanF

---

### Post by Paddy Landau on 2011-12-23
> **EvanF said:**
> Paddy, you're the MAN.
Which man?

I'm glad it worked for you.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---

### Post by MG&amp;TL on 2011-12-23
If, after you've got it fixed, you do want to enable cube and stuff, follow the excellent guide here:

[https://help.ubuntu.com/community/CompositeManager]("https://help.ubuntu.com/community/CompositeManager")

which works fine for me.


If you cannot get into CCSM normally, (it depends on what you ticked), click the cog on the login screen and select "ubuntu 2d" to login to a 2d environment, where you can launch CCSM (compiz won't be loaded, so you're safe).

Just some more detail for you, paddy's method is excellent. :)

---

### Post by Jayhawker on 2011-12-23
Thank You very much. It works!

But the cube doesn't rotate at all despite it's activated. 

Anyway, thank you.

> **Paddy Landau said:**
> [LIST=1]
[*]Open a terminal with *Ctrl-Alt-T*.
[*]Type *ccsm* and press Enter. This will start *CompizConfig Settings Manager*.
[*]Press *Desktop* (on the left).
[*]If *Ubuntu Unity Plugin* (on the right) is ticked, untick it.
[*]Tick *Ubuntu Unity Plugin*.
[*]You will receive one or more requests to resolve conflicts. In every case, tick the right-hand button (to resolve).
[/LIST]
Your launcher and panel should reappear. Log out and log in again.

Let me know if you hit any problems.

---

### Post by MG&amp;TL on 2011-12-24
You need to enable the 'rotate cube' plugin. :)

Click on the plugin, the keybindings are detailed there.

You can use my link or paddy's method to enable the rotate cube plugin.

---

### Post by Jayhawker on 2011-12-24
Thank You. I got it too!

> **MG&TL said:**
> You need to enable the 'rotate cube' plugin. :)

Click on the plugin, the keybindings are detailed there.

You can use my link or paddy's method to enable the rotate cube plugin.

---

