---
title: "Lucid-Thunderbird fail - SSL protocol has been disabled."
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-13
"Could not initialize the browser's security component - Now that's an an old error one could usually ignore, but then I get "TB can't connect because the SSP protocol has been disabled."  Not good.

Just noticed this , but anyone else getting this?

Any ideas?

---

### Post by ranch hand on 2010-02-13
Mine is currently downloading 99 messages.

---

### Post by emarkay on 2010-02-13
> **ranch hand said:**
> Mine is currently downloading 99 messages.

So yours is OK...  Cool - any ideas to investigate here? 

BTW this is with AT&T's broadband.

---

### Post by ranch hand on 2010-02-13
You might want to have dpkg reconfigure TB.

---

### Post by Yellow Pasque on 2010-02-13
My TB is fine. Look under Edit -> Preferences -> Advanced -> Config Editor and make sure the security.enable_ssl3 key is true. If that's okay, maybe reinstall libnss3-1d package.

---

### Post by emarkay on 2010-02-14
> **Temüjin said:**
> My TB is fine. Look under Edit -> Preferences -> Advanced -> Config Editor and make sure the security.enable_ssl3 key is true. If that's okay, maybe reinstall libnss3-1d package.

First was "true" and I did second, and problem seems OK now!

Thanks!

---

### Post by emarkay on 2010-02-15
Well, problem is back now...  "Unsolved" this till I find out more...

---

### Post by emarkay on 2010-02-22
Looks like they updated us to TB3 - will see if this still appears....

---

### Post by napzilla on 2010-04-10
Oh, hey, I just noticed that this was a posting for "Lucid". I'm still on "Karmic", but I am having the same problem...

I am encountering the same problem here, and *nothing* I've tried has done a thing to help. The weird thing is, this failure started after I let Firefox update, but Firefox works fine. The only app having issues is Thunderbird.

Anyway, I've attempted the following solutions so far:
[LIST]
[*]I have plenty of disk space
[*]There's no read/write restrictions on files in my profile
[*]I tried removing all three *.db files
[*]I tried creating a new profile
[*]I tried removing my Thunderbird profile
[*]I tried removing my Thunderbird, Firefox, and Sunbird profiles just for the hell of it
[*]I tried removing the Thunderbird directory from my home directory and removing it with apt-get purge, followed by a fresh install
[*]I checked, and ss3 is enabled
[*]I tried reinstalling libnss3-1d
[*]I tried sacrificing 13 virgins during a full moon
[/LIST]
As I said, not one of these has done me a bit of good. No matter what I do, still see that damned evil "Could not initialize the browser's security component..." message when I start Thunderbird, and then I get a series of messages telling me Thunderbird couldn't connect to any of my accounts because SSL is disabled.
](*,)
I've run out of possible solutions. Does anybody have any other ideas?

---

### Post by morozj on 2010-04-11
You are not alone napzilla, this happened to me exactly as you describe, after the update that occurred yesterday. I haven't tried many solutions as I was hoping it was an error in the update and another one would be sent soon to fix it, but it looks like it is only affecting a few people. 

If whoever issued yesterday's update is reading, please help, or anyone else who has managed to resolve the problem.

---

### Post by mrkaic on 2010-04-11
I have exactly the same problem that appeared after the last update. I have tried all remedies that are described on different forums--to no avail.

Please someone look into this, it has seriously impaired the productivity of several ubuntu users!

Mico

---

### Post by morozj on 2010-04-11
The bug has been reported and is being worked on. Meanwhile the solution is simple.

Go into Synaptic package manager, search for package 'libnss3-0d' and remove it. Now Thunderbird works again, phew!

Not sure what else the package is supposed to do but presumably we can do without it until the fix has been found.

---

### Post by WendyWeber on 2010-04-11
same here, I'm on Karmic, Thunderbird says that ssl has been disabled. Removing libnss3-0d worked for me.

---

### Post by lubeck on 2010-04-11
THIS WAS A BIG ONE AND _THIS IS_ THE FIX! Could be affecting many,many users. 

FIX of deleting libnss3-0d using Synaptec worked after trying nearly everything else.  Had disabled business email for days. Serious stuff. MUST GET THIS to Mozilla, if anyone knows how.

Thanks loads.

---

### Post by emarkay on 2010-04-12
> **morozj said:**
> The bug has been reported and is being worked on. Meanwhile the solution is simple.

Go into Synaptic package manager, search for package 'libnss3-0d' and remove it. Now Thunderbird works again, phew!

Not sure what else the package is supposed to do but presumably we can do without it until the fix has been found.


Got a Bug# - and is this a Bugzilla or a Launchapd issue? 

Also, as OP, this seems to be working fine still, now, marking "solved".  May want to start a new thread on this!

---

### Post by morozj on 2010-04-12
The link to the bug page is

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/559918](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/559918)

Glad to have my email back, hopefully it hasn't put too many people off Ubuntu and that such a far reaching bug doesn't occur again.

---

