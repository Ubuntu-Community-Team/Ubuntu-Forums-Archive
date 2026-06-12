---
title: "wubi says &quot;permission denied&quot;"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Mark_Galeck on 2010-05-26
Hello,

I am trying to install Ubuntu with Wubi, on XP Pro. wubi.exe downloads, but when I run it, click "Install", and then I get an error window that says:

"An error occured:
Permission denied
For more information, please see the log file (...)wubi-10.04-rev189.log"

I do have all the permissions on XP, this is admin account.  The file above does not exist (I do show hidden files).  I searched the filesystem for any files with wubi...log and there are none.  

I disabled the Windows Firewall too.  

There is a thread here that deals with this issue, the resolution is to "unhide" various folders, I have them all unhidden already, does not help.  

What to do?

Thank you,

Mark

---

### Post by thinktyler on 2010-06-13
Try downloading the ISO from ubuntu's website. Then replacing the ISO into your C:\Ubuntu\Install\ubuntu*.iso - 

*Make sure you uninstall wubi first. Install wubi, then replace the ISO when you enter your username and password and then continue. 

I haven't been able to isolate the problem as of now, but this seems like a solution.

Disabling "Hide extensions for known file types" and checking "show hidden files and folder" did fix it for me. (It didn't do it the first time, so try it again)

---

### Post by Jack9394 on 2010-06-15
:confused:
Test it but no go..
Copy the file to the directory but still having the same error...

---

### Post by d3v1150m471c on 2010-06-15
wubi is almost always a bad idea... use the live cd to install.

---

### Post by varunendra on 2010-06-15
The OP's problem has actually been solved. see [here]("http://ubuntuforums.org/showpost.php?p=9373919&postcount=6").

---

### Post by lisati on 2010-06-15
> **varunendra said:**
> The OP's problem has actually been solved. see [here]("http://ubuntuforums.org/showpost.php?p=9373919&postcount=6").

Thread closed

---

