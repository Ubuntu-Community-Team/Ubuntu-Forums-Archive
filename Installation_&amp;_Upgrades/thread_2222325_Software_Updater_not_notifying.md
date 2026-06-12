---
title: "Software Updater not notifying"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by linuxyogi on 2014-05-06
Hi,

I am using Lubuntu 14.04. Problem is the Software Updater is not appearing automatically even when security updates are available.

When I manually click on Software Updater it opens and I see security updates available. When I click Install Now updates get installed without any issue.

I double checked the settings, its configured to notify immediately as soon as security updates are available. Whats wrong ?[ATTACH=CONFIG]252904[/ATTACH]

---

### Post by bapoumba on 2014-05-06
Well, I run all my updates from the terminal, but indeed, the Software Updater never notifies me, although it's listed in the Default apps and set to autostart. I've made a few changes, will see if they work.

---

### Post by pfeiffep on 2014-05-06
Software updater notified me this morning about some updates which I choose to install immediately ... required a system reboot ... 
After reading this thread (about 30 minutes after updater finished) I executed sudo apt-get update and upgrade and received this
> The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default gettext gettext-base
  libasprintf-dev libasprintf0c2 libcompizconfig0 libdecoration0
  libgettextpo-dev libgettextpo0 libnautilus-extension1a nautilus 
  nautilus-data
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,048 kB of archives.
After this operation, 31.7 kB disk space will be freed.
Do you want to continue? [Y/n] y

Well I did continue but the question is "What exactly is the software updater doing or missing?"
Maybe I should disable automatic updates and use terminal in the future...

---

### Post by ibjsb4 on 2014-05-06
I do not have update-manger installed, so no help there.  But if you are looking for options, Synaptic PM works well for me.

---

### Post by linuxyogi on 2014-05-06
> **pfeiffep said:**
> Software updater notified me this morning about some updates which I choose to install immediately ... required a system reboot ... 
After reading this thread (about 30 minutes after updater finished) I executed sudo apt-get update and upgrade and received this

Well I did continue but the question is "What exactly is the software updater doing or missing?"
Maybe I should disable automatic updates and use terminal in the future...

After reading your post I tried apt-get update and upgrade to find out what happens in my case and I got these 

```
$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gettext-base libasprintf0c2 libnautilus-extension1a libtiff5 nautilus-data
  python3-software-properties software-properties-common
  software-properties-gtk
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 377 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 


```


I last updated approx 6 hrs ago so may be they were included during this time but I am not sure. 

You are running Ubuntu and reading your post I can see that the Software Updater at least launches automatically.

I read somewhere that the Software Updater works a bit differently in comparison to the CLI way. I guess I read this in 

AskUbuntu but I dont remember the exact difference. May be someone will answer that.

---

### Post by kansasnoob on 2014-05-06
It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563)

But apparently Lubuntu dev doesn't care :(

---

### Post by bapoumba on 2014-05-06
> **kansasnoob said:**
> It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563)

But apparently Lubuntu dev doesn't care :(

Ah thanks :)

---

### Post by pfeiffep on 2014-05-06
> **kansasnoob said:**
> It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563)

But apparently Lubuntu dev doesn't care :(

It's a bug in 12.04.1 that persisted in 14.04 - not very reassuring. 

So I'll continue with the terminal ad will not rely on faulty aautomation

---

### Post by monkeybrain20122 on 2014-05-06
Yup I used to install lubuntu on old machines for new users now I may switch over to xubuntu, lubuntu may be 'light' but at the cost of many usability bugs. It is problematic if the new user never run updates.

---

### Post by bapoumba on 2014-05-06
> **monkeybrain20122 said:**
> Yup I used to install lubuntu on old machines for new users now I may switch over to xubuntu, lubuntu may be 'light' but at the cost of many usability bugs. It is problematic if the new user never run updates.

But I guess it can be manually added to the autostart apps the same way nm-applet can, am I correct ? Will try that out.

---

### Post by kansasnoob on 2014-05-06
> **bapoumba said:**
> Ah thanks :)

Do you perhaps know how to bring that bug to the attention of the security team?

---

### Post by pfeiffep on 2014-05-06
OK - decided to try on my 64 bit tower ...

Software updater manually invoked with results similar to this morning on laptop - required reboot
Immediately after reboot apt-get update ; upgrade found more packages - very similar to this morning on laptop.

The reference bug is 2 years old and remains unassigned:confused:

---

