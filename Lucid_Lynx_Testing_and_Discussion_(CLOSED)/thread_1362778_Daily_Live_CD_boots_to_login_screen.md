---
title: "Daily Live CD boots to login screen?"
date: 2009-12-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-12-23
I'm trying to follow up on some Alpha 1 Live CD bugs (Xorg) that I filed and so I dl'ed and burned the 12-23 i386 Live CD.

Of course I checked the md5sum of the download, check disc for defects fails to run so I rebooted and actually checked the md5sum of the disc which was fine.

So I choose to run without changes and it boots to the login screen. I've seen that with other distros, maybe Mepis? So I've tried just waiting for several minutes and it just sits there.

I've also tried logging in as ubuntu w/ubuntu as pword, and demo, and root ............ several combinations. Have I missed something new?

Or is this just a goofy daily build?

I even tried going to a tty and then "startx" but that fails. Any ideas?????????

---

### Post by VMC on 2009-12-23
No your not alone. It was first reported [HERE]("http://ubuntuforums.org/showthread.php?t=1362488").

I think I will wait until the Christmas daily before I download Kubuntu.

Thanks for reporting this. Something must be wrong with this daily.

---

### Post by kansasnoob on 2009-12-23
Thanks, I didn't see that other thread.

I've been going bug-eyed trying to figure out some Xorg issues :confused:

Hopefully I can borrow my daughters laptop so I can ssh this sucker during a lockup. The devs want more info but it's hard to gather info from a Live CD when it locks up and you have to hit the power button.

I'm actually hoping that it's just already fixed so I can tell them it's no longer valid! But I dropped the ball on Karmic, thinking it was fixed, and then it wasn't!

I want badly for Lucid to be the best Ubuntu ever.

---

### Post by phillw on 2009-12-23
No doubt this is a real dumb reply... So excuse me being a n00b on testing. Would a USB-Stick boot with persitance on it allow apport to write the crash report ?

Phill.

---

### Post by Eclipse. on 2009-12-23
> **phillw said:**
> No doubt this is a real dumb reply... So excuse me being a n00b on testing. Would a USB-Stick boot with persitance on it allow apport to write the crash report ?

Phill.

With the livecd there is still the ability to write data, anything written gets stored to a tempfs in your RAM.

---

### Post by kansasnoob on 2009-12-23
> **Eclipse. said:**
> With the livecd there is still the ability to write data, anything written gets stored to a tempfs in your RAM.

So how do you recover that info?

Remember I'm talking about a total lockup where the only way to escape is hitting the power button! everything is frozen, not even Alt > Sys Req > B works.

---

### Post by kansasnoob on 2009-12-23
> **phillw said:**
> No doubt this is a real dumb reply... So excuse me being a n00b on testing. Would a USB-Stick boot with persitance on it allow apport to write the crash report ?

Phill.

IMO there's no such thing as a dumb reply, but in my case I need to test the iso, once saved to a disc, any disc, and then updated it's no longer really the iso I'm trying to test.

The thing is Xorg is farting around with openchrome support. So far bullet-proof-x is more like "bullet-in-the-head-x" here!

If I use the xorg crack repos I'm fine, but how many new users will wait and try to figure that out?

Trying to get the devs to include certain upgrades is sometimes like pulling teeth. For instance I can't get grub2 final pushed into Karmic proposed even though I've installed the .debs and it works fine.

---

### Post by ranch hand on 2009-12-23
This is OT but I have both 9.10 and 9.04 running grub1.97 quite handily.  They both run very nicely with the ...32-9 kernel.

---

### Post by kansasnoob on 2009-12-24
> **ranch hand said:**
> This is OT but I have both 9.10 and 9.04 running grub1.97 quite handily.  They both run very nicely with the ...32-9 kernel.

I'm just curious what method you used to install the 32-9 kernel? I've had fairly good luck just picking the .debs from the Ubuntu package list.

I doubt I'll fiddle with my 9.04, that's my 100% safe boot! It just works, but after using Karmic or Lucid I can see a difference in speed. It's not huge, but it's obvious.

---

### Post by ranch hand on 2009-12-24
I made a file "/etc/apt/sources.list.lucid".  The only thing in it was "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted".

Change the name of "sources.list" to "sources.list.k  (or j as the case may be) make my lucid the "sources.list".  Update apt so I ca nsee what is happening.  Synaptic for the kernel and grub1.97.

Change the lists back around and update apt.  Reboot.

