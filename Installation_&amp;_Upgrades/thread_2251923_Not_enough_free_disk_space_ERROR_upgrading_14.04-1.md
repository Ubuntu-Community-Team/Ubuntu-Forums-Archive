---
title: "Not enough free disk space ERROR upgrading 14.04-1 LTS to 14.10"
date: 2014-11-07
forum: Installation &amp; Upgrades
---

### Post by macsociety on 2014-11-07
Just tried my 1st sudo do-release-upgrade -d to upgrade from Ubuntu Gnome 14.04-1 to 14.10 but getting an error message that confuses me.  

I am not a linux expert either.

It basically aborts the upgrade saying not enough disk space.

My hard drive is 1TB and I have a good 700GB left so can't be that.

This is the log in the terminal that I see.  (help..... please)

TJ

"Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Not enough free disk space 

The upgrade has aborted. The upgrade needs a total of 63.1 M free 
space on disk '/boot'. Please free at least an additional 22.0 M of 
disk space on '/boot'. Empty your trash and remove temporary packages 
of former installations using 'sudo apt-get clean'. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done"

---

### Post by Bucky Ball on 2014-11-07
You have 700Gb free on the drive, but how much do you have free in the Ubuntu partition??? Open Gparted and have a look at the unused space in the partition marked /.

(PS: Please use [code] tags for code. See the last link in my signature. Thanks.)

---

### Post by macsociety on 2014-11-07
Ouch yes.... downloaded and installed GParted via Ubuntu Software Center and running the app see /boot is only 243MB and used is 191.65MB with remaining 51.35MB.

My /dev/sda2 is 931GB.

What size should /boot be?

I take it I have to create a GParted Live CD and boot from it to expand that /boot, correct?

Hope expanding can be done without affecting my main install.

TJ

---

### Post by Bashing-om on 2014-11-07
macsociety; Hello;

Maybe best to remove the old kernels from /boot:
```

sudo apt-get autoremove

```
If one pays attention to /boot, re-size-ing may not be required .

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-11-07
If you have an LVM install or LVM encrypted install changing the size if /boot is a lot more difficult.

Best just to maintain a minimum number of kernels in /boot. I normally keep 2 current and one old one. 

       I prefer synaptic but you can use command line:

 Determine your current kernel:
uname -a
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

---

### Post by macsociety on 2014-11-07
Thanks for all the advice so far.

Does not allow me to purge or erase any of the old kernels.

Getting error message.

Here is what I get.  See below code...

TJ

** Also side note... I am on Gnome Ubuntu so have no Synaptic that I see.  So trying to purge or erase these extra kernels.  Lastly...yes my drive is LVM2 so it would not allow me to make that 930GB smaller allowing me to make that /boot bigger.... so gparted did not work for me in that respect. **

```

tj@Maingear:/boot$ ls vmlinuz*
vmlinuz-3.13.0-24-generic  vmlinuz-3.13.0-29-generic  vmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-27-generic  vmlinuz-3.13.0-30-generic  vmlinuz-3.13.0-37-generic
tj@Maingear:/boot$ sudo apt-get purge vmlinuz-3.13.0-27-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vmlinuz-3.13.0-27-generic
E: Couldn't find any package by regex 'vmlinuz-3.13.0-27-generic'

```


> **oldfred said:**
> If you have an LVM install or LVM encrypted install changing the size if /boot is a lot more difficult.

Best just to maintain a minimum number of kernels in /boot. I normally keep 2 current and one old one. 

       I prefer synaptic but you can use command line:

 Determine your current kernel:
uname -a
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

---

### Post by ian-weisser on 2014-11-07
Re-read post #5, paying close attention to the package names to remove.
'vmlinuz' is not part of a package name, and the package manager is trying to tell you that.

---

### Post by Bucky Ball on 2014-11-07
And just to refresh your memory of oldfred's instructions, you need to run 'uname -a' to get your kernel details, then:

```
cd /boot
ls vmlinuz*
sudo apt-get purge linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
```

... where {XX,XX,XX,XX,XX,XX} is your kernel number. Hit return after each command. And oldfred's example:

```
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic 
```

