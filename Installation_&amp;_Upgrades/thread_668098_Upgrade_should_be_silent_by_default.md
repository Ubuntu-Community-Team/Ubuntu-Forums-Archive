---
title: "Upgrade should be silent by default"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by ricster on 2008-01-15
Finally got around to upgrading my 7.04 install last night so popped in the 7.10 CD i'd downloaded and burned... But there was no upgrade option (apparently you have to use an "alternate install CD" to do that or some command line munging)

so instead I booted and ran the auto update upgrade. Set it going, agreed to the terms and went to play on my xbox, popped up before bed and it had popped up a dialog asking if i wanted to stop some daemons (i think). so I clicked OK and judged the 6 hour ETA to mean i might as well go to bed

This morning it had another dialog up, asking if i wanted to overwrite some config file, clicked OK and went to have breakfast.

Did a quick check before I left and it'd asked the same question again - presumably a different config file - clicked ok and am now at work.

I can only guess wether or not it's actually going to have done it when i get home in 9 hours time

so my question is: Why is it not silent by default? I.E. a "Just do it" button at the start, ok so leave the "agree to disclaimer" click in but after that... just do it!



NB I'm a normally very happy ubuntu bunny, busy converting family and friends it just seems you're making this unneccesarily difficult, I've got two ubuntu dual-booters at home so thought using the CD would save bandwidth (not jusst for me, for my next door neighbours too, y'know) rather than downloading everything twice so think it's a shame it didn't have an upgrade option built right in (though I have to say the CD integrity check is a nice one to have , i used it to test a DVD DRIVE the other day :-)

Ricster

---

### Post by tehet on 2008-01-15
apt-get allows fearless souls to --force-yes.

---

### Post by zvacet on 2008-01-15
> Why is it not silent by default? I.E. a "Just do it" button at the start, ok so leave the "agree to disclaimer" click in but after that... just do it!


because you are upgrading and ubuntu ask if you want to keep existing conf or you want to install new one(if I remember correctly).Basicly it is doing right thing leaving you choice to decide wich one you want.You would save bandwidht if you downloaded alternate CD,but now you know that.

---

### Post by ricster on 2008-01-15
Well it nearly did it whilst i was at work, came home to a prompt asking about removing unused dependencies(IIRC) after that it cleaned up and rebooted. Job done.

I tar'ed up my home directory prior to doing the upgrade so a complete disaster wouldnt have been too bad an event, but it would have been nice to just have an unattended option in there somewhere - even if that itself is followed by a fat warning dialog that unpredictable badness might result.

anyway, all considered it's upgraded from 7.04 to 7.10 fine with no issues. yay!

---

### Post by iiibill on 2008-01-16
For long running processes you might want to consider using the screen utility.  It allows you to start the process running without have to worry about the case when you terminal gets nuked.  But, more importantly it allows you to peak at what is going on from any where as long as you can ssh into the box.  

By the by, I think that question about why doesn't it just do the right thing is a bit silly on its face.  By and large, the upgrades do the right thing on their own.  Questions asked are where it is not clear what is the right path or when a change is particularly critical.  For example, the upgrade of libnss_ldap from fiesty to gutsy caused me lots of heartburn and the only reason I had a clue of what was causing the issues was because of the warning dialog was presented.  Of course, maybe you read all of the change logs from all of the new software that was installed and didn't need the warning, but I did. 

Bill

---

