---
title: "Thinkfinger &quot;broken&quot; after upgrade to Lynx"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Rebootkid on 2010-05-03
So, oddball issues going on with Thinkfinger.

Things were working fine under 9.10. Boot up the laptop, select my user name, swipe my finger, and I'm logged on.

Now, if I swipe my finger, nothing happens. The system just continues to wait for me to do something. I experience the same behavior for tools that open a GUI like Synaptic. 

I can, often times, swipe my finger, and then hit the enter key. That means that the reader is working, but not accepting the carriage return. (I think)

Same behavior can be observed in the CLI. Swipe finger, hit enter. Anyone got any clue how to append a ^M on the end of a swipe? I'd swear I read about a solution somewhere, but I'll be darned if I can find it again. 

```

~$ tf-tool --verify

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing... done.
Please swipe your finger (successful swipes 1/1, failed swipes: 0)... done.
Result: Fingerprint does match.


$ sudo ls
Password or swipe finger: 
2009-07-13 08.54.46.jpg
```

---

### Post by tgalati4 on 2010-05-03
If your laptop gets stolen, then at least it's secure.

Any strange messages:

dmesg | grep error
dmesg | more

---

### Post by psytrox on 2010-05-03
I have a Toshiba Satellite P100, with the same issue.  If I press 'Enter' after scanning my finger, it puts the command through, as usual.  Otherwise, that's the only issue.  I'd like to have it as before, like stated above.  Thanks!

---

### Post by seagullplayer77 on 2010-05-04
I have the same issue on my IBM/Lenovo ThinkPad T60p. It worked just fine in 9.04, but 10.04 broke thinkfinger.

I think the issue is with X. In a virtual terminal (Ctrl+Alt+F1), the fingerprint reader works just fine without a carriage return, but that's not the case as long as there's GUI involved.

Unfortunately, it looks like this has been an ongoing issue for thinkfinger, and even more unfortunately, it looks like they might be abandoning the package entirely in favor of something called fprint---which has bugs of it's own.

Check out the official bug report:

[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429)

All that said, if anyone finds a fix---or even a workaround---I'm all ears.

---

