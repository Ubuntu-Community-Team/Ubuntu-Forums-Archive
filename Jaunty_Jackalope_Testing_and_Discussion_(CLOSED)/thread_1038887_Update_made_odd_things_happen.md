---
title: "Update made odd things happen"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-14
Ok, I was posting here and then decided to reboot because I updated.  After grub my PC starts yelling at me (literally beeping) and spits out an error that it can't load a file in /etc
 
After reboot, beeping didnt happen and I didnt get that error, instead black screen and nothing.

Reboot again and beeping and error return along with odd messages, so I ctr-alt-del and toss in my alpha 2 CD.  To my sorrow I realise it is the alternate and I can't live boot.  Reboot and it boots w/o any errors.

Odd...
EDIT: Also odd that I have an encrypted system (all but boot obviously) why would it be looking in /etc without having prompted me for my key yet?

---

### Post by LordVeovis on 2009-01-14
After log into system I was told that it had recovered from an error and I tried to update (by clicking the graphical update in the top right) and I got a crash error about opera, which I hadn't opened yet (posting on laptop atm) and it din't start the update.

---

### Post by BwackNinja on 2009-01-14
might this error have been "udevd [901] cannot open /etc/udev/rules.d: no such file or directory?"

this isn't bugging me much, but its stopping me from getting usplash.

---

### Post by LordVeovis on 2009-01-14
> **BwackNinja said:**
> might this error have been "udevd [901] cannot open /etc/udev/rules.d: no such file or directory?"

this isn't bugging me much, but its stopping me from getting usplash.

Yes.  But it was beeping at me and it sat with that error for about 15-20 seconds then I decided enough beeping and ctrl-alt-del.

The "weird messages" was something about sdb (not drive errors - and /boot isn't on sdb) and writing to cache so I decided i should reboot again (this was beeping at me again - had the /etc/udev/rules.d error too, before the sdb stuff)

---

### Post by autocrosser on 2009-01-14
> **BwackNinja said:**
> might this error have been "udevd [901] cannot open /etc/udev/rules.d: no such file or directory?"

this isn't bugging me much, but its stopping me from getting usplash.

The "noise" is something I've heard quite a bit over the last couple of releases--it is related to the udevd error & causes a conflict with usplash---which sometimes results in system warnings during boot.....It's worse than about this time in Intrepid--then it would only do it if you liked the text with your usplash (splash instead of quiet splash)--to stop the problem---edit your menu.lst for the current kernel & remove the "quiet splash"--you'll only get the B&W text--but no warnings......

---

### Post by LordVeovis on 2009-01-14
I knew I could get rid of splash and quiet for text only, but I prefer usplash.  I just didnt know this was a usplash problem.  Thanks!

---

### Post by autocrosser on 2009-01-14
I've had problems with usplash from Edgy onwards--That's why I'd like to see Ubuntu change to Plymouth--and Plymouth looks MUCH better....;)

---

### Post by LordVeovis on 2009-01-14
> **autocrosser said:**
> I've had problems with usplash from Edgy onwards--That's why I'd like to see Ubuntu change to Plymouth--and Plymouth looks MUCH better....;)

It just doesn't support many video cards at the moment.  But I can't wait!!

---

### Post by tawmas on 2009-01-14
I have the same. I saw an update coming in that I hoped would solve the problem, but it didn't (it actually made it worse, now my PC just beeps once and hangs if started with usplash enabled).

Is there already a bug for this? I can't seem to find one.

---

### Post by LordVeovis on 2009-01-14
> **tawmas said:**
> I have the same. I saw an update coming in that I hoped would solve the problem, but it didn't (it actually made it worse, now my PC just beeps once and hangs if started with usplash enabled).

Is there already a bug for this? I can't seem to find one.

I did not start one.  I need to restart to see if it will still give me issues.  Last time I restarted I did not get an error.

---

### Post by autocrosser on 2009-01-14
I have a old bug report at: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

If you read thru it, you'll find most of the issues you have been having......

---

### Post by Slug71 on 2009-01-14
> **autocrosser said:**
> I've had problems with usplash from Edgy onwards--That's why I'd like to see Ubuntu change to Plymouth--and Plymouth looks MUCH better....;)

Yep, i cant wait! :)

---

### Post by tawmas on 2009-01-15
After another batch of updates, my usplash is back, but I still see the message about /etc/udev/rules.d not being found.

I guess this comes from something in the initramfs, I will try and rebuild it this evening when I'm back from work and see if it clears (udev rules where moved from /etc/udev/rules.d to /var/lib/udev/rules.d, so complaining that the former is missing is a bug).

---

