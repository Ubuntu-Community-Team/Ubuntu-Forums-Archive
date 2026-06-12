---
title: "Cannot sudo after upgrading from 9.04 to 9.10."
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by arvinoids on 2009-12-29
I recently upgraded our local webserver from 9.04 to 9.10. The upgrade was successful, but after that, I am not able to do sudo on the terminal anymore (also gksudo or gksu). After entering the password and pressing enter, it just goes right back to the shell. Also, if I try to launch a program that requires admin i.e. Synaptic, it asks for the password, but after entering the password it does nothing. I don't know where to start with this issue.

I am still able to login as root into recovery mode, though. Also, I don't know if this has nothing to do with the sudo problem but when I login remotely through telnet or ssh, it just disconnects the session after entering the password.

Any help? :confused:

Thanks

---

### Post by phillw on 2009-12-29
Hi & Welcome, 

> It is trivial to reset the password in the recovery shell. Just type passwd along with the name of the user to reset: eg # passwd *username* Enter new UNIX password:

Or, as you only did an upgrade, you *should* still be on grub legacy... so...

> If you forgot you password for your ubuntu system you can recover using the following steps Turn your computer on.
 Press ESC at the grub prompt.
 Press e for edit.
 Highlight the line that begins kernel &#8230;&#8230;&#8230;, press e
 Go to the very end of the line, add **rw init=/bin/bash**
 press enter, then press b to boot your system.
 Your system will boot up to a passwordless root shell.
 Type in passwd  username
 

Should work for you.

Regards,

Phill.

---

### Post by arvinoids on 2009-12-29
Actually, I have no problem with the password, I am confident that it is correct because if I enter an incorrect password, it gives a login incorrect error (or the "sorry" error if I am trying to sudo). So there is no reason to change the password. The problem is that it does not do anything after executing anything with sudo.

---

### Post by phillw on 2009-12-29
welcome back... okies .. looks like a problem with sudoers ....

This can SO easily be messed up - So, being the devout coward that I am , I'm going to send you to a "How-To" written by one of the forum Mods on the subject.

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

I **cannot** stress strongly enough that you use **visudo** as he states.

Anyways, that should get you up and running, feel free to pop back if you get stuck.

/edit, once you get the feel of the warnings and how it works, continue reading the posts.... you'll find a link to your answer, I'm not going to post it - as it is REALLY important that you have some understanding, but it is there :-)

Regards,

Phill.

---

### Post by arvinoids on 2010-01-29
> **phillw said:**
> welcome back... okies .. looks like a problem with sudoers ....

This can SO easily be messed up - So, being the devout coward that I am , I'm going to send you to a "How-To" written by one of the forum Mods on the subject.

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

I **cannot** stress strongly enough that you use **visudo** as he states.

Anyways, that should get you up and running, feel free to pop back if you get stuck.

/edit, once you get the feel of the warnings and how it works, continue reading the posts.... you'll find a link to your answer, I'm not going to post it - as it is REALLY important that you have some understanding, but it is there :-)

Regards,

Phill.

I went ahead and did the visudo thing by logging on through Recovery Mode. After examining the configuration, it appears that everything is correct, so I just went ahead and saved the file and exited. I restarted to log back in normal mode. I am still not able to sudo or login to the terminal or SSH to the machine. Again, the password is correct because if I logout from the desktop and log back in, it goes through.

Also, in case I have not mentioned earlier, when I go to the terminal (i.e. alt+ctrl+f1 to f6) and try to login, it does not give me a shell. It just brings back the same login prompt with no error messages or authentication problems.

Any more ideas?

---

