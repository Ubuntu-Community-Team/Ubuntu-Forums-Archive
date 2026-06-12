---
title: "Ubuntu 19.04 Upgrade"
date: 2019-04-18
forum: Installation &amp; Upgrades
---

### Post by bionic3epl on 2019-04-18
What time is the Ubuntu 19.04 upgrade supposed to go Live so the Software Updater can detect it and Upgrade my PC?

---

### Post by sasafrass452 on 2019-04-18
I'd like to know the same thing! No notification on my end yet.... I'm guessing we just have to be patient, & the notification will come when it's ready.

---

### Post by deadflowr on 2019-04-18
It's available.
You might read the release notes to see what needs to be done.
[https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes#Upgrading_from_Ubuntu_18.10]("https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes#Upgrading_from_Ubuntu_18.10")

---

### Post by pzmosquito on 2019-04-18
No it's not available yet. I followed instruction exactly, it just doesn't have the new release available.
[ATTACH=CONFIG]283050[/ATTACH]

---

### Post by sasafrass452 on 2019-04-18
Still nothing on my end, either.... I'll give it a bit longer....

---

### Post by Impavidus on 2019-04-18
Depending on how fast the upgrade process is tested, whether everything works, how fast the mirrors are updated, how fast the upgrade for 18.10 enabling the upgrade to 19.04 is installed... I can't really say when the upgrade will be available, but it may take a few days. Are you in a hurry? I usually wait between one and two months after release before I upgrade, so that the most annoying bugs are gone.

---

### Post by deadflowr on 2019-04-18
I see this:
[ATTACH=CONFIG]283051[/ATTACH]

As to why it's not showing up for others,
Might be a mirror issue.
Might be software updater and phased-updates issue.
Might be any number of reasons.
But it's available.

Edit: From memory, the last time the upgrader option wasn't available when a new version was released  it was reflected in the release notes stating that the upgrader option will be available 
at some time in the future. I believe that was for the 18.04.1 release since that was the one that opened up the 18.04 channel for 16.04 upgrades. And it needed a bit more work since the whole thing was a big change overall.
But in general whenever a new version is officially released the upgrade channel gets opened.
If it's not open they reflect that in the release notes.

---

### Post by jdeca57 on 2019-04-18
```
 jdc@johan-Latitude-E6430:~$ cat /etc/issue
Ubuntu 19.04 \n \l


```

---

### Post by jerry47 on 2019-04-18
I just upgraded an hour ago. Had to do it manually. Press Alt+F2. Type "/usr/lib/ubuntu-release-upgrader/check-new-release-gtk" Came from [https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes](https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes) It took several tries before it appeared.

---

### Post by dre2fresh on 2019-04-18
here's a link to the iso file:[http://releases.ubuntu.com/19.04/](http://releases.ubuntu.com/19.04/) I don't know when the update will come out the (p.s 19.04 is 64bit only, well at least for the iso)

---

### Post by Impavidus on 2019-04-19
I guess I had to wait until I got an upgrade to system-info-data. You must have installed all available upgrades fro 18.10, including that one, before you can attempt the release upgrade. Read the release notes before you upgrade. And again, I'll wait until it's June or thereabouts.

The 32 bit live disk was dropped for Ubuntu earlier, but now the light flavours dropped it too.

---

### Post by DAVID_LECKIE on 2019-04-20
I have 19.04 Beta (post 01/04/2019) I assume the upgrade  to the release version will be automatic?
Dave

---

### Post by deadflowr on 2019-04-20
> **DAVID_LECKIE said:**
> I have 19.04 Beta (post 01/04/2019) I assume the upgrade  to the release version will be automatic?
Dave
Yes.
When a release becomes official and out of development they update the base files to reflect it's no longer a development version.
You'll that with a regular update.

Do you still see it showing as beta/development somewhere?

---

### Post by zachalexy on 2019-04-20
I was (maybe still am) on 19.04 beta. lsb_release showed "development branche". But now, without upgrading to the final 19.04 the label "development branche" is gone. So I take I'm on the final 19.04 now via a regular update too? Didn't know it works this way. Also thought I had to really upgrade again. Regards, Zach

---

### Post by mcsheffrey on 2019-04-20
Go into terminal mode and type in:  [COLOR=#383838][FONT=Monaco]sudo do-release-upgrade -c
and bingo it starts the upgrade.[/FONT][/COLOR]

---

### Post by zachalexy on 2019-04-20
Not for me!

---

### Post by DAVID_LECKIE on 2019-04-29
Hi
It just says 19.04 .
It did a fairly big update a couple of days ago.
When I check for updates it says its up to date.

I guess I am now running the release version.

Dave

---

### Post by bionic3epl on 2019-05-01
if I want to, How do I upgrade to 19.04 from 18.04 using the Software Updater?

---

### Post by Impavidus on 2019-05-01
You don't, at least, not yet.

When set to upgrade to any new release (not only LTS), Ubuntu 18.04 offers to upgrade to 18.10. It will offer the upgrade to 19.04 after 18.10 reaches end of life. You'll have to wait a little under 3 months.

---

### Post by bionic3epl on 2019-05-01
Okay

---

