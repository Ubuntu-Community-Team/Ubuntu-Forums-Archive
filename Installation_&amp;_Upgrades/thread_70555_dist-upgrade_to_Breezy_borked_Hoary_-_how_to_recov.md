---
title: "dist-upgrade to Breezy borked Hoary - how to recover ?"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by soonindallas on 2005-09-30
Hi all.

I thought I would upgrade to Breezy today using apt-get.

Applying the ugrade gave rise to a number of "locale" warnings.  I'm not sure the ugrade completed successfully.  In any case when I boot it appears that grub has not been rewritten, though after a laborious boot, Breezy is announced.

But all I get is a command line.

Also no network is available.  During boot, IPW2200 firmware fails to load and as a consequence I have no wlan.  Trouble is I have no eth0 either.  I cannot ifup eth0, ifconfig only gives info about lo.

I'm downloading the iso of a live cd to try to get the box running.

Would it be easier to fix Breezy or recover Hoary ?

I think that when I do install Breezy, or maybe this time I reinstall Hoary, I should rethink my partition strategy.  It seems wise to have partitions to seperate the OS from the data.  What is best practice ?

Thanks

---

### Post by adwait on 2005-09-30
I guess the upgrade didn't quite complete and so the problems I guess......try this:
Shift+Alt+F1, login and then use
```

sudo killall gdm
sudo apt-get install -f
sudo apt-get dist-upgrade

```

---

### Post by soonindallas on 2005-09-30
thanks.  I found a reference elsewhere to dpkg --configure --pending and it did the trick for most of the install of Breezy.

there's still a few things to fix but it looks manageable

---

### Post by mlomker on 2005-09-30
> Applying the ugrade gave rise to a number of "locale" warnings.

Most people have to:

```

dpkg-reconfigure xserver-xorg
dpkg-reconfigure locales  

```

The problem is that a dist-upgrade will not overwrite your customized /etc files but some changes are required for the new versions to work.


> 
Also no network is available.  During boot, IPW2200 firmware fails to load and as a consequence I have no wlan.  Trouble is I have no eth0 either.  I cannot ifup eth0, ifconfig only gives info about lo.


Neither Hoary nor Breezy's drivers work with my card.  I've always had to build them from source--there are quite a few [how-to's ]("http://www.ubuntuforums.org/showpost.php?p=338666&postcount=16")for that.  The eth0 thing isn't a good sign, though, but I don't know what card you have.

> 
Would it be easier to fix Breezy or recover Hoary ?

Fresh install is the way to go.

> It seems wise to have partitions to seperate the OS from the data.  What is best practice ?

1.5x memory for swap, 6-10 Gig for /, and the rest for /home is my recommendation.  The Breezy installer lets you format as reiser instead of ext3.  I like reiser, but you can suit yourself with filesystem type.

---

### Post by Skaman on 2005-10-02
i Have same problem with locales....
tried your suggestions...but i still got same errors....:confused:

---

### Post by mlomker on 2005-10-02
> i Have same problem with locales....


You could try one of the [other threads]("http://www.ubuntuforums.org/showthread.php?t=66825").  There are a few about this.

---

### Post by FLeiXiuS on 2005-10-02
My solution to this was to do a full dist-upgrade then upgrade.  After receiving the locales warning, I reconfigured my locales, then proceded with the dist-upgrade / upgrade.  I didn't receive any further warning meanwhile.

---

