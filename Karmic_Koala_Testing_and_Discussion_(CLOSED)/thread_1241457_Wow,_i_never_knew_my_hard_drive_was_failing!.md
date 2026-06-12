---
title: "Wow, i never knew my hard drive was failing!"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yvan300 on 2009-08-16
Ok, so i just updated karmic and it seems as though it has installed some hard drive inspection program. I installed karamic on an external hd but the scary thing is that it reports that my internal hd is failing. Could this be a bug or should i seek precautions etc?

---

### Post by autocrosser on 2009-08-16
Welcome to testing---you have found that the new gnome-disk-utility is a wee bit over sensitive :P:P:P  There are many posts about this--search for a couple of them & read the bug reports....there are quite a few of them also...................

---

### Post by Yvan300 on 2009-08-16
Phew, for a minute there i though i was in trouble, :)

---

### Post by nhasian on 2009-08-16
nah i think half the computers its installed on reports the hard disk is failing hehe

---

### Post by Yvan300 on 2009-08-16
Wow, there should be some kind of warning signal or something, i already begun gathering money for a new drive, lol.

---

### Post by harry2006 on 2009-08-16
thats way too much precaution....

---

### Post by lisati on 2009-08-16
> **autocrosser said:**
> Welcome to testing---you have found that the new gnome-disk-utility is a wee bit over sensitive :P:P:P  There are many posts about this--search for a couple of them & read the bug reports....there are quite a few of them also...................

Nothing wrong with erring on the side of caution, even if it's premature. What would worry me more would be a detector of Pebkac errors: on my machine it'd be going off quite regularly!

---

### Post by | MM | on 2009-08-16
Apparently one of my disks is failing... not too concerned cos all it has is my Os's.

What does annoy me is the icon that won't go away in the panel.

---

### Post by Yvan300 on 2009-08-16
+1

---

### Post by meborc on 2009-08-16
> **Yvan300 said:**
> +1

well, isn't there any way to disable it from startup programs???

(sorry, testing kubuntu karmic, and no icons there)

---

### Post by Katalog on 2009-08-16
I got the same kind of warning when I was trying to install Alpha 3 to dual boot with Jaunty on my netbook. It kept telling me I had serious errors on my drive and the installation could not continue until I fixed them. So I quit the install, ran fsck and it says everthing is fine. Glad to see I'm not the only one who ran into this sort of thing. It had me a little worried there for a bit.

---

### Post by oboedad55 on 2009-08-16
> **Katalog said:**
> I got the same kind of warning when I was trying to install Alpha 3 to dual boot with Jaunty on my netbook. It kept telling me I had serious errors on my drive and the installation could not continue until I fixed them. So I quit the install, ran fsck and it says everthing is fine. Glad to see I'm not the only one who ran into this sort of thing. It had me a little worried there for a bit.

Same deal here. When I run the CD it insists my secondary hd is full of errors. That's all it reports from the CD, I couldn't go any further without installing. It did make my heart skip a beat!

Jon

---

### Post by Taiebot65 on 2009-08-16
My message disappeared after the check at the boot... the strange thing is i m only testing live cd...

---

### Post by keithpeter on 2009-08-16
Hello Worried Ones

As others have said, this appears to be a bug!

Hard drive manufacturers give out a bootable .iso with some drive testing software specific to their drives. I downloaded the Samsung one and did a full test (3 hours) so I KNOW the hard drive in this machine is not failing.

I had to google for a *bootable* image, just searching for Samsung hard drive checking program threw up links to windows software. The Samsung .iso boots into freedos then runs a utility.

To switch off the notifications: System | Preferences | Startup Applications and then untick Disc Notifications. Next time you boot, you won't get the warning. I've put mine back on again so I know when the bug gets fixed :)

cheers

---

### Post by eyelessfade on 2009-08-16
I kind of liked it. Downloaded the Seagate "rescue disk" and it "fixed" my bad block. With only a single badblock I'm not worried anymore. Since its only 6 month old disk I'm kind o happy for it (it was a replacement for another failing disk)

---

### Post by stinger30au on 2009-08-16
> **| MM | said:**
> Apparently one of my disks is failing... not too concerned cos all it has is my Os's.

What does annoy me is the icon that won't go away in the panel.

oh wow...

does Koala have an icon that intergrates with the "s.m.a.r.t" on your hdd & warn you...

how cool is that :guitar:

---

### Post by froggyswamp on 2009-08-16
> **Yvan300 said:**
> Wow, there should be some kind of warning signal or something, i already begun gathering money for a new drive, lol.

me too, good to know it's just a bug

---

### Post by Moop on 2009-08-16
In my case the hard drive really was failing. After getting the warning I checked it with Western Digitals bootable cd, it failed the short test and would just freeze up on the long test. 

