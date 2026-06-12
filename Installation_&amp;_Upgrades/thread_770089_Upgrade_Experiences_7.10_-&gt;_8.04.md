---
title: "Upgrade Experiences: 7.10 -&gt; 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by arm-c on 2008-04-27
Ubuntu is a great Linux Distro, but there are some things that just make me want to scream!

BLUF (Bottom Line Up Front) [save the long read for the solution]:
a:  Java in 8.04 is broke out of box.  Remove OpenJava and install the Sun Java.  Fixed Java for me.
b:  Installing Firefox 2 still has java broke.  Make a sim link to the java plugin in the usr/lib/firefox/plugins directory that points to the usr/lib/jvm/java1-6.... /plugins/i386/ns7/(name of java plugin)
c:  VirtualBox is broke.  Have to goto synaptic and remove the virtualbox pkg and install the virutalbox-ose + the various other packages for your version of kernel (for me it was the "generic" endings.  After doing that, I was once again up and running.
d:  PLUCKER:  Package upgrade is broken due to PyPlucker files being in a different directory than expected.  Place a symbolic link in the /usr/lib/python2.5/site-packages directory that points to /usr/lib/python2.4/site-packages/PyPlucker directory.

------------------------------

First, the upgrade went fairly smoothly, however there were a couple of items that really didn't work for me and made me pull my hair out.

First, my mistake was to not wait a few weeks (a month?) to upgrade.  Upgrading at the peak time was just too slow for me.  Still, the problems that persisted could have been made more manageable.

JAVA.  I use it all the time and I must say that changing the system to "OpenJava" was a mistake.  Too many bugs and I lost an entire day trying to get to a java site that just would not function.  I thought it was the Firefox Beta, but it was not.  After pulling my hair out for over 1/2 a day, I finally installed the old Firefox, but that didn't work until I figured out how to install the link necessary to point to the java plugin.  Once that happened, I was up and running there.  Still, I felt VERY close to solving the 3.0b issue, so I continued.  Turns out, it was using the IceTea plugin, which would not function for the website I needed to access.  Solution, remove the OpenJava and the plugin from semantic.  For me, I guess I was fortunate I had done a upgrade and still had the latest Java installed.

VIRTUAL BOX.  VirtualBox doesn't work after an upgrade.  A bit frustrating, since the packages changed, I guess it wasn't upgraded.    Recommend uninstall VirtualBox and install the OpenSourceEdition and associated supporting files total of about 5).  Ensure that you select the appropriate series, which for me was the ones ending in "generic".  After that, my existing virtual machines ran fine.

PLUCKER:  Plucker didn't work for me either.  The problem was that it couldn't find the appropriate PyPlucker files and it was looking in the Python2.5 area; however, they were in python2.4 sitepackages director.  I placed a symbolic link in the usr/lib/python2.5/site-packages directory.  Once I did that, I ran synaptic and installed a package.  It picked up the unfinished plucker install and finished without error.

XGalaga:  What I don't have a solution to is the fact that this wonderful little game no longer works from the keyboard interface.  Mouse worked, but keyboard did not.  Sound hasn't worked since Feisty, and still doesn't work now.  I did submit a bug on both of these, but the keyboard input is the most important one of the two.  Anyone able to provide a solution or assistance I would appreciate it.

TABLET PC:  I am using a Tablet PC.  One thing that brought me to Ubuntu was that my tablet stylus worked right out of the box on Feisty.  I was hopeful that Heron would fix what broke in Gusty, but it hasn't.  It was the little things like pen support that brought me to Ubuntu... but failure to fix this configuration issue certainly bothers me.

So, that has been my experience so far.  Some other small annoyances, but have worked through them and cant recall the majority of them.

Finally, I will close with a few rants.  What I really want in Ubuntu is full Dual Monitor / Extended Desktop support.  Given my difficulties, I probably won't step up to next iteration until they offer me this as an option.  I know they made progress in this, but I was let down by the absence of it in Heron.,

Given my troubles, I would have rather waited a little while longer for them to work out the bugs and give me an excellently working system.  I could have survived with this if they had not attempted the Java thing.

SO:  ALL, Please forgive my failure to put the "copy / paste" solutions.  I didn't have time to do that, BUT I did want to write my experiences and hope that they will help someone else out.

---

