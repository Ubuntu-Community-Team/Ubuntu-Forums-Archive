---
title: "Outdated update information error"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by ganna10 on 2012-06-13
Hi all,

Since yesterday an exclamation mark is showing in the taskbar and stating that I have outdated update information.  The update manager is set to automatically update every day and I do have updates that need to installed (e.g. this morning).

I press the 'Check' and receive the following error: Failed to download repository information, Check your Internet connection and with the following details:

W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://de.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found [IP: 141.30.13.10 80]
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Can someone please help me out with this?

Ubuntu details are: 
Ubuntu 12.04 LTS 32-bit
Processor: Intel Core i5-2500CPU @ 3.30GHz x 4

Thanks in advance and if more info is required please let me know!
Jane

---

### Post by dino99 on 2012-06-13
use your browser to check these urls; note that sources are not always available, so no need to try to get them.

---

### Post by ganna10 on 2012-06-14
I have tried all the URLs and for all of them it is the same "Not Found" webpage.

Thanks.

---

### Post by plucky on 2012-06-14
> **ganna10 said:**
> I have tried all the URLs and for all of them it is the same "Not Found" webpage.

Thanks.

> W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...source/Sources](http://de.archive.ubuntu.com/ubuntu/...source/Sources) 404 Not Found [IP: 141.30.13.10 80]

That URL is valid,but it is trying to fetch a file **Sources** instead of **Sources.bz2**.

See [Here](http://de.archive.ubuntu.com/ubuntu/dists/precise/universe/source/)

You could use Synaptic Package Manager and navigate to the Repositories Button and select the MAIN Server to see if that fixes the problem.

> , W:Failed to fetch [http://ppa.launchpad.net/mozillateam...source/Sources](http://ppa.launchpad.net/mozillateam...source/Sources) 404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam...-i386/Packages](http://ppa.launchpad.net/mozillateam...-i386/Packages) 404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/shnatsel/gi...source/Sources](http://ppa.launchpad.net/shnatsel/gi...source/Sources) 404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/shnatsel/gi...-i386/Packages](http://ppa.launchpad.net/shnatsel/gi...-i386/Packages) 404 Not Found

The other two URLs do not have a repository for the **Precise** release.

See [Here](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/) and [Here](http://ppa.launchpad.net/shnatsel/gimp-paint-studio/ubuntu/dists/)

Again,using Synaptic Package Manager and navigating to the repository button,and then under the **Other Software** Tab,delete the two repositories.

Good Luck

---

### Post by ganna10 on 2012-06-15
Thanks a lot for the help.  I changed to the main server and also removed the two repositories and now it works fine.

:-)

---

