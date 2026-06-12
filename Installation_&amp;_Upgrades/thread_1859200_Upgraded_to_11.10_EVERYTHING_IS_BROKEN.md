---
title: "Upgraded to 11.10 EVERYTHING IS BROKEN"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by tippy24 on 2011-10-13
Thanks a lot, Ubuntu! I've been using your 'product' as my main OS at work, and you're poorly planned so0called 'upgrade' broke everything, I can't log in, blank screen, Unity sucks, you forgot somehow to include Gnome?!?!?
How could you make so many mistakes?!?! You completely broke our systems w/o warning us this is Beta!?!? 
What are you going to do to prevent us from losing data? 
DO SOMETHING NOW TO FIX MY SYSTEMS.
You're 11.10 release renders Ubuntu worse than Microsoft Windows. You're no longer an alternative. 
Someone of responsibility PLEASE contact me. This upgrade has put a halt to our ability to do business here. 
FIX IT< AND SOON.
-tippy24

---

### Post by e79 on 2011-10-13
Sorry but I have to respond to this:

> Thanks a lot, Ubuntu! I've been using your 'product' as my main OS at  work, and you're poorly planned so0called 'upgrade' broke everything, I  can't log in, blank screen, Running your business on a non LTS releases, upgrading the first day it comes out, think its wise ?  :confused:

> Unity sucks, you forgot somehow to include Gnome?!?!?This is old news, 11.10 [does not include Gnome2 by default]("http://www.webupd8.org/2011/04/ubuntu-1110-will-not-ship-with-classic.html"), I heard there should be a fallback in the repositories though.

> This upgrade has put a halt to our ability to do business here. Again, your only fault for running your business on a non LTS release and not doing a clean install to make sure everything runs smoothly.

I do sympathize with you though...

On a more serious note, if everything is borken, boot from a liveCD, backup your important data and do a clean install.

---

### Post by Jack Brown on 2011-10-13
reading the OP...  it almost sounds like a joke.

but if it's not, e79 provides cool-headed sound advice

  good reminder for newcomers though

---

### Post by joaquinx on 2011-10-13
So how do we revert to 11.04? Right now I'm trying to find out how to get Skype to run in the background and show an icon on the top bar. Skype just disappears,but is still running. Can't change font except for size.

They change ubuntu because they could and not because it was needed.

---

### Post by CharlesA on 2011-10-13
I know this is a rant.. but - backup before doing anything major with your system.

EDIT: If you need to pull your data off the drive - boot from a livecd and grab the data, as e79 suggested.

---

### Post by keithtoo on 2011-10-13
I, for one, can sympathize with the OP. I have been running some version of Ubuntu since the version 7 series and have been learning - incrementally - the painful lessons of jumping into the newest and greatest releases as soon as they become available.

First and foremost, I learned just how important it is to separate your data from the rest of the system by keeping your data (/home) in it's own partition. This makes it so much easier to revert back to the previously running release without blowing up important user files. I have no idea why this small step is left out of the installer and most installation documentation.

The next thing I learned was to _NEVER_ upgrade right away. Wait, and watch the forums for a month or longer. That way the problems inherent with rushing a release to market before all the bugs are found and dealt with have less of an impact. Many things are typically left until the NEXT iteration - and some things are simply left broken due to the so-called "better way" (an example of this can befound in the link provided above as well). You tend to get a much better perspective as to what works and what doesn't (and sometimes why and how to fix it) by holding off on your upgrades.

If you have mission critical software installed, the OP, or anyone else for that matter, should hold off on upgrades entirely until the next LTS release. Which brings me to the third point - at least after 10.04, newer has not necessarily proven itself to be any better when it comes to Ubuntu releases.

I know this doesn't help the OP out the jam he's currently in - I can't tell you how many times I've had to scrub an entire file system due to an "upgrade" because there was simply no other solution. I would heartily concur with the above responses - use a LiveCD distro that worked for you before, back up what you can, and then do a clean install reverting back to your original setup.

---

### Post by 23dornot23d on 2011-10-13
> 
The next thing I learned was to _NEVER_ upgrade right away. Wait,  and watch the forums for a month or longer. That way the problems  inherent with rushing a release to market before all the bugs are found  and dealt with have less of an impact. Many things are typically left  until the NEXT iteration - and some things are simply left broken due to  the so-called "better way" (an example of this can befound in the link  provided above as well). You tend to get a much better perspective as to  what works and what doesn't (and sometimes why and how to fix it) by  holding off on your upgrades.