### Post by Dennis N on 2014-05-06
I checked with htop and update-notifier was not running even though in **Default Applications for lxsession > Autostart** update-notifier is checked. I added it to **Manual Autostarted Applications** and rebooted. It has now started and is indicated as running. I manually updated with the terminal a while ago, so may have to wait for any notifications. We shall see.

---

### Post by bapoumba on 2014-05-06
> **kansasnoob said:**
> Do you perhaps know how to bring that bug to the attention of the security team?
Well, no, no more than anyone else here..

> **Dennis N said:**
> I checked with htop and update-notifier was not running even though in **Default Applications for lxsession > Autostart** update-notifier is checked. I added it to **Manual Autostarted Applications** and rebooted. It has now started and is indicated as running. I manually updated with the terminal a while ago, so may have to wait for any notifications. We shall see.
This is what I have done too, but am waiting until tomorrow and a reboot.

---

### Post by bapoumba on 2014-05-06
Well, I got accidentally logged out of my session, update-notifier did show up and offered the updates I had chosen not to apply on purpose today.

---

### Post by Rex Bouwense on 2014-05-06
OK.  I just did the same as you guys.  No wonder I haven't been getting any automatic update notifications.  I thought just because I was using the terminal there hadn't been any updates in between my checks.  Learn something every day.  Thanks bapoumba and Dennis N.

---

### Post by bapoumba on 2014-05-06
One thing to check in the longer run though. Will it show up at every login or only if there are updates to be applied ? The later would have my preference but I kinda doubt as it will be auto started up at every login. So not sure this is a fix, rather a workaround.

---

### Post by linuxyogi on 2014-05-06
I just got these 

```
$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  **python3-update-manager update-manager update-manager-core**
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 581 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 


```

Lets see if these fixes the bug.

---

### Post by linuxyogi on 2014-05-06
Those updates didn't do anything for this issue so I reselected update-notifier.

---

### Post by vasa1 on 2014-05-06
> **monkeybrain20122 said:**
> Yup I used to install lubuntu on old machines for new users now I may switch over to xubuntu, lubuntu may be 'light' but at the cost of many usability bugs. It is problematic if the new user never run updates.
That why I didn't show any interest in this whole StartUbuntu whatever. Unless one is with the user constantly, assuming the user really wants to use *buntu, the switch from Windows will be a nightmare for the "average" user.

Anyway, Lubuntu is the smallest team and there's just so much a few people can do. When one sees the bugs in better "equipped" distros, one wonders why some people target Lubuntu with caustic comments. I know that some people are very actively involved in testing and reporting bugs but venting in a forum like this doesn't really help. Sorry if anyone is offended but that's how I feel.

---

### Post by linuxyogi on 2014-05-06
But  I must say a lot of people have migrated to particularly Lubuntu after the release of 14.04. I can see that in their profiles in the forum.

---

### Post by bapoumba on 2014-05-07
> **vasa1 said:**
> That why I didn't show any interest in this whole StartUbuntu whatever. Unless one is with the user constantly, assuming the user really wants to use *buntu, the switch from Windows will be a nightmare for the "average" user.

Anyway, Lubuntu is the smallest team and there's just so much a few people can do. When one sees the bugs in better "equipped" distros, one wonders why some people target Lubuntu with caustic comments. I know that some people are very actively involved in testing and reporting bugs but venting in a forum like this doesn't really help. Sorry if anyone is offended but that's how I feel.

Rebooted this morning and it showed up with several updates. Is there anything I could do to help ? I'm not a dev and never did any coding, merely fussing around with confi files. The learning curve may be quite steep..

---

### Post by Dennis N on 2014-05-07
> Rebooted this morning and it showed up with several updates... 

Same here - I was notified of updates about 10 minutes after system start up.

---

### Post by Dennis N on 2014-05-07
Further comments: After the notification, I upgraded with Synaptic. I used the "Mark all Upgrades" button without reloading. There is a disparity on what Software Updater shows and what Synaptic shows, in that there are 5 additional packages in Synaptic's list. Why doesn't Software Updater show all upgrades? See attachment. Synaptic's History window on the right.

---

### Post by bapoumba on 2014-05-07
I updated with the Software Updater this morning. /var/log/apt/history.log :
```
Start-Date: 2014-05-07  09:58:11
Commandline: aptdaemon role='role-commit-packages' sender=':1.45'
Upgrade: libtiff5:i386 (4.0.3-7, 4.0.3-7ubuntu0.1), gettext-base:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3), libasprintf0c2:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
End-Date: 2014-05-07  09:58:22
```

Running apt-get update/upgrade (but that is about 6h later) shows :

