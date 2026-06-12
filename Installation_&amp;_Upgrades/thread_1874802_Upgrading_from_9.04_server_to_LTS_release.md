---
title: "Upgrading from 9.04 server to LTS release?"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by jasonmaha on 2011-11-03
I recently plugged in my old Ubuntu server which had been shelved for quite some time. It's still running 9.04, which of course was dropped from support a long time ago.

I'd like to get it upgraded to an LTS release so I can continue getting security updates for packages. I don't want to go through the headache of a complete reinstall since I have a ton of custom configurations, scripts, etc., for which I don't have time to take account.

Is there any way to upgrade this 9.04 box to an LTS release or am I dead in the water?

Thanks,
jasonmaha

---

### Post by Silvernail on 2011-11-03
Make that 2 users who have the same question.

---

### Post by overdrank on 2011-11-03
Hi and this may help [_EOLUpgrades_]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by MAFoElffen on 2011-11-03
> **jasonmaha said:**
> I recently plugged in my old Ubuntu server which had been shelved for quite some time. It's still running 9.04, which of course was dropped from support a long time ago.

I'd like to get it upgraded to an LTS release so I cancontinue getting security updates for packages. I don't want to go through the headache of a complete reinstall since I have a ton of custom configurations, scripts, etc., for which I don't have time to take account.

Is there any way to upgrade this 9.04 box to an LTS release or am I dead in the water?

Thanks,
jasonmaha
Post #3 may give you some help, but will get you upgraded to whatever is the current now = 11.10.. 

This info is closer to what both of you are looking for (to upgrade to an LTS release):
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Pay special attention to this part:
> Note: The minumum contents of  /etc/update-manager/release-upgrades should be
```


[DEFAULT] Prompt=lts
```

That method is installing the upgrade-core and using options on do-release-upgrade, with the configuration file set to an LTS release.

Another method (described there) is to mount an 10.04 LTS Alternate Install CD (or ISO file) and starting the cdupgrade script.

---

### Post by jasonmaha on 2011-11-08
Thanks for the links. Unfortunately it looks like the network-based upgrade path doesn't work anymore. Both of the upgrade guides involve using the 'do-release-upgrade' tool to switch to the newer release.

```

$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

```

Bummer. It looks like a CD-based install is the only option.

Thanks,
jasonmaha

---

### Post by BillyBoa on 2011-11-08
A suggestion. If you can wait, just do the upgrade in April 2012 when the new LTS release is coming.

---

### Post by jasonmaha on 2011-11-09
Thanks for the suggestion. I'll hold off for now.

Regards,
jasonmaha

---

### Post by MAFoElffen on 2011-11-09
> **jasonmaha said:**
> Thanks for the suggestion. I'll hold off for now.

Regards,
jasonmaha
On the link I posted there was an non-internet upgrade using the Alternate Install CD of the version you want to upgrade to... I know that works for Desktops... not sure on for Server.

***But, If you were going wait to re-do a  new "fresh install" anyway... You could install any version you want to.  I have 3 servers on Oneiric 11.10 and 2 more that I'm testing Precise 12.04 on.  What I've found on testing dev-versions since 9.10 is that Desktop Editions have many changes and subsequent growing pains surrounding that... Whereas, Servers... testing them is without much problems... 

The Server Edition versions between 10.04 and present are very stable (even with 12.04 which is currently pre-alpha, about to go alpha.)

---

### Post by jasonmaha on 2012-02-13
I've had some success. I randomly stumbled across this thread today:

[http://echenh.blogspot.com/2010/04/how-to-upgrade-ubuntu-server-904-to-910.html](http://echenh.blogspot.com/2010/04/how-to-upgrade-ubuntu-server-904-to-910.html)

I tweaked the instructions on this page, since I'd made some changes to the **/etc/apt/sources.list** file to accommodate the fact that I'm using an old release.

Step 1 is to modify **/etc/apt/sources.list** and switch 'jaunty' to 'karmic'. It's important to have the old-releases sources in there, since we're working with an unsupported release:

```

# Required
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

# Optional
deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

```

I then followed the steps outlined in Edward's blog post:

```

$ sudo apt-get update

$ sudo apt-get upgrade 

$ sudo apt-get dist-upgrade

```

After this completed, I rebooted my server, and lo and behold, my server has been upgraded to Ubuntu 9.10.

```

$ sudo cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

My next step is to get this server updated to Ubuntu 10.04 LTS. I'll post with my progress as I head down that road.

---

### Post by jasonmaha on 2012-02-13
Now that I'm running 9.10 and am on my way to 10.04 LTS, I want to stick with 'LTS' upgrades from here on out, so I modified **/etc/update-manager/release-upgrades**:

```
Prompt=lts
```

Next, I found that the **do-release-upgrade** method still doesn't work for the also unsupported 9.10 release. So I made another change to **/etc/apt/sources.list**. I switched all occurrences of "karmic" to "lucid" and changed the "old-releases" URLs to "us.archive" (If this creates duplicate lines, you can delete the duplicates).

```
# Required
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse

# Optional
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
```

Then, I proceeded down the same upgrade path that I used to switch from 9.04 to 9.10:

```
$ sudo apt-get update

$ sudo apt-get upgrade 

$ sudo apt-get dist-upgrade
```

When performing **sudo apt-get dist-upgrade**, I got an error indicating that 'util-linux' could not be configured via Immediate Configure. I re-ran the command with this setting:

```

$ sudo apt-get dist-upgrade -o APT::Immediate-Configure=0

```

Note that during the upgrade and dist-upgrade processes, you'll need to reconcile config files occasionally. I didn't have any catastrophic conflicts--generally, viewing the diffs made it quite clear as to whether I needed to keep my config file or accept the new one from the package manager.

Voila:

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

```

SSH still works (I did this whole process remotely), as do most of the tools I regularly use (GNU screen suddenly isn't working properly; it looks like it was replaced by "byobu" in this version so my .bashrc needs to get updated).

I'm feeling pretty good about this process. No guarantees it will work for you, but this was a pretty smooth transition for me. The whole thing took about 5 hours, but it required very little attention from me as most of that time was waiting for packages to install.

---

### Post by jasonmaha on 2012-02-14
Just a quick follow-up to this thread: my upgrade process went smoothly, and a day later, I've had no issues with the system. I didn't need to reconfigure anything; all my server applications are still running. The only change I had to make was switching to *byobu* from *screen*.

I just received my first security update today. It's great to have this system up to date again.

---

