---
title: "Thunderbird 8"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by subehsharma on 2011-11-10
Thunderbird ver 8 has been out now. ANybody knows hows to upgrade the current version to it?

---

### Post by subehsharma on 2011-11-11
Anyone???

---

### Post by BillyBoa on 2011-11-11
You could install Mozilla PPA and upgrade

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by subehsharma on 2011-11-11
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

---

### Post by sikander3786 on 2011-11-11
That PPA isn't meant for Ubuntu 11.10, only the older releases.

As Ubuntu 11.10 comes with Thunderbird by default, there is no need for a PPA. Thunderbird 8 will be available in the official Oneiric repositories soon and then you can simply use Update Manager to upgrade to Thunderbird 8.

You can keep an eye on the availability of Thunderbird 8 by visiting this page:

[http://packages.ubuntu.com/search?keywords=thunderbird&searchon=names&suite=oneiric&section=all](http://packages.ubuntu.com/search?keywords=thunderbird&searchon=names&suite=oneiric&section=all)

Notice, it states "7.0.1+build1+nobinonly-0ubuntu1: amd64 i386" currently.

What you need to do now is to go to Ubuntu Software Center > Edit > Software Sources > Other Software Tab and _Remove_ the entries for Thunderbird PPA you've just added. If you don't remove it, the above errors would keep bugging you forever, literally. :D

---

### Post by subehsharma on 2011-11-11
Thanks Sikander. I've removed them. The only reason i'm desperate to go onto version 8 is because ver 8 supports Lightning. Do you happen to know any workaround for this issue?

---

### Post by sikander3786 on 2011-11-11
> **subehsharma said:**
> Thanks Sikander. I've removed them. The only reason i'm desperate to go onto version 8 is because ver 8 supports Lightning. Do you happen to know any workaround for this issue?
You are Welcome. :)

Workarounds would be a bit ugly unless it is available in the official repositories.

If you are eager enough to try Thunderbird 8, please take a look at my blog post here:

[http://www.tuxgarage.com/2011/08/thunderbird-6-stable-released-ubuntu.html](http://www.tuxgarage.com/2011/08/thunderbird-6-stable-released-ubuntu.html)

See the section 'Other Linux' and replace '6.0' with '8.0' in all the instances. You are free to decide if you want to go for a Temporary or a Permanent solution. Both are listed there.

---

### Post by subehsharma on 2011-11-11
I installed Xubuntu in my Office laptop so Lightning is very important for me to keep my schedules and meetings. I am already have implemented your "Temporary Solution" with thunderbird 8 and i guess i'll just have to keep using it till Ubuntu's repo upgrades it. Thanks anyway.

---

### Post by ottosykora on 2011-11-11
yes but any Thunderbird since version 2.x or so support lightning, I have lightning on all versions installed and all works fine, so what is the problem with version 8?

---

### Post by subehsharma on 2011-11-11
Problem is lightning is not available on 7. its working on 8.

---

### Post by harshen_r on 2011-11-13
[B]Hi, do the following in terminal:

sudo apt-add-repository ppa:mozillateam/thunderbird-next[/B]
**sudo apt-get update**
[B]sudo apt-get upgrade


[/B]

---

### Post by ottosykora on 2011-11-13
sure it is, lightning is available for any version , I have it on 7.x and 3.x and 2.x and 8

Had not problems with that. You just have to take the right version for each version of TB

---

### Post by subehsharma on 2011-11-13
Thanks Ottosykora. You're right it is available although a little difficult to find on mozilla's website but it was there :-) Thanks.

---

### Post by lores on 2011-11-22
I really don't understand why there seems to be no single repo with Thunderbird 8 (64 bit and stable, not -next) for Ubuntu 11.10 after TB has been available for so long... Especially now that there is a tb-stable repo for the older releases of Ubuntu... Really annoying!

---

### Post by teejay17 on 2011-11-28
...still no Thunderbird 8 in the Oneiric official repositories. Are they planning on skipping 8 completely and just waiting for 9?

---

### Post by lores on 2011-11-28
Hm, I've recently (finally!) gotten the upgrade to 8.0+build1-0ubuntu0.11.10.1 (repo: Ubuntu).

---

### Post by teejay17 on 2011-11-28
> **lores said:**
> Hm, I've recently (finally!) gotten the upgrade to 8.0+build1-0ubuntu0.11.10.1 (repo: Ubuntu).
Yes, it finally arrived today.

---

### Post by lores on 2011-11-28
Hm, I got it on 24.11.11.

---

### Post by subehsharma on 2011-11-29
> **teejay17 said:**
> ...still no Thunderbird 8 in the Oneiric official repositories. Are they planning on skipping 8 completely and just waiting for 9?

Got the update today through System update.

---

### Post by evertmantel on 2011-11-29
Got the update as well: 
Lightning works, but suddenly I cannot write to the GMail calendar anymore.. Anyone an idea why?

:confused:

---

### Post by evertmantel on 2011-11-29
Ok I figured it out myself: 
the extension for Google calendar had not been updated yet to 0.9.

After some fiddling, the world was rosy, nice and great again..

---

### Post by teejay17 on 2011-11-29
> **lores said:**
> Hm, I got it on 24.11.11.
For 11.10? Is that 32 bit or 64 bit? My update, on the 29th, was on 11.10 64 bit.

---

### Post by teejay17 on 2011-11-29
Here's a good article explaining that we shouldn't have to wait too long for Thunderbird updates in the future: [http://www.h-online.com/open/news/item/Ubuntu-will-now-track-Mozilla-updates-1386831.html](http://www.h-online.com/open/news/item/Ubuntu-will-now-track-Mozilla-updates-1386831.html)

---

### Post by tattanke on 2011-11-29
evertmantel: how did you fix you problem with google calendar?

---

