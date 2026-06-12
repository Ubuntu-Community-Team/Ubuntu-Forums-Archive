---
title: "Wireless on Laptop Reseting Itself"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by ExxonValdeez on 2007-03-21
I am having problems with my wireless connection on my HP laptop. The connection is lost and reset about every five minutes and causes the mouse to slow down along with the keyboard to repeat oddly. The laptop uses a PRO/Wireless 3945ABG Network Intel builtin card that works fine when not reseting itself. Any suggestions?

---

### Post by Darko-TheRaven on 2007-03-21
> **ExxonValdeez said:**
> I am having problems with my wireless connection on my HP laptop. The connection is lost and reset about every five minutes and causes the mouse to slow down along with the keyboard to repeat oddly. The laptop uses a PRO/Wireless 3945ABG Network Intel builtin card that works fine when not reseting itself. Any suggestions?

same thing hapens to me, i just disable and renable the card and it seems to work fine then

---

### Post by ExxonValdeez on 2007-03-24
Shutting of the wireless card is not much of an option. Although, I was able to get some speed up with the [FONT="Courier New"]top[/FONT] command. To use it type this:

```
top
```

Then find the Intel processes that should include the driver name and look for the PID of the processes. Then type this will top is running:

```
r
```

It will ask you for the PID, so type that and then it will ask you for the renice value. Enter 19. To quit type:

```
q
```

Update: Seems as if I put this in the wrong category. I guess I clicked the wrong one.

---

