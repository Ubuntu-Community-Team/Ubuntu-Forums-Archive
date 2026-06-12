---
title: "HOWTO fix problems regarding broken dependencies"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-06-02
**I'm posting this as a forum user and not as a staff member. First read and understand the entire post before doing anything. This is all on your own risk. Please be very careful**

If you are upgrading from Breezy to Dapper first read this :
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

If your upgrade went wrong you have to fix problems regarding package management first.

It can be very frustrating to handle broken dependencies and/or problems with apt-get/aptitude.

Possible causes : 
-You started dist-upgrading while not having commented non-official Ubuntu repositories
-For some reason you had broken dependencies in Breezy, you didn't notice it and it got worse due to upgrading to Dapper
-Your system became unresponsive while dist-upgrading and you had to reboot after a while waiting.
-You have used too many unofficial repositories or bad ones.

Fear not. In most cases it's fixable. Though you may have to do everything from the terminal which can be intimidating for users.

good luck :)

**THE GENERAL IDEA :**

This is not a howto where you just have to copy-paste every command and press yes. First read and understand the entire post before doing anything. Don't do things you don't understand unless you are willingly taking a big risk. Handling broken dependencies can always be risky. There might be cases that are very hard or (nearly?) impossible to fix. This is all on your own risk.

If you have problems and you need help IMHO it's best to start a new thread. In your own new thread : be elaborate about your problems. **Post the errors you get.** Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

**Make sure you have done all steps even if you think some step in the middle has solved your problems.**

1)Making sure that your sources.list is in order
2)Trying some simple solutions.
3)Zooming in on the actual problems. This is the hard and risky part. It can be a big puzzle to solve even for experienced users. You may have to perform some "tricks". Don't remove essential packages unless you know what you are doing. Be very careful. 
4)Making sure all problems are solved
5)Getting everything back installed
6)Making sure everything is upgraded

Sometimes solving broken dependencies is easier using "apt-get" in other cases "aptitude" is easier. So you need to try to replace "aptitude" with "apt-get" in the commands (I list here).

**PRACTICAL ADVICE :**

**1)Making sure that your sources.list is in order**

First backup your personal files if you haven't done so.

Backup your sources.list :
$sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

Now edit your sources.list , make sure breezy is replaced by dapper everywhere and **comment** all non-official repositories. Or use this clean Dapper sources.list [[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

to edit your sources.list :
$gksudo gedit /etc/apt/sources.list
Or if you are in the terminal :
$sudo pico /etc/apt/sources.list

Read in the new information from your sources.list :
$sudo aptitude update

**2)Trying some simple solutions.**

Let's now try to configure all packages that are unconfigured :
$ sudo dpkg --configure -a

**You might want try RavenOfOdin's solution right now :**
Q4. Package A depends on Package B to install, but Package B depends on Package A to install! HELP!
[http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12)

**3)Zooming in on the actual problems**

Go to ctrl-alt-f1 and log in.

Now try to let apt-get remove all problematic packages automaticaly :
$ sudo aptitude -f remove

Let's try again to configure all packages that are unconfigured :
$ sudo dpkg --configure -a

Here comes the part where you remove all broken packages and all packages which give errors including dependencies by hand. Don't worry if ubuntu-desktop gets removed.

**Don't remove** apt /  linux-386 / linux-686 / linux-k7 / ubuntu-minimal / grub. If it wants to remove any of those packages tell us all packages that it wants to remove. There's information about other important packages below. **Please be careful.**

$sudo aptitude remove -f *packageA *
$sudo aptitude remove -f *packageB* 
$sudo aptitude remove -f *packageC *

Keep removing stuff until there are no more dependencies problems and things get actually removed. 

So if apt is reporting errors or broken dependencies for packageA then try to remove it including all dependencies and the dependencies of those dependencies.................and the dependencies of those dependencies.........and the dependencies of those dependencies........ 

Do the same for packageB, packageC and all other packages you have problems with.

After you have found all packages and dependencies that need removal you could bundle them in a big remove command :
$sudo aptitude remove -f packageA packageB packageC packageD packageE packageF  .......

**Warning **if you see something like this on your screen you should **press no** :
> 
**WARNING:** The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!


Sometimes you have to force packages by hand to install the latest version. $apt-cache show *packagename* will give you the possible versions of the package. Install the version from the official Dapper repos by :
$sudo aptitude install *packagename*=*version* -f

Sometimes it isn't possible to remove packages while there aren't any dependencies involved anymore. In this stage you are probably getting specific errors. Most of the times this means that you have to remove (or alter) some specific configuration file for example "start up" files. After having solved the problem with the problematic files by hand make sure to use the --purge switch to remove the package.

