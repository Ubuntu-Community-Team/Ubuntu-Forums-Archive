---
title: "Ubuntu won't always show disc that was inserted in CD-Rom"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by Gottier on 2016-05-03
Before I upgraded to Ubuntu 16.04, I burned some discs with Ubuntu 14.04. The contents of the discs is just data and pictures. When I insert them into the CD-Rom tray with 16.04, the light on the optical drive lights up, and I can hear it spin for a couple seconds, but then it stops. The disc contents are not available for me to use, and no icon appears in the menu bar. If I take the disc and put it in a different computer that has Ubuntu 14.04, it works just fine.

This doesn't happen on all CDs. But a good portion of the ones I have are unusable unless I go to a different computer.

Another thing that is interesting is that I can burn a CD from 16.04. After it is burned I can't use it. Same thing, it doesn't automatically mount. I can mount it in the terminal, and see the contents, but I'd really like this to happen automatically when I put in a disc.

Please help!

---

### Post by Gottier on 2016-05-04
Please help!

---

### Post by Gottier on 2016-05-05
Please help!

---

### Post by kansasnoob on 2016-05-05
I assume you're using the standard Unity DE? Does it show up in the Home folder side panel:

[ATTACH=CONFIG]268868[/ATTACH]

---

### Post by Gottier on 2016-05-06
> **kansasnoob said:**
> I assume you're using the standard Unity DE? Does it show up in the Home folder side panel:

[ATTACH=CONFIG]268868[/ATTACH]

No, it does not show up in the Home folder side panel.

---

### Post by kansasnoob on 2016-05-06
> **Gottier said:**
> No, it does not show up in the Home folder side panel.

Are you using Unity?

I haven't seen this problem but I'd like to try and reproduce it. I just need to be sure what DE you're using :)

I see you're not alone:

