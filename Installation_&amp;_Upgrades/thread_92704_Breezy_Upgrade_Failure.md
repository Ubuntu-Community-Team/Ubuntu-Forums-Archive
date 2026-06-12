---
title: "Breezy Upgrade Failure"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by Mike-97470 on 2005-11-20
Unfortunately, a few days have elapsed since I first tried upgrading and my memory is a little foggy.

I d/l'ed 5.10 and wrote it as .iso CD using GnomeBaker.

I think it was the Wiki that has an upgrade procedure that I tried to follow--

Using the Terminal I copied a couple of command lines to delete Firefox and then install Mozilla-Firefox, As I Recall.  That worked ok.  At least Firefox still works as good as it ever did, which is actually pretty darned good.

At some point I executed something that read the .iso CD and attempted the upgrade.

Last night and over night the upgrade was hanging trying to install a lib..6 (?)

This morning a tried to execute-
"sudo apt-get install ubuntu-base ubuntu-desktop"
per the wiki, but the following error occured and still occurs when Synaptic runs-
'"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
Yes, I tried to do that, but dpkg's gotta have an "action" and I have no clue what action.

This morning I looked in etc/apt/sources.lst and found
"deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted"
as the first 2 lines, the rest of the file is hoary.

ThThat's all I know and i'm gettin' dangerous!  So if someone can bail me out of this, I'd be reeeally appreciative.

---

### Post by adwait on 2005-11-20
Comment out the second line (the one reffering to hoary) and change all the references to the word "hoary" to breezy". After that run
```
sudo apt-get update
sudo apt-get dist-upgrade
```
This will upgrade anything. If there are any problems you can use
```
sudo apt-get install -f
```

and then again resume the upgrade with 
```
sudo apt-get dist-upgrade
```

---

### Post by Mike-97470 on 2005-11-21
Thanks,
I tried that but,
The apt-get update runs but doesn't find files in the backports.  And then some files seem to be corrupt. At the end it gernerates the reccommendation-

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

The other 2 commands generate the same dpkg interrupted message.  Here's the whole session--please let me know it it's not ok to post this length--
I just double checked my etc/art/sources.list and looks ok, everythings breezy.

mike@MikesPavillion:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages
  404 Not Found
Get:8 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages [33B]
Get:9 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages [33B ]
Get:10 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages [ 33B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:12 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages [ 33B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [8894B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [14B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [3978B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [14B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [6984B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [1062B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages [585kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources [915kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [15.4kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [3886B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [15.4kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [3886B]
99% [33 Packages bzip2 0] [Waiting for headers]                      151kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_di sts_breezy-updates_main_binary-i386_Packages - open (2 No such file or directory )
99% [34 Packages bzip2 0] [Waiting for headers]                      151kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_di sts_breezy-updates_restricted_binary-i386_Packages - open (2 No such file or dir ectory)
99% [35 Sources bzip2 0] [Waiting for headers]                       151kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_di sts_breezy-updates_main_source_Sources - open (2 No such file or directory)
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
99% [Working]                                                        151kB/s 0sb zip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

99% [36 Sources bzip2 0]                                             151kB/s 0sb zip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Fetched 4568kB in 35s (130kB/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/mai](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/mai) n/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/uni](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/uni) verse/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/mul](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/mul) tiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports/res](http://ubuntu-backports.mirrormax.net/dists/breezy-backports/res) tricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/bi](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/bi) nary-i386/Packages.gz  Could not open file /var/lib/apt/lists/partial/us.archive .ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages - open (2 No s uch file or directory)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric) ted/binary-i386/Packages.gz  Could not open file /var/lib/apt/lists/partial/us.a rchive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages - open (2 No such file or directory)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/so](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/so) urce/Sources.gz  Could not open file /var/lib/apt/lists/partial/us.archive.ubunt u.com_ubuntu_dists_breezy-updates_main_source_Sources - open (2 No such file or directory)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric) ted/source/Sources.gz  Sub-process bzip2 returned an error code (2)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
mike@MikesPavillion:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
mike@MikesPavillion:~$  sudo apt-get dist-upgrade
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
mike@MikesPavillion:~$

---

### Post by adwait on 2005-11-21
Well try running dpkg --configure -a like it asks you to. Alternatively, try changing the repositories from us.archive.ubuntu.com to just archive.ubuntu.com. To do this, open /etc/apt/sources.list and change all the references to us.archive.ubuntu.com to archive.ubuntu.com

But if you are trying to upgrade from a CD that you already have, then you can just comment out all the other lines except the CD line and then run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Mike-97470 on 2005-11-22
Thanks Adwait,

The "sudo dpkg --configure -a" got things going, over a 1000 files were d/l'ed, etc.  But a few things remain before everything is back to normal  The biggest problem is that my system boots up to a command line log on--and then stays in the terminal mode.  How do I start the Gnome desktop?

Thanks, Mike

---

### Post by adwait on 2005-11-22
Well, running
```
sudo /etc/init.d/gdm restart
```

This should technically get the GUI to start, but since it is not automatically starting on boot, there must be a problem. Try running
```
sudo apt-get install -f
```

Als try running
```
sudo apt-get dist-upgrade
```
Just to check if everything has been properly updated and set up, don't worry, it will only download the files it hasn't downloaded before (if any). not the whole bunch again.

---

### Post by Mike-97470 on 2005-11-23
Thanks again Adwait,
You're advice was on target!  But I did have a wrestling match on my hands for a while.  I think what initially went wrong is that when I changed hoary to breezy in sources.list I had a couple of double entries for one two of the repositories.  After I fixed that things started working even better.

The really nice thing about this whole upgrade process is that, except for the short time that I didn't know how to get out of terminal mode, Ubuntu just kept working.

---

