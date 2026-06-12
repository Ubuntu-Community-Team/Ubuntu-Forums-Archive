---
title: "Thinking about doing a clean reinstall"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by finlost on 2008-08-25
I have been running Hardy Heron for roughly two months.  It was a new hardware build, so the install was a fresh install.  I don't remember any issues from the install.  I have installed all current updates when prompted to do so.

Lately, especially today, I am having a lot of lock ups.  I must have rebooted ten times today (hold in the power button) due to lock ups.

It is difficult to say what the issue could be.  I am very green to Linux/Ubuntu so I really don't know how to track down problems.

Generally, the lock ups have occurred in Firefox. I by far spend a majority of my time on Firefox on the Ubuntu box.  If I am lucky, I can just kill Firefox and resume from there.  More often than not, the entire box is locked up and I have to hold in the power button. 

Compiz might also be a culprit.  The reason for suspecting Compiz is due to it becoming disabled quite frequently.  By disabled, the visual effects almost always switch back to "none".  I toggle it back to "Custom" only later to find it back to "none".   

Yesterday, I installed Deluge.  Today was the first day of running it.  I am not sure if Deluge contributed to my more than normal number of lock ups.

I also have Evolution running quite often.  I don't suspect Evolution because it seems to function without issue.

One of my lock ups today occurred while running Deluge and RhythmBox.  The MP3s RhythmBox was playing reside on an external USB HDD.

I am debating whether to uninstall and a reinstall of Compiz and possibly Firefox.  I am also debating to start over with a fresh install of the entire operating system.  I am also debating on just waiting for release 8.10 to do a fresh install.

Thoughts on my next move?

---

### Post by Sef on 2008-08-25
1) I would turn off Compiz-fusion and see if the problems still occur or not.

2) What are your system specs?

3) Have you done a mem86 test to make sure your ram is good?

---

### Post by finlost on 2008-08-25
I looked at removing Compiz.  I highly suspect Compiz if it is a software issue.  I need to search the forums to remember the exact packages I installed for Compiz.  Synaptic has quite a few Compiz packages installed.  I could be wrong, but I don't recall installing more than a couple packages when initially installed Compiz.

I will take a look at the memory test.  I hadn't thought of that.

Thanks for the suggestions.  I will report back with updates/conclusions.

---

### Post by finlost on 2008-08-25
What is an appropriate amount of time to run Mem86 test?  It has run 17 times without errors for the past 7 hours.

---

### Post by finlost on 2008-08-25
I ended up letting Mem86 test run for about 8 hours or 20 cycles.  It ran without any errors. 

I was still having substantial crash problems this morning.  I think Deluge and Compiz don't play well together.  I have disabled Compiz and things seem to be running smoother.  I have not had much opportunity to use Ubuntu now that Compiz is disabled.  I should know within the next few days if Compiz was the problem.

Is there a utility to check the HDD for bad sectors?

---

### Post by finlost on 2008-08-26
I think I have the lockup problem solved....the wireless card.
[COLOR="Blue"]
_[This is the wireless card.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041") _
[/COLOR]
The wireless card was recognized without issues when I initially installed Hardy Heron.  I had the occasional frozen software application and very infrequent lockups.  These were slight inconveniences that I was willing to deal with.  In recent weeks, lockups became the norm.  In the past days, my machine was almost inoperable with lockups happening nonstop.

I am curious what changed or became corrupted.  I have been accepting the updates pushed to me.  Hopefully Ubuntu 8.10 addresses this issue.  I believe I read a top priority of this October's release is wireless issues.

I uninstalled Compiz and Emerald.  I will have to reinstall them to see if if was truly the wireless card.  I think Compiz and Emerald will do just fine once reinstalled.

---

