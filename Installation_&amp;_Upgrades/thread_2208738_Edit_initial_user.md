---
title: "Edit initial user"
date: 2014-03-01
forum: Installation &amp; Upgrades
---

### Post by mastermwf-l on 2014-03-01
I had a brain fart while installing Ubuntu 12.04.4 LTS (64 bit) and typed the wrong name for the initial user during install. How do I change it without re-installing? I managed to set up dual boot Win 8.1 and Ubuntu and don't want to try the OEM install again.

I have read about dpkg-reconfigure but I am unfamiliar with the syntax.

[FONT=times new roman][SIZE=1]

Tread lightly and listen for the "click" of the land mine you just stepped on[/SIZE][/FONT]

---

### Post by TheFu on 2014-03-02
The steps are very easy.
* drop to single-user mode - that will leave you as "root" - no need to reboot.
* Edit a few files in /etc - changing the old name into the new name **everywhere**
** passwd - 2 places
** groups - at least 1 place, probably more
** shadow - 1 place
** check the sudoers (visudo) whether it needs to modified or not. May not be needed.
* move the user's HOME ... 

Switch back into multi-user mode .. or reboot - doesn't matter which.

Actually, if you don't change the HOME for the user inside the passwd file, then you don't need to move it on the disk.

No need to change any file ownership - the uid, not the username are used for that, so it will be fine.

There may be configurations, settings and scripts that still refer to the old username. These shouldn't be part of any system files ... just poorly written applications, since they should do everything based off "HOME", which we've changed.  Obviously, if you've done anything to point to the OLD HOME directory that isn't based on $HOME or ~/ ... then those will need to be changed too - like softlinks.  Hardlinks shouldn't be an issue and if you don't know what I'm talking about, things should be fine.

Doing the things inside /etc/ all at once is important. Do not reboot between unless you plan a way to get back into single user mode (recovery boot?).


Or you could just create a new user and put that new userid it the same groups as the main one.  Test that it does everything you want, especially sudo stuff before deleting the old userid. Don't forget to move the OLD-userid files over to the NEW-userid.

---

### Post by steeldriver on 2014-03-02
How about (from single-user mode as above - easiest way may be to reboot into recovery mode and then remount the root filesystem rw)

```
# usermod -l *newname* -d /home/*newname* -m *oldname*
```

If you also have a user private group with the same (incorrect) name then fix that with

```
# groupmod -n *newname* *oldname*
```

If you also need to change the 'display name' (aka fullname) you can do that at any time using chfn

```
$ sudo chfn -f '*new fullname'* *name*
```

---

### Post by mastermwf-l on 2014-03-03
I am going to try @steeldriver's Code as soon as I get to some decent WiFi. If I hand grenade Ubuntu in this environment, I will be stuck with Microsux Win 8.1 until I get  back on dry land. 

When I tried using chfn, I got an error that chfn does not exist

@TheFu I am not sure which few files need editing, so I will play it safe and edit none.

Thanks for the help. Worst case scenario, re-install!

---

### Post by Bucky Ball on 2014-03-04
Welcome. [This]("http://www.ubuntututorials.com/change-username-ubuntu-12-04/") and [this.]("https://duckduckgo.com/?q=change+username+ubuntu+12")

Please read the first line of my signature. ;)

---

### Post by TheFu on 2014-03-04
> **mastermwf-l said:**
> I am going to try @steeldriver's Code as soon as I get to some decent WiFi. If I hand grenade Ubuntu in this environment, I will be stuck with Microsux Win 8.1 until I get  back on dry land. 

When I tried using chfn, I got an error that chfn does not exist

@TheFu I am not sure which few files need editing, so I will play it safe and edit none.

Thanks for the help. Worst case scenario, re-install!

No worries. @steeldriver's method just edits those "few files in /etc" that I've listed above. Sorry my wording was confusing. Editing files is how all settings are controlled on UNIX-like systems. Sometimes a command has been created to modify those files, but not always. In more complex environments with network logins, using the commands is _better_, since it should know about those networked settings. Very few non-corporate desktops use those.

Just to clarify, /etc is a directory. It holds account information and system settings. The files are in the bullet list above are the ones to be modified - either by using an editor or the commands. Those files are safe to view. Take a look. Nothing complex about the files at all.

A reinstall is highly unlikely - perhaps 2%. This stuff is easy.

---

