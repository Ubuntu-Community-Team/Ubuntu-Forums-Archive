---
title: "Problems creating users"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by soupface on 2005-05-03
During the create-a-user section of the installation process, I had problems entering a password (there was no feedback as to whether or not my input had been received or not). No matter how many times I entered a password, I was asked, again, to create another user.

Frustrated, I hit ESC and continued with the next step in the installation. Upon reboot, I was told that I had not specified a password. I entered one for the root user, this time receiving proper feedback (asterisks appeared in the entry field). Again, when asked for a password, it looped, and, again, I hit ESC and continued the installation process.

At the terminal, I entered startx and used the Add User UI to create a new user. I then logged-out and rebooted. When the login screen came up, I entered the user name and password. When GNOME began too boot, it gave an error stating that it could not create a .gnome2 directory in /home/user. Switching to tty1 and logging-in as root, I saw that the /home/user folder was owned by root and permissions were such that no one else could write to it.

When I attempted, as root, to chown the /home/user directory, the terminal spits out "operation not permitted." When I attempted to adduser, the process chokes at chown (again, "operation not permitted") and does not create a new user.

What can I do?

---

### Post by soupface on 2005-05-04
I realised that the /home partition was FAT32, which does not allow for the same permission structure as ext3. Re-formatting the partition as ext3 has solved the problem.

My problem was caused by having mounted a FAT partition at /home. The Ubuntu installer assumes that the partition on which it's to create user accounts (/home) will allow reading, writing, and Unix-style file permissions. This assumption works fine if the /home partition happens to be a Unix-kind of filesystem (ext, ReiserFS), but not for FAT.

As I understand it, a FAT partition needs to be mounted with a special mask that allows all processes and users to read and write to it (see [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) ). This does not happen on its own and is not done by the Ubuntu installer. Worse still, the installer hides any sort of semi-useful errors during the user creation process. It wants to create directories in /home for each user, but because of the way FAT partitions are mounted initially it can't, and the entire create-a-user process is aborted.

I solved this problem by avoiding it: I created an ext3 partition at /home and then another FAT partition elsewhere (mounted at /gobe) on which to store files to share between Ubuntu and Windows XP. In order to make things simpler, and since I had not really copied anything useful onto my computer at that point, I simply began the Ubuntu install process again, from scratch.

*I added a detailed description of what (I guess) had caused the problem, in case anyone else with a similar problem should stumble across this thread in the future.

---

### Post by martinitheace on 2005-05-19
I'm having the same problem except my /home is on the same ext3 partition as /

I didn't know how to add a user from the terminal so I'm going to give that a try now.

[edit] Tried to create a user but it failed at the home folder creation so, as root, I created the folder, copied the default .bash_profile and .bashrc files then tried to chown it but I got the 'Operation Not Permitted' error.. Any ideas?

---

