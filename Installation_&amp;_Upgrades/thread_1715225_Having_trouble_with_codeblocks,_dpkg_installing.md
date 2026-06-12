---
title: "Having trouble with code::blocks, dpkg installing"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Wesnprogamat on 2011-03-26
I am trying to install the IDE program called Code::Blocks, downloaded from [http://www.codeblocks.org/downloads/26](http://www.codeblocks.org/downloads/26), scrolling down to 
[IMG]http://www.codeblocks.org/images/distro_logos/Debian-logo_48.png[/IMG]  [SIZE=2]codeblocks-10.05-1-debian-i386.tar.bz2[/SIZE]
 [SIZE=2]codeblocks-10.05-1-debian-dbg-i386.tar.bz2[/SIZE]
   [SIZE=2]27 May 2010[/SIZE]
 [SIZE=2]27 May 2010[/SIZE]
   [SIZE=2]18.6 MB[/SIZE]
 [SIZE=2]64.9 MB[/SIZE]
 selecting Sourceforge.net on this line [SIZE=2]codeblocks-10.05-1-debian-dbg-i386.tar.bz2[/SIZE].

I have both the "unpacked" version of this download and the "untouched" version (I put on) and was sent to try to install the "unpacked" version

I looked in _Moving to Ubuntu Linux_ for how to install from only one directory(Installing using *codeblocks*.deb didn't seem to work as there were a few files without codeblocks in their title and it needed those packages to successfully install) and didn't find out how. I found out how to install using shell (sudo dpkg --install), but I didn't find out a way to limit the installation to only the installation of the *.deb files inside this directory (i386). I am not exactly sure either on where to place the "--interactive" line to ensure that only the *.deb I wanted installed were.

So, in other words, I see that there are four different keys that unlock the same "forbidding door" and let me pass...

-And by the way, I would appreciate it more if more keys were shown to me. 

1.Tell me how to install a *.tar.bz2 file

2.Tell me how to tell the computer to install all *codeblocks*.deb AND ONLY the files the packages require by extension (if they are nearby, which in this case they are).

3.Tell me how to install all *.deb files inside a single directory (in this case, i386)

4.Show me the proper placement of "--interactive" in the following code: "Sudo dpkg --install *.deb" (Yes I know that this key would be the one which takes the longest to get the job done)

Now there are variations of these keys, and there may be more. I would sincerely appreciate those who would show me these keys and more, or in other words "ways to skin a cat", as the saying goes.

Now I do not ask those who read this to try to post every way they know at once, but that would be nice.

---

### Post by Wesnprogamat on 2011-04-06
Dad had found another *key* to this door.

His way was to try to put it onto "update manager".

This didn't work and now the update manager has the following error on boot:
E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)

Now solving this would likely be a means to opening this door. Please do more than read. I would really appreciate it if someone (especially so if more than one responds here) would respond.

  	 	 	 	p { margin-bottom: 0.08in; }   I have found a piece of the way to "2.Tell me how to tell the computer to install all *codeblocks*.deb AND ONLY the files the packages require by extension (if they are nearby, which in this case they are)." I just tried apt-get and it seemed to work. It took 2 lines of code:```

sudo apt-get install codeblocks
sudo apt-get -f install
```

Unfortunately, I made a windows user error:

The following packages will be REMOVED:
codeblocks codeblocks-contrib codeblocks-contrib-dbg codeblocks-dbg codeblocks-dev libcodeblocks0
0 upgraded, 0 newly installed, 6 to remove and 138 not upgraded.
6 not fully installed or removed.
After this operation, 148MB disk space will be freed.
Do you want to continue [Y/n]? y

And now it won't be totally installed, nor totally uninstalled. It wouldn't run. This is the error:
  Failed to execute child process "codeblocks" (No such file or directory)
  

   Maybe what I did next sealed the fate:
  
```

  sudo dpkg --remove codeblocks
  sudo dpkg --purge codeblocks
  
```
  

  Will someone please help me?
  

  To be precise, here is the whole list of what went on:
  [sudo] password for dad:
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  codeblocks is already the newest version.
  You might want to run `apt-get -f install' to correct these:
  The following packages have unmet dependencies:
    codeblocks: Depends: libwxbase2.8-0 (>= 2.8.10.1) but it is not going to be in
  stalled
                Depends: libwxgtk2.8-0 (>= 2.8.10.1) but it is not going to be ins
  talled
    codeblocks-contrib: Depends: libwxbase2.8-0 (>= 2.8.10.1) but it is not going
  to be installed
                        Depends: libwxgtk2.8-0 (>= 2.8.10.1) but it is not going t
  o be installed
                        Depends: libwxsmithlib0 (= 10.05-1) but it is not installa
  ble
    libcodeblocks0: Depends: libwxbase2.8-0 (>= 2.8.10.1) but it is not going to b
  e installed
                    Depends: libwxgtk2.8-0 (>= 2.8.10.1) but it is not going to be
   installed
  E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
  olution).
  dad@Deborah:~$ sudo apt-get -f install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  codeblocks is already the newest version.
  You might want to run `apt-get -f install' to correct these:
  The following packages have unmet dependencies:
    codeblocks: Depends: libwxbase2.8-0 (>= 2.8.10.1) but it is not going to be in                                               stalled
                Depends: libwxgtk2.8-0 (>= 2.8.10.1) but it is not going to be ins                                               talled
    codeblocks-contrib: Depends: libwxbase2.8-0 (>= 2.8.10.1) but it is not going                                                to be installed
                        Depends: libwxgtk2.8-0 (>= 2.8.10.1) but it is not going t                                               o be installed
                        Depends: libwxsmithlib0 (= 10.05-1) but it is not installa                                               ble
    libcodeblocks0: Depends: libwxbase2.8-0 (>= 2.8.10.1) but it is not going to b                                               e installed
                    Depends: libwxgtk2.8-0 (>= 2.8.10.1) but it is not going to be                                                installed
  E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s                                               olution).
  dad@Deborah:~$ sudo apt-get -f install
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Correcting dependencies... Done
  The following packages were automatically installed and are no longer required:
    libdns35 libsearchclient0 kwin-style-crystal libstrigihtmlgui0 xulrunner-1.9-gnome-support linux-headers-2.6.24-21-generic
    linux-headers-2.6.24-21 kmplayer-base
  Use 'apt-get autoremove' to remove them.
  The following packages will be REMOVED:
    codeblocks codeblocks-contrib codeblocks-contrib-dbg codeblocks-dbg codeblocks-dev libcodeblocks0
  0 upgraded, 0 newly installed, 6 to remove and 138 not upgraded.
  6 not fully installed or removed.
  After this operation, 148MB disk space will be freed.
  Do you want to continue [Y/n]? y
  (Reading database ... 344407 files and directories currently installed.)
  Removing codeblocks-contrib-dbg ...
  Removing codeblocks-dbg ...
  Removing codeblocks-contrib ...
  Removing codeblocks ...
  Removing codeblocks-dev ...
  Removing libcodeblocks0 ...
  Processing triggers for libc6 ...
  ldconfig deferred processing now taking place
  dad@Deborah:~$ sudo apt-get install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Package codeblocks is not available, but is referred to by another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package codeblocks has no installation candidate
  dad@Deborah:~$ sudo dpkg --remove codeblocks
  dpkg - warning: ignoring request to remove codeblocks, only the config
   files of which are on the system.  Use --purge to remove them too.
  dad@Deborah:~$ sudo dpkg --purge codeblocks
  (Reading database ... 344221 files and directories currently installed.)
  Removing codeblocks ...
  Purging configuration files for codeblocks ...
  dad@Deborah:~$ sudo apt-get --install codeblocks
  E: Command line option --install is not understood
  dad@Deborah:~$ sudo apt-get install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Package codeblocks is not available, but is referred to by another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package codeblocks has no installation candidate
  dad@Deborah:~$ sudo apt-get install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Package codeblocks is not available, but is referred to by another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package codeblocks has no installation candidate
  dad@Deborah:~$ sudo apt-get autoremove
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  The following packages were automatically installed and are no longer required:
    libdns35 libsearchclient0 kwin-style-crystal libstrigihtmlgui0 xulrunner-1.9-gnome-support linux-headers-2.6.24-21-generic
    linux-headers-2.6.24-21 kmplayer-base
  The following packages will be REMOVED:
    kmplayer-base kwin-style-crystal libdns35 libsearchclient0 libstrigihtmlgui0 linux-headers-2.6.24-21
    linux-headers-2.6.24-21-generic xulrunner-1.9-gnome-support
  0 upgraded, 0 newly installed, 8 to remove and 137 not upgraded.
  After this operation, 71.2MB disk space will be freed.
  Do you want to continue [Y/n]? Y
  (Reading database ... 344221 files and directories currently installed.)
  Removing kmplayer-base ...
  Removing kwin-style-crystal ...
  Removing libdns35 ...
  Removing libstrigihtmlgui0 ...
  Removing libsearchclient0 ...
  Removing linux-headers-2.6.24-21-generic ...
  Removing linux-headers-2.6.24-21 ...
  Removing xulrunner-1.9-gnome-support ...
  Processing triggers for libc6 ...
  ldconfig deferred processing now taking place
  dad@Deborah:~$ sudo apt-get install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Package codeblocks is not available, but is referred to by another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package codeblocks has no installation candidate
  dad@Deborah:~$ sudo apt-get -f install
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  0 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.
  dad@Deborah:~$ sudo rm -i *codeblocks*
  rm: cannot remove `*codeblocks*': No such file or directory
  dad@Deborah:~$ sudo rm -i *code::blocks*
  rm: cannot remove `*code::blocks*': No such file or directory
  dad@Deborah:~$ sudo rm -i *Code::Blocks*
  rm: cannot remove `*Code::Blocks*': No such file or directory
  dad@Deborah:~$ sudo cd i386
  sudo: cd: command not found
  dad@Deborah:~$ ls
  Desktop  Documents  Examples  i386  libflashplayer.so  Music  nautilus-debug-log.txt  Pictures  Public  Templates  Videos
  dad@Deborah:~$ cd /i386
  bash: cd: /i386: No such file or directory
  dad@Deborah:~$ cd i386
  dad@Deborah:~/i386$ apt-get install codeblocks
  E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
  E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
  dad@Deborah:~/i386$ apt-get install codeblocks
  E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
  E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
  dad@Deborah:~/i386$ sudo apt-get install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Package codeblocks is not available, but is referred to by another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package codeblocks has no installation candidate
  dad@Deborah:~/i386$ sudo apt-get install i386
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Note, selecting type-handling instead of i386
  The following extra packages will be installed:
    dpkg-dev libtimedate-perl patch type-handling
  Suggested packages:
    debian-keyring diff-doc
  Recommended packages:
    build-essential
  The following NEW packages will be installed:
    dpkg-dev libtimedate-perl patch type-handling
  0 upgraded, 4 newly installed, 0 to remove and 137 not upgraded.
  Need to get 690kB of archives.
  After this operation, 2130kB of additional disk space will be used.
  Do you want to continue [Y/n]? n
  Abort.
  dad@Deborah:~/i386$ sudo apt-get install i386
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Note, selecting type-handling instead of i386
  The following extra packages will be installed:
    dpkg-dev libtimedate-perl patch type-handling
  Suggested packages:
    debian-keyring diff-doc
  Recommended packages:
    build-essential
  The following NEW packages will be installed:
    dpkg-dev libtimedate-perl patch type-handling
  0 upgraded, 4 newly installed, 0 to remove and 137 not upgraded.
  Need to get 690kB of archives.
  After this operation, 2130kB of additional disk space will be used.
  Do you want to continue [Y/n]? Y
  Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
  Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]
  Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4.2 [558kB]
  Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main type-handling 0.2.23 [6262B]
  Fetched 690kB in 5s (130kB/s)
  Selecting previously deselected package libtimedate-perl.
  (Reading database ... 329422 files and directories currently installed.)
  Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
  Selecting previously deselected package patch.
  Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
  Selecting previously deselected package dpkg-dev.
  Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4.2_all.deb) ...
  Selecting previously deselected package type-handling.
  Unpacking type-handling (from .../type-handling_0.2.23_i386.deb) ...
  Setting up libtimedate-perl (1.1600-9) ...
  Setting up patch (2.5.9-4) ...
  Setting up dpkg-dev (1.14.16.6ubuntu4.2) ...
  Setting up type-handling (0.2.23) ...
  dad@Deborah:~/i386$ cd $HOME
  dad@Deborah:~$ sudo apt-get install i386
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Note, selecting type-handling instead of i386
  type-handling is already the newest version.
  0 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.
  dad@Deborah:~$ sudo apt-get install codeblocks
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Package codeblocks is not available, but is referred to by another package.
  This may mean that the package is missing, has been obsoleted, or
  is only available from another source
  E: Package codeblocks has no installation candidate

---

