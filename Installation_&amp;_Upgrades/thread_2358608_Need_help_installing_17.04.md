---
title: "Need help installing 17.04"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by epicdragon44 on 2017-04-15
Hello everyone!

I am doing an installation of Ubuntu GNOME 17.04 on top of my existing  Ubuntu Unity 16.10. I currently have three operating systems on my  laptop, being MX Workbench, Ubuntu 16.10, and Cent OS in that order (and  then swap). As a result, the Ubiquity installer doesn't give me the  option to install Ubuntu GNOME 17.04 on top of Ubuntu 16.10 and save my  files, apps, etc., from Ubuntu 16.10. Can I somehow do that manually,  and save my current Ubuntu preferences?

I also see that while installing, it gives me the ability to reformat a  partition. I understand that reformatting deletes the old files. If I do  not reformat, does it save the old files and preferences?

Thanks!

Does this mean Yes to my second question? [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by vasa1 on 2017-04-15
Run```
sudo fdisk -l; echo; sudo parted -l; echo; mount; echo; df -h
```and post the entire output here. People will have a better idea of your set-up.

---

### Post by oldfred on 2017-04-15
I do not recommend the "dirty" install or not formatting.
It still overwrites all standard configuration files with defaults, but any new file you added will be saved.
I do not think it saves a list of installed apps.
But if using different gui, the settings are usually but not always different, but you may get conflicts.

My process is to always have backups of my data, /home, files changed in /etc (I just copy those few files into /home as I edit them), and list of applications installed. I do install some KDE apps and those pull in all sorts of dependencies.
And if I just want to experiment, I install to another 25GB / (root) partition. I have all data in a shared /mnt/data partition that I link into all installs.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

