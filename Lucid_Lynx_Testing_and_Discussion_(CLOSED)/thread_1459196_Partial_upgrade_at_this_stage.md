---
title: "Partial upgrade at this stage?"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Olmy on 2010-04-21
Hi,

I've been offered nothing but partial upgrades since shortly after downloading beta-2 (I assume it's beta-2, I upgraded from 9.10 the day after the release). Having read the warnings I've not actually accepted any.

We are now in 'final freeze' and less that 24 hours to the release candidate but I'm still only offered a partial upgrade.

Is this a problem - can I expect it to be fixed tomorrow?

How can I guarantee I get the RC?

Sorry if this is a stupid question - I'm quite new to ubuntu and very new to this beta testing lark....

---

### Post by lispy on 2010-04-21
Just wait. It´s probably still not fully synced.

---

### Post by mick222 on 2010-04-21
How long is it since you got any updates. If your not sure you should steer clear of the beta releases unless you don't mind breaking your system.I'm just one of those people who can't wait but I make sure anything important is saved to a backup.
  
  If you have backed up your data try running
[PHP]sudo aptitude update && sudo aptitude safe-upgrade
[/PHP]
In the terminal

---

### Post by sdowney717 on 2010-04-21
I have had to do this a few times
> sudo apt-get update && sudo apt-get dist-upgrade  

---

### Post by philinux on 2010-04-21
> **Olmy said:**
> Hi,

I've been offered nothing but partial upgrades since shortly after downloading beta-2 (I assume it's beta-2, I upgraded from 9.10 the day after the release). Having read the warnings I've not actually accepted any.

We are now in 'final freeze' and less that 24 hours to the release candidate but I'm still only offered a partial upgrade.

Is this a problem - can I expect it to be fixed tomorrow?

How can I guarantee I get the RC?

Sorry if this is a stupid question - I'm quite new to ubuntu and very new to this beta testing lark....

Update manager is not the best thing to use during the development cycle. Either use synaptic or command line. I assume you've read the sticky re partials.

---

### Post by randomizer101 on 2010-04-21
Are you using a main or secondary mirror? I've found that if I use the unofficial mirrors that I sometimes get partial upgrades, probably due to the high rate that new packages are being turned out for Lucid and the much slower and irregular syncs between the main and secondary mirrors.

---

### Post by kansasnoob on 2010-04-21
I generally wait for 48 to 72 hours to see if these partial upgrade issues resolve themselves, if not then I prefer using Synaptic Package Manager.

After clicking on Reload, then Mark all Upgrades, then Apply, you'll still get a chance to review the changes and decide.

If you're unsure you can click on the Show Details button in that pop-up window, and then even copy-n-paste the content to a new forum thread to ask for assistance.

---

### Post by Olmy on 2010-04-21
Thanks all.

Update manager offered a normal update after (possible coincidence?) I used the janitor to remove some package to do with audacity (that I don't use anyway).

I'll bear all this in mind for next time.

---

### Post by Khakilang on 2010-04-21
I'll think I wait for the final release and upgrade entirely. I got the patience and beside my Ubuntu 9.10 is working great and provide most of my needs. If it ain't broke why fix it.

---

### Post by scradock on 2010-04-21
> **Koh Kook Loon said:**
> I'll think I wait for the final release and upgrade entirely. I got the patience and beside my Ubuntu 9.10 is working great and provide most of my needs. If it ain't broke why fix it.

Because it's FUN? ?????? (Apologies to Ranch Hand!

---

### Post by philinux on 2010-04-21
> **Koh Kook Loon said:**
> I'll think I wait for the final release and upgrade entirely. I got the patience and beside my Ubuntu 9.10 is working great and provide most of my needs. If it ain't broke why fix it.

There haven't been any updates for a while.

```
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

