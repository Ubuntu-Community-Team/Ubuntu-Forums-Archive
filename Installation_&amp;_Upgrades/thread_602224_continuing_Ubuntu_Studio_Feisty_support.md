---
title: "continuing Ubuntu Studio Feisty support?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by coverup on 2007-11-04
Hello all,

I upgraded to Ubuntu Studio Gutsy last week and didn't really like it, some important things like input monitoring were not working and one of my audio interfaces was experiencing triple the latency that jack was set to.  Things were freezing too much and rather than track down a bunch of bugs for my less-than-current setup and ask for a lot of help, I just wanted to go back to Feisty and keep making work..

In light of the repos at archive.ubuntustudio.org being taken down, I am at a bit of a loss as for what those of us who want to continue working with Feisty should do.  The meta-packages ubuntustudio-audio + etc that are in the regular Feisty Universe repos are unfortunately sub-par, ardour is back to 0.99 instead of 2, I can't run JACK in realtime mode at all (is this the lowlatency kernel in Feisty Universe or JACK's fault?)   I'm just concerned because the meta-packages + lowlatency kernel in Feisty Universe don't seem to be a suitable replacement for the recently removed "real" repos.

I understand that it was pretty expensive to keep those up and I am very grateful for all the work that has been put into Studio.  Most of you have probably moved on to Gutsy, but dropping the version immediately preceding it doesn't seem like a good idea to me.  Is there anything to be done here?  I need to do something cd or package based because I don't have a dvd drive/burner.

Thanks in advance!  Any information would be much appreciated.

---

### Post by coverup on 2007-11-04
I fixed my problem with jack, if anyone else is using a Zoom H2 you probably want to run it at 48 kHz instead of 44.1 :KS  Somehow this made jack report latency correctly.. so I don't think there's anything wrong with the lowlatency kernel, I just needed to run a command posted in another thread to get it to run realtime.

Still wondering about the meta-packages though.

---

### Post by Stochastic on 2007-11-04
I would ask this question in the IRC channel, there tends to be more devs and admins in there than on these forums.

---

### Post by Fmac on 2007-12-07
I'm wondering the same. When I try to run the Gutsy rt kernel (or, when it was accessible, the Feisty realtime kernel with a Gutsy installation), I get a wide selection of freezes, video glitches, and error messages which make it generally unusable. I presume all stemming from idiosyncrasies of my cheap old notebook computer.

I would have liked to have gone back to Feisty, which worked half-decently on it, if that were still an option.

---

### Post by streamsanddragonflies on 2007-12-07
Hi! I'm sorry to add a question rather than answer to the thread but as a newbie to linux and U. Studio, I had been concerned about latency when recording and how well my m-audio audiophile 2496 soundcard would work with jack.  I have to re-install Ubuntu Studio anyways and had delays (my bios won't boot a DVD with my too modern DVD multi drive).  I am now wondering whether I should start with fiesty or gutsy?  From the issues brought up in this thread I am unsure.  I will search this "IRC channel" I assume it is a forum also....:)

---

### Post by tekniche on 2007-12-10
> **coverup said:**
> Hello all,

I upgraded to Ubuntu Studio Gutsy last week and didn't really like it, some important things like input monitoring were not working and one of my audio interfaces was experiencing triple the latency that jack was set to.  Things were freezing too much and rather than track down a bunch of bugs for my less-than-current setup and ask for a lot of help, I just wanted to go back to Feisty and keep making work..

In light of the repos at archive.ubuntustudio.org being taken down, I am at a bit of a loss as for what those of us who want to continue working with Feisty should do.  The meta-packages ubuntustudio-audio + etc that are in the regular Feisty Universe repos are unfortunately sub-par, ardour is back to 0.99 instead of 2, I can't run JACK in realtime mode at all (is this the lowlatency kernel in Feisty Universe or JACK's fault?)   I'm just concerned because the meta-packages + lowlatency kernel in Feisty Universe don't seem to be a suitable replacement for the recently removed "real" repos.

I understand that it was pretty expensive to keep those up and I am very grateful for all the work that has been put into Studio.  Most of you have probably moved on to Gutsy, but dropping the version immediately preceding it doesn't seem like a good idea to me.  Is there anything to be done here?  I need to do something cd or package based because I don't have a dvd drive/burner.

Thanks in advance!  Any information would be much appreciated.

Is there anywhere that one running 7.04 could go to upgrade to gusty? I am at a loss for what to do because the repo has been taken down and I am getting all kinds of errors trying to upgrade/update. Can anyone help? Thanks.

---

### Post by Stochastic on 2007-12-10
> **tekniche said:**
> Is there anywhere that one running 7.04 could go to upgrade to gusty? I am at a loss for what to do because the repo has been taken down and I am getting all kinds of errors trying to upgrade/update. Can anyone help? Thanks.

Here's a tutorial on how to upgrade [http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html)

---

### Post by tekniche on 2007-12-10
Hey thanks a lot stochastic. I appreciate the quick response. Unfourtunatley I have another issue now. What I did with the repo problem was removed it from the software sources list so that I wasnt looking in that repo for files. So that fixed that issue but now I have another issue with dpkg not functioning properly with my updates. When trying to update through the update manager I am getting dpkg returned an error code (2). Not to sure how to proceed but I am pounding the forums and google for answers. Thanks again.

---

### Post by Stochastic on 2007-12-10
One way to go about fixing things, is to manually edit your /etc/apt/sources.list and change all your feisty to gutsy.  Save, then do "sudo apt-get update" "sudo apt-get dist-upgrade"

---

