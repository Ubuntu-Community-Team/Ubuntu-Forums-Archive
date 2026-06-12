---
title: "The package system is broken - unmet dependencies and no space on /boot"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by phil215 on 2016-11-14
I've been trying to solve this for a few hours now and read many posts on similar faults.
All useful command line suggestions have been tried, but they have failed to solve the problem.
There's an accumulation of kernels in /boot that are wasting disk space.
Trying to purge an old one was unsuccessful because of the lack of space.
This lack of space is clearly the reason for failure of the recommended command: "sudo apt-get -f install".
I would like to install BleachBit to help clean my system, but the Software Centre prevents any updates until this one is solved!

My Ubuntu release is 12.04.5 LTS and it's running kernel version 3.13.0-101-generic. Please help!

Here's the output from the Ubuntu Software Centre updater:
   ...
```
(Reading database ... 1192000 files and directories currently installed.)  
 Unpacking linux-headers-3.13.0-101 (from .../linux-headers-3.13.0-101_3.13.0-101.148~precise1_all.deb) ...  
 No apport report written because MaxReports is reached already  
 dpkg: error processing /var/cache/apt/archives/linux-headers-3.13.0-101_3.13.0-101.148~precise1_all.deb (--unpack):  
  unable to create `/usr/src/linux-headers-3.13.0-101/arch/cris/include/arch-v32/arch/ptrace.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-101/arch/cris/include/arch-v32/arch/ptrace.h'): No space left on device  
 dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)  
 Errors were encountered while processing:  
  /var/cache/apt/archives/linux-headers-3.13.0-101_3.13.0-101.148~precise1_all.deb 
 dpkg: dependency problems prevent configuration of linux-headers-3.13.0-101-generic:  
  linux-headers-3.13.0-101-generic depends on linux-headers-3.13.0-101; however:  
   Package linux-headers-3.13.0-101 is not installed.  
 dpkg: error processing linux-headers-3.13.0-101-generic (--configure):  
  dependency problems - leaving unconfigured  
 dpkg: dependency problems prevent configuration of linux-headers-generic-lts-trusty:  
  linux-headers-generic-lts-trusty depends on linux-headers-3.13.0-101-generic; however:  
   Package linux-headers-3.13.0-101-generic is not configured yet.  
 dpkg: error processing linux-headers-generic-lts-trusty (--configure):  
  dependency problems - leaving unconfigured  
 dpkg: dependency problems prevent configuration of linux-generic-lts-trusty:  
  linux-generic-lts-trusty depends on linux-headers-generic-lts-trusty; however:  
   Package linux-headers-generic-lts-trusty is not configured yet.  
 dpkg: error processing linux-generic-lts-trusty (--configure):  
  dependency problems - leaving unconfigured
```

---

### Post by nikefalcon on 2016-11-15
Have you tried clearing downloaded packages?
```
sudo apt-get clean
```
or manually:
```
 rm /var/cache/apt/archives
```

How is your disk set up? Is /boot on a partition of its own or shared with the root(/)? What about /home?

---

### Post by ajgreeny on 2016-11-15
Let's see the output of command ```
df -h
``` in terminal please which will tell us what is going on with your system partitions.

---

### Post by phil215 on 2016-11-15
Thank you both for your replies.
I removed the header file in /var/cache/apt/archives.
Then, when I opened the Software Centre it insisted on performing a repair.
There is no option, it **will** go through the motions, regardless.
This entailed yet another download of the offending header file, i.e. 
linux-headers-3.13.0-101_3.13.0-101.148~precise1_all.deb.
The subsequent update resulted in the same error as shown in my original post.

Here's the output from the “df -h”: 

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb8        19G   15G  3.2G  82% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           354M  980K  353M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   76K  1.8G   1% /run/shm

```

Further comment: I've been using this version of Linux since April 2014, and happily I've experienced very few problems.
Unfortunately, this latest predicament is proving to be extremely tiresome, as I seem to be going around in circles and getting nowhere fast.
It would appear that the housekeeping embedded in this distribution is wanting.
Too many old kernels are stored and they are wasting too much space. Where's the magic bullet to fix this problem, please?

---

### Post by ian-weisser on 2016-11-15
There are two magic bullets that will prevent this problem in 12.04. And it's fixed in 16.04. 
Neither of the solutions will fix an already-broken system - they are merely preventative.

