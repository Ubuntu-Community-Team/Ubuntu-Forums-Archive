---
title: "Unusual CUPS problem"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by unknown14 on 2016-05-05
Hi,

I have a gigabyte Z170X-UD5 motherboard, skylake cpu and two ethernet connections (might be significant) anyway, ubuntu installed ok, no graphics freezes etc that open suse leap42.1 gives, but with open suse and with ubuntu if I enter "localhost:631 in the browser directly I get nothing, if I follow a link in a webpage that points to the same place ( bottom of this page, for example: [http://hplipopensource.com/node/231](http://hplipopensource.com/node/231) ) I get the cups opening page, but all further pages are denied to me, I have opened up the CUPS conf page with the suggestions on that page and this one: [http://ubuntuforums.org/showthread.php?p=4916761#post4916761](http://ubuntuforums.org/showthread.php?p=4916761#post4916761) but still getting no further.
Any suggestions?

---

### Post by unknown14 on 2016-05-06
well I go to [http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

then they have the following link there for admin,

[http://localhost:631/admin](http://localhost:631/admin)

but that is alway denied to me in any browser I try, any suggestions please?

---

### Post by ian-weisser on 2016-05-06
Check that cups is running:
On 16.04,
```
service cups status
```
Look for the 'Active', which wil tell you if it is running or not.

If cups isn't running, restart it.
```
service cups restart
```

---

### Post by unknown14 on 2016-05-07
Hi,

Yes it is running, and it is infuriating that it is in, I can get to the printer web page, I can get to the first Cups page indirectly, and on suse could get to the other help pages, but it will not let me administer it.

---

### Post by unknown14 on 2016-05-07
Hi, 

Consider this now fixed, blundered into a config change that allowed me to access the CUPS admin pages, doable from thereon, couple of false starts misentering things, but now able to print, YAY.

---

