---
title: "Fixing semi-broken/fixed privileges in /usr"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by barkerson on 2015-09-23
So I was compiling Krita version 2.9.7 (since latest ubuntu version was 2.7.2). When compile was finished I thought I was going to be smart by using (gksudo) nautilus to prevent issues when moving files. I was wrong, very VERY wrong. after a couple of hours I managed to first set all files and folders in /usr* to 777. Then I was able to set sudo to 755 and be able to do things through terminal like usual, except for getting xserver to work.

So basically, is there a super awesome mega code/script I can create for fixing the mess I have created, or is there something built in?
Help is much appreciated

---

### Post by TheFu on 2015-09-23
Restore from a backup taken before the screw up.

[B]Do NOT use GUI programs as root - ever.
Do NOT use GUI programs as root - ever.
Do NOT use GUI programs as root - ever.[/B]

If you don't have a backup - make one now and reinstall the OS, then restore your data back.
Learn this lesson today - it has paid off well over the 20+ yrs I've been a user, programmer, and administrator of Unix and Linux systems.  File and directory permissions are absolutely critical for a properly working AND secured system.

---

### Post by ajgreeny on 2015-09-23
Regrettably, I think TheFu has given the only sensible answer you can use.

There a number of different permissions required for the many thousands of files and folders in /usr, so there is no simple change of permissions possible using a chmod command.  As above, and this time I will shout it as loud as possible even though it is normally frowned upon in the forum,
 **DO NOT USE GUI APPLICATIONS AS ROOT - EVER** 
unless like synaptic package manager, for example, they are specifically designed to be run that way for a particular purpose.

---

### Post by barkerson on 2015-09-23
gathered as much, then I just have to copy over my files, wipe and reinstall 15.04, and just copy over back. No worries though, thanks for input!

---

### Post by TheFu on 2015-09-23
Provided "my files" are only the files your userid owns, normally, sure.
There are some files in /etc and perhaps under /var or /opt whichmight also be nice-to-have.  Of course, we don't know anything about your system, so "my files" may include DBMS data files, locally compiled programs that you put/installed into /usr/local (and elsewhere) ... basically, only you will know where these are.

Versioned daily/weekly backups would make this a slight inconvenience - about 45 min to restore. I once lost 80% of my data - that learned me about **backup religion**. Just like regular style - it only works if you do it in advance of the need.  Obviously, the more you move/customize from a stock install, the more important this is.

---

### Post by barkerson on 2015-09-26
I still had the compiled version of Krita in another folder, so I just have to finish copying over the ~400 gigs of data I had to my empty 2TB drive I wasn't using.
Guess only thing now is finding a thread on moving/merging through terminal commands, no harm done other than a loss of time. Also I really need to clean out junk from yesteryear, I got files I've migrated from drives over 10 years old in various folders.

---

