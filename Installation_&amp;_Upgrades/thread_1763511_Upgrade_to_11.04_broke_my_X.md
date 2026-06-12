---
title: "Upgrade to 11.04 broke my X"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by ferulebezel on 2011-05-20
I used the update manage to upgrade to 11.04 just going with the defaults with every question.

When I rebooted it went into an old login prompt.  I logged in as a normal user and tried 'startx' and got a huge flow of text.

I can't post any output or logs because I can't get to a browser.

I'm guessing that it has something to to with the fact that I installed the manufacturers (Nvidia) video drivers and they somehow got deleted.

Anyway how to I fix it.

I'm posting from work and need answers I can print out and take home at 5:00 PDT.

Thanks.

---

### Post by ajgreeny on 2011-05-20
Login to the cli and then use command ```
sudo apt-get install nvidia-current
```then try startx, or reboot.

---

### Post by ferulebezel on 2011-05-20
That is a possibility.  But it's has been my experience that dist upgrades tend to break repository listings as well.  I need to make sure that that won't happen.  What file do I check and what lines need to be in it for that to work.

---

### Post by ajgreeny on 2011-05-20
Check that there are no references to maverick in the **/etc/apt/sources.list** file or any other files that may be in the **/etc/apt/sources.list.d** folder.  In fact you should disable any repos other than the standard ubuntu ones before doing a dist upgrade for safety's sake; some users seem to get no problems but more have great difficulty.

I've never done a dist upgrade, but always clean install which is very quick with a separate /home partition, so I have no personal experience of any of this.

---

### Post by ferulebezel on 2011-05-20
What are the standard repos?  I need a list.

I'll probably have to go kinkos to make a dvd for a clean install.

This is the last time I'm doing a dist upgrade.  It always breaks something.

---

### Post by MonsterTrimble on 2011-05-20
What video card do you have? There is a show stopper bug in many of the Nvidia drivers - they have mostly been corrected except for nvidia-96. Your best bet is to erase your /etc/X11/xorg.conf file (if you have one) and then reboot to see if nouveau or something picks up.

---

### Post by linuxinstalledfromhdd on 2011-05-20
That happens.  I do it this way over a lan network installation and it takes the most of 20 minutes to have this completely installed and over with...

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by ariel on 2011-05-20
> **ferulebezel said:**
> I used the update manage to upgrade to 11.04 just going with the defaults with every question.

When I rebooted it went into an old login prompt.  I logged in as a normal user and tried 'startx' and got a huge flow of text.

I can't post any output or logs because I can't get to a browser.

I'm guessing that it has something to to with the fact that I installed the manufacturers (Nvidia) video drivers and they somehow got deleted.

Anyway how to I fix it.

I'm posting from work and need answers I can print out and take home at 5:00 PDT.

Thanks.


I did my upgrade from 10.10 to 11.04 yesterday and it was a complete disaster, due to the graphic drivers (nvidia 8600gt here, with dual monitors (TV + LCD) and custom xorg.conf).

The machine would boot then freeze when opening firefox or when minimizing any window. I used Unity for about 10 minutes - the time it took me to figure out it is still half baked (not to mention that gnome3/shell looks much better).

Anyhow, the horror came when booting ubuntu classic and finding lockups and worst of all, the machine stopped booting right before the login screen (at the "checking battery status" boot action). Tried all sorts of things including older nvidia drivers, beta binaries directly from nvidia site and so on (which to my surprise are no longer installable in ubuntu due to the tight integration of nouveau).


To make a long story short, this is what I did to get my system to a "kind of stable" state:


   * In software sources:
        * activate the "Natty proposed updates" checkbox; with this you will get a new major kernel update which in my case fixed most of the issues, and litterally a ton of other updates
        * add the Ubuntu X PPA to get the latest and greatest nvidia drivers packaged by the canonical employees - there was an nvidia driver release this morning and the PPA had the new driver within an hour, very impressive - or showing that a LOT of people running natty was having problems and complaining
    * purge whatever nvidia driver was installed, and then install "nvidia-current" 

After this, the machine started to boot and for the last couple of hours, no lockups so far (touch wood).

For the last 6 or 7 releases, ubuntu was rock solid in my desktop - and for the first time in many, many years I was on the verge of rolling back an ubuntu upgrade. Or entertaining the possibility of trying out fedora and gnome 3. I guess I may wait a bit more before moving on. 

Given my own experience, I can only hope that they don't remove the "Classic" option in 11.10, which saved the day for me this time - if they do, maybe it will time to move on to some other distro.

---

### Post by ajgreeny on 2011-05-21
There is a very good site at [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) which will generate a default sources.list file for you, or add lots of extras if you want.  You can then simply replace your current faulty sources.list with the new one and run ```
sudo apt-get update
```to activate it, and away you go!

---

### Post by ferulebezel on 2011-05-22
I just went to kinkos, made a disk and did a clean reinstall which sucked but it worked.

---

