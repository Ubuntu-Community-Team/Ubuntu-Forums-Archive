---
title: "No Hardy for me?!"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by geeree on 2008-04-25
Hello,

I want to upgrade from Gutsy to Hardy but my update-manager won't show me the "New distribution release '8.04 LTS' is available." message. What could me wrong? 

I access the Internet via a proxy server. Had a similar problem last time: 

[http://ubuntuforums.org/showthread.php?t=579680](http://ubuntuforums.org/showthread.php?t=579680)

Could someone please help?

Thanks,
Girish.

---

### Post by ptcbus on 2008-04-25
In the update manager click on check.

But if you go through the update manager it will take you more than 6 hours for downloading all the packages. 

Instead use torrents. See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by geeree on 2008-04-25
> **ptcbus said:**
> In the update manager click on check.

Thanks for the reply, but in fact I did click on "Check". It downloaded "package information" (failed to download for some repositories) and then merely said "Your system is up-to-date". No new distribution message. :-(

Girish.

---

### Post by jedimasterk on 2008-04-25
Maybe it should have been called Ubuntu Vista instead of Hardy Heron. He He!!

---

### Post by perlluver on 2008-04-25
The server's are packed, try updating via the torrent option.

---

### Post by forkd on 2008-04-25
> **perlluver said:**
> The server's are packed, try updating via the torrent option.

I've been "pimping" the torrent approach here all day.  download the CD image via bittorrent.  It will download in less than an hour on a good high speed connection whereas if you try to download from the regular server it will take days at the current situation.

---

### Post by skoorbevad on 2008-04-25
I have the same issue.  No matter what official ubuntu mirror I choose (even the fast ones), I never get an option to upgrade to hardy via the update-manager.  My 7.10 install is 100% up to date, as well.

I was never presented this option with the 7.04 -> 7.10 upgrade, either, even weeks after the 7.10 release was made.

I have no idea why it never appears.

You'd think "apt-get update && apt-get dist-upgrade" would work, but it just continues showing that 0 packages need updating.

No idea on this one, it stumps everybody I show it to.  I'm just cursed with the inability to upgrade Ubuntu via update-manager, no matter what computer I load it on. ;)

---

### Post by awam66 on 2008-04-25
I have the same problem trying to upgrade from Dapper

---

### Post by geeree on 2008-04-25
> **skoorbevad said:**
> I have the same issue.

> **awam66 said:**
> I have the same problem trying to upgrade from Dapper

Perhaps this has to do with some of our network settings. I did not have this problem when I tried to upgrade from my home, where I access the Internet via a different network and with any proxy servers in between. I got immediate invitation to upgrade from there. But then I decided not to work there because that network is slow. So I got on my work network, which uses a proxy and then my problem started. 

And then News! - After around 3--4 hours of trying the problem went away here too. I got an invitation, I put the pot on boil, and after around 20 hours (!) I am in the process of installing the upgrades. I have no idea how this happened!

Hope this helps,
Girish.

---

### Post by mathenge on 2008-04-25
I had the same problem for most of yesterday (April 24th) but it eventually showed up. I don't know if that's because I'm using Canadian mirrors and they didn't update till later that afternoon.

In any case, my problem is very different now. I click the update button and it seems to work, fetching the installer, preparing software sources but then it hangs at the prompt "Checking package manager"... or something like that. I have to kill the process. But at that point it's broken /etc/apt/sources.list and Update Manager simply misbehaves from that point on. I have to restore the Gutsy sources.list and try again.

I'm thinking that a clean install might be the fastest and best way to go on this. I know it will be a pain to backup everything again, and then re-install all my software, but judging from the posts in this forum, this upgrade is simply not working well for most. I'm actually using the live CD to make this post and it works really well on my machine.

My upgrade from 7.04 (Feisty) to 7.11 (Gutsy) was a piece of cake. Was done the same day the software was released and without the server congestion that everyone's talking about.

---

### Post by geeree on 2008-04-25
> **mathenge said:**
> In any case, my problem is very different now. I click the update button and it seems to work, fetching the installer, preparing software sources but then it hangs at the prompt "Checking package manager"... or something like that. I have to kill the process. But at that point it's broken /etc/apt/sources.list and Update Manager simply misbehaves from that point on. I have to restore the Gutsy sources.list and try again.

I have had this same problem while upgrading from 7.04 to 7.10 and also yesterday while upgrading to 8.04. Both times, I solved it by commenting out all third-party repositories in /etc/apt/sources.list. The update-manager looks up for updates to those repositories and hangs up if it cannot find upgrades to these third-party repositories, 

Hope this helps,
Girish.

---

### Post by mathenge on 2008-04-25
> **geeree said:**
> I have had this same problem while upgrading from 7.04 to 7.10 and also yesterday while upgrading to 8.04. Both times, I solved it by commenting out all third-party repositories in /etc/apt/sources.list. The update-manager looks up for updates to those repositories and hangs up if it cannot find upgrades to these third-party repositories, 

Hope this helps,
Girish.


I think I tried that, but by using "System" -> "Administration" -> "Software Sources"

I'll try doing that manually in /etc/apt/sources.list and see if it helps.

Thanks for the tip.

---

### Post by mathenge on 2008-04-26
> **geeree said:**
> I have had this same problem while upgrading from 7.04 to 7.10 and also yesterday while upgrading to 8.04. Both times, I solved it by commenting out all third-party repositories in /etc/apt/sources.list. The update-manager looks up for updates to those repositories and hangs up if it cannot find upgrades to these third-party repositories, 

Hope this helps,
Girish.

I tried this but I still get the same hanging problem. Removing nearly all Third Party repositories doesn't help. I've attached an image of the frozen dialog window.

---

### Post by geeree on 2008-04-26
> **mathenge said:**
> I tried this but I still get the same hanging problem. Removing nearly all Third Party repositories doesn't help.

Hmm ... this beats me too. Maybe you should start a new thread, with a link to this one, to increase your chances of getting help. 

Good luck!
Girish.

---

### Post by fermin on 2008-04-27
I have the same problem in mi desktop computer. I check for upgrades in the upgrade manager and it updates the repositories info and tells me my system is up to date, but when i check again it doesnt give me the option to upgrade version to ubuntu 8.04 hardy heron.

I already upgraded my laptop from the same internet conection (with proxy) in my home wireless network and there all went well and smooth. I dont know what could be the problem with this other computer since it is the same version (ubuntu 7.10) and same internet connection... perhaps the upgrade system stopped working for some time?

I will check out in yet another computer i have in the same network but with Xubuntu 7.10 and see if it has the same problem to check if the problem is computer based or repository based.

---

