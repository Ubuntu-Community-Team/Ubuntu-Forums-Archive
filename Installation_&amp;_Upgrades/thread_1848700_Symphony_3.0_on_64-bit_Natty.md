---
title: "Symphony 3.0 on 64-bit Natty?"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2011-09-23
I've read and followed the instructions for forcing an install of Symphony:

[http://www-10.lotus.com/ldd/lswiki.nsf/dx/09292009024859AMWEB9ZQ.htm](http://www-10.lotus.com/ldd/lswiki.nsf/dx/09292009024859AMWEB9ZQ.htm)

I get an error when I try the final step of forcing the install, which references some "pre-dependency" issues. I'll post the actual output when I get back to my Ubuntu machine, but thought I'd post now to see if anyone else has tried and succeeded (or failed) to get Symphony 3.0 on a 64-bit Ubuntu system.

I also attempted to download the 64-bit re-packaged .deb, but multiple download attempts aborted, so I have not been able to try that approach, which seems to work for many...not sure what the download issue is, as the related re-packaged 64-bit FP installer seemed to download OK.

[http://www.omgubuntu.co.uk/2010/10/ibm-office-suite-lotus-symphony-3-released/](http://www.omgubuntu.co.uk/2010/10/ibm-office-suite-lotus-symphony-3-released/)

LATER. Here's the command and output:

[B]sudo dpkg --force-architecture -i symphony*386.deb
[sudo] password for MyAccount: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding symphony_3.0-1hardy1_i386.deb containing symphony:i386, pre-dependency problem:
 symphony:i386 pre-depends on libstdc++6
dpkg: error processing symphony_3.0-1hardy1_i386.deb (--install):
 pre-dependency problem - not installing symphony:i386
Errors were encountered while processing:
 symphony_3.0-1hardy1_i386.deb[/B]


Anyone?

*[SIZE="1"]I am actually aware of OpenOffice and LibreOffice and StarOffice and so forth. However, I have an idiosyncratic preference for Lotus Symphony, and am not open at this time to suggestions that I just use one of the others. Thanks.  [/SIZE]*:)

---

### Post by RMOP on 2011-09-24
I'm replying to my own thread rather than editing and marking it solved, because whilst I DID get Symphony installed, I never DID get the IBM-provided instructions to work. Rather, I persisted at the download site for the 64-bit install modification. It wouldn't do a smooth download, but kept aborting as if finished. I ended up pausing and restarting the download before it aborted. I did the pause/restart bit multiple times until the download completed. It then installed just fine. No idea why the download from this site was a problem.

I'd STILL like to know why the rather inelegant instructions from IBM failed.

Anyone know from the output? Thanks.

---

