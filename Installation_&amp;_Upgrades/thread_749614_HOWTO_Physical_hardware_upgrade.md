---
title: "HOWTO: Physical hardware upgrade"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by linuxpenguin on 2008-04-08
This is a trick which I recently learned switching my server from an aging Athlon 1800+ which did well in its day but is no longer performing to expectation, to a nice new 2.6GHz Pentium 4 which is more suitable.  I know that there's Debian users who visit the site too (I run Debian on my desktop and sometimes look here, or am brought here by Google) - **this should work on Debian too.**

Anyhow, if you get a new computer and are keeping the same distro and would like to keep all your same programs, the "dpkg" package utility in Debian/Ubuntu can create a list of your package selections. You can have it export a list of your currently-installed programs and then import the list on your new system.

So on your old PC you type:
```
dpkg --get-selections | grep -v deinstall >> installed-packages
```
to create a file called "installed-packages" that has a list of your installed packages.

Then copy the file over to your new computer, and then in the folder where you put the file run:
```
dpkg --set-selections < installed-packages
dselect
```
to set up those same packages on your new computer.  Your computer should now start downloading and installing any packages on the new computer that were installed on your other computer, but didn't get installed by default on your new computer (or haven't been installed by you manually yet).  It will most likely prompt you a few times to run it.
By the way. . . I like to manually create a "root" user on my install so that when I need to change something, I can just log in with the root password and type whatever commands I need.  **If you don't do this, then you need to either use "sudo" or some other program to run these commands with higher privileges.**
I have a set of scripts available on my site too which also do this, as well as copying over your apt sources (after backing them up, of course) - check it out: [http://www.linuxpenguin.net/component/option,com_remository/Itemid,88888899/func,fileinfo/id,12/]("http://www.linuxpenguin.net/component/option,com_remository/Itemid,88888899/func,fileinfo/id,12/")

---

### Post by Rocket2DMn on 2008-04-08
That is good information to have, I might give that a try on my desktop when I get Hardy going on it for good (since I use Ubuntu on my laptop).
On a side note, for using "root" - it exists already, but is disabled by default in Ubuntu.  You can enable it by rebooting into recovery kernel and running
```
passwd
```
Once the password is set, the root account is enabled, so you can login with it normally (use with caution!).  It may also work to do
```
sudo -s
passwd
```

---

### Post by linuxpenguin on 2008-04-08
> **Rocket2DMn said:**
> On a side note, for using "root" - it exists already, but is disabled by default in Ubuntu
Yeah, that's what I meant. . . I used "sudo -S passwd".  I just meant that if you didn't do that, you will have to use "sudo".

---

