---
title: "compiz on 8.04 upgrade"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2008-04-10
Compiz DOES NOT work on Ubuntu 8.04 (as part of a distro upgrade or a new install) on any of my Compaq/HP Laptops. 

Compiz DOES work on Ubuntu 7.10 (as part of a distro upgrade or a new install) on all of my Compaq/HP laptops.

When an attempt to run compiz --replace the following error occurs:

Checking for Xgl:  not present.
Found laptop using ati driver.
aborting and using fallback:  /usr/bin/metacity

I am alerting those that feel that compiz is one of the reasons for using Linux to begin with.  I personally came back to Linux a couple years ago because I liked what Beryl was doing.  Now without it, I'm unhappy.  Moreover I'm unhappy that Canonical doesn't appear to even be addressing the issue.  Not only that I have become dissatisfied with most of their total silence on issues concerning Ubuntu.  But that's another story.

I would like to alert many to the overwhelming number of issues that limit the functionality of certain hardware platforms, namely the laptops.  I can assure you that laptops are not on the way out and to not support old and new (a Presario R3000) is not very old.  It has a wide screen, 2 gigs of ram, a 160gig HDD, wireless, dvd +RW, and a 3.0 ghz P4 processor.  

That's not a low end spec and most of the laptops I see in my shop for repairs are that generation of laptop.  That generation of laptop, the R3000, ZV, DV, etc models were the staple of Compaq/HP sales for a very long time--meaning there are a tremendous number of these out there in the world and all primed for running Linux.

I can't understand why, it seems, that Canonical is ignoring the desire to get these models up and running fully.

It isn't just the video and compiz, it's the sound, and the wireless.  The firmware they give for the broadcom chipset doesn't work on these models and the sound drivers are also faulty to a major fault.  

From install to install I have  different rates of success/failure when dealing with sound on these.  Most of the time, when I fight with it, the sound will only work with the OSS driver, but if I set the system to auto login then try to play some sound, this causes the CPU to go into 100% CPU utilization and no sound.  Even if I terminate the program that was supposed to play the sound the cpu utilization is still 100%.

If I do not set it to auto login then I can only hear sound with the OSS driver.  To top that off, it completely gives fits during the process.  Often I have to switch and tell it, via VLC, to reverse audio or to disable audio and then re-enable it.  Other times it won't play at all.  

Well, I diverge.  I guess I was just trying to point out that these are being neglected and in a major way and that that neglect is spreading from sound to video.  Once working Compiz no longer works and no one at Canonical is efforting any sort of acknowledgment of the issue nor a resolution.

Can someone at Canonical please address these notebook issues and the deteriorating state of the Ubuntu upgrades?

---

### Post by eldragon on 2008-04-10
they will probably address these issues. but you will have to pay for support. like everyone needing professional support did. if you wish to go on the free ride i suggest the following:

a. dont rant, look for solutions ask for help on the forums. remember this is free.

b. dont rant. instead post your hardware specs in detail, what drivers are you using, versions etcetera.

c. dont rant, its pointless.


now to look for solutions.

i only know a bit on how to get compiz running with aiglx and fglrx drivers. mind you, the ati drivers arent as good as they should be. and no, this is not canonical's fault.
you need to

1. install the latest fglrx drivers from [www.ati.com](www.ati.com)
2. add to compiz whitelist the fglrx module, otherwise compiz wont like it.
3. try to set the desktop effects on. if you executed 1 and 2 correctly, compiz will start

this should work under gutsy (this is how i did it). probably hardy will work too.


concerning sound and wireless. i wouldnt know. i dont own a hp/compaq laptop, and to be honest. i wish that day never comes. i guess someone else in the forums (if he hasnt skipped your post like i should have) knows how to get you going.

---

### Post by picopir8 on 2008-04-10
Also, if you are going to run a BETA version then you should be willing to accept a few bugs.

---

### Post by jimbo99 on 2008-04-10
I've looked for solutions.  So my rant isn't from me just encountering these issues.

Secondly, they haven't addressed these issues.  The sound issues are long term issues.  The wireless is a long term issue.  Now we have issues with video cropping up.

My point in all this is that these are not so old as to be abandoned units and they are prime machines for Linux.

Also, they do not help you much on the paid support, in fact, from my experience with them their paid support is worse than the free community, which by the way, only is good when someone has the exact knowledge you are looking for.

The squeaky wheel gets  the grease.  Often a developer is so focused on their own point of view it takes someone yelling at them to get them to listen.  This is true of all things in life.  If you have children you know that every so often you have to  yell in order to get their attention.

My post is more a warning that Ubuntu's upgrade process is in a state of decline, not in a state of increase.  Entropy is settling in on their process.  They do a great job of hiding their voice from the community in favor of payment, but really, that payment is a whole lot for only a small amount of help.

It probably is inappropriate of you to lecture.  It can be viewed as censorship.  We want people voicing their desire and pain because without that freedom then no one will ever  hear...it becomes a bureaucracy instead of a community.

In the case of 8.04 I think it is a big backwards step, and I'm just telling people that this is the case.  It isn't just the sound, the video, the wireless (or even them combined), it is the error after error, the broken facilities that break an install and can't be undone without a huge amount of knowledge or a complete reinstall.

But most of all, I'm trying to keep this on focus about we the human beings of the world.  This is for the human being.  We leave the geeky to the other distros.  All things Ubuntu should focus on us, the human being, and priority should be given to those things that enable us as human beings.  If I were in charge of Canonicial's prioritization, I'd be asking of every project (On X scale how does this fix address the human being need)?  If it is a low answer indicating a machine geeky issue, then it would go on the back burner).

I can see it falling apart.  They have far too much focus these days on the geek and it has become obvious that there's far less focus on us as human beings.

I don't need a reply to this.  I don't need you to further attempt to lecture.

Ubuntu is going into a state of decline and the focus is shifting away to something more technical rather than more human.

---

### Post by kcox5342 on 2008-04-10
If you work repairing laptops, perhaps you could get one of these HPs cheap and donate it to a developer?  I imagine you'd see a quicker and more enthusiastic response.

---

