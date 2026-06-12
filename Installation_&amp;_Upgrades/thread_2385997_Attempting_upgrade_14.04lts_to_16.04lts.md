---
title: "Attempting upgrade 14.04lts to 16.04lts"
date: 2018-02-27
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2018-02-27
I ran sudo apt-get update, then apt-get upgrade, followed by backing up my 14.04 lts, on my RM 32bit laptop, onto an external hdd.

Went to Applications/System Tools/Administration/Software Updater, and ran it.
After it told me that the system was up-to-date, I then hit the Upgrade button.
Gave my password to authenticate, the pop up disappeared and that was the last thing that happened !

I tried it twice, but with the same result, so here I am, with a request for help.

I prefer to go this route, but if I am strongly advised to go by another one, I will gladly follow instructions.

John

---

### Post by kerry_s on 2018-02-27
sudo apt  install update-manager-core
sudo do-release-upgrade

if you can a clean install is always the best way to go.

---

### Post by grey1beard on 2018-02-27
[I]sudo apt install update-manager-core
sudo do-release-upgrade[/I]

Is that what you are referring to as a clean install, or would that the route via a new OS on a disc ?
Thanks for the quick reply, by the way.
John

---

### Post by grey1beard on 2018-02-27
> update-manager-core is already the newest version.
update-manager-core set to manually installed.
> 
john@john-RM:~$ sudo do-release-upgrade
[sudo] password for john: 
Checking for a new Ubuntu release
No new release found

So what next ?
John

---

### Post by kerry_s on 2018-02-27
yeah i meant fresh from disc or usb

maybe it needs a flag, try " man do-release-upgrade " see what the manual says. not sure since i've always done fresh install.
i do remember seeing some using a " -d " for it. aka: sudo do-release-upgrade -d

---

### Post by grey1beard on 2018-02-27
> sudo do-release-upgrade -d  still gives the same 'no new release found', and the man page doesn't show anything that might be useful.

---

### Post by mörgæs on 2018-02-27
If you can live with 14.04 a few months more you can do a fresh install of 18.04, skipping 16.04.

---

### Post by grey1beard on 2018-02-27
At least 16.04 lts has been around for 2 years, so should have any initial problems sorted !

---

### Post by ubfan1 on 2018-02-28
I second/third the new install route, but for the upgrade, take a look at "Software and Updates" under the "other software" tab, turn off any PPA sources (if set).  Then run the update again and try the upgrade.

---

### Post by grey1beard on 2018-02-28
Thanks ubfan1, when my current(v.slow) download finishes, I'll give that a try.
John
EDIT there are also two 'independent' in the list of other software. Should I leave those, or turn those off as well ?

---

### Post by ubfan1 on 2018-02-28
Uncheck everything under the "other software" tab, then after the upgrade, you may set them if you still need whatever they supply.

---

### Post by oldos2er on 2018-02-28
> **kerry_s said:**
> yeah i meant fresh from disc or usb

maybe it needs a flag, try " man do-release-upgrade " see what the manual says. not sure since i've always done fresh install.
i do remember seeing some using a " -d " for it. aka: sudo do-release-upgrade -d

"-d" means upgrade to a development (that is, pre-release) version. You really should warn people about what exactly it does, since not everyone is ok with running alpha or beta pre-release versions, especially LTS users.

---

### Post by cruzer001 on 2018-02-28
To further add to oldos2er post:

If on 16.04 for the -d switch will upgrade to 18.04.  The -d switch will do nothing when used on 14.04.
> -d, --devel-release
              If using the latest supported release, upgrade to  the  development release
The -d switch could be used to version upgrade a LTS before the first point release of the next LTS.
> LTS systems are only automatically considered for an upgrade to the next LTS via do-release-upgrade with the first point release. So for example 14.04 will only upgrade once 16.04.1 is released. If you want to update before, e.g. on a subset of machines to evaluate the LTS upgrade for your setup the same argument as an upgrade to a dev release has to be used via the -d switch.
[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

So just be careful how you use it.

---

### Post by grey1beard on 2018-03-01
Thank you for the cautionary comments, good people.
I do have 16.04 on a usb stick ready for a fresh install, but have yet to take the step of re-ordering my boot up sequence.
One other thing that concerns me is the possible/probable/certain loss of all my 'remembered' passwords on various sites that I am frequently logging in to.
I did suffer the effects of this on a recent 'clear all history' action I took, and then regretted it !
Which of these options will likely occur ?
Many thanks for your help,
John

---

### Post by Irihapeti on 2018-03-01
Sorry to be a bore, but please do a backup before you begin. Many have skipped this and regretted it. :cry:

You could keep your passwords in a password program such as keepass/keepassx. Even if you don't use it for everyday logging in, you at least have a record of them.

---

### Post by grey1beard on 2018-03-01
Thanks for your input.
Yes, as noted in my OP, I have done a back up as the first step, onto an external hdd.
Not familiar with password keepers of any type.
Do I have to type then all in, or does the software automagically extract them with just a couple of clicks ?
John

---

### Post by Irihapeti on 2018-03-01
I know that some of the password keepers allow you to import using a .csv file.

I'm less clear about how to get passwords out of Firefox or other browser; it's been a long time since I've saved passwords in a browser.

---

