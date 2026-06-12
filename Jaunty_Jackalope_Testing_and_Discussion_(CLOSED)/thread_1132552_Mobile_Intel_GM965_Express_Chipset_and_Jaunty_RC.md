---
title: "Mobile Intel GM965 Express Chipset and Jaunty RC"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by regonzal on 2009-04-22
I took heed of the release notes for the RC of Jaunty, and various threads on this forum, concerning performance regression in certain Intel graphic models. I have seen various work-arounds namely:

[http://ubuntuforums.org/showthread.php?t=1130582&highlight=x3100](http://ubuntuforums.org/showthread.php?t=1130582&highlight=x3100)

And, while I have wanted to try it out, I first wanted to check if any of these performance regressions affected Mobile Intel® GM965 Express Chipset models. The Live-CD worked fine and after the initial install things were great, after the first batch of upgrades the desktop effects were turned off and inaccessible. What could be causing this?

**Solution to this issue on post #8**

---

### Post by 00b00nt00 on 2009-04-22
I think the RC turns off desktop effects because of an underlying stability issue with Intel chipsets. I can get UXA working stably on my GM945 chipset, but only with desktop effects turned off.

---

### Post by Zorael on 2009-04-22
If you're feeling adventurous, you could add [the xorg-edgers ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) to get a fresher driver, which may or may not work better.
```
$ echo deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main | sudo tee /etc/apt/sources.list.d/xorg-edgers.list
$ echo deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main | sudo tee -a /etc/apt/sources.list.d/xorg-edgers.list
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
$ sudo aptitude update
$ sudo aptitude full-upgrade
```
Do note that if for some reason stuff gets botched and X won't load, you'll need some terminal knowhow to revert to an older driver. Shouldn't happen, though. But still.

---

### Post by andrewabc on 2009-04-22
As far as I know, intel 965 should not be blacklisted. It wasn't when I was testing RC, and it worked fine testing from livecd and liveusb. I have intel 965 x3000.

I thought they were only having serious problems with intel 950 and below?

---

### Post by nowardev on 2009-04-22
I Have solved installing old driver.

---

### Post by regonzal on 2009-04-22
> **andrewabc said:**
> As far as I know, intel 965 should not be blacklisted. It wasn't when I was testing RC, and it worked fine testing from livecd and liveusb. I have intel 965 x3000.

I thought they were only having serious problems with intel 950 and below?

It did work as well when testing the RC but after the first batch of upgrades after installation I could no longer enable the desktop effects.

---

### Post by forcotton on 2009-04-22
These drivers bring me borked fonts in Firefox 3.5beta. Otherwise it seems to be OK.

---

### Post by regonzal on 2009-04-22
> **regonzal said:**
> I took heed of the release notes for the RC of Jaunty, and various threads on this forum, concerning performance regression in certain Intel graphic models. I have seen various work-arounds namely:

[http://ubuntuforums.org/showthread.php?t=1130582&highlight=x3100](http://ubuntuforums.org/showthread.php?t=1130582&highlight=x3100)

And, while I have wanted to try it out, I first wanted to check if any of these performance regressions affected Mobile Intel® GM965 Express Chipset models. The Live-CD worked fine and after the initial install things were great, after the first batch of upgrades the desktop effects were turned off and inaccessible. What could be causing this?

I was able to find a solution to this issue in the following thread at Launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821/comments/7](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821/comments/7)

I hope this helps anyone experiencing this issue. It seems that the driver was blacklisted, but can be turned on by running these simple instructions courtesy of Shang Wu:

For anyone's video card does not freeze but still want to have their compiz enabled, can try to create a script under the home directory called: compiz_enable.sh with the content:

#!/bin/bash

SKIP_CHECKS=yes compiz

Then, Give the file executed permission:

chmod +x compiz_enable.sh

Last, go to System> Preferences> Startup Applications and add the entry there.

Log out and log back in. Everything should start working again.

* I tried to write it under ~/.config/compiz/compizconfig/config & ~/.config/compiz/compizconfig/Default.ini, but it does not work for me.

---

### Post by andrewabc on 2009-04-22
> **regonzal said:**
> It did work as well when testing the RC but after the first batch of upgrades after installation I could no longer enable the desktop effects.

So jaunty is crippled for all intel video cards even if they worked fine?

Guess I'll keep using intrepid.

---

### Post by psyke83 on 2009-04-22
> **andrewabc said:**
> So jaunty is crippled for all intel video cards even if they worked fine?

Guess I'll keep using intrepid.

No, they blacklisted just one Intel graphics chipset due to stability issues. Other Intel users aren't affected.

---

### Post by regonzal on 2009-04-22
> **andrewabc said:**
> So jaunty is crippled for all intel video cards even if they worked fine?

Guess I'll keep using intrepid.

I'm vaguely familiar with this issue, I know that some were blacklisted due to performance issues with the newer intel drivers. This, I have read, affects only certain models as you mentioned earlier in this thread; for whatever reason some working models were also black-listed. 

There is a way to re-enable compiz however, just look at post #8. 

The post above merely allows us to re-enable compiz without a glitch, try it!

---

