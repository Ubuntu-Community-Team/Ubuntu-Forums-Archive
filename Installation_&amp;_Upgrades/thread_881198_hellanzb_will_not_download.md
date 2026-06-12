---
title: "hellanzb will not download"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by orozcovision on 2008-08-05
Hello Everyone,

Not sure if a lot of people are experiencing the same troubles I am with getting hellaznb to download.  So far, it seems to be an issue with Hardy.

Anyway, here's a quick list of what I've tried so far.  If anyone has done anything different, please share.  Otherwise, hope this post helps you out.

1). Installed Needed files:
```
sudo apt-get install python-dev python-twisted unrar par2
```

2). Installed hellanzb (currently version 0.13-3)
```
sudo apt-get install hellanzb
```

3). Configured .conf file (e.g. Username, Password, Host, etc.)
```
sudo vim /usr/etc/hellanzb.conf
```

4). Running hellanzb is no problem.  It actually reads the queue, and parses .nzb files.  However, after opening it's connections, it doesn't download anything.

Example:
```
hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
(giganews) Opening 10 connections...
hellanzb - Now monitoring queue...
Parsing: nzb file ....
Parsed: 35 files (728 posts), 446.9MB
Queued: 446.9MB
[01]
[02]
[03]
[04]
[05]
[06]
[07]
[08]
[09]
[10]
[Total] 0.0KB/s, 446 MB queued, ETA: 00:00:00

```

After doing some research, I found a bug which was reported [here]("https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/233900").

Apparently, some folks have resolved this issue by making some minor changes to two different files:

1). NZBParser.py
2). Protocol.py

On my system, both files are located in:
```
/usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/
```

As per the bug description, modifying either file should do the trick.  As a developer, I personally find it is always better to go after the root of the problem.  So, I first chose to modify NZBParser.py:

```
sudo vim /usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/NZBParser.py 
```

Navigated to line 152; changed:
```
newsgroup = self.parseUnicode(''.join(self.chars))
```

to:
```
newsgroup = self.parseUnicode(''.join(self.chars)).strip()
```

I saved my changes, and ran hellaznb.  Of'course, it didn't fix the problem for me. I moved on to modifying Protocol.py:

```
sudo vim /usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/Protocol.py 
```

Navigated to line 513, Added "group = group.strip()" after line:

```
     
if not self.factory.skipGroupCmd:
   # Change group
   for group in self.currentSegment.nzbFile.groups:

      # Added to fix bug
      group = group.strip()

      # NOTE: we could get away with activating only one of the groups instead
      # of all
      if group not in self.activeGroups and group not in self.failedGroups:
         debug(str(self) + ' getting GROUP: ' + group)
            self.fetchGroup(group)
            return

```

Finally, saved my changes, and ran hellanzb.  Sadly, this also did not work for me.

Again, if anyone has done anything different to fix this issue, please share.  Otherwise, I hope this post helps you out.

Best,
OrozcoVision

Resources:
[http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb+won%27t+download](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb+won%27t+download)
[https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/233900](https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/233900)
[http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6](http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6)

---

### Post by biodiesel-bri on 2008-11-12
Look at the hellanzb ticket again, but further down; the proper fix is posted there.
[http://www.hellanzb.com/trac/hellanzb/ticket/393](http://www.hellanzb.com/trac/hellanzb/ticket/393)

---

