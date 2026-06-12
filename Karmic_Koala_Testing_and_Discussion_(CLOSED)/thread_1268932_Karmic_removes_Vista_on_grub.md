---
title: "Karmic removes Vista on grub"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by m-tarek on 2009-09-17
Hi every one, 
I installed Karmic today on jaunty's partitions but the new grub did not recognized my vista or my recovery partition>
I tried to add them in /boot/grub/menu.lst like the old way but I didn't find that file>
So any ideas..... just for note I'm using Alpha5.

---

### Post by quique1hn on 2009-09-17
Just update, that solve my problem

---

### Post by m-tarek on 2009-09-17
to alpha 6????

---

### Post by psyke83 on 2009-09-17
> **m-tarek said:**
> Hi every one, 
I installed Karmic today on jaunty's partitions but the new grub did not recognized my vista or my recovery partition>
I tried to add them in /boot/grub/menu.lst like the old way but I didn't find that file>
So any ideas..... just for note I'm using Alpha5.

Don't update the menu.lst manually. Ensure you are fully up-to-date, then:

```
$ sudo apt-get install os-prober
$ sudo os-prober
$ sudo update-grub
```

I thought that Alpha 4 failed to set up Windows partitions correctly and it was fixed in Alpha 5, but perhaps my memory is faulty.

---

### Post by m-tarek on 2009-09-17
OK, I'll update to alpha6 tomorow beccause I don't have a good internet connection right now and I'll try this tomorow and reply then.
Thanks

---

### Post by m-tarek on 2009-09-17
I geuss that helped me on alpha5, I tried this and it worked without updating to alpha6. the package os-prober was installed.
Thanks very much.

---

### Post by forumache on 2009-09-18
@m-tarek, please note that when you update, you update to the latest current version *plus* all the incremental updates.
I mean, you don't update to alpha6 - except if you delete everything and install from alpha6 cd.
Already out Karmic computers are better than Alpha 6 and your will be too ;)
If you update regularly, your transition to Karmic 9.10 (real release) will be smooth, no need to reinstall).

---

### Post by ELD on 2009-09-18
> **forumache said:**
> 
I mean, you don't update to alpha6 - except if you delete everything and install from alpha6 cd.


