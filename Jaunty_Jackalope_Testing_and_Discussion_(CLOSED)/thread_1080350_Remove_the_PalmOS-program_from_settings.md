---
title: "Remove the PalmOS-program from settings"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-02-25
I think the PalmOS-program should be removed from settings, perhaps even from defaultinstall? What do you think?  About two months ago there was even a pressrelease about Palm not making any new Handhelds ([http://www.palminfocenter.com/news/9654/colligan-no-new-palm-handhelds/](http://www.palminfocenter.com/news/9654/colligan-no-new-palm-handhelds/)). 

If anything it would make more sense to have Synce as default as Windows Mobiles is bigger then (no longer made) Palm Pilots?

---

### Post by taavikko on 2009-02-25
+1

How many of you guys/girls have some kind of an Handheld device, in use with ubuntu?

I know I don't :D

---

### Post by Tich666 on 2009-02-25
I recently wondered as well why there's software for a minority user group such as this is installed by default and cluttering up the system preferences even more.

---

### Post by olskar on 2009-02-25
> How many of you guys/girls have some kind of an Handheld device, in use with ubuntu?


I have a Windows Mobile-device but syncing via cable is kind of old. I use Google Calendar and sync with it over Wifi :)

(I only wish evolution could have better support for Google Calendar then Windows have :mad:)

> I recently wondered as well why there's software for a minority user group such as this is installed by default and cluttering up the system preferences even more.

Yes, it is way to cluttered. I will make a bugreport!

---

### Post by klange on 2009-02-25
I agree.

PalmOS is no longer even supported by Palm, and how many people actually have one these days?

Kill gnome-pilot.

---

### Post by olskar on 2009-02-25
You can confirm it here and add your opinions

[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446)

---

### Post by Nizarus on 2009-02-25
I use ubuntu and I got a palmos device :lolflag:

---

### Post by jmmL on 2009-02-25
I agree.

From the launchpad page, it appears development upstream has stopped. The last major version released was 2.0.15 on 2006-12-19.

---

### Post by olskar on 2009-02-25
> **jmmL said:**
> I agree.

From the launchpad page, it appears development upstream has stopped. The last major version released was 2.0.15 on 2006-12-19.

According to the mailinglist they had a release 08 Jan 2009, 2.0.17

---

### Post by Sockerdrickan on 2009-02-25
> **olskar said:**
> I think the PalmOS-program should be removed from settings, perhaps even from defaultinstall? What do you think?  About two months ago there was even a pressrelease about Palm not making any new Handhelds ([http://www.palminfocenter.com/news/9654/colligan-no-new-palm-handhelds/](http://www.palminfocenter.com/news/9654/colligan-no-new-palm-handhelds/)). 

If anything it would make more sense to have Synce as default as Windows Mobiles is bigger then (no longer made) Palm Pilots?
+1:guitar:

---

### Post by dingar on 2009-03-03
I have one, but I agree to remove it from default installation.

---

### Post by sgosnell on 2009-03-03
There are still lots of Palms in use, and while there have been no new standalone handhelds released recently, Palm is still making smartphones with PalmOS on them.  Just because you don't use something doesn't mean nobody else does, nor that nobody else should.  How is it hurting you to have the Palm sync in the distro?

---

### Post by macogw on 2009-03-03
> **olskar said:**
> I have a Windows Mobile-device but syncing via cable is kind of old. I use Google Calendar and sync with it over Wifi :)

(I only wish evolution could have better support for Google Calendar then Windows have :mad:)

Evolution in Jaunty actually does work with Google Calendars now.  Right click in the calendar list and add a Google calendar.  Give it your gmail address (with the @gmail.com) in the Username field, then click "retrieve list."  It'll show all calendars you have access to, and you can pick one.


I haven't seen a Palm Pilot since...probably 1999.  And it *does* take up space on the installer CD that could be used to include, for example, a VPN client by default so that people who can't get online without a VPN can.  I mean, if you can't get online without a VPN client, how are you supposed to get online to download the VPN client?

---

### Post by forcecore on 2009-03-04
i wondered too what the heck is that palm tool rotting there, i do not know noone who uses palm, everyone uses now better things like XpressMusic, iPhone etc...

---

### Post by Foaming Draught on 2009-03-04
If I had my way, I'd leave Evolution out and put JPilot in.  Evolution doesn't sync with Palm anyway, at least not without killing fields and duplicating what it doesn't kill.  So I agree that Gnome-Pilot is a waste of space, but for different reasons to younger posters here for whom tinned music is more important than a go-anywhere PIM.

But I understand that I'm in a minority, it appears that many folk like bloated, unfunctional Evolution, so I just delete as much of it as I can without wiping the ubuntu-desktop metapackage, install rock-solid, fast JPilot and go my own efficient way.

---

### Post by theSeinfeld on 2009-03-26
I have a palm and I use it with Kubuntu. :lolflag:

This thread is not for not supporting the Palm devices, but just to drop it from default install. Even though I don't like M$ mobile edition, I agree that it has more users than Palm nowadays.

Meanwhile, we can also wait for the next generation WebOS and Palm Pre to come up and then we'll see who is better smart phone :popcorn:

My vote, remove it from default install, keep it in Universe...

---

### Post by sgosnell on 2009-03-26
I agree about jpilot.  I've been using it since I first started using Linux, and I especially like the Keyring sync/desktop.  There are lots of people using Palms, especially the TX, Lifedrive, and various Treos.  In the business world, they're all over the place.  Kids mostly playing games don't use them much, but those kids are not the majority of the Ubuntu users. If they don't want Palm support, it's easy enough to remove it, and the space it takes on the CD is inconsequential, a few KB.  

I've tried to like Evolution, but I just can't, any more than I can like Outlook.  Maybe it's just too similar to Outlook.  JPilot works for me, and I really wish it were included.  But we get what we get, and we certainly get our money's worth.

---

### Post by olskar on 2009-03-29
> **sgosnell said:**
> I agree about jpilot.  I've been using it since I first started using Linux, and I especially like the Keyring sync/desktop.  There are lots of people using Palms, especially the TX, Lifedrive, and various Treos.  In the business world, they're all over the place.  Kids mostly playing games don't use them much, but those kids are not the majority of the Ubuntu users. If they don't want Palm support, it's easy enough to remove it, and the space it takes on the CD is inconsequential, a few KB.  

I've tried to like Evolution, but I just can't, any more than I can like Outlook.  Maybe it's just too similar to Outlook.  JPilot works for me, and I really wish it were included.  But we get what we get, and we certainly get our money's worth.

For me, it's not as much about space on the CD but rather a cluttered preferences menu. We simply have to make it less cluttered and remove things from it, my suggestion is the Palmdevicesetting.

---

### Post by binbash on 2009-03-29
I have also palm device, drop it from default installation please.

---

### Post by spike_naples on 2009-04-01
So how can it be removed? Please tell me. I don't have a Palm device.

---

### Post by olskar on 2009-04-01
> **spike_naples said:**
> So how can it be removed? Please tell me. I don't have a Palm device.

Use the command:

sudo apt-get remove gnome-pilot

---

### Post by sgosnell on 2009-04-01
And if you want to make really sure it's completely gone:

sudo apt-get purge gnome-pilot

---

### Post by BGFG on 2009-04-01
I just tried to pugre it. needless to say, it did not work.

---

### Post by johnnybirdman on 2009-04-01
> **olskar said:**
> I think the PalmOS-program should be removed from settings, perhaps even from default install? 

Funny, i did a fresh install of 9.04 beta last night and saw this on the menu and thought... why is that still there?

---

### Post by canabal on 2009-04-01
> **johnnybirdman said:**
> Funny, i did a fresh install of 9.04 beta last night and saw this on the menu and thought... why is that still there?
Vote for the idea in brainstorm.

[http://brainstorm.ubuntu.com/idea/3844/](http://brainstorm.ubuntu.com/idea/3844/)

---

### Post by johnnybirdman on 2009-04-02
> **canabal said:**
> Vote for the idea in brainstorm.

[http://brainstorm.ubuntu.com/idea/3844/](http://brainstorm.ubuntu.com/idea/3844/)

done.

---

### Post by olskar on 2009-04-02
Okay, I dare to say we have an overwhelming majority that wants to remove this from default install. Remember it will still be avaible for install, all of you that actually have one of these.

What is the next step? I checked to see if it depends on ubuntu-desktop but it does not. How does this get installed by default? 
Edit: It was, I was looking for packages with palm in it but the name is gnome-pilot :)

The first step to fixing this bug would be to submit a bugfix to the launchpadreport at [https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/334446)

---

### Post by olskar on 2009-04-02
I have now made a debdiff and attached to the bugreport :)  I realize it will most likely not be used but it kind of proves a point on how easy this can be fixed if just many enough think like this.

---

### Post by sgosnell on 2009-04-03
All I can say is that some people get awfully excited about the silliest things.  With all the problems in the world, I would think there are more important things to worry about.

---

