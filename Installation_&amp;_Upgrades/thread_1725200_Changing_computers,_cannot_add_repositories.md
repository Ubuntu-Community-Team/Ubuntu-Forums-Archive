---
title: "Changing computers, cannot add repositories"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by chromedome on 2011-04-09
Greetings, all...

I'm in the midst of updating from my poky old Dell to a newer (3 yr old) HP laptop. I've completed most of the changeover, but I can't seem to add any repositories to Software Sources. When I attempt to enter the APT line into Synaptic, the only button that's clickable is "Cancel." This holds true even if I use sudo to run Synaptic from the command line. 

I've also tried editing /etc/apt/sources.list directly, but when I enter the corresponding lines (cut and pasted from my old computer, to eliminate the chance of typos), I get a message that the newly inserted lines are "malformed."

I'm sure I've overlooked something simple, but I've been at this for two days now and I'm getting a bit frustrated (doesn't do much for mental clarity).

I'm really missing my ubuntu font family...

---

### Post by Hedgehog1 on 2011-04-10
Would you please post a few of the commands that are not working/are malformed (the ***whole*** command line please)?

Then we can see where things are going wrong. :P


***The Hedge***

:KS

---

### Post by zvacet on 2011-04-10
What Ubuntu version do you run?Did source list worked on old comp?Add lines you want to your new comp and then 

```
cat /etc/apt/sources.list
```

Post output here.

---

