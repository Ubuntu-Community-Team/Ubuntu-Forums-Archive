---
title: "severe graphics flicker with radeon - post alpha-3"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by skitching on 2010-03-12
I recently installed lucid alpha-3, and all worked fine.

But after upgrading to the latest packages, the screen flickers *very* badly (basically unusable). Installed alpha-3 again fresh on different partition, and all works fine there (I'm creating this thread from a plain unupdated alpha-3 install).

So it appears that graphics on this system has been broken by something between alpha-3 and latest.

Weirdly, the flickering does not happen immediately. If I boot the bad (updated) lucid system, then the login screen displays fine. Without doing anything (no login, etc), after about 30 seconds mild flickering starts, and gets progressively worse. After about 2 minutes system is unusable. Same happens if I log in.

If I shutdown and immediately restart, the flickering is there immediately. But if I shutdown, wait 10 mins or so, then restart then the flickering does not begin for 30 seconds or so.

So it is perhaps something related to power-management in the ATI Radeon driver?

System details:
  HP Compaq nc8430 laptop, Core Duo T2500@2ghz
  ATI Radeon Mobility M56P X1600, running at 1680x1050, 60hz

More detail about flickering: the screen appears to lose "vertical sync", redisplaying at various vertical offsets for a few frames. Initially, it displays the screen mostly correct with just a few "displaced" frames per second. Then it progresses to where just about every frame is displaced at some random vertical offset from where it should be, effectively "flickering" madly up and down.

There is nothing odd in dmesg.

I'm happy to test patches, try reconfiguration etc. Just let me know what..

---

### Post by Rob2687 on 2010-03-12
Do you have any extra PPA packages installed?

---

### Post by skitching on 2010-03-12
Forgot to mention, I searched the lucid forums and didn't find any other reports that sound the same.

The following do sound a little similar but are probably not related:

[http://ubuntuforums.org/showthread.php?t=1408036](http://ubuntuforums.org/showthread.php?t=1408036)

[http://ubuntuforums.org/showthread.php?t=1384443](http://ubuntuforums.org/showthread.php?t=1384443)

---

### Post by skitching on 2010-03-12
Rob: thanks for replying. No PPA packages are installed.

I've discovered that the problem is in the kernel; booting with 2.6.32-14 works fine. Booting with 2.6.32-16 triggers the flickering.

---

### Post by rockyjones on 2010-03-12
I have a Thinkpad T-60 with the mobility radeon x1300 and have this problem but ONLY if I log on manually (or log off then log back on).  If the system starts up and auto logs me on (as I have it do by default), I do not experience any flickering.  Weird!

---

### Post by psyke83 on 2010-03-12
Hi,

I have a laptop with a Radeon IGP 345M.  I experience the "vertical rolling" (your description sounds very similar, if not identical), except that it has occurred with all 2.6.32 kernel versions, including those released prior to the alpha 3 release.

If your problem is related to mine, then it's a problem with kernel modesetting. You can workaround the with the "nomodeset" kernel boot option. Alternatively, try the [2.6.33 kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/") - kernel modesetting works properly on my system with that release.

---

### Post by skitching on 2010-03-12
It looks like there are several ways to trigger this "vertical rolling" problem. The symptoms I got are very distinctive, and not like those described by rockyjones or psyke83. I have therefore filed a bug specifically for the issue I found:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538344)

This is specifically a problem introduced between 2.6.32-14 and 2.6.32-16, so should be fairly easy to locate. It's 100% repeatable for me.

It looks like KMS for intel graphics chips has a separate issue. As that has been fixed upstream in 2.6.33 the fix will presumably be backported to lucid sometime soon without any need for a bugreport.

The thinkpad+radeon issue *might* be related to mine. Rocky, do you get this problem with 2.6.32-16 but not 2.6.32-14? If so, you might want to watch for any responses to the above bugreport and test them out...

Ah the joys of alpha software :-)

---

### Post by psyke83 on 2010-03-13
> **skitching said:**
> It looks like there are several ways to trigger this "vertical rolling" problem. The symptoms I got are very distinctive, and not like those described by rockyjones or psyke83. I have therefore filed a bug specifically for the issue I found:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538344)

This is specifically a problem introduced between 2.6.32-14 and 2.6.32-16, so should be fairly easy to locate. It's 100% repeatable for me.

It looks like KMS for intel graphics chips has a separate issue. As that has been fixed upstream in 2.6.33 the fix will presumably be backported to lucid sometime soon without any need for a bugreport.

The thinkpad+radeon issue *might* be related to mine. Rocky, do you get this problem with 2.6.32-16 but not 2.6.32-14? If so, you might want to watch for any responses to the above bugreport and test them out...

Ah the joys of alpha software :-)

Our symptoms may differ, but the results could be identical. At the very least, try my suggestions and report back here (or on your bug report, if suitable). If you can verify the issue as related to KMS, then it's helping to diagnose and resolve the problem.

---

### Post by ubfu on 2010-03-13
Having screen flicker and fan problem. It's still alhpa , will wait for the beta 2.

---

### Post by skitching on 2010-03-15
> **psyke83 said:**
> Our symptoms may differ, but the results could be identical. At the very least, try my suggestions and report back here (or on your bug report, if suitable). If you can verify the issue as related to KMS, then it's helping to diagnose and resolve the problem.


I've done further testing, and can say:
  2.6.33 --> flicker
  2.6.34 pre rc1 (commit 3474cbd11df8cdd6413781ea95bd51dd469098ff) is good, no flicker.

So at least the problem appears to have been fixed in HEAD. Hopefully the patch will find its way into the 2.6.32 series soon..

And booting with "nomodeset" also seems to prevent flicker, even on 2.6.32-16 or 2.6.33. Of course there are disadvantages to that..

---

### Post by mervinb on 2010-03-16
I am testing Lucid with a Dell Studio 15 (RV620). I can confirm that I see precisely the same flickering on the 2.6.32 and 2.6.33 (mainline) kernels. With 2.6.34rc1, the flickering is completely gone, but there is still a problem with suspend.

On suspend/resume (with 2.6.34rc1):

1. Fan does not resume. System can get very HOT!
2. acpi/acpitools show temperature of 0 degrees.
3. Warning notification of kernel unstable.

With hibernate/restart, all the above do not appear.

Hope this info may be useful to someone.

---

