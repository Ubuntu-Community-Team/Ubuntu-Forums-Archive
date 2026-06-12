---
title: "Lost Update manager and Synaptic"
date: 2010-01-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sirkeith on 2010-01-24
Big woops. I am unsure what I did but I beleive I wiped out Synaptic and Update Manager when I did an upgrade of the Software Center.  I am unable to reload the programs apparently because there are incorrect dependicies. For instance the libept0 I neeed is version 0.5.29 and what is availabe is 0.5.30 and apt-get won't install it.

So do I just wait and keep attempting to install them every now and then, untill all components catch up to each other?


thanks

keith

---

### Post by exploder on 2010-01-24
> For instance the libept0 I neeed is version 0.5.29 and what is availabe is 0.5.30 and apt-get won't install it.


I just checked and I have 0.5.30 installed. I would wait a little while and see if this just hasn't made it into the repo that you are using yet. I am guessing but if you are in a different area of the world you are probably using a repo that nearer to your location and the update may not have made it in yet.

---

### Post by luffy_chan_19 on 2010-01-24
did you try to click system->administration->synaptic package manager  ? that is a very... unusual thing to happen.... [EMAIL="stmary.johnathan123@gmail.com"][/EMAIL]

---

### Post by sirkeith on 2010-01-24
Thanks, you are probably correct. I am in bc so don't know if that would make a difference in the repos or not. But I can wait, I think. :P

When I was doing the sofware center upgrade I got distracted with a customer and was not paying any attention. Later the upgrade manager didn't work and neither did synaptic. Didn't think too much of it. Shut the computer down later and went to bed, This morning after restarting there are not even icons for them in the administration launch menu.

keith

---

### Post by exploder on 2010-01-24
> This morning after restarting there are not even icons for them in the administration launch menu.

Wow, you are right, something went wrong somewhere. Are you still unable to reinstall Synaptic and Update Manager? You have the current version of libept0.

---

### Post by k64 on 2010-01-24
The Ubuntu Software Center's goal is "One repository, one app to access it". You see, Ubuntu Software Center is supposed to be a one-stop shop for applications, updates, and distribution upgrades. Its goal is to replace Synaptic and Update Manager! That's probably why you have that problem.

---

### Post by sirkeith on 2010-01-24
Exploder, I just checked the changelog site and k64 is correct in what he says. I guess I am experiencing a big change. I sure liked Synaptic, but knowing what is going on is good, doesn't seem quite so off-key now.

There are some new install/remove buttons in Software-Center, haven't noticed any indicators for upgrade yet, hopefully they are there. 

This is fun, I like new stuff.

keith

---

### Post by exploder on 2010-01-24
I just did a fresh install on another machine and still have Synaptic and Update Manager. k64 is right, the Software Center is supposed to handle everything but I don't think that everything is in place yet.

---

### Post by cariboo on 2010-01-24
k64 partially right as usual, the Software Center isn't scheduled to be finished until next year, that's when we'll see synaptic removed from the default installation, and update manager will still be around, as the software center won't do updates.

---

### Post by sirkeith on 2010-01-25
> **cariboo907 said:**
> k64 partially right as usual, the Software Center isn't scheduled to be finished until next year, that's when we'll see synaptic removed from the default installation, and update manager will still be around, as the software center won't do updates.

Okay, thanks cariboo. Means my problem is still a problem so I guess I will just wait for a bit and see if it happens to anyone else or releases may catch up and I will be able to reload. I am also missing the "hardware drivers" program. 

I am sure open to suggestions.

thanks

keith

---

### Post by sirkeith on 2010-01-25
I am going to download a new iso image from the daily-live site and burn a new cd and a fresh install and be a little more awake in the future. Hopefully what happened to me was strictly my bad and not a bug.

keith

---

