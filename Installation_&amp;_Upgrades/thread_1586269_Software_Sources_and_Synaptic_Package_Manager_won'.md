---
title: "Software Sources and Synaptic Package Manager won't run"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by kermittoad on 2010-10-01
Whenever I try to run the Software Sources and Synaptic Package Manager applications, 'Starting Administrative Application' appears briefly on the taskbar - and then disappears! And nothing starts.
 
I tried uninstalling and reinstalling them in case they were corrupt, but the same thing still happens.These two seem to be the only applications that behave this way, so can anyone think of anything that links the two of them and may cause this?

---

### Post by oldos2er on 2010-10-01
Try running ```
gksu synaptic
``` in a terminal; it may give some clues as to the problem.

---

### Post by drs305 on 2010-10-01
> **kermittoad said:**
> These two seem to be the only applications that behave this way, so can anyone think of anything that links the two of them and may cause this?

Both these rely on the package manager (APT). Most likely there will be an error message when you try to open Synaptic via the terminal as *oldos2er* recommends.

You may also get an idea via:```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by kermittoad on 2010-10-02
I inputted oldos2er's suggestion into Terminal, and after a couple of seconds delay it produced no output and returned me to the command prompt. I tried prefixing it with 'sudo' and it produced the next output.
 
I then tried drs305's suggestion and it produced the same result. I have to say that most of my sudo experience in Terminal has produced error codes.
 
```
[FONT=Courier New]gerald@gerald-Acer:~$[/FONT][FONT=Courier New] gksu synaptic[/FONT]
 
[FONT=Courier New]gerald@gerald-Acer:~$ sudo gksu synaptic[/FONT]
[FONT=Courier New]sudo: /etc/sudoers.d/README is mode 0460, should be 0440[/FONT]
[FONT=Courier New]>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<[/FONT]
[FONT=Courier New]sudo: parse error in /etc/sudoers near line 24[/FONT]
[FONT=Courier New]sudo: no valid sudoers sources found, quitting[/FONT]
 
[FONT=Courier New]gerald@gerald-Acer:~$ sudo apt-get update && sudo apt-get upgrade[/FONT]
[FONT=Courier New]sudo: /etc/sudoers.d/README is mode 0460, should be 0440[/FONT]
[FONT=Courier New]>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<[/FONT]
[FONT=Courier New]sudo: parse error in /etc/sudoers near line 24[/FONT]
[FONT=Courier New]sudo: no valid sudoers sources found, quitting[/FONT]
[FONT=Courier New]gerald@gerald-Acer:~$[/FONT]

