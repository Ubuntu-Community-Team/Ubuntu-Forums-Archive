---
title: "Empathy not connecting to MSN"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jpaisneto on 2009-10-04
Hi everyone! I have Karmic with all the updates and I wanted to test Empathy, but when I try to sign in to msn it just keeps signing in forever! I only see the connecting sign moving next to my status. I tried using Gtalk and it worked, but can't use MSN :( Any way to solve this?

P.S. - Tried to remove and install again using Ubuntu Software Center and it's still the same ... I don't know if it helps but the debug gives 2 warnings: GLib-GObject-WARNING: 1.254694e+09: instance of invalid non-instantiatable type `(null)'
GLib-GObject-CRITICAL: 1.254694e+09: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

---

### Post by jpaisneto on 2009-10-04
Filled bug at [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/442686](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/442686)

Hope I did it right :s

---

### Post by tuxxy on 2009-10-04
Bug looks ok but I have signed into empathy before, I use aMSN mostly but empathy definitely worked when I tested.

---

### Post by jpaisneto on 2009-10-04
> **tuxxy said:**
> Bug looks ok but I have signed into empathy before, I use aMSN mostly but empathy definitely worked when I tested.

I read in forums many people can sign in to msn, I don't know why I can't :confused: And it doesn't give any error and when I have aMSN on it even signs me off aMSN but it never really gets to sign in ....

---

### Post by dext on 2009-10-04
> **jpaisneto said:**
> I read in forums many people can sign in to msn, I don't know why I can't :confused: And it doesn't give any error and when I have aMSN on it even signs me off aMSN but it never really gets to sign in ....

try installing the **telepathy-butterfly** package

---

### Post by jpaisneto on 2009-10-05
> **dext said:**
> try installing the **telepathy-butterfly** package

Telepathy-butterfly is installed... Do you want me to reinstall it?

---

### Post by Amodef on 2009-10-05
I've the same problem than you. I've 2 msn addresses, I can connect with one but not the other.

Of course, my two addresses was working before...

If someone has a solution, please share :) .

---

### Post by phenest on 2009-10-05
Works fine here with my @msn.com address.

---

### Post by dext on 2009-10-05
> **jpaisneto said:**
> Telepathy-butterfly is installed... Do you want me to reinstall it?

ok try this *remove telepathy-butterfly* an you should just have *telepathy-haze* installed try connecting with that

---

### Post by jperez on 2009-10-06
All that to get Empathy to connect to MSN/Live servers? :|

I'll stick with Pidgin.  I don't mind doing the extra work to get it to connect with Empathy, but that's just...well...inconvenient...especially when Karmic is supposed to be much better about stuff like this.

I couldn't connect with my Live account in Empathy, but on Pidgin, it's perfect.  Ah well.

Jesse~

---

### Post by dext on 2009-10-06
> **jperez said:**
> All that to get Empathy to connect to MSN/Live servers? :|

I'll stick with Pidgin.  I don't mind doing the extra work to get it to connect with Empathy, but that's just...well...inconvenient...especially when Karmic is supposed to be much better about stuff like this.

I couldn't connect with my Live account in Empathy, but on Pidgin, it's perfect.  Ah well.

Jesse~you use Linux yeah? this aint windows im afraid, to findout why it isnt connecting its best to do these things incase there's a Bug in Ubuntu's telepathy packages. but if pidgin works for you, by all means use it

---

### Post by jperez on 2009-10-06
Please don't throw a "Used to Windows?" attitude at me.  It's not warranted.  Plus, I'm used to Ubuntu and Windows and Mac.  Thanks...

I'm speaking in terms of Karmic vs older Ubuntu versions.  I didn't really hear about Empathy not working properly before and only during Karmic is that an issue, again, from what I hear.

And yes, Pidgin does work better for me, thus why I said I'd use it, but still showing contrast to it working completely out-of-the-box as opposed to Empathy.

Please, next time, don't talk down to people like they don't know how to use Linux or that they never have.  It's rude, condescending and makes you look like a jerk.

Jesse~

---

### Post by dext on 2009-10-06
if your not prepared to do what i asked and or suggested im gonna opt out of this thread. goodluck getting your problem solved <sarcasm>

---

### Post by jpaisneto on 2009-10-07
> **dext said:**
> ok try this *remove telepathy-butterfly* an you should just have *telepathy-haze* installed try connecting with that

Thank you, uninstalled telepathy-butterfly and works now :D

Any idea why this happened? :confused:

---

### Post by nodius on 2009-10-08
Same with me, after reading this thread I've removed telepathy-butterfly and I can finally connect to msn with empathy.

---

### Post by jpaisneto on 2009-10-13
So, after today's updates empathy started working with telepathy-butterfly. I don't know what caused this, although there was an update for something called python-papyon. Looked it up on karmic changes mailing list and says 
"papyon (0.4.2-1ubuntu3) karmic; urgency=low

  * debian/patches/03_git_fix_utf8_problem.patch: fixes login in cases with
    unicode conversion errors. (LP: #439638)" and
"Description: 
 python-papyon - MSN client library written in Python"

([https://lists.ubuntu.com/archives/karmic-changes/2009-October/010937.html](https://lists.ubuntu.com/archives/karmic-changes/2009-October/010937.html))

Think the problem is solved, thank you everybody :)

---

