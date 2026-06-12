---
title: "Upgrades not working now"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2015-04-07
Xubuntu 12.04... Installed updates a couple of weeks ago, now get the message:
> The following extra packages will be installed:
  linux-generic linux-image-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,120 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.77.91); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-headers-generic (= 3.2.0.77.91); however:
  Version of linux-headers-generic on system is 3.2.0.79.93.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can de-select the files named above, but get the error message that the package information is corrupt, and a few other messages as well...  Is this a good time to upgrade to 14.04, perhaps?  I'd guess that I need to fix these errors first, however.  Any clues?

---

### Post by Bashing-om on 2015-04-07
dkolars; Hello;

My thinking from the report:
> 
2 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
<snip>
inux-image-generic depends on linux-image-3.2.0-77-generic; however:
Package linux-image-3.2.0-77-generic is not installed.
<snip>


is to :
```

sudo apt-get update
sudo apt-get dist-upgrade

```
see if 'dist-upgrade' will take care of the dependency issue and install the kernel image.

If it does so, I do expect a bit of house cleaning is now in order.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-04-07
Yes, you should fix those errors before upgrading to 14.04. The package manager must be functioning for a release-upgrade to work.

In addition to what Bashing-om has asked, could you please show us output containing some of those other error messages?
Corrupted package information may be pretty easy to fix. It also helps to know what other problems lurk....

---

### Post by dkolars on 2015-04-08
Ran the commands, got this:
(At end of 'sudo apt-get update' run:
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
```


```
dk@Desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.77.91) but 3.2.0.79.93 is installed
 linux-image-generic : Depends: linux-image-3.2.0-77-generic but it is not installed
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
```

So, have no clue what is happening... it's as if I skipped an update somewhere, but I didn't...

An attempt to install anything gives me the message that there is a "broken cache", and I'm put into a loop that asks me to repair the package catalog.  Then get this message again:

```
installArchives() failed: dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.77.91); however:
  Package linux-image-generic is not configured yet.
No apport report written because MaxReports is reached already
 linux-generic depends on linux-headers-generic (= 3.2.0.77.91); however:
  Version of linux-headers-generic on system is 3.2.0.80.94.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-generic
 linux-generic
Error in function: 
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-77-generic; however:
  Package linux-image-3.2.0-77-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.77.91); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-headers-generic (= 3.2.0.77.91); however:
  Version of linux-headers-generic on system is 3.2.0.80.94.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
```

Then the pop-up asking me to repair the package catalog, etc. etc.  Although, the system JUST told me I needed a re-boot... will return momentarily...

---

### Post by dkolars on 2015-04-08
Well, solved... Should have caught it right away... 

"[COLOR=#000000][I]Package linux-image-3.2.0-77-generic is not installed."

[/I][/COLOR]Went to Synaptic Pkg Mgr, installed linux.image-3.2.0-77-generic, and all else sorted itself out...  Not sure why that got skipped in the "normal" update processes, but it did.  Thanks...

---

### Post by Bashing-om on 2015-04-08
dkolars; Well. There are a few issues, yes .

Just as Ian suspected and as he called it.
We proceed.

Let's get the background, and see what it is we are working with:
Post back the outputs - Between Code Tags - of terminal commands:
```

dpkg --print-architecture
uname -a
dpkg -l | grep linux-
ls -al /lib/modules
ls -al /boot

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
We find out what it is going to take to get the that stubborn kernel  installed, and what i386 packages apply to.
Then is the sources lists duplication to be dealt with .. we Will get to that after we see about the kernel.

As always, the advise " know what the command is " applies. If you do not know and are in the least not comfortable, ask for clarification and/or consult the on-board manual. Presently all we are doing is "looking" to see what we should do and can do.

Slowly, surely
[INDENT][INDENT][INDENT]a small step at each time
[/INDENT][/INDENT][/INDENT]

---