[EDIT]To fix an already-broken system:
1) Use dpkg (not apt) to remove one or more older kernel HEADER packages to free enough space for apt to work. 
2) Run apt-get autoremove to remove obsolete kernels and other packages.
3) Use apt-get to remove the rest of the obsolete kernel header packages

Once it's fixed, we can discuss the magic-bullet to prevent future occurrences.

---

### Post by Impavidus on 2016-11-15
The error comes from a header package and you have some disk space left on your root partition (not much, but enough), so I think you ran out of inodes. That happens if you don't remove old header packages. You can run```
df -i
``` to check.

Let's first get a list of your installed packages and see which of those can be removed```
uname -r

dpkg -l | grep linux-header
```Then remove some old headers packages with dpkg or even manually to give apt-get room to work, then allow apt-get to bring the package manager in a consistent state again and remove the old stuff.

---

### Post by phil215 on 2016-11-15
Thanks Ian and Impavidus. Here are the results of your suggested commands:

1) df -i
```

   Filesystem      Inodes   IUsed  IFree IUse% Mounted on
/dev/sdb8      1220608 1215385   5223  100% /
udev            211442     566 210876    1% /dev
tmpfs           216199     504 215695    1% /run
none            216199       3 216196    1% /run/lock
none            216199       5 216194    1% /run/shm

```

2) uname -r
```

3.13.0-101-generic

```

3) dpkg -l | grep linux-header
```

pi  linux-headers-3.11.0-15                     3.11.0-15.25~precise1               Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-15-generic             3.11.0-15.25~precise1               Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-19                     3.11.0-19.33~precise1               Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-19-generic             3.11.0-19.33~precise1               Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-20                     3.11.0-20.35~precise1               Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-20-generic             3.11.0-20.35~precise1               Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-26                     3.11.0-26.45~precise1               Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-26-generic             3.11.0-26.45~precise1               Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-100                    3.13.0-100.147~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-100-generic            3.13.0-100.147~precise1             Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-3.13.0-101-generic            3.13.0-101.148~precise1             Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                     3.13.0-45.74~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic             3.13.0-45.74~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                     3.13.0-46.79~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic             3.13.0-46.79~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                     3.13.0-48.80~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic             3.13.0-48.80~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                     3.13.0-49.81~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic             3.13.0-49.81~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                     3.13.0-51.84~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic             3.13.0-51.84~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                     3.13.0-52.86~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic             3.13.0-52.86~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                     3.13.0-53.89~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic             3.13.0-53.89~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                     3.13.0-54.91~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic             3.13.0-54.91~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                     3.13.0-55.94~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic             3.13.0-55.94~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                     3.13.0-57.95~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic             3.13.0-57.95~precise1               Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                     3.13.0-61.100~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic             3.13.0-61.100~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                     3.13.0-62.102~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic             3.13.0-62.102~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                     3.13.0-63.104~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic             3.13.0-63.104~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                     3.13.0-65.106~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic             3.13.0-65.106~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                     3.13.0-66.108~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic             3.13.0-66.108~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                     3.13.0-68.111~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic             3.13.0-68.111~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                     3.13.0-71.114~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic             3.13.0-71.114~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-73                     3.13.0-73.116~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73-generic             3.13.0-73.116~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                     3.13.0-74.118~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic             3.13.0-74.118~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                     3.13.0-77.121~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic             3.13.0-77.121~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                     3.13.0-79.123~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic             3.13.0-79.123~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-83                     3.13.0-83.127~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic             3.13.0-83.127~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                     3.13.0-85.129~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic             3.13.0-85.129~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                     3.13.0-86.131~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic             3.13.0-86.131~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                     3.13.0-88.135~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic             3.13.0-88.135~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                     3.13.0-91.138~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic             3.13.0-91.138~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                     3.13.0-92.139~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic             3.13.0-92.139~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                     3.13.0-93.140~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic             3.13.0-93.140~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                     3.13.0-96.143~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic             3.13.0-96.143~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-98                     3.13.0-98.145~precise1              Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic             3.13.0-98.145~precise1              Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-saucy             3.11.0.26.23                        Generic Linux kernel headers
iU  linux-headers-generic-lts-trusty            3.13.0.101.92                       Generic Linux kernel headers

