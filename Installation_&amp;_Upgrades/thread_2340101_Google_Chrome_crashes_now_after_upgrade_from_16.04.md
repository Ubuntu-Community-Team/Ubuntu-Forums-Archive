---
title: "Google Chrome crashes now after upgrade from 16.04 to 16.10"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by andrew-thecallums on 2016-10-15
As title explains, my Google Chrome web browser now crashes at times after upgrading.

I have re-enabled the Google repository, but I haven't seen an update to Chrome.  

Anyone else having this problem?  Anyone solved it?

Thanks.

---

### Post by Surakin on 2016-10-16
> **andrew-thecallums said:**
> As title explains, my Google Chrome web browser now crashes at times after upgrading.

I have re-enabled the Google repository, but I haven't seen an update to Chrome.  

Anyone else having this problem?  Anyone solved it?

Thanks.

I'm having this same issue. Seems to be a bit random. I'm trying google-chrome-beta to see if it has the same problem.

---

### Post by RobGoss on 2016-10-16
Using Google chrome here no problems at all, have you tried uninstalling Chrome and reinstalling it to see if the problem persist

---

### Post by blackpoison357 on 2016-10-16
I use google chrome dev version and the problem still remain. I also have tried the normal and the chromium versions and they still crash.

---

### Post by nonparity on 2016-10-17
Chrome is starting to do the same thing for me after I upgraded to 16.10. I searched the bug tracker and could not find anything. I am going to dig into this a little more and will probably end up opening a bug.

---

### Post by Surakin on 2016-10-17
I confirm all branches of chrome are randomly crashing. I've been getting 'corrupted low memory' messages in dmesg but I don't know if it can be related since chrome is the only app misbehaving.

---

### Post by monkeybrain20122 on 2016-10-17
I am not seeing any crash. But this is a fresh install. Maybe your profiles get corrupted by the upgrade or some old settings are in conflict with the new  OS. Try this.  Close Chrome. Open the file manager, choose from menu "show hidden files" (or press ctrl + h) find the hidden folder .config, in it you would find chrome's configuration folder, called goole-chrome naturally. Rename this file to something else like google-chrome-bk. Now open Chrome and see if it still crashes. If it doesn't then the culprit is your settings.

 If you settings get corrupted reinstalling Chrome is not going to do you any good. The easy fix would be to just delete .config/google-chrome, maybe after you have export your bookmarks.

---

### Post by niry on 2016-10-19
I can confirm that deleting the profiles (all of ~/.config/google-chrome) isn't helping. I also reported this bug via chrome->menu->help->report an issue.

[19468.175099] Chrome_IOThread[19773]: segfault at ffffe8333d5cd127 ip 000055ce6629c583 sp 00007f4e63d102f0 error 5 in chrome[55ce62e71000+6433000]
[21759.167267] Chrome_IOThread[1032]: segfault at ffffc4ee70bfee32 ip 000055f0cc285583 sp 00007fd471e5d2f0 error 5 in chrome[55f0c8e5a000+6433000]
[29373.744341] Chrome_IOThread[5497]: segfault at ffffdc9052634edc ip 00005598ca231583 sp 00007fd71c5742f0 error 5 in chrome[5598c6e06000+6433000]
[33244.021769] Chrome_IOThread[9559]: segfault at ffffdac06b2527a3 ip 0000558c374a3583 sp 00007fcad43d42f0 error 5 in chrome[558c34078000+6433000]
[37634.523134] Chrome_IOThread[14156]: segfault at ffffc7f16ceddce6 ip 0000562d5e31e583 sp 00007f95e27082f0 error 5 in chrome[562d5aef3000+6433000]
[44657.493699] Chrome_IOThread[18828]: segfault at ffffe30d5afcf7ab ip 000055ca02c93583 sp 00007f528159e2f0 error 5 in chrome[55c9ff868000+6433000]
[47308.517915] Chrome_IOThread[21988]: segfault at ffffdfa755fef83f ip 00005599c826c583 sp 00007f4cad8572f0 error 5 in chrome[5599c4e41000+6433000]
[77851.089885] Chrome_IOThread[26217]: segfault at ffffc8c911d4780d ip 0000563b803d0583 sp 00007fc0b700c2f0 error 5 in chrome[563b7cfa5000+6433000]

My next test:

sudo apt-get update
sudo apt-get autoremove --purge google-chrome-stable 
sudo apt-get clean
sudo apt-get install google-chrome-stable 

Couple of hours now, seems promising. Few more days, and I'll post the result.


> **monkeybrain20122 said:**
> I am not seeing any crash. But this is a fresh install. Maybe your profiles get corrupted by the upgrade or some old settings are in conflict with the new  OS. Try this.  Close Chrome. Open the file manager, choose from menu "show hidden files" (or press ctrl + h) find the hidden folder .config, in it you would find chrome's configuration folder, called goole-chrome naturally. Rename this file to something else like google-chrome-bk. Now open Chrome and see if it still crashes. If it doesn't then the culprit is your settings.

 If you settings get corrupted reinstalling Chrome is not going to do you any good. The easy fix would be to just delete .config/google-chrome, maybe after you have export your bookmarks.

---

### Post by niry on 2016-10-20
This didn't take days. the below does not help, it crashed again in Chrome_IOThread.

[102861.264535] Chrome_IOThread[22145]: segfault at ffffc6531c63eda5 ip 0000562af4ca0583 sp 00007ff6d6dd42f0 error 5 in chrome[562af1875000+6433000]

> **niry said:**
> 

My next test:

sudo apt-get update
sudo apt-get autoremove --purge google-chrome-stable 
sudo apt-get clean
sudo apt-get install google-chrome-stable 

Couple of hours now, seems promising. Few more days, and I'll post the result.

---

### Post by Surakin on 2016-10-20
I'm trying running it with all extensions disabled and without WhatsApp web, and haven't crashed for 2 days now. (I'll probably crash soon after writing this :P )

---

### Post by Surakin on 2016-10-20
> **Surakin said:**
> I'm trying running it with all extensions disabled and without WhatsApp web, and haven't crashed for 2 days now. (I'll probably crash soon after writing this :P )

Aaaannd.. it did :(

It did reenable LastPass before the crash. Any of you using LastPass?

---

### Post by Surakin on 2016-10-23
> **andrew-thecallums said:**
> As title explains, my Google Chrome web browser now crashes at times after upgrading.

I have re-enabled the Google repository, but I haven't seen an update to Chrome.  

Anyone else having this problem?  Anyone solved it?

Thanks.

Is the 'translate page' option working for you?

---

### Post by Surakin on 2016-10-26
Maybe the problem is Chrome 54 and not Ubuntu 16.10? I just downgraded it, the translate option seems to work again, we'll see if it crashes.

---

### Post by acidreign on 2016-11-02
A temporary solution to this is to block ports 8008 and 8009. I did this by installing gufw (a gui-based firewall) and setting two rules. Apparently this has something to do with Chrome trying to detect Chromecasts, which happens on those two ports.

My Chrome has been constantly crashing since 16.10 came out and after I added these rules it stopped. 

I found the solution here. They also mention that a fix should be released any day now.
[https://bugs.chromium.org/p/chromium/issues/detail?id=658106](https://bugs.chromium.org/p/chromium/issues/detail?id=658106)

---

### Post by andrew-thecallums on 2016-11-14
I just updated Chrome this morning to [COLOR=#303942][FONT=Ubuntu]Version 54.0.2840.100 (64-bit) and will report how it works.

Thanks for all the input on this.

[/FONT][/COLOR]

---