It's about a 6 yr old 74gb raptor that isn't under warranty any longer. I'll take it apart and keep the magnets and toss the rest. :)

---

### Post by Seventh Reign on 2009-08-16
It seems to give the error if you have an NTFS formatted drive that needs a serious Defrag and Scandisc run on it too.  Just a smidge too sensitive.  

I believe its a bug in the App, not in Ubuntu.  Fedora 11 has the exact same problem.

---

### Post by psyke83 on 2009-08-16
> **Seventh Reign said:**
> It seems to give the error if you have an NTFS formatted drive that needs a serious Defrag and Scandisc run on it too.  Just a smidge too sensitive.  

I believe its a bug in the App, not in Ubuntu.  Fedora 11 has the exact same problem.

From what I've seen on the bug report and information posted, the problem is not related to filesystem issues. The notification is purely warning about SMART attributes (Uncorrectable_Count, Current_Pending_Sector_Count, Reallocated_Sectors_Count and possibly others).

The problem with this utility is that the author has decided to warn users about SMART attributes that indicate bad sectors on the drive, even if the bad sectors have been "corrected" (reallocated) by SMART already. This is unnecessary.

---

### Post by wayne_cat on 2009-08-16
The only relevant SMART result is:

```
rschmitt@macbook:~$ sudo smartctl -H /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
**[COLOR=Red]SMART overall-health self-assessment test result: PASSED[/COLOR]**

rschmitt@macbook:~$ 
```The only function of the new SMART support in gnome-disk-utility is: It spreads panic!

Who had the idea to implement it before it is at least a little bit useful ... I guess there is a marketing manager from a big hard disk manufacture in 
the gnome-disk-utility dev team ... "Hey ... let's stimulate the disk sells".

---

### Post by jerrylamos on 2009-08-16
From working in the computer industry, almost all hard drives have bad spots which are spared out.  The only cause for alarm is if the bad spots are increasing.

Everybody should be backed up anyway - now when was the last time I did?

Jerry

---

### Post by Paqman on 2009-08-16
For most people all Palimpsest is complaining about is a few bad sectors. It's not unusual to have the odd bad sector on a drive, and the hard drive itself will seamlessly take care of the issue.

If you look under "details" in Palimpsest, check the number of remapped sectors. If it's only a handful and not increasing then you don't need to worry, it's just normal wear and tear on the drive.

---

### Post by andrewabc on 2009-08-16
Only useful info I have noticed is power on hours, and power on counts.

My old (2001) computer has 800 days, meanwhile new(2007) computer has about 350 days I think.

It had some items listed as pre-fail and stuff. Didn't say hard drive was failing though.

---

### Post by SeePU on 2009-09-05
The utility SHOULD NEVER HAVE BEEN RELEASED.  Obviously, it's not reliable and the calculation/measurement/assessment, call it what you want it, is not reliable so you don't know if the drive has any issues or not.  Too many have used other tools that give a different message, so the utility is useless.  Just because it's assumed it's a bug, doesn't mean you can excuse it.  I think flashing 'disk is failing' messages when it's not a reliable assessment is very unnecessary.  It causes alarm and confusion and is not a help at all.

---

### Post by amano on 2009-09-05
I am sure that this behaviour can be turned off. 

Just file a bug for Karmic to do so before the release. Or is there any already?

---

### Post by froggyswamp on 2009-09-05
> **SeePU said:**
> It causes alarm and confusion and is not a help at all.
+1
Makes me remember Linus's words about "untested crap". This app with this bug ships with Fedora 11 and its devs didn't bother to fix it. So talk about criteria for "stable" releases of Linux desktops. Hope Ubuntu devs either fix it before release or remove this app.

---

### Post by SeePU on 2009-09-05
> **froggyswamp said:**
> +1
Makes me remember Linus's words about "untested crap". This app with this bug ships with Fedora 11 and its devs didn't bother to fix it. So talk about criteria for "stable" releases of Linux desktops. Hope Ubuntu devs either fix it before release or remove this app.
Since it is supposedly reporting hardware failure and something that is semi-serious to the user, perhaps, a blurb on the website is in order?  It could detail the ongoing progress with the utility or at least mention that it might not be 100% accurate.  It's almost akin to Windoze/MikeySoft's message that 'it's okay to remove hardware...' (in Linux, you 'just unplug the thing!').  My complaint, is that it shouldn't be a very complicated modification or adjustment to mention it needs more work or to wait until it's functioning more accurately before placing it in any version, beta, alpha or otherwise.  Like I said, it's not useful if it is reporting "minor" failures or issues since it's not giving a sufficiently accurate picture of the situation.

---

