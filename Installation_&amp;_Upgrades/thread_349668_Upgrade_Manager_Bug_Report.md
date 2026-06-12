---
title: "Upgrade Manager Bug Report"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by TheBrain0110 on 2007-01-30
Well, I decided I'd try the upgrade manager today, and get some testing done in Feisty. I ran 
$ gksu "update-manager -d -c" , since various guides have said either the -d or the -c switch, and I couldn't find any acutal docs on what they are, I threw in both. Probably not relevant, but its possible.

Anyway, it purred along nicely, updating all the repositories, and was in the middle of double-checking the apt databases and other "verification" stuff before the actual package files were downloaded, when it spat out a 'Fatal Error'

```
Traceback (most recent call last):

  File "/tmp/tmpAJKyFT/feisty", line 44, in ?
    app.run()

  File "/tmp/tmpAJKyFT/DistUpgradeControler.py", line 760, in run
    self.edgyUpgrade()

  File "/tmp/tmpAJKyFT/DistUpgradeControler.py", line 739, in edgyUpgrade
    if not self.askDistUpgrade():

  File "/tmp/tmpAJKyFT/DistUpgradeControler.py", line 435, in askDistUpgrade
    if not self._checkFreeSpace():

  File "/tmp/tmpAJKyFT/DistUpgradeControler.py", line 420, in _checkFreeSpace
    free_at_least = apt_pkg.SizeToStr(abs(fs_free[dir].free)+1)

TypeError: Only understand integers and floats

```

So apparently my free disk space is not a number? Strange, but that's what its telling me.

On a possibly-but-not-likely related note, dbus doesn't appear to be working for me. Pretty much any program that I launch (from the terminal anyway, as GNOME programs won't tell you), it says "warning: could not initiate dbus". Of course, they load anyway, and seem to run fine, but I thought I'd mention it.

Anyway, I've attached the upgrade logs for anyone who would like to read them. I added the .txt extension, as .log isn't one of the ones allowed by the forum uploader.

Oh, and when it quit, it didn't rollback properly, so I had to manually overwrite sources.lst with the backup it made. So there are some cases when it isn't crashproof...

---

