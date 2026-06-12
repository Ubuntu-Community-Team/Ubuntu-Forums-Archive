---
title: "Advice needed:  Clean Install or Not?"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2011-01-13
Hi folks:  My desktop did a lot of crashing in Karmic.  So, I'm planning on installing Lucid.  But, I'm not sure whether I should try to do a very time consuming clean installation or just upgrade as usual.

The reason I might want to do a clean install is that, perhaps because of having crashed so much, it might be that the software has been corrupted.  I don't have any direct evidence of that, other than the fact that crashes seem to be occurring more frequently and there's some weirdness w/ handling of windows and workspaces (though, honestly, my office computer, also running Ubuntu, is acting a bit odd in that regard).

But, does my concern make any sense?  If I just install over Karmic, could corruption in system or configuration files creep over into Lucid?

---

### Post by ssulaco on 2011-01-13
I would probably opt for a clean install if I were in your shoes,since your having problems with Karmic.But then again why not try upgrading.....what have you got to lose;)
Try running a fsck(file system check)open a terminal and run this command,you will need to reboot...```
sudo touch /forcefsck
```
Have you tried running Lucid "live"to see how your hardware likes it?
In the event you do decide to upgrade I would disable your proprietary drivers (i.e. nvidia) and any ppa's you might have

---

### Post by slowtrain on 2011-01-13
Thanks ssulaco!  My file system has been through several fsck's since all the crashing started, one recently.  Seems ok.  I suspect the problem is in the wireless setup.  On the previous OS, I couldn't get wireless working at all; on Karmic it works but error msgs show up and the system crashes frequently.  Hopefully Lucid or later will do better.  I have tried running Lucid from LiveCD.  Seemed fine.

Clean install could be a major time sink.  I've got a lot of non-base software installed.  And then there are little things like what will happen to all my gnupg encrypted directories and files.  Am not really sure where to find and copy my encryption keys or even if they will work in whatever version of gnupg is in Lucid.  Then there are things like my OpenOffice personal dictionary, macros, templates, etc.  Same issues as w/ encryption keys.

---

### Post by ssulaco on 2011-01-13
> **slowtrain said:**
>   I suspect the problem is in the wireless setup.  On the previous OS, I couldn't get wireless working at all; on Karmic it works but error msgs show up and the system crashes frequently.  Hopefully Lucid or later will do better.  I have tried running Lucid from LiveCD.  Seemed fine.

slowtrain,I wish I could help you,but I dont have any experience with wireless problems,both my computers are wired,Is everything you mentioned located in your home directory?
When you ran Lucid Live,could you get the wireless to work?

---

### Post by slowtrain on 2011-01-14
ssulaco--I suspect the wireless problems were more or less built into the kernel, so not much could be done and hopefully the upgrade would do the trick.

I didn't realize you could test wifi w/ LiveCD--have to give that a whirl, thanks!

I'll have to look around a bit on things related to encryption keys.  I suspect that there's a file somewhere that would have to be brought over to any new operating system if I need to open encrypted files / folders.  Alternatively, I suppose I could unencrypt everything, but then I'd need some way to find all the encrypted files on my system.  Not sure how to do that either.

Thanks for your thoughts!  Definitely helping me figure out what I need to do.

---

### Post by slowtrain on 2011-01-14
One thing I should ask, ssulaco-- why is it important to disable proprietary drivers and ppa's before the upgrade?  I don't think I've done that before.

---

### Post by PRC09 on 2011-01-14
If you go the upgrade route remember to back-up everything you wish to keep as this is usually controlled by Murphy`s Law.....Anything that can go wrong......Usually will..... I personally go with a clean install...Links below should answer your questions......

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)


[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by slowtrain on 2011-01-14
Thanks PRC09!  Those pages clarify a lot.

---

### Post by ssulaco on 2011-01-14
> **slowtrain said:**
> One thing I should ask, ssulaco-- why is it important to disable proprietary drivers and ppa's before the upgrade?  I don't think I've done that before.
According to some,it can cause issues,I like to play it safe.

[http://ubuntuforums.org/showthread.php?t=1588153](http://ubuntuforums.org/showthread.php?t=1588153)
[http://ubuntuforums.org/showthread.php?t=1431852](http://ubuntuforums.org/showthread.php?t=1431852)

Im not sure if you can access wireless running Lucid live ,just thought I would ask,if you can things are looking good

---

### Post by ssulaco on 2011-01-15
slowtrain,have you looked into ndiswrapper for your wireless problem?
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

---

### Post by presence1960 on 2011-01-15
> **slowtrain said:**
> Hi folks:  My desktop did a lot of crashing in Karmic.  So, I'm planning on installing Lucid.  But, I'm not sure whether I should try to do a very time consuming clean installation or just upgrade as usual.

The reason I might want to do a clean install is that, perhaps because of having crashed so much, it might be that the software has been corrupted.  I don't have any direct evidence of that, other than the fact that crashes seem to be occurring more frequently and there's some weirdness w/ handling of windows and workspaces (though, honestly, my office computer, also running Ubuntu, is acting a bit odd in that regard).

But, does my concern make any sense?  If I just install over Karmic, could corruption in system or configuration files creep over into Lucid?

Clean install does not have to be a time consuming affair. There is a way to save a file referencing all your installed packages in karmic. You move that file, do the clean install and then put that file into the /home of the new install and run one command. Voila- sit back while all packages are reinstalled in your new version of ubuntu.

There are some limitations of course!

I would set my repositories before reinstalling these packages.

Only packages in repositories will be reinstalled. Any third party packages or those compiled from source will have to be manually reinstalled.

Here is the [link]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5"). I have used this process since lovinglinux posted the instructions. Thanks lovinglinux!

---

### Post by slowtrain on 2011-01-15
Whew, ssulaco, looks like my Nvidia drivers and PPAs will have to at least be disabled.  Thanks for the info!  I did try ndiswrapper, without success.  Maybe I just needed that web page.  As stands, the OS now offers support for my wireless card.  It works, but also seems to crash a lot.  I'll upgrade, which may fix things.  If not, I may try to give ndiswrapper another try.  Thanks again!

I've also discovered where a lot of my configuration files are hiding.  Will put up my notes when I'm done for anyone interested in seeing that.

---

### Post by ssulaco on 2011-01-15
> **slowtrain said:**
>   I'll upgrade, which may fix things.  If not, I may try to give ndiswrapper another try. 

Good luck slowtrain,I hope Lucid works good for you,I'm upgrading to Lucid in a couple of months,Hardy's eol is april,...Love Hardy,the darn thing wont break.Im hoping Lucid is as solid,gotta love the LTS,I dont need the latest and greatest,thats why I highly recommend sticking with the LTS,3 yr support on the Desktop....
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

