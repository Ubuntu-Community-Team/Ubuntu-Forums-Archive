---
title: "ureadahead error message"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by bountonw on 2010-04-14
Last week I upgraded my daughter's Karmic install to Lucid Beta 2. Everything was fine for the first few days and then we got the following at boot up:

> init: ureadahead main process (274) terminated with status 59

Starting up...

There is a blinking cursor under the 'S' in Starting. It doesn't boot or respond to any escape combinations that I know. Several retries have yielded the same screen.

I read the original post and a few comments [here]("http://ubuntuforums.org/showthread.php?t=1434502") about ureadahead, but did not find anything related to my problem.

---

### Post by bountonw on 2010-04-14
I rebooted in recovery mode using an earlier kernel. 

Repaired grub, which took a couple of minutes only and then fixed the dpkg which took all night.

When I was returned to the recovery menu, I tried booting but got stuck after loading sshd.

Turned off the power and rebooted normally. Now I am have typed
```
sudo apt-get update
``` and am waiting to load the repository. Plan to upgrade everything again and reboot.

Not sure why this is so slow, 5,000 B/s on ADSL at 7AM during a holiday. Taking nearly 15 minutes just to update the repository. ...hmm... must be problem at ubuntu's end. Just loaded a Youtube video almost instantly.

---

