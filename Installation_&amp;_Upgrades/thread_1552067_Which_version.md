---
title: "Which version?"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by mike0liver on 2010-08-13
My system hasn't directed me to an automatic update of my Linux OS. Is there some way I can check what version I am currently running?

Also, if I want to upgrade to a later version, what's th best way to go about it?

Cheers,

Mike

---

### Post by surfer on 2010-08-13
```
lsb_release -av
```

gives you the current version.

---

### Post by surfer on 2010-08-13
```
update-manager -c
```
should announce new versions.

---

### Post by mike0liver on 2010-08-23
Thanks. I've checked and the system tells me I'm using Ubuntu 8,04 Hardy. I have run the Update Manager several times and it seems to download a package but I get no opportunity to install that package although I am informed that my system is up to date.

Looks like something is wrong - any ideas?

Cheers,

Mike

---

### Post by carl4926 on 2010-08-23
If you want to upgrade
I would recommend a new install

Just download the latest release and away you go.

---

### Post by mike0liver on 2010-08-23
For somebody who knows what they're doing, that is probably fine but I'm just a relatively new user & non-technical - shouldn't I be trying to find out why my Update Manager doesn't seem to be working properly?

Also, I gather I need to buy a memory stick before I can download the update - is that absolutely necessary?

Regards,

Mike

---

### Post by kansasnoob on 2010-08-23
So, you don't think you're even getting regular updates?

If so please post the output from terminal of:

```
cat /etc/apt/sources.list
```

That may show us why. I'd want to be sure your OS is updated properly before trying to upgrade. Quote from official documentation:

> Be sure that you apply all updates to your current version of Ubuntu before you upgrade.

Regarding distro upgrades I always like to be prepared for the worst just in case things go terribly wrong. So I either create a backup of everything important before beginning, or I have a plan in place to retrieve that data if need be.

That "plan" can vary greatly depending on the machine specs, amount of data (including app. profiles like Firefox, Thunderbird, Evolution, etc) that needs to be saved, etc, etc. Sometimes it's as simple as using a CD-R or DVD+/-R, other times I use a flash drive, and still others I use an actual external hard drive and clone whole partition(s).

Also I'd never upgrade without first trying the Live CD of the distro I'm upgrading to, in this case Ubuntu 10.04.1:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Also. if the upgrade would then fail, you'd have new installation media to sort things out. If the Live CD won't run on your hardware it'd be best to know why and figure out any potential work-arounds first ;)

Please take time to read more here:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by lechien73 on 2010-08-23
Not *the* now-famous [Michael Oliver]("http://uri.tl/15")...surely? :)

Are you running Ubuntu on a Dell netbook or something like that? Some hardware vendors supplied a customised version of Ubuntu, in which case you would be better off with a fresh install.

The contents of your /etc/apt/sources.list file, as requested above, will explain all.

---

### Post by rykel on 2010-08-23
Hi, I am trying to figure out if I am running Lucid 10.04 or 10.04.1.

How do I find out?

---

### Post by rykel on 2010-08-23
Hi, I found my answer by chance. I switched to another screen (Ctrl-Alt-F3) and it says Lucid 10.04.1. Thank you!

---

### Post by mike0liver on 2010-08-23
No, I don't think I'm getting regular updates. The terminal output reads:
"mike@TOSHIBA-User:~$ cat /etc/apt/sources.list
deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted"

I'll check out the other links you provided - thanks.

Mike

---

### Post by mike0liver on 2010-08-23
If you mean am I the youngest Premiership ref - no. I may well be the oldest ex-ref but certainly not the youngest :-)

I have a Toshiba NB100 Notebook and had to do a re-install from the recovery disk supplied when I lost my audio on installing Ubuntu V 9. I hsven't had the courage to do another upgrade until now but decided I ought to take the plunge. I am totally non-tech as far as Linux us concerned and feel completely at sea with the way everyone seems to expect me to know what they are talking about when I ask a question. I have to say, however, that this current thread doesn't fall into that category so far.

My big worry is that I'll have another problem with the audio when I upgrade this time and will have to go back to square one again!

Cheers,

Mike

---

### Post by mike0liver on 2010-08-23
I've checked out the update info given on the links you provided and am totally confused. It all seems so complex. All I want to do is upgrade to the latest version of Ubuntu suitable for my Toshiba NB100 Noteook but it seems there are all kinds of hoops to jump through.

Is there some kind of Idiot's Guide I can consult?

Cheers,

Mike

---

### Post by mike0liver on 2010-08-26
Was the info provided in post #11 of any use?

Mike

---

