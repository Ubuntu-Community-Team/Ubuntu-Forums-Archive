---
title: "Ubuntu: List of installed applications"
date: 2022-09-19
forum: Installation &amp; Upgrades
---

### Post by benjaminbreeg on 2022-09-19
Running Ubuntu 22.04.1. Is there a way to obtain a definitive list of installed applications **together with** the **directories where they are installed**? The commands I know (apt list and dpkg -l) do not do that ... unless there's a further parameter to be specified in the command line, which I have no knowledge of at this point in time.

Many thanks!

---

### Post by TheFu on 2022-09-19
Packages don't get installed into a single directory, so this question really doesn't work the way I suspect you hope it does.

Packages contain
* programs and support scripts
* libraries to support the program(s) in the package
* settings (either generic config files or templates)
* starter DB files (can be almost anything from SQLite, to dbm to text, to 500 other types.
* manpages  - manpages are placed by section. Learn more about manpage sections using the 'man man' command
* documentation - This can be longer files, html, doc, pdf, info or other sorts of helpful files. The README or INSTALL text files are examples, but some projects make extensive text documentation that goes beyond what a man page covers.  Sometimes examples are placed in this area, especially config file examples for complex setups.

The Linux File System Hierarchy Standards specify were each of those things should be placed.  Each in that list has multiple locations where that type of file can be placed.

This is for APT or RPM package managers.
flatpacks and snaps work different.
Manually installed files, say compiled from C or C++ source code and be put all sorts of places - it is up to the admin to choose, but the best location is under /usr/local/ with the split of  bin/, etc/, lib/, doc/, man/, ... you get the idea. Those are relative paths, not absolute.

The manpage for dpkg has lots and logs of options to show how to pull information from a package (.deb) header.  For example, a list of every file in the package and where it should be installed into is in there.

Probably best to search for the Linux File System Hierarchy Standards document and read it.  For me the 1-page table has always been sufficient.  It is very worth while understanding where files go on Unix.

However, if you plan some other purpose beyond general knowledge, then there is 100% a better solution.

```
$ dpkg -l
```
will provide a list of installed, partially installed, removed, packages.  It is everything that APT knows about.  With a little 'grep', that list can be restricted to just installed packages.  But for backups, there are better ways to get that list.  'apt-mark' will pull the list of packages from APT too and we can ask for manually installed packages, which is much more interesting than the thousands of automatically installed packages.  'man apt-mark' has more details on the options.  I use this method to get a list of manually installed packages nightly and save that list into a location for daily backups to capture it.  At restore time, the last step I perform is to feed that list of manually installed packages into APT to be installed on the new system/hardware/OS install.  There is little need to backup installed programs that came through APT. I don't bother, since reinstalling them is trivial and very automated.

---

### Post by benjaminbreeg on 2022-09-19
Thank you! I imagine I could re-phrase my question by specifying the type of file that I am looking for, along the lines of: "list of all applications, plus the **location of the main executable**," though I am guessing that you'd reply that it is not clear what I mean by "main executable."

Anyway, looks like snap might install all snapped applications (meaning everything pertaining to the snapped application) into the /snap/ folder, is that so?

---

### Post by TheFu on 2022-09-19
Snaps are an abomination, IMHO.  They don't work on many of my systems because we don't use /home/ for users HOME directories and because we are cross-platform, the suggested snap workaround isn't an option.

Snap packages are read-only, compressed, files and the snapd daemon mounts at boot (or first invocation?) to strange /dev/loop[1..999] devices.  If you boot using a flash drive into a Try Ubuntu environment and look at the installed Ubuntu files for snaps on the real system, you'll not find a program file. It will be a snap package buried down in /var/lib/snap/.... and there will probably be 3 versions, eating 10-100x more storage than a .deb package uses.

To get a list of installed snaps, use
```
$ snap list
```

As for where the main executable gets installed for an apt/deb package, that's easy ... 99% of the time they are put into /usr/bin/  . Some admin-only tools get put into /usr/sbin/   <--- these locations are spelled out in the standards document I suggested above.

---

### Post by TheFu on 2022-09-19
> **benjaminbreeg said:**
> Thank you! I imagine I could re-phrase my question by specifying the type of file that I am looking for, along the lines of: "list of all applications, plus the **location of the main executable**," though I am guessing that you'd reply that it is not clear what I mean by "main executable."

Actually, that is perfectly clear, but things are so simple.  In Unix, we often have a compiled binary and a startup script.   Both are the "main executable", since the startup script sets environment variables needed for the binary program to run successfully.

Let's use firefox.  Suppose you've avoided using the snap version, which you should for many reasons.  Anyways, to find the program, we can use 
```
$ which firefox
/usr/bin/firefox
```
Seems simple, right?  but /usr/bin/firefox isn't really the program. It is a script. See
```
$ file /usr/bin/firefox
/usr/bin/firefox: symbolic link to ../lib/firefox/firefox.sh
```
So we need to check out 
```
$ file /usr/lib/firefox/firefox.sh 
/usr/lib/firefox/firefox.sh: POSIX shell script, ASCII text executable
```
Ah ... a shell script, as predicted above.  If we look at that script ... way down at the bottom we see:
```
exec $MOZ_LIBDIR/$MOZ_APP_NAME "$@"
```
That's the binary file ... see:
```
$ file  /usr/lib/firefox/firefox
/usr/lib/firefox/firefox: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=176a7faada6ae3fd57f9d260e6cf8cf8480a93af, stripped
```
Just to show the vast difference in file size:
```
$ ls  -lF  /usr/lib/firefox/firefox*
-rwxr-xr-x 1 root root 777624 Aug 19 01:23 /usr/lib/firefox/firefox*
-rwxr-xr-x 1 root root   2667 Aug 19 01:23 /usr/lib/firefox/firefox.sh*
```
750KB for the binary.  2.5KB for the script.

Which is the main executable?  In the menu, it will be the symbolic link to the script.

---

### Post by ian-weisser on 2022-09-19
> **benjaminbreeg said:**
> ...definitive list of installed applications **together with** the **directories where they are installed**?

A good answer depends upon what you intend to do with the information.

For example, some folks ask for a list of applications for backup purposes -- they want to make sure they backup their applications. This is usually unnecessary for most folks for several reasons. Regardless, the information they actually find most useful is the name of the snap packages or the top-level debian packages that are NOT already included with a stock install of Ubuntu.

Is that where you were headed? Or did you have a different goal in mind?

---

### Post by benjaminbreeg on 2022-09-22
Thanks for the advice. Ideally I would feel much better knowing that one application is installed in one place, and not scattered all over the place on the hard drive--let's say out of a sheer obsessive-compulsive need for tidiness. Anyway, if that's not how Linux does it, then that's it, and I'll have to live with it, however much I may hate this "philosophy."

Be that as it may, sometimes--such as it is the case with the MakeMKV/VLC couple--you need to know where some file is installed in order to make a symlonk to it etc.

All in all, I, for one, feel much better knowing where my application files are located on the hard drive. (Yes, I know, there is such a ting as "search etc. etc. etc.")

---

### Post by ian-weisser on 2022-09-22
One big problem with knowing "all applications" is that an Ubuntu system is made up of many hundreds (thousands!) of applications from hundreds of upstream projects. The little wireless strength indicator? That's a simple little independent application running. Log service? That's another application. Daily log-rotate action? That's yet another application.

You might do better to consider just the user-facing applications that you care deeply about: Your web browser, your mail client, your spreadsheet, your movie player, your games, etc. That list is reasonable.

Now that you have a reasonable list of applications, look at which snap-packages and which deb-packages provide those applications.

Snap packages:
 - All application files are in /snap. For example, Firefox application files are in /snap/firefox
 - User files, including your profile, are in /home

deb-packages are spread across the filesystem. Run "dpkg -L <packagename> to see the each file and location.

File locations are hard-coded in each package -- you sacrifice that choice in order to use packages for easy install/update. Folks who don't use packages (compile from source -- advanced!) get to make those choices for themselves.

---

### Post by TheFu on 2022-09-23
> **benjaminbreeg said:**
> Thanks for the advice. Ideally I would feel much better knowing that one application is installed in one place, and not scattered all over the place on the hard drive--let's say out of a sheer obsessive-compulsive need for tidiness. Anyway, if that's not how Linux does it, then that's it, and I'll have to live with it, however much I may hate this "philosophy."

Be that as it may, sometimes--such as it is the case with the MakeMKV/VLC couple--you need to know where some file is installed in order to make a symlonk to it etc.

All in all, I, for one, feel much better knowing where my application files are located on the hard drive. (Yes, I know, there is such a ting as "search etc. etc. etc.")

There is a reason that package files go into different locations - Unix has this idea of a read-only file system and for a long time, we'd use shared storage for things that don't change across 5-5000 servers.  But settings and logs and data would often be different, so those things needed to be on read-write storage.  Putting all of that under a single mount, breaks that capability.

The main reason to know where files are stored today is to ensure your backups get the stuff that is specific to your system, not the program, but the data and settings.  They aren't "all over the place", since system settings go into /etc/, user settings go under that user's HOME, system data usually goes under /var/lib/ and user data goes under that user's HOME, unless we do something specific to place it elsewhere.
There is an elegance, when you look deeper and understand the history a bit.  The people before us were pretty smart and tended to follow the philosophy that things should be only as complex as required, but no more.

BTW, it isn't a Linux thing. It is a Unix thing.

---