```

How can I best use dpkg to remove a few old headers?
Quite frankly, I don't see the point in keeping more than two or three old ones on the system.
If I had been warned about the build up I would have had an opportunity to do something about it before crunch time arrived.
I shall give this version one more chance before I give up and migrate to v16.

---

### Post by ajgreeny on 2016-11-15
Let's start by trying to remove a few of these header packages of which you seem to have 36 versions, using dpkg.  Do you still also have all those kernels as well?  If so they will account for about 8GB of disk space, but we can deal with those later if necessary.

See what happens if you run command```
sudo dpkg -P linux-headers-3.11.0-19 linux-headers-3.11.0-19-generic linux-headers-3.11.0-20 linux-headers-3.11.0-20-generic linux-headers-3.11.0-26 linux-headers-3.11.0-26-generic
```
You may possibly get a dependency error but it will tell us what else needs to be removed.

It that does work we can then remove many more packages, either the same way, or better, I suggest using synaptic, which gives you good search options and allows you to remove any package that is installed.

---

### Post by phil215 on 2016-11-15
It worked! Good work ajgreeny, well done, and thanks very much.

Here are the five commands that straighten out my system and therefore constitute my particular magic bullet:
```

sudo dpkg -P linux-headers-3.11.0-19 linux-headers-3.11.0.19-generic
sudo dpkg -P linux-headers-3.11.0-20 linux-headers-3.11.0.20-generic
sudo dpkg -P linux-headers-3.11.0-26 linux-headers-3.11.0.26-generic
(N.B. This last command failed with dependency problems, but I ploughed on.)

sudo apt-get -f install
sudo apt-get install synaptic

