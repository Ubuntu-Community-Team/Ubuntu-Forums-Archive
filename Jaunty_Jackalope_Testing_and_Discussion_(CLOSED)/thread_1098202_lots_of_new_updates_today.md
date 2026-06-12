---
title: "lots of new updates today"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-03-16
a ton of updates today and so far nothing seems broken

---

### Post by Darkshade on 2009-03-16
Yup. I tested pretty much everything I have installed and everything seems to work. Where's the fun in that? :D

Now seriously - the Ubuntu devs are doing awesome job with Jaunty, tbh I didn't expect it to be THAT stable. It's still alpha so it's really early to make such conclusions but if the alpha works this good (actually seems to run even faster after the last update, might be just my imagination though) I wonder how the final release would feel like.

---

### Post by llamakc on 2009-03-16
I grabbed today's updates also. I'm noticing some font issues on several web pages. I'll see if I can't figure out what happened.

---

### Post by jmmL on 2009-03-16
I'm also experiencing the font issues. It's reproducible 100% of the time at [Engadget]("http://www.engadget.com")

Strange things happen if i try to purge fontconfig (with a view to then re-install). Apt-get prompts to remove 915MB worth of packages, most of which have nothing to do with fonts (eg pulseaudio stuff). I'm pretty confused; but I know it's definitely the most recent updates to fontconfig and fontconfig-config that caused the problems.

---

### Post by rudenko_ruslan on 2009-03-17
> **jmmL said:**
> I'm also experiencing the font issues. It's reproducible 100% of the time at [Engadget]("http://www.engadget.com")
That's weird, I didn't notice font corruption at Engadget. But, for example, [on this page]("http://labs.mozilla.com/2009/01/test-pilot-vision/"), "Test Pilot Update","01.20.2009", "Blog", "Scalable", "How It’ll Work", etc looks just awful :(

](*,)

---

### Post by xens on 2009-03-17
Same problem after today updates

---

### Post by philinux on 2009-03-17
Can someone explain what SAUCE is, been looking through update manager details.

---

### Post by Yumi on 2009-03-17
According to Synaptics it is a "SMTP defence software agains spam".

---

### Post by taavikko on 2009-03-17
> **Yumi said:**
> According to Synaptics it is a "SMTP defence software agains spam".

Nope, that's not the thing in question.

SAUCE is something that could be described as,
modification to old recipe...
Food analogy, but tough word to translate :)

---

### Post by philinux on 2009-03-17
> **taavikko said:**
> Nope, that's not the thing in question.

SAUCE is something that could be described as,
modification to old recipe...
Food analogy, but tough word to translate :)

Cheers. I thought it might be derivative of source as in code LOL.

---

### Post by linux6994 on 2009-03-17
Hitting the sauce is a popular past time especially on this St. Patrick's Day!

---

### Post by jmmL on 2009-03-17
Anyone experiencing font issues should check out this: [http://ubuntuforums.org/showpost.php?p=6909837&postcount=7](http://ubuntuforums.org/showpost.php?p=6909837&postcount=7)

It seems to be solving the problem.

---

### Post by andrewabc on 2009-03-17
for me:
90 updates yesterday totalling 60mb
71 updates today totalling 81.4mb
Lots of updates :)

They're probably trying to cram in as many updates as possible before the beta.

---

### Post by lcohen999 on 2009-03-17
I'm sitting on Partial Updates, so I am waiting patiently

---

### Post by SketchyClown on 2009-03-17
Those dang slow repositories. I got informed of a "***partial upgrade***" this morning as well.

I just switched repositories in ***Software Sources*** and got the full upgrade.

And as a bonus a repository that has tons of bandwidth. Very fast.

I see that ***System Monitor*** is reporting **Gnome 2.26.0 **today!

---

### Post by lachild on 2009-03-17
> **rburkartjo said:**
> a ton of updates today and so far nothing seems broken

I use separate X sessions in a dual monitors monitor system.  I've seen a few problems with the gnome-panel on the second monitor through out the day (besides the ones I've already submitted to launchpad).  The first update I did today, that updated gnome packages, caused the launchers on the panel to crash gnome-panel when used on screen :0.1.  Then about an hour later I updated again and it was fixed.  Now they are broken again.... It's like one contributor has this fixed and one doesn't and they are updating the repos at different times.   

Been an interesting ride for me.  :D

---

### Post by andrewabc on 2009-03-17
Wow, yet another 80mb of updates. This time partial upgrade with brasero and something else. Will wait until partial upgrade is gone before updating.

---

