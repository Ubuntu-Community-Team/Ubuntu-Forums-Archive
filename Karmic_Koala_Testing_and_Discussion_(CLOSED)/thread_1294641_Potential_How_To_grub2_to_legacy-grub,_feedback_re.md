---
title: "Potential How To: grub2 to legacy-grub, feedback requested"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-10-18
Several weeks ago I began playing around:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Since then I realize a few things.

(1) The average user can really hose things fast using 'nautilus-gksu'! It's just too darn easy to choose to "mount as administrator" and break things.

(2) Since not all parts of the process can be completed without using the CLI why not just use the CLI throughout?

Well, I could ramble on, but this is so far the "nearly finished product":

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

Please tell me what you think. I'd like some feedback before I copy this to the Tips and Tutorials.

All negative and/or positive comments welcome :)

I'd rather someone point out here in a testing forum that I'm a moron than wait until final. Let's face it, many minds work better than a single mind.

---

### Post by psyke83 on 2009-10-18
Q: What's the point of using GRUB legacy?
A: GRUB2 has a problem on my machine or functionality I don't like.

My reply: file a bug against GRUB2!

I appreciate the effort, but you're just adding complication to everybody's lives. Each person you convince to revert to GRUB1 is one less person filing bugs against GRUB2, so everybody suffers.

Just my opinion; it's a free world, of course.

---

### Post by kansasnoob on 2009-10-18
> **psyke83 said:**
> Q: What's the point of using GRUB legacy?
A: GRUB2 has a problem on my machine or functionality I don't like.

My reply: file a bug against GRUB2!

I appreciate the effort, but you're just adding complication to everybody's lives. Each person you convince to revert to GRUB1 is one less person filing bugs against GRUB2, so everybody suffers.

Just my opinion; it's a free world, of course.


That is one of my concerns! That's why I say:

> "why would I want to revert to legacy grub"? My answer is, "I hope you don't". Grub 2 is the way of the future and I'd bet that a year from now nearly everyone will think of legacy grub as downright prehistoric! If you're new to Ubuntu I believe you'll find Grub 2 to be no more complicated than legacy grub, and the documentation continues to improve. I know 20 months ago grub was confusing to me.

Your tutorials regarding pulse-audio have helped me immensely so I appreciate your feedback.

I think I'll stress the point of "I hope you don't". Grub 2 is the way of the future" with a different font size or color.

My goal is to **not** coax anyone to do anything but rather just provide some guidance if needed.

And I'd hate for them to follow my original post, so I'd like to create a new "How-To" and then ask the Moderators to dump that or I'll make sure to mark each post as CRAP. 

Clear as mud?

---

### Post by psyke83 on 2009-10-18
> **kansasnoob said:**
> I think I'll stress the point of "I hope you don't". Grub 2 is the way of the future" with a different font size or color.

I don't think it'll make a difference. In my experience, warnings tend to get completely ignored irrespective of its prominence in the post (color/ size/language).

> My goal is to **not** coax anyone to do anything but rather just provide some guidance if needed.

Yes, I understand, but I stand by my original reply. It's pretty obvious that the legacy GRUB is going to be left unmaintained from Karmic onwards, so it's only going to distract potential bug reporters against GRUB2.

Also, I can easily imagine a good portion of users trying to revert to GRUB1 because they have various problems booting their system, but the symptom was not the bootloader.

> And I'd hate for them to follow my original post, so I'd like to create a new "How-To" and then ask the Moderators to dump that or I'll make sure to mark each post as CRAP. 

Clear as mud?

My understanding was that the post you referenced would be a semi-final draft of what would ultimately get posted to the Tutorials & Tips section.

Have you considered writing a how-to designed to help users get accustomed to GRUB2 instead? Perhaps someone else has already done so, I haven't paid too much attention.

---

### Post by kansasnoob on 2009-10-19
There are tutorials regarding grub2:

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

They both contain multiple links and the latter includes a link to my original thread.

Just today there was this:

