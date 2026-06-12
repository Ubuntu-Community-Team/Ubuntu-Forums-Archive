---
title: "Latest libc6 /tzdata is broken?"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by mejesster on 2006-08-24
When attempting to install xfce4-cpufreq-plugin, it depends on libc6, which it attempts to get and install, but that depends on tzdata.  Now I've seen several posts on various sites about problems where users are unable to install the latest tzdata/libc6 because of an error where tzdata wants to overwrite something from package locales, but nobody has ever posted a solution. Locales is a package that ubuntu-minimal uses.  Any suggestions for how to get tzdata to install, for me to remove locales without removing ubuntu-minimal, or some other way for me to get libc6 installed and working? The precise error is here:
mejesster@mejesster-laptop:/etc/apt$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6-i686 tzdata
The following NEW packages will be installed:
  tzdata
The following packages will be upgraded:
  libc6-i686
1 upgraded, 1 newly installed, 0 to remove and 541 not upgraded.
2 not fully installed or removed.
Need to get 0B/1440kB of archives.
After unpacking 6005kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tzdata libc6-i686
Install these packages without verification [y/N]? y
(Reading database ... 66879 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2006g-2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/tzdata_2006g-2_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2006g-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mejesster on 2006-08-25
bump.
The threads I've found on here seem to suggest that I have to force install an older version of libc6 to get rid of the errors, but I really want to get xfce4-cpufreq-plugin working, and that depends on (what I assume is the troublemaking) libc6.
Oh, running Xubuntu 6.06.
If I should move this topic to another part of the forums, let me know.

---

### Post by PaperPilot on 2006-12-25
I have tried to install libc6 and tzdata too and I get the message **unsatisfied dependencies (cache broken)**.  I tried to install from a flash drive as the subject machine has no Internet conncetion.  

Have you found a solution to this problem?

---

### Post by mejesster on 2007-01-08
Nope, never found a solution, I just gave up on it for now and allowed my battery life to suffer.  I'm also considering switching back to debian as I've been very frustrated with the way ubuntu doesn't like a lot of debian packages and the official repositories use a lot of dated packages.

---

### Post by tacubuntuforums on 2007-02-19
Hi,
It seems to me that the answer is yes. That there's something wrong in the packages dependencies or packages management.

If you search, you'll see that I had a big problem a few months ago. For, who know's what reason, one day a lot of packages were being unintalled during an upgrade of Firefox. The chain of packgs selected for removal went down to the kernel, where it stopped in a Kernel Panic. I was able to fix the disaster but there remained an obsolete package: tzdata (I have read documentation saying that you can uninstall it as soon as you finish your system installation), which seems hard to remove as it will remove beind a lot of crucial packages.

Fo me, now, the problem appeared again when just upgrading packages. I should  upgrade libc6 from version sarge4 to sarge5 and that implies overwriting files 'ownd' by tzdata but which I will never need at all. I've tried rmoving those files before the upgrade , but it doesn't make any difference

So, I understand that package tzdata is usually very little needed after installing the system, also it's obsolete in my installation but i can't remove it and it doesn't let me upgrade important packages. 
Moreover, there's a couple of packages ( libc6-dev, locales) that have been upgraded but can't be configured because they depend on the version of the one i can't install. So I have BROKEN packages

INCREDIBLE!

But don't think it's only a problem with Ubuntu, i'm talking about a Debian install where I mainly do upgrades and very seldom install new things.

Now i'll probably have to spend hours or days (of other things) to try to find a solution to this nonsense and be working with a wobbly system (if i'm not able to downgrade some packages without problems)

Here is the output, after renaming(moving) those files, in case you want to take a look:

```
sudo aptitude install libc6
Reading Package Lists... Done
Building Dependency Tree
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
The following packages will be upgraded:
  libc6
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5029kB of archives. After unpacking 262kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 77037 files and directories currently installed.)
Preparing to replace libc6 2.3.2.ds1-22sarge4 (using .../libc6_2.3.2.ds1-22sarge5_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.3.2.ds1-22sarge5_i386.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Pacific/Palau', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.2.ds1-22sarge5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.3.2.ds1-22sarge5); however:
  Version of libc6 on system is 2.3.2.ds1-22sarge4.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on glibc-2.3.2.ds1-22sarge5; however:
  Package glibc-2.3.2.ds1-22sarge5 is not installed.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 locales
Reading Package Lists... Done
Building Dependency Tree
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
```

----------------------------
Ok, now i discovered that according to aptitude and not to synaptic, removing tzdata is not a big problem, no other package will be deleted.
I try to delete it, BUT there's still one error because aptitude tries to upgrade the packg (libc6) that overwrites tzdata files. So I hold the package and now the problem is that the packages that were recently downloaded for upgrade (libc6-dev, locales),  but were not able to be configured after, produce an error so nothing is done.

It drives me NUTS!, NUTS!, NUTS!

I find no way to downgrade the packages:  libc6-dev, locales, and no way to remove firrst tzdata and then continue with the configuration of these recently downloaded packgs.

