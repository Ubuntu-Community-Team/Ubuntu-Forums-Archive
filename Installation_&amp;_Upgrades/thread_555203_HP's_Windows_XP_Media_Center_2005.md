---
title: "HP's Windows XP Media Center 2005"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Sonno on 2007-09-19
I have an AMD 64 x2 dual core 5200+ processor, 2 gb RAM, 240gb hdd, and I don't think anything else matters for this problem.

I'm fairly certain HP has done something retarded with it's partitioning method, but I'm clueless as to how to resolve this. I want to resize (because the recovery drives from hp never work) my /dev/hda1 partition (which is windows xp media center 2005), but nothing works. Any tips? I've tried qparted, fdisk, and some other stuff, but it all either can't read the partition or tells me it's impossible. At this point I almost don't care about extreme stability for windows. I'm nearly willing to force a resize (if that's possible) and let the computer figure out what to do with less hdd space.

---

### Post by rsambuca on 2007-09-19
Are you sure that hda1 is the actual XP partition and not the recovery partition?  A lot of the HP's I have seen have a very tiny multimedia key partition, as well as a recovery, and then the main XP partition.

---

### Post by Pumalite on 2007-09-19
Gefrag XP several times, erase all temp files, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (the stand alone, burn to CD, boot from program), right click on XP partition and 'resize'

---

### Post by Sonno on 2007-09-19
Well fdisk couldn't read the harddrive at all, and I used mostly graphical interface bootdiscs that don't actually classify it as "/dev/hda1", but I know it's the main drive. There's 224.4 GB on my C: (windows), and 8.475gb on the recovery drive, and around 7 megs free on the hdd.

---

### Post by Pumalite on 2007-09-19
If Gparted doesn't work, try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
It has a partitioner too.

---

### Post by Sonno on 2007-09-19
[http://s243.photobucket.com/albums/ff64/ilsonno/?action=view&current=hdd.jpg](http://s243.photobucket.com/albums/ff64/ilsonno/?action=view&current=hdd.jpg) Is that not defragged well enough? I figure I could shave at least a good 20 gigs off the back of that, right? (I defragged it before I started trying to resize it.)

---

### Post by Pumalite on 2007-09-19
If you defrag several times, you'll see the difference.

---

### Post by Sonno on 2007-09-19
I wasn't denying you knew what you were talking about at all, I just would have thought that with all that free space at the back of it, couldn't I steal a good 20-30 gigs easily? I mean, I could easily be wrong, but I just wondered if that might neutralize hopes of fixing it by multiple defrags before I go through that for no reason. *Edit* Trying the systemrescue again.

---

### Post by Pumalite on 2007-09-19
I think Windows should have the least space possible in anyone's computer. None at all is even better.

---

### Post by Sonno on 2007-09-19
Well, I first tried the systemrescue disc, then realized that I didn't know the commands to resize the partition, so I tried to gparted (which I also already had downloaded and burned to disc), and it's doing the same thing. I try to drag the arrow and it won't move, I can add to the partition but I can't take away from it more than what I started with. Is there any way to override the (safety?) feature that keeps me from making it smaller than what it is? *Edit* I also found out it's /dev/sda1 not /dev/hda1, if that helps at all. Probably not, but just in case. And sda1 is the C:, sda2 is the D: (backup drive that doesn't actually restore anything).

---

### Post by Pumalite on 2007-09-19
You must have a 'recovery partition' somewhere. Otherwise is no problem; in Gparted you right click XP partition and on the menu you get, you choose 'resize partition'.

---

### Post by Sonno on 2007-09-19
So if I delete the D: then it should work?

---

### Post by rsambuca on 2007-09-19
I'm guessing it is that little hidden partition that has the files for the special HP media keys.

---

### Post by Sonno on 2007-09-19
Any advise about that hidden drive would be gangster, my friend. I've never heard of such a thing.

---

### Post by Pumalite on 2007-09-19
If what we are talking here is an HP laptop you can count on having a 'recovery partition', that way they get away with selling it to you without an Installation CD

---

### Post by joe.turion64x2 on 2007-09-19
Aren't you able to burn a recovery disc? Are you relying only in that recovery partition?

If I were in your position and had the option of creating recovery media, I would definitely create them and format the hard drive. It is most likely that reinstalling from the media would help you get rid of that annoying and retarded partitioning you refer to.

Joe.

---

### Post by rsambuca on 2007-09-19
I am sorry, but I don't think we are getting all of the information here.  You said you tried using gParted?  If so, could you please tell us exactly what the disk structure is that is displayed by gParted?  

After we have all of that information, we will be better able to assist you.

---

### Post by Pumalite on 2007-09-19
It's hard to get rid of it if you intend to keep Windows because this partition is usually at the beginning of the drive.

---

### Post by Sonno on 2007-09-20
Well, I fell asleep. Sorry :)
And I've already said what gParted showed. Now I've deleted the /dev/sda2 partition and I still can't resize the /dev/sda1. The sda2 *was* the recovery drive, and the only other "drives" there are are removable ones that are built into the comp. As for the recovery disc for windows, HP has **** recovery discs. All the ones I've ever used (and I've used about three or four on this computer) have reformated my entire harddrive and then left them without replacing windows. I don't mean a single partition either, it deletes *everything*. I had the intentions of having ubuntu as my primary boot and was going to reinstall windows with the recovery disc (the first week I got the computer), but after running the recovery disc, I just had a messed up ntfs partition.

---

### Post by rsambuca on 2007-09-20
Please use the gparted disc and tell us EXACTLY what is says you have for partitions and their sizes.  You still haven't done so.

---

### Post by joe.turion64x2 on 2007-09-20
> **rsambuca said:**
> Please use the gparted disc and tell us EXACTLY what is says you have for partitions and their sizes.  You still haven't done so.
Yes, you could send us at least a Gparted's screenshot.

---

### Post by Pumalite on 2007-09-20
Hey rsambuca; doesn't it remind you of another client we had recently?

---

### Post by rsambuca on 2007-09-20
> **Pumalite said:**
> Hey rsambuca; doesn't it remind you of another client we had recently?

Too many, in fact!

Still patiently waiting...

:popcorn:

---

### Post by Pumalite on 2007-09-20
These guys come here, want help and we are more than willing to help them; we ask a few simple questions about their machines: and they refuse to answer?????

---

### Post by rsambuca on 2007-09-20
:popcorn:

---

### Post by Pumalite on 2007-09-20
:guitar:

---

### Post by Sonno on 2007-09-20
I have a long school day, for personal reasons that are completely irrelevant. I do apologize for taking so long, though. What information are you looking for? gParted doesn't give me any errors or anything, it just won't let me slide the arrow on the right of the partition like it should, and if I change the number of sectors?(I think it's sectors, or cylinders, or mb or something) it goes back to what it was before I changed it when I click off.

---

### Post by rsambuca on 2007-09-20
Would you mind re-reading post #20 and answering it?

---

### Post by Sonno on 2007-09-20
How can I get a screen shot from a boot disc? That seems the simplest way to get what you want, right? I still don't know what you're looking for, or I'd just tell you, but if a screenshot'll do, tell me how and I'll do it.

Quote:
Originally Posted by Sonno  
Well fdisk couldn't read the harddrive at all, and I used mostly graphical interface bootdiscs that don't actually classify it as "/dev/hda1", but I know it's the main drive. There's 224.4 GB on my C: (windows), and 8.475gb on the recovery drive, and around 7 megs free on the hdd. 

I can't imagine that this is what you're looking for, but if it is, here it is again. The only thing I can add to that is that C: is /dev/sda1 and the recovery drive is /dev/sda2. Does that answer it?

---

### Post by Sonno on 2007-09-20
Edit*

---

### Post by Sonno on 2007-09-21
This problem is still unresolved, if anyone is willing to help me.

---

### Post by rsambuca on 2007-09-21
Hey Sonno.  OK, why don't you boot up the gParted liveCD, and then write down what it shows for partitions, filesystems, sizes, used, unused, flags, etc.  We'll go from there.

---

### Post by Pumalite on 2007-09-21
'I have an AMD 64 x2 dual core 5200+ processor, 2 gb RAM, 240gb hdd, and I don't think anything else matters for this problem.'

Everything matters. We need to know about your 'recovery partition'. Without Gparted and a screenshot we will never know. We can speculate that's in the front of your drive and that is the culprit in this situation, but that's it without what we asked you. At this point I can advise you this: get Gparted, wipe your hard drive clean, install XP first in a hard drive formated ntfs, boot from Gparted again, click on XP partition, in the menu choose 'resize partition' and then install Ubuntu. You can get a cheap OEM XP CD for ten bucks and use the serial # stamped in your machine.

---

### Post by Sonno on 2007-09-21
> **Pumalite said:**
> get Gparted, wipe your hard drive clean, install XP first in a hard drive formated ntfs, boot from Gparted again, click on XP partition, in the menu choose 'resize partition' and then install Ubuntu. You can get a cheap OEM XP CD for ten bucks and use the serial # stamped in your machine.

I believe that's my best option as well, thanks. I have tried this with the hp given discs, but they always reformat my hdd before it lets xp install.

---

### Post by Pumalite on 2007-09-21
You are welcome.

---

### Post by rsambuca on 2007-09-21
](*,)

---

