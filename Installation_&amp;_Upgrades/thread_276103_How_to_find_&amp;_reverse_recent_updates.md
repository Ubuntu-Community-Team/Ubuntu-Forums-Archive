---
title: "How to find &amp; reverse recent updates?"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by andnos on 2006-10-12
Hi, I automatically installed some updates yesterday, about 10 of them, and now my nxclient won't work for remote desktop. 

My question is how do I find out the last most recent updates, and is there a way to reverse them? 

or is there a way to reverse back to a certain date? say back two days?

any ideas would be appreciated.

---

### Post by dannyboy79 on 2006-10-12
i think you could look at your apt log? open the log viewer within system, admin, log viewer (i think) than go up to the file tab and hit open, it should take you to where most all the logs are kept, then look for apt. it's worth a try anyway. otherwise I don't know but that is something I would love to make sure I knew how to do just in case! Oh, if you do find a log that tells you what was updated, you would probably have to either sudo aptitude remove blahblah or use the gui to remove them one by one.


So if you find out, please post back and let us all know.,

---

### Post by andnos on 2006-10-12
I got it figured out, when I rebooted, it actually gave me an error, and I uninstalled the package that I previously installed.

---

