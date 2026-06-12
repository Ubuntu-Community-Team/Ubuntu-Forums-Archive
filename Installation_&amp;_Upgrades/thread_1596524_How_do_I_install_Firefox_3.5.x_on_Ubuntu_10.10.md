---
title: "How do I install Firefox 3.5.x on Ubuntu 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by crf112 on 2010-10-14
I'm having a problem with iMacros running on Firefox 3.6.10 on my Ubuntu 10.10 system.  I posted the symptoms of the problem on the [iOpus Forum]("http://forum.iopus.com/viewtopic.php?f=11&t=11199") and it looks like the problem may be associated with Firefox 3.6.

I would like to install a copy of Firefox 3.5 to see if that fixes the problem, but haven't been able to sort through everything I have read at [FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion") and [Firefox Stable Channel]("https://launchpad.net/~mozillateam/+archive/firefox-stable").  Can someone give me some step-by-step instructions to install Firefox 3.5 on my Ubuntu 10.10 system?

---

### Post by dino99 on 2010-10-14
you can make your choice there:

[https://launchpad.net/ubuntu/+ppas?name_filter=firefox](https://launchpad.net/ubuntu/+ppas?name_filter=firefox)

---

### Post by crf112 on 2010-10-14
OK, this is what I have done so far:

1. I went to [https://launchpad.net/ubuntu/+ppas?name_filter=firefox]("https://launchpad.net/ubuntu/+ppas?name_filter=firefox")
2. from there I went to [firefox 3.5]("https://launchpad.net/~bdonlan/+archive/ff3.5")
3. from there I went to [firefox-3.5 ... Newer version]("https://launchpad.net/ubuntu/jaunty/+source/firefox-3.5/3.5.12+build1+nobinonly-0ubuntu0.9.04.1")
4. from there I went to [Build ... jaunty amd64]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/1936146") since I'm running Ubuntu 10.10 64 bit on an AMD 64-bit processor.
5. from there I downloaded [firefox-3.5_3.5.12+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/1936146/+files/firefox-3.5_3.5.12%2Bbuild1%2Bnobinonly-0ubuntu0.9.04.1_amd64.deb")

I assume that I just run the .deb file to do the install.  But, do I need to uninstall the existing firefox before I run the .deb?  Is there anything else I need to do?

---

### Post by mikewhatever on 2010-10-14
I rather doubt firefox.deb for Jaunty will install successfully on Maverick. You'll probably hit unmet dependencies wall.

---

### Post by crf112 on 2010-10-14
I thought I could check out the dependencies by the command:> sudo dpkg --no-act --install ./Downloads/firefox-3.5_3.5.12+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb
That gave me: > Selecting previously deselected package firefox-3.5.
(Reading database ... 126645 files and directories currently installed.)
Unpacking firefox-3.5 (from .../firefox-3.5_3.5.12+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb) ...
Does this mean I don't have a dependency issue?

---

### Post by crf112 on 2010-10-14
It turns out that the --no-act option must stop dependency checking. I have a .deb for AmazonMP3 that has dependency problems and when I run dpkg --no-act on it the dependencies are NOT listed.

So I decided to just go ahead and run the install. This is what happened:> charlie@Gateway:~$ sudo dpkg --install ./Downloads/firefox-3.5_3.5.12+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb 
Selecting previously deselected package firefox-3.5.
(Reading database ... 126660 files and directories currently installed.)
Unpacking firefox-3.5 (from .../firefox-3.5_3.5.12+build1+nobinonly-0ubuntu0.9.04.1_amd64.deb) ...
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not installed.
 firefox-3.5 depends on firefox-3.5-branding | abrowser-3.5-branding; however:
  Package firefox-3.5-branding is not installed.
  Package abrowser-3.5-branding is not installed.
dpkg: error processing firefox-3.5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-3.5
I have xulrunner-1.9.2 installed, so I don't understand why I should be getting that error.  On the other hand, I see that xulrunner-1.9.1 is available [HERE]("https://launchpad.net/ubuntu/jaunty/+source/xulrunner-1.9.1/1.9.1.12+build1+nobinonly-0ubuntu0.9.04.1").

But, I haven't found firefox-3.5-branding yet.

---

### Post by crf112 on 2010-10-19
I found a Firefox-3.5-branding [HERE.]("http://packages.ubuntu.com/jaunty/firefox-3.5-branding")  I was able to get 3.5 to run enough to determine that 3.5 did fix my original problem (with iMacros). However, the distro of 3.5 that I choose to use has a problem with branding as discussed at [http://ubuntuforums.org/showthread.php?t=1225754]("http://ubuntuforums.org/showthread.php?t=1225754") which shows a fix to the problem assuming you are going from 3.0 to 3.5.  I tried to modify the instructions to fit my downgrade from 3.6 to 3.5 but things didn't work out correctly.

For now, I am going to restore my system to a backup I took just before installing Firefox 3.5.

---

