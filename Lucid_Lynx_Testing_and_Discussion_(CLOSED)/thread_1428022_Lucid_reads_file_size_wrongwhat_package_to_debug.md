---
title: "Lucid reads file size wrong/what package to debug?"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-03-12
On the 10th I was going to burn the daily iso to do some testing and noticed that it appeared to be oversize even though the daily build web page showed the size to be 685 MB (by memory).

I didn't think too much of that and noticed yesterday they never did post a new daily, then this AM I zsynced the new build and while the web page says it's 676 MB it showed up as 708.3 MB in Lucid.

So a light bulb went on and I booted into Jaunty and checked the size, viola 675.5 MB, so it wasn't an oversize iso after all :D

So now what? I have no idea what package to file a bug report against? Nautilus? That seems awfully broad.

---

### Post by kansasnoob on 2010-03-12
Well I decided to just let Apport sort this out so I booted back into Lucid and opened the Downloads folder and clicked on Report a problem, errrm that's a problem:

[ATTACH]149856[/ATTACH]

So I guess I'll try starting with ubuntu-bug apport ;)

---

### Post by kansasnoob on 2010-03-12
Nope! Can't report any bugs using Apport!

---

### Post by kansasnoob on 2010-03-12
OK I filed a bug report using "http://bugs.launchpad.net/ubuntu/+source/nautilus/+filebug?no-redirect":

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165)

I sure would appreciate anyone checking the size of any isos or other large files in their Lucid to see if they have the same problem.

I'm going to see if todays daily build will run for me and see how it reads the sizes of my isos.

---

### Post by kansasnoob on 2010-03-12
Just double checked this using todays daily build Live and it's the same way. Reads an iso that's about 676MB as 708.3MB.

---

### Post by kansasnoob on 2010-03-12
I don't see how this can be right but the reply I got:

> 

Thank you for your bug report. However, this is due to recent changes to standardise the units that are used on the desktop (see [https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy) for details).

Your issue is that the web page is using the SI prefix for presenting a base 2 number, which is incorrect (718 * (10^6/2^20) = 685)
Changed in nautilus (Ubuntu):
status: 	Confirmed &#8594; Invalid 

All other OS's on my machine say the image is 675.5MB but lucid says it's 708.3MB. I tried installing Thunar and it reads the image as 675.5!

What kind of hassle is it going to be telling a 700MB disc to hold a 708.3MB image??????????

Whoever is putting up the Daily iso's posts the size as 676MB!!!!!!!!!!

So I guess that Lucid's Nautilus is right, the devs that put up the size of the Daily iso's are wrong. Thunar is wrong and I suppose CD manufacturers are wrong - they're not 700MB dics anymore??????????

WTF?????????????????

Time to take a break from the insanity!

---

### Post by Endolith on 2010-03-12
Right.  Your image is 708.3 MB, which is equal to 675.5 M**i**B, with an *i*.  Jaunty was wrong to use "[MB]("http://en.wikipedia.org/wiki/Megabyte")" when it meant "[MiB]("http://en.wikipedia.org/wiki/Mebibyte")".  Lucid is using the correct units and this will solve a lot of confusion.

---

### Post by kansasnoob on 2010-03-12
> **Endolith said:**
> Right.  Your image is 708.3 MB, which is equal to 675.5 M**i**B, with an *i*.  Jaunty was wrong to use "[MB]("http://en.wikipedia.org/wiki/Megabyte")" when it meant "[MiB]("http://en.wikipedia.org/wiki/Mebibyte")".  Lucid is using the correct units and this will solve a lot of confusion.

Well suffice it to say I disagree with the notion that "**this will solve a lot of confusion**". I much more agree with the last comment here:

[https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)

