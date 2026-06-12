---
title: "No upgrade, no update, no build essential..."
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-06-28
Upgrade returns authentication failure. (don't really want to anyway, just tryin' to install wireless)

Can't update - not all repositories indexes are download-able.

Can't install 'build-essential' (can't find package). 
> chuckdl@chuckdl-laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
chuckdl@chuckdl-laptop:~$ 


Help?

---

### Post by buccaneere on 2008-06-28
This tell me anything?

> chuckdl@chuckdl-laptop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  g++ g++-4.1 libstdc++6-4.1-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libstdc++6-4.1-dev 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6052kB of archives. After unpacking 24.6MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12) but 2.5-0ubuntu14 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
chuckdl@chuckdl-laptop:~$ 

---

### Post by buccaneere on 2008-06-28
Any help here? It came up after I deleted all source.list, and re-listed the Edgy repository list at psychocats' page...

---

### Post by saidinesh5 on 2008-06-28
@
Can't update - not all repositories indexes are download-able.

and cant install build-essentials..

yea that happened with me too....but then i figured out that was the problem with my internet connection!(so cant really help you out here)...and without updating the package list, synaptic doesnt know where to look for the packages...so check your internet connection first...and also you could find the deb packages of build-essentials on the ubuntu CD itself....use it..

---

### Post by buccaneere on 2008-06-28
Thanks saidinesh...

I made sure to add the CD to the source list. Still no luck.

Some else with a similar problem had a network connection indicated as the reason, but the solution did not involve his connection.

---

### Post by saidinesh5 on 2008-06-28
well yes..i faced even that problem too..lolz ..i am a complete beginner to this...so i dont really know the technical aspects of wht went wrong , but i was desperately needing those build-essentials...and luckily in the ubuntu cd , you ve got a package called build-essentials, simply double click on it...and it will install all the build-essentials for you..mean while lemme look for the actuall solution of your problem..

in hardy CD, you have it in

<cdrom>/pool/main/b/build-essentials

---

### Post by buccaneere on 2008-06-28
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5


> chuckdl@chuckdl-laptop:~$ gpg --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
**[COLOR="Red"]gpg: can't access `/home/chuckdl/.gnupg/trustdb.gpg': Permission denied[/COLOR]**
gpg: fatal: can't init trustdb: trust database error
secmem usage: 1408/1408 bytes in 2/2 blocks of pool 1408/32768
chuckdl@chuckdl-laptop:~$ 

**[COLOR="Red"]Can the server not verify data on my computer???[/COLOR]**

---

### Post by saidinesh5 on 2008-06-28
@
gpg: can't access `/home/chuckdl/.gnupg/trustdb.gpg': Permission denied

hey check this out

