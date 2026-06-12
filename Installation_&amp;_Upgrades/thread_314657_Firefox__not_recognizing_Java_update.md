---
title: "Firefox  not recognizing Java update"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2006-12-07
Ok, after spending DAYS getting  jre1.5.0_10 installed correctly for use with applications such as Frostwire. I also have a website that I need to access for work that requires Java (which I had v1.4 installed until about an hour ago). 

Upon the advice I've gotten from that thread as well as IRC, I finally got it correctly installed and Frostwire was working- downloading as I type this, infact. 

Upon checking firefox plugins, v1.4 was still installed, and I was advised to 
copy libjavaplugin_oji.so from /usr/java/jre1.5.0_09/plugin/i386/ns7 to /usr/lib/mozilla-firefox/plugins, which I did. 

Upon checking Firefox's plugins again, I still saw v1.4 was recognized, but I was getting no more responses from my thread and the few people in IRC had run out of suggestions, so I started thinkin on my own (a dangerous thing to have happen). Upon examining the contents of /usr/lib/mozilla-firefox/plugins, I saw 2 files:

libjavaplugin_oji.so and libjavaplugin.so 

I thought, perhaps libjavaplugin.so was conflicting with libjavaplugin_oji.so  or preventing it from being recognized. To test this, I thought it would be a good idea to remove it:

```
sudo rm libjavaplugin.so 
```

OoOpS!!! Upon re-checking the plugins in firefox, there is NO java recognized now! HELP! I was back in IRC and was told to try to re-install jre1.5 again, which I did, but still NOTHING!

Any ideas what I'm missing here?

---

### Post by taurus on 2006-12-07
I already posted a reply in your other thread so do you want to start a new one here?

---

### Post by sp0nge on 2006-12-07
Not necessarily, sorry. 

I posted here because I was getting NO more responses on the other thread and I've been banging my head on this topic for nearly a week now! 

I did respond on the other thread, but if this is a more appropriate place, that's fine. I just want this dang thing to work!

---

