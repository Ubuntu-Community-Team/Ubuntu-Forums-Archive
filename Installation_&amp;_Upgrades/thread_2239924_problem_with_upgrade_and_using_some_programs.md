---
title: "problem with upgrade and using some programs"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by podobin on 2014-08-16
Hi,
I'm running Ubuntu 12.04 LTS

few days ago I had a notification from update centre about new version of Ubuntu. I clicked "yes" as usual, but something went wrong. I now see a "no entry" sign (white rectangle at the red circle) near the language sign all the time. 

I'm using Ukrainian localization, so my wording won't probably be exact, sorry. I tried to switch to English to be more clear here, but when I click at "localization" (I know how to switch), the window starts to open, but then shuts down..

the same with Program centre (red bag with bubbles) - it starts to open, then shuts down. I recently tried Synaptyc (when I read some threads here) - the same story.

when I click at "no entry" sign it says (in my translation) - "there was a problem with checking updates"

also, I frequently had a pop-up window saying "mistake of system program detected", and sometimes other mistakes, and then I click "report the problem" it says me "unable to report"...

browsers, skype, LibreOffice work fine. I had that "no entry" sign problem maybe two weeks ago, but it went somehow by itself, updated successfully.. I recently installed Adobe Reader (I read that non-canonical packages might create problems)..

what might be the problem, and what are possible solutions?

thank you,

Alex

---

### Post by ibjsb4 on 2014-08-17
There is a lot of breakage going around with version upgrades, yours is compounded with localization.  Have you tried to fix broken packages?
```
sudo apt-get -f install
```
In my opinion the best way to upgrade to 14.04 is a fresh install.

What are you running?  Ubuntu/Unity or something else?

Edit:  Found a better answer
[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)

---

### Post by podobin on 2014-08-17
Hi,
thank you very much for your reply! you helped me to solve my problem!
I'm running Ubuntu 12.04 LTS
sudo apt-get -f install  -- didn't help, it got stuck at 3% checking, 
but then I checked your link to another thread, and
sudo apt-get update   -- helped me.
"no entry" sign gone, Program centre works, no error messages..
However, based on the reports of problems with 14.04.1 LTS I will wait
with upgrading:) 

thank you again!
hav a nice day!

---

