---
title: "Server boot: tty comes too early"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by pbatt on 2008-03-17
I have server 7.10 installed. During startup there is a tty login coming up too early while there are still components to be loaded. tty login comes immediately after loading ssh server. The startup sequence does not stop there, however. The login prompt is overwirtten by loading of mysql, postfix, samba, ftp, winbind, atd, cron an apache. After that the /etc/rc.local script is executed an the prompt hangs unless I press Enter. It is only then that tty login comes up again and I can login normally. Is there a way to correct this?
Thank you, Paul

---

### Post by mrsteveman1 on 2008-03-17
The login program does run before the rest of the system is done running init scripts, but i've never seen it cause a real problem, because although those messages continue to appear they are simple console messages, not programs running in the foreground on that TTY. You could force the system to wait until everything else is done before bringing up login by changing the order of the init scripts, which might help a bit. You could also change to tty2, which should have no console messages.

You could also configure syslog so that it only prints messages at the error level, this would stop the information notices but still leave in errors so you can see when something is wrong. Another option would be to get syslog to print messages to tty4 etc, so that tty1 isnt affected.

I was under the impression that the "quiet" option passed on the kernel commandline (in grub) was supposed to suppress a lot of these messages, but perhaps not.

The hang you specify i believe is caused by the login prompt pausing because of a failed login, so it waits a second before giving you another login prompt. You might try just pretending the random messages weren't on the screen, and type your username, hit enter, then your password, and hit enter. It should login normally because the system thinks you are just seeing the login prompt. We have to do this on cisco routers a lot because the OS prints messages while you are typing commands, but they don't actually affect anything if you type correctly.

As long as you can login eventually its technically OK, but it would be nice to fix the order or suppress the console messages that aren't really needed.

---

### Post by pbatt on 2008-03-18
Your're perfectly right, ignoring the mess on the screen and typing in my username brings everything back to order. Also ttyX work well, as do ssh logins. So there's really not more to it than aesthetics. Since I seldom ever see the startup screen at all I rather leave everything as is. Don't mess up a working system. Thanks!
Paul

---

