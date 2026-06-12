---
title: "PyNeighborhood. Possible to autorun?"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Kosimo on 2007-08-30
Following this guide: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)
I just installed PyNeighborhood in Xubuntu and is running really fine.
But now, I have two important things I must do

It is possible to autorun PyNeighborhood on each login? Does it always need to use sudo mode?

I need to create a "non privileged" user for a school and this user should be able to browse to the folder network mounted by PyNeighborhood and it should it be mounted automatically...
Do I'm asking too much maybe?

Help!!

---

### Post by PaganBlasphemy on 2008-01-31
I think this ability is in the old version of pyNeighborhood called LinNeighborhood, but I didn't see the option to do so anywhere in pyNeighborhood and the shares certainly don't seem to stay mounted after a reboot, do they!

This is the PITA way to do it:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

I haven't figured out where to save the changes to persist between reboots, but I did find a little setup guide here: [http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html)

LinNeighborhood isn't hard to use, and once you enter all of the settings in the Prefs and save them, it automatically fills the resulting dialogs with all of the correct info.  I wrote a little howto regarding using LinNeighborhood on my blog:

> sudo aptitude install linneighborhood

Then, right click on the Applications toolbar, hit Edit Menus, and create a shortcut for LinNeighborhood. I placed mine under System Tools. Note that the Create Launcher dialog may spawn behind your active window, so click on it from the toolbar and use this as the command:

gksudo LinNeighborhood

I put LinNeighborhood in for the name and allowed the default icon. Now that it is installed and we have access to our network shares, just a little work with LinNeighborhood. First thing I did was set the Preferences as so:

Under the Scan tab:

    * enter my workgroup (actually the first 15 characters of our domain name)
    * check off all of the &#8217;scan as user&#8217; buttons
    * check &#8216;use group name on browse&#8217;
    * check &#8216;use group name on mount&#8217;,
    * &#8216;initial browse on startup&#8217;.

Under the Miscellaneous tab:

    * Enter the default user with the credentials used to access the shares
    * check &#8217;save password&#8217;
    * check &#8216;Use RootMountDir/machine/share as default mount point&#8217; and change the location (in my case) to /home/garrett/mnt/
    * check &#8216;Replace spaces with underscores&#8217;
    * check &#8216;Memorize Mount Shares / Remount on next Startup&#8217;.
    * Hit Save
    * Hit Close

&#8230;and we&#8217;re (finally) ready to start actually adding shares&#8230;

I restarted LinNeighborhood, and drilled down from the Workgroup entry to the shares I wanted to access. Each time I was challaned for credentials, an &#8216;Insert User&#8217; dialog box pops up with the default user information ready to go, so I just hit OK.

Arriving at my destination, I want to add the &#8216;Mail&#8217; share. Right click on the share and hit &#8216;mount&#8217;. With the settings entered into the Preferences, most of this dialog box is already filled out:

Service, Mount Point, SMB User, SMB Password and the check boxes can all be left as default. The file and dir mode can be left as default. The only thing that I changed was that I made the shares accessible by my user account by selecting my UID and GID off the selection box (both near the bottom). Hit &#8216;Mount&#8217;, and the share should appear at the bottom of the LinNeighborhood window under &#8216;Resources&#8217;.

Now, any time you want to access this share, you simply navigate with your software to /homedirectory/user/mount/server/share (in my case /home/garrett/mnt/pcsserver/mail/). Easy, but not quite effortless&#8230;

From: [http://www.garrettsocling.com/2008/01/29/ubuntu-710/](http://www.garrettsocling.com/2008/01/29/ubuntu-710/)

I hope someone picks up with development of pyNeighborhood (and ideally integrates it more directly into Ubuntu) as 'connect to server' and bookmarks just don't cut it, LinNeighborhood is clunky and editing fstab is absurdly complicated for grandma to figure out.

---