> This policy is a real trouble-maker. (See [http://ubuntuforums.org/showpost.php?p=8956284&postcount=6](http://ubuntuforums.org/showpost.php?p=8956284&postcount=6)). 700 "MB" CDs are apparently 700 MiB, but have always been referred to as 700 MB. The consequence is that people are seeing "oversized" ISOs when they really are properly sized, which is a much bigger issue than someone getting confused about the file size. Additionally, (@last poster) systems such as Windows use base-2, and the quickest way of checking integrity is looking at size.--Ibidem 

While I'm sure you're technically correct there can be 180 degrees of separation between what's technically correct and what's user friendly. I have no technical training in computer technology, and I'm sure most end users don't possess that skill level.

Consider this GUI:

[ATTACH]149898[/ATTACH]

Now most users probably don't even bother to look, but when I see 707.1MB an alarm goes off. Whoa my CD's are only 700MB, but it also says I'll have 29.8MB of free space :o

Man oh man I sure got a bargain on those CD's they're 736.9MB each, I sure wished I'd bought more of those :D

So to most end users IMHO it creates confusion rather than solving it. Even more so when the behavior differs in Thunar, I haven't been able to check Konqueror as the current Live CD won't run on my hardware.

I'd almost bet iso testing is going to raise a few eyebrows ;) Are they to use your new formula? If so everyone will say, hey do we need to use DVD's?

We'll see.

---

### Post by Endolith on 2010-03-12
> **kansasnoob said:**
> Well suffice it to say I disagree with the notion that "**this will solve a lot of confusion**". I much more agree with the last comment here:

So, instead of using standardized units that have an unambiguous meaning, you want to use units that can mean different things in different places?  And you think that will *reduce* confusion??

> While I'm sure you're technically correct there can be 180 degrees of separation between what's technically correct and what's user friendly. I have no technical training in computer technology, and I'm sure most end users don't possess that skill level.Right.  End users with no computer training think that kilo- means 1000.  Which it does.  
kilometer = 1000 meters.  
kilogram = 1000 grams.  
kilobyte = 1000 bytes.

It's only the people who have had some computer science training who even know about Windows' stupid, non-standard 1024 definition, and they're smart enough to deal with the discrepancy.

The Linux Programmer's Manual describes how to do it right:

[http://manpages.ubuntu.com/manpages/lucid/man7/units.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/units.7.html)

Apple follows the standards, too:

[http://support.apple.com/kb/TS2419](http://support.apple.com/kb/TS2419)

Is the typical Apple user more technically skilled than the typical Linux user?

> Consider this GUI:

[ATTACH]149898[/ATTACH]

Now most users probably don't even bother to look, but when I see 707.1MB an alarm goes off. Whoa my CD's are only 700MB, but it also says I'll have 29.8MB of free space :oYes, that's confusing.  Your CD is actually 734 MB = 700 MiB.  They need to fix the bug in  Brasero:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/315913](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/315913)

This guy says it better than I ever could:

[http://lpar.ath0.com/2008/07/15/si-unit-prefixes-a-plea-for-sanity/](http://lpar.ath0.com/2008/07/15/si-unit-prefixes-a-plea-for-sanity/)

---

### Post by kansasnoob on 2010-03-12
> Yes, that's confusing. Your CD is actually 734 MB = 700 MiB. They need to fix the bug in Brasero:

I understand that now, but all of my discs are labeled 700MB (not MiB), so the average end user like me is going to think that if they right click an iso image in Nautilus and it says 707.1MB, or if Brasero shows the same it isn't going to fit. Or maybe all disc manufacturers need to be convinced to relabel their discs?

And I'm not just being argumentative, now that I know I'll take this into consideration, it's not a show-stopper to me.

But I'm sure I won't be the last to be puzzled. As I said we'll have to wait and see :)

---

### Post by recluce on 2010-03-12
Sigh, change for change's sake. I go back in computing a bit longer, so from the late 70s on, a Kilobyte (kB) was 1024 Bytes, a Megabyte (MB) was 1024 kb or 1024*1024 bytes (earlier too, but that I don't remember).

Some marketing guy at a hard drive manufacturer came up with the "1000 byte = 1 kB" cr*p - and it stuck, to the point that we got nonsense constructions like Mibibyte (sp?) or "MiB" and some computer-analphabets "made it the norm".

Fortunately, most filesystems ignored this rubbish and stayed with the base2 byte count, not even Microsoft messed it up. ;)

Now Ubuntu does it - of course without telling anybody and of course, causing a lot of FUD in the process. So my question now: how the f**k can I reconfigure Lucid to behave sanely (1 MB = 1024B)?

---

### Post by ranch hand on 2010-03-12
Well, I for one am happy to read this thread.  It will save me some irritation.

Thanks kansasnoob.

---

### Post by kklimonda on 2010-03-12
@recluce: Well, to revert back those changes you would have to recompile some libraries (I know that glib has been patched but it's most likely not the only library).

---

### Post by recluce on 2010-03-13
> **kklimonda said:**
> @recluce: Well, to revert back those changes you would have to recompile some libraries (I know that glib has been patched but it's most likely not the only library).

That is a lot of work, if you don't know which libraries are broken, ahem, sorry, have been patched. Thank you for the information. While I don't have much hope, maybe somebody will come up with a workable solution. 

I am considering to switch to another distro - is Debian messing around with file size calculation as well?

---

### Post by kansasnoob on 2010-03-13
@Recluce, you asked, "is Debian messing around with file size calculation as well?"

ATM Squeeze still uses the old (IMHO proper) behavior. Now, before I get jumped on, when I say "proper" I've already explained that to non-techies like me (and most of us) I buy discs and they say 700MB (not MiB) so when both Nautilus and Brasero tell me an image is over 700MB I'd think "oh crap" time to bust out a DVD or USB stick.

But I have installed presently Hardy, Jaunty, Karmic, Lucid, Fedora12, Mint7, WinXP, and Squeeze - of those only Lucid has this "odd" behavior.

---

### Post by kklimonda on 2010-03-13
@recluce: No, from what I can tell debian hasn't yet made a decision to either go with the change or don't. I'm pretty sure that even if they decide to follow us it won't happen before squeeze release. The change is indeed somewhat controversial but it's not a "change for the sake of change" - there are real problems that developers try to fix (I think one of better examples of the broken behaviour is this screenshot: [http://bugzilla-attachments.gnome.org/attachment.cgi?id=155865](http://bugzilla-attachments.gnome.org/attachment.cgi?id=155865)). Even if you decide to switch over to Debian or other distribution this change may still affect you. 
@kansasnoob: Brasero has already been discussed in this thread.

The current behaviour is broken - only because it has been broken for years is not a reason not to fix it.

---

### Post by kansasnoob on 2010-03-13
> Brasero has already been discussed in this thread.


I'd think I'm aware of that since I'm the one that brought it up. But Brasero is displaying the same "size" reported by Nautilus.

And I've already made clear the difference between "technically correct" and "user friendly". If I go buy CD's they're marked 700MB, is that not correct?

If I right click an iso in Nautilus to check properties and it says the iso is in excess of 700MB does that not create confusion?

If you refer to my bug report you'll see that Chris Coulson said:

> Your issue is that the web page is using the SI prefix for presenting a base 2 number, which is incorrect (718 * (10^6/2^20) = 685)

So if those posting the size of an iso image use the "correct" method won't most people think that if the image is over 700MB it will NOT fit on a 700MB disc?

I'd mentioned previously that maybe we can get the whole industry to start relabeling their discs :D

I really don't think I can be any more clear than that, or as Forrest Gump would say, "that's all I have to say about that".

---

### Post by kansasnoob on 2010-03-13
I lied, I guess I wasn't done after reading the last response at launchpad. Here's what I had to say:

> 

I just want to clarify a couple of things here for those who may not follow the discussion on the forums:

[http://ubuntuforums.org/showthread.php?t=1428022](http://ubuntuforums.org/showthread.php?t=1428022)

I'm just an end user with no actual computer training and I respect your opinions as developers with true technical knowledge in this field. I hope you can respect my opinion as well. As I'm the only subscriber to this thread ATM I assure you I have no intention of debating this ad nauseam, now that I understand what's up I'll adjust to it, but I just want to point out how this effects the common end user such as myself.

Point #1: CD's are marketed and labeled as 700MB. (I've never bought discs that would make me aware that, "Your CD is actually 734 MB = 700 MiB." BTW that quote is taken from Endolith's post here:

[http://ubuntuforums.org/showpost.php?p=8957863&postcount=9](http://ubuntuforums.org/showpost.php?p=8957863&postcount=9)

Point #2: Currently the devs that put up the Ubuntu, Xubuntu, and Kubuntu daily builds show the size incorrectly according to Chris Coulson: "Your issue is that the web page is using the SI prefix for presenting a base 2 number, which is incorrect (718 * (10^6/2^20) = 685)". That comes from post #2 of this report. So they must all change to using your new "correct" method?

Point #3: If the daily builds, the iso testing builds, and the release announcements themselves all adopt this standard, as described above, won't most end users, such as myself, think they would then need to use a DVD or Flash Drive? How would that work? I'd really like an answer to that one!

Point #4: At this time I'm multi-booting Win XP, Hardy, Jaunty, Karmic, Lucid, Mint Gloria, Fedora 12, and Debian Squeeze. I even tried the current Lucid Thunar and it still follows the old behavior. Only Lucid's Nautilus employs this new policy, is this really a good move given points #1, #2, and #3 above?

In conclusion, as an "uneducated" end user, I must say I don't see how this can work without getting the disc manufacturers to clarify the difference between MB and MiB, do you really think you can bring that about?

I guess we'll all need to get re-educated to keep using Ubuntu.


Link:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165)

---

### Post by Endolith on 2010-03-13
> **recluce said:**
> Sigh, change for change's sake.

Nope.

>  I go back in computing a bit longer, so from the late 70s on, a Kilobyte (kB) was 1024 Bytes, a Megabyte (MB) was 1024 kb or 1024*1024 bytesNope.  It was never consistently used that way.

> Some marketing guy at a hard drive manufacturer came up withPeople keep saying this, but as far as I know, it's an urban legend.  I've never seen anyone produce any evidence of it.  Show some advertising or a manual from an old hard drive that marketed a measurement in base 2 units that wasn't just rounding.  See [http://en.wikipedia.org/wiki/Binary_prefix#Disk_drives](http://en.wikipedia.org/wiki/Binary_prefix#Disk_drives)

Were the networking manufacturers in on the conspiracy?  How about tape drives and disk drives?  A 56K modem was 56,000 bits per second, not 57,344. The Memorex 650 disk was marketed as "1.5 megabit", using mega = 1,000,000.    The "1.44 MB" disk, on the other hand, was 1.44 x 1024 x 1000 bytes, which is wrong no matter how you look at it.

The "good old days" when K always meant 1024 and M always mean 1024 x 1024 exist only in your mind.  It has always been inconsistent and confusing.

> how the f**k can I reconfigure Lucid to behave sanely (1 MB = 1024B)?It's being made to behave sanely as we speak.  The previous behavior was insane.


> **recluce said:**
> is Debian messing around with file size calculation as well?[http://wiki.debian.org/ConsistentUnitPrefixes](http://wiki.debian.org/ConsistentUnitPrefixes)

Mac OS X already made the switch to proper decimal units.  [http://support.apple.com/kb/TS2419](http://support.apple.com/kb/TS2419)

Yes, this will be confusing in the case of CDs in particular, because they're measured in MiB but stated as "MB" by the manufacturer. But everything else is measured in decimal and stated in decimal, including other optical disks.  Disk drives, DVDs, Blu-Ray, USB flash drives, etc. are all measured in decimal.  This is why I think they should show *both* measurements in Brasero, because it deals with both CDs and DVDs.

---

### Post by Longinus00 on 2010-03-13
This would have been much easier if they just changed the wording from MB to MiB instead of sticking with MB and then switching the numbers around. I'm sure if they did that virtually nobody would notice the extra 'i' and ubuntu could stay being consistent with previous expectations. Is this change pulled in from upstream or is it a ubuntu specfic patch?

---

### Post by kansasnoob on 2010-03-13
> Yes, **[COLOR="Red"]this will be confusing in the case of CDs in particular[/COLOR]**, because they're measured in MiB but stated as "MB" by the manufacturer. But everything else is measured in decimal and stated in decimal, including other optical disks. Disk drives, DVDs, Blu-Ray, USB flash drives, etc. are all measured in decimal. This is why I think they should show both  measurements in Brasero, because it deals with both CDs and DVDs.

And how is Ubuntu largely obtained?

Until you can convince all CD manufacturers to change there way leave it at alone! Or suffer the wrath of the masses ;)

After you convince all the CD manufacturers to amend their ways you can then convince the Thunar devs, the Brasero devs, etc!

We're looking at an LTS! Whatever decisions we make we'll live with for three years!

---

### Post by Arlanthir on 2010-03-13
I think I'd panic if I tried Lucid without having read this thread!
A bit awkward but also informative.

Have to remember this whenever I reboot to a new OS and all my free space amounts change.

What's the word on the other distros regarding this? Is there any agreement in the Linux world to change it or did Ubuntu take the initiative?

---

### Post by kansasnoob on 2010-03-13
> **Longinus00 said:**
> This would have been much **easier if they just changed the wording from MB to MiB** instead of sticking with MB and then switching the numbers around. I'm sure if they did that virtually nobody would notice the extra 'i' and ubuntu could stay being consistent with previous expectations. Is this change pulled in from upstream or is it a ubuntu specfic patch?

+1! Or +1.04~ :)

---

### Post by recluce on 2010-03-13
> **Endolith said:**
> 
Nope.  It was never consistently used that way.


No other definition than base2 was used up to some point in the 80s. Quote me other usage from before the time that hard drives showed up in personal computers.

> 
People keep saying this, but as far as I know, it's an urban legend.  I've never seen anyone produce any evidence of it.  Show some advertising or a manual from an old hard drive that marketed a measurement in base 2 units that wasn't just rounding.  See [http://en.wikipedia.org/wiki/Binary_prefix#Disk_drives](http://en.wikipedia.org/wiki/Binary_prefix#Disk_drives)


Just check out the size calculation of all floppy disks and floppy drives (go to wikipedia for a source, if you like). a 1.44 MB floppy was 1.44*1024² bytes. Same for optical media. Any media BUT hard drives was base2 calculated for the longest time.

> 
Were the networking manufacturers in on the conspiracy?  How about tape drives and disk drives?  A 56K modem was 56,000 bits per second, not 57,344. The Memorex 650 disk was marketed as "1.5 megabit", using mega = 1,000,000.    The "1.44 MB" disk, on the other hand, was 1.44 x 1024 x 1000 bytes, which is wrong no matter how you look at it.


Modem definitions were based on baud (pulses per second) and that definition originates with telex and earlier services, not the computer world. Thus transfer rates were always expressed as base10. The usage of "kbit/s" is indead wrong here, It should be kBd (kilo-Baud). Again, blame human laziness for no longer using the Baud unit where appropriate.

> 
The "good old days" when K always meant 1024 and M always mean 1024 x 1024 exist only in your mind.  It has always been inconsistent and confusing.

It's being made to behave sanely as we speak.  The previous behavior was insane.


Based on the above quote from you, I do not believe that you are a person to listen to reason, so I will quit trying. I was THERE in those days. I know what was used. Period.

Too bad that no other OS, except MAC OS (which is not exactly the OS of choice of most "nerds") agrees with Ubuntu.

> 

[http://wiki.debian.org/ConsistentUnitPrefixes](http://wiki.debian.org/ConsistentUnitPrefixes)



The above is three years old and apparently has resulted in no other effect than controversy.

It seems that Ubuntu has taken up the task of "reeducating" the computing world. Buttons on the left, base10 file size calculation and so forth. And we, the "Joe Users" of Ubuntu, just have to sit back in awe and take it as god given? Well, I do not want to be reeducated - and most other people do not want to be reeducated, either. This is too bad, as Ubuntu is just unnecessarily alienating users. Not a good choice if you want to elimiate bug #1 on launchpad. 

But enough said. To avoid further escalation, this will be my last post in this thread.

BTW: thanks to all the feedback given as to other Linux distros that keep the correct file size calculations for now

---

### Post by yoasif on 2010-03-13
> **Endolith said:**
> Mac OS X already made the switch to proper decimal units.  [http://support.apple.com/kb/TS2419](http://support.apple.com/kb/TS2419)I have seen this both here, the bug report and on the units policy page.

However, I have a simple question for you, if you can answer it. 

In the Finder, how are file sizes reported? base-2 or base-10?

---

### Post by IanW on 2010-03-14
Looks like it's the devs that need debugging, not Lucid.

---

### Post by 6205 on 2010-03-14
Another colossal BS... MiB, KiB or GiB?  What a nonsense... Staying on W7

---

### Post by rottentree on 2010-03-14
> **6205 said:**
> Another colossal BS... MiB, KiB or GiB?  What a nonsense... Staying on W7

Ubuntu didn't invent Mib and it's brothers.
You have to start fixing things one day because as time progresses it's just going to get more chaotic and harder to fix but I admit that it's questionable if it's good for Ubuntu.

Staying on my ***.

---

### Post by shafin on 2010-03-14
I Like this change, at last my 8 GB pen drive is 8.1 GB and not some 7.xx.

It might be confusing, but if it is not addressed soon, it might become another anomaly, like how electricity always flows opposite to the actual flow of electrons.

---

### Post by MacUntu on 2010-03-14
> **6205 said:**
> Another colossal BS... MiB, KiB or GiB?  What a nonsense... Staying on W7

My deepest condolences! :-s

---

### Post by Longinus00 on 2010-03-14
What's hilarious is that the new ubuntu unit policy [https://wiki.ubuntu.com/UnitsPolicy]("https://wiki.ubuntu.com/UnitsPolicy") is the pretty much what people voted not to do in the brainstorm [http://brainstorm.ubuntu.com/idea/17839/](http://brainstorm.ubuntu.com/idea/17839/)

---

### Post by rottentree on 2010-03-14
> **Longinus00 said:**
> What's hilarious is that the new ubuntu unit policy [https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy) is the pretty much what people voted not to do in the brainstorm [http://brainstorm.ubuntu.com/idea/17839/](http://brainstorm.ubuntu.com/idea/17839/)

What the majority vote for is not always the best.

---

### Post by LKjell on 2010-03-14
I understand why the new unit policy is needed. And I can use it when writing programs or write essays. But I will never ever use it orally in a technical situation. kilo is 2^10 This is because 10^3 is not viable. The SI prefix is only used in marketing purposes and for those mortals.

---

### Post by torer1 on 2010-03-14
Since we are righting wrongs ... (although it is slightly OT)

> **recluce said:**
> 

Modem definitions were based on baud (pulses per second) and that definition originates with telex and earlier services, not the computer world. Thus transfer rates were always expressed as base10. The usage of "kbit/s" is indead wrong here, It should be kBd (kilo-Baud). Again, blame human laziness for no longer using the Baud unit where appropriate.


It is a common misunderstanding, mixing baudrate with bitrate. These two measures are related - but only slightly. The baudrate specifies the number of "symbols" transferred per second. However, one symbol might represent one or several bits of information; how many depends on the type of modulation. 

Consider the common (well, it used to be) V29 16 point QAM modulation. The baud rate is 2400 baud (symbols per second). But since each symbol represents 1-of-16 different data points, it carries four bits of information across. Hence, the bit-rate is 2400 * 4 = 9600 bits / second.

---

### Post by Penguin Guy on 2010-03-14
Glad they've done this, but they should display all sizes in iB, rather than B, or at least give you the option to choose for yourself how sizes are displayed. For your information, although CD's are measured in MiBs, DVDs are measured in GBs - so although at first this may cause some CD confusion, it will avoid more confusion in the long run.
```

CD = 700MiB
DVD = 4.7GB

```
Yep, they're measured differently.
[More info here.]("http://lpar.ath0.com/2008/07/15/si-unit-prefixes-a-plea-for-sanity/")

---

### Post by bdrung on 2010-03-14
> **recluce said:**
> Just check out the size calculation of all floppy disks and floppy drives (go to wikipedia for a source, if you like). a 1.44 MB floppy was 1.44*1024² bytes. Same for optical media. Any media BUT hard drives was base2 calculated for the longest time.

Floppy disks are the best example of abusing standards. A floppy labeled with "1.44 MB" neither has 1.44 MiB, nor 1.44 MB. It has 1,440 KiB = 1,440 * 1024 bytes = 1474560 bytes = 1.47 MB = 1.41 MiB.

---

### Post by faustobp on 2010-03-17
> **recluce said:**
> I go back in computing a bit longer, so from the late 70s on, a Kilobyte (kB) was 1024 Bytes, a Megabyte (MB) was 1024 kb or 1024*1024 bytes (earlier too, but that I don't remember).

The convention which defines that a kilo = 1000 goes way back, it was created by Lavoisier **more than 200 years ago**. Some computer scientists of the 70s made a mistake when they tried to redefine kilo to a more practical value creating the mess we have today.

---

### Post by iwbcman on 2010-03-26
Until the day comes that we abolish the bit as the fundamental unit of all computation-and that includes the size of the registers in your cpu, to the pins coming out the bottom of that cpu, to the number of transistors used to represent a unit of memory in silicon memory chips, abandoning base-2 operations and all of the logic(electrical and algorithmic) based on that base, any mucking around the numbers being displayed at either the OS level or application level is just flat out, unconditionally wrong.

If one feels one must adhere to standards, which often amount to little more than mere conventions, even while one is transgressing against some 100 years of established binary usage in all things computational, the one can change the 2 letter prefix(MB) to a 3 letter prefix (MiB) if that really floats your boat. 

The issue at hand here is that the binary basis of computers is not *merely* a convention, it is not simply a matter that we talk about computers this way or that. It is not simply a standard. Our agreement, yours and mine-means NOTHING in terms of computation, in terms of algorithmic and electrical logic, which is the basis of the computer. 

Computers ARE binary, that is how they function, how they are built, how they are designed and how they work. In a world where almost everything is arbitrary, and we just need to agree to get along, computers are like stalwart reminders that not everything *is* arbitrary. (this impotence, this being thrown-back on ourselves in a futile attempt to make computers more human, even though there is NOTHING human about computers in terms of how they function, is the ultimate source of this little charade)

If you break the underlying link between the numbers that we get displayed in the outputs from the OS, from applications, etc. and the binary basis of these calculations you will get nothing more than a world of hurt:confusion, mistakes, wrong assumptions, and outright frustration.

The SI is a wonderful system. It's advantages are too many as to be denied. Personally I wish that the whole world would make the switch. But as with any standard, standards are only useful within a specific scope of application. In the scientific world where SI has had nearly universal success, it's success has been based on the fact that at the basis of all scientific activity there lies act of measuring. How we measure things is by definition arbitrary. And if we construct countless devices and instruments which record measurements in units that facilitate our practical utilities, science as a whole, and all things dependent on science make spectacular progress. Yet how much memory is being used is not in the first instance a measurement. There is a difference between that which is being measured and the measurement. One is a representation the other is not. How much memory is being used on a given media is a reality, not simply a way of looking at it. If you attempt to write more data to a medium than it can hold Bad Things Happen(TM). Regardless of how you or I or anyone else looks at it. 

Go ahead and change to GiB,MiB and KiB. I can ignore the little 'i' and get on with things. Change the actual numbers and you turn my computer into something which continually misrepresents, something that I cannot count on, something where it's only consistency is in the consistency of it's inaccuracy. And although we are used to such from politicians I really don't want my computer to become that way.

Have a nice day ;)

---

