---
title: "upgrade to 11.04 failed. System Broken"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by ZGruk on 2011-06-29
I attempted to upgrade to 11.04 from 10.10. At first it wouldn't download the files because of "authentication failure" after cleaning out my repos down to the basics, it downloaded the files. At some point during the install however, it stopped, saying it had some error and would try running "dpkg --configure -a". That didn't work. Later when I tried to run that command it gave the following error:

```
dpkg: error: parse error near line 20 thousand something: compiz-switch
junk after word in 'priority' field
```

After scanning the forums I failed to find a solution, and attempted to restart the computer (big mistake). It failed to boot saying that "filesystem '/' cannot be mounted press S to skip or M for manual repair" pressing S caused it to lock up, M drops me to a command line. I can access the filesystem in the command line, but it's all read-only

Assistance greatly appreciated :p

---

### Post by mörgæs on 2011-06-29
I guess the fastest solution is to begin anew:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by ZGruk on 2011-06-30
*sigh* I was afraid of that. Oh, well, it's not the end of the world, since I can get all my files. Thanks for the reply.

---

