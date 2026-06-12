---
title: "less free space (Hardy -&gt; Intrepid -&gt; Jaunty)"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-02-12
[solved]

Well I don't really care about the space - but I have to resize the partition if Ubuntu keeps growing - and I'd rather not do that.

Is this known / does this happen to you / does anybody care?

Less Space after upgrading to Jaunty ~1.7GB.

Also should compiz work on an Ati X700 atm?
I only get:
```
[   99.597154] glxinfo[5627]: segfault at 18 ip b7f73c3a sp bfc05a18 error 4 in libGL.so.1.2[b7f42000+83000]
[   99.606125] glxinfo[5631]: segfault at 18 ip b7f4fc3a sp bfde23d8 error 4 in libGL.so.1.2[b7f1e000+83000]
[   99.640061] glxinfo[5633]: segfault at 18 ip b7e6cc3a sp bfeff518 error 4 in libGL.so.1.2[b7e3b000+83000]
[   99.923038] glxinfo[5655]: segfault at 18 ip b800cc3a sp bfba11a8 error 4 in libGL.so.1.2[b7fdb000+83000]
[  102.091076] compiz.real[5660]: segfault at 0 ip b7e3de15 sp bfb8c850 error 4 in libGL.so.1.2[b7e08000+83000]

```

---

### Post by andrewabc on 2009-02-12
> **excogitation said:**
> Well I don't really care about the space - but I have to resize the partition if Ubuntu keeps growing - and I'd rather not do that.

Is this known / does this happen to you / does anybody care?

Less Space after upgrading to Jaunty ~1.7GB.
[/CODE]

Search synaptic for old kernels that are not being used. I just cleaned my jaunty the other day and removed 700mb of old kernels that were not in use.

---

### Post by praxis22 on 2009-02-12
I seem to remember that you can also remove the package cache, (sorry to be a bit vague) Every program you have downloaded is cached so it can be backed out, this cache can get very large. I think I purged mine before I upgraded to intrepid. It was a while ago :)

---

### Post by excogitation on 2009-02-12
> **andrewabc said:**
> Search synaptic for old kernels that are not being used. I just cleaned my jaunty the other day and removed 700mb of old kernels that were not in use.

> **praxis22 said:**
> I seem to remember that you can also remove the package cache, (sorry to be a bit vague) Every program you have downloaded is cached so it can be backed out, this cache can get very large. I think I purged mine before I upgraded to intrepid. It was a while ago :)
Sorry, my bad - I didn't tell you that I already removed the previous kernels (of course) and deleted the old downloaded archive files.

"apt-get autoclean" is what you're looking for, praxis22.

---

### Post by andrewabc on 2009-02-12
Maybe my next guess is that somehow some logs (maybe boot logs or program logs?) or something is getting larger? maybe something was accidentally enabled that logs everything that happens?

---

### Post by excogitation on 2009-02-12
"apt-get clean" just gave me 1.3 GB back ;-)
Also emptying "/root/.local/share/Trash/files" gave me another 500MB. 

Do you know of a tool that helps you track down what "eats" your disk space?


What about Compiz? is it working for you?

---

### Post by Gourgi on 2009-02-12
> **excogitation said:**
> 
Do you know of a tool that helps you track down what "eats" your disk space?



Applications ->  Accessories -> Disk Usage Analyzer
it's been there by default for a long time and still is usefull :popcorn:

---

### Post by excogitation on 2009-02-12
> **Gourgi said:**
> Applications ->  Accessories -> Disk Usage Analyzer
it's been there by default for a long time and still is usefull :popcorn:

I vaguely remembered such a tool (but shame on me I thought that was in Win). :-\"
Thanks.

---

### Post by excogitation on 2009-02-13
Also I just found 3.3GB "tcpconns" files in /var/lib/collectd/rrd/"user" and another 1.5GB in /var/lib/collectd/rrd/localhost
Where can I check if collectd's tcpconns is now disabled?

Also I wonder if others know they're wasting GB's on those files :D

Now I'm sure this partition can handle some more Ubuntu releases.

---

### Post by ezsit on 2009-02-18
Also, for finding used disk space is "du"

For example:

sudo du -h /var

will give you disk usage of /var in human readable terms.

Very useful command and you can pipe the output to a text file if you want for easier reading.

---

### Post by durand on 2009-02-18
> **excogitation said:**
> Also I just found 3.3GB "tcpconns" files in /var/lib/collectd/rrd/"user" and another 1.5GB in /var/lib/collectd/rrd/localhost
Where can I check if collectd's tcpconns is now disabled?

Also I wonder if others know they're wasting GB's on those files :D

Now I'm sure this partition can handle some more Ubuntu releases.

I don't even have collectd installed. Maybe you installed it yourself?
> collectd - statistics collection and monitoring daemon

---

### Post by zika on 2009-02-18
it might look foolish but check ~/.nautilus/ and ~/.nautilus/metafiles/ and ~/.thumbnails/. I regained a lot of space after deleting (literally)  tens of thousands of files from these places. I've kept just those from several days ago and made appropriate changes so that cache is now restricted to reasonable size. [http://ubuntuforums.org/showthread.php?t=1068084](http://ubuntuforums.org/showthread.php?t=1068084)

---

### Post by BilliShere on 2009-02-18
Bleachbit is an excellent program... it is very similar to ccleaner in windows.. except for ubuntu and (that there is less crap to clean). ;)
run it just like you would run ccleaner on windows... cleaned 1.5 gigs of junk for me.

---

### Post by Therion on 2009-02-18
Try using **QuickStart** (House Cleaning option).  Works like a charm and it's amazing how much junk it removes:

[http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html](http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html)

---

