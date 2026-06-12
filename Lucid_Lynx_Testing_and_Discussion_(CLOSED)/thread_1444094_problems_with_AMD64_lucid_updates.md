---
title: "problems with AMD64 lucid updates?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gare on 2010-03-31
Hello,

Just wondering if anyone is having problems with Mar 31 2010 updates to Lucid Beta?

My Gnome will boot to login screen. 

But Will not open desktop after typing in password.

Anyone else?

Thanks.

---

### Post by bigsmitty64 on 2010-03-31
None here.

---

### Post by Sef on 2010-03-31
Moved to Lucid.

---

### Post by jjcv on 2010-04-01
Same problem with me.  amd64 on a dell laptop.  Working fine until todays updates.

---

### Post by Scott82 on 2010-04-01
was it partial update? if so have a looksie here: [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

i ask 'cuz i haven't been able to find a time that it wasn't partial since saturday on my pc's

---

### Post by NightwishFan on 2010-04-01
You might be affected by a known bug that is already fixed. Try this:

Press ctl+alt+f5 to get to a console, log in as your user and run these commands:
```
sudo aptitude update
```
```
sudo aptitude safe-upgrade
```
```
sudo aptitude full-upgrade
```

Then reboot.

---

### Post by jjcv on 2010-04-01
Thanks for that NightwishFan.  

I did not know about the ctl+alt+f5 so that was  great to find.

The process removed quite a few packages and installed a few but alas no progress with login in.   I get the gdm login screen.  Enter password, the screen disappears and then goes black and it comes back a few seconds later with the gdm login again.

Perhaps the updates are taking a bit of time to get downunder to New Zealand.  Will try again in the morning and if not working then dig a little deeper if I get a chance.... Easter Friday so maybe not.

---

### Post by gmoore777 on 2010-04-01
yeah, i'm hosed as well.
This happened yesterday as well but I managed to make things right,
by running, 
sudo aptitude update; sudo aptitude full-upgrade;

rather than my usual 
sudo apt-get update;sudo apt-get dist-upgrade;

I also had to install the ubuntu-desktop, since that was removed early on in the install process of yesterday.
sudo apt-get install ubuntu-desktop

But today, as of right now, the package dependencies are messed up
or the packages they depend on haven't been pushed.
Cause trying to install ubuntu-desktop, I now get:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Recommends: evolution but it is not going to be installed
                  Recommends: evolution-couchdb but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: evolution-indicator but it is not going to be installed
                  Recommends: evolution-plugins but it is not going to be installed
                  Recommends: rhythmbox-ubuntuone-music-store but it is not going to be installed
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
E: Broken packages


(and a side comment to people who keep reminding that this is a beta and that we shouldn't be using LucidLynx for beta. There would be quite a lot less testers if we only installed this on an extra machine, and then tested it in our spare time. I have no extra machine, I have no extra time. I use mainly LucidLynx at work, and yes, I hope for the best and expect the worst. It's at the worst right now.)

---

### Post by NightwishFan on 2010-04-01
Thats fine, they just arent ready to be installed yet. Stuck to "safe-upgrade" instead of "full-upgrade" for now then.

As for you are unable to login? Do you have a nvidia card?

---

### Post by gmoore777 on 2010-04-01
"safe-upgrade" does nothing. (probably what I should have been running all along)
I can ssh into the machine. I have not rebooted machine yet.
Don't want to. I'd be afraid what state it will be in.
In this case, time will fix this problem. (Otherwise, the bulletin board will just fill up with all the same postings.)
I don't have a separate graphics card (nvidia), just the built in Intel graphics processor.

---

### Post by NightwishFan on 2010-04-01
Safe-Upgrade does not remove packages to fix dependencies. So it means you are probably fully upgraded. If you cannot log in it seems like an X related issue. Try reinstalling your graphics drivers.

---

### Post by arnab_das on 2010-04-01
i have been repeatedly getting partial upgrade messages since installation.

i did what u said (@Nightwishfan), and what the upgrade is doing is currently installing packages which its not supposed to. (eg. i have locked a version of wine but its still repeatedly upgrading to the latest version) is this to do with my software sources list? (apparently the lucid repo is unselected)

[[IMG]http://img693.imageshack.us/img693/340/softwaresources003.png[/IMG]](http://img693.imageshack.us/i/softwaresources003.png/)


unfortunately only sudo apt-get upgrade works. the other two commands are supposedly "invalid operation"s.

---

### Post by NightwishFan on 2010-04-01
If you manually updated to Lucid it disables all the third party repositories. Check if you have a lucid verson available in the ppa and re-add them.

Ensure you type the command right, I OCD'd and capitalised them since they were not in code form, the correct command is:
```
sudo aptitude update
```
```
sudo aptitude safe-upgrade
```

It is basically the same thing as saying "no" to the partial upgrade then hitting install updates.

---

### Post by arnab_das on 2010-04-01
@Nightwishfan

thanks. that worked. but still getting the partial updates info.

[[IMG]http://img231.imageshack.us/img231/2861/updatemanager004r.png[/IMG]](http://img231.imageshack.us/i/updatemanager004r.png/)

btw i was talking about the lucid repo in that screenshot which is the archive.com/canonical/ubuntu lucid. is that one supposed to be unchecked?


(i manually disabled the wine repo since it kept reminding me of a newer version. but unfortunately even that and version locking didnt work and i'm still getting messages of wine updates.)

---

### Post by NightwishFan on 2010-04-01
Yes, I think only "main" in the first tab is all you need. All else are optional. Just hit  "close" if you do not want to partial update. The safe-upgrade will not fix that. It will just update you as much as possible without breaking any packages.

---

### Post by jjcv on 2010-04-01
Well I am now back in.  :p

I did as suggested and this morning the aptitude safe-upgrade then aptitude full-upgrade pulled a lot of stuff in.

I then did an:

aptitude install gnome-desktop-environment

which installed some of the packages which had previously been removed.   Once I was back in I used synaptic to install further packages that had been removed like ubuntu-store.

There is still one dependency problems. 

I have been running Lucid since Alpha 3 and overall it has been a great experience.  Was hard going back to Karmic - I missed Lucid too much.  :-)   I will probably do a reinstall once Beta 2 comes out.

---

### Post by NightwishFan on 2010-04-01
Gnome-Desktop-Environment is mostly a Debian thing. You need:
```
sudo aptitude install ubuntu-desktop
```

---

