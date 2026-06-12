---
title: "Karmic: Pidgin/Empathy and Ipod"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 5nak3 on 2009-10-27
Hi all,

Well I decided to jump the gun just slightly and get a copy of Karmic before release date. While the iso says RC version, I'm not sure if we are to expect any changes between when I downloaded the iso and the 29th. 

In any case for the most part the RC has been great. Fixed a major problem I was having from 8.04, and on the whole seems much nicer to work with.

But I have three problems:

1) I run pidgin primarily for the plugin set, and empathy is simply a backup at the moment. While I'm running pidgin if someone sends me a message all of a sudden empathy will start up. I don't want that. Anyway to stop that?

2) Empathy would replace pidgin on my system but I cannot work out how to display a pop-up for when a user comes online. The pop-ups for when a user messages me works but not when they become available.

3)Ipod support, basically in Jaunty I had songbird which would detect the ipod when connected and everything was good. In Karmic I couldn't find a songbird package so I installed the Jaunty package, but the ipod cannot be found.

I can see it on my desktop and I can actually view the contents. But songbird would not mount it. Any ideas?

Many thanks!

---

### Post by phillw on 2009-10-27
Re: iPod

Is gtkpod available from koala registry ? this has ability to synch & play ipod music and vids
(GPixPod is it's little brother for photo's on an iPod)

Regards,

Phill.

---

### Post by 5nak3 on 2009-10-27
Gtkpod is indeed within the Karmic registry, but my last outing with it on Jaunty did not go very well so I just ignored it.

I'll give it a shot now.

---

### Post by phillw on 2009-10-27
> **5nak3 said:**
> Gtkpod is indeed within the Karmic registry, but my last outing with it on Jaunty did not go very well so I just ignored it.

I'll give it a shot now.


Please post back how you get on - I'm due to start supporting my brothers Ipod for backing up, etc.:-\

Thanks,

Phill.

---

### Post by 5nak3 on 2009-10-27
Yeah the reason for my trouble is because my dad has his ipod...i can't stand ipods and use an iriver player myself with MTP support meaning plug and play goodness :).

Anyways, I managed to get gtkpod setup despite some difficulties.

As long as Karmic can load your ipod onto the desktop then you are good to go as all you have to do is specify the mount point and it should work. My mount point was /media/<insert ipod name> 

After that you need to set the settings for the ipod you own...which I'll admit was guesswork on my behalf, but I'm sure google will help if you get stuck.

Now while I can easily just drag and drop music folders into gtkpod's window and get the files loaded onto my ipod I'm not sure what backing up the files are like.

I'll test my dads ipod mini and see if i can back up the files, last thing I want is to delete all his music from his primary device.

To be perfectly honest with you though, the use of songbird was much easier on jaunty. It works more like itunes, and needs less fiddling. As a result if you have an option of running jaunty, intrepid, or hardy choose to run one of those along with songbird as opposed to a Karmic and gtkpod mashup.

This message was written quite hastily as I'm in the middle of several different activities, if you would like more details I can try and fill you in later.

---

### Post by joey-elijah on 2009-10-27
You could always use the nightly builds of songbird from the official PPA - they come in Karmic flavour. 

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

Empathy randomly starting up annoys me, too. It's like it gets jealous! 

A quick fix is to set Empathy to not automatically login to your accounts when it starts up.

---

### Post by 5nak3 on 2009-10-27
Ah see I thought I was the only one that had empathy doing that as I found no information on it through google.

If I set Empathy to not log me in on startup, wouldn't that still mean it is running in the background though?

I tried to delete it as well, but as far as I remember I saw that it was linked t to ubuntu-desktop package and I'm pretty sure deleting that is a bad thing...

Just wondering about the Songbird nightly builds you mentioned Joey, are they pretty much developer builds prone to be less stable? And are they likely to be ported over as a stable release in the future? The reason I ask is because there didn't seem to be any information on the Launchpad site.

Cheers!

---

### Post by terry_gardener on 2009-10-27
2. 
notification when contact comes online.

open empathy and go edit - preferences, notifications tab, enable notifications when contacts come online, there is also option for offline. 

use the sound tab to enable sound notifications. 

hope this helps.

---

### Post by 5nak3 on 2009-10-27
@Terry

Hi, thanks for the post. I had seen and enabled that option. But despite this there was no pop up to notify me of contacts coming on or offline.

