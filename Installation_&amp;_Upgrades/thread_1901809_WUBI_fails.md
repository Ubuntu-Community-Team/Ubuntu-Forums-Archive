---
title: "WUBI fails"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by paulcliman on 2011-12-29
I'm trying to install Ubuntu onto a Windows 7 machine in a slave drive.
I have dowloaded the .iso file and I have downloaded the wubi.exe file.
Each time I try to run this I get a warning box titled "pyrun.exe-No Disk" and a message within "There is no disk in the drive. Please insert a disk into drive /Device/Harddisk2/DR2
CANCEL >>TRY AGAIN >> CONTINUE"

This box REFUSES to go away and I have to reboot just to get rid of it.

What am I doing wrong ?
Thanks in anticipation...

---

### Post by vieridipaola on 2012-02-04
I'm having the same problem here.
Trying to run WUBI on Windows 7. It immediately fails with a message from pyrun.exe:

No disk
"There is no disk in the drive. Please insert a disk into drive \Device\Harddisk3\DR7.

Any ideas?

[EDIT] never mind. Just pressed "continue" several times and it finally went on. Not too elegant but anyway...

---

### Post by Frogs Hair on 2012-02-04
> **paulcliman said:**
> I'm trying to install Ubuntu onto a Windows 7 machine in a slave drive.
I have dowloaded the .iso file and I have downloaded the wubi.exe file.
Each time I try to run this I get a warning box titled "pyrun.exe-No Disk" and a message within "There is no disk in the drive. Please insert a disk into drive /Device/Harddisk2/DR2
CANCEL >>TRY AGAIN >> CONTINUE"

This box REFUSES to go away and I have to reboot just to get rid of it.

What am I doing wrong ?
Thanks in anticipation...

If  you download the ISO file and created a cd you can choose the Wubi option from the cd . If you use Wubi exe it will download the ubuntu files for you . I am not sure why you have both .

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Wubi Help : [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Wubi Mega)

---

### Post by darkod on 2012-02-04
Due to windows security options, for vista and 7 you should not start wubi.exe with the standard double-click. Instead with right-click, Run As Administrator option. That way it runs with max permissions.

Also, if you want to avoid that wubi downloads the files itself, you need to put both the ISO and wubi.exe in a same folder, and run the exe. If the ISO for the same version (exactly same) is in the same folder, it doesn't download anything, it uses the ISO.

wubi.exe is also included in the ISO so to make sure you have the same version you can simply extract wubi.exe from the ISO and use that one.

---

### Post by bcbc on 2012-02-04
I just double click on Wubi.exe and it works fine (win7). My account has administrator privileges. I suppose if you're not running an administrator account you'd have to run as administrator, but windows would moan about it in that case.

The 'no disk' problem is a longstanding bug in wubi... [https://bugs.launchpad.net/bugs/365881](https://bugs.launchpad.net/bugs/365881)
I don't know when they'll fix this - I'm guessing never. There are workarounds mentioned in the bug report, but it's a pain.

---

