---
title: "The 'python-zopeinterface' Problem"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2009-09-19
python-zopeinterface is the only package left that won't properly uninstall without removing a buttload of necessary packages like apport and Ubuntu One.  Try to get rid of it in Synaptic and see for yourself.

The Launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/427110](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/427110)

Anyone else see this?  Anyone know where the goof is?

---

### Post by forumache on 2009-09-21
I see it too. It was like that for a couple of days. I subscribed to the bug you linked to.

There is another problem in Synaptic. A long list of "Installed (Manual)" packages. I did not installed them manually. I have manually installed only crossover office, crossover games, and nx server which all appear under "Installed (local or obsolete)". So, what does this Installed (Manual) means in symaptic? It shows "1051 listed, 1502 installed" (this is not a typo, there are 451 packages not listed). On the other hand, the "Installed" item has "1502 listen, 1502 installed", so there is a difference but I was not able to see it.

---

### Post by Leighman on 2009-09-21
If you install its recommended it gets rid of it.  Did for me, at least...

---

### Post by forumache on 2009-09-21
Great!

I removed it from the command line and it was replaced with python-zope.interface, which does not appear in the "removable" list in synaptic anymore.

Problem solved.

```
dan@shuttle:~$ sudo aptitude remove python-zopeinterface
...
The following actions will resolve these dependencies:

Install the following packages:
python-zope.interface [3.5.2-1 (karmic)]

Score is 39
Accept this solution? [Y/n/q/?] 
The following NEW packages will be installed:
  python-zope.interface{a} 
The following packages will be REMOVED:
  python-zopeinterface 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.



```

---

### Post by VMC on 2009-09-21
> **forumache said:**
> I see it too. It was like that for a couple of days. I subscribed to the bug you linked to.

There is another problem in Synaptic. A long list of "Installed (Manual)" packages. I did not installed them manually.....
There's [**_topic_**]("http://ubuntuforums.org/showthread.php?t=1258250&highlight=Synaptic+manual") already on this subject.

---

### Post by forumache on 2009-09-21
> **VMC said:**
> There's [**_topic_**]("http://ubuntuforums.org/showthread.php?t=1258250&highlight=Synaptic+manual") already on this subject.

Thanks for pointing out to the other thread, but it seems to be that one is quite dead (no post for more than one week).

Here I hoped to get an explanation, since this is new behaviour, somehow intended (by looking at the changelog), but not explained. What the beep is "Installed (manual)"? What does it mean? Maybe I should raise a bug, saying that I didn't manually install 1051 packages (it would be hard) and hope to get an explanation there :)

But, if you really want to help, VMC, you said (in the other thread) that you don't see it as being a problem. Care to elaborate?

Thanks.

P.S. I hope TheForkOfJustice does not mind that I "hijacked" his/her thread since the bug reported is now solved.

---

### Post by VMC on 2009-09-21
> **forumache said:**
> But, if you really want to help, VMC, you said (in the other thread) that you don't see it as being a problem. Care to elaborate?
What I said was I didn't see it as a problem. I wasn't sure;still not sure. But, you could take the steps that  [**post#9**]("http://ubuntuforums.org/showpost.php?p=7933396&postcount=9") took, and it removed a lot of stuff. I did.

---

### Post by TheForkOfJustice on 2009-09-21
> **forumache said:**
> 
P.S. I hope TheForkOfJustice does not mind that I "hijacked" his/her thread since the bug reported is now solved.

No problem with it at all. :)

Couldn't have solved anything without you.

---

