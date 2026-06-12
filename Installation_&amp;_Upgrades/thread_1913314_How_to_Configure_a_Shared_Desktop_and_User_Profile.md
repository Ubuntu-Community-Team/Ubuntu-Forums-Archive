---
title: "How to Configure a Shared Desktop and User Profile between Windows and Linux"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by Wug on 2012-01-22
[SIZE="4"][THREAD UNDER CONSTRUCTION][/SIZE]

I have been dual booting windows and ubuntu for some time.  When I got it set up, I was content just to be able to access the data between the two OSs. Recently, however, I decided to update (I don't do cumulative updates because they break things in bizarre ways, so I was about 4 versions out of date) and decided it would be cool to shoot for a shared desktop.

I managed to make it work, and made a ton of mistakes during the process, and even figured out what could even be considered The Right Way to set it up.  It wasn't easy, and while most of the users here would have no trouble with the linux side of the requirements, lots of you who are less familiar with windows would struggle with it, so I decided to write this post.

If I had to do it again, I would put Linux / on the 100GB EXT4, and Linux /home on the 800GB EXT3, but keep everything else the same. You might think 100GB is a little large, but resizing partitions later is a pain, so make it larger than you think it needs to be. I didn't do it quite this way, so I WILL BE DETAILING HOW I WOULD HAVE DONE IT IF I HAD TO DO IT AGAIN.

When you're done following this guide, you will have the following configuration:
[LIST]
[*] a windows xp, vista, or 7 installation
[*] a linux (ubuntu?) installation
[*] a shared desktop
[*] an emergency windows admin account
[*] at least 3 partitions
[/LIST]

Here is what I had to do to make it work:

[LIST=1]
[*] [SIZE="4"]READ ALL STEPS BEFORE CONTINUING[/SIZE]
This step is really really important.  I ask some things that may seem arbitrary or nonsensical, but if you read the whole thing, you will understand that "later its important that it be set up exactly this way". So, read all of the steps before continuing.  If you jump into this and dont have any idea what you're in for, you could potentially make things very difficult for yourself.  I made a lot of mistakes as I was doing this, there were times when windows would not let me login to any of my accounts.  If you follow the directions properly, you shouldnt have any issues, but if you go charging on ahead and do something wrong, it will probably break and it will be your own fault.  You have been warned.  Also, take a look at the troubleshooting section to get an idea of what might go wrong.  Please also note that I've compiled a list of download links for all of the required software at the bottom.


[*] [SIZE="4"]Make a Backup of the Registry[/SIZE]
We will be changing the HKLM branch of the registry (HKEY_Local_Machine) for those who are not familiar with the windows registry.  If you want, you can back up the whole thing, though that might take a long time.  We're only changing keys in one place so you can choose only to back up that one branch if you wish.  To do this, open the registry editor, and in the tree on the left, right click the branch you wish to backup and choose export.  Save it somewhere safe and make a redundant backup, just in case.

```
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList
```
The registry key that is being modified, referred to from here on as PROFILELIST.  We will be looking at this key a lot.


[IMG]http://wug.me/shareddesktoptut/export.png[/IMG]
The export option on the PROFILELIST registry key


[*] [SIZE="4"]Burn any necessary recovery CDs[/SIZE]
Things can go wrong sometimes, having the recovery CDs can save hours of painstaking recovery work and gigabytes of important data.  I recommend having your windows install CD handy (if you still have it) which can be used to patch the registry and perform other emergency diagnostic tasks, and an install CD for the version of linux that you plan to be using in the end, as well as one for the version you currently have installed (if they're not the same version). You can use bootable USB sticks if you wish.


[*] [SIZE="4"]Change a few Windows Settings[/SIZE]
UAC may hinder you during this process, you may wish to temporarily disable it.  You will want to be able to see hidden and system files and folders from windows, you should enable this.
To disable UAC: open the control panel, search for "UAC", open UAC settings, disable
To enable viewing of hidden/system files and folders, open the control panel, search for and open "folder options", jump to the view tab, and in the list, select the "show hidden files and folders" bubble and uncheck "hide protected operating system files"


[IMG]http://wug.me/shareddesktoptut/settings.png[/IMG]
Folder Options and Disabling UAC


[*] [SIZE="4"]Install the Required Software[/SIZE]
Ubuntu does not like to install on NTFS partitions, though it can read them.  Windows, by default, cannot even read EXT partitions.  We need to find some sort of middle ground that both OSs will allow.  You will need a windows program called EXT2FSD, which provides a filesystem driver that supports EXT- 2, 3, and 4 partitions.  Download and install.


[*][SIZE=4]**Checkpoint:** About to begin[/SIZE]
You are at the point of no return.  After this point, it becomes significantly less trivial to undo changes that this guide requires.  If you damage your environment in these later steps, you may have no choice except a full reinstall in order to return to normal.  You may lose data.  You may lose time.  You may cry yourself to sleep for weeks, thinking of the horror of what you have done (probably not though). This procedure is highly experimental.  Be advised that although it works correctly for me, it may not work as well for others, and that factors I have not isolated may bring about unexpected behavior in future steps.


[*] [SIZE="4"]Modify Partitions (Maybe?)[/SIZE]
At absolute minimum, setting up your system in this way requires a MINIMUM of one NTFS partition (for the windows system), a MINIMUM of one EXT3 (it is imperative that it be EXT3) partition (for shared data), and a MINIMUM of one other linux system partition (EXT4 preferred, for the linux system).  You can have other partitions for mounting /boot and whatever else to if you feel like, but they are optional, and you must have a minimum of these partitions.


[LIST]
[*] [SIZE=3]Backup[/SIZE]
It is ALWAYS a good idea to back up your data before doing any work with partitions.  There exists the risk of accidental stupidity, in which you erase a partition you wanted to keep, or critical failure, in which your partition editor screws up somehow and destroys data.  Always make backups before doing partition work.  It is also a very good idea to do partition work while connected to AC power, so your battery does not cut out during the work, which can leave the drive in a very damaged and sometimes irrecoverable state.  If its thundering out, put this aside and do something else.  (That being said, I didn't make any backups :P DO WHAT I SAY NOT WHAT I DO)  


[*] [SIZE=3]Windows[/SIZE]
Using your best judgement based on the size and content of your drives, choose the location and size of the Windows System partition. This partition can be on any drive, must be NTFS and should be large enough to install a bunch of software on.  If you already have one, it is possible to reuse it and/or resize it to fit.  Everything that should be stored here is windows system or software. Windows 7 takes up something like 11GB, and some software packages get pretty huge.  I have a lot of software on my system, so my partition is about 65/100GB full. (Even though I install games to a different partition)


[*] [SIZE=3]Linux[/SIZE]
Using your best judgement based on the size and content of your drives, choose the location and size of the Linux System partition.  This partition can be on any drive, and can be any partition type that linux supports installing to.  I recommend the latest, EXT4.  It should be large enough to store the linux system and software.  The core of an ubuntu installation is usually a few GB, plus any space you want to leave for software.  If you want to split this up as multiple partitions, thats fine.  While I'm sure its possible to reuse an existing installation, changing the mount points to the new partitions, I did not do that myself, I just reinstalled.  Ill try to find a guide that details how to do it.


[*] [SIZE=3]Shared[/SIZE]
Using your best judgement based on the size and content of your drives, choose the location and size of the Shared partition.  This partition can be on any drive but MUST BE EXT3, and should be large enough to store any documents and user files from both OSs, so it should be as large as possible.  It might be a good idea to backup any other data that may still be on the disk, and remove any remaining partitions so this one can use the remainder of the space.


[*] [SIZE=3]Swap[/SIZE]
Depending on how much ram you have, you might have a need for swap space.  Various rules exist for determining how much swap space you need.  In my opinion, you should have at least enough RAM and SWAP together to make 4GB.  If you have more than 4GB of ram, you dont really need swap, but it never hurts. This partition can be on any drive, but if you have multiple drives, it may be a good idea to put the swap partition on a different drive than the linux system partition.

Here is a table of how much swap is generally a good idea for some amount of ram:
[table]


[*] [SIZE=3]Others[/SIZE]
If you see fit to create other partitions for other purposes, do so.


[*] [SIZE=3]Organize[/SIZE]
Give each of the partitions a clear, unambiguous drive label so you can identify them with no effort.  Things like "WindowsSystem", "LinuxSystem", "SharedProfiles", "BulkStorage", and other such blunt and obvious names are preferable to things like "MyLaptop" and "MyData".  It is important that you be able to distinguish between what is what to prevent silly mistakes which could have dire consequences.[/LIST]


[IMG]https://www.google.com/intl/en_com/images/srpr/logo3w.png[/IMG]
Gparted Overview of Partitions (Google Logo until I actually take the picture.  I love you google!)


[*] [SIZE=4]Check if it Still Works[/SIZE]
Boot into all of your OSs and make sure they still function.  Under some circumstances, you might have to use the linux recovery CD to reinstall grub because windows has a bad habit of breaking it.  Please also note that when booting after modifying partitions, most OSs will automatically do disk checks to ensure drive integrity, this is normal and to be expected.  It helps to boot into windows last because the next step involves being in windows.


[*] [SIZE=4]**Checkpoint:** Partitions are done[/SIZE]
Repartitioning sometimes takes hours, even days for larger drives.  Might be a good time to go to sleep, or grab some food.  By the time you get here, you should have set up your partitions correctly.  The contents of the partitions is totally up in the air.  You may have decided to keep your existing windows and linux environments, or you may have done a complete reinstall or are starting from scratch.  But the partitions are set up.  You will not need to make any changes to partitions from this point on.


[*] [SIZE="4"]Set up windows[/SIZE]
If your windows partition does not have windows installed on it, this would be the time to do that.  Dont create any accounts other than the Admin account it creates automatically, its easier to handle that later.  Don't install any unnecessary software either, as it sometimes creates registry entried with hardcoded path names, and often has to be reinstalled after changing the profile drives.  The obvious exception is EXT2FSD.  If you're using a new installation of windows, double check steps 2, 3, and 4 to make sure everything is set up and ready to go.


[*] [SIZE="4"]Set up linux accounts and Change Mount Points[/SIZE]
If you are using a preexisting linux installation:


[LIST=1][*]Copy existing profile folders to the new partition, putting them in the root (remember, the partition is going to be mounted as /home)


[*] Change Mount Point for /home. ??? I am not sure how to do this.  Like I said, I used a fresh installation when I did it.[/LIST]


If you are installing a fresh install of linux:


[LIST=1][*] Install Linux.  Use the drive you designated as the system drive as the mount point for / and the drive you designated as the Shared drive as the mount point for /home.  Proceed through the rest of the installation.  After it has complete, do standard installation verification to ensure that everything isnt all fubar.


[*] Migrate Old Data.  If you want to create any additional accounts and/or restore data from a backup of an old installation, this is the time to do it.  Create the accounts from your own account (they should be created with their profiles in the shared partition) and populate them with any backed up data from old accounts, as you see fit.[/LIST]


[*] [SIZE=4]**Checkpoint:** Partitions, OSs are installed[/SIZE]
The partitions at this point are not changing.  You should now have both windows and linux installed and functional (albiet still seperate) on their respective partitions.  The shared partition is currently used only as the linux installations' /home.  Might be time to get another snack


[*] [SIZE="4"]Create the Windows Emergency Admin Account[/SIZE]
Boot into windows.  Log in as the administrator account.  If this account is not a general use account, it will serve as the Emergency Admin Account.  If it is an account you use regularly, open the control panel and create a new account.  Set the account as an administrator and choose a strong password.  When you're done, log out, and log into the new account.  There are some issues later during the process which can prevent logins to accounts that have been moved off of the drive, so we will be leaving this account where it is so we can access it in the event of a mistake or emergency.


[*] [SIZE="4"]Mount the Shared Partition for Temporary Use[/SIZE]
If you are not already logged in as your Emergency Admin Account, do so.  Open the EXT2FSD volume manager.  If UAC propmts, allow it.  You should now be able to see all of the system partitions along with their drive labels. Locate the shared partition (The interface does not display volume labels so you will need to pick it based on size and type.), right click, and choose ext2 management.  Fill out the options as specified by the picture and apply all changes.  Open "Computer" or "My Computer" and you should see the drive in the list.


[IMG]http://wug.me/shareddesktoptut/mounttemp.png[/IMG]
Configure the drive according to this picture


[*] [SIZE="4"]Duplicate your Windows Profiles[/SIZE]
Open the system drive (usually C) and open "Users" (on vista or 7) or "Documents and Settings" (on XP).  Subfolders of this folder are user profile folders.  Copy all of them (including hidden ones, which represent accounts used by the windows system and system services) EXCEPT the Emergency Admin Account's user profile to the root of the new EXT3 drive you mounted (remember that the Emergency Admin Account is staying on the system drive).  If you want to merge any accounts to give shared desktops, move the contents of the windows profile folders into the linux profile folders, or rename the windows folders and then copy them (prompting a merge).  Merge the contents as necessary.  Keep in mind that you may have to rename a folder to merge it with the linux equivalent profile folder, and make a note of each folder that you renamed, and what it was and is now called.


[IMG]http://wug.me/shareddesktoptut/profmove.png[/IMG]
How and where to move the files


[*] [SIZE=4]**Checkpoint:** About to Migrate the Profiles[/SIZE]
The profile migration was, in my experience, the most obnoxious step.  There are about a million things that can go wrong, and most of them would be (for someone not good with the windows registry) unrecoverable.  If anything goes wrong, check the troubleshooting steps, where I reported all of the issues I had during the migration and how I solved them.


[*] [SIZE="4"]Restart windows in safe mode[/SIZE]
Restart the computer.  Select the windows installation in grub.  After hitting enter, press and hold F8 to bring up the windows boot options.  Boot into safe mode.  After windows has loaded, login to the Emergency Admin Account.


[*] [SIZE="4"]Assign the Final Volume Settings and Migrate the Profiles[/SIZE]
Decide on what you want the final volume letter of the shared profile partition to be.  For the purposes of demonstration, I'll choose drive X.


It is possible that you may have already moved your profile folder to a different drive. If you intend to have the old profiles and the new ones have DIFFERENT drive letters:


[LIST=1][*] [SIZE=3]Configure the Partition with a Fixed Mount Point[/SIZE]
Open the EXT2FSD volume manager. Find the shared partition in the list. If it is already mounted, remove its drive letter and unmount it.  Right click it and select ext2 management.  Fill out its options as specified in the picture (using your choice of drive letter).  Apply all settings.  EXT2FSD will warn that you need to reboot to apply the settings.


[*] [SIZE=3]Reboot into Safe Mode Again to Apply Fixed Mount Point[/SIZE]
Follow the steps above to restart into safe mode again.  Without opening EXT2FSD, open Computer and verify that the drive is present, under the correct drive letter.  If it is, the drive should exist and you should be able to create files inside it.  If this is true, then the fixed mountpoint applied correctly.


[*] [SIZE=3]Migrate the Profiles to the new Partition[/SIZE]
Open the registry editor.  Navigate to the PROFILELIST key we defined earlier.  Under this key, change the values "Default", "ProfilesDirectory", and "Public" to the new location. These values control the location of new profiles and default settings, IE any profile created will be located in the folder it specifies.  Change the value "ProfilesDirectory" to "X:\" (substituting your selected drive letter for X).  Notice that the data in "Default" and "Public" were subdirectories of the data in "ProfilesDirectory", and update them accordingly.  Now expand the PROFILELIST key and look at each of its subkeys.  They should each have a name of the following format or similar: 
```
S-1-5-21-3623811015-3361044348-30300820-1013
```
These are the unique IDs of the user accounts.  They may not all look exactly like this, some of them will be shorter (those are typically system accounts).  Expand each of these keys and look for a value called "ProfileImagePath".  This value contains the location of the user's profile folder.  Change the data for each value to the new location, keeping in mind that you may have had to rename some of the profile folders to conform with linux's expectations.  Remember NOT to change the location of the Emergency Admin Account.[/LIST]


If the intended drive letter of the new shared drive is **THE SAME** as the one the profiles currently exist on:


[LIST=1][*] [SIZE=3]Make sure the Emergency Admin Account's profile is on the system drive[/SIZE]
If you knew enough about windows to change the profile locations before now and have moved them to another partition already, then you probably know enough about what you're doing for me to leave out the gory details.  Move the Emergency Admin's profile back to the system drive.  You can do this entirely from safe mode without having to log off.  Copy the profile folder to the system drive.  Navigate to the registry key PROFILELIST, find the subkey for the account, and change the "ProfileImagePath" value to the new location.  When you're done, logout and login again to make sure the migration occurred successfully.


[*] [SIZE=3]Drive Letter Musical Chairs[/SIZE]
Open the windows disk manager service (press Win+R and run "diskmgmt.msc").  Find the drive letter containing the volume that is currently holding the windows user profiles, right click, change drive letter, pick a new drive letter, and apply.  Open EXT2FSD, find the shared profile drive, remove its drive letter if it has one.  Then right click, choose ext2 management, and fill in the options as specified in the picture.  Apply and close.


[*] [SIZE=3]Registry Profile Location Changes[/SIZE]
You may have to fix some of the profile paths if you had to rename any of them.  Use the the instructions in step 18.A.3 to do so.[/LIST]


[IMG]http://wug.me/shareddesktoptut/drivex.png[/IMG]
The drive, as it appears in my computer


[IMG]http://wug.me/shareddesktoptut/mountfixed.png[/IMG]
The configuration of the drive's fixed mount point


[*] [SIZE="4"]Tentatively Test to see if Everything is Correct[/SIZE]
Reboot into safe mode again with the instructions in step 17.  Try to login to any account that is not the Emergency Admin Account.  If the login succeeds, try to make a file on your desktop.  Open My Computer and verify that the file is indeed being created in the migrated profile folder.  If windows is using the correct folder, reading and writing access is enabled, and no unusual behavior is detected, proceed, otherwise, visit the troubleshooting steps.


[*] [SIZE="4"]Test Windows more Bluntly[/SIZE]
Reboot windows normally.  Try logging into all of the accounts, try reading and writing files to make sure that they are being created in the correct places.  Check the troubleshooting steps to resolve any unusual behavior.


[*] [SIZE="4"]Configure Linux to use the Same Profile Folders[/SIZE]
One thing that I have not tried is creating an account on linux if an existing windows account already exists.  I know windows will append something to the foldername to prevent possible issues with dual ownership of an account folder.  It is possible that linux may behave this way, or it may simply delete the contents of the folder before proceeding.  PROCEDE WITH CAUTION AND MAKE BACKUPS AS NECESSARY! Any accounts that already exist should be merged already, as was handled in step 15.


[*] [SIZE=4]**Checkpoint:** Officially Done[/SIZE]
At this point, you have configured the two operating systems to use a shared data partition, as well as a shared desktop, documents folder, and other things.  You have done what you set out to do.


[*] [SIZE="4"]Creating accounts in the future[/SIZE]
If you want to create new accounts in the future that should also be shared between windows and linux, it would probably be better to create the linux account first, then create the windows account.  Before logging in to the account, use the instructions in step 18.A.3 to change the location of the users profile folder to the location of the existing linux profile folder.
[/list]

[SIZE=4]**TROUBLESHOOTING**[/SIZE]
[LIST]
[*] Why does the shared partition have to be EXT3, why cant I use EXT2/EXT4
You could probably use EXT2.  However, EXT2FSD does not have write support for EXT4 partitions, and I think windows would "be offended" (read: not work) if it could not write to the users profile.
[*] I cant login to any account on windows outside of safe mode except the emergency admin account.  In safe mode I can login, but the profile doesnt load.
The profile folder can't be found.  Make sure you specified the right drive letter in the registry and in EXT2FSD.  Also make sure that you chose a fixed mount point, if you did not, the drive will not be mounted until you open EXT2FSD, which will prevent windows from getting profile information from the drive.
[*] I fixed the problem in the previous bullet, but still cant login.
If the login fails, windows will rename some of the settings in the registry and attempt to restore the defaults.  You will have to undo this, preferably in safe mode with the Emergency Admin Account.  Open regedit and find key PROFILELIST.  You will notice that some of the subkeys have been renamed to <oldkeyname>.bak and new, mostly blank entries created.  Delete the new keys and remove .bak from the names of the old ones.  F2 will rename a selected key.
[*] I have done everything right, but I cant seem to run some programs.
UAC does not seem to agree with EXT file systems, you may have to disable it.
[*] <insert program here> does not work properly after doing this.
You might have to reinstall it.  Like I said somewhere else in the guide, some programs store paths in the registry and do not use relative paths, and if they attempt to run using their absolute path which no longer exists, they may encounter issues.
[*] Something went wrong when I was editing the partitions and I can't find any of my data.
I hope you made a backup.  If you didn't, then you're an idiot.  You might have some success if you use a livecd or liveusb, open gparted, and attempt data recovery.  However, if you did not make a backup and lost data, you directly disregarded one of the steps and it's your own fault.
[*] I did this and want to undo it, how would I do that?
Make a ton of backups, and use steps 15 through 18 to move your profiles back to the primary OS partition.  Alternatively, you could reinstall the OSs.
[*] Are there security issues with this?
Yes, potentially.  If you are the only user of your computer there should be little issue, however, EXT2FSD disregards EXT permissions (including the executable bit) so it will be difficult to prevent users from tampering with each others data from the windows side.  If this will be a problem, you should not follow these steps.
[*] Can I use symlinks and other links?
Yes, but you should make them through linux.  I do believe that windows will recognize links as reparsepoints and handle them correctly in VISTA AND 7 ONLY, XP handles them weirdly.  If you're using XP, be very careful when dealing with them because they are not treated specially.  I am not sure that windows linking utilities can handle creating links on ext filesystems through EXT2FSD, but they should still be able to read them.
[*] Other questions or comments.
Rather than sending me a PM, as I use this forum rather infrequently, you should post a reply.  You can still PM me, I just probably wont reply for 2 months.  If you post a reply though, someone else will read it and help you sooner.[/LIST]


[SIZE=4]DOWNLOADS[/SIZE]
[EXT2FSD 0.51 SourceForge Project]("http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.51/")
[Download Ubuntu]("http://www.ubuntu.com/download/ubuntu/download")
[Offline Registry Editor Utility (Linux LiveCD)]("http://pogostick.net/~pnh/ntpasswd/")


[SIZE=4]RELEVANT THREADS[/SIZE]
[How much swap space do you need?](https://help.ubuntu.com/community/SwapFaq)
[How do I move a static mount point?](https://help.ubuntu.com/community/MoveMountpointHowto)


[SIZE=4]ADDITIONAL NOTES[/SIZE]
I did this with Ubuntu 11.10 and Windows 7 x64 SP1.  I have used EXT2FSD on 32 bit XP and and 32 bit Vista as well, so I can attest to its functionality in both of these places.
I am using EXT2FSD version 0.50, slightly more out of date than the current version.  I am led to believe that while 0.50 does not support writing to EXT4 volumes, 0.51 does.  A word of caution however, data corruption has been reported for EXT4 volumes under some circumstances.


EDIT SECTION
you know, you could do this with links too, but thats not really The Right Way to do it.
added download section, which I said I would but didnt.
I'll be a video tutorial later.

---

