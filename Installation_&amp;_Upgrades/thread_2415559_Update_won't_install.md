---
title: "Update won't install"
date: 2019-03-27
forum: Installation &amp; Upgrades
---

### Post by ewog on 2019-03-27
Good afternoon -

I am having troubles updating Ubuntu 16.04 LTS.  I found the following errors:

**System Notification:**
An error occurred, lease run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Error: BrokenCount was >0'.
This usually means that your installed packages have unmet dependencies.

**apt-get update:**
ktm@LittleMan:~$ apt-get update
Reading package lists... Done
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)


**apt-get install:**
ktm@LittleMan:~$ apt-get install
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
[B]
apt-get upgrade:[/B]
ktm@LittleMan:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


**Software Updater Error:**
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

libperl5.22: Depends: zlib1g (>= 1:1.2.2.3) but 1:1.2.8.dfsg-2ubuntu4.1 is installed
             Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.6) but 5.22.1-9ubuntu0.5 is installed
perl: Depends: perl-base (= 5.22.1-9ubuntu0.6) but 5.22.1-9ubuntu0.6 is installed
      Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.6) but 5.22.1-9ubuntu0.5 is installed
      Depends: libperl5.22 (= 5.22.1-9ubuntu0.6) but 5.22.1-9ubuntu0.6 is installed


**apt-get install -f:**
ktm@LittleMan:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


I cannot find if I'm using any third party repositories, and I don't think I am.

Does anyone have suggestions on how to resolve my update problem, and get it to work/run?

Thanks!

Paul

---

### Post by QIII on 2019-03-27
Hello!

The first problem you must correct is that you appear to have two package management interfaces open.  Please close them all and use only one:  either a gui or command line.  Don't have both open at the same time.

If that doesn't work, sometimes the lock is not released and we can help you through correcting that.

---

### Post by again? on 2019-03-27
> **ewog said:**
> Good afternoon -

**apt-get install -f:**
ktm@LittleMan:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), [COLOR="#FF0000"]are you root?[/COLOR]

You need to precede admin terminal commands with sudo.
eg
```
sudo apt-get install -f

```

You can check for third party repositories with (don't use sudo)...
```
software-properties-gtk --open-tab 1
```
Will bring up a gui where you can uncheck selected repos.
[ATTACH=CONFIG]282869[/ATTACH]

---

### Post by QIII on 2019-03-27
Ach!  Good catch.  Too distracted here, I suppose.

---

### Post by again? on 2019-03-27
Yes, I didn't notice it at first as the error notifications are similar.

---

### Post by ewog on 2019-03-28
Thanks, guber2 and QIII -

I ran the commands with sudo, and came up with the results in the attached PDF.  I've put each command line in **bold**, so they should be fairly easy to locate.

The System Notification message is no longer popping up.  And, it looks like by running Update and Upgrade via *sudo apt-get* that I'm trusting I have the latest updates to 16.04 LTS.

One oddity in all of this is that I have been successfully receiving updates for the past year, and I had made no changes to the selected repositories (before this error showed up).  Currently, in the gui "System Settings", under the heading 'System', there is no Update icon, whereas there was one when all this started (see attached JPG).  Any idea why it was removed?

Thanks for the help!

Paul[ATTACH=CONFIG]282874[/ATTACH]

---

### Post by again? on 2019-03-28
Occasionally, when packages have changing dependencies you may need to run full-upgrade
to intelligently handle the changing dependencies.
Check what output you get from...
```
sudo apt full-upgrade
```

I haven't used 16.04 with Unity for a long while so not aware of current issues.
The application that shows as "Software and Updates" in system settings is software-properties-gtk
Run in terminal ...
```
sudo apt install software-properties-gtk
```
****NOTE**** Only confirm to install if it's not removing other packages.
If unsure post your terminal output.

---

### Post by oldos2er on 2019-03-29
> **ewog said:**
> Thanks, guber2 and QIII -

I ran the commands with sudo, and came up with the results in the attached PDF.  I've put each command line in **bold**

Rather than doing this, please copy/paste all the text output into your post here using [codetags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"). Thanks.

---

