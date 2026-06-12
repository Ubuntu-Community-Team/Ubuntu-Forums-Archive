---
title: "partial upgrade?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Bashed on 2007-05-06
Why I am getting this?

I'm new to linux, so please be precisely clear

---

### Post by Sef on 2007-05-06
You're getting it because you are running Automatix.   It is nice, but it often causes problems like you have, if not worse.  With Feisty, Automatix really isn't needed.   Most of the codecs can be installed through Add/Remove.

---

### Post by starcraft.man on 2007-05-06
You could try well uninstalling everything you installed with Automatix, via the gui, then removing automatix and after that, upgrading. That should do it, if not, maybe you should simply consider a clean install and remount your home partition with it. I do agree with Sef, me no like automatix. Only script I ever recommend is envy, and it only does one thing, drivers :)

---

### Post by Bashed on 2007-05-06
Ok, first are you both 100% positive automatix is the problem? Reason I ask is because it seems so popular of a program and gets praises from what I've read and asked around in the forums and linux/ubuntu blogs.

Secondly, what about the hassle of reinstalling all the necessary codecs? What's an easy way to install every common and extra "special" codec for video/dvd/audio, etc via Synaptic?

Also, how do I properly uninstall Automatix anyway? I google'd and got nothing.

---

### Post by starcraft.man on 2007-05-06
> **TalkJesus said:**
> Ok, first are you both 100% positive automatix is the problem? Reason I ask is because it seems so popular of a program and gets praises from what I've read and asked around in the forums and linux/ubuntu blogs.

Secondly, what about the hassle of reinstalling all the necessary codecs? What's an easy way to install every common and extra "special" codec for video/dvd/audio, etc via Synaptic?

Also, how do I properly uninstall Automatix anyway? I google'd and got nothing.

Yes, I am pretty confident its automatix (can't speak for sef or he might smite me :p). You are also right that it is pretty popular, mostly because it is push to click easy like windows and helps transition people (rather than the culture shock of apt-get). As for the praise, I bet a lot of the people who praise it when they first begin using Ubuntu, will likely run into problems later and either 1) Don't post it or mention it or 2) don't figure out that its the cause and reinstall from scratch with new version instead of upgrade and put automatix back on and perpetuate  their ignorance of it.

I also don't know which Ubuntu blogs you read, but I don't find automatix that highly recommended, in fact I try and steer people away from it... why? It encourages complacency, ignorance and laziness... apt-get isn't that difficult, it is incredibly powerful and able to do almost anything you want with an installation.

As for your next question an easy way to install all the codecs... Ubuntu isn't strictly speaking designed to be easiest, its designed to be Ubuntu. Don't try and compare it to windows, its a bad comparison. However, if your looking for how to install things in Ubuntu look [here]("http://www.psychocats.net/ubuntu/index.php") and [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") . For specific instructions on installing codecs, read [this...]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") its not too hard, don't just copy and paste though, its important to understand what things mean.

To remove:

```
sudo aptitude autoremove automatix2
```
Into your terminal (Applications > Accessories > Terminal)

That should be enough answers, please read up it will benefit you in the long run :)

---

### Post by Bashed on 2007-05-06
Ok, is it 100% necessary to first uninstall all software installed via automatix, or is automatix ITSELF the conflict of synaptic upgrades?

---

### Post by Bashed on 2007-05-06
I proceeded to uninstall everything in automatix, and only the multimedia codecs gave errors:

---

### Post by Bashed on 2007-05-06
chad@Secured:~$ sudo aptitude autoremove automatix2
Password:
Unknown command "autoremove"
aptitude 0.4.4
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...


chad@Secured:~$ sudo aptitude remove automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  transcode 
The following packages have been kept back:
  faad ffmpeg libgpod1 mjpegtools 
The following packages will be REMOVED:
  automatix2 
0 packages upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 100589 files and directories currently installed.)
Removing automatix2 ...


I still get the same error in update manager.

---

### Post by starcraft.man on 2007-05-06
> **TalkJesus said:**
> I proceeded to uninstall everything in automatix, and only the multimedia codecs gave errors:

Uhhhh, stupid thing. Multimedia codecs can be removed without causing errors...

Ok, just run the following command:

```
sudo aptitude autoremove automatix2
```

Your probably ok after it gets uninstalled.

One additional note, change your graphics driver to nv or the other default when upgrading. Leaving your computer on the graphics driver has caused problems for many people.

Then try your upgrade again. It should work, if not bah, might just want to do a quick reinstall and remount your data to the drive.

EDIT: Geez, your fast. Ok then, just switch your driver to the 2d drivers IF you installed nivida or ati drivers and then go for the upgrade again. Please don't put automatix in again... >.>

---

### Post by Bashed on 2007-05-06
See my last few posts.  "autoremove" does work

"EDIT: Geez, your fast. Ok then, just switch your driver to the 2d drivers IF you installed nivida or ati drivers and then go for the upgrade again. Please don't put automatix in again... >.>"

I'm new to linux. You talk to me as if I have every bit of linux knowledge.

My graphics driver on my Sony laptop is Intel 945GM. I have no idea if there is any nvidia relation to that chipset.  I also never touched the drivers either.

---

### Post by starcraft.man on 2007-05-06
> **TalkJesus said:**
> See my last few posts.  "autoremove" does work

"EDIT: Geez, your fast. Ok then, just switch your driver to the 2d drivers IF you installed nivida or ati drivers and then go for the upgrade again. Please don't put automatix in again... >.>"

I'm new to linux. You talk to me as if I have every bit of linux knowledge.

My graphics driver on my Sony laptop is Intel 945GM. I have no idea if there is any nvidia relation to that chipset.  I also never touched the drivers either.

Hehe, sorry, doing a few things at once. Ok then, so you don't have any special drivers installed, try the upgrade now. Don't worry about autoremove.

---

### Post by Bashed on 2007-05-06
Please see my 2nd or 3rd last post. I already tried the upgrade and still got the same error. I provided a screenshot before.

---

