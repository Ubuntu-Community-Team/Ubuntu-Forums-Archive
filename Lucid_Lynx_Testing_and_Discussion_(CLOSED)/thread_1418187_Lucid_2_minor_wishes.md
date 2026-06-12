---
title: "Lucid: 2 minor wishes"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-02-28
1) Fix Transmission's anxiety to send upload/download totals to trackers (it's like confusing developer's problems with user's problems and needs). First, it takes several seconds (none, uTorrent nor Azureus do that in such an intruding way if at all). Second, it's so anxious about sending this data that it tries sending this data even when nothing has been done and there's no torrent in the first place (brain-dead behaviour)!
Except for this - Transmission is ideal.

2) No one uses /mnt any more (not counting folks who love retro), time to dump it yet? Nothing earth shuttering here , but removing redundant stuff like this is always good and makes things simpler.

---

### Post by Keyper7 on 2010-02-28
1) Upstream issue, have you reported it to the Transmission devs?

2) Might be there for legacy purposes, are you 100% sure no current app needs it?

---

### Post by kahumba on 2010-02-28
1) I'm never reporting obvious stuff to the original devs, cause in such cases they're usually aware of the problem but refuse to treat it as a problem. I'm sure the problem is in their way of thinking, hence only Canonical or so can persuade/suggest them to change their mind and hence the way Transmission works in this particular case.

2) I'm suggesting. No one can ever guarantee there's no (obscure) app on Earth using it. So it's not about "if anyone", it's about "if few enough". Thus the question is, is it **already** worth removing it or not, and I think it's worth it.

---

### Post by ranch hand on 2010-02-28
There would be an awful lot of problems if one were  not able to chroot into a screwed system.  This is particularly true in pre-release testing.

You need to chroot to recover grub from the CD.

My current /mnt;
```

sam@sam-desktop:~$ ls /mnt
Daily-root  ISO-home    Lounge-root   Maiden-root  Stoner1.2-root  Zenix-root
Hairy-root  ISO-root    Lubuntu-root  MAIN         Throw-root
Horny-root  Kinky-root  Lxde-root     Mini-root    UMangler-root

```

---

### Post by uBeer on 2010-02-28
> **ranch hand said:**
> 
You need to chroot to recover grub from the CD.

I've recovered grub quite a lot of times from the live cd but I never needed to use chroot. Both with grub 1 and 2 you don't need it. What's your procedure if you restore grub?

---

### Post by kahumba on 2010-02-28
Great, it seems we found out that (unfortunately) there are still dependencies on /tmp. Moving on.
ps: fixing /mnt for /media would be really easy, (almost) no one cares though.

---

### Post by ranch hand on 2010-02-28
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

If you are using some other method of working with grub1.96 through the current grub1.98 I would love to hear about it.

I am running on 10.04 as my production OS during the daytime.  I have boinc running at a high rate that keeps my cpus cranked all the way up to 99 to 100%.  I have 6 other 10.04 variations on this test platform and 4 on another.

I run all my update/upgrades from chroot without ever having to leave this OS.  Then I can go and check on them before upgrading this one.

Folks running banks of servers also need to chroot to do routine updates and other tasks.  /mnt is not an obsolete directory.  You may not use it.  This does not mean that a whole lot of others do not.

---

### Post by Keyper7 on 2010-02-28
> **kahumba said:**
> 1) I'm never reporting obvious stuff to the original devs, cause in such cases they're usually aware of the problem but refuse to treat it as a problem. I'm sure the problem is in their way of thinking, hence only Canonical or so can persuade/suggest them to change their mind and hence the way Transmission works in this particular case.

Considering my needs, I don't particularly care about the problem you described. What is "obviously" a problem to you might be a non-issue to others depending on their needs. The only way to be sure that developers are looking into something is by properly reporting it.

Furthermore, if the Transmission developers are anything close to serious, then they wouldn't give a Canonical request any more priority then they would give a request from you or another user. Few upstream projects do that.

In fact, in some projects the developers tend to frown upon Canonical requests because of its reputation as a company that only leeches and does not contribute upstream. In those projects, you have a better chance of being heard than Canonical does.

---

### Post by phenest on 2010-02-28
> **Keyper7 said:**
> What is "obviously" a problem to you might be a non-issue to others depending on their needs.

Agreed. I consider both the OP's points to be a non-issue. I cannot see how fixing neither would hurt anything, or if they need fixing at all. I wonder how many other empty/unused folders there are that could be removed, so why pick on /mnt? If you want the Canonical devs to 'fix' Transmission, I suggest you supply them with a patch.

---

### Post by coffeecat on 2010-02-28
> **kahumba said:**
> 2) No one uses /mnt any more

Oh yes they do!