```
The following packages will be upgraded:
  libido3-0.1-0 libnautilus-extension1a libselinux1 nautilus-data
  python3-update-manager update-manager update-manager-core
7 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 790 kB of archives.

```

I'll have another look tomorrow to check both at the same time.

---

### Post by linuxyogi on 2014-05-07
I dont understand whats wrong at my end. I added /usr/bin/update-notifier to a startup, rebooted and checked with htop but Software Updater is still not notifying. When I do apt-get update/upgrade I see updates.

---

### Post by bapoumba on 2014-05-07
I just added update-notifier.

---

### Post by Rex Bouwense on 2014-05-07
This morning I got a notification that there were updates to be downloaded and installed.  Well, there was only one so I installed it.  I checked the synaptic package manager immediately there after and there were four more, two of which dealt with the update notifier.  Not to be undone, I exited and checked apt-get and the same four showed up, which I installed.  I too will wait for tomorrow's check.

---

### Post by pfeiffep on 2014-05-07
> **bapoumba said:**
> I just added update-notifier.
With the activity on this thread it might be advisable to move it to Security Discussions. 
Many folks using Ubuntu probably do not connect to this forum and an issue with Software Updater not notifying consistently is a security issue. 
This thread has some folks testing different aspects, but I'm not noticing solutions.
Possibly some of the gurus who read security discussions will have some solutions.

---

### Post by bapoumba on 2014-05-07
> **pfeiffep said:**
> With the activity on this thread it might be advisable to move it to Security Discussions. 
Many folks using Ubuntu probably do not connect to this forum and an issue with Software Updater not notifying consistently is a security issue. 
This thread has some folks testing different aspects, but I'm not noticing solutions.
Possibly some of the gurus who read security discussions will have some solutions.
I'm not sure about Security (you can browse through it, more firewall & stuff than anything else), more Installation & Upgrades to me, but all in all GH is as good. Maybe wait for the OP and see what they have to say.

---

### Post by Tar_Ni on 2014-05-07
> **pfeiffep said:**
> With the activity on this thread it might be advisable to move it to Security Discussions. 
Many folks using Ubuntu probably do not connect to this forum and an issue with Software Updater not notifying consistently is a security issue. 
This thread has some folks testing different aspects, but I'm not noticing solutions.
Possibly some of the gurus who read security discussions will have some solutions.

I was using Lubuntu 13.10 a few months ago and was never notified of any kind of update.. Had to search for them manually. Hopefully most people will have the sens to run the Update manager from time to time and get their updates but the beginner might not..

---

### Post by Dennis N on 2014-05-07
It is not Lubuntu 14.04 only. Xubuntu 14.04 exhibits the same difference in the available upgrades from Software Updater and apt-get or Synaptic. So the question is why are they different? In Xubuntu 14.04, I am leaving them both untouched and will see when (tomorrow?) Software Updater shows me the other packages. Maybe it just works differently and will pick them up. 

The only difference is Xubuntu came configured to autostart update-notifier. In Lubuntu, it's just an oversight that it is not.

---