I'm getting to the conclusion that many problems in the so called civilized world are due to a meteoric philosophy in software engineering,  trying to do new things just for marketing  instead of fixing/repearing/improving the basement.

Any Help?

---

### Post by tacubuntuforums on 2007-02-19
OK, thank you.

I managed to fix everything

The 4 or 5 applications to manage packages, the different sintaxis and all together is such a mess that took me a while.

By the way, the files that I didn't need and belonged to tzdata were relaced by exactly the same ones!!

I think that aptitude and synaptic should FIRST DELETE packages AND THEN REPAIR BROKEN (configure)/UPGRADE/INSTALL.

FIRST DELETE AND THEN ADD MORE. ALWAYS!

---

### Post by er0k on 2007-02-23
> **tacubuntuforums said:**
> OK, thank you.

I managed to fix everything

The 4 or 5 applications to manage packages, the different sintaxis and all together is such a mess that took me a while.

By the way, the files that I didn't need and belonged to tzdata were relaced by exactly the same ones!!

I think that aptitude and synaptic should FIRST DELETE packages AND THEN REPAIR BROKEN (configure)/UPGRADE/INSTALL.

FIRST DELETE AND THEN ADD MORE. ALWAYS!

How exactly did you manage to fix everything? I'm having the same problems, could you please provide some more details?

edit: nevermind, I fixed it by using the force package option in synaptic to downgrade libc6 :)

---

### Post by alanm1 on 2007-02-24
I'm posting this although I'm running Debian because of the parallels between Debian and Ubuntu and the fact that searching for a solution to this libc6/tzdata contention problem turned up this thread.

My system is based on the Debian stable release (Sarge 3.1) with a few packages from the testing release (Etch).  One of these testing packages is tzdata, which is not in stable.  The latest stable version of libc6 (part of the fifth update of Sarge, see  [http://www.debian.org/News/2007/20070218](http://www.debian.org/News/2007/20070218)) now contains time zone data duplicating that held by tzdata.  When trying to upgrade to this latest version of libc6 I too got:

<code>
Preparing to replace libc6 2.3.2.ds1-22sarge4 (using .../libc6_2.3.2.ds1-22sarge5_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.3.2.ds1-22sarge5_i386.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Pacific/Palau', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
</code>

As tacubuntuforums suggested one possible solution is to delete tzdata but trying to do this within aptitude wouldn't work as the install of libc6 has priority.  Instead I used (hit '**n**' at the 'Do you want to continue?' prompt):

<code>
#aptitude -DP remove tzdata
</code>

This lists which packages would automatically be removed along with tzdata, which for my system were build-essential, g++, g++-3.3, libc6-dev, libmysqlclient14-dev, libstdc++5-3.3-dev, locales and zlib1g-dev.  Having looked at the description of each of these packages I felt I could let these be deleted and then re-install them later as necessary.  Of course if you are unsure, do a system backup first (I use mondoarchive).  So I repeated the '#aptitude -DP remove tzdata' command replying 'y' at the prompt, which successfully removed tzdata.  

I then re-installed the above automatically removed packages.  

Oddly, at least to me, when I tried '#**apt-get** remove tzdata' it warned that, as well as automatically removing the packages that aptitude removed, it was also going to remove kde and other kde related packages.  I presume that the configuration data for aptitude and apt-get is out of line on my system.

The moral of this: you can mix stable and testing packages (at least in Debian) but you may occasionally come across contention between the 2 sets.

---

### Post by FRuMMaGe on 2007-05-16
I have the same problem!

But when I tried to downgrade libc6 it completely destroyed my system.  Now I can't use synaptic at all, and when I try and use apt-get i'm faced with a "Floating Point Exception".

Can anyone help me fix libc6 please??
I'm running Ubuntu 6.06

---

### Post by FXWGBill on 2007-05-23
My notes from the same problem:

Figured out that had to back up to the previous version of tzdata and lock it
did this by going to:  /var/cache/apt/archives   and invoking:
	 sudo dpkg -i tzdata_2007e-6ubuntu1_all.deb
	 
NOTE!!!:  THE  f  version of tzdata is the bad one!!! 	 

	 (says if need to 'adjust the time' use:  dpkg-reconfigure tzdata  )
	 
Once that was done, then loaded up synaptic and locked down tzdata

Next... starting running the updates again, and NOW we seem to have an
issue with:  

/var/cache/apt/archives/remote-tty_4.0-10_i386.deb    going to see if I can unmark it and that fix it for now!!

It did unmark and now we can just go back and finish the upgrade

---

### Post by Rabindranath on 2007-06-29
I am also having the same problem. Could someone post how to remove tzdata. I am not an expert in the terminal and give me the code I have to type in the terminal. I use kubuntu 7.04 and it doesnt allow mw to install  libc6. Please help me.

---

### Post by athaki on 2007-08-28
```
 sudo apt-get remove tzdata

sudo apt-get install -f tzdata
sudo apt-get install util-linux
sudo apt-get install locales
sudo apt-get install ubuntu-minimal

```

You should be able to rebuild if you reinstall the other packages after you install these four

---

