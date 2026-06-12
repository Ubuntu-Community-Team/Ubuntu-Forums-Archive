---
title: "Another 9.04-&gt;9.10 upgrade sob story (64 bit)"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2009-12-21
Yesterday I tried a Kubuntu 9.04->9.10 upgrade.  Today I downloaded a Kubuntu 9.10 install CD, because yet again, the upgrade broke something major.

Two hours of downloading a bit over 1 GB of packages was not the problem.  The problem was that after the upgrade, sound was simply broken.  The only way I could get the system to utter a peep was by playing back a DVD image.  I initially thought it was the old "No sound in Flash videos" bug reborn, because that was one of the first things I tested.  I spent about half an hour trying various fixed for that, reinstalling Flash etc.  I then realized that I wasn't getting any sound in any app, apart from the noted exception with Kaffeine playing DVDs.

I also tried installing a newer version of ALSA, but I gave up when it wanted to do a 400+ MB download.  Ridiculous.  I must have stumbled on a poorly-written set of directions.  Maybe it would work if I gave it another shot, but I'm not inclined to do so anytime soon.

My sound hardware is not anything exotic.  I have both onboard sound, SoundMax HD using an Analog Devices 1988B chipset, and a Creative Audigy 2 ZS sound card.  Both work fine in Kubuntu 9.04, including in games, such as Urban Terror.  I can even use Teamspeak at the same time on the same device, something that was broken in Kubuntu 8.04 (whichever program I ran first would monopolize the sound device, for some reason).  So I don't understand why sound broke when I upgraded to 9.10.

Fortunately, I had used Clonezilla to image my / partition before trying the upgrade, so it was easy to roll back to my 9.04 install.

While flailing about in 9.10 yesterday, I came across lots of comments on other forums from poor sods who'd had something similar happen to them after an upgrade.  Has anyone found a fix for this "no sound after upgrade" problem?

---

### Post by presence1960 on 2009-12-21
> **Objekt said:**
> Yesterday I tried a Kubuntu 9.04->9.10 upgrade.  Today I downloaded a Kubuntu 9.10 install CD, because yet again, the upgrade broke something major.

Two hours of downloading a bit over 1 GB of packages was not the problem.  The problem was that after the upgrade, sound was simply broken.  The only way I could get the system to utter a peep was by playing back a DVD image.  I initially thought it was the old "No sound in Flash videos" bug reborn, because that was one of the first things I tested.  I spent about half an hour trying various fixed for that, reinstalling Flash etc.  I then realized that I wasn't getting any sound in any app, apart from the noted exception with Kaffeine playing DVDs.

I also tried installing a newer version of ALSA, but I gave up when it wanted to do a 400+ MB download.  Ridiculous.  I must have stumbled on a poorly-written set of directions.  Maybe it would work if I gave it another shot, but I'm not inclined to do so anytime soon.

My sound hardware is not anything exotic.  I have both onboard sound, SoundMax HD using an Analog Devices 1988B chipset, and a Creative Audigy 2 ZS sound card.  Both work fine in Kubuntu 9.04, including in games, such as Urban Terror.  I can even use Teamspeak at the same time on the same device, something that was broken in Kubuntu 8.04 (whichever program I ran first would monopolize the sound device, for some reason).  So I don't understand why sound broke when I upgraded to 9.10.

Fortunately, I had used Clonezilla to image my / partition before trying the upgrade, so it was easy to roll back to my 9.04 install.

While flailing about in 9.10 yesterday, I came across lots of comments on other forums from poor sods who'd had something similar happen to them after an upgrade.  Has anyone found a fix for this "no sound after upgrade" problem?

