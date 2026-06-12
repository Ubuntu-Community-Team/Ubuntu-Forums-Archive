---
title: "firefox deb respositories for 22.04 not working?"
date: 2022-05-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-05-19
All attempts this (19 May EDT) evening to download deb version of firefox for 22.04 have timed out.  Has the deb-version been withdrawn?

John

---

### Post by deadflowr on 2022-05-19
What repository?

---

### Post by cigtoxdoc on 2022-05-19
Both mozillateam/ppa and ppa:phd/firefox .  Tried two differnt PC's.  No problems with any other downloads and greater than 100 Mbps download speed.

---

### Post by cigtoxdoc on 2022-05-21
I got the mozillateam/ppa to work this morning and tried it on of three pc's running Ubuntu Unity 22.04.  It loaded 91.9.1esr (64-bit).  It works and stays locked to launcher.  One website has already told me that I need to update Firefox to current version [100.0.1 (64-bit)].  So, what are the plans of mozxillateam to update Firefox esr?

John

---

### Post by #&amp;thj^% on 2022-05-21
I'm not sure whats going on in yours but mine shows:
```
apt policy firefox
firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
     100.0.2+build1-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages

```

---

### Post by cigtoxdoc on 2022-05-21
I have also added the ppa phd/firefox to one of my systems.  It shows up in the respositories under synaptic.  It does not want to install however.  Am I missing something?  Perhaps I failed somewhere in removing the snap version.  I wouls appreciate some step-by-step help.

Thank you,

John

---

### Post by #&amp;thj^% on 2022-05-21
I'm not sure you'll want to follow my path, IE
```
snap list firefox
Command 'snap' not found, but can be installed with:
sudo apt install snapd

```
Snap free on this system.
> Warning: These steps will remove Software and Firefox, the two critical applications in your Ubuntu system. 
Make sure you take backups of bookmarks and other Firefox settings before trying these steps.
If your unsure about the snap removal try again:
```
sudo snap remove --purge firefox
sudo snap remove --purge snap-store
```
Again I warn about my suggestions about snap/s
```
sudo apt remove --autoremove snapd
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'snapd' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
If your wondering about any fallout, I have no complaints on my end.

---

### Post by deadflowr on 2022-05-21
If on ESR then it'll take weeks to months before it hits version 100+.
That is the whole point of ESR.
>  So, what are the plans of mozxillateam to update Firefox esr?

Looks Mozilla plans on updating it to 102.0 in June.
Reference: [https://wiki.mozilla.org/Release_Management/Calendar]("https://wiki.mozilla.org/Release_Management/Calendar")

However, it's unclear when Ubuntu's mozillateam PPA will move over to it because the ESR release will have two running in tandem for a little while.
(Both version 91 and 102 will run together until September)

If I were to venture a guess the PPA will stay on 91 until they have to move it up.
So I would expect it to stay at 91 until September.
But who knows, maybe they'll update it quicker.

---

### Post by cigtoxdoc on 2022-05-21
RE: ppa:phd/firefox.

A I mentioned earlier, ppa was already in synaptic.

In [https://launchpad.net/~phd/+archive/ubuntu/firefox](https://launchpad.net/~phd/+archive/ubuntu/firefox) there are several lines of code that I had missed:

echo '
Package: *
Pin: release o=LP-PPA-phd-firefox
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/phd-firefox

That didn't solve the problem for me.  I had to go into synaptic ans completely remove the snap version of firefox.

Then I had to load the version from phd-firefox.

It install version 1000.2 (non snap)

If anyone has a better way of doing this, I hope they post it.  Also have to get rid of mozilla-team version on another PC.

John

---

### Post by #&amp;thj^% on 2022-05-21
I use a different PPA: [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)
up to you, both ESR and current firefox resides there.

---

