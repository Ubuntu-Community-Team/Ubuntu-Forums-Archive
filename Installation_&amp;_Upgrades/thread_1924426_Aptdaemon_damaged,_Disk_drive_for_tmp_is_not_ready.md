---
title: "Aptdaemon damaged, Disk drive for /tmp is not ready, RW access to HD from Live CD?"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by innerspaceboy on 2012-02-12
I have been using Ubuntu 11.10 since December 2010 and had a previous version dual booting with Windows 7 in the past.  I've been able to solve all problems I've encountered by searching the Web this far, until yesterday's error.  I consider myself a beginner.

Yesterday **aptdaemon** became damaged and my system would no longer boot.  Removing and reinstalling it didn't work, manually running updates from the command line didn't work, and as a last resort I inserted my Ubuntu 11.10 Live CD and ran "Upgrade to 11.10" to replace the OS and preserve my personal files.

Sadly, I still can't boot - I still get the same error:

**"The disk drive for /tmp is not ready or not present" **during startup.

Then I thought I'd just boot to the restore CD, mount my HD, back up my most recent files and do a full format but no matter what I do, I can't gain RW access to the HD.

I am denied permissions to view or copy any files from the HD.

When I boot to the Live CD and type "sudo nautilus" into terminal it  generates a sea of error codes and does not unlock disk access. Nor does any variation of the "sudo mount" command that I've tried. 

I'm pretty sure it all started with the update manager, I've found reports from users online who were getting the same tmp error at boot. I had selected shutdown when firefox was non responsive and from then got this error - 

[B]"An unhandlable error occurred, there seems to be a programming error in aptdaemon... " 

"Traceback... File /usr/lib/puthon2.7/dist-packages/aptdaemon/worker.py......." [/B](and other errors)

**"Filesystem check or mount failed" **now happens at boot.

Pressing F for fix in the recovery console generates pages of errors and doesn't fix the problem.

I also tried M for manual repair with the following commands I found on the forum:

sudo mount -n -o remount,rw /
sudo dpkg --configure -a

or

sudo mount /dev/sda1 -o rw,remount
sudo dpkg --configure -a

Neither do anything, I press enter and it goes to the next line without any processing time.

I read that the "gksu nautilus" command grant rw access within the gui file browser but it returns a number of errors including,

**"Nautilus could not create the folder /root/.config/nautilus"**

I created the folder and then got other errors.  It starts to let me look at folders on the HD, but quickly hangs or denies access.

Two other commands I read about and tried were

sudo apt-get install (no changes made)
qtk2-engines-pixbuf (to fix another of the many Nautilus errors)

sudo fsck -n /dev/sda1 returns the message that **/dev/sda1 contains a file system with errors.**

A final recurring error that keeps turning up is while attempting to browse folders - 

**"There was an error while getting the sharing information 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares.  Error, no such file of directory."**

Can anyone help me either gain RW access to my file system to back up my latest files and reformat or better still fix the** "disk drive for /tmp is not ready or not present" **message at boot so the system boots again without the Live CD?

[SIZE=2]*Thank you*[/SIZE] in advance!

---

### Post by innerspaceboy on 2012-02-12
Tried a few additional commands after pressing M for manual repair -

sudo apt-get update returns several lines beginning with

**W: Failed to fetch...**

sudo apt-get upgrade appears to fetch a few updates.

apt-get install -f returns **"0 upgraded, 0 newly installed, 0 to remove"**

amd apt-get autoremove removes 74MB of unnecessary files.

Then booted with "I" for "ignore errors."

It booted after 10 minutes and granted RW access, but could not open Firefox or DropBox.  Mounting an external HD failed, as did inserting a blank DVD - **"automount failed, unable to create temporary directory."  **As such I still have no means of backing up my most recent data.

---

