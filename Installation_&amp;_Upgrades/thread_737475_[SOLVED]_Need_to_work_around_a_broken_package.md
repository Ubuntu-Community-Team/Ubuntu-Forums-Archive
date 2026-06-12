---
title: "[SOLVED] Need to work around a broken package"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by rouge568 on 2008-03-27
I have a laptop on which I am trying to get the internet working. This means that I am manually installing updates, with the help of [nonetdebs.homeip.net]("http://nonetdebs.homeip.net") (a very helpful site). Unfortunately, the latest Hardy updates included e2fslibs and e2fsprogs, with progs being dependent on libs. Not realizing this, I tried to install e2fsprogs first. Oops. The package manager yelled at me for this, and promptly marked my current version of e2fsprogs as broken. Fine. I went into Synaptic and told it to fix the broken packages. Then, *Apply*. Now, those of you very familiar with linux can see the train wreck coming from a mile away. You see, e2fsprogs is a dependency of many critical packages, such as apparmor, gnome-mount, grub, hal, ubuntu-desktop, and **the entire linux kernel**. I am eternally greatful that I'm cautious enough to check which packages are affected by updates. So, disaster avoided, but I am still stuck with a mission critical package marked as broken and the rest of my package management in a standstill. So the question is, how can I tell app that it is wrong, or install these two packages forcefully? I'm sure that there is a nice easy fix that I'm too inexperienced to know about.

edit: Yes, I am on Hardy, but this is not a Hardy problem so I'm not putting it in the development section of the forum.

---

### Post by Pumalite on 2008-03-27
What's the output of?:
sudo apt-get -f install

---

### Post by rouge568 on 2008-03-27
```

The following packages will be REMOVED:
  amarok amarok-xine apparmor apparmor-utils brltty brltty-x11 console-setup
  e2fsprogs gnome-mount gnome-power-manager gnome-session gnome-volume-manager
  grub hal hal-cups-utils initramfs-tools initscripts libmtp7 linux-generic
  linux-image-2.6.24-12-generic linux-image-generic
  linux-restricted-modules-2.6.24-12-generic linux-restricted-modules-generic
  linux-ubuntu-modules-2.6.24-12-generic network-manager network-manager-gnome
  nvidia-glx-new pcmciautils pulseaudio-module-hal sound-juicer
  system-services ubuntu-desktop ubuntu-minimal udev update-notifier
  upstart-compat-sysv usplash usplash-theme-ubuntu volumeid
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs
0 upgraded, 0 newly installed, 39 to remove and 0 not upgraded.
After this operation, 221MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 
```
I love that last line.

Also:
```
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  e2fsprogs: PreDepends: e2fslibs (= 1.40.8-2ubuntu1) but 1.40.8-2ubuntu2 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by Pumalite on 2008-03-27
Did you go ahead with it?

---

### Post by pibb69173 on 2008-03-27
i have the same exact problem with the same package also i dont have internet on my comp

---

### Post by rouge568 on 2008-03-27
No. I'm looking for a solution that won't completely break my computer.

---

### Post by Pumalite on 2008-03-27
I hope somebody comes up with a good answer.

---

### Post by pibb69173 on 2008-03-27
i am also

---

### Post by pibb69173 on 2008-03-27
i need a fix that wont render my pc usless

---

### Post by ruibernardo on 2008-03-27
Hi,

I was browsing around and found this thread. I really don't know what happen, but it's a strange situation. I don't know if you interrupted a package installation/upgrade or missed some packages or if this a problem with Hardy development (can happen).

The nearest thread I found to have a solution for a problem like this was this one: 

[[SOLVED] Huge Screw-up]("http://ubuntuforums.org/showthread.php?t=512994").

Apparently the solution was to use aptitude to install the package that is to be removed by apt-get. Then aptitude should popup the problem and present a downgrade solution. **NOTE**:If you don't get this downgrade option, answer to abort, put the output here so anyone can help and wait for a better solution.

---

### Post by rouge568 on 2008-03-27
Thank you very much - the problem is solved! Here is the series of steps I took for reference:
```

 scott@scott-laptop:~$ **sudo aptitude install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  e2fsprogs 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  e2fsprogs: PreDepends: e2fslibs (= 1.40.8-2ubuntu1) but 1.40.8-2ubuntu2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
e2fslibs [1.40.8-2ubuntu2 (now) -> 1.40.8-2ubuntu1 (hardy)]

