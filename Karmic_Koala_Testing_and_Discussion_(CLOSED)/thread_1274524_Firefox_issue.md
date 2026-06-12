---
title: "Firefox issue"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SuicideSmurf on 2009-09-24
Is anyone else experiencing oversized text boxes?
[IMG]http://i35.tinypic.com/2ewk6io.png[/IMG]

---

### Post by zika on 2009-09-24
Yes, it started on 3.7 yesterday and progressed to 3.6 today. In my case it is contained only in the address bar ...

---

### Post by rubenverweij on 2009-09-24
No, sorry, I'm not seeing it.
I've got all the updates installed.

---

### Post by SuicideSmurf on 2009-09-24
> **zika said:**
> Yes, it started on 3.7 yesterday and progressed to 3.6 today. In my case it is contained only in the address bar ...

I'm getting it in 3.5.3

> **rubenverweij said:**
> No, sorry, I'm not seeing it.
I've got all the updates installed.

Same here with updates, but I still get this problem.

---

### Post by joepotter on 2009-09-24
I lost all of the addons or extensions that I had with Firefox. Not funny at all.

---

### Post by sports fan Matt on 2009-09-24
And the text in Youtube under videos is terrible...

---

### Post by SuicideSmurf on 2009-09-24
> **sox fan Matt said:**
> And the text in Youtube under videos is terrible...

Have you changed the font in Firefox? I have, and I'm beginning to think this maybe something to do with it. :-k

---

### Post by mdurham on 2009-09-24
no problem here with 3.5.3 32-bit

---

### Post by Merk42 on 2009-09-24
> **zika said:**
> Yes, it started on 3.7 yesterday and progressed to 3.6 today. In my case it is contained only in the address bar ...

EDIT

Nevermind, would open a can of worms

---

### Post by SuicideSmurf on 2009-09-24
<<Erased smurfiness>>

---

### Post by Merk42 on 2009-09-24
> **SuicideSmurf said:**
> Ugh, can we please keep the thread on topic?

Sorry fine, I'll edit my post and you edit the quote.

---

### Post by SuicideSmurf on 2009-09-24
> **Merk42 said:**
> Sorry fine, I'll edit my post and you edit the quote.

Ok deal. Sorry if that seemed rude, it's just you post something here, one person makes a slightly off topic remark and the whole thread gets derailed into an argument. I've already had 2 threads in the Community Cafe closed this way. I don't want the same thing happening here, especially as it's a bug/glitch thread! :)

---

### Post by sfreed on 2009-09-25
> **joepotter said:**
> I lost all of the addons or extensions that I had with Firefox. Not funny at all.


Yeah, same here, when I first upgraded. (fresh install) 

When I ran firefox it did not load my addons. They were listed in the "add-ons" but at the top, it said:

```
restart Firefox to complete your changes
```

and I believe a couple of the listed add-ons said

```
this add-on will be updated when Firefox is restarted
```

 I poked around a bit, decided there must be some incompatibilities, moved my .mozilla directory and started a fresh and downloaded and installed my add-ons.

Everything seemed to work perfectly.
... until today.

I just disabled a couple of the add-ons and updated a third. And guess what? On restart none of my plugins loaded! And we're back to 

```
restart Firefox to complete your changes
```
```
this add-on will be updated when Firefox is restarted
```
```
this add-on will be disabled when Firefox is restarted
```

I also noticed that it wanted to update Xulrunner (fr) 1.9.1.2 and Xulrunner (fr) 1.9.0.8.

I just deleted all the French language packs on my system and restarted Firefox. Now it looks like all my add-ons are back (may have no correlation to lang pacs). All the "restart" messages are the same, however except for Xulrunner (fr) 1.9.1.2 which it now says will be uninstalled when Firefox is restarted.

I'm guessing it is stumbling over a permissions problem somewhere. I'll post more if I uncover anything else.

---

### Post by steeleyuk on 2009-09-25
> **joepotter said:**
> I lost all of the addons or extensions that I had with Firefox. Not funny at all.

Don't run alpha then...

Anyway same issue.

---

### Post by petri on 2009-09-26
Extensions disappeared in 3.0 too.

I have Jaunty root partition and home partition. I created a Karmic root partition but I used same home partition and extensions didn't install any more and they actually vanished from Jaunty Firefox 3.0

I have installed 3.5 but it doesn't help I still get "Th"This add-on will be upgraded when Firefox is restarted"

---

### Post by NCLI on 2009-09-26
Nightly Testers Tools is the best Firefox plugin since Adblock+, you should try it out if you don't want to suffer from incompatible extensions.

---

### Post by sfreed on 2009-09-26
> **NCLI said:**
> Nightly Testers Tools is the best Firefox plugin since Adblock+, you should try it out if you don't want to suffer from incompatible extensions.

Unfortunately, this is not about incompatible extensions. It's about FF's inability to complete add-on installs/updates/disables/removals. 

Interestingly enough, when I try to install the NTTs, (2.0.2) it says 

```
Not compatible with Firefox 3.5.3
```

So something in the Ubuntu Karmic distributed Firefox is borked. Note that this is a fresh clean install with no carry-over from previous installations, including a new .mozilla directory in my home directory.

---

### Post by ilarrain on 2009-10-05
Same problem here. I've also tried removing my extensions folder from my profile, but the problem rapidly came back after I reinstalled the plugins. Using Chrome for now.

---

### Post by ilarrain on 2009-10-05
Please subscribe to this bug in Launchpad and post your comments, in order to get developers attention.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/441552](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/441552)

---

