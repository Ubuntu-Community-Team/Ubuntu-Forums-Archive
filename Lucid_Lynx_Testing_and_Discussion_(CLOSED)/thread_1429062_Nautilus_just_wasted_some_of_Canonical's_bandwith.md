---
title: "Nautilus just wasted some of Canonical's bandwith"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by splicerr on 2010-03-13
So I'm already running Lucid, but also wanted to download one of the latest Live CDs from here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

So I downloaded one of them. On the website it's listed with a size of 676MB and Firefox also listed the download size as 676MB. But when I went to the downloads folder the file was listed as having a size of 708MB, too big to fit on a CD-ROM, so I deleted it and downloaded it again, alas again too big, tried another one and another one... Finally I thought maybe something is wrong with Nautilus, so I used ls -hl:

```

$ ls -hl Downloads/lucid-desktop-i386.iso
-rw-r--r-- 1 splicer splicer 676M 2010-03-13 21:03 Downloads/lucid-desktop-i386.iso

```Turn out there's also a bug report about this, and apparently this new Nautilus behavior is by design. 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165)

This decision must have been made by some bureaucrat out of touch with reality. Anybody know how I can make Nautilus list the file size as the rest of the world does?

Thanks!

---

### Post by kahumba on 2010-03-13
This is a clash of 2 views, to represent the size on the desktop by 1000 or by 1024. Generally most people expect 1024 including me, and I agree with you, Nautilus usually chooses the worst solution imo. Nautilus is lucky cause it's the default file browser (like IE6 is on XP) and cause there's no decent alternative file browser for Gnome (thunar has ridiculously huge buttons and other issues).
So basically, live with it, choose another (wacky) file browser or create your own one. Sorry for not being "optimistic".

---

### Post by Jordanwb on 2010-03-13
Don't let hard drive manufacturers change standards.

Problem solved.

IMO: 1KB = 1024B

---

### Post by MacUntu on 2010-03-13
> **Jordanwb said:**
> Don't let hard drive manufacturers change standards.

Don't let computer nerds change standards. 'Kilo' = 1000. ;)

---

### Post by napsy on 2010-03-13
By standards it's:

1 MiB = 1024 KiB = 2^20 B

and

1 MB = 1000 KB = 10^6 B

---

### Post by kansasnoob on 2010-03-13
Yeah, I think I opened a real can of worms when I filed that one :D

FYI my related thread: 

[http://ubuntuforums.org/showthread.php?t=1428022](http://ubuntuforums.org/showthread.php?t=1428022)

I've even fumed a bit, biting my tongue a bit over this comment:

> Erick, you are not the only subscriber.

Uh, yeah I was ATM, that's why I said ATM!

I'm fully aware that the reports get dumped in many mailboxes, but I was the only subscriber ATM.

And if just getting dumped in many mailboxes solved things someone should have this nailed:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097)

What bug can possibly be worse than a bug that prevents us from filing bug reports?

---

### Post by gletob on 2010-03-13
> **MacUntu said:**
> Don't let computer nerds change standards. 'Kilo' = 1000. ;)

Don't use kilo, it's kibibyte.

---

### Post by Mr. Picklesworth on 2010-03-13
> **gletob said:**
> Don't use kilo, it's kibibyte.

Geeks shouldn't be allowed to invent measuring scales. We used up our made-up words quota years ago :b

Splicerr: It's always a good idea to open up the image and see if it will actually work instead of relying purely on the file size. The disk burning tools are awesome (Brasero has a beautiful interface, in my opinion!) and know exactly what will fit and what won't. I've seen Brasero perform magic tricks of all sorts, usually to good end.

(Except that time it turned a DVD into a toad. That was troublesome.)


As for Nautilus being nasty, I have to agree, although slightly reluctantly because there's really nothing better. All these file managers are trying to do too much. They need to be decoupled! Nautilus feels like it should be three different applications at least.

---

### Post by recluce on 2010-03-14
Also discussed here:

