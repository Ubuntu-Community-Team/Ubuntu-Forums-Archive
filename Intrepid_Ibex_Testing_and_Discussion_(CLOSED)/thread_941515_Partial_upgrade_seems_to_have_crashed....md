---
title: "Partial upgrade seems to have crashed..."
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xeriouxi on 2008-10-08
Hi!

I am trying to get some updates installed from the Update Manager, but I seem to have encountered a problem.

It said it needed to do a partial upgrade, so I said that was okay and it ran through the process fine, but it seems to have crashed on cleaning up. It's been stuck on the following process for ages:

> Processing triggers for man-db ...

Is this normal to have to wait a while or do I have a problem? :confused:

---

### Post by xlinuks on 2008-10-08
Congrats!

---

### Post by philinux on 2008-10-08
> **xeriouxi said:**
> Hi!
I am trying to get some updates installed from the Update Manager, but I seem to have encountered a problem.
It said it needed to do a partial upgrade, so I said that was okay and it ran through the process fine, but it seems to have crashed on cleaning up. It's been stuck on the following process for ages:
Is this normal to have to wait a while or do I have a problem? :confused:

The advice I've always followed is "never do a partial upgrade". I press cancel and then let it update. I then use synaptic. Click upgradable upstream. Mark these and see what it wants to remove install upgrade. If I'm happy i then let it proceed. This is exactly what I've done this morning and all updates done with no errors. 
I suggest you look at synaptic and see if it can fix things.

---

### Post by mc4100 on 2008-10-08
If you're sure it's crashed, then there's not much you can do. Try ending the process and running the usual:
```
sudo dpkg --configure -a
```

---

### Post by mister_pink on 2008-10-08
Mines done exactly the same. Won't be doing any of them again! Nevermind... 

I've killed it and had no obvious adverse effects.

---

### Post by ju2wheels on 2008-10-08
Same thing happened here except mines luckily froze at the end during the clean up portion. This has never happened to me at all before. Hopefully Ill be as lucky as you, im going to kill mine now...

---

### Post by rbmorse on 2008-10-08
My usual approach to a partial upgrade from upgrade manager is to open a terminal and try sudo apt-get dist-upgrade.  This morning I got some file-missing errors, but everything else installed cleanly.  

I would not do that with a production machine, but since this is my test installation with a pre-release O/S, why not see what breaks and what doesn't?

---

### Post by aaronb on 2008-10-08
Same thing happened here. No issue since I rebooted.

---

### Post by zooounds on 2008-10-08
Same here.

"ldconfig deferred processing now taking place"

But it seem like it has released the deb-database so I just play on :)

---

### Post by tensop on 2008-10-08
Yep, mine locks at 

"ldconfig deferred processing now taking place"

:)

---

### Post by Enigmatic on 2008-10-08
Mine had locked at man-db in this morning's round of updates. Killed the process and just ran dist-upgrade from the commandline. So far so good.

---

### Post by Bios Element on 2008-10-09
I can also confirm the same bug.

---

### Post by nystire on 2008-10-09
I have the same "lock" during the cleanup phase.

---

### Post by Odisej on 2008-10-09
Same problem here. After which - am not sure if it is related yet - nvidia drivers don't want to load (kernel issue etc.)

Odisej

UPDATE: Did upgrade in terminal, selected nvidia driver v. 173, restarted and selected version 177 again. It seems it is working just fine now. After all this Skype working as well. I had some problems with it previously.

---

### Post by philinux on 2008-10-09
Partial upgrades are known to fail.

Use

sudo apt-get update && sudo apt-get upgrade

If there are any packages not upgraded use synaptic channel "upgradeable (upstream)".
Click mark all upgrades then apply. It will then tell you whats need to be removed etc before it can proceed.

---

### Post by aaronb on 2008-10-09
> **philinux said:**
> Partial upgrades are known to fail.

Use

sudo apt-get update && sudo apt-get upgrade

If there are any packages not upgraded use synaptic channel "upgradeable (upstream)".
Click mark all upgrades then apply. It will then tell you whats need to be removed etc before it can proceed.

Do you mean that its a known bug that will be fixed or is a feature of 8.10?

---

### Post by zooounds on 2008-10-09
> **aaronb said:**
> Do you mean that its a known bug that will be fixed or is a feature of 8.10?

A feature that hangs the upgrade procedure seem pretty stupid to me.

This HAS to be fixed.

---

### Post by jerome1232 on 2008-10-09
> **zooounds said:**
> A feature that hangs the upgrade procedure seem pretty stupid to me.

This HAS to be fixed.

Ummm Does BETA OS have any meaning to you?

---

### Post by zooounds on 2008-10-09
> **jerome1232 said:**
> Ummm Does BETA OS have any meaning to you?

Yes, that's why I wrote "It has to be fixed". It's under a month until release and the upgrade procedure crash. Big issue I think.

---

### Post by Locke_99GS on 2008-10-09
Same thing happened to me during the recent "partial upgrade". It seems to have finished though. I just killed it after a fair amount of time, and had no issues.

---

### Post by mister_pink on 2008-10-09
> **zooounds said:**
> Yes, that's why I wrote "It has to be fixed". It's under a month until release and the upgrade procedure crash. Big issue I think.

It is only a problem for those running the beta. You shouldn't have to do any partial upgrades when the final version comes out.

---

### Post by Vraaq on 2008-10-10
> **Locke_99GS said:**
> Same thing happened to me during the recent "partial upgrade". It seems to have finished though. I just killed it after a fair amount of time, and had no issues.

Same here, everything seems to be working.

---

