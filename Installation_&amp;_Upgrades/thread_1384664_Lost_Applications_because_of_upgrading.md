---
title: "Lost Applications because of upgrading"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by nichpakaich on 2010-01-18
Recently I updated my Ubuntu 7.10 to 8.10, by performing a clean install and not-formatting my home partition (set it as home mount point for the 8.10).

At first I didn't realize any changes in the desktop environment, my compiz setting still doing fine (except for the background set for each desktop). And then I wanted to set the image, but to found out that there is no more shortcut to my compiz setting (through the System > Preferences menu).

I checked the Appearance menu, and since I clicked on one of the options available, my compiz feature is no more to be available. The desktop is set to default 8.10 feature.

I checked my other pre-installed application; such as Amarok, Thunderbird, etc. They all are gone.

My question is, how can I get them back?
This question is important, because from now on I'm going to perform the sequential upgrade (8.10 > 9.04 > 9.10), if I'm going to loose those application on every upgrade phase, then I'd just upgrade first before solving my problem.

A clear solution is needed, thanks in advance ;)

---

### Post by phillw on 2010-01-18
Hi,

You did well by keeping your /home seperate !!

My concern is that you may over-write the preferences when you install things like Thunder Bird.

So, for safetys sake...

```
cd /home/.mozilla
mkdir mozback
sudo cp -r * ./mozback

```It'll report an error about copying the mozback directory -- I'm not in script mode, but it will take a backup of all of the mozilla stuff (like your Thunderbird preferences)

You can then install Thunderbird and copy the back-up of the Thunderbird preferences back into the new /home/.mozilla/Thundebird from your /home/.mozilla/mozback/Thunderbird directory.

I don't use amarok, so don't know where it keeps your profile in /home - try either /home/amarok or /home/.amarok and back up the profile as above.

Do this for each application you put back on

Doing an upgrade from 8.10 --> 9.04 will take care of this on its own, but, TBH. Here's what I'd do ...

1) Make a fresh install of 9.10, as per your 8.10 one
2) unmount your /home partition
3) make a new /home/*your-name* directory structure
4) Put on the all the programmes you had on under 8.04 onto 9.10
5) delete the /home/*your-name* directory structure
6) remount your /home partition.

An important note on doing it this way .... make sure you have the same UID on both systems
```
cat /etc/passwd | grep *your-name*
```Your UID will be the first set of digits (usually 1001, but do check !!)

Regards,

Phill.

---

### Post by nichpakaich on 2010-01-18
@phillw:
I've tried to explore my freshly installed Ubuntu 8.10 before I read your reply.

Before I even try about the mozilla backup, I realized that all my Firefox Preferences is kept intact (my bookmarks, password, etc.) So I got to a conclusion, that all I have to do is just to instal the missing application (and hope they will perform just the same way as they were).

But your reply surely gave me a deep understanding of how to manage backups for the previous installation, and so I say thank you.

About your last part, the tips of unmounting the /home then re-mount it, what difference does it make? Isn't it just the same as I did (not formatting the /home during a fresh install).

---

