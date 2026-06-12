---
title: "Minimal Install &amp; Driver"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by krainboltgreene on 2010-03-31
So I go to install the Minimal Ubuntu edition and get to the ethernet driver selection part and it can't figure out what driver I have (Odd since Ubuntu regular can).

I find it on the list and it doesn't do anything. Any suggestions?

---

### Post by ajgreeny on 2010-03-31
I didn't have to do anything when I installed the minimal install CD two ubuntu versions ago, ie 8.10, and then installed the lxde desktop just to try it out.

Have you got a need to specifically add a driver for your ethernet card, or are you talking about a wireless card or adapter?

---

### Post by krainboltgreene on 2010-03-31
> Have you got a need to specifically add a driver for your ethernet card

It refuses to let you continue unless you have an active Ethernet network.

---

### Post by ajgreeny on 2010-03-31
OK, but are you wired or wireless?  I was wired when I did it and connected without having to do anything at all.

---

### Post by krainboltgreene on 2010-03-31
Why does it matter if I've got a wireless or wired device? *It wont let me get past the step where I need a ethernet device.*

---

### Post by krainboltgreene on 2010-04-04
I've decided to install the minimal version of Ubuntu and build my way up. One of the steps to installing the Minimal Ubuntu is that you need a working Ethernet connection. I have that and I have it plugged in when I'm installing Ubuntu.

When it gets to that step it tells me it can't find my Ethernet driver and asks me to pick from a list. I pick the one that matches the one shown below. It blinks and takes me back to the list.

What do I do?

Here's my driver according to **lspci**:
```

03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
	Kernel driver in use: atl1c
	Kernel modules: atl1c
```

---

### Post by krainboltgreene on 2010-04-04
I've decided to install the minimal version of Ubuntu and build my way up. One of the steps to installing the Minimal Ubuntu is that you need a working Ethernet connection. I have that and I have it plugged in when I'm installing Ubuntu.

When it gets to that step it tells me it can't find my Ethernet driver and asks me to pick from a list. I pick the one that matches the one shown below. It blinks and takes me back to the list.

What do I do?

Here's my driver according to **lspci**:
```

03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
	Kernel driver in use: atl1c
	Kernel modules: atl1c
```

---

### Post by krainboltgreene on 2010-04-04
Ok, the list shows:
```
atl1
atl1e
```

But the block of text says "No Ethernet card detected".

---

### Post by krainboltgreene on 2010-04-04
Ok, the list shows:
```
atl1
atl1e
```

But the block of text says "No Ethernet card detected".

---

### Post by krainboltgreene on 2010-04-11
So there's no one on this board who might understand the problem?

---

### Post by krainboltgreene on 2010-04-11
So there's no one on this board who might understand the problem?

---

### Post by lisati on 2010-04-11
Threads merged. Having multiple threads open on the same question can be confusing to those trying to help.

---

