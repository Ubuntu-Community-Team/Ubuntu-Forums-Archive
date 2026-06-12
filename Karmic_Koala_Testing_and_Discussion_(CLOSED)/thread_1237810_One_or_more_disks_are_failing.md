---
title: "One or more disks are failing"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2009-08-11
A new icon in the main panel just showed up.
Any body have this ? Right and left mouse click just shows "20 GB ATA MAXTOR 92049U6". How or what can I do with it ?

---

### Post by psyke83 on 2009-08-11
It sounds like a [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") notification, though I wasn't aware that SMART notifications were implemented like this. If that's the case, then you should take the warning seriously and backup any important data.

Usually you need to install "smartmontools" and run the following command to get detailed statistics:

```
$ sudo smartctl -a /dev/sdX
```

---

### Post by wayne_cat on 2009-08-11
> **cecilpierce said:**
> A new icon in the main panel just showed up.
Any body have this ? Right and left mouse click just shows "20 GB ATA MAXTOR 92049U6". How or what can I do with it ?


You can check your disks with the program "palimpsest" or from the command line:

(if sdb is the 20 GB disk)

```
devkit-disks --show-info /dev/sdb
```

---

### Post by Reiger on 2009-08-11
That notification bubble is palimpsest. Useful up to a degree: I had that too but only after my default mode of turning off the PC had degraded to hold-down-the-power-long-enough-will-work-too (Jaunty days with random X hangs). Being able to "stay up for 20 minutes" when doing actual work counted as a good day for me, so you can imagine that I did corrupt quite a few blocks of my harddisk.

Then when I booted into Fedora 11 I was greeted by an error message about how my harddisk was failing because palimpsest detected "bad blocks". Well, obviously. :P

---

### Post by cecilpierce on 2009-08-11
Thanks to all for the info, this is my KK 9.10 test drive so if it craps out I'll just have to buy another one. But....I wish I could turn off that icon!

---

### Post by Starks on 2009-08-12
I started getting the notification today.

Is this a bug or is my disk failing?

---

### Post by ktp on 2009-08-12
See this thread also

[http://ubuntuforums.org/showthread.php?t=1237899](http://ubuntuforums.org/showthread.php?t=1237899)

---

### Post by ktp on 2009-08-12
> **Starks said:**
> I started getting the notification today.

Is this a bug or is my disk failing?

It seems like there is a bug....see this comment

[http://ubuntuforums.org/showpost.php?p=7772393&postcount=17](http://ubuntuforums.org/showpost.php?p=7772393&postcount=17)

---

### Post by keithpeter on 2009-08-12
> **ktp said:**
> It seems like there is a bug....see this comment

[http://ubuntuforums.org/showpost.php?p=7772393&postcount=17](http://ubuntuforums.org/showpost.php?p=7772393&postcount=17)

[Me too]("http://ubuntuforums.org/showthread.php?p=7772663"). My computer has a Samsung hard drive so I downloaded the Samsung bootable drive checking program (Hutils210.iso) and did a full test (3 hours). No issues. I'll add to the bug report.

Comment: The alert identifies itself as 'Palimpsest' so I searched launchpad on that name, and here.

---

### Post by Jay_Bee on 2009-08-12
I am too getting that icon and a warning, it's kind of troubling.

---

### Post by ronacc on 2009-08-12
getting it here too , either is a bug or there are a lot of sick hard drives out there .

---

### Post by Bill.Gates on 2009-08-12
this was happening to me on fedora, it seems palimpsest says almost everyones drives are dying.  I'm not at my ubuntu box right now, but if my memory serves me correctly, in fedora you could go to system>preferences>startup and remove disk notificatons it will stop popping up.  I imagine it would be similar in ubuntu

---

### Post by MacUntu on 2009-08-12
S.M.A.R.T. is no standard. Raw values could mean anything and lead to such warnings (some of my hard disks show funny read error values that are magnitudes larger than the thresholds). I'd use that as an opportunity to check the disk with the vendor's tool but I wouldn't be too worried.

---

### Post by rajeev1204 on 2009-08-12
OK i too got this error today.But my hard disk has been behaving funny anyway with the light glowing continuously sometimes,but on reboot does disappear .

I think i have a problem with the MBR with boot failing sometimes.

But since a lot of users together got the warning,we can reasonably assume its a bug.

---

### Post by bear24rw on 2009-08-12
i got the error last night. it says that BOTH of my new 1.5TB drives are dying.. being that everyone seems to have this im thinking it is a bug..

---

### Post by keithpeter on 2009-08-12
> **MacUntu said:**
> S.M.A.R.T. is no standard. Raw values could mean anything and lead to such warnings (some of my hard disks show funny read error values that are magnitudes larger than the thresholds). I'd use that as an opportunity to check the disk with the vendor's tool but I wouldn't be too worried.

OK, that is exactly what *I* did, Samsung have a bootable iso image that I could burn to a CD-ROM and run a thorough test with. No issues. The test took three hours.

Respectfully suggest that an error message warning that the computer's hard drive is about to fail may not be the best welcome to the Ubuntu world for a user new to Linux!

---

### Post by ViRMiN on 2009-08-12
Phew!  I was getting a bit twitchy thinking that I had a dodgy disk on RAID-0, and two dying independent ATA disks too.  Will get the vendor tools and double check it's not true!

---

### Post by rajeev1204 on 2009-08-13
> **keithpeter said:**
> 
Respectfully suggest that an error message warning that the computer's hard drive is about to fail may not be the best welcome to the Ubuntu world for a user new to Linux!

Lol i agree.:):lol:

---

### Post by mgsfan on 2009-08-13
I've have this for the past few days ever since I did an update...scanned my hdd which said was failing and everything is fine so..bug

---

### Post by ViRMiN on 2009-08-13
My SATA RAID-0 disks are fine but, my PATA disks are genuinely on their way out it seems; kind of known that for a while but, they're never used for anything important, more like scratch disks!

---

### Post by keithpeter on 2009-08-13
> **ViRMiN said:**
> My SATA RAID-0 disks are fine but, my PATA disks are genuinely on their way out it seems; kind of known that for a while but, they're never used for anything important, more like scratch disks!

OK< how about putting the smartctl test results for your suspect PATA drives on the bug report for this issue or here so we can see what 'suspect' looks like? I'd find that educational.

---

### Post by Cuba71 on 2009-08-13
I was running the Live CD and got this notification on a secondary empty hard drive formatted NTFS.
I think it's a bug

---

### Post by vishalrao on 2009-08-13
Well lots of people/testers on the forum ask "why is karmic so boring and stable" so the developers give us this buggy stuff with a frightening warning for some excitement :lolflag:

---

### Post by ViRMiN on 2009-08-14
> **keithpeter said:**
> OK< how about putting the smartctl test results for your suspect PATA drives on the bug report for this issue or here so we can see what 'suspect' looks like? I'd find that educational.

Will give it a go and post up the results.  I used the vendor tools to test the disks to verify their status.

---

### Post by Grenage on 2009-08-14
You can turn of SMART in the BIOS, doesn't that stop it appearing?  SMART is quite notorious for flagging up issues where they won't cause a problem; the problems are usually there, it's just that they don't always have any real-world impact.

---

### Post by keithpeter on 2009-08-14
> **vishalrao said:**
> Well lots of people/testers on the forum ask "why is karmic so boring and stable" so the developers give us this buggy stuff with a frightening warning for some excitement

Aha, I see. I was expecting broken Xorg and being dumped onto command line log in on starting and stuff like that :)

---

### Post by practic on 2009-08-14
> **keithpeter said:**
> Aha, I see. I was expecting broken Xorg and being dumped onto command line log in on starting and stuff like that :)

Yeah, or getting the white or black "screens of death" at the desktop! [-o<

---

### Post by Giggity on 2009-08-14
> **vishalrao said:**
> Well lots of people/testers on the forum ask "why is karmic so boring and stable" so the developers give us this buggy stuff with a frightening warning for some excitement :lolflag:True, Karmic has been a real pleasure to run.  This is the first real problem I've seen.  Either that, or suddenly there's a worldwide bad sector epidemic.

---

### Post by SeePU on 2009-09-05
Whatever!   No wonder Ubuntu has so many bugs!  Users just laugh off whatever's wrong.  This is a serious bug if it is a bug!  Developers or testers don't find this stuff?!?  What are they doing with their time?!?  I think it's pretty serious if you are getting a message or warning that your drive is failing.  If it's false and a bug, then it's pretty stupid that the utility was released in the first place.  

I am getting this message when I try a LiveCD of Karmic x86 version, Alpha 5 and after a short period of time, everything freezes up and I have to turn off/turn off my notebook (Thinkpad T41).  So far, a horrible experience with Ubuntu, Karmic! 

In addition, the users who have tested on another tool, are you using something in Windows?  What tool is confirming that your drive is okay?  I think that if the one in Ubuntu/Linux, whatever it is, is not reliable, it SHOULD NOT BE RELEASED!

---

### Post by Paqman on 2009-09-05
> **SeePU said:**
> Whatever!   No wonder Ubuntu has so many bugs!  Users just laugh off whatever's wrong.

Karmic is still in alpha. So yes, the users should and do expect bugs. The whole point of running the development branch is to find and report the bugs.

---

### Post by cariboo on 2009-09-05
> In addition, the users who have tested on another tool, are you using something in Windows? What tool is confirming that your drive is okay? I think that if the one in Ubuntu/Linux, whatever it is, is not reliable, it SHOULD NOT BE RELEASED!

I use the diagnostic tools from my hard drive manufacturer. 

This is an old issue and has been discussed to death, the developer of Palimsest is correct in saying there are bad sectors on the hard drive. Personally I think the threshold for notification is set to low.

---

### Post by wnelson on 2009-09-05
I turned on S.M.A.R.T in my BIO's and I had to hit F1 to continue. I also noticed things like apt-get when reading package list on my old drive incremented at 5% at a time. My new drive zips right on through. I guess leaving a machine on 6 years straight, (rebooted once in awhile), could cause a drive to fail after a while.

Walt
Tacoma,WA

---

### Post by Paqman on 2009-09-05
> **cariboo907 said:**
> Personally I think the threshold for notification is set to low.

Indeed. A handful of seamlessly reallocated bad sectors in no way needs a "Your hard disk is failing!" alert.

---

### Post by SeePU on 2009-09-05
> **Paqman said:**
> Karmic is still in alpha. So yes, the users should and do expect bugs. The whole point of running the development branch is to find and report the bugs.
Let's get this straight, then.  So, Ubuntu allows up to Alpha 5! a utility that falsely claims disk failure or claims disk failing based on a few bad sectors?!?   Furthermore, the LiveCD then soon freezes your entire system!  It's a notebook, sure, but it's a Thinkpad T4x series which is pretty reliable as far as computers/notebooks go.   Sorry, your excuse doesn't fly.  :rolleyes:

---

### Post by MacUntu on 2009-09-05
It's difficult to give advise based on the count of reallocation events. A warning about that value raising within a short period of time would be more useful I guess.

---

### Post by SeePU on 2009-09-05
> **MacUntu said:**
> It's difficult to give advise based on the count of reallocation events. A warning about that value raising within a short period of time would be more useful I guess.
That's true.   If there is a measurement or test that updates deterioration or gives info on updates of that failure over time, it would be more useful but to be that accurate, can it be?  

My drive in my Thinkpad was used and bought off a dealer or seller of laptops.   I bought it on impulse but still, I have had it for a little while and perceived no problems or issues in XP (was already partitioned with XP).  In addition, I have read of this warnings before for many people and most of the time, the majority end up figuring it's a warning regarding a minor disk issue.   Or even plain faulty as other disk tests showed no imminent failure.

---

### Post by Paqman on 2009-09-05
> **SeePU said:**
> Let's get this straight, then.  So, Ubuntu allows up to Alpha 5! a utility that falsely claims disk failure or claims disk failing based on a few bad sectors?!?   


There's been quite a large discussion about this. I happen to agree that Palimpsest/gnome-disk-utiliy is behaving ridiculously.

Remember that Ubuntu doesn't develop this app. The developer has responded to this when reported on the Red Hat bug tracker [here]("https://bugzilla.redhat.com/show_bug.cgi?id=500079"). He seems to think there's nothing wrong with the current situation. I'd expect that the Ubuntu devs will then make a decision about what they want to do with this app. In the meantime i'd suggest simply removing it from your list of autostarted apps. It will then stop nagging you.

---

