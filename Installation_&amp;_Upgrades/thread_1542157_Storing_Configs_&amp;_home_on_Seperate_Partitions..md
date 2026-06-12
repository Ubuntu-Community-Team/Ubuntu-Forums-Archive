---
title: "Storing Configs &amp; /home on Seperate Partitions."
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by MonkeyPants on 2010-07-30
Hi everyone.

I'm trying to make a clean install of Ubuntu but doing so using three or so partitions: -


[LIST]
[*]/home
[*]Config files
[*]Main install
[/LIST]
I've found a few guides out there for setting up the /home folder on its own partition, but nothing really for config files. The only solution I have come up with is using a series of links using [FONT=Courier New]*ln*[/FONT]. The only downside is that for every install I'd have to go around the system and replace the links.

Since I'm on the topic too, and I know this probably sounds daft, but does a file linked with *[FONT=Courier New]ln[/FONT]* carry and admin privildges? So if it was created by root, would you still need to be root to edit/delete the file its linking?

Any help would be appreciated.

Thanks all.

---

### Post by ajgreeny on 2010-07-30
Part of the answer to this depends on what you mean by config files.  Most of your user configuration files are stored in hidden folders in /home, so if you have a separate /home partition, which is highly recommended, much of your config will already be there, and I don't think you can put these files anywhere other than the user's home.

What you could do, however, is use a separate /data partition for all your data files, eg docs, photos, music, videos, etc etc, and just have the configuration files in /home, but none of the data files.  A separate /data partition formatted as ntfs is often used when dual booting in order to be able to use the data files in both ubuntu and windows, and it works very successfully.

I think a linked file carries exactly the same permissions as it does in its "real" home; it is after all the same file, not a copy or anything like that.  I am not totally sure about file permissions if you use a shared ntfs data partition, but no doubt others will be able to answer that query.

---

### Post by MonkeyPants on 2010-07-30
Thanks for the reply, ajgreeny.

I was thinking Apache config files, things like that. So generally configs that are outside the /home folder.

My aim is to have a system that can be flawlessly upgraded to newer kernals without any loss of data, configurations and setup.

It's good to know that at least half of what I'm doing here is right :P. I seem to get mixed opinions about breaking installs up over partitions.

---

### Post by oldfred on 2010-07-30
I have a separate /data partition with all the normal folders in it. I then link those into /home, so /home has just the user configs. Whenever I manually edit any config in /etc I try to remember to copy to a folder in /home so my standard backup makes a copy and I do not have to backup all of /etc.

I also wanted to make it easier with each install. My first one I tried to do every thing from the command line, then I listed history and converted to a bash file. I now have one script to  mount files and auto edit fstab and another to add in all the programs I have installed that I export via dpkg.

My data gets mounted in /usr/local/fred and then running this from /home (becomes default location of link) links every folder in /data.
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done
I was doing this (now commented out in my script):
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
etc

Part of my program install adds in sources and some specific apps (may be redundant) and then I reinstall all programs from this file:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

