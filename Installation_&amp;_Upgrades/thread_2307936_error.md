---
title: "error"
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by dr.drip on 2015-12-29
Upgraded to 15.10 2 weks ago and no troubles till yesterday.....getting this message....everything else works.

  	 	 	 	   W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
 , W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

any help would be appreciated.

---

### Post by dr.drip on 2015-12-29
This is the whole error....


  	 	 	 	   W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
 , W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

---

### Post by Bashing-om on 2015-12-29
dr.drip; Yep;

That is a fact " file not found (404)" ;
see:
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/)
That PPA is not supported in wily .

Remove the PPA for now .. Maybe the Maintainers will catch up soon - maybe ? As the last activity was Apr 2014 .

[INDENT]If it ain't 'buntu
[INDENT][INDENT][INDENT]never can tell
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slickymaster on 2015-12-29
That PPA is either no longer maintained, has no version for your release or has been withdrawn. Disable it in your sources and attempt to update again.

---

### Post by dr.drip on 2016-01-02
had to remove all ppa from the software update to get rid of the errors......I had one for wine, and xbmc also.....

Not real good with Linux yet,,,,was this ok to do, will it still update?

---

### Post by Bashing-om on 2016-01-02
dr.drip; Well ...

Yea and no.

Yes in that the rest of the system will update;
No that the Wine and xbmc PPAs will not update.

Wont hurt at this time to turn them on individually, run ' sudo apt update ' and see the results.

Be even better to run with what is in our software repo:
14.04 - trusty:
```

sysop@1404mini:~$ apt-cache show wine
Version: 1:1.6.2-0ubuntu4
Filename: pool/universe/w/wine1.6/wine_1.6.2-0ubuntu4_amd64.deb

sysop@1404mini:~$ apt-cache show xbmc
Version: 2:12.3+dfsg1-3ubuntu1
Filename: pool/universe/x/xbmc/xbmc_12.3+dfsg1-3ubuntu1_all.deb

``` (ppa-purge)
[INDENT][INDENT]but hey;
[INDENT][INDENT][INDENT]it is what works best for you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-01-02
Bashing-om is right.
If you are a new user, try the versions of Wine and xbmc and other software in the Ubuntu repositories first.
It's easier for you to install, it's easier for us to support.

It's your system, and you are welcome to install non-Ubuntu software and PPAs if you wish.
Of course...you're the one who has to deal with the crashes and errors and problems that sometimes crop up when doing so.

---

### Post by dr.drip on 2016-01-03
Thanks everyone...I will leave off till next LTS which will be 16.04 and then leave well enough alone.

---

### Post by Bashing-om on 2016-01-03
dr.drip; Ho Kay ..

Good 'nuff .
As this situation is now concluded
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread)

When the need arises
[INDENT][INDENT]we are here
[/INDENT][/INDENT]

---

