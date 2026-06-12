---
title: "gksu broken?"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-09-21
I'm trying to do "gksu nautilus" and here's what I get: 

Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x01 0x00 0x00 0x00 0x00 0x00 

Then it fails.

---

### Post by kansasnoob on 2009-09-21
It's my understanding that gksu nautilus is intentionally disabled, but someone taught me a new command:

```
gksu dbus-launch nautilus
```

Seems to work OK. I assume you know you can really hose things working in Nautilus as root?

---

### Post by mc4man on 2009-09-21
see this thread
[http://ubuntuforums.org/showthread.php?t=1269866](http://ubuntuforums.org/showthread.php?t=1269866)

While reading the other day wasn't 100% clear on whether all graphical uses with elevated privileges was going to be removed or just some.

It does appear that ATM  it's all.
( there is a workaround, though I'm hesitant to post, the reasons for disabling are valid (at least in the context of that thread

Edit : it appears there are at least 2 workarounds

---

### Post by VMC on 2009-09-21
There's been a few topics on this subject. Here's one [**explanation**]("http://ubuntuforums.org/showthread.php?t=1271066&highlight=gksudo")

It has been frowned upon and discouraged by the devs.

---

### Post by oboedad55 on 2009-09-21
> **mc4man said:**
> see this thread
[http://ubuntuforums.org/showthread.php?t=1269866](http://ubuntuforums.org/showthread.php?t=1269866)

While reading the other day wasn't 100% clear on whether all graphical uses with elevated privileges was going to be removed or just some.

It does appear that ATM  it's all.
( there is a workaround, though I'm hesitant to post, the reasons for disabling are valid (at least in the context of that thread

Well, I know it's frowned upon in these forums for good reason. Things have changed in karmic in this area. I don't know if it's temporary or not. I wouldn't mind a PM.

---

### Post by mc4man on 2009-09-21
I'm going to make 1 comment on this and then forget the whole deal, affects me not in the least.

While people much smarter than me have given good reasons why you shouldn't use root graphically I do find it curious than simply removing brasero and as a result  also rhythmbox allows gksudo nautilus to function as it has in the past.(libbrasero-media0 is the 'culprit' it seems

That does beg the ? was it disabled because it should be or is it that it just won't work with the above mentioned

It also is curious that the nautilus-gksu package remains in the repo (Canonical supported

---

### Post by oboedad55 on 2009-09-21
> **mc4man said:**
> I'm going to make 1 comment on this and then forget the whole deal, affects me not in the least.

While people much smarter than me have given good reasons why you shouldn't use root graphically I do find it curious than simply removing brasero and as a result  also rhythmbox allows gksudo nautilus to function as it has in the past.(libbrasero-media0 is the 'culprit' it seems

That does beg the ? was it disabled because it should be or is it that it just won't work with the above mentioned

It also is curious that the nautilus-gksu package remains in the repo (Canonical supported

That is most peculiar. What possessed you to try and remove these programs? I can see no reason why gksu shouldn't be used. If you don't want a user to have access to it, then don't tell them about it or uninstall it.

---

### Post by mc4man on 2009-09-21
I also meant to re-mention that I'm not sure that running gksu nautilus was what was disabled or that the inability to do so is only a bug to be resolved.

My feeling is that it is a bug to be fixed, the thread I linked to is of a 'somewhat ' different nature.

A clarification would be good, otherwise time will tell

---

### Post by oboedad55 on 2009-09-21
> **mc4man said:**
> I also meant to re-mention that I'm not sure that running gksu nautilus was what was disabled or that the inability to do so is only a bug to be resolved.

My feeling is that it is a bug to be fixed, the thread I linked to is of a 'somewhat ' different nature.

A clarification would be good, otherwise time will tell

Do you know if it's been reported? I can't believe we're the only ones that happened to notice. Maybe it got broken with today's updates? I didn't check thte function until after I installed all the updates...

---

### Post by mc4man on 2009-09-22
> Do you know if it's been reported? 

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/420841](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/420841)
+ 30-40 duplicates

---

### Post by oboedad55 on 2009-09-22
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/420841](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/420841)
+ 30-40 duplicates

Cool, the same error message I got. Thanks for the link.

---

### Post by VMC on 2009-09-22
mc4man, It's too late now, but it would be interesting if you started gksu from a terminal and captured the output and then after removal of brasero do it again to see difference.

How did you pull that out of the hat. Removal of brasero fixed gksu. Whatever possessed you to do that?

---

### Post by mc4man on 2009-09-22
@ VMC
When i started thinking about it a few things weren't adding up. The post I linked to didn't really seem to say specifically that opening a dir. as root had bee disabled, though it somewhat seemed to.

Also it was working here yesterday (root term. -> nautilus
So I rebooted and saw that it would work once per fresh boot

the logic here is that if it works, even if only once per boot, than it can't be disabled, just broken.

So if it's broken then there'd be bug reports, clearly there are numerous.

in the report I linked if you browse there and some of the dups you'll see mention of reverting brasero to jaunty ver., reverting rhythmbox ect. 

I had already removed rhythmbox while testing the gstreamer pitfdll plugin, so brasero and it's lib were no loss.

(i wouldn't revert if either of those 2 apps are wanted, this should be fixed.

Still 100% percent unclear on whether opening a dir. as root graphically is good, bad or doesn't matter

---

### Post by handaxe on 2009-09-22
```
gksudo nautilus
``` now works as it should in nautilus 2.28, at least for me and according to the devs

HA

---

### Post by mc4man on 2009-09-22
Is fixed with an update of libbrasero-media0 to 2.28.0, ck in update manager, or here [http://packages.ubuntu.com/karmic/libbrasero-media0](http://packages.ubuntu.com/karmic/libbrasero-media0)

---

### Post by oboedad55 on 2009-09-22
> **mc4man said:**
> Is fixed with an update of libbrasero-media0 to 2.28.0, ck in update manager, or here [http://packages.ubuntu.com/karmic/libbrasero-media0](http://packages.ubuntu.com/karmic/libbrasero-media0)

6:30 pm here eastern time, US, and the latest updates have fixed the gksu problem. WooHoo!

---

### Post by kansasnoob on 2009-09-22
Yes! Also the package nautilus-gksu works again!

---

### Post by mc4man on 2009-09-22
What I've just noticed (i think ) is that the new libbrasero-media0 has broken the automount of cd/dvd drives that was just fixed yesterday.(at least on this hardware

In this case though it only affected /dev/sr0 in a 2 drive system (where the cd/dvd drives are on the primary and secondary ide's as master (sata hdd's

Going to ck. on a parallel install that is behind on updates and is all ide

---

### Post by kansasnoob on 2009-09-22
I must also add that I should have known about the 'libbrasero-media0' connection since I wrote this:

> 

This certainly does seem to be related to brasero. If I downgrade to the Jaunty versions of both brasero and libbrasero-media0 that seems to solve the "nautilus as root" problem (both from cli and using the gui 'nautilus-gksu').

I must say however that it's not even a decent work-around because you must also downgrade to the Jaunty version of rhythmbox and it crashes on Karmic.

Just a heads up as far as having this assigned to brasero, maybe more specifically libbrasero-media0. I haven't tried to parse the differences between versions 2.27.91-0 and 2.26.0-0 (not sure what I'd be looking for anyway).


But since then I'd read a lot from forum admins discouraging the process so I assumed it was going to stay that way!

---

### Post by kansasnoob on 2009-09-22
> **mc4man said:**
> What I've just noticed (i think ) is that the new libbrasero-media0 has broken the automount of cd/dvd drives that was just fixed yesterday.(at least on this hardware

In this case though it only affected /dev/sr0 in a 2 drive system (where the cd/dvd drives are on the primary and secondary ide's as master (sata hdd's

Going to ck. on a parallel install that is behind on updates and is all ide

Try installing 'usbmount' from synaptic and rebooting.

---

### Post by mc4man on 2009-09-22
> Try installing 'usbmount' from synaptic and rebooting. 

I'll try that now

just to confirm
On similar hardware (p4), with the exception of being all ide (2 ide hdd's, 2 cd/dvd drives. master and slave on secondary ide) that updating libbrasero-media0 breaks automount on /dev/sr0

Booting up with a data cd/dvd in /dev/sr0 will allow automount for the session.

Will try that lib now

---

### Post by mc4man on 2009-09-22
> 
Will try that lib now

Well it seems to negate whatever the ill effect of the latest libbrasero-media0 had on these p4's

Interesting the 'reach' of libbrasero-media0

---

### Post by oboedad55 on 2009-09-22
> **kansasnoob said:**
> Try installing 'usbmount' from synaptic and rebooting.

No love from usbmount. I can mount from the command line but automount seems to be broken again. Maybe tomorrow?

---

### Post by mc4man on 2009-09-22
small update on the usbmount deal

It works on the p4 that is all ide, ie. /dev/sr0 is on the secondary ide (as master

It **does not wor**k on the p4 where /dev/sr0 is on the primary ide (as master

I forgot to restart the p4 where it doesn't work.

So this still appears to be a bug in brasero

---

### Post by mc4man on 2009-09-22
@ oboedad55

Do a full update, there is a fairly significant one that just came up here, then you should be good for gksu and the automount deal

Edit:
I mentioned in passing before but if you have amarok installed then I'd remove it temporally till your up to date, then re-install. Will prevent getting some partial updates.

Remove both amarok and libtag-extras0

---

### Post by oboedad55 on 2009-09-22
> **mc4man said:**
> @ oboedad55

Do a full update, there is a fairly significant one that just came up here, then you should be good for gksu and the automount deal

Thanks, I just got the update and gksu and automount are both working! Yippee!

---

