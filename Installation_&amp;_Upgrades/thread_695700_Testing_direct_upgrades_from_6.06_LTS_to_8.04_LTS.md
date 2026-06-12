---
title: "Testing direct upgrades from 6.06 LTS to 8.04 LTS"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by magicfab on 2008-02-13
Hi

If anyone is interested in testing direct upgrades from LTS (6.06) to LTS (8.04 alpha), see:
[https://wiki.ubuntu.com/LTSUpgradesHowto](https://wiki.ubuntu.com/LTSUpgradesHowto)

Please post any questions or comments here.

I am not directly involved in that feature development but I can log bugs. I am interested in this from the support point of view :)

Cheers,

Fabian

---

### Post by ubnuturero on 2008-02-13
I think it would Help a lot  before the upgrade we Setup a server as a "REAL" server  I mean  set it up with the packages working  as  we need in dapper  and then  do the  upgrade 


Leonel

---

### Post by muzzol on 2008-02-13
i think you could clarify the 2nd point with something like:
[I]
update-manager is a graphical program. you can run it from local desktop or remotelly with 'ssh -X machine'[/I]

lot of people use LTS for server purposes so i think this clarification would be nice.

---

### Post by magicfab on 2008-02-13
@muzzol: actually, if you are using dapper as a server, many times you don'tinstall X, which would prevent from using the command you're describing.

In fact I would advise against upgrading graphically like that, as any X problem would prevent you from seing any problems. I am oversimplifying but you get the idea. I'd rather always ssh into the dapper machine and do it command line if I *have* to do it remotely.

Which raises another interesting point, SSH has to be running all the time if you do that. :)

---

### Post by mvo on 2008-02-14
> **muzzol said:**
> i think you could clarify the 2nd point with something like:
[I]
update-manager is a graphical program. you can run it from local desktop or remotelly with 'ssh -X machine'[/I]

lot of people use LTS for server purposes so i think this clarification would be nice.

update-manager is indeed a GUI application. For server upgrades Ubuntu does recommend to use "do-release-upgrade" from the update-manager-core package. Its text based and is more suitable for server installs.

Cheers,
 Michael

---

### Post by samb on 2008-02-14
I'm just getting this:


```

sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found

```

---

### Post by ubnuturero on 2008-02-14
Same  here 
Yesterday started worked but when asked me to proceed  I answered  NO and stopped the process for today  and  today 
No  new release found .

---

### Post by mvo on 2008-02-15
> **ubnuturero said:**
> Same  here 
Yesterday started worked but when asked me to proceed  I answered  NO and stopped the process for today  and  today 
No  new release found .

Thanks a lot for testing it and posting this bug here! This is fixed locally now and a new package is uploaded to dapper-proposed. 

As a workaround you can delete the file in /var/lib/update-manager/meta-release-lts

Thanks again,
 Michael

---

### Post by ubnuturero on 2008-02-15
did a apt-get update && apt-get upgrade  and  no new update-manager-core was found 
Removed  /var/lib/update-manager/meta-release-lts  and all started to flow .. upgrading right now ..

---