[http://ubuntuforums.org/showthread.php?t=185584](http://ubuntuforums.org/showthread.php?t=185584)

---

### Post by buccaneere on 2008-06-28
Errors/dependencies working...

> chuckdl@chuckdl-laptop:~$ ls -lah ~/.gnupg
total 28K
drwx------  2 chuckdl chuckdl 4.0K 2008-06-28 01:59 .
drwxr-xr-x 24 chuckdl chuckdl 4.0K 2008-06-28 02:10 ..
-rw-------  1 chuckdl chuckdl 9.1K 2008-06-27 23:33 gpg.conf
-rw-------  1 chuckdl chuckdl 3.6K 2008-06-28 01:59 pubring.gpg
-rw-------  1 chuckdl chuckdl    0 2008-06-27 23:33 pubring.gpg~
-rw-------  1 chuckdl chuckdl    0 2008-06-27 23:33 secring.gpg
-rw-------  1 root    root    1.2K 2008-06-27 23:35 trustdb.gpg


chuckdl@chuckdl-laptop:~$ sudo chown -R chuckdl.chuckdl ~/.gnupg
Password:
chuckdl@chuckdl-laptop:~$ gpg --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
chuckdl@chuckdl-laptop:~$ 


> chuckdl@chuckdl-laptop:~$ gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
**[COLOR="Red"]OK[/COLOR]**
chuckdl@chuckdl-laptop:~$ 

---

### Post by adityadeva on 2008-06-28
Ten sticking points for new Ubuntu users
By Michael Reed on June 27, 2008 (9:00:00 PM)

Share    Print    Comments   

With Ubuntu, Canonical has had notable success in convincing people to switch from other platforms, but potential Ubuntu users are still running into trouble in several areas. Having spent some time on Canonical's forums, I've identified 10 points that seem to be common sticking points for new users -- that is, problems that have the potential to prevent a new user from adopting Ubuntu in the long term. These problems span the entire Ubuntu experience, but they all have two things in common: they are all serious enough to evoke the dreaded "I tried Linux but it didn't work" excuse, and they are all solvable.

Screen setup

Ubuntu is still bad at properly detecting and setting up the display. Once it's gone wrong, there isn't much you can do from the GUI setup tool -- it either lies about your screen settings or offers inappropriate screen modes. Anyone for 640x480@52Hz on a 19-inch CRT?

This is probably the most frequently reported complaint on the beginner forum. Other operating systems can set up the screen, so why can't Linux?

From the user perspective, the solution involves some research and the editing of the xorg.conf config file. This is bad, because if the user makes a single mistake -- presuming the typical user is resourceful enough to make it this far -- it's all too easy to render the whole Ubuntu setup unusable.

This problem is so widely acknowledged as a weakness of Ubuntu that I was surprised that Ubuntu 8.04 was still getting it wrong. Ubuntu should use its leadership muscle to create a robust, reliable solution from scratch or champion an existing project.
Boot management

I'm against the idea of making things unnecessarily flashy, but GRUB is both feature-poor and complicated to configure.

Smart Boot Manager is a boot manager that has more run-time configuration features than GRUB without being frivolous. Other boot managers, such as GAG, offer an attractive GUI interface. Both of these GRUB alternatives that I mentioned are GPL projects.

Having the boot manager overwritten by a Windows upgrade is another common complaint. A feature to reinstate the boot manager from the install disk menu would help people who can no longer boot Ubuntu.
Mounting

It's a shame that Ubuntu doesn't come with a GUI tool to configure the boot-time mounting of new partitions. Most advice on this issue revolves around editing /etc/fstab. A common complaint is that the partition can be seen but the permissions are wrong. There are a few other gotchas that can come up when a user is trying to make the system recognise a new partition.

Such a utility could be added to the live CD, as mounting a partition from the command line is difficult for non-experts.
Installation

I have a pet niggle with the Ubuntu installer: it's not very forgiving of network errors, often hanging at about 92%. I suspect that Ubuntu pings a test server, and if it receives a reply, assumes that the machine is connected to the Internet. The snag is that there is a class of networking problems that only affect DNS resolution.

The workaround for this problem is simple: disconnect from the network before beginning the install.

Ideally, the Ubuntu installer would pop up a warning when its attempt to connect to the server has failed, then finish the install. I'd settle for an error box stating that the install couldn't complete, accompanied with advice about how to proceed. Even a note saying, "If the installer stops at 92%, try installing without the network connected" would be better than an installer that stops dead with no explanation.
Sound configuration

Sound under Linux is a bit of a mess. There are a lot of different systems, and a lot of overlapping functionality. This needn't matter if the system sets itself up properly, but sound setup on Linux is hardly what I would call robust. As a result, when things go wrong, users have to hit the forums and the config files.

Some users report that sound is working but that only one program can use it at once. In extreme situations, this may lead to people switching off system alert sounds so that application sound works. Sometimes people can't get sound working in Web videos in Firefox. The common fixes for that problem can leave them with a system in which sound works only in Firefox.

Canonical is trying to solve the Linux sound problem by standardising on ALSA with Pulse Audio. This combination has the potential to be a killer system in the long run, but at the moment a lot of people can't get their sound up and running.
Networking: IPv6 support

Version 4 of the Internet Protocol (the layer that connects software to the Internet) is in the process of being superseded by version 6. By default, Ubuntu supports the new version, but many Internet service providers have not switched over yet. When IPv6 support has not been implemented properly by an ISP or by a broadband router, an Ubuntu user can experience slow access or even a total lack of access to the Internet.

From reading the forums it seems that Ubuntu may have defaulted to IPv6 support too early. IPv4 support can be re-enabled, but it involves editing configuration files. If Canonical has decided to be ahead of the curve, it should make it easier for people to switch back to IPv4.

I wonder how many people have given up on Ubuntu because Web browsing seemed slow? I suspect that some people are left thinking that Ubuntu doesn't support their network hardware, but in fact they were running afoul of incompatibilities with the new IP standard.

A simple check-box configuration for switching between IPv4/6 would save a lot of headaches for users who have run into problems.
Power and hibernation

Power management is vital for laptop users, and hibernating a desktop computer can be a cool approach to startup and shutdown.

Canonical should intensify its efforts in this area, because for most users, a laptop that doesn't sleep properly is a broken laptop. Ubuntu features a hardware testing and reporting application, but it didn't even prompt me for details about my experiences with power management.
Email migration

One of the most common things that new users want to do is migrate their email from their Windows setup. If they were lucky enough to be using a client such as Thunderbird on Windows, they can migrate their email with a combination research and some complicated file copying, all within an unfamiliar interface. Transferring email from the most popular Windows email client, Outlook Express, is even more complicated.

This process could be made more approachable with some prominent documentation, or even an email migration tool. I regard this as a fix rather than an enhancement as it refers to such a common and vital activity.
Documentation

How about providing some documentation to help get new users started, covering topics such as "Internet and networking problems" and "Getting the screen set up"? The Ubuntu team could produce a list, like this one, describing some of the most common problems that users are likely to encounter and make some simple suggestions.
Building from source

Ubuntu's package management implementation constitutes a significant enticement for the potential switcher in its own right. However, building packages from source is unavoidable when a desired package isn't in the repositories or the version in the repositories is out of date.

The build instructions in most source packages put the package manager out of sync with the actual packages that are installed. Why doesn't Canonical standardise on one of the GUI build tools in tandem with Checkinstall? Checkinstall installs the compiled application but works with the package manager to keep it in sync with the real state of the system.

By addressing these 10 points, Canonical can improve the Ubuntu experience for new users, and retain more of them who might otherwise become frustrated by problems with relatively simple fixes.

Michael Reed writes about technology, retro computing, geek culture, and gender. He's a also a musician, bicyclist, and comedy writer.

---

### Post by buccaneere on 2008-06-28
> **saidinesh5 said:**
> @
gpg: can't access `/home/chuckdl/.gnupg/trustdb.gpg': Permission denied

hey check this out

[http://ubuntuforums.org/showthread.php?t=185584](http://ubuntuforums.org/showthread.php?t=185584)

Thanks... Will check (*ED.: I got it in archived threads!*). Working backwards SEVERAL dependencies; **bug found** (might be one I read about browsing at another point).

bug details:
> 
Traceback (most recent call last):

  File "/tmp/tmpi3vJ-L/feisty", line 56, in ?
    app.run()

  File "/tmp/tmpi3vJ-L/DistUpgradeControler.py", line 1025, in run
    self.fullUpgrade()

  File "/tmp/tmpi3vJ-L/DistUpgradeControler.py", line 962, in fullUpgrade
    if not self.updateSourcesList():

  File "/tmp/tmpi3vJ-L/DistUpgradeControler.py", line 390, in updateSourcesList
    if not self.rewriteSourcesList(mirror_check=True):

  File "/tmp/tmpi3vJ-L/DistUpgradeControler.py", line 302, in rewriteSourcesList
    if ((len(self.cache[pkgname].candidateOrigin) == 0)

  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 82, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-minimal'

:confused:

---

### Post by saidinesh5 on 2008-06-28
sorry dude cudnt find much info on that...and things now are way beyond my head....told you rite im stil a beginner!
hope you find some solution soon
all d best

---

