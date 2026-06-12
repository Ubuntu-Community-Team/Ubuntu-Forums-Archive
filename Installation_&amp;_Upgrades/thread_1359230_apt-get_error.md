---
title: "apt-get error"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by NJ0E on 2009-12-19
Hello all,

tried to ad a repository this morning.  after adding it I was given the following error and then the computer locked up and had to be restarted.  I deleted the repository but was intrested to see if anyone had some information on this error.  I'll try and submit it to the bug report as well.

Error:
E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory
E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Thanks for the help.

---

### Post by snowpine on 2009-12-19
Without more details, all I can tell you is, you added the repository incorrectly (at line 63 of /etc/apt/sources.list).

You can edit this file with: 

```
gksu gedit /etc/apt/sources.list
```

or

```
sudo nano /etc/apt/sources.list
```

It would be helpful if you told the details: which repository were you trying to add, and why? In my experience, new users are better off sticking with the main Ubuntu repositories if stability is an important goal.

---

### Post by presence1960 on 2009-12-19
> **NJ0E said:**
> Hello all,

tried to ad a repository this morning.  after adding it I was given the following error and then the computer locked up and had to be restarted.  I deleted the repository but was intrested to see if anyone had some information on this error.  I'll try and submit it to the bug report as well.

Error:
E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory
E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Thanks for the help.
That is a common error meaning line 63 had an error in it. Try adding the repository again.

---

### Post by NJ0E on 2009-12-19
snowpine, thanks for the "help" here is teh repository that I was trying to add.  I had to hand jam it, for some reason copy paste wouldn't work.  

I do admit that I am new to some of Ubuntu, but I do know how to add repositories.  As I stated -- I deleted the repository and all is fine.

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/

---

### Post by utnubuuser on 2009-12-19
sometimes web-page formating gets in the way. A safe work-around is to copy, paste to gedit, then re-copy from gedit to make sure you've got clean commands.

---

