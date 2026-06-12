---
title: "Hoping I can get away with an upgrade.. not a format"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2010-04-25
I recently started getting an error message telling me that "A problem occurred when checking for the updates". I've tried to troubleshoot the problem but with no success, and the only other help I've gotten was "Change your repositories to something else" which was more frustrating than no response at all. 

Attempting to install updates from this warning does nothing, attempting to open the update manager also does nothing, and trying to open synaptic gives me this error message: 

```
E: The package devede needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

Since I can not get this resolved, I have decided this is a perfect opportunity to upgrade to 9.10 or maybe even 10.04?! I'm just wondering if anyone can tell me if an upgrade should resolve these issues or if I need to backup my data and format the drive and start from scratch? 

Any input or suggestions will be appreciated.

---

### Post by Gatemaze on 2010-04-25
Patience... neither an upgrade nor a format is necessary to resolve this... All repos are stored on /etc/apt/sources.list so it is a matter of finding the right repo for the program you want to update/install. With a quick look on the website of devede have you tried installing the debian package?
[http://www.rastersoft.com/descargas/devede_3.16.8-0~rastersoft1_all.deb](http://www.rastersoft.com/descargas/devede_3.16.8-0~rastersoft1_all.deb)

---

### Post by sp0nge on 2010-04-25
Affirmative. 

In trying to click-install the .deb, the machine tries to open the gui then closes. Install attempts via command line result in the following:

```
dpkg -i devede_3.16.8-0~rastersoft1_all.deb 
Selecting previously deselected package devede.
(Reading database ... 281614 files and directories currently installed.)
Preparing to replace devede 3.14.0-0~rastersoft1 (using devede_3.16.8-0~rastersoft1_all.deb) ...
  File "/usr/sbin/update-python-modules", line 45
    print x
          ^
SyntaxError: invalid syntax
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
  File "/usr/sbin/update-python-modules", line 45
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing devede_3.16.8-0~rastersoft1_all.deb (--install):
 subprocess new pre-removal script returned error exit status 1
  File "/usr/sbin/update-python-modules", line 45
    print x
          ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 devede_3.16.8-0~rastersoft1_all.deb

```

---

### Post by Sef on 2010-04-25
I would recommend having a Live CD (either for the os you are using or the current one), in case there is a problem with the upgrade.  And back up your data first before upgrading or installing.

---

### Post by Gatemaze on 2010-04-25
hmmm, it seems like the latest version of devede is incompatible with one of your older libraries... but let me ask, is your current version of devede owrking ok? you could get rid of the warning during the update but commenting out the (no longer existing?) repo for the devede in the /etc/apt/sources.list file.

---

### Post by sp0nge on 2010-04-25
No, DeVeDe is not working at all. It is completely unresponsive.

---

### Post by sp0nge on 2010-04-26
Bump.. 

I appreciate the effort thus far. I would *love* to fix the issue rather than start from scratch but I've come to accept the fact. However, can anyone tell me if an upgrade of my current system should be sufficient to fix the problem or if I really need to format and start over?

---

### Post by Gatemaze on 2010-04-29
An upgrade (to a compatible version) should be ok, but I am not really 100% sure... However, I always reinstall. Having a separate /home partition is a life-safer in this case as I don't need to touch my files...

---

### Post by lykwydchykyn on 2010-04-29
Can you post the output of 
```

python -V

```

The reason is, your update script is getting a syntax error with the code "print x".  

My suspicion is that your default python has been changed to python 3.x, in which case "print x" would be incorrect syntax.

You'd need to switch your default python back to 2.x if this is the case.  That'd probably fix things.

Of course, I could be way wrong, but it's worth looking at.

---

