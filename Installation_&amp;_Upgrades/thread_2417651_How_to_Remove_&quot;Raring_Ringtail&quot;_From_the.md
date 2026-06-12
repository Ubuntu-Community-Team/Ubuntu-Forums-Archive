---
title: "How to Remove &quot;Raring Ringtail&quot; From the Source List?"
date: 2019-04-25
forum: Installation &amp; Upgrades
---

### Post by braznyc on 2019-04-25
I get this error message when I try to upgrade to 19.04

[COLOR=#000000][FONT=monospace]E: The repository 'http://archive.canonical.com/ubuntu raring Release' no longer has a Release file. [/FONT][/COLOR]
[FONT=monospace]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/FONT]

I've already edit the software sources list and removed all the entries that have "raring ringtail".


Is it hidden in a secret directory? How can I find it and remove it from the system?

[FONT=monospace]
[/FONT]

---

### Post by deadflowr on 2019-04-25
Check the 3rd party repository directory /etc/apt/sources.list.d/
I've seen newer installs add that particular entry there.
It'll probably list the file as something like raring-partner.list.

---

### Post by braznyc on 2019-04-25
Hello, deadflowr,


I have all these listed there. Should I delete them all?

/etc/apt/sources.list.d/canonical-chromium-builds-stage-raring.list
/etc/apt/sources.list.d/canonical-chromium-builds-stage-raring.list.distUpgrade
/etc/apt/sources.list.d/canonical-chromium-builds-stage-raring.list.save
/etc/apt/sources.list.d/chromium-daily-stable-raring.list
/etc/apt/sources.list.d/chromium-daily-stable-raring.list.distUpgrade
/etc/apt/sources.list.d/chromium-daily-stable-raring.list.save
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-raring.list
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-raring.list.distUpgrade
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-raring.list.save
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-raring.list
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-raring.list.distUpgrade
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-raring.list.save

---

### Post by deadflowr on 2019-04-25
Sure. Go ahead and remove them.
Then check launchpad to see if those have versions for the new release you're on.

This one does:
[https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage]("https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage")

This one does not:
[https://launchpad.net/~chromium-daily/+archive/ubuntu/stable]("https://launchpad.net/~chromium-daily/+archive/ubuntu/stable")

This one does:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa")

And this one doesn't have a disco archive yet, so hold off:
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa")
But expect the last one to get a disco archive soon.

---

### Post by braznyc on 2019-04-25
All disabled and still can't upgrade to 19.04

[FONT=monospace][COLOR=#000000]"Checking for a new Ubuntu release[/COLOR]
New release '19.04' available.
Run 'do-release-upgrade' to upgrade to it.
Satellite-A305:~$ do-release-upgrade                       
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading"
...

[/FONT][FONT=monospace][COLOR=#000000]Satellite-A305:~$ sudo apt update && sudo apt dist-upgrade

... And again

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]Satellite-A305:~$ do-release-upgrade                       [/COLOR]
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

Nothing happens. 
[/FONT][FONT=monospace]
[/FONT]

---

### Post by deadflowr on 2019-04-25
What release is it to begin with?
And what option is it set to upgrade for?
(Setting options for upgrades are either any new release or long term supported releases or none)

---

### Post by braznyc on 2019-04-25
Notification set to "Any New Version".

---

### Post by oldos2er on 2019-04-25
Try  ```
sudo apt full-upgrade  
```

---

### Post by braznyc on 2019-04-25
> **oldos2er said:**
> Try  ```
sudo apt full-upgrade  
```


Hello, Oldos2er.

I did that and it worked, thanks guys!

---

### Post by oldos2er on 2019-04-26
Great! Would you please mark your thread 'Solved' under Thread Tools at the top of the page? Thanks.

---

