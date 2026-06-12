---
title: "dpkg locked by another process?"
date: 2010-01-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-01-24
I've seen this error quite a few times over the last few releases of Ubuntu, and it still happens in Lucid.
Scenario: Open Synaptics and Apply updates. Updates are dowloaded and unpacked, but then gives the error: dpkg locked by another process. Same happens with apt-get.

At a guess, I'd say Update Manager has started in the background *after* I started Synaptics (or apt-get).

EDIT: If I dismiss the error and click Apply again in Synaptics, it proceeds normally.

---

### Post by VMC on 2010-01-24
I believe your right, in thinking update-manager is looking for updates.

Next time use the 'top' command and see if in fact there is a process to verify that.

---

### Post by phenest on 2010-01-24
What I have noticed is update-notifier doing something when synaptic is already running.

---

### Post by ranch hand on 2010-01-24
I haven't had trouble with it here in 10.04 in that manner (so far) and my past experience is moot because I get rid of as much of Update Mangler as you can as soon as I install an OS.  It is a complete pain all the way around.

I leave it on these testing OS' to see what it does.  I did go to System>Preferences>Startup Applications and uncheck Update Notifier.  This may do it for you unless you like the bugger.

---

### Post by phenest on 2010-01-24
> **ranch hand said:**
> I haven't had trouble with it here in 10.04 in that manner (so far) and my past experience is moot because I get rid of as much of Update Mangler as you can as soon as I install an OS.  It is a complete pain all the way around.

I leave it on these testing OS' to see what it does.  I did go to System>Preferences>Startup Applications and uncheck Update Notifier.  This may do it for you unless you like the bugger.

That's as maybe, but it doesn't fix the problem. We are testing, after all.

---

### Post by ranch hand on 2010-01-24
Yup, I know.  Update Mangler is likely to give me a stroke though.  I just loath it.  The notifier is too much to stand.

---

### Post by VMC on 2010-01-24
I haven't touched update notifier or update-manager and I never see it. Maybe because I don't give it time to respond. I usually run aptitude updates when I boot up. But even so, sometimes I don't and I still never see those outputs.

---

### Post by ranch hand on 2010-01-24
> **VMC said:**
> I haven't touched update notifier or update-manager and I never see it. Maybe because I don't give it time to respond. I usually run aptitude updates when I boot up. But even so, sometimes I don't and I still never see those outputs.
You are lucky.  The bugger is not working on your box.  Congratulations.

---

### Post by 23meg on 2010-01-24
Solving this problem will be among the benefits of using a lockless backend such as PackageKit or Aptdaemon. Software Center currently uses Aptdaemon; Update Manager switched to the Aptdaemon backend during the Karmic development cycle too, but it returned to using the Synaptic backend due to problems.

---

### Post by phenest on 2010-01-24
Should this be reported as a bug, or is it work in progress?

---

### Post by xebian on 2010-01-24
> **phenest said:**
> Should this be reported as a bug, or is it work in progress?

Please don't.  It's there for a simple reason -  only one hand in the cookie jar at one time.

This idea of a lockless apt is getting out of hand.  At some point you have to dip your hand in the jar, and you just have to obey one simple rule - only one hand in the cookie jar at one time (repeated for clarity).

---

### Post by phenest on 2010-01-24
> **xebian said:**
> Please don't.  It's there for a simple reason -  only one hand in the cookie jar at one time.

This idea of a lockless apt is getting out of hand.  At some point you have to dip your hand in the jar, and you just have to obey one simple rule - only one hand in the cookie jar at one time (repeated for clarity).

Exactly my point. If synaptic is already open, should update-notifier being jumping in?

---

### Post by xebian on 2010-01-24
> **phenest said:**
> Exactly my point. If synaptic is already open, should update-notifier being jumping in?

It's not that it's jumping in.  It may have been started earlier. Let it finish it's job.  

Or, check your preference-> start-up and disable it.

Also, in Synaptic->Settings->repositories->update tab, there is something about Auto checking updates.  Disable it.

---

### Post by ranch hand on 2010-01-24
> **xebian said:**
> it's not that it's jumping in.  It may have been started earlier. Let it finish it's job.  

Or, check your preference-> start-up and disable it.

Also, in synaptic->settings->repositories->update tab, there is something about auto checking updates.  Disable it.
+324

---

### Post by phenest on 2010-01-25
> **xebian said:**
> It's not that it's jumping in.  It may have been started earlier. Let it finish it's job.  

Or, check your preference-> start-up and disable it.

Also, in Synaptic->Settings->repositories->update tab, there is something about Auto checking updates.  Disable it.

If it started earlier then surely I shouldn't be able to start synaptic? Also, if it was already running, how am I to know if there is no notification icon?

Disabling something doesn't fix it.

---

### Post by D3V11 on 2010-01-25
If it's disabled, it doesn't start...if it doesn't start it can't use the same resources you're trying to access.

---

### Post by emarkay on 2010-01-25
I have seen this too, but  a reboot usually "frees" things.

---

