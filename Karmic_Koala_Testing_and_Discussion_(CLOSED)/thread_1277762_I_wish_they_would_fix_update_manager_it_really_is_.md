---
title: "I wish they would fix update manager it really is buggy."
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-28
I've never known such a buggy essential app  even at alpha stage.

---

### Post by doas777 on 2009-09-28
is the one in karmic signifigantly differant? I've never had a problem with the one they've used since feisty. whats it doin?

---

### Post by FuturePilot on 2009-09-28
What's the problem exactly? It hasn't been giving me any issues really.

---

### Post by shafin on 2009-09-28
I'm having problems with this, too. I'm unable to update through it. It starts alright, but when I hit 'Check for updates', it gives me a waiting cursor which never ends. For now, i'm updating through synaptic,which is quite dangerous.

---

### Post by jpeddicord on 2009-09-28
> **shafin said:**
> I'm having problems with this, too. I'm unable to update through it. It starts alright, but when I hit 'Check for updates', it gives me a waiting cursor which never ends. For now, i'm updating through synaptic,which is quite dangerous.

Check behind the window. There's likely a PolicyKit dialog waiting for your password.

---

### Post by Lightstar on 2009-09-28
> **shafin said:**
> I'm having problems with this, too. I'm unable to update through it. It starts alright, but when I hit 'Check for updates', it gives me a waiting cursor which never ends. For now, i'm updating through synaptic,which is quite dangerous.

should do it through terminal instead of synaptic
sudo apt-get update
sudo apt-get upgrade

---

### Post by kansasnoob on 2009-09-28
The only changes I notice are it asks for a password only after you check for updates, update DL progress is shown in kb or mb rather than # of sources, and it seems faster.

Oh, and if you have new installs and upgrades it asks for authorization for both.

---

### Post by Squonk07 on 2009-09-28
Once or twice I've had updates fail to download, but the last time that happened was over a week ago and I assume that either something got fixed or else it was a server issue.

I do have one nitpicky problem, though. The "Applying updates" box (I think I have the right name--it's the one that shows progress when there are actually updates being installed) still seems to lack an icon, at least on my system. Anybody else having this issue, and is there a simple way to fix it?

---

### Post by philinux on 2009-09-28
> **Lightstar said:**
> should do it through terminal instead of synaptic
sudo apt-get update
sudo apt-get upgrade

This is why we are testing to find bugs not workarounds. :lolflag:

---

### Post by 23meg on 2009-09-28
> **philinux said:**
> This is why we are testing to find bugs not workarounds. :lolflag:

And yet you haven't mentioned a specific behavior that may qualify as a bug.

---

### Post by philinux on 2009-09-29
> **23meg said:**
> And yet you haven't mentioned a specific behavior that may qualify as a bug.

The aptdaemon keeps crashing greys out etc. It's bugged but not fixed yet.

Sometimes the updates go ahead in the backgroud sometimes they fail.

I'm sure it will get sorted.

There a few which have been reported when you search for aptd bugs.

---

### Post by LKjell on 2009-09-29
The thing they should fix is the download dialog. The download speed is hidden.

---

### Post by grandtoubab on 2009-09-29
Hello all,
The first thing is to fix the feature:):lolflag:
Unusable as it crash !!!
Must use the command line to keep updated as Philinux said

---

### Post by Vanishing on 2009-09-29
> **23meg said:**
> And yet you haven't mentioned a specific behavior that may qualify as a bug.

Heres one:
if you do :
> sudo update-manager
instead of 
> update-manager
to fire it up, it WILL fail.

---

### Post by jpeddicord on 2009-09-29
> **Vanishing said:**
> Heres one:
if you do :

instead of 

to fire it up, it WILL fail.

And you shouldn't be doing that...

---

### Post by 23meg on 2009-09-29
> **philinux said:**
> 
I'm sure it will get sorted.

That's never a good thing to assume, since your crashes can be caused by different underlying problems, despite producing an identical outcome.

And please refrain from starting "wish" threads unless you need help reporting a bug or improving an existing report, and be more specific in your original posts.

---

### Post by 23meg on 2009-09-29
> **Vanishing said:**
> Heres one:


There's absolutely no need to run Update Manager as root. Don't do it.

---

### Post by philinux on 2009-09-29
> **23meg said:**
> That's never a good thing to assume, since your crashes can be caused by different underlying problems, despite producing an identical outcome.

And please refrain from starting "wish" threads unless you need help reporting a bug or improving an existing report, and be more specific in your original posts.

I think I'll carry on testing and reporting bugs. But this is a discussion forum too.
Just a wording thing I dont wish for it to be fixed it needs to be fixed and soon.

And this is still a light hearted forum.  So please lighten up.:P
You dont want to put people off testing.

---

### Post by ikt on 2009-09-29
> **23meg said:**
> There's absolutely no need to run Update Manager as root. Don't do it.

what happens if you do?

I understand it will fail, but why?

---

### Post by 23meg on 2009-09-29
> **ikt said:**
> what happens if you do?

I understand it will fail, but why?

Update Manager currently uses Aptdaemon, which in turn uses PolicyKit for fine grained privilege authorization, the whole point of which is to get rid of the need to run your whole application as root.

---

### Post by 23meg on 2009-09-29
> **philinux said:**
> I think I'll carry on testing and reporting bugs. But this is a discussion forum too.
Just a wording thing I dont wish for it to be fixed it needs to be fixed and soon.

And that can't happen unless you report the bug. Starting a thread saying "It needs to be fixed" accomplishes nothing; it just wastes spaces on the thread index that's better reserved for threads that genuinely need attention, and decreases the signal-to-noise ratio.

> **philinux said:**
> And this is still a light hearted forum.  So please lighten up.:P

[There's a separate forum for light hearted general discussion]("http://ubuntuforums.org/forumdisplay.php?f=11"). If this one gets too light hearted it turns into random chat and becomes unproductive, which is something I'm trying to prevent.

---

### Post by hanzomon4 on 2009-09-29
> **philinux said:**
> I think I'll carry on testing and reporting bugs. But this is a discussion forum too.
Just a wording thing I dont wish for it to be fixed it needs to be fixed and soon.

And this is still a light hearted forum.  So please lighten up.:P
You dont want to put people off testing.

+1 every time I see you popup in a thread it's usually down someone's throat. Try yoga... 

My advice would be to file a bug about your specific problem.. I tried looking through the [update-manger bugs]("https://bugs.launchpad.net/ubuntu/+source/update-manager") and the list is huge. I tried to limit it to karmic but did not see how

---

### Post by philinux on 2009-09-29
Oh well! I guess Ill contribute to this thread instead.
[http://ubuntuforums.org/showthread.php?t=1278385](http://ubuntuforums.org/showthread.php?t=1278385)

---

### Post by grandtoubab on 2009-09-30
Hello all,
Gar all those given lessons, just read the bug report inlaunchpad
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/434748](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/434748)

BR:P

---

### Post by 23meg on 2009-09-30
> **philinux said:**
> Oh well! I guess Ill contribute to this thread instead.
[http://ubuntuforums.org/showthread.php?t=1278385](http://ubuntuforums.org/showthread.php?t=1278385)

If you see a thread that you think should not be in this forum, report it to be moved.

---

### Post by Michael.Godawski on 2009-09-30
Guys, relax.:)
Thread closed.

---

