---
title: "General Installation Failures 12.04"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by henry cow on 2012-07-03
I have attempted to install 12.04 (usually Ubuntu x64, but also x32 and Xubuntu x32) on at least 4-5 different computers. 

I have downloaded several different .iso images and burned them at different speeds and using different software.

The computers are decent desktops, some fairly "hot" (including AMD Athlon 64x2) down to older Sempron-level processors. I have made multiple attempts on every machine, even changing out freshly formatted hard disks.

The dozens of install attempts have succeeded in only 2 cases. Otherwise, they get about halfway through and hang, with a dead-end error message such as "encountered an error and cannot continue"

What the heck is going on? These are somewhat obsolescent machines, I grant you that, but they are generally strong and capable, and easily meet the hardware requirements.

One box also installed Windows 7 x64, another took XP x64, and one successfully installed XP x32, all on entirely separate hard drives from the ones I was using for Ubuntu. To avoid conflict and ensure success, I sometimes unhooked the Windows hard drive altogether before starting the Ubuntu install. I have several 40GB-80GB hard drives laying around that I was dedicating to Ubuntu.

I don't think it is a format/partition issue because they were all freshly partitioned and formatted, and I agreed to let the installation do its own format if it wanted to.

Help!

---

### Post by msammels on 2012-07-03
You say you are burning to a physical disk? Is the ISO checksum OK? Also, what speed do you burn them at? I find burning them at a lower speed generally provides better results.

---

### Post by jmfal on 2012-07-03
Are you allowing Ubuntu to update during the installation?

Sometimes that can cause it to hangup.

Unplugging the other hdd's is  not a problem, that's what I do,  you can always go back and update grub.

I use K3B to burn a iso image, just open it select other ,close the window asking which app to use, find the iso file, double click on it , and insert a disc when the second window pops up, start.........

---

### Post by msammels on 2012-07-03
Also, if you are updating during the install, sometimes loosing connection to the internet for whatever reason can cause it to fail, if the connection is not restored fast enough and the buffer empties.

---

### Post by henry cow on 2012-07-04
Thanks for the responses, but they do not really help.

My most recent attempts have been with internet connections and Windows hard drives unplugged.

The CDRs have been burned at slow speeds mostly using Windows software.

Since I am getting similar problems across multiple systems using multiple .iso downloads and multiple CDR burns, there has to be something else.

And the fact that I have installed Windows without problems on some of these same machines indicates to me that there should not be hardware problems, unless it was the target hard drive, and I have even swapped those out.

And, lastly, since the installations did succeed in 2 cases, it indicates that the .iso and CDR process is not flawed either.

The only logical answer I can think of is that many of these old hard drives are failing, but they have been in use, recently, without problems, and have been freshly formatted.

I have noticed an inordinate number of installation issues for 12.04 in recent weeks and months. Is it just a much more finicky OS than earlier distros?

---

### Post by henry cow on 2012-07-06
To keep anybody who has read this thread for curiosity, here is the workaround that has succeeded:

I found an .iso online for Lucid Lynx 10.04 x32, downloaded it and burned it to a CDR.

This installed with no problems on all 3 hard drives that I tried.

Then I went through the arduous procedure of "upgrading" to 12.04 LTS online, which took well over 2 hours each time ("why?" I have to ask) on a decent ethernet LAN.

In spite of the slowness of the proceedings, it all eventually worked properly.

So I am left with my original perplexity: like thousands or millions of other people, I would love to move away from Microsoft Windows, if there was a viable alternative. Don't say Apple, they are like Microsoft but just as bad, if not far worse.

In theory, Ubuntu should be great, but in practice, everything is excruciatingly painful and difficult to get up and running. Once up, it is pretty sweet.

Ubuntu let its golden opportunity slip away in not seizing the market ASAP after MS made the Vista disaster, and it is not likely to get another chance.

The jury is still out on Unity, I don't hate it as much as I used to, but it still irritates me.

So, if you are trying to install 12.04 on older gear, my recommendation is to do it from 10.04 rather than clean.

Boo-hoo. What a kludge.

---

### Post by Frsutrato on 2012-07-06
> **henry cow said:**
> Don't say Apple, they are like Microsoft but just as bad, if not far worse.

I'd love to agree with you but when did you last hear of a Mac owner going to any more lengths to get their computer to work, other than taking the plug to the AC socket...  Sad fact.  I, too have spent many precious hours fiddling with this Linux nonsense and am no further on after nearly having a nervous breakdown.  I must be insane.  I'm certainly embarrassed.

---

### Post by ronnysingh on 2012-07-06
I've never faced any problem either in installing Ubuntu or in upgrading existing version of Ubuntu. Installation guide may be helpful :

[https://wiki.ubuntu.com/Installation/](https://wiki.ubuntu.com/Installation/)

---

### Post by henry cow on 2012-07-06
2 comments that demonstrate the problems.

With Windows, most things "just work" except when they don't. If they don't, then throwing a small to medium amount of time or money at the problem usually fixes it.

With Apple, things almost always "work" as long as you pay Apple's price (2x-5x the going rate for everybody else) and do everything by Apple's very strict rules on their appliance-like hardware. I was ready to switch over to Apple a few years ago until I found out that you can't just buy an Apple motherboard and attach your desired components to it.

I totally understand that without an underlying revenue source there is no incentive to make ANYTHING work, it is just the desires of a group of people who are operating well outside of the mainstream.

Here, the universal answer seems to be: just plug it in and turn it on, it will work. But it doesn't, very often.

Read my original posts to understand my frustration. Somebody telling me that "it worked for them" only rubs salt into my wounds.

A couple of years ago I bought a very ordinary mainstream laptop and spent dozens of hours trying to get it to connect wirelessly. Eventually I got it working, but only after chasing MANY dead ends.

I desperately want Ubuntu, or some form of Linux, to be "Ready for Prime Time", but that continues to seem like 5 years in the future, just like it did 5 years ago.

---

### Post by Frsutrato on 2012-07-06
> **henry cow said:**
> 
Read my original posts to understand my frustration. Somebody telling me that it worked for them only rubs salt into my wounds.

I have and I'm completely with you on this.  Someone suggested I use CDBurnerXP, so I went to download it.  Simple?  Not half... when I went to run the installation, it said "You need netframe something".  So I went searching for whatever that is.  When I went to install THAT, it said I need something called "Windows imaging component".  Got there, found a whole bunch of files, on a page that tells you to "Download the one you want".  How can I POSSIBLY KNOW what I want, when I don't even KNOW what it is???  Now my head is just boiling with rage.

This is not a pleasant computing experience.  It feels like computer hell.  When people say "Oh, I had no problems with it" it rubs salt into my wounds, too.

If I had a penny for each hour I've spent f**ing about with this madness, I could have BOUGHT the Apple Mac company!!!

I've never liked Windows and Macs are definitely expensive.  Obviously, one gets what one pays for.

So I'm stuck with this.

And to add insult to injury,  I was so frustrated, I even managed to mis-type my own intended username when registering to this forum.  How embarrassing.

---

### Post by henry cow on 2012-07-06
For whatever it's worth, I have used CDBurnerXP <in Windows> for years and love it. It replaced Roxio with a few shortcomings but it is solid and reliable. I took it to Windows 7 with me a couple of months ago and am still happy.

I did not even know that it existed in Linux. I have not burned to many discs in Ubuntu, but would be interested to find a clean straightforward program for doing that important task.

Speed is unimportant but accuracy and reliability are.

---