[I]**examples :**
if your problem of broken dependencies is somehow related to getting into X. Something like this may help :
$sudo aptitude remove xserver-xorg x-window-system-core gdm -f --purge
Dependency problems with libc6 :
[http://www.ubuntuforums.org/showthread.php?t=186570](http://www.ubuntuforums.org/showthread.php?t=186570)
Dependency problems with clvm which you don't need unless you are sure that you need it :
$sudo rm /etc/init.d/clvm
$sudo aptitude remove clvm -f --purge[/I]

**4)Making sure all problems are solved**
Let's run this command again to make sure it has removed everything that's problematic :
$ sudo aptitude -f remove

Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. 

**5)Getting everything back installed**

Let's install everything :

$ sudo aptitude install ubuntu-minimal
$ sudo aptitude install ubuntu-base
$ sudo aptitude install xserver-xorg x-window-system-core ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

**6)Making sure everything is upgraded**

And make sure everything is upgraded :
$ sudo aptitude update
$ sudo aptitude upgrade
$ sudo aptitude dist-upgrade

If everything went well your broken dependencies problem is fixed. 

Now do a reboot :
$ sudo reboot

**What if you can't boot into a terminal at all :**

First try booting into recovery mode.

If that doesn't work then boot from a live cd. Mount your Ubuntu Dapper partition, chroot and work from there.

$sudo mkdir /mnt/dapper
use the correct device here .. for example /dev/hda6 :
$sudo mount /dev/hda6 /mnt/dapper
$sudo chroot /mnt/dapper

Now you can work again from dapper.

**MORE IMPORTANT INFORMATION :**

The "--purge" switch tells apt-get to also remove all configuration files of the package. For example : $sudo apt-get remove packageA --purge

Solving these dependencies problems can sometimes be a **big puzzle**. If you are having troubles with clearing these dependencies problems make sure you read and understand this :
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

