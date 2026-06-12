---
title: "2 OS 1 user"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by Mellatau on 2015-12-22
Hello.
I have Mint 17.3 installed with /home folder on a separate partition. Now I want to install Ubuntu 14.04 LTS as a second system.
The question is: can I use the same /home folder with the same user for both Mint and Ubuntu?
There is a point during installation process where I can setup /home on a separate partition without formatting it. Will this do the trick? Will there be any problems?
It's such a pain to copypaste FireFox, ThunderBird and other apps' profile folders over and over again whenever I want to "switch workplaces", so I'm looking fore a solution. Is there some?

---

### Post by lliseil on 2015-12-22
[http://ubuntuforums.org/showthread.php?t=2291023&p=13407994](http://ubuntuforums.org/showthread.php?t=2291023&p=13407994)
See Bucky Ball's answer for most informations, then mine (browser...)

---

### Post by Bucky Ball on 2015-12-22
Snap. :) The short answer is yes. And /swap. Choose 'Something Else' and mark /home and /swap to use but NOT to format.

[This will link you directly to my post ]("http://ubuntuforums.org/showthread.php?t=2291023&p=13339915&viewfull=1#post13339915")on that thread. Good luck.

---

### Post by oldfred on 2015-12-22
I typically do not suggest sharing /home, but use /mnt/data.
And I even have moved my Firefox & Thunderbird profiles into a shared data partition. I did that when dual booting with XP and used a NTFS data partition.

The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)

---

### Post by 1clue on 2015-12-22
The problem with doing this is that your apps are rarely on the same version.

Your apps put their settings in your home folder.  For any version of an app, if Mint is on version A and Ubuntu is on version B, and the two versions don't use the same exact config format, then Mint (since A is earlier than B) will not be able to run the app because its configuration appears to be corrupt.

It's best to give each a separate home, and then share the downloads, documents, etc by using a symbolic link to a common folder with permissions that work for both users.

---

### Post by lliseil on 2015-12-22
Woah, we're close to unanimity with four answers and *one* single and easier way ;)

Note that with /home in the system partition, IMHO you better have a workin backup solution (at any case but yet definitively here!). Unless you never customize your shell & terminal, conky, ssh keys, file-level encrypted keys and a variety of other conf. I keep a small, separated /home on the fastest drive for that reason. Even though they are backed up once a day. I also find it easier to separate my files (in /data) from dotfiles (in $HOME) and temporary. I.e. for synchronizing and backing up.

---

### Post by Mellatau on 2016-01-19
('v been away from laptop for a while...)

So the solution is:
1. to back up what's needed;
2. to install OSs needed;
3. during installation process make each of them use the same swap and /data partitions without formatting;
4. to place backed up files and profiles into /data partition;
5. install needed software in each system, delete .folders in /home/username directory and place symlinks to the ones in the separate /data directory instead.

Is that all? And is that all correct?

And a few more questions:
1. can I make /data an NTFS partition? To make it accessible from Windows without Linux Reader app (not necessary, but would be nice).
2.any issues with openSUSE being one of the operating systems in question? It's ISO didn't have a live OS, unlike Ubuntu-based ones, so I don't know if it's installation process is any different.

---

### Post by oldfred on 2016-01-19
I do not delete any . folders, just the standard data folders like documents, videos, music, etc.
And then symlink all those folders to my data partition.

I have moved .thunderbird & .mozilla to my NTFS back with XP. 
I changed profile.ini to use new location.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by 1clue on 2016-01-19
I think you have it backward.

You really need a separate $HOME for each operating system, but you can have a common set of standard folders like documents, downloads, etc.

These standard visible folders are what goes in the data partition, but all your .folders and .files stay in the original place.

---

