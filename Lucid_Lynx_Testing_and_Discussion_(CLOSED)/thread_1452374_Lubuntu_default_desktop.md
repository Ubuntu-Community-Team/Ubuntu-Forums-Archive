---
title: "Lubuntu default desktop"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RTrev on 2010-04-11
I've been using Lubuntu, and had no problems until today.

Problem 1 was that I logged in and found myself with a blank desktop and could do nothing except Ctrl-Alt-F2, login, and then do a shutdown from the cli.  When it had rebooted, I saw that Lubuntu was no longer the selected desktop, and it was now saying "Default" instead.  Changing it to Lubuntu again solved that problem, except that I have to change it every time I log in.  Does anyone know how to make that setting "stick" like it used to?

Problem 2 is that I use Audacity to make a type of voice recording which I can later convert into PureVoice (.qcp) format to converse with a friend who uses this format.  Under Gnome, it works perfectly.  Under Lubuntu, it works for a while and then it simply stops recording.  The program is still responsive, and I can exit from it using the usual menus, but it simply is stuck recording.  This happens at random times, but always within the first few minutes.  If I make a very short recording, and stop it before it stops itself, then I can play it back, save it, etc.  It's got me stumped.  Anyone have any ideas?

Thanks in advance!

---

### Post by ranch hand on 2010-04-11
I know nothing about the second problem.

The first is related to the update of lxdm.

You might try putting up with it as they seem to be getting it better behaved.

You could try re-enabling gdm and disabling lxdm.

---

### Post by RTrev on 2010-04-11
> **ranch hand said:**
> I know nothing about the second problem.

The first is related to the update of lxdm.

You might try putting up with it as they seem to be getting it better behaved.

You could try re-enabling gdm and disabling lxdm.

Oh, okay.. thanks.  I thought it was just something dumb I did.  If they're working on it, I'll wait.  I don't really want to install gdm to solve this, but good to know I could.  Thanks!

---

### Post by ranch hand on 2010-04-11
I installed a long time ago and we were using gdm and it has never been removed by any updates.  It may not be on clean installs.

I had to use it for a while after we started using lxde.  This is something you might want to file a bug on.

I am sorry I can 't find the link right now, it is in the Lubuntu documentation somewhere.  It is part of the Lubuntu Launchpad stuff.   I am just tired and my wife and I have both had kind of bad days.  Just too lazy to look for it.

EDIT

It is actually an lxde problem.

---

### Post by RTrev on 2010-04-11
> **ranch hand said:**
> I installed a long time ago and we were using gdm and it has never been removed by any updates.  It may not be on clean installs.

I had to use it for a while after we started using lxde.  This is something you might want to file a bug on.

I am sorry I can 't find the link right now, it is in the Lubuntu documentation somewhere.  It is part of the Lubuntu Launchpad stuff.   I am just tired and my wife and I have both had kind of bad days.  Just too lazy to look for it.

EDIT

It is actually an lxde problem.

Fair 'nuff! <g>  Appreciate the tip!  I'll go see if there's a bug filed yet, and file one if not.

---

### Post by keithpeter on 2010-04-12
Hello

[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/561377/](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/561377/)

but I think it may be duplicating some of the other bugs shown at

