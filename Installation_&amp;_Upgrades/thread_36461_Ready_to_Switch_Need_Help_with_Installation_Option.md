---
title: "Ready to Switch: Need Help with Installation Options"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-05-23
After two days of slow downloading, I finally have my Ubuntu DVD and I'm ready to make the switch. [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img] My harddrive has been split into 4 partitions for Linux: boot, root, home, and swap. 

Does the Ubuntu installer have an option for replacing the OS but keeping user accounts from another distro? I have about 10gigs of files in my Mandrake user account alone. My plan is to replace the Mandrake OS with the Ubuntu OS, copy some of my files and settings from my old account into my new one, and manually delete my old accounts.

Does this sound like a good plan? Your advice would be greatly appreciated.

---

### Post by vladanian on 2005-05-23
[QUOTE=cinematography]After two days of slow downloading, I finally have my Ubuntu DVD and I'm ready to make the switch. [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img] My harddrive has been split into 4 partitions for Linux: boot, root, home, and swap. 

Does the Ubuntu installer have an option for replacing the OS but keeping user accounts from another distro? I have about 10gigs of files in my Mandrake user account alone. My plan is to replace the Mandrake OS with the Ubuntu OS, copy some of my files and settings from my old account into my new one, and manually delete my old accounts.

Does this sound like a good plan? Your advice would be greatly appreciated.[/QUOTE]
 What I typically do in this situation is rename my home directory, like from "user" to "user-old," and then, during the OS install, choose not to format the home directory.  When you're up and running with Ubuntu, you'll have "user" and "user-old" in your home dir.  You can then copy the files you'd like to keep from your "user-old" dir to your new home directory.

You'll probably have to use chown to change ownership of your old files to your new user.

---

### Post by cinematography on 2005-05-23
Wow. I'm so happy someone replied. :) Thanks, vladanian. 

I've gone through the installation options a couple of times. They're a little confusing and I want to make sure I don't fuzzuck up anything before I continue. By default, it won't format anything unless you tell it to? I just want to format one partition, and that's my 10gig / partition. So if I go through, select that partition, and then select ext3, it'll format and install Ubuntu to that partition? :(

---

### Post by vladanian on 2005-05-23
I don't have the installer running in front of me, but the default behavior--which you don't want--is to wipe your whole disk and have Ubuntu partition it anew.  

Instead, you want to choose manual partitioning.  That'll show you your disk and its 4 current partitions, and for each, you'll need to set whether or not to format it and set what the mount point should be.

For home, set the mount point to home and set it not to format.

Again, I don't know the exact names of everything off the top of my head, but the basic idea is custom partitioning, setting the appropriate mount points for each existing partition, and setting everything BUT the home partition to be formatted anew.

Good luck!

---

### Post by cinematography on 2005-05-23
This sounds about right from what I can remember as well. I'm going to wait for a couple more replies and try to find some EASY documents on this. Thank you so much again for your reply and help.

---

