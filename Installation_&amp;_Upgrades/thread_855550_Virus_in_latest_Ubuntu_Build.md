---
title: "Virus in latest Ubuntu Build?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by k-bl on 2008-07-10
In Ubuntu 8.04.1 on install within Vista, avast! pops up during the installation and says that nearly all the temp files (c:\users\current_user\appdate\local\temp\nsl3355.tmp\nsB265.tmp for example) contain a Win32:Trojan-gen / Virus/Worm.  And then it gives me an error that "wubibcd" couldn't execute.  I imagine it's because I moved the temp file to the chest.


Is this for real?  I've downloaded it many times and did a full deep system scan and haven't found anything.  I hope that I'm wrong.

Anybody else running into the same thing?


K-BL

---

### Post by avtolle on 2008-07-10
IIRC, there was a thread on the Wubi forum about this, and there seems to be no problem. One user deleted avast, installed AVG free, and found no problem, and was then able to install. What consensus there is seems to be that this is a "false positive".

---

### Post by calraith on 2008-07-10
My $0.02: something-gen in the antivirus world indicates that the detection was based on heuristics, not by static definition.  There's apparently something in c:\users\current_user\appdata\local\temp\nsl3355. tmp\nsB265.tmp that has similar functionality to an actual Trojan that *is* in Avast's defs (perhaps a module that posts back tracking data during installation), or at least Avast's heuristics are overzealously suspicious of this potentially unknown virus.

False-positives happen.  For what it's worth, I wrote and maintain a custom NSIS installer for Symantec AntiVirus for my school, which tracks some unique information per user and posts back to a SQL database to enforce strict license compliance.  At one point, my installers kept disappearing from the web server.  Investigation revealed that Symantec AntiVirus running on the web server was deleting the Symantec AntiVirus installers because of Trojan-like behavior -- I assume because the installer was configured to phone home during installation.  It's ironic when antivirus software quarantines its own installer, though.

Just thought I'd share.  :)

---

### Post by k-bl on 2008-07-10
So, then, do you think it would be ok to disconnect from the internet, shut-down avast! and then run the installer (assuming that it has been scanned for virus before execution)?

K-BL

---

### Post by jimv on 2008-07-10
Usually anything that says "gen" or "generic" is possibly a virus, but the antivirus has no specific definition for it.  Most of the time it's a false positive.

---

### Post by k-bl on 2008-07-11
If you do get the error, simply disconnect from the internet, disable your virus software (with avast! simply right click and select "Stop On-Access Protection").

After you've done that, re-insert the cd and install it under windows (assuming you want dual boot), if you've already attempted an install, uninstall what's there (you'll be prompted to do so).

The install should go fine.  After it's done reboot, let ubuntu set itself up, and enjoy.

Worked for me :)


K-BL

---

### Post by phildaman46 on 2008-07-13
You can e-mail Avast at [email]virus@avast.com[/email] and ask if it's a false positive or a real virus. You can also send them the files you think are false positives in a zip file with the password: virus. I sent them quite a few files and most of them were false positives. Only one was a real virus. They may not tell you it's a false positive but when they update there virus definitions, those false positives are gone. They do tell you if it's a real virus but they don't tell you if it's a false positive for some reason.

---

