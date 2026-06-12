---
title: "Minor problems with chmod command"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by Gustaf_Alhll on 2014-10-28
What I've been trying to do lately is to install NetBeans IDE for Linux, but I have some issues by doing that.

From the instructions I read, the only thing I need to do is to run "chmod +x [Directory]" in the console. I did that, but literally nothing gets returned. Nothing pops up on-screen, nothing happens to the computer. Not even the terminal itself returns anything.
When I intentionally type in an invalid directory, it returns:
```
chmod: kan inte komma åt ”/home/gustav/Skrivbord/netbeans-8.0.1-javase-linux”: Filen eller katalogen finns inte

Translation: chmod: cannot reach ”/home/gustav/Skrivbord/netbeans-8.0.1-javase-linux”: The file or folder doesn't exist
```
But when I type it correctly, nothing happens at all (Then I mean that even less happens than when I intentionally mistype). Should this happen? Am I doing something wrong? Should I use something else than +x?

Thank you.

---

### Post by TheFu on 2014-10-28
Generally, shell commands don't complain when things work. Check the permissions on the directory to see that what you did worked, if it was even needed at all.

There are many short tutorials on file/directory permissions or you can learn more about non-GUI Linux here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) It is a free, no-hassle, PDF download ... or you can buy the book from dead trees, if you like.  Having a little more background in the OS design and architecture will save you hours, days, weeks of frustration - skim the 1st 100 pgs. No need to read it, just skim.

---

### Post by Gustaf_Alhll on 2014-10-28
> **TheFu said:**
> Generally, shell commands don't complain when things work. Check the permissions on the directory to see that what you did worked, if it was even needed at all.
Well, I rather would say that it ignores since nothing gets returned. I've also tried running it with Sudo, no good.
Also, I'm pretty sure that I have permission to the desktop (Since Skrivbord is translated to Desktop in english). And shouldn't the terminal say something in either cases?

Should I try to boot the file with the terminal? Do you think that works?

*EDIT: Found the error. Apparently, JDK didn't come with the installer.
I'm going to install it and see if it works then.

*EDIT2: Problem resolved. It all works now.

---

### Post by TheFu on 2014-10-28
> **Gustaf_Alhll said:**
> Well, I rather would say that it ignores since nothing gets returned. I've also tried running it with Sudo, no good.
Also, I'm pretty sure that I have permission to the desktop (Since Skrivbord is translated to Desktop in english). And shouldn't the terminal say something in either cases?

Should I try to boot the file with the terminal? Do you think that works?

The return code is stored in a shell variable that you can check, if you like. This is the way that commonly used UNIX/Linux command work and have for ... 40 yrs.

NO. The terminal is not supposed to say anything if no error is caused.  UNIX has a history of "do what I say"  and don't bother me unless there is an issue.  As you gain more experience, you'll come to appreciate this greatly.

Check the permissions. Verify they are what you want. There is no shortcut to understanding file and directory permissions. Sorry. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is the shortest I've seen that covers just the basics.

---

### Post by Gustaf_Alhll on 2014-10-28
Alright, problem resolved. JDK was missing, that's why it didn't work. Thanks anyway.

---

### Post by TheFu on 2014-10-28
> **Gustaf_Alhll said:**
> Alright, problem resolved. JDK was missing, that's why it didn't work. Thanks anyway.

JDK has nothing to do with chmod. I suppose the issue was something completely different.

I still hope you'll skim that book. It will really save you time.

---

