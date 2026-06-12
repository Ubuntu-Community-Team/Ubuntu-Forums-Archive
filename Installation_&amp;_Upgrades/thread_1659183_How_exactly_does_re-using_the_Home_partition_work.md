---
title: "How exactly does re-using the Home partition work?"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by burpootus on 2011-01-03
Title pretty much says it all. I did my current install of Ubuntu on a 500 gig drive, reserving most for /Home. I now have many gigs of data in /Home. So, let's say I want to install Mint and I do the install without formatting /Home to preserve the data. How do I link my user's folder structure currently in /Home to the new Mint install? If I create a new user with the same name, won't it just create a new set of default folders? Exactly how does the mechanics of preserving the /Home partition work? Thanks for your help.

---

### Post by kansasnoob on 2011-01-03
I'm personally a great proponent of using a separate /home partition just because it makes "reinstalling" due to update/upgrade failure considerably easier. And I assume you know that, if your existing OS consists of /, /home, and SWAP, you **must not** click on format when selecting a pre-existing /home for a new/fresh install or reinstall. Have I confused you yet :confused:

On to more confusion!!!!!!! Sharing a /home between different distros gets downright funky! Obviously things like the .gconf and .gnome2 are going to be different, and the Ubuntu /home won't have a .linuxmint, so sharing  a /home without a different username just won't work! 

And sharing /home between different desktops (like Gnome and LXDE) won't work w/o different usernames. It gets even worse if you have a  mix of debian based and rpm based distros. Because of that I no longer use a separate /home:

[ATTACH]180043[/ATTACH]

Most partitions are labeled but regardless I can transfer data from one OS to another quite easily, but certain things, like evolution files, are best transferred with no OS mounted so I tend to do that with a Live CD/USB. (Puppy is dandy for that).

I do have 4 separate data partitions that are symlinked to each OS's /home, but that only works with debian based distros. That is, if I symlink those to Fedora or PCLinuxOS the permissions change and I can no longer access them with Ubuntu.

A lot of that is discussed here:

[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

---

### Post by burpootus on 2011-01-05
I was afraid it wasn't going to be easy.

---

### Post by C.S.Cameron on 2011-01-05
The /home from Ubuntu should be fairly compatible with the one from Mint.
After a new install you will have to point the way to home in fstab.

---

### Post by wkulecz on 2011-01-05
> I was afraid it wasn't going to be easy.

It is easy for your personal data files, but what breaks is all the crap applications setup in /home/USERNAME/.app directories.  You can pretty much count on breakage and weird behavour here after upgrades for many applications.

I keep a seperate "archive" drive for my data and consider anything in /home to be expendable, so I don't see a seperate home partition as particularly useful or helpful.  I can access the archive from any of my multiboots that each have their own /home so the apps don't step on each other.



I backup my "archive" drive nightly (using rsync in a cron job), the system (including /home) gets backed up weekly just to avoid the hassle of reinstalling and setting up everything again should a drive fail.

---

### Post by srs5694 on 2011-01-05
> **kansasnoob said:**
> And sharing /home between different desktops (like Gnome and LXDE) won't work w/o different usernames.

Actually, that's irrelevant. Different desktop environments almost certainly use different configuration files, so if Distribution A uses Desktop A and Distribution B uses Desktop B, you won't have cross-distribution issues with the desktops *unless* you install the non-standard desktop on one or both distributions, in which case their configuration files might conflict.

> It gets even worse if you have a  mix of debian based and rpm based distros.

This isn't really the issue; package files don't go in home directories, except possibly as temporary holding areas if you download software for manual installation. There *might* be an effect of Debian-based distributions being more consistent between themselves in where they place icons and whatnot, but I wouldn't count on that.

[quote=burpootus]I was afraid it wasn't going to be easy. 	[/quote]

Don't get discouraged. It's really not that hard.

For best safety, all you need is separate home directories in your /home partition. That is, if your current home directory is /home/burpootus, you'd create a new home directory for your second installation -- say, /home/burpootus1. This can be done in any number of ways, the easiest of which is to use a different username for each installation. You can, however, use the same username so long as you set up one (or both) to use a home directory name that's not exactly the same as the username. I'm not that familiar with Ubuntu's GUI account management tools, and I don't recall exactly what the installer does, so I can only advise you on the use of text-mode utilities or hand-editing files. I'd do this:


[list=1]
[*]Install your second distribution and use a different username.
[*]Test your second distribution.
[*]Reboot into your first distribution.
[*]Mount the second distribution's root (/) directory and open its /etc/passwd, /etc/shadow, and /etc/group files in a text editor. (You'll need root access, so use sudo.)
[*]Change the username you used for installation to your preferred username in all three files (some distributions won't use it in /etc/group), but be sure *not* to change the home directory reference (such as /home/burpootus1).
[*]Shut down and reboot into the second distribution.
[*]Test the account. You should be able to log in using your preferred username, but you should find you're still using your new home directory.
[/list]


(This task could be done a bit more easily and safely using the usermod utility if Ubuntu supported direct root logins or if you have multiple accounts with sudo access, but Ubuntu's choice to rely on sudo makes this approach less practical. You can modify Ubuntu to enable regular direct root access, but doing so for this one task could produce problems down the road.)

If the distributions use the same UID-assignment policies, chances are you'll be the owner of the files in both home directories in both distributions. This is fine and makes using the files convenient. You can create one or more symbolic links that point to the old home directory or to individual files or subdirectories in it, as you prefer, to simplify access. If the UIDs don't match across distributions, you'll have to correct that, which is easily done.

---