### Post by ubnuturero on 2008-02-15
when Upgrading  there was an error and upgrade stoped  
the error was :
Setting up clamsmtp (1.9-0ubuntu1) ...
chown: cannot access `/var/run/clamsmtp': No such file or directory
dpkg: error processing clamsmtp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 clamsmtp


did a  dpkg --configure -a   and same error
removed  clamstp 
and no errors but  the update Stopped


re run   do-release-upgrade  and   no new release found 
removed again the met-release-lts   
and do again a do-release upgrade  and  no new release found

---

### Post by samb on 2008-02-15
OK, I encountered two problems.

Firstly, the server was a LAP (Linux/Apache/PHP, MySQL is hosted on another server) box.  PHP5 was previously installed, but seems to have got lost in the upgrade.  After manually re-installing via apt-get it worked fine.

Secondly, the server is actually a VM running under Xen.  The inittab had a console running on xvc0 - but this wasn't reflected in the new event.d config.

Other than that, everything seemed to go OK.

---

### Post by ubnuturero on 2008-02-15
Starting again  now  I've removed clamsmtp  before upgrade 

It's good have qemu images with dapper server configured and ready to use  :-P

---

### Post by ubnuturero on 2008-02-15
Houston  WE HAVE AN UPGRADE !!! 

All worked  FINE  \o/

Just removed  clamsmtp    did the upgrade
installed clamsmtp 
touched  dovecot config   ( I've selected to install maintainer's dovecot.conf )

and ALL WORKING Fine ..

I know this is for  dapper-hardy  But I'll try  Gutsy - hardy  since I have some gutsy servers ..

a  BIG THANK YOU for your work !

---

### Post by magicfab on 2008-02-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Tonight I tried a 6.06.2 to 8.04 upgrade but it didn't work. I've logged a bug report:
[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117)

I've also updated the wiki page with a link to bug reports for the update-manager-core package:
[https://wiki.ubuntu.com/LTSUpgradesHowto](https://wiki.ubuntu.com/LTSUpgradesHowto)

I suggest anyone interested in following that wiki page subscribes to it.

Cheers,

F./

---

### Post by komputes on 2008-02-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

I don't know hoe ubunturero got it to work, I don't have clamsmtp (virus-scanning SMTP proxy). I just tried it directly from a clean install.

Tried 6.06.1 -> 8.04 and it almost went through but there were some errors. WARNING: Failed to read mirror file and a slew of bzip2 errors.

Is it possible that the archived copy of the upgrade is corrupted because I'm getting:

```

extracting '/tmp/tmpSTW1YM/hardy.tar.gz'
authenticate '/tmp/tmpSTW1YM/hardy.tar.gz' against '/tmp/tmpSTW1YM/hardy.tar.gz.gpg'
WARNING: Failed to read mirror file

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
```

---

### Post by mvo on 2008-02-21
> **ubnuturero said:**
> when Upgrading  there was an error and upgrade stoped  
the error was :
Setting up clamsmtp (1.9-0ubuntu1) ...
chown: cannot access `/var/run/clamsmtp': No such file or directory
dpkg: error processing clamsmtp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 clamsmtp


did a  dpkg --configure -a   and same error
removed  clamstp 
and no errors but  the update Stopped


re run   do-release-upgrade  and   no new release found 
removed again the met-release-lts   
and do again a do-release upgrade  and  no new release found

Thanks for this test. Could you please file a bug into launchpad about it and attach the log files in /var/log/dist-upgrade ? I tested the upgrade with clasmtp installed, but unfortunately I wasn't able to reproduce the problem. The logs may help to figure out why it is broken and what we can do to fix it. What does your "ls -l /var/run/" show? Could you include that into the bugreport as well please?

Thanks,
 Michael

---

### Post by mvo on 2008-02-21
> **komputes said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

I don't know hoe ubunturero got it to work, I don't have clamsmtp (virus-scanning SMTP proxy). I just tried it directly from a clean install.

Tried 6.06.1 -> 8.04 and it almost went through but there were some errors. WARNING: Failed to read mirror file and a slew of bzip2 errors.

Is it possible that the archived copy of the upgrade is corrupted because I'm getting:

```

extracting '/tmp/tmpSTW1YM/hardy.tar.gz'
authenticate '/tmp/tmpSTW1YM/hardy.tar.gz' against '/tmp/tmpSTW1YM/hardy.tar.gz.gpg'
WARNING: Failed to read mirror file

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
```

Thanks a lot for testing the upgrade. Could you please put the output in /var/log/dist-upgrade/main.log somewhere so that I can review it? That would be much appreciated (a bugreport is fine as well of course).

Cheers,
 Michael

---

### Post by mvo on 2008-02-21
> **magicfab said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Tonight I tried a 6.06.2 to 8.04 upgrade but it didn't work. I've logged a bug report:
[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/193117)