### Post by Peter09 on 2008-04-27
Virtualbox worked for me, it needs a rebuild because of the new kernel, but it does say that when you attempt to run it - it even gives you the command line to use. 

May be it was different for you.

PC

---

### Post by arm-c on 2008-04-27
I tried the command, but it still failed for me.  Discovered the OSE version while I was attempting to reinstall VB.  Wish my expereience was yours. :)  Funny, how the various experiences are so different.

---

### Post by Peter09 on 2008-04-27
Yes,
sometimes its difficult to understand the linkages between one user/machine/setup and another and the final result.I do wonder sometimes if the linkages within the O/S are evolving towards the unmanageable ... :(

PC

---

### Post by arm-c on 2008-04-27
Well,

Sometimes difference within machines are a result of the various packages installed, and certainly installing downloaded .DEBs not in the repository are likely to introduce uncertainties.

I am undecided about all of the "linkages".  I am sure they are numerous ones; but they certainly save on space and given the nature of "open source" it is hard to completely dictate a common understanding of file locations, etc... that would simplify some of the linkages.  I am sure there is a guideline present, but doesn't mean it is followed.

Still, I think the root of this problem is the premature release of an attempt to integrate OpenJava when it is not completely tested.  Believe me, it was frustrating to goto the java test page and get a "thumbs up" from the site (just that it said wasn't latest version of java) and then goto the site of my online course and the site freeze on launch of applet.  Means that there is a shortcoming in the OpenJava they attempted to include.

I would have liked to have had an option to choose between Sun Java and Open Java during the upgrade / install process.

---

### Post by arm-c on 2009-02-07
For those that are reading now, I'd like to make a few notes about Ubuntu 8.10.

Ubuntu 8.10 has had some surprising advances for ME.  Some of my rants have been addressed.  There are, of course, a few problems that weren't addressed.... yet. :)

Ubuntu 8.10 has addressed:

a.  VirtualBox.  I go straight for the full version because I need the USB pass through.  Any upgrade / kernel upgrade requires the module to be reconfigured; however, there is now a module that will monitor the status of the kernel and automatically rebuild the module after it is upgraded.  This is great, but it must be installed before building the module and then you still must manually run the reconfigure module.  Don't worry, the first time you have to do this, the help text provides you details on both the module to install and the command to run in order to rebuild the module.

b.  Dual Monitor Support:  Got it working.  8.10 now detects the second monitor and will auto matically set the virtual setting required in xorg.conf to handle "twinview".  This is great; however, it still appears that twinview cannot handle a virtual setting higher than 2048x1024 if you want to use Compiz-Fusion, so both of my monitors are essentially 1024/768 in size.  Cool with me. :)

c.  Pulse Audio(PA):  PA has gotten more stable since 8.04.  The 8.10 settings seam to handle pulse better.  I must say that the primary aspect of PUlse that I hated has not been retested since === use of audio editor such as Audacity.  Still, my sounds appear to work much better.  One day I will see if Audacity is working now.

d.  Java.  Didn't have the struggles with OpenJava like before, but that may be simply because I did an upgrade vs a clean instal.  Jury remains out.

e.  Tablet PC:  Well, still didn't work out of box; however, it simply required me to make physical changes to the xorg.conf.  The howto on ubuntu Wacom page covers this quite well.  On this note, I do want to say that my USB Wacom works out of box for pen, however, it still requires the manual edit of xorg.conf to enable the pad buttons, etc...  Not that bad.

f.  Wireless:  My wireless worked great; however, my wife's laptop would not connect to her school network.  WICD fixed the issue for her.  I still use NetworkManger; however, I keep in mind that WICD will connect to hidden access points where as NetworkManager won't.

g.  Bluetooth and acerhk:  The drivers are there by default.  Have been.  That is great! however, ubuntu doesn't have a way to activate my bluetooth hardware.  (Note, networkmanager does enable me to turn on/off the hardware for wifi).  So, while it is possible to do it from command line, I still wanted a GUI interface... so I wrote one for users of the acerhk driver.  The GUI interfaces with the acerhk driver.  You can get a deb for the gui at sourceforge:

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

More info is available at:
[http://ubuntuforums.org/showthread.php?t=1059704](http://ubuntuforums.org/showthread.php?t=1059704)

Well, that does it for this post.  Hope this is helpful for someone.

ARM-C

---

