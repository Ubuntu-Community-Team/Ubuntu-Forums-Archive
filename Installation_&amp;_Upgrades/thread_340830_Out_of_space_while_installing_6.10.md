---
title: "Out of space while installing 6.10"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by tvor on 2007-01-17
Yesterday, after unsuccessful official method of upgrade from 6.06 to 6.10 :

>  sudo update-manager -c -d /usr/lib/python2.4/site-packages/apt/__init__.py:17: 
FutureWarning: apt API not stable yet  warnings.warn("apt API not stable yet", FutureWarning) 

I've made decision to use the non- recommended method get-apt. This went OK, with message of some packages not installed. After restart Ubuntu comes with login screen, logs me in, but comes back to login screen. it is unable to save session - either out of space or not right to write. With the "recovery mode" I tried to configure Xserver, but it failed to save configuration file (out of space?)
As I'm absolute beginner, any ideas are welcome. I wish not to reinstall or have Phd. in command line. :D Thank you.

---

### Post by taurus on 2007-01-17
From the recovery mode, what's the output of this command?

```
df -h
```

---

### Post by tvor on 2007-01-18
I got this :
> file system   size     used   avail  use%   mount
/dev/hda6     5.5G     5.2G    0     100%   /
varrun        506M      16k   506M   1%     /var/run
varlock       506M      4.0K  506M   1%     /var/lock
ndev          506M      136K  506M   1%     /dev
devshm        506M        0   506M   0%     /dev/shm
lrm           506M       19M  487M   4%      /lib/modules126.15-25-386/volatile
/dev/hda8     3.4G      101M  3.2G   4%     /boot
/dev/hda5      41G       34G  6.2G   85%    /media/windows

P.S. since there is no such a thing as a stupid question: "how do I copy the text from command line" ? May this Q. symbolise me typing the output here  ](*,) 

Thank you:)

---

### Post by taurus on 2007-01-18
You are definitely out of space alright.

```
/dev/hda6  5.5G  5.2G  0  100%  /
```

You need to boot your machine into recovery mode from GRUB menu and do a little house cleaning.

```
aptitude clean
cd ~/.Trash
rm *
cd /home/**username**/.Trash
rm *
```
(Where **username** is the name of the user on your machine, the one that you normally would log in.)

Then, look at your disk space situation again to see if you have created any room.

```
df -h
```
If everything is good, reboot with

```
shutdown -r now
```

p.s.  To copy 'n paste in a console, you need to install gpm.

```
sudo aptitude update
sudo aptitude install gpm
```

---

### Post by mcduck on 2007-01-18
> **tvor said:**
> 
P.S. since there is no such a thing as a stupid question: "how do I copy the text from command line" ? May this Q. symbolise me typing the output here  ](*,) 

There's 3 ways: the one I like best is to select what you want to copy with mouse and then just middle-click to paste it.

Second way is to use shift-ctrl-c and shift-ctrl-v (or just ctrl-v when you paste somewhere else than to a terminal), and the last is to use copy&paste in the right-click menu.

---

### Post by tvor on 2007-01-19
Thank you Taurus, the your solution has worked! I was able to start with > startx and after cleaning up login as a user :-)
Ubuntu 6.10 was stuck without space. After restart I was out of space again while upgrading, had to repeat cleanup. 

I guess my question is is the following sufficient for stable run with occasional updates and some extra software?> Filesystem            Size Used Avail Use% Mounted on
/dev/hda6             5.5G  4.7G  580M  90% /
varrun                506M  104K  505M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                   10M  156K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.17-10-386/volatile
/dev/hda8             3.4G  110M  3.1G   4% /boot
/dev/hda5              41G   34G  6.6G  84% /media/windows
/dev/hdb              453M  453M     0 100% /media/cdrom0
  

Or would you recommend to change the size of some of the partitions?
6.10 is now running beautifully -job certainly worth it! Thank you.
 P.S to McDuck: I had problem to copy in recovery mode only.

---

### Post by taurus on 2007-01-19
What's on /dev/hda5 anyway (XP)?  5.5GB is not a whole lot if you save a bunch of stuff to your own $HOME directory.  If you don't have anything important files on /dev/hda5, you can either use that as a storage or move /home over there.  Otherwise, I think you should get another harddrive to give you some room.  Harddrives (PATA) are real dirt cheap now.  :) 

On the other hand, your /boot partition, /dev/hda8, doesn't have to be that large, ~3.4GB.  It only holds your kernels (and grub menu/config) so shouldn't take up more then a few hundred MB.

However, I think another harddrive is a way to go.

---

### Post by tvor on 2007-04-06
Thank you. As I have found out, the /home for Ubuntu has to be in linux format ext3 or smilar. Unfortunately my experience with Win drivers for ext3 is not great. Therefore my decision was to resize boot partition, /dev/hda8 for the benefit of the home directory. 

Gtparted  software shows LOCK next to all used partitions, therefore I can't resize. Is is a permission problem (I run Gparted as sudo)

Resolved (it still does puzzles me why is Gparted there at all then)
> [http://ubuntuforums.org/showthread.php?t=380306&highlight=locked+partition+gparted](http://ubuntuforums.org/showthread.php?t=380306&highlight=locked+partition+gparted)

---

