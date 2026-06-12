---
title: "Can't download/install updates"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by nightmareci on 2007-07-25
I'm not exactly sure what caused this problem, but the file /var/lib/dpkg/status can't be read, written to, or deleted by any user (including root) on my system, and still cannot be tampered with on an external livecd system. I get this error from Update Manager, if I run it right now:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (13 Permission denied), E:The package lists or status file could not be parsed or opened.'

If it helps, my root filesystem is JFS (I read it can give better performance than ext3 in some situations). I read about some things that can be done on an ext3 partition to forcefully remove a file, but those methods won't work on a JFS partition. So, how do I make /var/lib/dpkg/status have proper permissions again, or get rid of it so it can be replaced with a copy with proper permissions? I don't understand how a file can become completely inaccessible to everyone.

---

### Post by tbroderick on 2007-07-26
Open a terminal and enter
```
ls -l /var/lib/dpkg/status*
```

If you have got a backup **status-old**, you can try renaming it to the current /var/lib/dpkg/status and renaming the old one. Then run,

```
sudo apt-get update
```

---

### Post by nightmareci on 2007-07-26
Sorry, you may be misunderstanding me, or I didn't quite explain it clearly enough, but absolutely no user as access to /var/lib/dpkg/status, AT ALL. Nothing can be done to the file, other than seeing that it "exists" in the file system. root cannot read/write to it, so what sort of user has even more permissions than root does? No matter what I do to that file, I always get "Permission denied". I cannot fathom what can be done to the file, outside of a total file system reformat.

When I did "ls -l /var/lib/dpkg/status*", it just gave "ls: status: Permission denied", just like anything else on the file. Is there really such a thing as an immutable file, and could this file be one?

---

### Post by meyou on 2007-07-27
I'm guessing you've already tried this, but try: chown -R root:root /var/lib/dpkg/status*

---

### Post by tbroderick on 2007-07-27
Did apt work before or has it always been like this? Maybe your root partition can not be JFS. File a bug report and see if anyone their can help you or reinstall with a differnet filesystem as root.

---

### Post by nightmareci on 2007-07-28
When I first had the system installed with a JFS root partition, there were no problems with anything vs. when I had the system formatted to ext3, but I think this issue popped up when I temporarily switched my ATi Radeon 9800 XT with my nVidia GeForce4 440 MX SE (it's far worse than the ATi card, so it's not worth using it just for nVidia drivers) when my video was freaking out sometimes (but I've fixed that issue... it was because the video card wasn't plugged in all the way, yet somehow still worked), but when I switched back to my ATi card the problem with the status file appeared. If I *must* reinstall my entire root partition to a different file system, I will, but I don't want to unless I really must.

---

### Post by Circuit99 on 2007-07-29
This might help have a look at this link.


[http://ubuntuforums.org/showthread.php?t=494869&highlight=error+302](http://ubuntuforums.org/showthread.php?t=494869&highlight=error+302)


What is your error message, post it?

---

### Post by nightmareci on 2007-07-30
Okay, when I did "sudo apt-get update", or upgrade, I get this same error, but otherwise package lists download fine and whatnot, and this error is the last thing displayed:
E: Could not open file /var/lib/dpkg/status - open (13 Permission denied)
E: The package lists or status file could not be parsed or opened.

I tried pulling up System Monitor and killing the update notifier, because I thought that maybe that part about "open" might be because update notifier had the file "open", but the same error occurred even when update notifier was killed. I also tried changing my session to Failesafe Terminal, but the same error STILL pops up. Plus, there's that problem with the file having these same "properties" when a livecd is running, with the file system mounted. And as an additional weird aspect of that status file, when ls is used in a terminal in it's directory, status' name is displayed with a black background and red text, and I don't know what that really means.

Oh, I just got a different error now (not sure how I made it happen), but here it is:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

Again, the error was the last thing displayed before apt-get gave up and closed.

---

### Post by jazzybob on 2007-08-07
I am having similar problems (I think)

E: Dynamic MMap ran out of room
E: Error occured while processing tightvnc-java (NewFileDesc2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
root@jazzybob-dell1501:/home/jazzybob#

---

