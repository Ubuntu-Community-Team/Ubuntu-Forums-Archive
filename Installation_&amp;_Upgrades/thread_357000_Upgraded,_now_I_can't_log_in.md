---
title: "Upgraded, now I can't log in"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Zarkoth on 2007-02-09
It all started with Youtube, so if I can't fix this, I'll take a whack at suing them for emotional damages.  However, to save on court costs, I'd rather fix this thing.  So I'm on Youtube and see a video with beryl on it.  Basically, I instantly re-fell in love with linux.
       Being the can-do man I am, I got right to it with an upgrade to edgy eft.  I just went through my repo file and switched all the dapper's to edgy's.  Simple enough, right?  Did the appropriate apt-get commands and woo hoo.

So I re-start afterwards and I get to my log in screen and nonchalantly type in my username and password.  The login screen disappears, and suddenly I find myself in a terminal login, only for it to flash straight back to the login screen.  In a mad frenzy, I attempted logging in under several configurations, KDE, Gnome, Failsafe Gnome, I even used my guest account a few times.  At one point I received this error message in a friendly window-

```
GDM could not write to your authorization file.  this could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator
```

Well, I checked from my XP install, and I've got space (although it's only 250 megs) and so  here I am. 

I do remember a small error with one package during the upgrade, but foolishly dismissed it as moot, and have forgotten what it was.  I do vaguely remember it starting with an "m" and having no vowels, but then that doens't help much.

Any ideas?

---

### Post by gradedcheese on 2007-02-09
AH, you did not follow the official upgrade procedure (which is not to replace everything with edgy in sources.list and then apt-get upgrade).  There's a sticky thread at the top of the forum: [http://www.ubuntuforums.org/showthread.php?t=286599](http://www.ubuntuforums.org/showthread.php?t=286599)

I suppose that you could have a permissions problem with some files needed by GDM (and others).  That should be easy to fix from the shell.  By the way, to switch to a text shell, press Control+Alt+F1 (actually F1 through F6 are text shells).  Now do an "ls -al" in your home directory and check that permissions look good: you can read files, they belong to the same user/group as you are, etc.  

Try starting X from your text shell, perhaps you'll get more error output that way ("startx" should do it), you can press Control+Alt+Backspaces to kill X (which it hangs, for example) and drop back to the shell.

---

### Post by Zarkoth on 2007-02-09
Cool, thanks very much.  I'll go ahead and try all that, as a side note, I went and tried again, and noticed that the CLI login that comes up for a split second shows Ubuntu 6.06, so...yeah.  Also, nothing fails on start up.

At any rate, I'll try that and get back to ya.

---

### Post by Zarkoth on 2007-02-10
Succes!  Well, sort of.  I successfully updated, although it didn't go exactly smoothly, perl kept having error about my locales, I think, but nothing so bad as to stop everything.  So I reboot, to see if everything worked right, and it's the same problem as before, just take away the brief terminal login.

So I get the exact same error as before, I'll check my privileges, but I can't see how that'd happen, I've never touched 'em.

Also, when I run "startx" I don't get any errors, it just starts right up.

---

### Post by Zarkoth on 2007-02-10
Yeah, don't know why I keep rapid-firing posts...but oh well

I checked those privileges and I've got root privileges on everything....so.....what now?

---

### Post by Zarkoth on 2007-02-10
I ran "gdmsetup" after doing a little research in the documentation, and got this error - 

```

root@zarkoths-lair:~# gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

```

---

### Post by gradedcheese on 2007-02-10
> 
Could not access GDM configuration file.


That's likely a permission problem.

Files in your home directory should belong to you, with permission to read/write.  Substitute 'username' with your user name in this post.  So a file (I'm picking a random one in /home/username) should look like this in ls -al

-rw-r--r--  1 username username       414 2006-11-29 21:19 .bash_profile

If yours are instead owned by root, you need to fix this.  One way is to reboot and boot up in recovery mode.  This will give you a root shell.  You can then change ownership:

chown -R username.username /home/username

Perhaps also ensure that things are readable:

chmod -R +r /home/username

Now reboot:

shutdown -r now

...and see what happens.  Also you can try any of the above commands (well, beside the reboot) as sudo, perhaps that will work without rebooting into the recovery mode.

---

### Post by Zarkoth on 2007-02-13
Well, I did all that good stuff, but...the problem remains the same.

Just a thought, but could I do the exact same thing I did originally, with my sources.list and change it back to dapper?  I imagine it wouldn't help much but...it might be worth a try?

---

### Post by Zarkoth on 2007-02-14
Well, I feel like an idiot.  Turns out I didn't have *enough* disk space, I did sudo aptitude clean and yeah, now I can log in.  But thanks for all of your help, I really appreciate it!

 - Zarkoth

---