I've also updated the wiki page with a link to bug reports for the update-manager-core package:
[https://wiki.ubuntu.com/LTSUpgradesHowto](https://wiki.ubuntu.com/LTSUpgradesHowto)

I suggest anyone interested in following that wiki page subscribes to it.

Cheers,

F./

Thanks for your testing! You got hit by a error in python-central (#192992) in hardy that affected a lot of people. Fortunately this one is fixed now.

Cheers,
 Michael

---

### Post by oldHat on 2008-02-22
Here's what went wrong for me:

On my first few tries, update-manager found nothing to update...nothing seemed to work until I cleaned out /var/lib/update-manager

I wasted way too much time trying to enable dapper-proposed (not necessary, repository is not in sources.list, and I couldn't find the URL documented anywhere).  suggest you drop that instruction from the webpage ([https://wiki.ubuntu.com/LTSUpgradesHowto](https://wiki.ubuntu.com/LTSUpgradesHowto)) because it is untrue, unnecessary, and causes confusion

installation aborted when it encountered xvncviewer, so i removed it with synaptic
next, xmms
next vnc-common
later nvidia-glx
de-installed them all

finally, things began to move.

When the configuration and installation finally started, I noticed hundreds of errors about my LOCALE and LANG.  en_CA:UTF-8 and en_CA:en.  Perhaps this is because you install the fonts before the locales?  I don't know.

Then, I ran into a dependency trap that I couldn't resolve, something about gnome-screensaver 2.4.13 and gdm being incompatible, and 2.7.17 being required,  but the dependencies couldn't be undone  (lost the logs, don't remember, but I think xmod and xbase-clients may also have been mentioned) .  recommended "apt-get -f install" or synaptic "mark changes".  tried that, rinse,lather,repeat....began to realize that I was digging myself into a hole

It starts to get blurry here.  Thought I was done, restarted X, but X wouldn't run because of NVIDIA issues.  Not surprising with a new kernel (I always used to use Envy to install nvidia drivers but couldn't do this with Hardy).  
 
At some point, I tried a reboot, fsck kicked in, did a lot of work, but left me with an unusable hard drive.  No problem, now I have something to look forward to when I get up in the morning.

Slap in the Dapper CD, repartition my hard drive, reinstall Dapper, recover /home from a backup and try again.  Should be easy this time because I'm starting with a default installation and there are no unforseen dependencies.  Make sure to lie about my nationality and language, just in case Hardy hasn't been configured for en_CA.  It's all so sloooowww!  Finally, I remember to install linux-686-smp (my bad)

Try again.  Eventually remember to wipe out /var/lib/update-manager/*.  Downloads run hours faster because this time there are about 400 fewer packages and I'm getting double the bandwidth at noon than at 5 a.m. for some reason (my ISP or your server?  doesn't really make any difference).

Installation and configuration finish, I reboot, but grub can't find the kernel.  No big surprise, I had the same problem this morning with Dapper.  This upgrade repeated the same error.  My primary is a SATA drive, and there is also an IDE drive I use for backups (is this some random default because /dev/hda is ahead of /dev/sda in the sort sequence? dunno, i told the dapper installer to use /dev/sda1 for root, but it ignored me).  I use the grub editor to replace  "hd1" with "hd0", but discover that I only have the 2.6.15-51 and 2.6.15-26 kernels.  Where's 2.6.16?  Click on "about Ubuntu", and find that I'm still at 6.06.

Rerun update-manager, it does some more work, thankfully using the cached files, and not re-downloading.

BTW, the "applying changes" dialogue needs to keep the "terminal" area open by default.  The installation stops several times to ask questions in this window.  Unless this part of the display is visible, you'll never realize that it's waiting for an answer (ok, *you* will, but you're an expert and you already know how this is supposed to work).

Get hung up again, this time on python-apt 0.7.4 preinstallation errors.  Try again a few times, then try using dpkg for just this package.  Fails, complaining that the package file lacks a "Python Version" entry.  Corrupt file maybe?  Run apt-get clean, run synaptic, fix broken packages, apply.  100 quick downloads, try to install, fail on same error.

Is this really a show stopper?  If not, I don't know how to work around it.

Back to square 1.  No other plans for today.  Interesting and kind of fun, but still frustrating.  Maybe I'll try again in April.

I'm really surprised that this would fail to upgrade a brand-new Dapper default installation.   Is this your first level of end-user testing, or have you already had success with other non-tekkies?  I'm not a total newbie--I've used unix and linux at work every day for more than 10 years.  I don't have sysadmin skills, but I have installed mandrake, fedora, then finally dapper, at home, then used and maintained them for years.

Lessons learned:  there isn't much documentation online for Alpha releases; for every solution there's a problem.  Alpha tests may fail.  Make sure you're *really* familiar with update-manager, apt-get, synaptic and dpkg before you try any of this.

---

### Post by geraner on 2008-02-23
I got the following problem.
> Setting up apache2 (2.2.8-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 lsb-core
 launchpad-integration
 lsb-graphics

Could not install the upgrades
The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on python-central (>= 0.5.8); however:
  Package python-central is not installed.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of launchpad-integration:
 launchpad-integration depends on python-central (>= 0.5.8); however:
  Package python-central is not installed.
dpkg: error processing launchpad-integration (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lsb-core
 launchpad-integration
 lsb-graphics
root@linux:/home/stl# 


---

### Post by geraner on 2008-02-23
And trying this to correct:
> root@linux:/home/stl# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python python-dev python-gnupginterface python-minimal python-qt3 python-reportlab python-sip4 python-support python-xml python2.5-dev update-manager-core
Suggested packages:
  python-doc python-tk python-profiler libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql python-qt3-doc python-qt3-gl pdf-viewer python-egenix-mxtexttools python-reportlab-doc
  python-xml-dbg python-xml-doc
Recommended packages:
  python-imaging python-renderpm ttf-dustin
The following packages will be REMOVED:
  python2.4-reportlab python2.4-xml
The following NEW packages will be installed:
  python-sip4 python-support python2.5-dev
The following packages will be upgraded:
  python python-dev python-gnupginterface python-minimal python-qt3 python-reportlab python-xml update-manager-core
8 upgraded, 3 newly installed, 2 to remove and 343 not upgraded.
5 not fully installed or removed.
Need to get 0B/8187kB of archives.
After this operation, 28.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_SE:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 54960 files and directories currently installed.)
Unpacking python-sip4 (from .../python-sip4_4.7.3-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-sip4_4.7.3-1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/sipconfig.py', which is also in package python2.4-sip4-qt3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace python-qt3 3.15.1-0ubuntu3 (using .../python-qt3_3.17.4-1ubuntu1_i386.deb) ...
Unpacking replacement python-qt3 ...
dpkg: error processing /var/cache/apt/archives/python-qt3_3.17.4-1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/pyqtconfig.py', which is also in package python2.4-qt3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-sip4_4.7.3-1ubuntu1_i386.deb
 /var/cache/apt/archives/python-qt3_3.17.4-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@linux:/home/stl# 
But it's not working. :(

---

### Post by komputes on 2008-03-31
I would like to report that I was able to do an LTS-to LTS from a clean install of 6.06 upgraded to 8.04. Great success! I used the following method:

```
sudo apt get install update-manager
run "update-manager -d
```

Once the update manager click on the upgrade to 8.04 button and follow on-screen instructions.

Two lines, very simple, no extra repos, nice, I like, how much, FREE? You _must_ be kidding.

Note: A lot of packages will be erased because they are no longer supported, look at the list and make sure that nothing will be missed.

---

### Post by paynito on 2008-04-19
I had a relatively new 6.06 installed from a cd ubuntu mailed to me a long time ago.  it had been running maybe 2 weeks.  i downloaded the 8.04 beta cd, not the alternative install cd.  i performed the upgrades until update manager told me i could upgrade to 8.04.  things downloaded overnight
in the morning i told it to install the upgrades
several times during this process in the detailed terminal view inside update-manager it said something about not finding Ex:Au language and reverting to default language C
after rebooting all my menus only show boxes instead of letters.  
per instructions in irc://irc.freenode.net/Ubuntu+1
i ran sudo apt-get install ubuntu-desktop and got these errors

danny@danny-laptop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for danny:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.2) but it is  not going to be installed or
                                      language-support-en but it is not going to  be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to  be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.2) but it is  not going to be installed or
                                      language-support-en but it is not going to  be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to  be installed
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: consolekit but it is not going to be installed
                  Depends: fast-user-switch-applet but it is not going to be ins talled
                  Depends: gdebi but it is not going to be installed
                  Depends: gimp-python but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be instal led
                  Depends: gnome-menus but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: gtk2-engines but it is not going to be installed
                  Depends: hwtest-gtk but it is not going to be installed
                  Depends: libgl1-mesa-glx but it is not going to be installed
                  Depends: libgnomevfs2-extra but it is not going to be installe d
                  Depends: nautilus but it is not going to be installed
                  Depends: seahorse but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be ins talled
                  Depends: system-config-printer-gnome but it is not going to be  installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: xdg-user-dirs-gtk but it is not going to be installed
                  Depends: xorg but it is not going to be installed
E: Broken packages


i can read and write in the terminal and in firefox
i can see the firefox menus file edit view go
but above that the line that would usually say the window title like "ubuntu irc - Google Search"  only shows about 40 boxes

---

### Post by paynito on 2008-04-20
here are some more errors that may helo you diagnose what is wrong with my system fonts after the upgrade


danny@danny-laptop:~$ gnome-screenshot --delay 5

(gnome-panel-screenshot:6002): Gdk-WARNING **: locale not supported by Xlib

(gnome-panel-screenshot:6002): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel-screenshot:6002): Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running pango-querymodules.

[IMG]http://img232.imageshack.us/my.php?image=aaatv6.png[/IMG]

(gnome-panel-screenshot:6002): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(gnome-panel-screenshot:6002): Pango-WARNING **: pango_font_get_glyph_extents called with bad font, expect ugly output

(gnome-panel-screenshot:6002): Pango-WARNING **: _pango_cairo_font_install called with bad font, expect ugly output

(gnome-panel-screenshot:6002): Pango-WARNING **: pango_font_get_font_map called with bad font, expect ugly output

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-WARNING **: pango_font_get_metrics called with bad font, expect ugly output

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed

(gnome-panel-screenshot:6002): Pango-CRITICAL **: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed
danny@danny-laptop:~$

something like sudo apt-get install pango1.0.0

fixed the boxes problem
now i'm running sudo apt-get dist-upgrade

it says it'll be finished in 6 days

let's blame the whole thing on kicking out the power cord while doing the 384 upgrades between 6.06 and 8.04 
it picked up again on #100, but something must have gotten lost in translation.  also i don't recommend choosing Australian English, that may have confused it

---

### Post by magicfab on 2008-04-20
If you're upgrading a Dell Poweredge 1650  or generally speaking any Dell server, make sure your BIOS is updated. With 6.06 you may need Windows to do such an upgrade. It would help if someone with a Dell and 6.06 could test this BIOS upgrade howto:
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

Also see this blog post for discussion:
[http://ivoks.blogspot.com/2008/04/ubuntu-804-and-dell-poweredge-1650.html](http://ivoks.blogspot.com/2008/04/ubuntu-804-and-dell-poweredge-1650.html)

---

### Post by ubuntubrian on 2008-04-26
I tried this method from 6.06 to 8.04 and  on the first step after clicking the upgrade button UpdateManager tried fetching for many minutes and I canceled. I edited my repositories down to the minimum, no third party left, I tried again but even after UpdateManager giving message that fetching was complete it continued to fetch. It finally canceled itself with a message that it was returning computer to previous state. The only info is from the terminal:

$ gksudo "update-manager -d"
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpTcI5Cs/hardy.tar.gz'
authenticate '/tmp/tmpTcI5Cs/hardy.tar.gz' against '/tmp/tmpTcI5Cs/hardy.tar.gz.gpg'
WARNING: Failed to read mirror file
WARNING: Failed to read mirror file

Mac TiBook PowerPC

---

### Post by ubuntubrian on 2008-04-26
I'm getting this from the log file but it appears that Update Manager debug is adding a source that it then cannot access, ie, 
```
DEBUG adding 'deb http://ports.ubuntu.com/ubuntu-ports dapper-backports main/debian-installer
```
It then tries to 
```
ERROR IOError/SystemError in cache.update(): 'Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz 404 Not Found
```

there is no ```
http://ports.ubuntu.com/ubuntu-ports dapper-backports main/debian-installer
``` that I can find

Is this PPC specific? It wouldn't seem so as the source doesn't exist asfar as i can tell.

Thanks

---

### Post by ubuntubrian on 2008-04-26
I was able to track the address all the way to here:
[http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/](http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/)
and there is no binary-powerpc available-I guess I'm out of luck!

---

### Post by ubuntubrian on 2008-05-02
Hellooooooooo!!!!

---

