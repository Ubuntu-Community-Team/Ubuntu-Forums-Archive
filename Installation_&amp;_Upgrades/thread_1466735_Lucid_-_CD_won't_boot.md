---
title: "Lucid - CD won't boot"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by carlbeech on 2010-04-30
Got two machines - both running 9.10 no problems - when I try ubuntu 10.04, I get to a purple background screen, with a grey box, and then stops?

Downloaded kubuntu, and while my desktop machine does work, my laptop stops at the main KDE loading panel - where you've got the picture of the disk that fades in, up to the big 'K', and then stops...

Both machines are dual-core, 2Gb, and run Nvidia  drivers (laptop is a geforce 8200m - I think)...

The laptop is an ASUS X59GL

I suspect that the problem is with the X server - but I don't know how to get to the log files to do a diagnosis...

Anyone any ideas - I was really looking forward to 10.04...

Cheers 

Carl.

---

### Post by jonathangayton on 2010-05-01
Just to let you know, I have the same laptop and am having exactly the same problem.

Please post if you manage to fix this.

---

### Post by Rackstar on 2010-05-01
Sound like the issue discussed in this thread and workarounds that work for some people:
[http://ubuntuforums.org/showthread.php?p=9195971#post9195971](http://ubuntuforums.org/showthread.php?p=9195971#post9195971)

I filed a bugreport about it here:
[https://bugs.launchpad.net/ubuntu/+bug/572868](https://bugs.launchpad.net/ubuntu/+bug/572868)

It is new report, so if you could be kind enough to post additional information and click "affects me too"

If this is what you're looking for.

---

### Post by danciac on 2010-05-08
Hey carlbeech!

I have the exact same laptop, and have experienced the same problem.

The reason for it is that the default video driver crashes because of the desktop effects.

So you want to boot in safe mode and install the proprietary nVidia drivers and it will work smoothly.

I have one more problem though. Related to the volume up/down, mute buttons. They really lag. Could you tell me if it is the same for you?

Cheers,
danciac

---

### Post by carlbeech on 2010-05-27
Hi, Yes I've got the same 'lag' problem - really annoying, considering 9.4 / 9.10 worked fine! - raised a thread, however, no-one replied, so I've been assuming it must just be me...

Not sure how to go about getting this one recognised / sorted though...

As a matter of interest (and it may be me...) but is your CPU fan running more often? - not sure whether all the improvements are more CPU hungry therefore the CPU requires cooling more often, or whether the CPU temperature monitoring is more aggressive? - or is it just me....

Hmm...

Thanks

Carl.

---

