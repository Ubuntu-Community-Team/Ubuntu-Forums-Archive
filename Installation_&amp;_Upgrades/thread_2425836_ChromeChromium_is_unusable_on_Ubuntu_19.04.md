---
title: "Chrome/Chromium is unusable on Ubuntu 19.04"
date: 2019-08-31
forum: Installation &amp; Upgrades
---

### Post by UBUminJ on 2019-08-31
I have upgraded from Ubuntu 14.04 to 19.04.
On 14.04, Chrome and Chromium were without any trouble, now on 19.04, they are unusable. It takes ages to load a single page, if at all.
Is that a known problem?

---

### Post by The Cog on 2019-08-31
I'm on Xubuntu 19.04 so it's not quite the same, but I see no such problem. And I haven't seen lots of complaints like this here, so I am guessing it's not a common issue. I wonder it it's a network problem - have you tried Firefox to see it the problem shows there too?

---

### Post by uRock on 2019-08-31
Another thing to try, since I am not sure of the upgrade method you used, is going in your /home folder and hit Ctrl+H to show hidden, then go into the .config folder and rename the google-chrome folder to google-chrome_old. Try Chrome again. If this works, then there was an issue with the old Chrome configurations.

---

### Post by SeijiSensei on 2019-08-31
I'm now using [Brave Browser]("https://www.brave.com/"), a derivative of Chromium, on Kubuntu 19.04. Works like a charm.  I can install add-ons from the Google Chrome store into it as well.

---

### Post by UBUminJ on 2019-08-31
Thank you for the answers. Must be something else, renaming didn't change a think - it takes 10s to display pages. 
The only thing I also changed between my old installation and the new one is that the new one runs on an SSD.

---

### Post by TheFu on 2019-08-31
I would check the DNS settings.  A misconfigured DNS can really slow down browsers.  If you try a few different ones and they all have the same issue, that's probably it.

---

### Post by kurt18947 on 2019-09-01
> **SeijiSensei said:**
> I'm now using [Brave Browser]("https://www.brave.com/"), a derivative of Chromium, on Kubuntu 19.04. Works like a charm.  I can install add-ons from the Google Chrome store into it as well.

Vivaldi is similar, seems to work well as a second browser. Some online forms don't work well with Firefox; missing fields, fields won't accept keyboard entries etc.

---

### Post by SeijiSensei on 2019-09-01
Quick test:  first enter 91.189.94.12 in the address bar. You should see the Canonical home page, and it should pop up pretty much immediately.

Now try entering [https://www.canonical.com/](https://www.canonical.com/). Does it come up as quickly?  If not, you have a DNS problem.

---

