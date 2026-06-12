---
title: "Re-sync with Old Home Folder after Installing 15.10 on SSD?"
date: 2015-12-08
forum: Installation &amp; Upgrades
---

### Post by dswaugh on 2015-12-08
Just installed Ubuntu 15.10 on an SSD, but want to sync this new install with my old home folder on the old drive. Is this possible (with LiveCD or gparted, for example)? Or, do I need to go through the install process again, doing something special in the process? I've scoured the web for info on how to do this, but all of the info seems to relate more to relocating a new home folder than it does re-syncing a new 15.10 install with an old Home folder on a separate disk. Thoughts? Thanks much for your time, and so sorry if I've duplicated someone else's post.

---

### Post by oldfred on 2015-12-08
When you say sync, do you just want to mount & use the oldhome on old drive, or do you want to just copy all the data on the old home onto the new home?
Do you just have SSD or also another HDD?
Is your home a partition inside / (root) or a separate partition?

If you have not made changes to new /home on SSD, then you can just copy everything. Essentially the reverse of the move home to a new partition instructions. 

I keep /home inside my / partition, but have all my data folders like Documents, Music etc in data partition on my HDD. My /home then is tiny, but does have all the user settings and configurations. It also has .wine, Firefox & Thunderbird folders which I may also move to my data partition. I used to have Firefox & Thunderbird in a shared NTFS partition back when I still had XP.

---

### Post by dswaugh on 2015-12-10
Thanks so much for replying, oldfred. Yes, I'm very interested in doing what you said. I want to install /home inside my /partition on the SSD (I've allocated approximately 56GB of space on the SSD), but then I want to store all of my /home data on a separate HDD. Just wondering how to set this up. Do I just do a standard install on my SSD with LiveCD (putting everything on a single ext4 partition rather than creating separate /root and /home partitions), and then do a separate standard install on the HDD (again, without creating separate partitions)? Or is there a better way? Seems I read on one of your previous posts that you like to maintain a fully functional Ubuntu OS on both the SSD and HDD. So, if I do this, how do I ultimately set things up to transfer all of my /SSD/home data to /HDD/home so I don't end up using any of the SSD's 56GB ext4 partition for data? Do I just copy data files from one /home folder to the other as I go, or is there an easier way? Essentially, I guess I'm looking for a way for /SSD/root to automatically write to /HDD/home. Is this possible? Would appreciate any advice you can give me on the subject, as it seems I've read so many different posts but still haven't been able to find an easy solution. Have been using Ubuntu for years, so am familiar with creating separate partitions via gparted (as well as performing "something else" installs via LiveCD). It's just that this is my initial foray into the realm of using separate SSDs and HDDs for OSes and data. Help?

---

### Post by oldfred on 2015-12-10
I do not normally copy /home from one install to another. But I have scripted about 75% of the configuration. And I keep trying to use Unity, for me it is better then it was, but I like the old gnome panels or fallback with menus. So after a few days I run my part 2 install script including gnome-panel and some settings.

Then my /home is tiny and all my data is in another data partition which I link into all my installs.
I just posted my current partitions here:
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by dswaugh on 2015-12-10
<<[COLOR=#000000]Then my /home is tiny and all my data is in another data partition which I link into all my installs.>>
[/COLOR]
Okay, think I got it. Your SSD's home folder is part of the SSD's root partition, but you link it to the data partition on the HDD. Guess my last question is how one does this. Once I follow your suggested partition scheme on both disks, how do I link my two home folders (SSD /home and HDD /home) to the data partition on the HDD, making them both write data to it automatically? Am assuming that you're creating your script with a terminal command? If so, could you please share it? Also, I know that I should create an 8GB SWAP partition on the HDD (since I have 8GB of RAM), but should I also do so on the SSD? Have read mixed reviews about SWAP partitions on SSDs (makes the SSD work harder, shortens its shelf life, etc.). Anyhoo, thanks much for your time, oldfred. You've been a huge help. Blessings.

---

### Post by oldfred on 2015-12-10
Details are in oldfred's post in first link on splitting /home and data. Post #4. :)

Last entry is a one line mini-script I found somewhere that links every thing at once. Best first couple of times to do it manually so you know it works the way you expect.

---

