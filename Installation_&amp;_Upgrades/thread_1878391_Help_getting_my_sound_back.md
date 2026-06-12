---
title: "Help getting my sound back"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-11-09
Hi I've updated to 2.6.32-35-generic kernel but now I don't have audio!

Reading in other forum after running

```
lspci -v
```

i get:


```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

How can I fix this issue? Thanks for helping!

P.D. if I go back to the previous version on the Ubuntu launcher the audio works

---

### Post by Peter2009 on 2011-11-14
> **Peter2009 said:**
> Hi I've updated to 2.6.32-35-generic kernel but now I don't have audio!

Reading in other forum after running

```
lspci -v
```

i get:


```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

How can I fix this issue? Thanks for helping!

P.D. if I go back to the previous version on the Ubuntu launcher the audio works


I check the previous version and it said its using "snd-hda-intel"

I have run:
sudo nano /etc/modules

and add that module but its not working! :-(

---

### Post by Peter2009 on 2011-11-14
> **Peter2009 said:**
> I check the previous version and it said its using "snd-hda-intel"

I have run:
sudo nano /etc/modules

and add that module but its not working! :-(

Ok this is now fix

I did the following! (some things in between but I this the following is what it fix it)

```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

I got this solution from [here]("http://ubuntuforums.org/showthread.php?t=1382744")

It looks it just re build it from the source.

I have noticed there is some other things may not have driver! I guess I will try it in another thread.

---

### Post by Peter2009 on 2011-11-14
> **Peter2009 said:**
> Ok this is now fix

I did the following! (some things in between but I this the following is what it fix it)

```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

I got this solution from [here]("http://ubuntuforums.org/showthread.php?t=1382744")

It looks it just re build it from the source.

I have noticed there is some other things may not have driver! I guess I will try it in another thread.

By the way anyway please no too fast to reply to my post!LOL

---

### Post by Peter2009 on 2011-11-22
I update to 2.6.32-36-generic on Ubuntu 10.04 and I had to manually update this again, good new is that the audio is back (just in case you are using this as a reference to update your system)

---

