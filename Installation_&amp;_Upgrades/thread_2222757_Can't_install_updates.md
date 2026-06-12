---
title: "Can't install updates"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by i6Shot on 2014-05-08
Hello,

For a few days now I have had a problem installing my updates. I have the following output:

```
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting: 
reading files list for package 'linux-headers-3.2.0-60-generic': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

I'm really at a loss as to what the problem is and how I can solve it. Let me know what you need from me and I can provide it. 

Thanks in advance,

Luke

---

### Post by Slopsbucket on 2014-05-08
Hi Luke,

Looks like you're not the first one to have this problem.

The answer appears to be:

1. Go into the /var/lib/dpkg directory
2. Make a backup of the "status" file
3. Edit the "status" file
4. Search the package that gave the error
5. Just delete the lines from this package (but let all other lines that  concern other packages even if they contains the broken package in  their "Replaces" or "Depends" fields)

Shamelessly taken from [http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143)

Just out of curiosity, did you suffer a power cut just before this happened?

Cheers,

Andrew.

---

### Post by i6Shot on 2014-05-08
Hey Andrew,

Cheers for the post. You know I came across that post and thought I had done it word for word yet upon redoing it I found I hadn't.....whoops!?
Everything seems to be working fine now.

To be honest I can't remember how this issue came about. 

Cheers for your post,

Luke

---

