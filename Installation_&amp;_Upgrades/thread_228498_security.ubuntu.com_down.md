---
title: "security.ubuntu.com down??"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by Jabran Asghar on 2006-08-03
Hi,

I am installing few packages and it seems security.ubuntu.com is down.

I get this error when using apt-get : 

################
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
################


Is there any alternative?

Jabran

---

### Post by wieman01 on 2006-08-03
Same problem here... the trouble started today. Apparently the server is down. Don't worry, I expect that it will be up & running soon again.

---

### Post by Pridkett on 2006-08-03
It appears to be somewhat related to some of the shift of servers that caused similar problems with us.archive.ubuntu.com.  But then again, I have nothing to do with Canonical.

Replace the lines in /etc/apt/sources.list referring to security.ubuntu.com with lines like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

I did that and can now get all the stuff that otherwise was coming from security.ubuntu.com.

---

### Post by Pridkett on 2006-08-03
It appears to be somewhat related to some of the shift of servers that caused similar problems with us.archive.ubuntu.com.  But then again, I have nothing to do with Canonical.

Replace the lines in /etc/apt/sources.list referring to security.ubuntu.com with lines like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

I did that and can now get all the stuff that otherwise was coming from security.ubuntu.com.

---

### Post by wieman01 on 2006-08-03
Thanks, man. That did the trick.

---

### Post by ShirishAg75 on 2006-08-03
I tried but it doesn't work. In fact there are four lines in /etc/apt/sources.list which are to do with security. Is this right or should I delete the 2? I just upgraded to GDM 2.14.3

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe universe multiverse
 instead of the two tht should be there & the ip it's referring to is 82.211.81.138

Although it got 2 of the updates but not all. Any more ideas anybody. Also somebody just write when the main server is up. Thnx in advance.

---

### Post by wieman01 on 2006-08-03
> **shirishag75 said:**
> Although it got 2 of the updates but not all. Any more ideas anybody. Also somebody just write when the main server is up. Thnx in advance.

I think the 2 lines mentioned by Pridkett are sufficient. Yours seem redundant/repetitive.

I also experienced the reverse thing this morning. Now the "security" servers were alright, but the "archive" ones were down. Strange.

There is a source.list generator tool. You may want to play around with it, works well:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by Jabran Asghar on 2006-08-04
The link above for generating sources list is very handy, I liked it :-)

---

