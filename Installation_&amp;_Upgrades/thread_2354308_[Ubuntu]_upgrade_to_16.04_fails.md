---
title: "[Ubuntu] upgrade to 16.04 fails"
date: 2017-03-01
forum: Installation &amp; Upgrades
---

### Post by conor9 on 2017-03-01
Really confusing problem, hope someone can help.

I tried upgrading from 14.04 to 16.04. (System prompted for version upgrade after recent regular software upgrade)
I let it do it. I watched it download  the packages, that seemed fine.
It warned about xscreensaver and xlockmore. I killed both before proceeding
 It then installed the packages and seemed to get stuck on the fonts.
Eventually it resumed, but the screen showed a message about low graphics mode.
It then gave an empty dialog with no options. I clicked OK and the system dropped to a flashing cursor.
I left it for 30mins before forcibly rebooting.

It booted into a shell, but I can't login.

This is where it gets tricky. I had the box set to auto login.
I know the password for su operations (e.g. to install software etc) - indeed, I needed it to start the upgrade. But the problem is that I can't think what the username is. I've tried my usual suspects but no joy.

I've tried to boot to recovery via GRUB, but when I select recovery, it drops to tty1 and looks for a login, without asking what I want (such as root shell etc.)

I've tried editing the grub entry to give me a root prompt (rw init=/bin/bash) but the USB keyboard doesn't work.

I've booted it from a live CD and can see the hard disk, but not sure what else to do.

Can anyone help please?

Thanks!

---

### Post by Bashing-om on 2017-03-01
conor9; Hey !

In small steps toward recovery .
Let's find the user ID.
From the liiveDVD booted in try ubuntu to a terminal ( ctl+alt+t) :
```

sudo parted -l # to find the root partition .
sudo mkdir /mnt/looksee/
sudo mount /dev/sda1 /mnt/looksee/ # let's "suppose" sda1 is where the root partition is, adjust as needed  ##
ls -al /mnt/looksee/home/

```
In the output from the ls command is "your" user directory that will be named as "you"
example:
> 
drwxr-xr-x 28 sysop sysop 4096 Mar  1 12:56 sysop

where my username is "sysop" .

Now when all done looking around. as we mounted the file system it is our responsibility to UN-mount it. Failure to UN-mount can lead to file system inconsistencies !
unmount:
```

sudo umount /dev/sda1 ## or whatever the actual mount point is ( sda1 ??) 

```
Next is to see what happens attempting to boot into the install.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by conor9 on 2017-03-01
@bashing-om:

Ahh good stuff. Didn't even think of that.
OK, I can login [   stupidest username of all time :)  ]
It says welcome to Ubuntu 16.04.02 etc

I tried to get it to refresh the apt by doing apt-get update but it reported that I need to run dpkg --configure, so that's running now.

When it does finish, where to look for what went wrong?

Thanks for the help

---

### Post by Bashing-om on 2017-03-01
conor9; Hey hey !

We make progress !

As to :
> 
 where to look for what went wrong?

could have been any number of causes . My opinion without looking is the screensaver active.

We get the system stable we can go looking as you please .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by conor9 on 2017-03-01
I'll update when dpkg is finished.

As mentioned, I did a killall of the screensaver so I'm not clear on how it would have restarted itself, but let's see.

---

### Post by conor9 on 2017-03-01
Dpkg finished and rebooting, it went straight into GUI - hooray!

Any installation logs I can check to see if I can work out what happened?

---

### Post by Bashing-om on 2017-03-01
conor9l Great !

1st order of business now that you are up is to insure that the package manager is in a consistent state of mind - such that the system is happy also:
```

sudo apt autoclean
sudo apt autoremove
sudo apt clean
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg --configure -a
sudo dpkg -C

```
if all comes back clean - dpkg returns only to prompt - then we are home free. Ya done it !

Now log files:
anything left over in "  /var/log/dist-upgrade/ " ?
Have a look " /var/log/apt/term.log ", "/var/log/dpkg.log" and "/var/log/dpkg.log.1" .
These should give hints of any problems.


[INDENT][INDENT]wiping the sweat off
[/INDENT][/INDENT]

---

