---
title: "Installing ubuntu on / mount without deleting /home mount"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by BigBaka on 2012-06-23
Dear all,

For reasons I won't go into I'm wanting to re-install 12.04 32 bit as a stand alone system on a hard drive that is already partitioned with a separate boot partition (/boot) file system (/) and home partition (/home). Is there a way I can just re-install the ubuntu operating system on the / partition while not erasing all my files on the /home partition?

Thanks
BB

---

### Post by nipunshakya on 2012-06-24
Its good if you go for a clean install rather than not touching the /home thing... this is because if you have programs installed in this version, it might now work properly after a new installation...
I would backup my data first and then go for a clean installation of ubuntu.
If you dont want a seperate /home, during installation, just allocate / partition for your ubuntu installation and leave the rest as unallocated space... then after installation is done, run Gparted and format the unallocated space as any format as u want...

Goodluck

---

### Post by BigBaka on 2012-06-24
Thanks,

Just to clarify, I wanted to re-install the ubuntu system as well as all the programs / applications as well. I just didn't want to have to go through the process of backuping up and restoring all my files and folders as well by to not touching the user files and folders which are located on the /home mount which is on a seperate partition. I just can't figure out how to do that when reinstalling by booting from the installation cd. What should I select from the three installation options

- Install ubuntu 12.04 LTS alonside Ubuntu 12.04 LTS
- Erase Ubuntu 12.04 LTS and reinstall
- Something else

I was thinking to pick the 2nd option but got scared because of the warning that says warning This will delete all your ubuntu 12.04 LTS programs, documents, photos, music and any other files.

---

### Post by nipunshakya on 2012-06-24
well, if you don't want any backup, you can go with the second option.... but i suggest going with third option, and then at the partition table, select the partition with 'mount point' as / and then select the bootloader to be installed at /dev/sda and then you are good to go..

---

### Post by BigBaka on 2012-06-24
So the 2nd option won't delete all my user files on the /home partition? Why do you prefer option 3 over option 2? Would option 3 require full backup of files and folders on the /home partition?

---

### Post by nipunshakya on 2012-06-24
Go either any way, option 2 or 3, the programs installed in /home in your current installation wont work out on your next fresh installation. Honestly, i haven't used option 2 till now coz option 3 will give me freedom to rearrange my partitions as i wish to.. 

on top, unless you have written some scripts to make your applications of current /home to work in your future installation, the installed programs on this current installation won't work.

---

### Post by Bucky Ball on 2012-06-24
At the partitioning section of the install choose 'Something Else'. Install to the existing / and make sure /home and /swap are not ticked to format. These will be used automatically. 

Once installed the original contents of the original user should still be in /home/olduser along with a directory for the new user; /home/newuser. Transfer personal data from /home/olduser then delete /home/olduser directory. ;)

I have three Ubuntu installs all using the same /home partition, each install with a /home/user directory in there. I can access the directories of all other installs from any other install!

Good luck. There is no problem with using the existing /home.

(PS: Programs and settings in the original /home/olduser are hidden files, anyhow. They play absolutely no part in your session with /newuser as you are booted into /newuser and a totally different install which is looking in /newuser for info and settings, not /olduser.)

---

### Post by BigBaka on 2012-06-24
Thanks Bucky Ball,

What if I wanted to keep the same user name (work) and keep all the hidden settings folders etc located in the root directory of "~/work"? would that work so that I don't have to copy, for example all my thunderbird settings across to a new uer, and instead the new software installs could just pick up the old settings in the old user folder?

---

### Post by Bucky Ball on 2012-06-24
Well ...

I was using 10.10 but had 10.04 installed also (and 11.04). As 10.10 reached EOL I swapped to the 10.04 as my main squeeze.

In /home/10.04user I deleted all directories; /Documents, /Downloads, /Video, etc, and replaced them with symlinks to the directories in /home/10.10user. 

I then simply moved the appropriate files to the Thunderbird folder in the 10.04 install, pointed my Zotero to use the database in the /home/10.10user directory and that's it. Nothing much has changed apart from the release number!

To move Thunderbird data simply find /home/olduser/.thunderbird folder and copy the profile (ends in .default) and the profile.ini file over to /home/newuser/.thunderbird.

.thunderbird is a hidden directory so you need to hit control+h to see it in the /home/user directory. ;)

---

### Post by darkod on 2012-06-24
Bucky, when you say /home and swap will be used automatically, I hope you don't mean totally automatically.

You still need to select the /home partition, click the Change button below, and change the Use As from Do not use, into the filesystem you have on it (for example ext4), and change the mount point to /home. Otherwise, it will not be used.

To the OP:
The second option you mention, Erase 12.04, was introduced in the latest 12.04 and I haven't used it, but I wouldn't trust any option that says Erase. I would stay clear of it, since you DO want to keep your data and settings in /home. I even think I saw one thread here with this exact situation, separate /home, and when the Erase option was used the data in /home was erased too.

The manual option, Something Else, is your best bet, as always.

When the list of partitions shows up, all you need to do is select them one by one, click the Change button and tell the installer how to use each partition.
The root with mount point /, ticking the format box so that it deletes the old system.
The /home with mount point /home, making sure the format box IS NOT selected.
The swap as swap area (no mount point).

If you want to reuse the /boot also, the same applies. Select it and choose the mount point /boot, formatting it also to delete the old boot files.

That's it.

As for the user(s). In the new installation create the first user (during the installation) the same as your first user on the old installation. All permissions will be fine, there is no olduser newuser folders, everything stays the same.

I am using a separate /home and I don't need to change permissions, make symlinks, etc. Nothing. Just create the identical user as you did in the old install and it works out.
If you do want to create different folders, symlinks, and other stuff, that's up to you, but you DON'T need to, that's the main part you should know. It's not a requirement, it's an option.

---

### Post by BigBaka on 2012-06-24
Thanks all for the tips, used the third option and reset all the mount points and only checked format for the /boot and / mounts.

Re-installed using same user name and everything was still there when I opened up. Only problem now is getting everything re-installed. See my medibuntu post on the same install forum...

BB

---

### Post by nipunshakya on 2012-06-24
Good to know that...

Happy Linuxing

---

