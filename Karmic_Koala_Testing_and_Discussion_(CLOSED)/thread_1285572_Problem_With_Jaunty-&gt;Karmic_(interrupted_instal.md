---
title: "Problem With Jaunty-&gt;Karmic (interrupted installer)"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by revf on 2009-10-07
So, I'm in the process of upgrading from jaunty to karmic using update manager -d.  Because of my flaky connection at home, I've had to run and cancel the download part of the installer several times.  The installer had no problem seamlessly resuming the first few times, but when I ran it this morning, it crashed during the download.  When I ran update-manager again after that, I noticed that the list had at least a hundred packages on it, and it popped up an error message, but I was able to click on the upgrade button again to resume the installation, and I got almost all the way to the end of the download process before I had to cancel and shut the computer down.

Unfortunately, the next time I ran update-manager, the button to upgrade to karmic was gone, and do-release-upgrade now says "No new release found."

Looking at sources.list confirmed my suspicion that the crashed installer hadn't properly put back its configuration changes; every item said "karmic" instead of "jaunty".  But when I fixed that and reran update-manager, the upgrade button still didn't show up.

So, my question is: What changes, besides switching sources.list to karmic, does the installer normally make and then reverse?  Or, if manually reversing those changes isn't the answer here, what else can I do to make it recognize the karmic update?

Thanks in advance for any help.  I'd really rather not re-download everything, considering what a pain it was to get to this point.

---

### Post by kansasnoob on 2009-10-07
If you're at least getting to the desktop go to Terminal and run the following commands:

```
sudo dpkg --configure -a
```

and:

```
sudo apt-get -f install
```

Let us know what happens. It could be helpful to copy-n-paste the Terminal output here also.

BTW a fresh install would be preferable to an upgrade on a slow or unreliable connection, but you know that now. Sorry to rub salt in an open wound.

Do you have any *buntu Live CD's?

---

### Post by revf on 2009-10-07
Well, there's no problem with the actual system at this point, since it didn't quite finish the downloading part of the installation process.  I feel like if I can get update-manager to realize that I haven't updated to karmic yet (and that karmic exists), the rest of the installation would probably work fine.

Having clarified that, do you still think I should run those commands?  I'm a little unclear on what they'd do.  My natural inclination is to steer clear of the downloaded packages that are currently sitting on the drive until I can get the normal installation process to continue, but I'll do whatever you guys think is best.

---

### Post by revf on 2009-10-07
Oh, by the way, if I run those commands, should I be using the sources.list with "karmic" on all the entries, or the one I put back to "jaunty"?

---

### Post by kansasnoob on 2009-10-07
Well, I'd restore the sources.list to what it was before you manually edited it!

Explaining commands:

```
cat /etc/issue
```

Would tell us what OS is now recognized.

```
uname -a
```

Will provide kernel info that'll give us more of a clue where you're at in the upgrade process.

```
sudo dpkg --configure -a
```

Will only use the current packages and attempt to "configure" things.

```
sudo apt-get -f install
```

Would tell you if you needed to correct any dependencies.

Maybe you have a disc space problem!

```
df -H
```

would help us determine that.

Now, I have a question for you, "if you have no clue what you're doing, and know you have a poor internet connection, why would you try a development release?"

I don't believe you even answered if you have a Live CD!

---

### Post by ronacc on 2009-10-08
I think that while you still have a working system you should download the beta livecd so that you can install from scratch if your attempts to recover don't work . I realize that if you have a flaky connection it may take awhile but that is the safest way to proceed at this point .

after thought : if your connection was down for a few hours many of the packages in the repo's would have changed between the time your d/l originaly started ant your restart attempts , the updates have been comming very fast the last couple of days .

---

### Post by revf on 2009-10-08
> **kansasnoob said:**
> ```
cat /etc/issue
```

Would tell us what OS is now recognized.

```
uname -a
```

Will provide kernel info that'll give us more of a clue where you're at in the upgrade process.
Like I said, I am not anywhere in the upgrade process.  The installer has almost finished downloading all of the packages, but nothing has been installed.  Everything that I've looked at (/etc/issue, the kernel version, lsb_release) has been consistent with jaunty except the sources.list, which the installer modified before crashing.

> Maybe you have a disc space problem!

```
df -H
```

would help us determine that.
What have I said that makes it sound like I have a disk space problem?  I have plenty of space.

> Now, I have a question for you, "if you have no clue what you're doing, and know you have a poor internet connection, why would you try a development release?"
I'm pretty new at this, but I don't have "no clue what I'm doing."  The reason I asked about the dpkg and apt-get commands is that it sounded like you misunderstood what I was saying about the present situation and thought that there was some kind of botched install that needed to be cleaned up.  And I'm not sure what the internet connection has to do with anything, since the installer has had no problem stopping and resuming when necessary.

> I don't believe you even answered if you have a Live CD!
I have a Jaunty USB stick.

---

### Post by kansasnoob on 2009-10-08
> **revf said:**
> Like I said, I am not anywhere in the upgrade process.  The installer has almost finished downloading all of the packages, but nothing has been installed.  Everything that I've looked at (/etc/issue, the kernel version, lsb_release) has been consistent with jaunty except the sources.list, which the installer modified before crashing.


What have I said that makes it sound like I have a disk space problem?  I have plenty of space.


I'm pretty new at this, but I don't have "no clue what I'm doing."  The reason I asked about the dpkg and apt-get commands is that it sounded like you misunderstood what I was saying about the present situation and thought that there was some kind of botched install that needed to be cleaned up.  And I'm not sure what the internet connection has to do with anything, since the installer has had no problem stopping and resuming when necessary.


I have a Jaunty USB stick.

Well, then why not just post the output of those three commands like this:

> lance@lance-desktop:~$ cat /etc/issue
Ubuntu karmic (development branch) \n \l

lance@lance-desktop:~$ uname -a
Linux lance-desktop 2.6.31-12-generic #40-Ubuntu SMP Wed Oct 7 04:14:43 UTC 2009 i686 GNU/Linux
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              6.3G   3.0G   3.1G  50% /
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   115k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


You'll have to excuse me for being a grouchy old man but I work on lots of computers (no formal training) and I have people all the time tell me, "it can't be that" but then it turns out being "just that".

No command I recommended was as dangerous as modifying your sources.list half way thru the process.

You CAN NOT downgrade by editing the sources.lst!

---

### Post by revf on 2009-10-08
```
ryan:~$ cat /etc/issue
Ubuntu 9.04 \n \l

ryan:~$ uname -a
Linux computer 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

ryan:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2              7.3G   5.2G   1.8G  76% /
tmpfs                  245M      0   245M   0% /lib/init/rw
varrun                 245M   357k   244M   1% /var/run
varlock                245M      0   245M   0% /var/lock
udev                   245M   148k   245M   1% /dev
tmpfs                  245M   406k   244M   1% /dev/shm
lrm                    245M   2.3M   242M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda4               51G    15G    34G  31% /home
```

> **kansasnoob said:**
> You CAN NOT downgrade by editing the sources.lst!
I wasn't trying to downgrade, I was undoing a change that was supposed to be temporary in the first place.  I just don't know what else the installer did that's causing problems now.

---

### Post by ranch hand on 2009-10-08
Put you sources list back to "karmic" and at least run the friggin'
```

sudo dpkg --configure -a

```
If ANYTHING is still stuck in there, nothing is going to work.

Just do it.

Another grumpy geezer.

---

### Post by revf on 2009-10-08
Thanks, but I actually just found out my hard drive is damaged, so I'm going to have to buy a new one and do a fresh install after all.

---

### Post by nanog on 2009-10-09
```
You CAN NOT downgrade by editing the sources.lst! 
```

Downgrading is possible. I went from Jaunty back to Hardy and then skipped to Karmic on one box. 

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[http://www.leune.org/blog/kees/2005/05/downgrading-debian-gnulinux-fr.html](http://www.leune.org/blog/kees/2005/05/downgrading-debian-gnulinux-fr.html)
[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

Edit /etc/apt/preferences as explained in above posts.

Example 

> X-comment: Force downgrade to testing.
Package: *
Pin: release a=jaunty
Pin-Priority: 1100

---

### Post by ranch hand on 2009-10-09
> **nanog said:**
> ```
You CAN NOT downgrade by editing the sources.lst! 
```Downgrading is possible. I went from Jaunty back to Hardy and then skipped to Karmic on one box. 

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[http://www.leune.org/blog/kees/2005/05/downgrading-debian-gnulinux-fr.html](http://www.leune.org/blog/kees/2005/05/downgrading-debian-gnulinux-fr.html)
[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

Edit /etc/apt/preferences as explained in above posts.

Example
WOW, something useful out of this thread.

That is a neat piece of information.  I can't imagine using it, but you never know.

Heck, I may have to try it just to see it work.

---