[http://ubuntuforums.org/showthread.php?t=1428022](http://ubuntuforums.org/showthread.php?t=1428022)

I dropped out of that thread, as I cannot stand the "Everything the Ubuntu developers do comes directly from GOD" attitude displayed by some few people.

At this point in time: 

Operating systems using base2 file sizes (1024 bytes = 1kB): everybody (Windows, BSD, Unix derivates, all other Linux distros, DOS, embedded devices), except the two listed below....

Operating systems using base10 file sizes: Ubuntu Lucid, Mac OS X Snow Leopard

So why does Ubuntu nowadays copy everything Apples believes is cool, no matter how much confusion and antagonism it may cause? If they need to be so SI-conforming, they could just change the units "kb" and "MB" to "KiB" and "MiB" instead of converting the numbers! But then, they should also remove Celsius and Fahrenheit and use Kelvin EXCLUSIVELY! ;) 

BTW: the changes are not limited to nautilus, it also effects the command line, for example the ls command.

@splicerr: this is the tip of the iceberg. Confused posts about wrong file sizes will only be second to confused posts about the buttons being in the wrong spot, once Lucid is released.

---

### Post by mc4man on 2010-03-14
While I actually like the change - I believe there is a ppa for a glib that uses the previous method of file size, whatever..
[https://launchpad.net/~bdrung/+archive/base-2](https://launchpad.net/~bdrung/+archive/base-2)

---

### Post by MacUntu on 2010-03-14
> **recluce said:**
> If they need to be so SI-conforming, they could just change the units "kb" and "MB" to "KiB" and "MiB" instead of converting the numbers!

I'd be (and was) totally happy with that (right) solution. :-\"

---

### Post by kansasnoob on 2010-03-14
> **mc4man said:**
> While I actually like the change - I believe there is a ppa for a glib that uses the previous method of file size, whatever..
[https://launchpad.net/~bdrung/+archive/base-2](https://launchpad.net/~bdrung/+archive/base-2)

Great find!

---

### Post by splicerr on 2010-03-15
Cool looks like the change has been reverted. With the latest glib updates Nautilus is back to listing file sizes as the rest of the world does. :D

---

### Post by lisati on 2010-03-15
> **kansasnoob said:**
> 
Uh, yeah I was ATM, that's why I said ATM!

I'm fully aware that the reports get dumped in many mailboxes, but I was the only subscriber ATM.


Yet another potentially confusing term. I can't see the point of mentioning **A**utomated **T**eller **M**achines. :)

---

### Post by bdrung on 2010-03-15
> **splicerr said:**
> Cool looks like the change has been reverted. With the latest glib updates Nautilus is back to listing file sizes as the rest of the world does. :D

We reverted the [FONT=monospace]glib patch, because it produces inconsistency in other applications. We will adhere to the [units policy]("https://wiki.ubuntu.com/UnitsPolicy") and we will patch Nautilus before lucid will be release to avoid dialog like these:

[IMG]http://launchpadlibrarian.net/40938824/karmic-disk-properties.png[/IMG]
[/FONT]

---

### Post by mc4man on 2010-03-15
> We will adhere to the units policy  and we will patch Nautilus before lucid will be release to avoid dialog like these:
I'm taking that to mean the patch or similar will be restored at some point by release which would be a good thing

---

### Post by bdrung on 2010-03-15
> **mc4man said:**
> I'm taking that to mean the patch or similar will be restored at some point by release which would be a good thing

Nautilus will show file sizes in base-10 before final release. Technically we will drop the glib patch and write a patch for Nautilus. I hope that we get as many programs fixed in lucid.

---

### Post by thatguruguy on 2010-03-15
> **Mr. Picklesworth said:**
> Geeks shouldn't be allowed to invent measuring scales. We used up our made-up words quota years ago :b

  When I first learned about computers, a "kilobyte" meant "1024 bytes". And that was in 1980. Is that what you mean when you use the words, "years ago"?

EDIT: I wrote 1982 when I should have written 1980.  I'm old, and I forget stuff.

---

### Post by tekstr1der on 2010-03-15
Huh. I've always used du & df commands for this info. Guess I've never paid attention to nautilus. For me, nautilus file properties just says:

Volume: Unknown

Free Space: Unknown


No pie chart, no used/free/total capacity/filesystem to see here. This happens as my user and as root with any folder. Anyone else?

---

### Post by lisati on 2010-03-15
> **thatguruguy said:**
> When I first learned about computers, a "kilobyte" meant "1024 bytes". And that was in 1982. Is that what you mean when you use the words, "years ago"?
I concur. I first learned about computers about the same time (late 1970s-early 1980s), and had the same understanding. My memory of the explanations I saw at the time is a bit hazy, but seem to recall that the main reason is that in a binary-based environment, 1024 is more "natural".

---

### Post by MacUntu on 2010-03-15
> **bdrung said:**
> Nautilus will show file sizes in base-10 before final release. Technically we will drop the glib patch and write a patch for Nautilus. I hope that we get as many programs fixed in lucid.

"Fixed" according to your units policy. ;) So if I don't like that policy I'll have to undo all those patches and patch glib again instead of eg. just switch a gconf key?

---

### Post by bdrung on 2010-03-15
> **MacUntu said:**
> "Fixed" according to your units policy. ;) So if I don't like that policy I'll have to undo all those patches and patch glib again instead of eg. just switch a gconf key?