[http://ubuntuforums.org/showthread.php?t=2323524](http://ubuntuforums.org/showthread.php?t=2323524)

Important to note they say there:

> Now, with 16.04, with or without libdvdcss2, the system is unable to even detect that the DVD is there. 

So it's clear there's a problem and if I can reproduce it I'll try to file a bug report and/or find a work-around.

---

### Post by Gottier on 2016-05-06
> **kansasnoob said:**
> Are you using Unity?

I haven't seen this problem but I'd like to try and reproduce it. I just need to be sure what DE you're using :)

I see you're not alone:

[http://ubuntuforums.org/showthread.php?t=2323524](http://ubuntuforums.org/showthread.php?t=2323524)

Important to note they say there:



So it's clear there's a problem and if I can reproduce it I'll try to file a bug report and/or find a work-around.

Yes, it's Unity.

Discs are Memorex CD-R (Never had a problem with Ubuntu 14.04 or any other computer)

Drives are HP model DVD1260 (Pretty plain optical drive)

---

### Post by kansasnoob on 2016-05-06
I found a couple of upstream bug reports against gvfs:

[https://bugzilla.gnome.org/show_bug.cgi?id=759952](https://bugzilla.gnome.org/show_bug.cgi?id=759952)

[https://bugs.freedesktop.org/show_bug.cgi?id=93771](https://bugs.freedesktop.org/show_bug.cgi?id=93771)

I'll play some more and see what happens. I tried a couple of data DVD's last night and they were recognized OK.

---

### Post by kansasnoob on 2016-05-06
I did find one Ubuntu bug report:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768)

---

### Post by Gottier on 2016-05-06
I appreciate your help. I've got a few computers to update to Ubuntu 16.04, but must wait until I know everything will work.

---

### Post by kansasnoob on 2016-05-06
> **Gottier said:**
> I appreciate your help. I've got a few computers to update to Ubuntu 16.04, but must wait until I know everything will work.

I've encountered enough issues that I'm keeping most of the machines I maintain on Trusty for the foreseeable future.

---

### Post by Gottier on 2016-05-06
> **kansasnoob said:**
> I've encountered enough issues that I'm keeping most of the machines I maintain on Trusty for the foreseeable future.

I really don't have any other problems that I'm aware of. PHP7 is my main reason for wanting 16.04, as I'm a web dev. I guess I can live with one computer having broken optical drives, but hope a fix comes my way.

---

### Post by Gottier on 2016-05-07
I just applied some system updates, including new linux kernel I believe. I was hoping that might take care of the issue, but it didn't. Is there anything I might be able to try?

---

### Post by Gottier on 2016-05-10
How can I file a bug complaint, or do something other than wait and hope?

---

### Post by kansasnoob on 2016-05-10
This would be the appropriate bug report:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768)

So mark it as affecting you also and please subscribe as we'll need more debugging/testing info.

Just curious, is a certain type of disc more likely to fail than others?

BTW I'm Erick Brunzell there, not a developer but a long time tester so I know how to light fires :)

---

### Post by Gottier on 2016-05-11
Thanks Erick. I did what you told me to do.

I have a 100-pack of Memorex CD-R, and they never auto-mount, regardless of content. ([COLOR=#ff0000]**does not work**[/COLOR])

Philips CD-R [COLOR=#ff0000]**does not work**[/COLOR]. I only tried one disc.

Sony DVD-R [COLOR=#008000]**seems to work**[/COLOR]. I only tried one disc.

Older Memorex Black CD-R [COLOR=#ff0000]**does not work**[/COLOR]. I only tried one disc.

Older Memorex CD-R from 2009 [COLOR=#008000]**seems to work**[/COLOR]. I only tried one disc.

Staples brand CD-R [COLOR=#ff0000]**does not work**[/COLOR]. I only tried one disc.

HP CD-R [COLOR=#ff0000]**does not work. **[/COLOR][COLOR=#000000]I only tried one disc.

I could go one with some more testing, but you can see that they don't work more than they do. It's not a good enough experience to satisfy.
[/COLOR][COLOR=#ff0000][/COLOR]

---

### Post by kansasnoob on 2016-05-11
Thank you. I've also found at least one disc that doesn't work so after a bit of testing on my end I'll contact a friend that is an actual developer and see what other debugging info is needed so we can get this fixed. It won't be incredibly fast because the fix will have to pass SRU testing.

---

### Post by Gottier on 2016-05-11
I'm glad that you can do something. I wonder if it's not a widely reported bug because many people don't use optical drives anymore. 

I saw comments where people were replacing libblkid.so.1.1.0 with the one that was in Ubuntu 14.04. I'm a little reluctant to do that because I'm not sure what would happen when upgrading. Do you think it's safe to replace? Upgrade not effected?

Thanks again. I appreciate your help.

---

### Post by Gottier on 2016-05-22
> **kansasnoob said:**
> Thank you. I've also found at least one disc that doesn't work so after a bit of testing on my end I'll contact a friend that is an actual developer and see what other debugging info is needed so we can get this fixed. It won't be incredibly fast because the fix will have to pass SRU testing.

If you were to give your best guess as to when it would be fixed, when do you think that would be?

---

### Post by kansasnoob on 2016-05-25
> **Gottier said:**
> If you were to give your best guess as to when it would be fixed, when do you think that would be?

Looks like sooner rather than later now. It took me quite a while to get the right fire lit :)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768/comments/14](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768/comments/14)

> it was fixed upstream with [https://git.kernel.org/cgit/utils/util-linux/util-linux.git/commit/?id=55ad13c26fe5d0e606be5a83937f31b8cf576588](https://git.kernel.org/cgit/utils/util-linux/util-linux.git/commit/?id=55ad13c26fe5d0e606be5a83937f31b8cf576588) I'm going to backport that to yakkety/xenial


The change in Xenial will probably require SRU verification and I won't be able to do that because I was wrong about finding a disc that was affected. The disc I'd thought was affected was a Memorex CDR with an older copy of supergrub2 burned on it but it turned out that disc was also not recognized in Trusty.

---