### Post by negativ on 2009-03-17
Blah.  I started a dist-upgrade and went away. when I came back, I was met with a black screen and a hard-locked machine.

Powercycled, and now gdm won't load.  I get the background screen and the busy cursor, but no login screen.

I can ctrl-alt-f2 and killall gdm, and then startx.  That gets me to the desktop, but nautilus and gnome-panel don't start.

Normally I don't mind these kinds of things while playing with alpha releases, but in this case I don't know how to tell if it's just bugged packages, or if something got borked due to the lockup.

Oh well.  Fun times.

---

### Post by Nullack on 2009-03-18
> **negativ said:**
> Blah.  I started a dist-upgrade and went away

Thats why dist upgrades generally should be avoided on Alphas.

---

### Post by Kow on 2009-03-18
> **andrewabc said:**
> Wow, yet another 80mb of updates. This time partial upgrade with brasero and something else. Will wait until partial upgrade is gone before updating.

You can remove nautilus-cd-burner if that is the conflict. I believe it is no longer being maintained in jaunty... Brasero is now incorporated into the GNOME package set (note with intrepid it was version 0.8'ish and now it's suddenly 2.26.0).

---

### Post by vishalrao on 2009-03-18
I believe SAUCE is the term used for Ubuntu's custom distro patches to upstream packages...

edit: see the "patching" section here [https://wiki.ubuntu.com/KernelTeam/Specs/JauntyKernelTreeManagement](https://wiki.ubuntu.com/KernelTeam/Specs/JauntyKernelTreeManagement)

> Ubuntu Sauce -- changes to upstream code but which have not yet, or are not likely to be merged

---

### Post by markbuntu on 2009-03-18
I ran update manager, got partial upgrade, 205 pkgs, did that, ran update manager again, check, got 40 more upgrade packages ( fully updated), ran it again, check, got 8 more (fully updated), ran it again, check, no more packages to update, fully updated... something like 253 pkgs total.

---

### Post by andrewabc on 2009-03-18
It is still showing partial upgrade. Not checked is brasero, and another brasero related item.

If I go to synaptic and mark all upgrades, it only has 1 cd burning program to remove, and the rest are upgrades.

This is safe to do partial upgrade? Sounds like it will have to be done if they have got rid of brasero (or renamed it).

---

### Post by markbuntu on 2009-03-18
As long as nothing critical is missing I usually do partial upgrades. Of course, this is not the safest thing to do and I would not reccommend it if you do not have another completely separate (grub, everything) distro you can boot up and are not willing to do a complete reinstall if something does go haywire. It is sort of like playing with matches while standing in a pool of gasoline.

---

### Post by andrewabc on 2009-03-18
140mb to download.
Did synaptic->mark all upgrades. It removed one thing, installed about 8, and upgraded ~100.
Updated fine. Got asked about some gtk box things, I told it to use maintainers version instead of the default selected "keep current version" because in previous versions (hardy/intrepid testing) keeping current broke stuff.

---

### Post by Rainstride on 2009-03-18
theres a whole lot of partial upgrades in my list... its kind of annoying.

---

### Post by Nullack on 2009-03-19
> **Rainstride said:**
> theres a whole lot of partial upgrades in my list... its kind of annoying.

Hit main for the latest instead of a mirror

Besides, Id rather have you annoyed than the devs not pushing updates to the repos in this Alpha :)

---

### Post by andrewabc on 2009-03-19
> **Rainstride said:**
> theres a whole lot of partial upgrades in my list... its kind of annoying.

I had same problem just before updating. It was even listing linux kernels and stuff not checkmarked.

Go to synaptic, mark all upgrades and see what is being removed/installed/upgraded. If only brasero(cd/dvd program) is being removed then you could be safe.

---

### Post by taavikko on 2009-03-19
> **andrewabc said:**
> I had same problem just before updating. It was even listing linux kernels and stuff not checkmarked.

Go to synaptic, mark all upgrades and see what is being removed/installed/upgraded. If only brasero(cd/dvd program) is being removed then you could be safe.

No! brasero is integrated to GNOME, and should not be removed.
nautilus-cd-burner is obsolete as of few days ago.

Use main-server when using dev-versions, and see where it takes you.

---

### Post by andrewabc on 2009-03-19
> **taavikko said:**
> No! brasero is integrated to GNOME, and should not be removed.
nautilus-cd-burner is obsolete as of few days ago.

Use main-server when using dev-versions, and see where it takes you.

Ok. That is what wanted to be removed. It just said cd/dvd cerator.

EDIT:
another 183 updates totalling 60mb of updates.
I must've downloaded 300mb of stuff this week.

---

