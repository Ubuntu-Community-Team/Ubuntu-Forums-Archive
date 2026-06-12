---
title: "Update Error"
date: 2016-03-04
forum: MINT
---

### Post by David_Elliott on 2016-03-04
My Update icon shows a red x on it and I get this error message.
Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Dennis N on 2016-03-04
Google no longer provides updates for Chrome 32-bit version starting in March (now). If you have a 32-bit processor, I guess that means the end of the line. If you have a 64-bit processor, you can install the 64-bit version and continue with that. 

> On Linux, Chrome is going 64-bit only at the start of March, 2016. If you still have the 32-bit version installed, you can visit the Google Chrome download page and install the 64-bit version now. If you&#8217;re using a 32-bit version of your Linux distribution, you should probably upgrade to a 64-bit version.

source: [http://www.howtogeek.com/241501/you-should-upgrade-to-64-bit-chrome.-its-more-secure-stable-and-speedy/](http://www.howtogeek.com/241501/you-should-upgrade-to-64-bit-chrome.-its-more-secure-stable-and-speedy/)

---

### Post by David_Elliott on 2016-03-04
I do have both a 64 bit processor and a 64 bit Chrome OS.

---

### Post by presto1232 on 2016-03-05
type into chrome: chrome://help/  and navigate to the "About" page. It will tell you what you have installed, and report back here. If you, indeed have 64 bit Chrome, then the fix is easy, but if you have 32 bit, then you'll just have to uncheck that repo to suppress the error messages.
According to that output above, you at least have the repo for 32bit, all i386 is for 32 bit systems: [COLOR=#000000]'main/binary-i386/Packages'  

[/COLOR]

> **Dennis N said:**
> Google no longer provides updates for Chrome 32-bit version starting in March (now). If you have a 32-bit processor, I guess that means the end of the line. If you have a 64-bit processor, you can install the 64-bit version and continue with that. 



source: [http://www.howtogeek.com/241501/you-should-upgrade-to-64-bit-chrome.-its-more-secure-stable-and-speedy/](http://www.howtogeek.com/241501/you-should-upgrade-to-64-bit-chrome.-its-more-secure-stable-and-speedy/)

Funny how they completely take it away, and tell you to get the 64 bit, despite the fact that if you're running a 32 bit operating system, it won't work. Not liking the path Google is going.

---

### Post by deadflowr on 2016-03-05
The error is actually a packaging error by google.
Does not matter if you are running 32-bit version or 64-bit version.

See: [http://ubuntuforums.org/showthread.php?t=2315941](http://ubuntuforums.org/showthread.php?t=2315941)
for solution.

---

### Post by presto1232 on 2016-03-05
Ooh, yeah, checked my own repos and they were disabled. When I enabled it, I got the same error. Silly.

---