Exactly and there are threads here showing this ....... as well as people trying to show
others that there are other ways ...... to check it out .....

The main being to try it out on a liveCD or USB first  ........ 

If failing that put it on a clean 20 Gig Partition ....

---

### Post by joaquinx on 2011-10-13
This is my backup:

tar czvf /media/BACKUP/Ubuntu_Backup/john.tgz /home/john
cp /etc/apt/sources.list /media/BACKUP/Ubuntu_Backup/
dpkg --get-selections > /media/BACKUP/Ubuntu_Backup/list_of_applications.txt

Not only all the files in my directory,but all the sources that I use and a complete list of applications. If I need to reinstall (to be done real soon), I lose nothing but time. And the .iso file of a good OS along with a bootable usb device.

---

### Post by cariboo on 2011-10-13
Using some mod-magic, I can say that this thread, is not serious, and was meant as a joke, and a preview of the 100's of threads yet to come. :)

---

### Post by vuarra on 2011-10-13
> **cariboo907 said:**
> Using some mod-magic, I can say that this thread, is not serious, and was meant as a joke, and a preview of the 100's of threads yet to come. :)

Unfortunately, I was looking to see if there were solutions to my problems (tty only, reverted to Dvorak keyboard).

Glad to see this is a troll/ joke, but :guitar::guitar:

---

### Post by BazookaAce on 2011-10-13
Haha :p I installed the last beta last week, and i've been out of the linux world for a couple of years and maaaan did i notice. Everything broke, everything was a pain in the ***, and i've reinstalled Ubuntu 4 times in one week, and the latest was last night. 

I couldn't do anything besides laugh my *** off. Every single time i install Ubuntu, hours if not days goes to waste. But i like it! I'm up and running now, and i've installed and tweaked Gnome-Shell, got rid of 7 tons of bloatware and i'm feeling good. I managed to install and run Ubuntu without killing the postman twice. Good week, good week.

---

### Post by e79 on 2011-10-13
> **cariboo907 said:**
> Using some mod-magic, I can say that this thread, is not serious, and was meant as a joke, and a preview of the 100's of threads yet to come. :)

DOH..Facepalm'ed :lolflag:

---

### Post by lisati on 2011-10-13
> **BazookaAce said:**
> Haha :p I installed the last beta last week, and i've been out of the linux world for a couple of years and maaaan did i notice. Everything broke, everything was a pain in the ***, and i've reinstalled Ubuntu 4 times in one week, and the latest was last night. 

I couldn't do anything besides laugh my *** off. Every single time i install Ubuntu, hours if not days goes to waste. But i like it! I'm up and running now, and i've installed and tweaked Gnome-Shell, got rid of 7 tons of bloatware and i'm feeling good. I managed to install and run Ubuntu without killing the postman twice. Good week, good week.

Yes, I can imagine that it some things can seem like a pain in the donkey at times. Being a city boy, I don't have a donkey to kick, so I have to make do with other things getting kicked. :D

---

### Post by BoredOutOfMyMind on 2011-10-13
> **cariboo907 said:**
> Using some mod-magic, I can say that this thread, is not serious, and was meant as a joke, and a preview of the 100's of threads yet to come. :)

Trick or Treat?


;)

---

### Post by lisati on 2011-10-13
> **BoredOutOfMyMind said:**
> Trick or Treat?


;)

We're a couple of weeks early, aren't we? :D

---

### Post by ignatj on 2011-10-14
Upgraded on HP dm6-2070 laptop dual boot. I will not come up, no way no how.

---

### Post by BoredOutOfMyMind on 2011-10-14
> **BoredOutOfMyMind said:**
> Trick or Treat?


;)

> **lisati said:**
> We're a couple of weeks early, aren't we? :D

Tongue in cheek snarky comment that included a smiley.  A counter of all the similiar threads after 30 days could prove entertainment. 

:guitar:

(Ubuntu user since 2005)

---

### Post by parthamage on 2011-10-14
Well, it just isn't that funny.  I ran the upgrade, and everything is broken.  Fortunately, I have /home on a different partition than /, so I can download the friggin iso at the speed of a snail, do an install, massage the partitions, and I won't lose my data.  But it's a pain in the butt, and I am using precious time that I could be doing things I really need to be doing, instead of this BS, which would be avoided by the developers putting out a product that actually worked out of the gate.  I don't care if it takes another month to get it right guys, just don't make it available until it works.

---