[https://bugs.launchpad.net/ubuntu/+source/lxdm/](https://bugs.launchpad.net/ubuntu/+source/lxdm/)

there are references to lxdm.conf there as well.

I only see this on first boot, not on logging in/logging out.

PS: hope today is better for people.

**Added 14th April**: A new lxdm came down with today's update and that corrected the failure to use the last session when booting fresh.

---

### Post by RTrev on 2010-04-14
Okay, the booting into the LXDE desktop problem has been fixed, but the Audacity one hasn't.  I'm not very comfortable in the bug pages, but haven't found any such bug reported yet.  Guess it's time to get my feet wet and report it. :(

---

### Post by keithpeter on 2010-04-14
> **RTrev said:**
> Okay, the booting into the LXDE desktop problem has been fixed, but the Audacity one hasn't.  I'm not very comfortable in the bug pages, but haven't found any such bug reported yet.  Guess it's time to get my feet wet and report it. :(

Hello RTrev, well, all I can say is that I've just installed Audacity and made a 10 minute recording of next door's dog, the boy racers out the back, and me doing bobby mcferrin impressions, and Audacity seemed quite happy. I've tried the default 44.1 Kb/s sampling rate and 48Kb/s. I did have to make sure my 'front mic' socket was the default input and turn the volume up on the 'capture' channel using alsamixer but I guess you have got that far already.

There are some reports of problems with Audacity in earlier versions of Ubuntu...

[http://ubuntuforums.org/search.php?searchid=71915622](http://ubuntuforums.org/search.php?searchid=71915622)

...but they seem to be cutting out after seconds rather than minutes.

I'd suggest posting a new thread with something like 'Lubuntu Audacity problem' as the subject line.

**Long shot**: I had already installed the ubuntu-restricted-extras package that has a lot of codecs. I also have Firefox installed as I need it for some plug ins I use a lot. I've also installed openoffice and gimp, so this isn't a 'pristine' Lubuntu box.

---

### Post by RTrev on 2010-04-14
> **keithpeter said:**
> Hello RTrev, well, all I can say is that I've just installed Audacity and made a 10 minute recording of next door's dog, the boy racers out the back, and me doing bobby mcferrin impressions, and Audacity seemed quite happy. I've tried the default 44.1 Kb/s sampling rate and 48Kb/s. I did have to make sure my 'front mic' socket was the default input and turn the volume up on the 'capture' channel using alsamixer but I guess you have got that far already.

There are some reports of problems with Audacity in earlier versions of Ubuntu...

[http://ubuntuforums.org/search.php?searchid=71915622](http://ubuntuforums.org/search.php?searchid=71915622)

...but they seem to be cutting out after seconds rather than minutes.

I'd suggest posting a new thread with something like 'Lubuntu Audacity problem' as the subject line.

**Long shot**: I had already installed the ubuntu-restricted-extras package that has a lot of codecs. I also have Firefox installed as I need it for some plug ins I use a lot. I've also installed openoffice and gimp, so this isn't a 'pristine' Lubuntu box.

Thanks keithpeter.  I'll try the new thread.

Part of my problem is that I'm not really sure where to report the bugs.  Maybe Lubuntu on launchpad, since it isn't officially a part of Ubuntu yet?

But I'll try that new thread here.  Yes, often I only make it seconds before it stops recording, but sometimes it's over a minute.  I'm creating specific types of files, but.. well, I'll go into it in my new thread. <g>

Thanks again..

---

### Post by Khakilang on 2010-04-23
I have use Lubuntu Lucid Lynx Alpha 1 I think and update through the Update Manager and everything works fine but I have not test the Audacity because of low hardware resources. Maybe try download all the updates and test it out again and see.

---

### Post by RTrev on 2010-04-23
> **Koh Kook Loon said:**
> I have use Lubuntu Lucid Lynx Alpha 1 I think and update through the Update Manager and everything works fine but I have not test the Audacity because of low hardware resources. Maybe try download all the updates and test it out again and see.

There's an update manager in Lubuntu?  Where?  All I have is Synaptic.  Used to have both with Gnome Ubuntu, but I've never had it under Lubuntu.

Yes, I'll download Audacity and try it again.  Odd problem.  Thanks.

---

### Post by Khakilang on 2010-04-23
> **RTrev said:**
> There's an update manager in Lubuntu?  Where?  All I have is Synaptic.  Used to have both with Gnome Ubuntu, but I've never had it under Lubuntu.

Yes, I'll download Audacity and try it again.  Odd problem.  Thanks.

Actually I went to Synaptic Manager and do a search for "Software Centre" and download and the "Update Manager" appear on my menu list. Can't you use the Synaptic to do the update? Another way is type Alt + F2 and run update-manager -d. All this command I found in the thread but I can't remember where. Hope this help.

---

### Post by RTrev on 2010-04-23
> **Koh Kook Loon said:**
> Actually I went to Synaptic Manager and do a search for "Software Centre" and download and the "Update Manager" appear on my menu list. Can't you use the Synaptic to do the update? Another way is type Alt + F2 and run update-manager -d. All this command I found in the thread but I can't remember where. Hope this help.

Oh sure, Synaptic is my preferred way of doing updates.. I was just curious if Lubuntu has some stuff that I'd missed. <g>  Thanks!

---

### Post by Khakilang on 2010-04-23
I guess in Synaptic there is a "Mark All Upgrades" and than "Apply" will also do the same thing. I am also new to Lubuntu and I am trying to get use to it and at the moment I don't know what is missing and I will keep on fiddling it I until I found out. Cheers!

---

### Post by Plumtreed on 2010-04-23
To 'update' I have been using the terminal:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoclean


I don't know if update-manager is working?

I used  'xubuntu-restricted-extras'  which works or at least I haven't hit any problems.

---

### Post by RTrev on 2010-04-23
> **Plumtreed said:**
> To 'update' I have been using the terminal:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoclean


I don't know if update-manager is working?

I used  'xubuntu-restricted-extras'  which works or at least I haven't hit any problems.

Oh, sure, the apt package, at the command line, works fine.  But the package called update-manager isn't a dependency of lubuntu-desktop.  It isn't installed by default.  One can always install it, I suppose, if it provides some functionality that isn't provided by apt or Synaptic.  (I can't think of any, offhand.)

---