Score is 80

Accept this solution? [Y/n/q/?] **y**
The following packages will be DOWNGRADED:
  e2fslibs 
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 0B/111kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] **y**
Writing extended state information... Done
dpkg - warning: downgrading e2fslibs from 1.40.8-2ubuntu2 to 1.40.8-2ubuntu1.
(Reading database ... 111024 files and directories currently installed.)
Preparing to replace e2fslibs 1.40.8-2ubuntu2 (using .../e2fslibs_1.40.8-2ubuntu1_i386.deb) ...
Unpacking replacement e2fslibs ...
Setting up e2fslibs (1.40.8-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      

scott@scott-laptop:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

scott@scott-laptop:/media/UDISK 2.0$ **sudo dpkg -i '/media/UDISK 2.0/e2fsprogs_1.40.8-2ubuntu2_i386.deb' '/media/UDISK 2.0/e2fslibs_1.40.8-2ubuntu2_i386.deb' **
dpkg: regarding .../e2fsprogs_1.40.8-2ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on e2fslibs (= 1.40.8-2ubuntu2)
  e2fslibs is installed, but is version 1.40.8-2ubuntu1.
dpkg: error processing /media/UDISK 2.0/e2fsprogs_1.40.8-2ubuntu2_i386.deb (--install):
 pre-dependency problem - not installing e2fsprogs
(Reading database ... 111024 files and directories currently installed.)
Preparing to replace e2fslibs 1.40.8-2ubuntu1 (using .../e2fslibs_1.40.8-2ubuntu2_i386.deb) ...
Unpacking replacement e2fslibs ...
Setting up e2fslibs (1.40.8-2ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 /media/UDISK 2.0/e2fsprogs_1.40.8-2ubuntu2_i386.deb

scott@scott-laptop:/media/UDISK 2.0$ **sudo dpkg -i '/media/UDISK 2.0/e2fsprogs_1.40.8-2ubuntu2_i386.deb' '/media/UDISK 2.0/e2fslibs_1.40.8-2ubuntu2_i386.deb' **
(Reading database ... 111024 files and directories currently installed.)
Preparing to replace e2fsprogs 1.40.8-2ubuntu1 (using .../e2fsprogs_1.40.8-2ubuntu2_i386.deb) ...
Unpacking replacement e2fsprogs ...
Preparing to replace e2fslibs 1.40.8-2ubuntu2 (using .../e2fslibs_1.40.8-2ubuntu2_i386.deb) ...
Unpacking replacement e2fslibs ...
Setting up e2fslibs (1.40.8-2ubuntu2) ...

Setting up e2fsprogs (1.40.8-2ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by ruibernardo on 2008-03-27
I must confess I wasn't very sure of that solution but I'm glad it worked and could help somehow. 

I'll take your complete post and solution (how you "re"-installed the missing package) as a reference to how to solve a very bad dependency problem on a offline computer in the future.

Just for the record, the missing/re-installed packages were in the list of packages in nonetdebs (and something broke while installing them) or you had to download them manually (without nonetdebs help)?

---

### Post by rouge568 on 2008-03-27
The list that nonetdebs provides. (but these link directly to archive.ubuntu.com/ubuntu/pool/).
I looked up your thread on nonetdebs. Did you set up the site? It looks amazing, and works just as well. 
If you *are* the webmaster, the only recommendation I have is that the status.txt upload page should say *where* the status file is located. (/var/lib/dpkg/status)

---

### Post by ruibernardo on 2008-03-27
> **rouge568 said:**
> The list that nonetdebs provides. (but these link directly to archive.ubuntu.com/ubuntu/pool/).
I looked up your thread on nonetdebs. Did you set up the site? It looks amazing, and works just as well. 
If you *are[i] the webmaster, the only recommendation I have is that the status.txt upload page should say [I]where* the status file is located. (/var/lib/dpkg/status)

Thanks :)

This is good, because if the "re"-installed packages were in the list and were downloaded, it means that the offline user can apply this solution in-place (if he knew/knows the solution) without having to leave a broken system and have to download more packages. That's great.

I'm not *a* webmaster. I've just installed drupal5 and set it to run apt-get in a chroot based on the script (with php and mysql). The bash script was how I started. Install Drupal5 and you'll get a website just like that (after configuring it).

 Thanks for the recommendation, I'll make a(nother) reference to where the status file is to make it more clear after I change the website to another server (working on it).

---

