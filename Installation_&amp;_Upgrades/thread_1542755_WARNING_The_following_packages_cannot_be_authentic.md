---
title: "WARNING: The following packages cannot be authenticated!"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by iamqiuhui on 2010-07-31
when i install software by apt-get 
the message will appear
i  don't know how to do
install:if there is virus ,,,,,,,
not install: cannot accomplish the task
because i am afraid of this is a malice software

---

### Post by naveen9885 on 2010-07-31
trust ubuntu I am using and i installed the updates like that so far no issues

---

### Post by Deadite81 on 2010-07-31
When it says not authenticated, That generally means you are installing software from an "unofficial" source.  It does not mean that it is malicious, necessarily, just that it's not from an official repository.  If you have enabled the "Universe" repository (like to install Flash, for example, you may get that message).

I recommend reading up on repositories [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Most of what I install/update is "Not Authenticated", but I use lots of alpha/beta junk.

---

### Post by dev.null on 2010-12-15
If the advice above doesn't work, try this thread, it's the only thing that worked for me: [http://ubuntuforums.org/showthread.php?p=7001019#7001019]("http://ubuntuforums.org/showthread.php?p=7001019#7001019")

---

### Post by Dutch70 on 2010-12-15
And also... 
[http://ubuntuforums.org/showthread.php?t=304430](http://ubuntuforums.org/showthread.php?t=304430)

I wouldn't worry about a virus too much.

---

### Post by lewisskinner on 2011-01-30
I'm getting this message as well guys.  I've tried the above solution, but nothing's working.

*sudo apt-get update* gives me a long list of things which seems to work, with a few failures, which it groups at the bottom for me:

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any solutions?  I'm not too worried, but it's bloody annoying to get these warnings every time!

---

### Post by lewisskinner on 2011-02-01
Bump

Anyone help on this?  Please?

---

### Post by oldos2er on 2011-02-01
You'd probably get your question answered quicker by starting your own thread; people don't usually look for new questions in old threads.

Anyway, look at post #18 here: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

---