Or try debfoster. Using debfoster it's relatively easy to remove packages including all it's "children". Only use it if you really **understand** it because it's easy to delete too much. **Be very careful** :
[http://www.ubuntuforums.org/showpost.php?p=1106946&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1106946&postcount=2)

The key meta packages of Ubuntu are :

ubuntu-base consists of ubuntu-minimal and ubuntu-standard which together form the whole base system. ubuntu-minimal is essential.
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

You need a kernel. These are the most important ones :
linux-686 the metapackages which ensures you have always the latest 686 kernel
linux-386 the metapackages which ensures you have always the latest 386 kernel
linux-k7 the metapackages which ensures you have always the latest amd (non-64 bit) kernel

So after a standard ubuntu (gnome) installation ubuntu-base and ubuntu-desktop are installed which makes sure every other ubuntu package is installed.

Here are some information about certain packages :

apt - absolutely necessary
xserver-xorg - Xorg. This is the graphical server which is needed to get a GUI environment (for example gnome).needs to be installed to get into the GUI.
x-window-system-core - part of Xorg. needs to be installed to get into a the GUI.
gdm - This is Ubuntu's and Xubuntu's default login manager. needs to be installed for Ubuntu(gnome) and Xubuntu.
metacity - gnome's window manager. needs to be installed for Ubuntu(gnome).
xfwm4 - xfce4's window manager. analogous to metacity. needs to be installed for Xubuntu.
kdm - kde's login manager - needs to be installed for Kubuntu.
kwin - kde's window manager analogue to metacity. needs to be installed for Kubuntu.

A Concise apt-get / dpkg primer for new Debian users :
[http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html](http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html)

What to do when apt-get fails :
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

Here's a commandline reference :
[https://wiki.ubuntu.com/CommandLinePackageManagement](https://wiki.ubuntu.com/CommandLinePackageManagement)

For more information about apt-get type :
$man apt-get

For more information about aptitude type :
$man aptitude

For more information about dpkg type :
$man dpkg

After you have fixed all your problems regarding broken dependencies you still might have troubles with booting into X (getting into your graphical environment). **Dealing with problems with the Xserver :** 
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

**Please post your tips and/or fixes here :**
[http://www.ubuntuforums.org/showthread.php?t=187659](http://www.ubuntuforums.org/showthread.php?t=187659)

If you have problems and you need help IMHO it's best to start a new thread. In your own new thread : be elaborate about your problems. **Post the errors you get.** Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

**edit :**
I changed uncommented to commented. I hope it was obvious that in order to disable non official repo's those repo's have to be **commented** in the sources.list.

I changed apt-get to aptitude. I can probably improve it a little. But it will have to do for now. If you are sure you get better results with apt-get instead of aptitude (don't make the change if you want to compare them) then please let me know and include the proposed results.

---

### Post by ubuntu_demon on 2006-06-07
**I'm posting this as a forum user and not as a staff member. First read and understand the entire post before doing anything. This is all on your own risk. Please be very careful**

Using debfoster it's relatively easy to remove packages including all it's "children". Only use it if you really **understand **it because it's easy to delete too much. You should read the manpage($ man defoster) **Be very careful**

This is inspired on scenerario 3 from my breezy guide for debfoster :
[http://www.ubuntuforums.org/showthread.php?t=90675](http://www.ubuntuforums.org/showthread.php?t=90675)

apt-cache show debfoster :
> 
Description: Install only wanted Debian packages
 debfoster is a wrapper program for apt and dpkg.  When first run, it
 will ask you which of the installed packages you want to keep
 installed.
 .
 After that, it maintains a list of packages that you want to have
 installed on your system.  It uses this list to detect packages that
 have been installed only because other packages depended on them.  If
 one of these dependencies changes, debfoster will take notice, and
 ask if you want to remove the old package.
 .
 This helps you to maintain a clean Debian install, without old
 (mainly library) packages lying around that aren't used any more.


man debfoster :
> 
debfoster - weed unnecessary Debian packages

debfoster maintains a list of installed packages that were explicitly requested rather than installed as a dependency.  Arguments are entirely optional, debfoster can be invoked per se after each run of dpkg and/or apt-get.

Alternatively you can use debfoster to install and remove packages by specifying the packages on the command line.  Packages suffixed with a - are removed while packages without a suffix are installed.

If a new package is encountered or if debfoster notices that a package that used to be a dependency is now an orphan, it will ask you what to do with it.  If you decide to keep it, debfoster will just take note and continue.  If you decide that this package is not interesting enough it will be removed as soon as debfoster is done asking questions.  If your choises cause other packages to become orphaned more questions will ensue.


-**VERY IMPORTANT** : always make sure that ubuntu-minimal is mentioned in your keepers file!. Never choose to purge it when running debfoster from the commandline! This will render your system unusable.

-Be sure to to never remove the kernel you are currently running from your keepers file. Removing it probably won't succeed but if it will succeed (and you have no other kernels available in your grub menu then it will be a pain to boot the correct kernel)

-don't remove the grub package!

-it's nice if you leave debfoster in the keepers file otherwise it might try to remove itself :-D

Okay here we go :

**1)First do my regular guide (above this post) to fix problems regarding broken dependencies**
Here's the direct link :
[http://www.ubuntuforums.org/showpost.php?p=1080767&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1080767&postcount=1)

Make sure to use a clean sources.list such as this one :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

**2)Preparing**
install debfoster :
$ sudo apt-get install debfoster

edit your keepers file by :

$ sudo pico /var/lib/debfoster/keepers

It should look at like this (you may have linux-k7 or linux-686 instead of linux-686). Don't make typos!! :

```

ubuntu-minimal
linux-*386*
debfoster
grub

```

You should remove all other lines.

Keep a live-cd aside in case you run into troubles (for example the Dapper desktop cd).

Also be sure that you backup personal files and important configuration files that you have edited yourself!

**3)Making your system to conform to the keepers file**

Logout, go to ctrl-alt-f1 and login.

Now we go to init 1. To make sure we don't harm processes that are running.
$ sudo init 1

To force debfoster to remove all packages that aren't listed in this list or dependencies of packages that are listed in this list.It will also add all packages in this list that aren't installed. So it makes your system comply with this list. Do this :

$ sudo debfoster -f

from the manpage of debfoster :
> 
 -f, --force
Don&#8217;t ask anything and assume &#8216;no&#8217; as the answer to all questions. It also installs any packages that seem to be missing, thus forcing your
system to comply with the debfoster database. Can have &#8216;interesting&#8217; results if you&#8217;re not careful.


After this your system is compatible with the keepers file. 

**4)Making sure all problems are solved**
Let's run this command again to make sure it has removed everything that's problematic :
$ sudo apt-get -f remove

Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured.

**5)Getting everything back installed**

Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install xserver-xorg x-window-system-core ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

**6)Making sure everything is upgraded**

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If everything went well your broken dependencies problem is fixed.

Now do a reboot :
$ sudo reboot

To keep track of what you installed you can do once in a while :

$ sudo debfoster

type i for info, h for help, p for purge, y for remove and n for not remove

---

