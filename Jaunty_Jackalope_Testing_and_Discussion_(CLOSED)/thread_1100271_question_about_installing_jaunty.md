---
title: "question about installing jaunty"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sthapit on 2009-03-19
I want to install Jaunty using the daily build from [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current)

I believe this is an alpha release so when the final version is released in April would I have to re-install it or can I just do apt-get update?  

I'm trying to decide whether to wait till April or install now...

---

### Post by blackened on 2009-03-19
Keep using apt-get upgrade and you'll be using the final release when it comes out.

---

### Post by Paqman on 2009-03-19
Wait till April, Jaunty isn't stable yet. There are a ton of updates coming in every day, and any of them could cause breakage.

Best thing to do is stick to Hardy or Intrepid for a little while.

---

### Post by rburkartjo on 2009-03-20
sth yes my advise is also wait for the final release then upgrade. even for experienced users a and b releases can be a challenge. and if you have only one computer i would not recommend it. i really like jj but wait.

---

### Post by SunnyRabbiera on 2009-03-20
Yes its better just to wait.
Besides Jaunty doesnt really offer a lot over intrepid it seems anyhow, Jaunty looks to be a real sleeper.

---

### Post by blackened on 2009-03-21
> **SunnyRabbiera said:**
> ...Jaunty looks to be a real sleeper.

Agreed. There are no glaring differences between Jaunty and Intrepid except ext4 support and the new notification system. 

There has been plenty of full system breakage during this alpha cycle though. Mostly due to the new version of Python.

---

### Post by executorvs on 2009-03-22
I'm using the current daily build and it works. It has fixed a number of bugs that I hadn't had time to fix under intrepid. my suggestion would be if you load the daily build and everything works, then you could disable updates to avoid breakage until a day or two before the RC release.

I don't think this release is a sleeper. I think that Ubuntu has made many improvements over the past 3 years but was experiencing an increasing number of little annoying bugs. This release addresses stability and compatibility. I am glad this was done and hope that it enables some larger more edgy features in the next few releases at which time I would expect they might need to shore up the OS again.

---

### Post by kansasnoob on 2009-03-22
I'm using Jaunty right now with no problems, but an ALPHA or BETA should never be used as your only OS!

Also I see that the daily build for i386 is over 700mb! OOPS! That happens!

If you **must** upgrade from Intrepid then hit Alt > F2 on the keyboard and type:

```
update-manager -d
```

If you want to download use this link;

[http://www.ubuntu.com/testing/jaunty/alpha6#Download%20Alpha%206](http://www.ubuntu.com/testing/jaunty/alpha6#Download%20Alpha%206)

And then update! Currenty there are no automatic updates so you must run "sudo apt-get update" and then launch the update manager to see what's available.

I can say this is a good one! It's a major "wow' regarding speed! But there are bugs!

I love it, but breakage is expected at this stage of development!

---

