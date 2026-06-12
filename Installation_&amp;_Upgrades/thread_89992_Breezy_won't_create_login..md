---
title: "Breezy won't create login."
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Carbon Copy Man on 2005-11-13
While installing Breezy Badger, it wouldn't let me create my login. 

I got up to that part of the process, and typed in name, username, password, confirm password. But after pressing Enter, it'd put me back to entering my name.

After trying it again a few times, I wasn't getting anywhere. I just pressed Esc, and skipped to the next part of the installation.

So the computer restarts, Ubuntu loads up and it complains that I haven't got a root password. It comes up with a prompt and I try to enter it, but it still seems to have the problem and won't save it.

And I'm stuck.


By the way, the first hard disk of my computer was partitioned for Windows XP (NTFS) and extra space (FAT32).

The second, which I installed on, I partitioned into root (the Ubuntu default format -- name forgotten), /boot (same), /home (FAT32), & swap.

---

### Post by yesplease on 2005-11-14
I remember that one has to use lower case letters for the user name (no capitals). Does the installer give a comment at the point where things go wrong?

---

### Post by Carbon Copy Man on 2005-11-14
The installer itself didn't report any errors. I would get past the password screen and it'd pause before sending me back to the name screen.

When I booted up Ubuntu it said the problem was that the password was empty. After typing in a new password it reported an error and wouldn't save it.

My username was all in lowercase.

I'll have to get back to you about the exact error message I got.

Thanks.


**Edit:**
It starts with the error message:[INDENT]You entered an empty password, which is not allowed. Please choose a non-empty password.[/INDENT]

And then, after typing in a new password (and it only asks for a password), it says:[INDENT]groupdel: group carboncopyman does not exist
chpasswd: line 1: unknown user carboncopyman
chpasswd: error detected, changes ignored[/INDENT]

---

### Post by bcochran on 2005-11-14
I was having this exact same problem just a few minutes ago and was browsing the forum looking for a solution... I installed and reinstalled the os like 15 times already and kept running into this same problem. you finally get past the create user screen, and reboot then it tells you theres a bunch of errors and wont let you log in.
I finally figured out what was causing the problem (or so I think), I noticed in your post you mentioned creating a fat32 partition during the install... I too was trying to make a fat32 partition during the install... I just let it auto partition the drive, and this time around I got past that create login screen fine. 
Try getting rid of the fat 32 and see if that helps... it fixed my problem.. not sure what having a fat32 partition would have to do with creating a login, but it seems to have fixed the problem and let me install the os.
Give it a try and lets hear how it worked out?

---

### Post by Carbon Copy Man on 2005-11-14
I guess it's possible that the partition interferes with it. Well, I'll just have to try reinstalling it again without the FAT32.

---

### Post by bcochran on 2005-11-14
let us all know if that worked or not.

---

### Post by Carbon Copy Man on 2005-11-15
Reinstalled without the FAT32, and my login created fine. 

Although now I'm in, I'm having a problem getting it to work with my wireless. Perhaps I should start a thread somewhere else?

---

### Post by yesplease on 2005-11-16
I found it curious that install on fat32 could continue, while you cant write a user name or password. 

On the Dutch forum I was told that it is unsafe to put passwords on fat 32, while ext2 and ext3 allow safety measures.

It is a bug that you can continue to install, and this bug is already repaired for the Dapper release.

---

### Post by bcochran on 2005-11-19
I wasn't making a fat32 partition for the os to install on, I was trying to make an extended partition for just storing files on that was fat32.

---

### Post by yesplease on 2005-11-19
[QUOTE=bcochran]I wasn't making a fat32 partition for the os to install on, I was trying to make an extended partition for just storing files on that was fat32.[/QUOTE]

Carbon Copy Man tried to make a fat32 /home partition, but your case is interesting too. 

Anyway, I just posted it because it might be of interest to readers who bump into this problem.

---

### Post by Frymaster on 2005-12-16
Thank you... you have pinpointed a problem that doesn't seem to appear in the release notes, or the bug tracker (or that I could find searching kubuntu support - which was the distro I was actually trying to install) or that anyone in #kubuntu knew about, or most people on this forum judging by my search.  Many thanks :)

can I suggest that if this is a known problem (implied by dapper having a fix for it) then the lack of mention of this problem in the "known issues" section of the release notes (or in any other "official" place for that matter) is maybe a cause for concern?

---

### Post by Carbon Copy Man on 2005-12-16
Well, I'm no expert on such things, but it does sound like it's worth a mention in an official place somewhere.

---