[http://ubuntuforums.org/showthread.php?t=1294804](http://ubuntuforums.org/showthread.php?t=1294804)

> Thank you for the replies!!

My raid systems were just for /var and /home.

Since Grub was looking at hd2,1 for my /boot I don't think the raid arrays were of any significance to the grub error.

Because I needed to move forward, I abandoned 9.10 and went back to 9.04.

I wish i had the skills to diagnose/fix the issue but I definitely do not.

I may try to fiddle with it on a test system if i find the time.

Sorry for being a quitter. I just needed an up and running system quickly.

I'm still gonna read through that grub2 link.

Thank you for your help, nonetheless.

I think we'll see a lot of that!

So, my focus is on improving my potential "how-to", not doing away with it altogether. If people make sure to tick the Submit Statistical Info box in Software Sources and Canonical sees a lot of downloads of "grub" they'll know there's work to be done.

---

### Post by psyke83 on 2009-10-19
> **kansasnoob said:**
> 

Just today there was this:

[http://ubuntuforums.org/showthread.php?t=1294804](http://ubuntuforums.org/showthread.php?t=1294804)



I think we'll see a lot of that!

That's because, quite frankly, people are too lazy to read the appropriate documentation. The issue with GRUB2 and RAID configurations is documented in the [Release Notes]("http://www.ubuntu.com/testing/karmic/beta") - the bug is filed and should be fixed.

Do you see the problem? If that bug was not yet filed, and the user reverted to GRUB1 instead of filing a new report...

> So, my focus is on improving my potential "how-to", not doing away with it altogether. If people make sure to tick the Submit Statistical Info box in Software Sources and Canonical sees a lot of downloads of "grub" they'll know there's work to be done.

Again, I have to disagree. The developers will know there's a lot of work to be done from the volume of valid bugs reported against GRUB2, not from vague statistics.

---

### Post by MALEADt on 2009-10-19
People might want to downgrade for now due to the [known bug](http://ubuntuforums.org/showthread.php?t=1284914) possibly preventing to install in partition boot records. However, people managing to set-up a chain of grub's loading each other, will most likely manage just fine reverting their grub2 setups to -legacy.

---

### Post by ranch hand on 2009-10-19
While I share all of psyke83 concerns, and agree with them, I still think this is a good idea.

I think that we all have a little reactionary head banger in us.  I think that grub2 is going to bring this out in many people.

9.10 is going to be a real nice OS and I think folks should use it.  If they want to use grub-legacy on an OS designed to NOT use it, a guide is a good idea.

Maybe by the time 10.04 comes out they will come to their senses.

The bug reports on grub2 are the critical issue here and the more there are the faster the improvement.  As far as folks that just will not try to learn something new goes though, will they file bugs or will they just down grade or move on to another distro?

I am a Blacksmith and like a big hammer and love working nautilus as root.  It really is, on the other hand, the best way to really, completely, screw your entire OS.

I think that this version is an improvement because of the greater safety.

---

### Post by VMC on 2009-10-19
I will use grub2, but I'm sure there are those that will unequivocally use grub-legacy to its death. Some still prefer lilo !?

So if they don't find topics here to support their search and how to keep grub-legacy they will find it elsewhere. I don't know if keeping it "in house" is best or not. 

I just know that some will never give up on the old way. Maybe partly fear of the unknown. And there's a world of differences between the two. ...The should I use Ext4 is still being debated. I wouldn't expect anything less from grub-legacy-lovers.

---

### Post by ranch hand on 2009-10-19
> **VMC said:**
> I will use grub2, but I'm sure there are those that will unequivocally use grub-legacy to its death. Some still prefer lilo !?

So if they don't find topics here to support their search and how to keep grub-legacy they will find it elsewhere. I don't know if keeping it "in house" is best or not. 

I just know that some will never give up on the old way. Maybe partly fear of the unknown. And there's a world of differences between the two. ...The should I use Ext4 is still being debated. I wouldn't expect anything less from grub-legacy-lovers.
+1

I love grub2.

I prefer ext4 and wish I could use it on more OS'.

Some folks don't.

This is Linux, we have choices here.  So do the folks that don't like some things we think are the cats meow.

---

### Post by duncan_bayne on 2009-10-19
> **VMC said:**
> Maybe partly fear of the unknown.

In my case, I happily tried out 9.10 with Grub2.  The problem is that Grub2 lacks features that exist in Grub Legacy.  That's fine for most users, but those of us who are using said features are better off sticking with Grub Legacy.

Personally, I would have appreciated the ability to choose between boot-loaders in 9.10.  Why force users to run with Grub2 when it simply isn't finished yet?

I'd love to see a Grub2 -> Grub Legacy HOWTO in the docs (and am more than happy to test it out & give feedback).  My only concern is whether this would play nicely with the automatic update feature in Karmic when it comes to kernel updates?

---

### Post by psyke83 on 2009-10-20
> **duncan_bayne said:**
> In my case, I happily tried out 9.10 with Grub2.  The problem is that Grub2 lacks features that exist in Grub Legacy.  That's fine for most users, but those of us who are using said features are better off sticking with Grub Legacy.

Personally, I would have appreciated the ability to choose between boot-loaders in 9.10.  Why force users to run with Grub2 when it simply isn't finished yet?

I'd love to see a Grub2 -> Grub Legacy HOWTO in the docs (and am more than happy to test it out & give feedback).  My only concern is whether this would play nicely with the automatic update feature in Karmic when it comes to kernel updates?

What features is GRUB2 missing that are present in the legacy version?

---

### Post by duncan_bayne on 2009-10-20
> **psyke83 said:**
> What features is GRUB2 missing that are present in the legacy version?

Not sure how many regressions there have been, but there's one in particular that is causing me pain - the ability to prevent the user from (trivially) entering recovery mode.  In Grub Legacy I could use password protection; in Grub2 [I can't](http://ubuntuforums.org/showpost.php?p=8118124&postcount=40) ([further confirmation here](http://ubuntuforums.org/showpost.php?p=8132476&postcount=49)).

Personally I applaud the aim of Grub2, and can vouch for it in operation.  I'm not suggesting that it should be kept out of Ubuntu until it faithfully replicates all of the functionality of Grub Legacy, just suggesting that until it does, users should be given the option of installing Legacy instead.

One doesn't usually expect an *upgrade* to *remove* functionality that's in current use.

Microsoft has been soundly criticised for [feature regression in Vista](http://en.wikipedia.org/wiki/Features_removed_from_Windows_Vista), and usually for good reason (although some of the items in that list represent the graceful retirement of antiquated tech.).  It seems sad that Ubuntu is following the same path.

---

### Post by psyke83 on 2009-10-20
> **duncan_bayne said:**
> Not sure how many regressions there have been, but there's one in particular that is causing me pain - the ability to prevent the user from (trivially) entering recovery mode.  In Grub Legacy I could use password protection; in Grub2 [I can't](http://ubuntuforums.org/showpost.php?p=8118124&postcount=40) ([further confirmation here](http://ubuntuforums.org/showpost.php?p=8132476&postcount=49)).

Personally I applaud the aim of Grub2, and can vouch for it in operation.  I'm not suggesting that it should be kept out of Ubuntu until it faithfully replicates all of the functionality of Grub Legacy, just suggesting that until it does, users should be given the option of installing Legacy instead.

One doesn't usually expect an *upgrade* to *remove* functionality that's in current use.

Microsoft has been soundly criticised for [feature regression in Vista](http://en.wikipedia.org/wiki/Features_removed_from_Windows_Vista), and usually for good reason (although some of the items in that list represent the graceful retirement of antiquated tech.).  It seems sad that Ubuntu is following the same path.

Ok, I see. That was filed as [bug #392158]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158"). You can edit the scripts to enable password enforcement - not as convenient as GRUB1 yet, but still possible.

---

### Post by duncan_bayne on 2009-10-20
> **psyke83 said:**
> Ok, I see. Is a bug filed requesting this functionality to be introduced into GRUB2?

[Yup](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158), although the core functionality doesn't cover the particular case in which I'm interested.

> **psyke83 said:**
> If you're worried about malicious folk accessing your machine, you could also set the BIOS password. However, when someone gains physical access to your machine, you data is no longer safe. GRUB legacy's password can probably be bypassed by using the Super Grub disk, so it's probably not something you should rely on for security.

Agreed; my use of this functionality is part of a multi-layered approach (which includes encryption) to increase the time & effort required to get access to the disk contents.

Maybe I should pull my finger out, read up about bootloaders, & submit a patch ...

---

### Post by psyke83 on 2009-10-20
> **duncan_bayne said:**
> [Yup](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158), although the core functionality doesn't cover the particular case in which I'm interested.

I edited my reply to link to the same bug, just a minute before yours ;).

You can edit the script to enable password enforcement of recovery mode, and also disable recovery mode entirely.

From /etc/default/grub:
```
# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by duncan_bayne on 2009-10-20
> **psyke83 said:**
> You can edit the script to enable password enforcement of recovery mode

I couldn't find that :confused:

The docs mention that password support has been enabled to secure booting from specific partitions, but I couldn't find any mention of password-protecting Grub2 itself so that SHIFT doesn't bring up the menu.

> **psyke83 said:**
> , and also disable recovery mode entirely.

From /etc/default/grub:
```
# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

I uncommented that & it did indeed remove the menu item, but a user can still do [this](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1):

> 11. How to Boot to the Recovery Mode w/o a Menu Option

   1. If you have Grub 2 set to boot without displaying the menu at all, hold the SHIFT key down until the menu displays. (In Grub it was the ESC key.)
   2. Press any key once the menu is displayed to 'freeze' it. Then arrow to the kernel you want to boot.
   3. Press E
   4. Scroll to the end of the "linux /boot/vmlinuz...." line. If displayed, remove "quiet" and/or "splash". Add the word "single" to the end of the line.
   5. Press CTRL-X to boot to the Recovery menu.

On an unrelated note, thanks for all the help ... :)

---

### Post by VMC on 2009-10-20
> **duncan_bayne said:**
> Agreed; my use of this functionality is part of a multi-layered approach (which includes encryption) to increase the time & effort required to get access to the disk contents.

Maybe I should pull my finger out, read up about bootloaders, & submit a patch ...
Depending on how your BIOS is set up, and unknown user can gain access to grub either through usb, floppy, or cd, and access or alter grub. I'm speaking in regards to your grub2 concerns.

Also you have your partitions encrypted anyway.

I figure if someone gains physical access to my computer I have been compromised anyway.

---

