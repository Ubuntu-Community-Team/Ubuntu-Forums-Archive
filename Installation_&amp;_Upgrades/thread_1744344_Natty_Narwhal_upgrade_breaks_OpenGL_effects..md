---
title: "Natty Narwhal upgrade breaks OpenGL effects."
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by elliotcroft on 2011-04-30
I upgraded from Maverick a few days ago, and ever since, OpenGL effects are getting disabled by KDE with a message stating that the effects were making the machine slow.
Switching to Xrender works fine, but XRender isn't as advanced as OpenGL.
What are the methods that I could use to solve this?

---

### Post by elliotcroft on 2011-05-01
Bump.
I really need my wobbly windows back and OpenGL is interpretive to that.

---

### Post by elliotcroft on 2011-05-02
Bump.
I need this fixed.

---

### Post by elliotcroft on 2011-05-02
Bump.
What is the problem with OpenGL?

---

### Post by schnelle on 2011-05-02
Maybe your kwin configuration file got corrupted during upgrade. Delete kwin configuration file ( ~/.kde/share/config/ kwinrc ) and then alt+f2 and type: kwin --replace. This way you will be back to default kwin settings.

---

### Post by elliotcroft on 2011-05-02
> **schnelle said:**
> Maybe your kwin configuration file got corrupted during upgrade. Delete kwin configuration file ( ~/.kde/share/config/ kwinrc ) and then alt+f2 and type: kwin --replace. This way you will be back to default kwin settings.
The problem still exists.
Unless I disable the check, the only problem is that it disables the effects randomly, but if I disable the check, it becomes slow.

---

### Post by schnelle on 2011-05-02
What graphic card do you have? Intel, ati or nvidia?

---

### Post by elliotcroft on 2011-05-02
> **schnelle said:**
> What graphic card do you have? Intel, ati or nvidia?
Intel.
Before the upgrade to 11.04 I had no problem with effects.

---

### Post by schnelle on 2011-05-02
Turn off blur effect, check "disable functionality checks" and change from "accurate" to "smooth" or "crisp" scale method. If these "hacks" doesn't help, you should try booting up liveCD of natty to see if everything works as it should. I have never did an upgrade because I always expect some breakage to happen. If live session works ok you should make clean install.

I did clean install of natty beta2 two weeks ago and everything works great so far. But I am using an ati card.

---

### Post by elliotcroft on 2011-05-02
> **schnelle said:**
> Turn off blur effect, check "disable functionality checks" and change from "accurate" to "smooth" or "crisp" scale method. If these "hacks" doesn't help, you should try booting up liveCD of natty to see if everything works as it should. I have never did an upgrade because I always expect some breakage to happen. If live session works ok you should make clean install.

I did clean install of natty beta2 two weeks ago and everything works great so far. But I am using an ati card.
Looks to have worked, thanks.
EDIT: It's actually incredibly buggy so I've had to switch back to XRender.
Any way to solve this?

---

### Post by schnelle on 2011-05-02
Boot up liveCD and see if "clean" Natty works ok. Remember, blur effect doesn't work well with intel graphics so turn it off in live session too.

---

### Post by elliotcroft on 2011-05-02
> **schnelle said:**
> Boot up liveCD and see if "clean" Natty works ok. Remember, blur effect doesn't work well with intel graphics so turn it off in live session too.
Would I lose any themes or alike when I clean install?

---

### Post by schnelle on 2011-05-02
Yes. You have to format your root and home partition if you want to make clean (new) install with brand new configuration files.

But you don't have to do it right away, you can just boot up liveCD to see if desktop effect are working well. If they work well in live session, then something got broken during upgrade process and you will have to do a clean install. Back up your important data and install kubuntu natty from scratch.

If desktop effects doesn't work well in live session, then the problem is probably in intel drivers and I am afraid I cannot help you with that.

---

### Post by elliotcroft on 2011-05-02
> **schnelle said:**
> Yes. You have to format your root and home partition if you want to make clean (new) install with brand new configuration files.

But you don't have to do it right away, you can just boot up liveCD to see if desktop effect are working well. If they work well in live session, then something got broken during upgrade process and you will have to do a clean install. Back up your important data and install kubuntu natty from scratch.

If desktop effects doesn't work well in live session, then the problem is probably with intel drivers and I am afraid I cannot help you with that.
Would this affect my Windows partition?

---

### Post by schnelle on 2011-05-02
> **elliotcroft said:**
> Would this affect my Windows partition?

No if you choose NOT to format them. When you are in process of installing kubuntu, when you come to step about partitions, choose "select partitions manually" (or something similar I cannot remember exactly) and then choose your root partition where you want to install kubuntu and check "format" option. As long you don't check "format" to your windows partitons, your windows partitions will be untouched. 

If you have any doubts about how to install ubuntu/kubuntu please start new thread or google some howto :)

---

### Post by elliotcroft on 2011-05-02
> **schnelle said:**
> No if you choose NOT to format them. When you are in process of installing kubuntu, when you come to step about partitions, choose "select partitions manually" (or something similar I cannot remember exactly) and then choose your root partition where you want to install kubuntu and check "format" option. As long you don't check "format" to your windows partitons, your windows partitions will be untouched. 

If you have any doubts about how to install ubuntu/kubuntu please start new thread or google some howto :)
Actually, I think I'll just wait until a new version of KDE or Ubuntu comes out.
I originally installed Kubuntu with Wubi so I don't know the process. (Actually, I have done the process before, but from the text based alternative install disc)

---

### Post by elliotcroft on 2011-05-02
Reinstalled the QT4 plugin for OpenGL and all is working fine now.
Good news!

---

### Post by elliotcroft on 2011-05-02
I also needed to enable effects in fullscreen applications, since suspending them crashes Kwin.

---