Having said that, the sound notifications work perfectly...so I really am unsure as to why that is the case.

Out of curiosity do you use the notification envelope in the top panel? I disabled it from the start so maybe that could have an effect?

---

### Post by terry_gardener on 2009-10-27
last time i tested it worked ok. 
see screenshot to see how i have mine setup 

not tested it for about a week though.

---

### Post by michael37 on 2009-10-28
> **5nak3 said:**
> Hi all,

Well I decided to jump the gun just slightly and get a copy of Karmic before release date. While the iso says RC version, I'm not sure if we are to expect any changes between when I downloaded the iso and the 29th. 

In any case for the most part the RC has been great. Fixed a major problem I was having from 8.04, and on the whole seems much nicer to work with.

But I have three problems:

1) I run pidgin primarily for the plugin set, and empathy is simply a backup at the moment. While I'm running pidgin if someone sends me a message all of a sudden empathy will start up. I don't want that. Anyway to stop that?

2) Empathy would replace pidgin on my system but I cannot work out how to display a pop-up for when a user comes online. The pop-ups for when a user messages me works but not when they become available.

Many thanks!

Pidgin/Empathy - I am not huge of Empathy too.  Make sure it's not running - it has a "chat" icon is on the top right next to your username/login/logout button.  If you can't kill it gracefully, there is always an option to "killall empathy"

---

### Post by 5nak3 on 2009-10-28
Thanks for the screenshot Terry, I too have the same setup as you, but it just doesn't work :(

Never mind, that little problem and the fact file transfer support for msn was not present made me go ahead and remove empathy.

One thing I did notice upon its removal was the face that telepathy-butterfly, babble and haze were still installed. But synaptic says that these are needed for libpurple. As a result I just left them as they were.

I'm back to Pidgin full time, and while I might not have nice adium theme support, I have file transfer support, a wealth of plugins and I am not interrupted by a "jealous" empathy ;)


I'm still not getting anywhere with the ipod support. Gtkpod seems to work in terms of reading and making small changes to my ipod. But it wants to keep writing the iTunesDB to my admin user as opposed to the user that is using the program, which ends up with a load of write permission errors.

Further to that, I tried backing up a song collection and found the program would back up the songs to an external drive for about 4 min and then crash. Not really practical to keep guessing what songs are saved and what you need to save. I just ended up taking the iPod_contol folder and sticking that on my external drive until a more elegant solution is found.

If anyone has any information about the Songbird nightly builds I would be very thankful.

I'm really looking at whether or not you can actually use the iPod with Karmic and Songbird nightly. As Karmic and Songbird stable didn't work together.

And also I would like to know about the stability of nightly builds, my dad is the one who will be using it and his technical knowledge is limited. So I need a program he can use when I'm not around and not fear breaking anything.

Big thanks to everyone that has helped out so far.

---

### Post by 5nak3 on 2009-10-28
In terms of songbird and ipod problems I've been having, I think I've found a solution.

Using songbird 1.2 (the stable version from getdeb.net), I've found that you can actually run your ipod by doing the following:

1) Download and install songbird 1.2 (do not upgrade to the daily build as this has no ipod support)

2) Install the ipod add-on for songbird

3) Connect your ipod to your PC. At this point ubuntu should recognize it and place the icon on your desktop. However songbird does not recognize the ipod.

4) Right click the desktop icon and select unmount, it is important to select unmount and not eject.

5) Re-mount the ipod, e.g. click on the ipod link under the places menu places -> ipod

6) After this, songbird should identify the ipod and start showing it as a device and then go ahead and start to sync with the ipod. Also Nautilus will pop up showing the contents of the ipod. Simply close the nautilus window and manage your ipod through Songbird.

---

### Post by quimkaos on 2009-10-28
well for me with  Empathy its more, the notifications are ok but if someone sends me an messages i only get a notification, and the message dialog doesn't pop up, only the icon of the sender gets flashing in the contact list. I have lost messages because of this...
Plus i seted it to start on startup and it's not starting up on system startup (question of the day: were can i put one more star in this sentence?)
I have multiple protocols in use and it doesn't uses an icon to distinguish from them (this is for me, a useful feature implemented in pidgin)...
for some reason i have a few contacts out without group that in pidgin (and msn - the original software were they were organized) were in another contact group, so i have a mess in my contact list with contacts from gtalk mixed with some of msn...
so I'm probably going to replace it with pidgin...

---