```

I hope this documentation is helpful to others, should they experience similar troubles with Ubuntu 12.04. Thanks again to all involved.
How do I mark this as solved?

---

### Post by ian-weisser on 2016-11-15
Marking 'SOLVED' is premature.
You have merely cleared enough space on your system to begin using apt again.
In a few weeks, the problem will return.

Clean out the rest of those headers using 'sudo apt-get autoremove'. If that fails, remove them using apt-get manually.
Mark your calendar once or twice a year to clean out obsolete headers...or stop subscribing to headers if you don't actually use them.
Then use the 'Thread Tools' at the top of the thread to mark the thread [SOLVED]

---

### Post by ajgreeny on 2016-11-15
I like to keep my housekeeping under my manual control so I use synaptic to remove unneeded versions of the kernel and headers.

First I find what kernels are installed with command **ls /boot | grep vmlinuz**
```
user@XubuntuXenial:~$ ls /boot | grep vmlinuz
14:vmlinuz-4.4.0-46-generic
15:vmlinuz-4.4.0-47-generic
```
If more than two versions show in the list I search for the oldest versions by version number alone, eg search name only for 4.4.0-45 using synaptic and mark all the kernel and header packages found for complete removal which is very quick to do.  
That way I never have any extra unwanted kernel or header versions sitting on my system.

In 16.04 and later ```
sudo apt-get autoremove
``` will get rid of all but the two most recent kernels but I'm not sure if it also removes header packages.

---

### Post by phil215 on 2016-11-16
Okay Ian, I shall refrain from marking this thread as solved until we are done with the clutter in /boot, at least.

I see there are still a collection of file sets for each old kernel.
E.g. The oldest comprises: abi-3.11.0-26-generic, config-3.11.0-26-generic, initrd-img-3.11.0-26-generic, System.map-3.11.0-26-generic and vmlinuz-3.11.0-26-generic.
So, that's another five files for each kernel.
Is it safe to manually delete these without any nasty consequences?

Btw, I've used Synaptic to remove a couple more old kernels, but when I used the Software Centre just now to try installing the much talked about Ubuntu-tweak, it failed. From the “unsafe download” warning screen I was offered the options of “Ok” and “Repair”. After two attempts, neither of these resulted in a complete installation.

Today, I successfully executed:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

Now I feel ready to hear what you had in mind regarding the magic-bullet to prevent future occurrences of the kernel accumulation problem. I've seen some clever scripts that claim to prevent the kernel logjam that crippled my system recently. Was it one of these perhaps?

---

### Post by ian-weisser on 2016-11-16
> **phil215 said:**
> Okay Ian, I shall refrain from marking this thread as solved until we are done with the clutter in /boot, at least.
Your problem is caused by header packages that have consumed all your inodes, not lack of capacity in /boot.


> **phil215 said:**
> I see there are still a collection of file sets for each old kernel.
E.g. The oldest comprises: abi-3.11.0-26-generic, config-3.11.0-26-generic, initrd-img-3.11.0-26-generic, System.map-3.11.0-26-generic and vmlinuz-3.11.0-26-generic.
So, that's another five files for each kernel.
Is it safe to manually delete these without any nasty consequences?
Do NOT delete any files in boot using 'rm' unless you are skilled in troubleshooting dpkg errors.
Let apt clean out /boot for you: Delete old kernel packages using apt-get.
Oh, and DO NOT accidentally remove the currently-running kernel. That would be bad.


> **phil215 said:**
> 
Today, I successfully executed:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```
'clean' destroys all the work of 'autoclean'. Neither was particularly helpful to you - packages cached locally are not the problem. 
'autoremove' should have spent a long time removing old kernel packages and old kernel header packages. If not, then there is another layer of the problem still to discover.
Check that you are down to two or three installed kernels in /boot.
Check that you are down to coresponding header kerlel header packages. (see Post #6)
Check that you inodes are well below 100%. (see Post #6)

---

### Post by phil215 on 2016-11-16
Thanks again ajgreeny and Ian.
It looks like I'm not quite out of the woods yet.

The current inode usage value Iuse% = 94%
The current vmlinuz file count = 33

A re-run of “sudo apt-get autoremove”, reports:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

So, no it doesn't remove the old kernels as expected.
Is the autoremove option in 12.04 supposed to work the same as in 16.04?

---

### Post by ian-weisser on 2016-11-16
> **phil215 said:**
> 0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Well, that's a shame. But could be much worse.
Happily, removing those obsolete kernel packages and header packages using apt-get or Synaptic is merely a bit tedious, not difficult.
Go to it.

> **phil215 said:**
> Is the autoremove option in 12.04 supposed to work the same as in 16.04?
Mostly, but that doesn't seem relevant.
Autoremove is an ordinary, non-magic tool. It's not psychic, and users are notoriously vague, capricious, and contradictory about their intent,
So developers deliberately made autoremove fragile - better to fail safe instead of destroying a user's system.
Because of that fragility, autoremove's logic can easily be (unknowingly) defeated by an unskilled user in several easy ways.

Troubleshooting autoremove is a very different topic; you need to learn all about apt-marking and the apt-mark command, and back up your data, before we go down that path. Monkeying with autoremove can be risky for the unskilled. It's job is to *remove without asking.*

If you cannot rely upon autoremove, then your magic bullet will wind up being a calendar (once or twice a year) and a few jotted notes reminding you how to houseclean.

---

### Post by Impavidus on 2016-11-16
> **phil215 said:**
> 
So, no it doesn't remove the old kernels as expected.
Is the autoremove option in 12.04 supposed to work the same as in 16.04?

If I'm not mistaken, the ability to autoremove old kernels and headers was introduced in Ubuntu 13.10. And at first it missed some packages that should've been autoremovable.

Best thing to do is use synaptic to search for all old headers and kernels and mark them for complete removal. They are named linux-image-*-generic, linux-image-extra-*-generic, linux-headers-*, linux-headers-*-generic. Possibly some others too, so search for the version numbers and remove all the old 3.11.0-xx packages.

One cleanup every 6 months should be sufficient. If you clean up now, your problem will be gone. 12.04 has 5 months of support left, so before the problem reoccurs you'll have to move to a more recent version (I suggest skipping 14.04 and directly installing 16.04 from live disk) and this newer version can autoremove the old kernels and headers. And even of you don't upgrade, the old kernels and headers will stop accumulating, as no updates will be provided. But that means no security upgrades, so not a good idea.

---

### Post by phil215 on 2016-11-17
Thanks for all the good advice. I've been busy using Synaptic to remove a number of obsolete kernels, bringing the total number on the system down to five. That's very safe; one to boot from and four older backup kernels.

The inode usage is now under control, with Iuse% = 59%

I shall upgrade to v16.04 in due course.

Thanks to all contributors to this thread and your help with teaching me how to keep a tidy system!

---

