---
title: "Cannot login after update"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by barbablu on 2009-12-24
Just updated the system and now I can no longer login.

Following a reboot, I am presented with the usual list of local users in the standard ubuntu interface.  I select my user icon and instead of offering me a password entry field, it immediately reports the error "Unable to authenticate user" and I am returned to the list of local users.  Same result if I select any other user.

I run Ubuntu 9.10 which I installed about a month ago in a dual-boot configuration alongside Windows XP on a separate partition. Last week I installed OpenOffice Base and yesterday TTPT packages for VPN connectivity to my office. Today I ran Update Manager which installed a number of packages (maybe a dozen, no reboot required). Then I logged out (to let another user login) and that's when the problem started.

I tried starting in safe mode and choosing the option to repair packages. No improvement on restart. 

I can login at the console in safe mode, but I am unsure how to proceed from there.

Any suggestion?

---

### Post by DrMelon on 2009-12-24
If you start normally, (i.e, not in safe-mode) you can press Ctrl+Alt+F2 at the login screen to enter another console. You can login there, and type "startx" to start the user interface.

While this is clumsy, it will allow you to use your desktop until you can reach a solution.

---

### Post by llawwehttam on 2009-12-24
do check in /etc that passwd and shadow are existent and not corrupted. sounds like the passwd file is broken more than shadow though.

---

### Post by barbablu on 2009-12-24
Thank you for the prompt response.  Very useful tip.  

However, I could only startx from the root shell in safe mode.  When I try from a normal boot, I get an error about the display being already in use by another session.  I tried removing some lock file in the tmp directory as suggested by some automatic feedback from the startx attempt, but no luck.

The in-use symptoms continue: I now have my usual desktop through the startx route, but when I started Evolution, a prompt for access to the keyring came up, suggesting that it was in use.  This is confusing me, given the number of restarts I have made in the past hour or so. Maybe a side-effect of the safe-mode start.

---

### Post by barbablu on 2009-12-24
@[llawwehttam]("http://ubuntuforums.org/member.php?u=930300") 
Thank you.

Password authentication appears to work well at the shell with su <user>: it succeeds with with a good password and fails with a bad one.

---

### Post by barbablu on 2009-12-26
The ubuntu login screen still reports authentication failure even before giving me the opportunity to enter a password (same with all users).

Tried a few options on the safe mode menu: repairing packages, memory test (gave up after half-an-hour at the start of the 3rd pass, having accumulated about 1200 errors - is that serious?).  

Now reduced to boot in safe mode and drop to shell, su to my username and startx. Works ok for web browsing, email, but no sound and limited administration (can change my password, but not reset others; cannot change to auto-authentication on login screen - just testing, never used before).

Tried Update Manager again (nothing to update). Tried re-installing the ubuntu-desktop packages. Looked through the logs for clues...

I would greatly appreciate suggestions on strategy to pin down issue..:confused:

PS Not sure if significant, but the last operation before that fatal update a couple of days ago was to reset a user's password (in a rush). Password authentication on that user works (failing with incorrect password).

---

### Post by phillw on 2009-12-26
Hi,

This is a bit of a dirty hack, but may get you up and running ....

```

If you forgot you password for your ubuntu system you can recover using the following steps

Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot

```

You'd be after doing it for an admin user - like yourself, after that, you should be able to reset the others via the normal way.

There are other ways - but it does sound like either your passwd or shadow file has checked in sick.

Regards,

Phill.

---

### Post by barbablu on 2009-12-26
@[phillw]("http://ubuntuforums.org/member.php?u=824544") Thank you for the the very prompt suggestion.  I am so impressed with this forum on the speed of responses.

You are not the first to suggest a problem with the password/shadow, so I felt I had to give a go at resetting some passwords.  I did it from a root shell using the passwd command.  I changed mine and the other user I mentioned in an earlier post.  Unfortunately, it made no difference at the login screen.

There are many operations suggesting that authentication on its own works well. Examples, including some I mentioned before:
1. at the shell I can su <user> and test passwords (with failure and successes as expected).
2. In the About Me dialog I can authenticate myself in order to change my password (positive case only).
3. The Update Manager is set to auto-update, but when I press the Check button, I am asked to authenticate myself (positive case tested only).
4. I am asked my password when Evolution is accessing my keyring/password vault.

I looked that the /etc/passwd and shadow files and they do not have any sign of random corruption (though, not being an expert, they might be broken in a subtle way).

There are cases that suggest that the desktop is struggling to resolve authentication calls:
1. at the login screen (where it all started :(
2. In the About Me dialog when entering a bad password to authenticate myself (it just stays there with the message "Checking password...", but pressing Close works; maybe it is the way it normally works)

Is there a way to see where the system is going wrong?

---

### Post by phillw on 2009-12-26
> **barbablu said:**
> @[phillw]("http://ubuntuforums.org/member.php?u=824544") Thank you for the the very prompt suggestion.  I am so impressed with this forum on the speed of responses.

You are not the first to suggest a problem with the password/shadow, so I felt I had to give a go at resetting some passwords.  I did it from a root shell using the passwd command.  I changed mine and the other user I mentioned in an earlier post.  Unfortunately, it made no difference at the login screen.

There are many operations suggesting that authentication on its own works well. Examples, including some I mentioned before:
1. at the shell I can su <user> and test passwords (with failure and successes as expected).
2. In the About Me dialog I can authenticate myself in order to change my password (positive case only).
3. The Update Manager is set to auto-update, but when I press the Check button, I am asked to authenticate myself (positive case tested only).
4. I am asked my password when Evolution is accessing my keyring/password vault.

I looked that the /etc/passwd and shadow files and they do not have any sign of random corruption (though, not being an expert, they might be broken in a subtle way).

There are cases that suggest that the desktop is struggling to resolve authentication calls:
1. at the login screen (where it all started :(
2. In the About Me dialog when entering a bad password to authenticate myself (it just stays there with the message "Checking password...", but pressing Close works; maybe it is the way it normally works)

Is there a way to see where the system is going wrong?


Hi, IMHO.... we can spend hours trying to repair it, or we can more productively put our time to a back up & clean install.

If it is that un-happy, then something really bad has happened and you want to get your data off there. Unlike other operating systems, Linux will not just roll on its back with the legs up in the air (with a slight hint of blue).

Can you confirm are you
1) using Wubi
2) dual booting with Win
3) booting with other linux systems
4) 100% Ubuntu

and also what backup devices you have - external hard-drives etc.

I'm minded to do a re-install, if others believe they can heal your system - please listen to them.

Phill.

---

### Post by barbablu on 2010-01-02
Reluctantly, I gave up on finding the problem preventing logging in and went for a re-install (first time with Ubuntu).

I have a dual-boot with Windows XP on the first partition (hardly ever used).  Created backups using sbackup. Re-partitioned the hard-disk, installed afresh from Ubuntu desktop CD, restored packages (including ones from additional software source for the Opera browser), re-created my users (in same order so to preserve uid sequence, just in case it might have helped with file ownership with later restores from sbackup), restored /home but none of the other root-level folders.  Several times I restarted the machine to see if the problem re-occurred, but it hasn't so far.  There were a few hiccups here and there but overall, if was not too difficult, just time consuming.  I am just so glad that I use NAS and IMAP servers to store anything valuable.

Thank you all for the prompt and helpful advice.

---