### Post by pfeiffep on 2014-05-07
+1>  by @Dennis N [COLOR=#000000]It is not Lubuntu 14.04 only. Xubuntu 14.04 exhibits the same difference in the available upgrades from Software Updater and apt-get or Synaptic. **So the question is why are they different?** [/COLOR] Also affecting Ubuntu 'native'.  

> by @[COLOR=#000000]bapoumba ...[/COLOR] [COLOR=#000000] but all in all GH is as good ...[/COLOR] You're the boss ;-) - AFAIC we can leave it where it is. You have much more experience with the forum than I.

---

### Post by bapoumba on 2014-05-07
> **pfeiffep said:**
> +1 Also affecting Ubuntu 'native'.  

 You're the boss ;-) - AFAIC we can leave it where it is. You have much more experience with the forum than I.

Well, thinking this over, Installation & Upgrade might be better, if you are OK.

---

### Post by pfeiffep on 2014-05-07
> **bapoumba said:**
> Well, thinking this over, Installation & Upgrade might be better, if you are OK.I'm OK with it - but I'm not the OP

---

### Post by linuxyogi on 2014-05-08
I have no issue. If moving the thread helps then please do it.

---

### Post by bapoumba on 2014-05-08
*Thread moved to **Installation & Upgrade**.*
Might get a broader audience here.

---

### Post by bapoumba on 2014-05-08
Here.
Booted up, waited for a while doing other things to see if software-updater would show up, did not, ran apt-get update/upgrade, 3 files to upgrade, from main, started software-updater, let it check the repos, no upgrade suggestions.

I'll dig a bit into software-updater to see if I can come up with the proper wording and traces to add to the bug report.

Edit : linked the bug report here : [https://code.launchpad.net/~ubuntu-core-dev/update-manager/main](https://code.launchpad.net/~ubuntu-core-dev/update-manager/main)
Edit 2 : I also changed te bug report adding trusty to the title.

---

### Post by bapoumba on 2014-05-08
Very good point raised on the lubuntu mailing list : phased updates.
The iputils packages that apt-get sees and not the Software Updater are in the phased updates process : [http://people.canonical.com/~ubuntu-archive/phased-updates.html](http://people.canonical.com/~ubuntu-archive/phased-updates.html)

So this aspect is normal to me now. Will not run the updates through apt-get to see what happens in the next few days.

---

### Post by Dennis N on 2014-05-08
> **bapoumba said:**
> Very good point raised on the lubuntu mailing list : phased updates. ..So this aspect is normal to me now. Will not run the updates through apt-get to see what happens in the next few days.

I tried this between yesterday (see post 32) and today, for what its worth:

Day 1 (yesterday, May 7):
Software Updater showed 5 fewer packages for upgrade than Synaptic.  

Day 2 (today, May 8):
Software Updater increased its list of possible upgrades from 6 to 9, now including 3 of the 5 packages it missed yesterday.
However, Synaptic has now increased its list of upgradable packages from 11 to 14.
So Software Manager remains 5 behind: 2 holdovers from yesterday still not offered, and 3 more newly available from Synaptic but not from Software Manager added today.

No plans to carry this further.
---------------------

Phased Upgrades? Maybe that is it. Apt and Synaptic offer all upgrades from the list of available packages and Software Manager is following a different release schedule. 

My usual practice is to use the panel notification from update notifier only an indication that some upgrades are available. The I use Synaptic to actually do the package upgrades.

---

### Post by linuxyogi on 2014-05-08
Software Updater launched automatically today. I installed whatever was on the list but then whe I did sudo apt-get update/upgrade I found these 

```
The following packages will be upgraded:
  gir1.2-freedesktop gir1.2-glib-2.0 libgirepository-1.0-1
```

---

### Post by Dennis N on 2014-05-09
> **linuxyogi said:**
> Software Updater launched automatically today. I installed whatever was on the list but then whe I did sudo apt-get update/upgrade I found these 
```
The following packages will be upgraded:
  gir1.2-freedesktop gir1.2-glib-2.0 libgirepository-1.0-1
```

I think you will get all the updates eventually using Software Updater. Some may be delayed a few days for reasons that are unclear - Bapoumba in post 39 suggested there may be a phased update process in play here with Software Updater, but how that works is beyond me. Synaptic and Apt do not hold back showing any upgrades so you may see more available.

What I always do when the Software Updater pops up on the panel, is start up Synaptic Package Manager instead, click on the "Mark All Upgrades" Button, then in the popup window - Mark, then Apply. You will get everything Software Updater would send you, and sometimes more. If you prefer to just use the Software Updater, you will have to wait as the same updates appear over the coming days. 

I gather your original problem in post #1 with the Update Notifier not notifying of updates is now corrected? If everything is now working, you could mark the thread solved (use thread tools).

---

### Post by bapoumba on 2014-05-09
Phased updates : [http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)
[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)
[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

Basically, updates are marked to be offered to only a percentage of users, packages are checked against regressions or bugs, then are gradually offered to all users if no problem is encountered. This works with the Software Updater. apt-get does not check for phased updates, so it retrieves anything that can be upgraded from the repos.

---

### Post by Dennis N on 2014-05-09
@bapoumba:

Thanks for the links. Brian's Blog (the first link) explains the general idea quite well and confirms my suspicions in post 32 that Software Updater "works differently." Now I know details as to why and how. I like the error tracker page ([https://errors.ubuntu.com/](https://errors.ubuntu.com/)). Didn't know it existed.

---

### Post by bapoumba on 2014-05-09
> **Dennis N said:**
> @bapoumba:

Thanks for the links. Brian's Blog (the first link) explains the general idea quite well and confirms my suspicions in post 32 that Software Center "works differently." Now I know details as to why and how. I like the error tracker page ([https://errors.ubuntu.com/](https://errors.ubuntu.com/)). Didn't know it existed.
TBH, I discovered it yesterday :)

---

### Post by bapoumba on 2014-05-10
My iputils packages came in Software Updater today.

---