Here is the fix: **_DO A CLEAN INSTALL!!_** Beforehand do this: [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Make sure you have a good backup nevertheless every time you partition/install an OS.

After the install and prior to restoring the packages add all repositories you had enabled on the old version. 

Now run that second command from the link and relax while your packages are downloaded and reinstalled for you.

---

### Post by Objekt on 2009-12-21
Yeah, clean install is the only thing that's been reliable so far.  I'm not sure why, but the *buntu "upgrades" never, ever work for me.

Thanks for the link.  Having to reinstall lots of stuff was one reason I was dreading a clean install.  Now I won't have that problem.  Might not even have to re-run the Medibuntu stuff.  Neat.

I downloaded the Kubuntu 9.04 64-bit desktop CD today & have it burned to a disc, so I guess I'll go ahead and do the clean install.

---

### Post by presence1960 on 2009-12-21
> **Objekt said:**
> Yeah, clean install is the only thing that's been reliable so far.  I'm not sure why, but the *buntu "upgrades" never, ever work for me.

Thanks for the link.  Having to reinstall lots of stuff was one reason I was dreading a clean install.  Now I won't have that problem.  Might not even have to re-run the Medibuntu stuff.  Neat.

I downloaded the Kubuntu 9.04 64-bit desktop CD today & have it burned to a disc, so I guess I'll go ahead and do the clean install.

You are welcome. Just passing on what I have learned. Just be sure to enable all the repositories and sources in the clean install that you had in the prior version. Then run that second command to restore packages. Obviously if the repositories are not enabled the packages can't get installed.

---

### Post by Objekt on 2009-12-22
I finished a clean install and re-downloading all my former packages like in the thread you linked.  Some stuff is still broken:

1) Sound doesn't work in games. <fixed by reinstall>

2) The display configuration will not persist between sessions.  I set the screen to 1600x1200 every time I log in, but it keeps resetting itself to 1280x1024 after restart.  Very annoying!   FWIW, I am using the proprietary NVidia drivers (GeForce 9800 GTX+ video card).  Trying to save settings in the Nvidia control panel app doesn't work.  

I'm getting the problems licked one by one.  Nvidia settings lack of persistence is the only one remaining.

---

### Post by sliketymo on 2009-12-22
Try disabling any extra repositories you have added before updating,then upgrading.A lot of folks seem to miss that step.

---

### Post by presence1960 on 2009-12-22
> **sliketymo said:**
> Try disabling any extra repositories you have added before updating,then upgrading.A lot of folks seem to miss that step.

He didn't do a dist-upgrade but rather a clean install.

---

### Post by presence1960 on 2009-12-22
> **Objekt said:**
> I finished a clean install and re-downloading all my former packages like in the thread you linked.  Some stuff is still broken:

1) Sound doesn't work in games. <fixed by reinstall>

2) The display configuration will not persist between sessions.  I set the screen to 1600x1200 every time I log in, but it keeps resetting itself to 1280x1024 after restart.  Very annoying!   FWIW, I am using the proprietary NVidia drivers (GeForce 9800 GTX+ video card).  Trying to save settings in the Nvidia control panel app doesn't work.  

I'm getting the problems licked one by one.  Nvidia settings lack of persistence is the only one remaining.

Run the nvidia-settings as root from terminal ```
gksu nvidia-settings
```

---

### Post by sliketymo on 2009-12-22
> **presence1960 said:**
> He didn't do a dist-upgrade but rather a clean install.

Post title says thats what he tried to do first.Just sayin'

---

### Post by presence1960 on 2009-12-22
> **sliketymo said:**
> Post title says thats what he tried to do first.Just sayin'

Just sayin' read all the posts before commenting.

---

### Post by Objekt on 2009-12-22
Everything was working fine for a while, then sound randomly stopped working in several apps.  It stopped working in games, Teamspeak 2, and VLC media player, but still worked in Kaffeine and for the system startup/shutdown sounds.

After several hours of trying to find a fix, I had to just give up.  To hell with 9.10.  I'm glad I kept an image of my 9.04 install, which I've restored & am now using trouble-free.

---

### Post by presence1960 on 2009-12-22
> **Objekt said:**
> Everything was working fine for a while, then sound randomly stopped working in several apps.  It stopped working in games, Teamspeak 2, and VLC media player, but still worked in Kaffeine and for the system startup/shutdown sounds.

After several hours of trying to find a fix, I had to just give up.  To hell with 9.10.  I'm glad I kept an image of my 9.04 install, which I've restored & am now using trouble-free.

sorry it didn't work out. Sometimes that happens. But at least you found a  way to do a clean install and have your previous version's packages installed on the new version. That saves a lot of work!

---

