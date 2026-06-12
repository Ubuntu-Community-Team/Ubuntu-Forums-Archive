---
title: "How to upgrade and use apt-proxy"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Archmage on 2008-04-23
I'm always having a problem when upgrading to a new release. Maybe this time someone can finally help me.

I'm using apr-proxy to download the packages for my ten machines. This is working quite well. I have a slow internet-connection, but since I only only need to download the packages once this is still quite fast.

My source.list looks something like this:

```

deb http://APTPROXY:9999/ubuntu dapper main restricted universe multiverse
deb http://APTPROXY:9999/ubuntu-security dapper-security main restricted universe multiverse

```

The problem is, that if I use the Update Manager or the "sudo do-release-upgrade" it will always change my source.list to something like this:

```

deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

Resulting that I need to download ALL the packages on ALL the machines over the internet one by one.

Instead of fetching the packages in **15 minutes** from my local apt-proxy server they will download the packages over the internet in **5 days** for each machine. That means that the whole update proces will take **50 days** instead of **15 minutes**, since the internet is so slow and I don't have a CD-Rom acces on these machines.

Is there any way to do a upgrade that will leave my sources.list intact (or simply change the *dapper* to *hardy* entry) and than get the packages from my local apt-proxy server?

---

### Post by paxmark1 on 2008-04-23
Wow.

apt-proxy looks like a very interesting and powerful command.  I don't seem to have a manual for it on my system.  But I see it has Debian and Ubuntu documentation on the web.  Very strong little command.

[http://www.nabble.com/dapper-to-hardy-upgrade-td15582253.html](http://www.nabble.com/dapper-to-hardy-upgrade-td15582253.html)

[http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/](http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/)

To change all references from dapper to hardy you can edit your source list via hand or use the  sed command.
 

I am not a guru, but I can't help but noticing dapper in your /etc/apt/sources.list.  But the above mentioned url's says that it will work for the server version.

The x-windows versions  dist-upgrade usually only works from one version to the next.  

I could be wrong, but I if you are not running servers I believe you would have to dist-upgrade first to edgy, then upgrade to feisty, then to gutsy, then to hardy.

peace Mark

---

### Post by paxmark1 on 2008-04-23
sorry, I live in Kubuntu land.  I am wrong.

Ubuntu 8.04 is a long term release.  Kubuntu is not.

---

### Post by Archmage on 2008-04-23
> **paxmark1 said:**
> apt-proxy looks like a very interesting and powerful command.  I don't seem to have a manual for it on my system.  But I see it has Debian and Ubuntu documentation on the web.  Very strong little command.

If you have more than one PC in your network, than I would recommend this. No need to redownload packages. Once there are downloaded by one system the other can get it at once. The only problem are the dist-upgrades.

> 
To change all references from dapper to hardy you can edit your source list via hand or use the  sed command.

Well, the problem is, that the update manager might also change something else. I remember when changing to gusty, if you haven't turn off something that was on since edgy than your whole system would be incredible slow. So only changing dapper to hardy might bring additional problems. (But 49 days, 23 hours and 45 minutes less downloading time.)

---

### Post by tyblu on 2008-04-25
Was this resolved?

---

### Post by Archmage on 2008-04-25
> **tyblu said:**
> Was this resolved?

Unfortunatly not. I'm upgerading my first machine. Downloading will take round about 10 days (because of the high serverload).

After that I have 9 more machines in front of me that will take 5 days each to download the upgrade.

So if someone know how I can do the upgrade over my apt-proxy-server and not via internet, I would be very happy.

---

### Post by ptcbus on 2008-04-25
You can try downloading the torrent file. It is extremely fast. See [http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/]("http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/")

---

### Post by Archmage on 2008-04-25
> **ptcbus said:**
> You can try downloading the torrent file. It is extremely fast. See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

I know that I can upgrade with a alternate-CD. But since the machines don't have a CD-Rom-drive the only way is over the internet. Either via apt-proxy within **15 minutes** or directly via the internet in **50 days**.

---

### Post by aperomsik on 2008-04-28
I have been using apt-proxy for several Ubuntu release now... currently trying it for hardy, and it seems to be working.

When I start via Update Manager, I get a prompt saying...

No valid mirror found

While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'gutsy' to 'hardy' entries.
If you select 'no' the update will cancel.

Are you getting this prompt? I choose "yes" and it seems to work OK, meaning it is running via the proxy. I'm not completely thrilled though because I tried to preseed the proxy using files from the DVD image, and the proxy is still contacting the internet more than I think it should. But at least the packages are being cached locally.

---

### Post by Archmage on 2008-04-28
> **aperomsik said:**
> When I start via Update Manager, I get a prompt saying...

No valid mirror found

While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'gutsy' to 'hardy' entries.
If you select 'no' the update will cancel.

Are you getting this prompt?

Strangly I never see this prompt. I only get the information that there is a new update and the question if I want to upgrade. If I click on it, it will rewrite the source.list and I have to wait 5 dayst till the upgrade if finish. :(

---

### Post by velmont on 2009-12-02
Upgrading machines at work from Jaunty to Karmic is incredible boring, as apt-cacher-ng (or do-release-upgrade) doesn't work with it.

Nobody has a solution to this? That's all very strange!

**Edit**

Ah, found solution:

> 
This is fixed in apt-cacher-ng 0.2.1-1 in Intrepid, although I confirm
that it's broken in Hardy and it might be worth fixing this there.

** Changed in: apt-cacher-ng (Ubuntu Intrepid)
       Status: New => Fix Released

** Changed in: update-manager-core (Ubuntu Hardy)
       Status: New => Invalid


So... I have to upgrade my server? :-( :-( :-( Stupid.

**Edit2**

Ah, no, I just downloaded the apt-cacher-ng from jaunty and installed it (dpkg -i). Works nice! (Couldn't use the one from Karmic, as it required other deps)

---

