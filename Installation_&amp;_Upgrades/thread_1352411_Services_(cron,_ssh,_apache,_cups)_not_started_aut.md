---
title: "Services (cron, ssh, apache, cups) not started automatically after upgrade"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by cmcginty on 2009-12-11
I've been dealing with service startup problems on two different systems ever system I upgraded to Karmic 9.10.

I have a thread opened over here: [http://ubuntuforums.org/showthread.php?t=1305226](http://ubuntuforums.org/showthread.php?t=1305226)

I'm looking for any advice on this before I submit a bug to the launchpad.

Is there any info on the new boot process with upstart? What script is running the old /etc/init.d/* services?

thanks.

---

### Post by lemming465 on 2009-12-12
> Is there any info on the new boot process with upstart?
Some, but not as much as we'd like. Two possibly helpful starting points are:
[the main upstart page]("http://upstart.ubuntu.com/") (try the "Getting Started" and "FAQ" tabs first) and 
[the boot performance planning wiki]("https://wiki.ubuntu.com/FoundationsTeam/BootPerformance").
> What script is running the old /etc/init.d/* services?
As can be seen from /etc/init/rc.conf, the execution is by /etc/init.d/rc.  However, the scripts are run based not on what's in /etc/init.d, but rather based on what is linked from the /etc/rc?.d directories.  Default ubuntu (and Debian) systems boot to system-V style runlevel "2".

Does your /etc/rc2.d have S* links for the services you expect to be running?
if not fix that with your choice of runlevel editors.  A command line tool is *update-rc.d*; as usual read the man page before trying to use it.  There are various GUI or menu driver runlevel editors available too, such as *bum* or *sysv-rc-conf*.

---