I now have grub and the kernel where I can get to them if I need an update.

The 9.04 that I used was an "extra", not the one I use most of the time.  It is just there to screw with.

---

### Post by kansasnoob on 2009-12-24
Related bug reports:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

[https://bugs.launchpad.net/ubuntu/+bug/500198](https://bugs.launchpad.net/ubuntu/+bug/500198)

One new, one joined. Help out please! We want Lucid to be the best Ubuntu ever.

---

### Post by kansasnoob on 2009-12-24
> **ranch hand said:**
> I made a file "/etc/apt/sources.list.lucid".  The only thing in it was "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted".

Change the name of "sources.list" to "sources.list.k  (or j as the case may be) make my lucid the "sources.list".  Update apt so I ca nsee what is happening.  Synaptic for the kernel and grub1.97.

Change the lists back around and update apt.  Reboot.

I now have grub and the kernel where I can get to them if I need an update.

The 9.04 that I used was an "extra", not the one I use most of the time.  It is just there to screw with.

That almost makes my brain hurt :lolflag:

---

### Post by ranch hand on 2009-12-25
I attached comments affirming both bugs and when I did it made the pages say "effects you and one other person".  People with problems need to get on the stick and file.

---

### Post by ranch hand on 2009-12-25
> **kansasnoob said:**
> That almost makes my brain hurt :lolflag:
It is quite easy if you just open /etc as "administrator" (you need nautilus-gksu installed).

---

### Post by jppr on 2009-12-25
when i try install livecd and choose install ubuntu, installation stops soon  and came this...
stdin: error 0
/init: line7: can't open /dev/sr0: No medium found
/init: line7: can't open /dev/sr0: No medium found

---

### Post by sparker256 on 2009-12-25
Just tried the daily build for today 122509 and when booted it tells me I need to run in low res. I allow that and end up with a login dialog box that I do not know what login in that it is looking for. I tried ubuntu but that did not work. The last daily build that I can boot is 121609 just not sure what the problem is.

Bill

---

### Post by kansasnoob on 2009-12-25
The steps here work for me:

[http://ubuntuforums.org/showpost.php?p=8548884&postcount=9](http://ubuntuforums.org/showpost.php?p=8548884&postcount=9)

But please everyone add your confirmation to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

In fact I'd appreciate if someone would change the status to Confirmed.

---

### Post by ranch hand on 2009-12-25
> **kansasnoob said:**
> The steps here work for me:

[http://ubuntuforums.org/showpost.php?p=8548884&postcount=9](http://ubuntuforums.org/showpost.php?p=8548884&postcount=9)

But please everyone add your confirmation to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

In fact I'd appreciate if someone would change the status to Confirmed.
Confirm the friggin bug.  I see that, according to the bug page, this effects THREE people.

I am sure that this number is low judging from the pissing and moaning on this forum.  Our job is to report bugs.

DO IT.

---

### Post by kansasnoob on 2010-01-06
I burned the 01/05/2010 daily live CD and confirmed that this is fixed.

I see that the 01/06/2010 is out now if anyone would care to double check me. I did have to use Safe Graphics mode.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

---

### Post by Lepodo on 2010-01-06
I did the same as kansasnoob and can confirm that it is fixed. ;)

---

### Post by kansasnoob on 2010-01-06
> **Lepodo said:**
> I did the same as kansasnoob and can confirm that it is fixed. ;)

Would you please confirm that at the bug report?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250)

That way the devs needn't waste any more time on that one.

---

### Post by Lepodo on 2010-01-06
Do I post anything informational or just confirm it? Sorry but thsi is my first bug report

---

### Post by ranch hand on 2010-01-06
You will have to hit the effects me too link and then add a comment at the bottom of the page to the effect that it is fixed.

I need to download the bugger to see if this is the case on my hardware and ad a comment too.

---

### Post by ranch hand on 2010-01-06
I was happy when the bugger booted right up.  Posted comment on bug page.

I was not so happy that the installer did not work.

First it wouldn't load.  Joined that bug.

Then I ran apt update and installed ubiquity (on LiveCD) ran "sudo ubiquity" since I was in terminal and it came up.  Added comment to bug.

Got to the partitioner and, of coarse, it folded up on me.  Open gparted and create my partitions.  Open the installer from link on desktop (very happy).  Installer still folded at partitioner (not happy at all).

Apport did not react at all to this so I just added a comment on the installer (ubiquity) bug page.

I hope this works Monday or Tuesday for the ISO testing for A2.

---

