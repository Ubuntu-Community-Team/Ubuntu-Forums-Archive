---
title: "internet connected but there is a problem"
date: 2016-02-11
forum: Installation &amp; Upgrades
---

### Post by jgw on 2016-02-11
I was trying to install synaptic and kept getting odd errors.   Then I thought I would check my Software & Updates.  I told that to find the best server and got:
W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.201 80]

and

No suitable download server was found

I have something pretty much screwed up but have no clue what it might be.  I have tested my internet connection and it seems to be just fine.  I am sending this email with the same machine that has this problem.  When I enter 91.189.92.201 80 into the firefox address I get a google search.  I am tempted to simply reinstall but thought I would write this in case somebody has an idea.

Thank you...............

---

### Post by newbie-user on 2016-02-11
That just means that those files are not available on the server you tried to get the files from. Just change your repo servers. So instead of using archive.ubuntu.com, use mirror.pnl.gov or another mirror closer to you. You can look at a list of mirrors here: [https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

You can change your mirrors by editing /etc/apt/sources.list

---

### Post by Bashing-om on 2016-02-11
jgw; Hello again:

Well, you have fallen behind the times and got caught in the crunch . -> utopic (14.10) is now End_Of_Life and is no longer supported. I bet now the software repo is turned down !

Upgrade to 15.10 ( or fresh install the current LTS release 14.04 ).

[INDENT][INDENT]time just slips on away
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-02-11
> The requested URL /ubuntu/dists/utopic/main/source/Sources was not found on this server.

Utopic is Ubuntu 14.10 and it was the last interim release to have 18 months support. It reached end of life more than 6 months ago and the repositories are now closed and have been moved.

It gets worse, The next release in line is 15.04 and that reached end of life the first week of February because interim releases now only get 9 months support. So, if you do manage to get upgraded to 15.04 (and there is way to do it) you will then have to upgrade to 15.10.

Better to do a fresh install.

Regards.

---

### Post by QIII on 2016-02-11
Hello!

Before you ask "OK, so how do I do it?" and go down the old-releases upgrade path, let me warn you that it is more likely to result in a ***Significant Emotional Event&#8482;*** than success.

I and most users here would highly recommend against it.  That is why you see the suggestions to do a fresh installation of a supported release.

---

### Post by jgw on 2016-02-12
Thank you all for the responses!  I spent some more time on this one and decided to simply reinstall (124.04.3)   I have now done that and everything is back where it belongs and I can now do what I want.  My real problem, a bit embarrassing, is that I thought I had 14.04 on this machine, I didn't, and, obviously, wasn't paying as much attention as I should have been.  So, I also apologize for this one.  I will mark it closed (If there was a category for 'bogus' I would have used that <G>

Thanks again!!!!!!!!!!!!

---