WRONG. Updating constantly will update you to alpha 6, alpha 6 is simply a snapshot. It is even in the sticky thread at the top of the forum -> [http://ubuntuforums.org/showthread.php?t=1269009](http://ubuntuforums.org/showthread.php?t=1269009)

You should read it before giving the wrong advice.

---

### Post by dino99 on 2009-09-18
> **ELD said:**
> WRONG. Updating constantly will update you to alpha 6, alpha 6 is simply a snapshot. It is even in the sticky thread at the top of the forum -> [http://ubuntuforums.org/showthread.php?t=1269009](http://ubuntuforums.org/showthread.php?t=1269009)

You should read it before giving the wrong advice.

Absolutely agreed, nothing better than a clean install.

---

### Post by ELD on 2009-09-18
> **dino99 said:**
> Absolutely agreed, nothing better than a clean install.

Not what i am saying, but i agree with you a clean install is always best, but updating will keep you updated to alpha6 and beyond which the other post was saying it did not. Was just clearing things up.

---

### Post by forumache on 2009-09-18
> **ELD said:**
> WRONG. Updating constantly will update you to alpha 6, alpha 6 is simply a snapshot. It is even in the sticky thread at the top of the forum -> [http://ubuntuforums.org/showthread.php?t=1269009](http://ubuntuforums.org/showthread.php?t=1269009)

You should read it before giving the wrong advice.

Hmm, sorry for my English, I guess...

Updating constantly will take me to:

Ubuntu Karmic Beta on 1st of October
Ubuntu Karmic ReleaseCandidate on 22th of October
Ubuntu 9.10 on 29th of October

Anyway, I did read and I did understood. Maybe I didn't explained right. You can update from Ubuntu 8.10 to Ubuntu 9.04, but you cannot say: Ok, let's upgrade to Ubuntu 9.10 Alpha 5 (because that snapshot does not exist anywhere (except on a CD)). There is no visible tag in Ubuntu Karmic repository for alpha5 (go see [http://archive.ubuntu.com/ubuntu/dists/karmic/](http://archive.ubuntu.com/ubuntu/dists/karmic/)). You can only update to the current Karmic, whatever that is at the moment we speak.

@dino99, I upgraded constantly from Dapper Drake (6.06). I will stay on Karmic until Karmic+1 reaches Alpha 2 and then join the fun. If something breaks, there is also LiveCD, a backup, and a community ;)

I like to use my main computer for bug reporting. This guarantees that I will notice bugs, because I do all the computer related activities on my main computer (burn DVDs, watch movies, use webcams, fingerprint device, etc). On a second computer, where I don't do all this activities, I will surely have missed bugs.

Have fun and good karma to you all :)

---

### Post by ELD on 2009-09-18
Actually you can easily update to an alpha from your install of jaunty, if you insert an alpha cd it will notify you it has detected it as a repository. So if i download an alpha 5 cd i can "upgrade" to alpha 5, may be picky of me to say it but it can be done ;)

---

### Post by psyke83 on 2009-09-18
> **ELD said:**
> Actually you can easily update to an alpha from your install of jaunty, if you insert an alpha cd it will notify you it has detected it as a repository. So if i download an alpha 5 cd i can "upgrade" to alpha 5, may be picky of me to say it but it can be done ;)

If you insert a desktop cd, it will detect it as a repository, but it contains only a tiny subset of the total packages required to upgrade. The desktop CD cannot be used in this way.

If you don't believe me, stick in your desktop cd and browse to /media/cdrom0/pool. The alpha 6 desktop cd contains 8.3mb of packages in this directory (which are used to boot the live environment).

You *must* use the alternate cd if you wish to perform an offline upgrade.

---

### Post by m-tarek on 2009-09-18
OK, thanks folks, But I prefer to update my system until the final release. Then I will download it.
BTW, I updated my beta-jaunty to the final release without any problem.

---

### Post by Vanishing on 2009-09-18
> **m-tarek said:**
> Hi every one, 
I installed Karmic today on jaunty's partitions but the new grub did not recognized my vista or my recovery partition>
I tried to add them in /boot/grub/menu.lst like the old way but I didn't find that file>
So any ideas..... just for note I'm using Alpha5.

new grub(ie.grub2) no longer uses /boot/grub/menu.lst
instead, it use /boot/grub/grub.cfg

good luck

---

### Post by m-tarek on 2009-09-18
Yes, Thanks, but the way:
```
$ sudo apt-get install os-prober
$ sudo os-prober
$ sudo update-grub
```
by [psyke83]("http://ubuntuforums.org/member.php?u=50843") is much better, it needs 5 seconds!!!!\\:D/

---

### Post by psyke83 on 2009-09-18
> **m-tarek said:**
> Yes, Thanks, but the way:
```
$ sudo apt-get install os-prober
$ sudo os-prober
$ sudo update-grub
```
by [psyke83]("http://ubuntuforums.org/member.php?u=50843") is much better, it needs 5 seconds!!!!\\:D/

I performed a clean install of alpha 6 today, and Windows wasn't added to GRUB. Instead of doing the above, I simply ran:

```
$ sudo update-grub
```

This added Windows successfully. Therefore it seems that os-prober is no longer necessary (in fact, it adds a redundant item to GRUB).

---

### Post by PGHammer on 2009-09-18
> **forumache said:**
> Hmm, sorry for my English, I guess...

Updating constantly will take me to:

Ubuntu Karmic Beta on 1st of October
Ubuntu Karmic ReleaseCandidate on 22th of October
Ubuntu 9.10 on 29th of October

Anyway, I did read and I did understood. Maybe I didn't explained right. You can update from Ubuntu 8.10 to Ubuntu 9.04, but you cannot say: Ok, let's upgrade to Ubuntu 9.10 Alpha 5 (because that snapshot does not exist anywhere (except on a CD)). There is no visible tag in Ubuntu Karmic repository for alpha5 (go see [http://archive.ubuntu.com/ubuntu/dists/karmic/](http://archive.ubuntu.com/ubuntu/dists/karmic/)). You can only update to the current Karmic, whatever that is at the moment we speak.

@dino99, I upgraded constantly from Dapper Drake (6.06). I will stay on Karmic until Karmic+1 reaches Alpha 2 and then join the fun. If something breaks, there is also LiveCD, a backup, and a community ;)

I like to use my main computer for bug reporting. This guarantees that I will notice bugs, because I do all the computer related activities on my main computer (burn DVDs, watch movies, use webcams, fingerprint device, etc). On a second computer, where I don't do all this activities, I will surely have missed bugs.

Have fun and good karma to you all :)

Untrue.  You can *chain-upgrade* from 8.04 to 9.10 M6 (I just finished an in-place upgrade from Kubuntu Jaunty to Kubuntu Karmic M6, in fact; Jaunty was originally installed via Wubi).  No CD needed; I used Update Manager (with the -d switch).  I *did* burn the Kubuntu Karmic M6 live CD, but only for pre-install peeking....

By *chain-upgrade*, I mean upgrading to the highest possible distribution in a series, then upgrading again the same way (like the links in a chain; hence chain-upgrade).  This has been possible in Linux in general (and Ubuntu in particular) for years.

The GRUB issues (commonplace with new versions or major updates to GRUB, and LILO before that) are why I like Wubi (which doesn't rely on LILO or GRUB).

---

### Post by forumache on 2009-09-19
> **PGHammer said:**
> By *chain-upgrade*, I mean upgrading to the highest possible distribution in a series, then upgrading again the same way (like the links in a chain; hence chain-upgrade).  This has been possible in Linux in general (and Ubuntu in particular) for years.

If you upgrade today, without CD, you'll upgrade to Karmic Alpha 6 **plus** all the other updates since Thursday (when Karmic Alpha 6) was released. You cannot upgrade to Alpha 6 as it looked in the day of its release, without CD.

I guess it's a matter of "naming". I name Alpha 6 just the release on the CD, not all the period between Alpha 6 and Beta.

You might call what you have now on your computer Alpha 6. I call it "Karmic updated today" ;)

You say tomato, I say potato (to make fun of an old song).

---

