---
title: "automatic updates"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-04-13
this linux machine will be mostly unattended since students will be using it and their account will be without any SUDO,ADMIN... priviliges.So I would like that all of the UPDATES would be automaticly installed without any user intervention.

Now I believe this could be best achived thru a CRON JOB. Please correct me if am wrong. How would I set it up then??

---

### Post by rcarnevale on 2006-04-13
Perfect... My server makes

CRON.TAB:

0 3     * * *   root    apt-get update
0 4     * * *   root    apt-get dselect-upgrade -y

---

### Post by ashrack on 2006-04-13
this is how I did it:
```
export EDITOR=gedit && sudo crontab -e
50 18 * * * root apt-get update
0 19 * * * root apt-get dselect-upgrade -y
```

it is now 19:15 and nothing happened. What did I do wrong??

---

### Post by ashrack on 2006-04-15
anyone?

---

### Post by strider1551 on 2006-04-24
Try replacing root with sudo:
```

50 18 * * * sudo apt-get update
00 19 * * * sudo apt-get dselect-upgrade -y

```

There might still be some issues, though.  The discussion in [this thread]("http://www.ubuntuforums.org/showthread.php?t=102927") seems to indicate that some packages will return error messages because they ask more than the normal permission to install.  I'm not sure what the difference is between dselect-upgrade and dist-upgrade.

---

### Post by ashrack on 2006-04-25
weird. for some strange reason the link Uve given me:
http://"http//www.ubuntuforums.org/showthread.php?t=10292
gets me to [www.microsoft.com](www.microsoft.com). How is that possible??

ps. this link works ok.  [http://www.ubuntuforums.org/showthread.php?t=10292](http://www.ubuntuforums.org/showthread.php?t=10292)

---

### Post by strider1551 on 2006-04-25
Heh.  That's pretty funny.  I'll go back and edit the post.

Wow.  It wasn't even linking to the right thread.  That's the last time I don't check my links!  I meant to send you [here]("http://ubuntuforums.org/showthread.php?t=102927")

---

### Post by nocturn on 2006-04-25
There's a good chance that Dapper will have this functionality built-in.
You will need to enable it on each computer though.

---

### Post by nocturn on 2006-04-25
Incidently, I had been looking at the auto-update problem some time ago.

The safest way to do this is to use one of the good scripts on this forum for this, but not from cron but rather invoke it from init on the shutdown of the machine.

That way, you limit the chance of breakage during the operation of the machine and move it to the next boot.

---

### Post by mbrubeck on 2006-04-26
Yes, the Dapper version of update-manager has an automatic update feature built in.  You have to enable it in the update-manager preferences ("software-properties"):

[https://launchpad.net/distros/ubuntu/+spec/unattended-package-upgrades](https://launchpad.net/distros/ubuntu/+spec/unattended-package-upgrades)

---

