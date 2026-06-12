---
title: "Overloaded CPU on GNOME login?"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-08-27
I just ran updates, so I'm running a fully updated Karmic, and now whenever I log in the CPU is fully loaded, and my RAM gets filled to capacity. I haven't stayed logged in enough to fill up the swapspace, but it is higher than it has ever been.
The CPU is too full to be able to run even Firefox and even the desktop icons (I try to select multiple icons and is can't even do that). I think that Ubuntu might be turning into Windows XP by loading programs after you are logged in.

---

### Post by tekstr1der on 2009-08-27
For me, that would be sreadahead hogging the CPU for about 15-20 seconds following boot. This recently replaced readahead and certainly has some issues ATM. Also you should see about 5-10 seconds tacked on to your boot time as a result of this change.

---

### Post by camper365 on 2009-08-27
I don't remember how long the CPU was full, but I do remember that there was a huge surge in the amount of RAM used. It went from a little more than 200 MB to over 1 GB in about 10 seconds after login

---

### Post by andresmh on 2009-08-27
> **tekstr1der said:**
> For me, that would be sreadahead hogging the CPU for about 15-20 seconds following boot. This recently replaced readahead and certainly has some issues ATM. Also you should see about 5-10 seconds tacked on to your boot time as a result of this change.

Yes! I have the same problem with sreadahead. I also saw Dropbox eating a lot of CPU at login time but I think it's all caused by sreadahead.

---

### Post by chronosMark on 2009-08-27
I've noticed this issue appeared to be something to do with ubuntuone well at least in my case.

---

### Post by yellerKat on 2009-08-28
> **chronosMark said:**
> I've noticed this issue appeared to be something to do with ubuntuone well at least in my case.

I've put up a thread in the ubuntuone forum - [LINK]("http://ubuntuforums.org/showthread.php?t=1251064").

I've had ubuntuone-syncdaemon spawning multiple instances. Only a rapid ctrl-alt-f1 and removal of ubuntuone worked.

No reply from anyone yet, though. :confused:

---

### Post by camper365 on 2009-08-28
After further diagnosis, I have figured out that it is Ubuntu One that is overloading my processor. What is happening is that ubuntuone-syncdaemon has multiple instances and it is taking up the entire CPU. I have tried running ```
pkill ubuntuone-syncdaemon
``` but that doesn't work. However, running ```
pkill ubuntuone
``` works fine.
I will check Launchpad for a bug report and then file a bug report.

---

### Post by yelo3 on 2009-08-28
I also have this problem (or a similar problem).
In gnome every process eats up lots of CPU (it's not related to a particular process, all of them causes this issue).
For instance, when navigating in firefox 50% of the cpu is used,
when updating the apt index 100% cpu is used
and so on...

---

### Post by frustphil on 2009-08-28
experienced this too..

---

### Post by andrewfn on 2009-08-28
Same here. I have to kill ubuntuone in order to do anything.

---

### Post by camper365 on 2009-08-28
I ran updates earlier today, and the problem is fixed.

> **yelo3 said:**
> I also have this problem (or a similar problem).
In gnome every process eats up lots of CPU (it's not related to a particular process, all of them causes this issue).
For instance, when navigating in firefox 50% of the cpu is used,
when updating the apt index 100% cpu is used
and so on...
I don't really have that problem.
I have a 1.86 GHz single core processor.

---

### Post by froggyswamp on 2009-08-28
Well, I've just updated from main server and the issue with sreadahead is still there.. Using Karmic x64.
It starts a few seconds after I login (auto login) and lasts for like a minute.

---

### Post by camper365 on 2009-08-29
I don't really have a problem with sreadhead at all.
I don't know if it's a configuration on my system or something else, but I am running 32-bit, not 64 bit

---

### Post by utnubuuser on 2009-08-29
Are apps not supposed to be using all the CPU cycles they can get?  My oldish thinkpad runs on an "on-demand" basis, and the cpu regularly goes to "full-on", but only on a temporary basis, while FF is fetching/drawing a new page, (1-3 seconds).  I've got 1gig of ram, and it's rarely over 750megs, even with FF, Gimp, Nautilus, Filezilla, and gEdit all running at the same time.
The only app that really draws full use of the CPU is Synaptic/apt.  And that's just a little old pentium M 1.7ghz, (2004).
Is KDE easier on the resources?
I'm under the impression that Linux is a "smart" OS and uses as much of the available resources as possible.
Normally, my processor runs at the meek rate of 600mhz, and Ubuntu's Gnome is still quite snappy.

---

### Post by andresmh on 2009-09-08
I am also seeing sreadahead using 100% of the CPU for the first 2 or 3 minutes after logging into GNOME. Is this the expected behavior then? I have an SSD.

---

