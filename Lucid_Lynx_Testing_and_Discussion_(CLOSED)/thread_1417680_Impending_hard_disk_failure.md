---
title: "Impending hard disk failure"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-02-27
I remember this from 9.10 --> [http://ubuntuforums.org/showthread.php?t=1299556](http://ubuntuforums.org/showthread.php?t=1299556)

now, I checked my disk out (again)  with manufacturers utility & it checks out as okay. (WD Drive, have to use the dos based check)

Anyone else seeing this ? Oh, and the 'failure imminent' type icon is dancing all over my notification bar at the top left, pushed my weather report one over to left & obliterated my volume one - it's also dancing over my Network indicator.

[IMG]http://www.phillw.net/img/Screenshot-3.png[/IMG]

Any ideas ?

Regards,

Phill.

---

### Post by howefield on 2010-02-27
I'd be more inclined to believe your disk manufacturers utility. 

Although either way, you'd want a back up of all your important data.

---

### Post by Anduu on 2010-02-27
> **howefield said:**
> I'd be more inclined to believe your disk manufacturers utility. 

Although either way, you'd want a back up of all your important data.

+1

Your manufacturer's utility ***should*** know better.

IIRC when I first upgraded to Karmic I had disk failure notifications popping up all the time.Ended up being a bug which was fixed in short order.

I would definitely backup just in case and file it as a possible bug so it can get looked into.

---

### Post by MacUntu on 2010-02-27
Well, if the WD tool (extended test) finds a bad sector, it gets mapped out and the report says everything's fine. I'd not use it and keep an eye on the S.M.A.R.T. parameters Reallocated_Sector_Ct, Current_Pending_Sector, and Offline_Uncorrectable. If their values increase replace your drive.

---

### Post by gradinaruvasile on 2010-02-27
I booted once an computer with karmic live-usb. The hardware failure imminent icon appeared, i just dismissed it as a fluke. But then that computer was used as a gateway server (CentOS) and in 2 months or so the drive kicked the bucket (there was little i/o / CPU usage on that computer so in theory should have worked years).
So back up, just in case...

---

### Post by phillw on 2010-02-27
Thanks,

Yeah, I do keep backups ... lots of them.

I'll disable it for now, and see if it a resurection of the old bug that flooded the 9.10 area.

WD drives, whilst not known for speed, are pretty well known for life expectancy. It may just being gotten confused as a system crash while I had my win partition mounted ended up with win not being able to boot.

And, as for the creeping image .... I feel like I'm gradually being taken over !!!!
 
[IMG]http://www.phillw.net/img/Screenshot-4.png[/IMG]

It's gotta go !!!!

If one of the mods knows where to report what effect the notification is having, could they post it -- A notification is enough, without it taking over !!!

Phill.

---

### Post by phillw on 2010-02-27
Hmmm.. not good,

9.10 also reports it - going to take all my ISO's from the win area, which is the complaining partition.

But, disk failure apart ... the notification is definatley wrong with 10.04. 

9.10 shows it correctly ..

[IMG]http://www.phillw.net/img/Screenshot-5.png[/IMG]

Which reminds me !!!, why are we on black & white version of the Ubuntu logo on the left ?

Phill.

---

### Post by cariboo on 2010-02-27
I looks like the weather icon needs to be locked to the panel, right-click and make sure lock is checked.

Phillw, could also reduce the width of your images, as they don't fit on the page.

---

### Post by phillw on 2010-02-27
> **cariboo907 said:**
> 

Phillw, could also reduce the width of your images, as they don't fit on the page.

The image is just a photo-shot of my desktop, held on my server. If you'd like me mangle the image with gimp, please let me know what you would like it mangling to. As it is a full horizontal screen shot, IMHO, shrinking it has no beneficial effect.

But, not wishing for an infraction, I will, in future, just leave a link embedded.
::sigh::

> 
        I looks like the weather icon needs to be locked to the panel,  right-click and make sure lock is checked.As to what is going on with the weather notification, and the battery monitor, and the volume applet, and, of course, all the other stuff on the left...

My 10.04 top-bar is similar to my 9.10 one .. i.e., I actually have the ubuntu symbol, Next to it I have "Applications", then "Places", followed by "System" followed by my moz icon, my speaker icon (still an outstanding bug on that), my pidgin icon & last, but in no ways least, my Terminal icon.

So, either ubuntu is wrong in where it places the whole of the left hand side with the logo, 'Applications ... Places ... System' etc ... or maybe you have to consider it the warning icon that is actually breaking the rules ?

Without a video camera, I cannot show you how that hard-disk icon gradually takes over.. suffice to say, it starts off similar to my 9.10 screen shot and ends up like my last 10.04 screen-shot.

If it would be of help, i do have an extra laptop kicking around (win XP) that I can plug a webcam into and record what it does ?

You can see how it eventually "shoves" everything to that far left.

Regards,

Phill.

---

### Post by phillw on 2010-03-03
Okies ...

Hopefully, successfully mangled to fit the forum

[IMG]http://www.phillw.net/img/Screenshot-5.1.png[/IMG]

Well, this is what it does, when given enough time (a couple of hours) .. I think it is a **little** bit more than the weather icon needing fixing.

The process gnome-notification was eating up processor time, killing it does give me my top bar back, but minus the notification area (WiFi ... I think sound had already gone via a different bug)

I am guessing - and it is a complete "in the dark" idea, but I am having the same issue with my Top-Bar being crowded out into oblivion to the left also occurring in Lubuntu, as they do not have the 'failing disk' icon, yet what happens (their bar is on the bottom) is identical.

Any ideas, where I can get some further information to flag this as a bug. 

All my data is backed up, but if I replace this (supposed) faulty drive, I will not be able to re-create the problem with alert icon.

Regards,

Phill.

---

### Post by nanog on 2010-03-03
Modern terabyte sized drives often have bad sectors. I have a drive thats been throwing off palimpset warnings for 7 months with no change in bad sectors. I finally disabled the annoying notification icon in palimpset.

---

