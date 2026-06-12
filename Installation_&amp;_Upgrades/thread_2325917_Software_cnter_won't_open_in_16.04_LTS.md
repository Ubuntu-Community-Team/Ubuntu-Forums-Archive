---
title: "Software cnter won't open in 16.04 LTS"
date: 2016-05-26
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2016-05-26
I upgraded to 16.04 LTS several weeks ago to solve some problems I was ignoring in 15.10. The problems didn't go away and now I have a few more. First the software center won't open. Second I can't open crash reports.

Larry

---

### Post by RobGoss on 2016-05-26
Hello and welcome, did you recently upgrade or is this a fresh installation?

I would recommend doing a fresh installation of 16.04 because it seems there are a few issues when using the upgrade method. I also experience a few problems when I try to upgrade from 1404 to 1604

I did a fresh install and never looked back. Hope this helps

---

### Post by l6griffin on 2016-05-30
I had a good experience with 13.04 to .10 solved a lot of problems I had at the time. Backed Home and re-installed 16.04, most of the problems went away. I still have an occasional screen dimming, I'll chase it sooner or later.

Thanks Rob,

Larry

oops marked this solved, before I tried the software center again, only to find out that if I rebooted after install it works.

---

### Post by RobGoss on 2016-05-30
So is everything running OK now?

---

### Post by l6griffin on 2016-05-30
No everything is not OK it is closer to a can of worms than an OS. I started this time with backing up my directory in Home. I downloaded a copy 16.04 LTS and burned an installation disk. I installed .04 from the disk. The first problem I came to was there was no option to erase the disk it seemed to be implied. Judging from your advice I think you would agree that installing on a clean disk is the best way to get "fool proof" installation. I've got thirty years experience working with personal computers and have found that to be best method. After the install there was a definite improvement in performance. I copied my directory back into the Home directory using 'gksu nautilus' from the command line. This is were another anomaly presented itself. During copying when ever another file was found of the same name there are three options given 'cancel, skip, and merge'. How do you merge files, cancel, skip, replace, concatenate, I understand. I ended up merging the file who knows what this did. 

After the backup was complete I rebooted. All the files I expected to be there were. I needed to install a photo editor and software center would still not come up it would hang loading. Thinking I would just over write the existing software I googled installing the software center from the command line. I even found instructions to do it in 16.04. I now have two copies of ubuntu software in the launcher one is 'ubuntu software' and the other is 'ubuntu software center', and niether one tells you that showfoto is for kubuntu not ubuntu with gnome. BSD anyone.

---

### Post by Omar_Jair on 2016-05-30
Ubuntu Software center is a separate app, ubuntu software its a small software manager you can use to install common apps,i personally use software center, if you don't find a software center for your Desktop Environment search in ubuntu software, there you will find software center for lubuntu, mate, etc.

---

### Post by l6griffin on 2016-05-31
That's all well and good, except why name them so closely. 8-( It also doesn't explain why neither program warned that Showfoto was for Kubuntu not Ubuntu, or that showfoto on install didn't recognise it was being installed on the wrong OS.

---

### Post by Omar_Jair on 2016-06-11
If im not wrong shotwell is the photo one for Ubuntu (unity Desktop)

---

### Post by vasa1 on 2016-06-11
> **l6griffin said:**
> No everything is not OK it is closer to a can of worms than an OS. ... I've got thirty years experience working with personal computers ... I copied my directory back into the Home directory using 'gksu nautilus' from the command line. ... BSD anyone.
You can mark your thread [UNSOLVED]. See how to here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thirty years with PCs isn't bad.

Why did you need to use gksu?

What about BSD :confused:

---

### Post by l6griffin on 2016-06-11
Shotwell is installed with Ubuntu, but is primarily a organizer, viewer, Unfortunately google no longer maintains a version of Picasa for linux. Photo editors without updates don't keep up with current camera raw files. I've installed Fotoox for the time being it recognizes that Raw Therapee is installed and I with RT some in the past.

---

### Post by l6griffin on 2016-06-11
vasa1, I originally started with a Osborne One running CP/M in the early 80s. I had been hooked on computer a decade earlier and had watched the computer hobbyist in the Silicon Valley develop. 

Running gksu nautilus from the command line puts nautilus in graphics mode with root privileges. I'm not a mickeysoft fan but there is something to be said for a GUI.

BSD was frustration talking, another user who evidently runs it came to mind. At 70 years old I don't need to learn another OS.

If anything more needs to be done with this thread I need to look at my first post, double check the install, and file bug reports. I did check the readme on 16.04 and didn't see anything about merge files. If I'm correct I'll file some bug reports to do that I need to a laptop repaired.

---

