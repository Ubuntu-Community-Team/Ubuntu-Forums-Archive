---
title: "dual booting ubuntu 10.04 with WUBI"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by nathanielsaxe on 2010-10-22
So basically, I installed Ubuntu 10.04 using Wubi. Installed fine, no error messages or anything. But when i restarted and booted into Ubuntu, it would do some finalizing install and then come up with

"No root file system is defined" and it won't go away when I click cancel or whatever.
But I can't do anything in it. It's just the background picture.

I have a live cd and that works fine.

I'm on a Dell Studio 15 windows 7 Home Premium.

Any help appreciated.

---

### Post by drs305 on 2010-10-22
If this is a new Wubi install, the fastest way to fix this is probably just to try to reinstall it. You remove Wubi from Windows via the Windows Control Panel, Add/Remove Programs.

If you would rather spend time trying to troubleshoot this, run *meierfra's* boot info script. When you paste the contents of RESULTS.txt, use "code" tags which you generate by pressing the # icon in the post's menubar.

---

### Post by Dale61 on 2010-10-22
There is already an ongoing discussion on this very problem.

[No root file system is defined.]("http://ubuntuforums.org/showthread.php?t=1601818")

---

### Post by nathanielsaxe on 2010-10-23
I reinstalled it with no avail. 

I tried to install it without wubi, booted using the livecd then chose install. and now its telling me that theres no partition map. Only two options, no install alongside.

when i chose the manual install, it shows 500gb (size of harddrive) of unallocated space and tells me to create a partition map. If i do, then it'll wipe everything off the harddrive.

---

### Post by drs305 on 2010-10-23
If you still have (or think you have) the wubi installation, open Windows and copy the file c:\ubuntu\winboot\wubildr  to c:\Windows . That will replace the current *wubildr* file. Reboot and try to run wubi again.

If you don't have the file in c:\ubuntu\winboot\wubildr , I attached it to Post # 57 of [this thread]("http://ubuntuforums.org/showpost.php?p=10003840&postcount=57").

If that doesn't get wubi working (and you have it installed) there is another thing we can try. See the first paragraph (Wubi Users) of this thread, which I updated yesterday: [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by nathanielsaxe on 2010-10-23
> **drs305 said:**
> If you still have (or think you have) the wubi installation, open Windows and copy the file c:\ubuntu\winboot\wubildr  to c:\Windows . That will replace the current *wubildr* file. Reboot and try to run wubi again.

If you don't have the file in c:\ubuntu\winboot\wubildr , I attached it to Post # 57 of [this thread]("http://ubuntuforums.org/showpost.php?p=10003840&postcount=57").

If that doesn't get wubi working (and you have it installed) there is another thing we can try. See the first paragraph (Wubi Users) of this thread, which I updated yesterday: [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

sorry, a bit confused. So I install ubuntu via WUBI then get the file from c:\ubuntu\winboot\wubildr  to c:\Windows?

---

### Post by drs305 on 2010-10-23
> **nathanielsaxe said:**
> sorry, a bit confused. So I install ubuntu via WUBI then get the file from c:\ubuntu\winboot\wubildr  to c:\Windows?

Well ... yes. I brought it up in case you still had the wubi installation on your system but couldn't get it to boot. In that case, you would boot Windows, open the file manager, copy c:\ubuntu\winboot\wubildr and replace c:\Windows\wubildr. The wubildr file in c:\Windows apparently is flawed. Replacing it with the one in the ubuntu\windboot folder has fixed this issue for quite a few users.

If you didn't still have wubi installed, you would have to decide if it was worth it to reinstall and then try this method. Sometimes I have a hard time intentionally installing something I know is broken in the first place. The fix may or may not work. It's up to you to decide if you want to 'invest/gamble' your time trying this method.

---

### Post by nathanielsaxe on 2010-10-23
ah ok. cheers. I might take a look sometime later than. Got other stuff to do now.

---

