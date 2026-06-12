---
title: "Your /usr is broken - grub2 error after partial upgrade"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rex4u on 2009-10-06
Hello everyone,

I just partially upgraded my Karmic and a new kernel was installed.
After the reboot when I ran update-grub it showed me this error
"Your /usr  is broken. Please fix it before calling this wrapper"

Surprisingly there is no update-grub file in /usr/sbin or /usr/bin but one in /sbin.

Any idea, anyone...?

Thanks...

---

### Post by ranch hand on 2009-10-06
Get on your terminal and;
```

sudo apt-get update
THEN
sudo apt-get dist-upgrade

```
The best thing you can do for your self is to learn to never do a partial upgrade in update-manager.

I am currently on an upgraded version of 9.04 and I do not have update-manager.  It was removed a long time ago.  I only use apt-get and synaptic for updating my system.

Lots of people really like update-manager.  That is great.  DON'T DO PARTIAL UPDATES in it.

---

### Post by VMC on 2009-10-06
> **ranch hand said:**
> Get on your terminal and;
```

sudo apt-get update
THEN
sudo apt-get dist-upgrade

```
The best thing you can do for your self is to learn to never do a partial upgrade in update-manager.

I am currently on an upgraded version of 9.04 and I do not have update-manager.  It was removed a long time ago.  I only use apt-get and synaptic for updating my system.

Lots of people really like update-manager.  That is great.  DON'T DO PARTIAL UPDATES in it.
I haven't used update-manager for a long time. I've been using aptitude myself.

---

### Post by ranch hand on 2009-10-07
> **VMC said:**
> I haven't used update-manager for a long time. I've been using aptitude myself.
I just filed a bug on os-prober and aport sent the xsession error log.  It was ALL related to update-manager and I have never even looked at it.  I am glad I haven'.

I don't know why aptitude does not blow my skirt up, just doesn't.  I can tell you that if it was that or update-manager, aptitude is my FRIEND.

l like apt-get and synaptic and suggested synaptic because it is a gui.  Update-manager is too but synaptic works.

---

### Post by rex4u on 2009-10-07
Hi,

Thanks everyone...
I would re-look at update-manager since I never had any problems in last few years with partial upgrades or full dist-upgrades. This is the first and only case.

I am going back to terminal to try update again with apt-get (thanks Ranch Hand). Lets see what comes. I will post back the results.

Thanks again...

---

### Post by rex4u on 2009-10-07
> **ranch hand said:**
> Get on your terminal and;
```

sudo apt-get update
THEN
sudo apt-get dist-upgrade

```

No sir, it did not solve my problem. Same as where I was. System was already fully updated and upgraded. What next ...? Plz help.

Thanks...

---

### Post by ranch hand on 2009-10-07
dist-upgrade should have worked because of your missing files.  It should have installed what was needed to make you whole.

My current theory is that you have something that is not finished in dpkg.

Try this;
```

sudo dpkg --configure -a

```
That has been real handy for me on 9.10.  If it does anything, try the dist-upgrade business again.

---

### Post by rex4u on 2009-10-07
> **ranch hand said:**
> 
Try this;
```

sudo dpkg --configure -a

```

Nothing again...
I see no grub in /usr/sbin or /usr/bin. Strange ...? Is it that last update wiped off some of the grub files(but then I m able to boot into system) ? Would u suggest re-install of Grub ? if yes how (sorry don't know commands of Grub2).

It seems to me that grub-update command is looking for it in /usr/sbin and it is not there...Any ideas.

Thanks...

---

### Post by ranch hand on 2009-10-07
I have 5 grub-<whatever> files in /usr/bin and 9 in sbin.

personally, I think you are screwed.  I would get a Live cd and install again.  Make sure you back every thing up of that partition because it will be gone.

---

### Post by vulfgar on 2009-10-09
> **rex4u said:**
> Nothing again...
I see no grub in /usr/sbin or /usr/bin. Strange ...? Is it that last update wiped off some of the grub files(but then I m able to boot into system) ? Would u suggest re-install of Grub ? if yes how (sorry don't know commands of Grub2).

It seems to me that grub-update command is looking for it in /usr/sbin and it is not there...Any ideas.

Thanks...

Same problem here.

---

### Post by ranch hand on 2009-10-09
If you can boot into the system I would reinstall grub2 (meta package), grub-common and grub-pc.

You could also try transplanting those files that are missing from elsewhere (another grub2 using OS).

You could chroot in from the liveCD and do an "apt-get update" and "apt-get dist-upgrade" and hope for the best.  If you go this route you may need to run "start network-manager" or what ever hooks you up to the net.

---

