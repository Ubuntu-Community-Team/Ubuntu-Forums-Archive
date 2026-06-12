---
title: "Alpha 5 now, or Alpha 6 tomorrow?"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hotstovejer on 2009-03-11
Been having the usual issues with Jaunty64 for a while now. Banshee and Rhythmbox pop and crackle while playing sound, but Movie player works just fine with the sound. Compiz is broken, my keyboard all of a sudden becomes unresponsive when I type or play games. All normal stuff when testing a alpha!

I've been reporting my bugs, and I think that maybe I put alpha 3 on the machine. I would throw hardy back on there till it's time for Jaunty, but I don't know if you can put hardy or intrepid on an ext4 partition. 

So, ladies and gentlemen, would it behoove me to throw a6 on tomorrow, or even reinstall with a5?

Thanks!

Jeremy

---

### Post by nyarnon on 2009-03-11
You will not be able to ext4 under hardy or intrepid. The fact that you ask does trigger the advice to strongly consider going back to the stable tree. I'n on 64 and reading this forum and participating gave me all the info needed to run a mostly stable system. 

Running alpha's is not everybodies treat and maybe in this case it's not yours. Just wait a few weeks then Jaunty will enter the stable tree and you can give it another try.

---

### Post by ronacc on 2009-03-11
If you are going to continue with jaunty it would probably be best to wait for A6 since breakages often occur during the transition from one alpha to the next as not everything is updated in sequence . It is good that you have been reporting bugs , that is what we are here for , however you should also have a stable install to fall back on when things get borked as they will during a dev cycle . do not run alphas as your primary system .and as nyarnon says use the forums as a resource to help work through breakages that is what the "search this forum" button is for .

---

### Post by hotstovejer on 2009-03-11
Well, I have a backup system at home, but this is my primary, Got a new machine, and am hardly at it, so I let the updates just floooow. Was just wondering.

Thanks!

Jeremy

---

### Post by Kow on 2009-03-11
The best time to switch over the repos is just after the alpha milestone freeze. If A6 is tagged for tomorrow then the tree should be frozen right now and now would be a good time to switch. The tree/repos may re-open on the day of an alpha release. I always switch my desktop during the Beta milestone freeze.

---

### Post by jfernyhough on 2009-03-11
To try and answer the original question... ;)

Intrepid won't install onto ext4 without kernel 2.6.28 and a version of Ubiquity that accepts ext4 - neither of which the LiveCD have. So, bar a reformat you're stuck with Jaunty (or Arch or whatever).

The current daily iso is going to be little different to Alpha 6 if A6 is out tomorrow as (IIRC) the auto-build process is frozen as the packages are finalised.

Finally, to try and solve the sound issues you might consider adding some PPAs to get pulseaudio 0.9.15-test5 and alsa 1.0.19. I have both of these installed and Jaunty is purring.

> do not run alphas as your primary systemWhere's the fun in that? :D

---

### Post by dBuster on 2009-03-11
What do not run Alphas as your primary?!  Who is smoking what?!  

I have been running Jaunty since Alpha3 and it is running quite stable for me.  Only a few hickups along the way once I was able to get it configured on the new laptop.  Incidentally it was the only distro of Ubuntu that would install without a complete kernel panic on this new laptop...  

I am excited and enjoy Jaunty at the moment and will look forward to the final.

---

### Post by Gina on 2009-03-11
I'm back on Intrepid on my laptop as Jaunty borked at an update a week or two ago and I haven't had time to sort it out.  I'll be re-installing with Alpha 6 (or tomorrow's daily - which should be the same).  I have a separate /home partition.  Jaunty on my AMD64 is running fine and updated every day.  My P4 is my "safe" machine and not touched by development versions.  Jaunty is runnin OK on my AMD K6-2 but I haven't had time to play with that lately.

---

### Post by scaine on 2009-03-11
Pulseaudio has just been reverted to disable the troublesome "glitch-free audio" feature that was (probably) causing everyone's crackling issues.

Compiz has just been upgraded to 0.8 as of Monday night.

No idea what might be causing your keyboard freezes though.

Bottom line - probably worth burning from the latest nightly :
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
... and upgrading to see what happens.

Or wait for Alpha 6 - tomorrow ([https://launchpad.net/ubuntu/jaunty](https://launchpad.net/ubuntu/jaunty)), or even the beta two weeks after that?

How adventurous are you feeling?  ;)

---

### Post by andrewabc on 2009-03-11
Wait for alpha 6 if installing fresh. Installing alpha 5 the day before alpha 6 is released and then updating will probably cause more problems. You'll have to download 200mb of updates with alpha 5. So waste of bandwidth as well (700mb+200mb alpha 5 or just 700mb for alpha6).

---

### Post by nanog on 2009-03-11
Since we've already had the disclaimer about hosing your system.


:evil:


Install 2.6.28:

[https://launchpad.net/~next-kernel/+archive/ppa](https://launchpad.net/~next-kernel/+archive/ppa)

Follow this tutorial:

[http://ubuntuforums.org/showthread.php?t=973701](http://ubuntuforums.org/showthread.php?t=973701)

---

### Post by ronacc on 2009-03-11
> **jfernyhough said:**
> 

Where's the fun in that? :D

I stand by my admonition , while jaunty has been quite stable and dependable for me, just a look through this forum will show that is not the case for everyone . I have had enough true disasters over the years that I wont even put an alpha on a seperate drive on my main box , I built a seperate box that I only use for testing .

---

### Post by SushiR on 2009-03-12
Isn't Alpha 6 due today? Until now I found no images... :(

---

### Post by Technoviking on 2009-03-12
> **SushiR said:**
> Isn't Alpha 6 due today? Until now I found no images... :(

It may be a few hours yet.

---

### Post by SushiR on 2009-03-12
> **Technoviking said:**
> It may be a few hours yet.

Thanks! I know I'm a little bit impatient... ;)

---

### Post by Technoviking on 2009-03-12
> **SushiR said:**
> Thanks! I know I'm a little bit impatient... ;)

I think Alpha 4 and 5 came out about 4-5pm MST (2300 UTCish)

---

### Post by Joeb454 on 2009-03-12
2 hours 40 minutes remaining!!!

j/k

I'm going to download Alpha 6 (whenever it's out) and begin testing :D

---