```
 
I'm not very familiar with Linux so would appreciate any suggestions assuming a reasonable level of ignorance on my part.

---

### Post by drs305 on 2010-10-02
Boot to the recovery mode by choosing that option in the Grub2 menu. As the recovery mode boots, select 'root' to drop you to a prompt. Then run this command:

```
chmod 0440 /etc/sudoers.d/README
```

It is also reporting a parse error on line 24 of the above file. I don't have that many lines in my README file. Here is what my Lucid README file contains:

> 
#
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
#     #includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because the sudoers file is not a 'conffile' in the Debian 
# sense, and sudoers contents can vary widely, no attempt is made to add this 
# directive to existing sudoers files on upgrade.  Feel free to add the above 
# directive to the end of your /etc/sudoers file to enable this functionality 
# for existing installations if you wish!
#

It's possible you have the same plus more. You can run either of the following commands from the terminal to check it:
```
cat /etc/sudoers.d/README  # View only
nano /etc/sudoers.d/README # Edit 
```

If you aren't familiar with nano or don't know what you are looking at, just run the "chmod" command above and reboot. Then try synaptic or the update/upgrade commands to see if they now work. If not, at least you should be able to copy the contents of the /etc/sudoers.d/README so we can view it.

---

### Post by kermittoad on 2010-10-02
I tried -
 
```
[FONT=Courier New]sudo chmod 0440 /etc/sudoers.d/README[/FONT]
```
 
from the root but but it produced the same error codes as before. All previous attempts to change to mode 0440 have failed.
 
I then attempted to open the file in Terminal but was refused permission. Opening it in the root again produced the following output. I had to photograph it as there was no way to copy and paste it.
 
[IMG]http://i949.photobucket.com/albums/ad338/geraldcohen/Temp/sudoers-README.jpg[/IMG]
 
As you see, it doesn't have 24 lines and is pretty similar to yours.
 
The parse error was produced by the /etc/sudoers file, not the README one. I took a couple of shots of the /etc/sudoers file and it's below. Hopefully it will give a clue to the problem.
 
[IMG]http://i949.photobucket.com/albums/ad338/geraldcohen/Temp/sudoers2.jpg[/IMG]
[IMG]http://i949.photobucket.com/albums/ad338/geraldcohen/Temp/sudoers3.jpg[/IMG]
 
I can't see anything in line 24 (whichever one that is) that is producing the error code, but hopefully you may see something.  If I need to edit anything in the root, I'd really appreciate detailed instructions.

---

### Post by drs305 on 2010-10-02
From the recovery mode 'root' prompt, what happened when you ran the chmod command? Actually, 'sudo' probably shouldn't be part of the command since you are already in a root environment. I tried it with 'sudo' and it worked for me, but if you got error messages you should try running the command without 'sudo':
```
chmod 0440 /etc/sudoers.d/README
ls -la /etc/sudoers.d/README
```
After running this, the second command should show the following:
> -r--r----- 1 root root 819 2010-07-06 18:22 /etc/sudoers.d/README

**Added:** I am in the process of 'destroying' a Lucid VM. When I simply changed README to 444 I received the exact same error messages you did - I can no longer use 'sudo' and get the sudoers line 24 parse message. This means that there is nothing wrong with the sudoers file itself. I will post back as soon as I figure out how to repair this.

---

### Post by drs305 on 2010-10-02
> 
Added: I am in the process of 'destroying' a Lucid VM. When I simply changed README to 444 I received the exact same error messages you did - I can no longer use 'sudo' and get the sudoers line 24 parse message. This means that there is nothing wrong with the sudoers file itself. I will post back as soon as I figure out how to repair this.


The procedure I outlined should work.

[LIST=1]
[*]Boot to the Grub menu.
[*]Select a Recovery mode option.
[LIST]
[*]If you don't have a recovery mode displayed, highlight an Ubuntu entry.
[LIST]
[*]Press 'e' to enter the edit mode.
[*]Cursor to the "linux" line.
[*]Del the "quiet splash" and add "single" at the end of the line.
[*]CTRL-x to boot
[/LIST]
[/LIST]
[*]Select 'Drop to a root shell prompt'
[/LIST]
Run:
```
chmod 0440 /etc/sudoers.d/README
```
Check the properties:
```
ls -la /etc/sudoers.d/README
```
It should look like:
> -r--r----- 1 root root 819 2010-07-06 18:22 /etc/sudoers.d/README
Reboot:
```
reboot -n
```

---

### Post by kermittoad on 2010-10-03
BRILLIANT!!
 
I inputted as you advised into root and got the following output -
 
[IMG]http://i949.photobucket.com/albums/ad338/geraldcohen/Temp/sudoers3oct.jpg[/IMG]
 
The date and time is different to yours, but the format is the same.
 
I then rebooted and tried to start Synaptic Package Manager...
 
...and it worked!  So did Software Sources.  I then started Update Manager, who's failure to work properly had originally set me on this solution hunt.  Previously, it had started but refused to do any updating.  But now it works as well.
 
Thank you drs305 for an accurate and detailed solution to my problem.

---

### Post by drs305 on 2010-10-03
Edited: See it's Solved now. Thanks.

kermittoad,

Glad you have your system back to normal. :-)

When the original poster has his problem resolved, it helps if he/she marks the thread SOLVED. It allows those looking for solutions to find threads that contain a valid answer and also lets the helpers concentrate on unresolved problems.

You mark it SOLVED via the 'Thread Tools' link near the top right of the first post, and you can remove the tag from the same place if necessary.

Happy Ubuntu-ing !

---

### Post by proch04 on 2010-12-10
Not so Fast. I followed the direction and got the same results as  you did and still getting the error in [http://ubuntuforums.org/showthread.php?t=1586269]("http://ubuntuforums.org/showthread.php?t=1586269")[http://ubuntuforums.org/showthread.php?t=1586269](http://ubuntuforums.org/showthread.php?t=1586269)

---

### Post by drs305 on 2010-12-10
proch04,

Welecome to the Ubuntu forums.

Normally it's best to start your own thread. Since this one is several months old I suppose the original poster won't mind continuing here.

Your post is a bit confusing, with the thread linking to this same thread.

What errors specifically are you getting, and when running what command?

---

