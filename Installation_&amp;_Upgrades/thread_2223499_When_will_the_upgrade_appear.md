---
title: "When will the upgrade appear?"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by josephellengar2 on 2014-05-11
I am currently running 13.10 and am set up only to receive LTS releases. At what point will the upgrade to 14.04 get pushed out to my machine? I know that I can force upgrade now, but I normally wait a month. I just want to be sure I won't forget if I was supposed to have already received the upgrade by now and my machine isn't receiving it for some reason.

Also, if you happen to know, what is the standard timeframe when upgrade from LTS->LTS (for example, 14.04 to 16.04)?

---

### Post by ben-schweitzer on 2014-05-11
The upgrade has been out for a while now. Try switching the option to all releases. If that doesn't work, in a terminal type:
"do-release-upgrade" without the quotes.

---

### Post by josephellengar2 on 2014-05-11
> **ben-schweitzer said:**
> The upgrade has been out for a while now. Try switching the option to all releases. If that doesn't work, in a terminal type:
"do-release-upgrade" without the quotes.

I think that normally when you are going LTS->LTS they don't push the update out until the first .1 release. Is it possible that's what they are doing for me, since I am set to only do LTS releases anyway?

---

### Post by ben-schweitzer on 2014-05-11
That rule only applies for LTS to LTS. You said you were running 13.10 it should be working.

---

### Post by josephellengar2 on 2014-05-11
In my sources I have it set to go LTS to LTS. I am only running 13.10 because I got a new computer a month ago and installed 13.10 rather than going all the way back to 12.04.

---

### Post by ben-schweitzer on 2014-05-11
Just try changing the setting temporarily and see if there is a change

---

### Post by deadflowr on 2014-05-11
Change it to "any new version".
Then run the updater.
first install whatever new updates come, and then it should have an upgrade button next to the OK button.
If that makes sense.

---

### Post by josephellengar2 on 2014-05-11
Thanks everyone. I got it to work, but for some reason it was freezing really badly and I had to roll back to my backup (did two updates/rollbacks to make sure it wasn't a fluke). I started a new thread about that here: [http://ubuntuforums.org/showthread.php?t=2223542](http://ubuntuforums.org/showthread.php?t=2223542)

---