... replacing '3.8.0-{17,18,19,21,22,23,24}' with the details of your kernel. 

It is much easier via Synaptic, but this is fine.

---

### Post by macsociety on 2014-11-07
Thanks all.  Old Kernels erased, freed up space..... and not my 14.04-1LTS is 14.10

TJ

---

### Post by Bucky Ball on 2014-11-07
Excellent. Trouble is, you'll be needing to upgrade that in six months rather than five years. But if that is not a problem, great! Good luck and enjoy ... ;)

I generally use an LTS release as my main squeeze (I need stability and reliability) and have three other partitions for installing playthings (occasionally a Ubuntu interim release or another distro). Different strokes and all that.

---

### Post by macsociety on 2014-11-08
Does the OS have to be upgraded in 6, like it stops working?  Or just recommend it be upgraded? TJ

---

### Post by Bashing-om on 2014-11-08
macsociety; Hoo Boy !

Now we are getting deep.

Generally:
There are as many ways to administer a system as there are people administering a system. Each and every system may be different, in that long run.
Post #6 is certainly one way, for those of us who prefer the (C)ommand (L)ine (I)nterface. Equally effective can be the GUI alternatives. I am the more comfortable from the CLI as the greater information is imparted.
Here in the later releases, normal nominal house cleaning should remove those no-longer needed kernels ( else there is a problem that requires addressing) .

I am of the opinion that the package manager knows what it is doing and I accept all recommendations - In the event that I do not accept, I remove the offending software from the system so the package manager no longer tracks it. Always keep the package manager happy.

Now if there be specific issues, we can get the more specific.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-11-08
> **macsociety said:**
> Does the OS have to be upgraded in 6, like it stops working?  Or just recommend it be upgraded? TJ

14.10 will be supported for only 9 months (July 2015).
14.10 users are expected to migrate to 15.04, then 15.10, then 16.04, etc. I have done this for years and it isn't onerous. I like getting new versions of my favorite applications.

If you remain on 14.10, security patches and bugfix updates will cease in July 2015. The Ubuntu software repositories will also be closed (inaccessible), and support here in this forum will be limited to "you should install a supported version of Ubuntu". Using an unpatched system is _not_ advisable if your system uses the big, dirty internet.

If you do not migrate to 15.04 before it reaches end-of-life in January 2016, that upgrade path will close when 15.04's repositories are closed. Then your only option will be a reinstall.

So will your system stop working? Not immediately. But it already failed on you once.

Oh, and I recommend against using the -d flag with do-release-upgrade unless you are familiar with how Ubuntu works and how to fill out good bug reports.

---

### Post by macsociety on 2014-11-08
My system is not mission critical so yes, I plan on updating with each new release.  If **** hits the fan, will re-install from scratch.  I own many systems so always have fall-back.

As for know Ubuntu.... no I am not a linux expert.  Enough to get in trouble as they say.  ;)

I did that -d as the system would not update unless I used it.  So did it.  If she blew, I would start all over.  hehe

Thanks for the answers and help along the way.

TJ

> **ian-weisser said:**
> 14.10 will be supported for only 9 months (July 2015).
14.10 users are expected to migrate to 15.04, then 15.10, then 16.04, etc. I have done this for years and it isn't onerous. I like getting new versions of my favorite applications.

If you remain on 14.10, security patches and bugfix updates will cease in July 2015. The Ubuntu software repositories will also be closed (inaccessible), and support here in this forum will be limited to "you should install a supported version of Ubuntu". Using an unpatched system is _not_ advisable if your system uses the big, dirty internet.

If you do not migrate to 15.04 before it reaches end-of-life in January 2016, that upgrade path will close when 15.04's repositories are closed. Then your only option will be a reinstall.

So will your system stop working? Not immediately. But it already failed on you once.

Oh, and I recommend against using the -d flag with do-release-upgrade unless you are familiar with how Ubuntu works and how to fill out good bug reports.

---

### Post by macsociety on 2014-11-08
What I have noticed so far is slower boot..... compared to 14.04-1 LTS and workspace switching is clunky with some apps and not smooth switching.

Otherwise apps appear to run OK, etc....

TJ

---

