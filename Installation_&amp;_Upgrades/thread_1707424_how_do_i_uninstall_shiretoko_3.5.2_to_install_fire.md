---
title: "how do i uninstall shiretoko 3.5.2 to install firefox 4 rc1"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by jewfromdahood on 2011-03-15
I have an Ubuntu x86_64 system, with custom kernel on 10.10. I can't firgure out how to remove it, and am still a bit of a noob. So I tried purging on the command line using:
sudo apt-remove purge firefox*
removed it all then 
sudo apt-get install firefox 
to reinstall and still when i open it is still saying and showing shiretoko 3.5.2 in the about section
I've been using Google Chrome, which I do love to fill the void of a good browser, Probably won't go back to firefox, but some things I use only work on firefox and not on chrome yet. But I want to check it out.
Also what sites can I use to test the browsers, I know of the acid3 test, any other tests I can run to benchmark a browser, not the internet speed, but the browser.

---

### Post by Frogs Hair on 2011-03-15
After the purge remove the Shiretoko source from your software sources list . I was wondering what version of Ubuntu you are running because Firefox 3.5. XX is a bit outdated considering the FF 4 release candidate is out. For benchmarks run the test at the link.   [http://clients.futuremark.com/peacekeeper/index.action](http://clients.futuremark.com/peacekeeper/index.action)

---

