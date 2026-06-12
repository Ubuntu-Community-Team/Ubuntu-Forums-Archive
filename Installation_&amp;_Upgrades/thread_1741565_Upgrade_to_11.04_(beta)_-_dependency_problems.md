---
title: "Upgrade to 11.04 (beta) - dependency problems"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Drengur on 2011-04-28
Because of other problems [http://ubuntuforums.org/showthread.php?t=1719249]("http://ubuntuforums.org/showthread.php?t=1719249") I decided to try the 11.04 beta a couple of days back. 

Upgrade went fine for most parts but when I rebooted I found that neither the mouse nor keyboard were working. Unplugging and plugging back in activates these devices.

After starting up I found that many things were missing. I did a apt-get update and upgrade and found that the system was unable to install some 200 packages because of dependency problems. I tried doing a build-dep and that worked for a few packages but the remaining packages are being held back. (192 or so)

Because of the older problem I mentioned above I am unable to paste all of the relevant package information in here but the most common dependency problem seems to be something called "plymouth". I could type those in if relevant.

Does anyone have any ideas before I do a clean install? (I would rather not have to go down that road - as I suspect my problem has not been fixed with 11.04 - which means it would be an upgrade followed by a downgrade to 10.04)

Thank you for your help.

---

### Post by KegHead on 2011-04-28
Hi!

I use the following;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

KegHead

---

### Post by Drengur on 2011-04-28
Thank you.

I had done all of the aforementioned except the last part. It fetched a new image, which broke my x (switched from nvidia to nv to fix it) but everything remains quite the same.

```
0 upgraded, 0 newly installed, 0 to remove and 279 not upgraded.

```

As my mouse/keyboard seem to be fine at the moment I can paste the output from the automatic update manager in Gnome: ```
 Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
```

---

### Post by mörgæs on 2011-04-28
Blessaður

As the error message says, it would be good to have the error reported, so it can be corrected: 

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Drengur on 2011-04-28
Sömuleiðis Mörgæs!

I will do that to the best of my abilities.

---

### Post by dino99 on 2011-04-28
nothing better than a fresh clean install

---

### Post by Drengur on 2011-04-28
The bug report provided a result:

> The upgrade is blocked by xorg-edgers ppa. Can you please install ppa-purge and downgrade to the official ubuntu package before trying to upgrade again to natty.

Now, I have installed ppa-purge, but I am unable to downgrade the "xorg-edgers".

```
sudo ppa-purge xorg-edgers
``` provides me with ```
drengur@drengur-MS-7100:~$ sudo ppa-purge xorg-edgers
Updating packages lists
PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa

```

I checked the /etc/apt/sources.list and could not find any reference to this source there...

As I understand it I should have done this BEFORE upgrading. I will now mark this thread as solved and try another distro (because of the other problem I was having). Thank you for your help.

---

### Post by KegHead on 2011-04-28
Hi!

Maybe todays updates to final will solve your problems.

KegHead

---

### Post by mafitzpatrick on 2011-04-28
For what it's worth I had a similar problem before (not with this upgrade). What has happened is you have added a ppa, upgraded, then removed the ppa. The installed packages are still there unless you do a purge.

When I had this problem, the (somewhat counterintuitive) solution was to re-add the ppa, and then ppa purge the same ppa. This provides ppa-purge with the package information required to do the downgrade.

You should then be able to complete the upgrade normally.

Hope this helps

---

### Post by mörgæs on 2011-04-28
This seems to get into a long and risky process. Before spending too much time, keep in mind that a clean install will most likely solve the problem, as Dino99 suggested.

---

### Post by mafitzpatrick on 2011-04-28
Sorry, did I post this on Windows forum by mistake? Reinstall! Reinstall! ;)

In all seriousness, for fixing the OPs system its kind of moot (looks like they're doing the distro dance), my intent was to explain why the problem occurred so it can be avoided. This will happen on any system where you add ppa, upgrade, remove ppa without purging.

Reinstalling helps now, but unless you find out why its going to be the same story every 6 months. I'll file a bug

---

### Post by Drengur on 2011-04-29
I reinstalled. I tried Fedora in between and the problem I am having is the same with Fedora. It seems to be a xorg problem(?).

I am now in a freshly installed 11.04. Logging twice into Ubuntu Classic seems to be a temporary fix for my focus problem. (loggin in and straight out again). I wouldn't be using unity anyways ;)

---

