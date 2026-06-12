---
title: "install desktop on server 8.04"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by snorkytheweasel on 2008-05-08
The problem is speed - or significant lack thereof.

For openers, I have installed ubu/kubu/xubu - server and desktop - many times since dapper...  I think I have a reasonable expectation of how the process should work. This time, using hardy... the process is not what should happen (assuming that history is a guide).
This is a fresh install, including new partitions and new file system (ext3)
[LIST=1]
[*]install 8.04 server from cd
[*]remove cd / reboot/ logon / put cd back in same drive
[*]using apt-get or aptitude many times, and having to abort each....
[*]apt... update
[*]apt.. install (ubu/kubu/xubu)-desktop
[*]the system goes straight to a mirror; does not pass go, does not ask cd for files
[*]each of several times I've killed the process after a couple of hours
[*]this should take 20-30 minutes, tops
[*]it takes over an hour to get to 10% complete
[*]after 2+ hours it's under 25% and threatens to keep me waiting for another 3-10 hours
[/LIST]

All of this is on a p4-2000 1GB ram

I've had much faster installs on a celeron 700 with 256mb ram - and on this same machine as well.

I have 100mBit to the router, then 1GB fiber out into the vast wasteland. All other things network are performing properly (I know- I'm the SysAdmin)

What's going on? 
How do I fix it?
Why doesn't install look to the cd first?

---