> **kahumba said:**
> ps: fixing /mnt for /media would be really easy, (almost) no one cares though.

Oh yes they do! :wink:

Some people don't like the desktop icon you get when you mount in /media  (not me), and prefer to mount in /mnt so that they get a "clean" desktop. This is not my choice, but I've seen this preference expressed enough times in the forums to think it's more than "almost no one".

---

### Post by iggykoopa on 2010-02-28
I kind of agree with the OP about mnt. You can turn off desktop icons in nautilus, so that would fix that issue. I wish more distros would do something along the lines of gobolinux, I think there are a lot of legacy decisions with the naming of the file structure. It would break a lot of things at first, and people always complain about changes when they are used to things a certain way, but it would make a lot of sense to have all config files in a /config directory, executables in a /programs directory, home tmp and a few others could stay the same, dev could go to devices possibly. It would just make the filesystem a lot cleaner and make more sense.

---

### Post by phenest on 2010-02-28
> **iggykoopa said:**
> I kind of agree with the OP about mnt. You can turn off desktop icons in nautilus, so that would fix that issue. I wish more distros would do something along the lines of gobolinux, I think there are a lot of legacy decisions with the naming of the file structure. It would break a lot of things at first, and people always complain about changes when they are used to things a certain way, but it would make a lot of sense to have all config files in a /config directory, executables in a /programs directory, home tmp and a few others could stay the same, dev could go to devices possibly. It would just make the filesystem a lot cleaner and make more sense.

So what if it makes it cleaner. Who's going to see it? This is the least important issue in Linux (or any OS).

---

### Post by iggykoopa on 2010-02-28
ummmm your going to see it any time you open the file manager or drop to a command line. For new users what makes more sense, telling them to go to a directory called /etc to modify a configuration file, or a directory called /config, or telling a user that the program they want to run could be in /bin or /sbin or /usr/bin or /usr/sbin, or that the program they want is in /programs? I think this is a very important issue, but that's just my opinion.

---

### Post by phenest on 2010-02-28
> **iggykoopa said:**
> ummmm your going to see it any time you open the file manager or drop to a command line.

Nope. I see my $HOME directory. And dir (on its own) does not show hidden folders.

> **iggykoopa said:**
> For new users what makes more sense, telling them to go to a directory called /etc to modify a configuration file, or a directory called /config, or telling a user that the program they want to run could be in /bin or /sbin or /usr/bin or /usr/sbin, or that the program they want is in /programs? I think this is a very important issue, but that's just my opinion.

Again, no. It makes more sense to keep new users away from a terminal. Ubuntu is about making life easier and giving users gui's to play with, so a terminal ends up being used by more experienced users who, by then, will have already gained an understanding of the file system.

Besides, I don't think gobolinux uses a different folder structure. I believe it uses links instead to give that impression.

---

### Post by iggykoopa on 2010-02-28
yup gobolinux uses symlinks to create the view they use for the directories. It would have to be something that basically all distro, application, and kernel devs would have to agree on. So basically it'll probably never happen, just wishful thinking.

---

### Post by kahumba on 2010-02-28
> **Keyper7 said:**
> Considering my needs, I don't particularly care about the problem you described. What is "obviously" a problem to you might be a non-issue to others depending on their needs. The only way to be sure that developers are looking into something is by properly reporting it.

Furthermore, if the Transmission developers are anything close to serious, then they wouldn't give a Canonical request any more priority then they would give a request from you or another user. Few upstream projects do that.

In fact, in some projects the developers tend to frown upon Canonical requests because of its reputation as a company that only leeches and does not contribute upstream. In those projects, you have a better chance of being heard than Canonical does.

You are my hero and champion of casuistry.

---

### Post by Keyper7 on 2010-03-01
> **kahumba said:**
> You are my hero and champion of casuistry.

If my words were too difficult before, I'll make it simpler:

1) If you don't report a problem, you can't complain about it not being looked into. "They won't listen" is a bad excuse for laziness.

2) There is absolutely no evidence to believe that Canonical would be more listened to than you.

3) If such evidence existed, reporting a bug against the Transmission Ubuntu package in Launchpad would be more useful than posting in this forum.

---

### Post by 23meg on 2010-03-01
In any case, filing a bug report in the appropriate bug tracker or raising an issue in a relevant mailing list in an adequate manner is always infintely more useful than posting a list of wishes in a testing and discussion forum frequented mostly by testers, where it's nearly guaranteed not to be heard by the relevant people (and in the rare case that it's heard, forums are still hugely inferior for keeping track of issues over time). 

Closing this thread, since threads dedicated to arbitrary wishes are beyond the scope of this forum, whose focus is assisting people with testing. If you need help on taking the concrete steps for getting your wishes implemented in some way, feel free to start a thread dedicated to that.

---