What piece of the policy don't you like? Only users, which like [SI standard]("http://en.wikipedia.org/wiki/International_System_of_Units") for base-2 units, will be displeased. All other are hopefully happy.

We are aware that some user prefer base-10 and others base-2. For this reason, we have the clause: "Only show base-10, or give the user the opportunity to decide between base-10 and base-2 (the default must be base-10)." For this reason I created the [base-2 PPA]("https://launchpad.net/%7Ebdrung/+archive/base-2").

Instead of patching g_format_size_for_display() in glib, we hopefully introduce a new set of functions. These functions are then easy modifiable (with recompiling) to present base-2 or base-10. Please follow [glib bug #]("https://bugzilla.gnome.org/show_bug.cgi?id=554172")[554172]("https://bugzilla.gnome.org/show_bug.cgi?id=554172"), if you are interested in the progress.

---

### Post by Mr. Picklesworth on 2010-03-15
> **thatguruguy said:**
> When I first learned about computers, a "kilobyte" meant "1024 bytes". And that was in 1980. Is that what you mean when you use the words, "years ago"?
I'm talking more about the kibibyte, but that works, too :P

@bdrung: I, for one, love that unit policy. It's a nice document and I think having a solid policy like that will help us avoid misunderstandings in the future. Kudos for those who made it happen!

---

### Post by bdrung on 2010-03-15
> **Mr. Picklesworth said:**
> @bdrung: I, for one, love that unit policy. It's a nice document and I think having a solid policy like that will help us avoid misunderstandings in the future. Kudos for those who made it happen!

Nice to hear. The biggest benefit of this policy is that it will avoid endless discussions in bug reports about the validity of the requested changes.

---

### Post by MacUntu on 2010-03-15
> **bdrung said:**
> What piece of the policy don't you like? 
Basically this: "the default must be base-10" but base-2 is just my preference - there's nothing wrong with the policy! :)

> **bdrung said:**
> Instead of patching g_format_size_for_display() in glib, we hopefully introduce a new set of functions. These functions are then easy modifiable (with recompiling) to present base-2 or base-10. Please follow [glib bug #]("https://bugzilla.gnome.org/show_bug.cgi?id=554172")[554172]("https://bugzilla.gnome.org/show_bug.cgi?id=554172"), if you are interested in the progress.

Thanks for the link, interesting read (it's really hard to find objective discussions of this topic :P).

---

### Post by Menthu_Rae on 2010-03-15
> **bdrung said:**
> What piece of the policy don't you like? **Only users, which like [SI standard]("http://en.wikipedia.org/wiki/International_System_of_Units") for base-2 units, will be displeased. **All other are hopefully happy.

We are aware that some user prefer base-10 and others base-2. For this reason, we have the clause: "Only show base-10, or give the user the opportunity to decide between base-10 and base-2 (the default must be base-10)." For this reason I created the [base-2 PPA]("https://launchpad.net/%7Ebdrung/+archive/base-2").

Instead of patching g_format_size_for_display() in glib, we hopefully introduce a new set of functions. These functions are then easy modifiable (with recompiling) to present base-2 or base-10. Please follow [glib bug #]("https://bugzilla.gnome.org/show_bug.cgi?id=554172")[554172]("https://bugzilla.gnome.org/show_bug.cgi?id=554172"), if you are interested in the progress.

**ONLY** users that dislike the **SI STANDARD** will be displeased?

What a downright joke, mate. It's a standard for a reason. Burma, Liberia, and the United States are the only countries **not using SI units** in the whole world.

What kind of backwards OS is Ubuntu turning into that it decides to go against using the **international standard of unit measurement for filesizes**?

---

### Post by bdrung on 2010-03-15
> **MacUntu said:**
> Basically this: "the default must be base-10" but base-2 is just my preference - there's nothing wrong with the policy! :)

A easy to change default would be preferable. In lucid you will probably have to recompile at least one package to change the default. It's not the optimum, but with my PPA tolerable.

> **MacUntu said:**
> Thanks for the link, interesting read (it's really hard to find objective discussions of this topic :P).

It's hard to find two people with the same opinion on this topic. ;)

---

### Post by bdrung on 2010-03-15
> **Menthu_Rae said:**
> **ONLY** users that dislike the **SI STANDARD** will be displeased?

Yes, or be more specific: users that dislike the SI prefix standard, which defines kilo, mega, giga, and so on. There are some users out there that like base-2, but don't like the IEC prefixes.

> **Menthu_Rae said:**
> What a downright joke, mate. It's a standard for a reason. Burma, Liberia, and the United States are the only countries **not using SI units** in the whole world.

But these countries use the SI prefixes, aren't they?

 > **Menthu_Rae said:**
> What kind of backwards OS is Ubuntu turning into that it decides to go against using the **international standard of unit measurement for filesizes**?

The policy forbids the SI prefixes for base-2. Please read the policy: [https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)

---

### Post by thatguruguy on 2010-03-15
There are 10 kinds of people in the world.

Those who understand binary and those who don't.

---

### Post by Menthu_Rae on 2010-03-15
OK I think I was a little brash with my post, but the way I see it - this will create issues because the correct notations (for base-2 and base-10) aren't followed by many apps/websites/etc.

e.g. On the iiNet FTP mirror, the Ubuntu Desktop ISO shows as **690.80 MB**. This is actually Mebi-bytes (base-2), not Mega-bytes (base-10), so MB is incorrect and it should be prefixed MiB.

In Nautilus currently (Karmic), it is shown as **690.8 MB (724353024 bytes)**. Again, it is Mebi-bytes (base-2) not Mega-bytes (base-10) so MB is incorrect and it should be prefixed MiB.

However in Nautilus (Lucid), you guys are saying it will show as **724.35 MB** and this would be correct (since we divide the bytes using base-10) - so no problems here right?

Wrong. The idea for the changes all well and good *in theory* - but the problems will come about from all the apps and websites using MB for the base-2 prefix... they should technically be using MiB, but most users won't know that.

If I were re-writing nautilus. I would just show both. There is no harm to it and it's not like it's hard. Technical users will still know what's going on - and those who don't hopefully can ask, rather than just being entirely confused.

---

### Post by bdrung on 2010-03-16
> **Menthu_Rae said:**
> Wrong. The idea for the changes all well and good *in theory* - but the problems will come about from all the apps and websites using MB for the base-2 prefix... they should technically be using MiB, but most users won't know that.

Yes, using SI prefixes for base-2 and base-10 can lead to confusion. We neither can fix the web, nor the hardware manufacturers, but we can make Ubuntu consistent.

> **Menthu_Rae said:**
>  If I were re-writing nautilus. I would just show both. There is no harm to it and it's not like it's hard. Technical users will still know what's going on - and those who don't hopefully can ask, rather than just being entirely confused.

Showing both is allowed by the policy, but I doubt that showing both fit in GNOME's keep it simple policy.

---

### Post by recluce on 2010-03-16
> **mc4man said:**
> While I actually like the change - I believe there is a ppa for a glib that uses the previous method of file size, whatever..
[https://launchpad.net/~bdrung/+archive/base-2](https://launchpad.net/~bdrung/+archive/base-2)

Thank you! This will allow me to keep my sanity across a multi-OS environment! :p

---

### Post by captaincrook on 2010-03-18
If they don't go back now, the new waves of backlash on the forum will hopefully make them understand. What a terrible thing to change, ESPECIALLY for a long term release.

---

### Post by Gonz_91 on 2010-03-21
Well, just my two cents as a fairly seasoned computer user:
I can see why the devs would want to make things right, following the SI standards and whatnot, but also, I cannot see what's oh so wrong about our little geeky exception.
Additionally, I agree with someone who said earlier we should have the opportunity to just add the little "i", and keep our familiar numbers. I don't care if it's called a megabyte, a mebibyte, or whatever name they come up with next, as long as I don't have to pull out my calculator every time I want to know how many bytes something is using up.


As said, just my two cents.

---

### Post by tekstr1der on 2010-03-29
> **bdrung said:**
> We reverted the [FONT=monospace]glib patch, because it produces inconsistency in other applications. We will adhere to the [units policy]("https://wiki.ubuntu.com/UnitsPolicy") and we will patch Nautilus before lucid will be release to avoid dialog like these:

[IMG]http://launchpadlibrarian.net/40938824/karmic-disk-properties.png[/IMG]
[/FONT]

Topic of this thread aside, are we supposed to be seeing any of this information in nautilus' folder properties dialog? If I right-click a folder and choose properties, I only see volume:unknown, free space:unknown and no pie chart. This is on multiple installs on various hardware.

---

### Post by tekstr1der on 2010-03-30
Could someone test this please? If you are using lucid with nautilus could you right-click a folder, select properties, and see if you are displayed the information above? Thanks.

---

### Post by Sam on 2010-03-30
> **tekstr1der said:**
> Could someone test this please? If you are using lucid with nautilus could you right-click a folder, select properties, and see if you are displayed the information above? Thanks.

No it does not. The strange thing is the desktop properties which displays the total free space but not the others folders.

---

### Post by Uncle Spellbinder on 2010-03-30
> **tekstr1der said:**
> Could someone test this please? If you are using lucid with nautilus could you right-click a folder, select properties, and see if you are displayed the information above? Thanks.

Mine looks like this...

[IMG]http://content.imagesocket.com/images/PropertiesImagead4.png[/IMG]

---

### Post by mrsurb on 2010-03-30
The picture with the pie chart isn't a normal folder, it looks like a 4GB thumb drive or other removable media mounted on /media/130B-DABE

---

### Post by mrsurb on 2010-03-30
This is what appears when I attach a 32GB external drive, right-click its icon in Nautilus and select "Properties..."

---

### Post by tekstr1der on 2010-03-30
Thanks. I can see that with a USB drive myself. I realized from the screenshot showing the mount point, and I was curious why nautilus would get all detailed and fancy for a removable drive, but not the filesystem or partitions on the internal drive.

Is this a bug? A regression? Is it something that has never worked and/or is not fully implemented? Seems pretty weak!

---

### Post by Mr. Picklesworth on 2010-03-30
> **tekstr1der said:**
> Thanks. I can see that with a USB drive myself. I realized from the screenshot showing the mount point, and I was curious why nautilus would get all detailed and fancy for a removable drive, but not the filesystem or partitions on the internal drive.

Is this a bug? A regression? Is it something that has never worked and/or is not fully implemented? Seems pretty weak!

It's because a pie chart is completely pointless when it is measuring a segment of used disk space against the total free space on that disk. One could be made, but it wouldn't make any sense ;)

Thus, the pie chart and filesystem info is specific to a mounted volume. (Although, come to think of it, it would be awesome if Properties had a link to the separate Disk Utility for volumes and to the Disk Usage Analyzer for everything else).

---

### Post by Brian Vaughan on 2010-03-30
I'm pretty technically oriented, and I've found inconsistent practices on units to be thoroughly confusing. I like the new policy. At some point, there's got to be a deliberate shift towards a coherent standard, with clear and distinct units.

Also, outside of IT-land, people use decimal. Programmers and computer technicians are in the business of translating human intentions into machine code, and machine code into human language. So, using binary-based units and expecting regular people to adapt is just backwards. Decimal should be the norm for formatting output.

---

