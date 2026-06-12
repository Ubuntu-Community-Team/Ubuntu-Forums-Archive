---
title: "Should I upgrade from 10.04?"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by zozza on 2013-06-23
I am using 10.04.  I like the simplistic style which is not heavy on the graphics.  I did experiment some time ago with a later version (can't remember which) but I found it a bit Windows-like (lots of GUIs).

However, 10.04 is somewhat old.  So, should I upgrade and, if so, which would be a good version?

I want something basic, not demanding on my 4 year old computer, nothing fancy.

Thanks.

---

### Post by JRV on 2013-06-23
You should upgrade, 10.04 has reached end of life.
For an older computer I would try Lubuntu.

---

### Post by dino99 on 2013-06-23
you can still installing from the mini iso, instead of the main iso which now have guis everywhere: only dont install the meta-packages to get a custom installation (only the apps you need/want)
or if you prefer the old gtk2 fashion, but with recent releases (raring saucy), then Lubuntu is a good choice; other like Mint can also do the trick.

[http://distrowatch.com/search.php?basedon=Ubuntu](http://distrowatch.com/search.php?basedon=Ubuntu)

---

### Post by zozza on 2013-06-23
Thanks - I will go for 12.04.  

One thing I am wondering though is whether the upgrade will remove all my files.  First, I have lots of personal files I've added over the years.  Second, I have apt-get installed lots and lots of programs.  What happens to them?

---

### Post by Frogs Hair on 2013-06-23
You can install 12.04 and then install the gnome-session-fallback(selected @ login)  which is most like Gnome 2 on 10.04 . The 10.04 desktop has reached end of life and that would make it an EOL upgrade. Doing a backup and fresh installation of 12.04 would have less potential for problems than the upgrade.
 
Testing  12.04 live would give you an idea of how it runs on your hardware. Other desktop/distro options could include Kubuntu Xubuntu and Lubuntu. The best reason to upgrade is that 10.04 security updates and other improvements have ceased except for the server edition. Mate is a fork of Gnome 2 and a Linux Mint option or can be installed via PPA. [http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

---

### Post by Lars Noodén on 2013-06-23
> **zozza said:**
> Thanks - I will go for 12.04.  

One thing I am wondering though is whether the upgrade will remove all my files.  First, I have lots of personal files I've added over the years.  Second, I have apt-get installed lots and lots of programs.  What happens to them?

You *must* do a full backup of your data before beginning the upgrade.  You need to do that in addition to anything else you might try.  If you have a separate /home directory, that is the best way of ensuring that the upgrade leaves your data be.  However, things can still go wrong with the process and that's why you need the back up.

About the packages you have installed, you can use [dpkg](http://manpages.ubuntu.com/manpages/raring/en/man1/dpkg.1.html) to make a list of what you have added to or removed from the system.  First make a list:

```

dpkg --get-selections > /home/zozza/packages.txt

```

Then once you have the new system set up, you can add what is missing (and remove the extras):

```

sudo dpkg --set-selections < /home/zozza/packages.txt
sudo apt-get dselect-upgrade

```

---

### Post by sudodus on 2013-06-23
Thanks *Lars* for sharing this tip how to keep selected packages :-)

---

