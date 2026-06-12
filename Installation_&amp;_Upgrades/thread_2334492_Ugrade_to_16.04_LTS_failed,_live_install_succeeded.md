---
title: "Ugrade to 16.04 LTS failed, live install succeeded but home problem"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by longsjos on 2016-08-19
Someone else originally set up my laptop to dual boot windows and ubuntu. Since then I've been able to "follow the bouncing ball" and upgrade to each new LTS version until 16.04. 
The upgrade from 14.04 failed with lots of errors saying that packages could not be installed, kernel panic, etc. I then re-installed 16.04 using a live usb. 
As there were existing partitions,  I chose "Something else" for installation type.
/dev/sda5 looked like it contained Ubuntu so I set the mount point as "/" 
/dev/sda6 originally had a label 'local' so I took a guess and set the mount point as "/home".
After installation completed, /home contains a directory "anne" (with empty Desktop, Downloads, etc) along with the old 14.04 "home" directory (i.e., all my old data files).
How do I go about getting /home/anne to have all the relevant files in /home/home/anne? Copy? Link? Do something with the partition? 
I'm out of my depth at this stage and would appreciate suggestions.

---

### Post by mook765 on 2016-08-20
Move the Folders from /home/home/anne to home/anne.
Open the terminal, use these commands:
```

mv -f /home/home/anne/Desktop /home/anne
mv -f /home/home/anne/Documents /home/anne
mv -f /home/home/anne/Downloads /home/anne
mv -f /home/home/anne/Music /home/anne
mv -f /home/home/anne/Pictures /home/anne
mv -f /home/home/anne/Public /home/anne
mv -f /home/home/anne/Templates /home/anne
mv -f /home/home/anne/Videos /home/anne
```
You may check first if all these folders are in /home/home/anne.
If one of the folders i mentioned in the command-list is not present in /home/home/anne, you don't need to use the corresponding command.
If you have more folders in /home/home/anne which you created yourself and want to move them to /home/anne, just build a command following my examples.
There are more files and folders in /home/home/anne which you may not see just right now. you may see them when you open your file manager and enable "Show hidden files"
These hidden files are mostly configuration files from your former release, I think you should not move them, leave them where they are.
Ready to go?
Regards...

---

### Post by longsjos on 2016-08-20
Thanks. Yes, I can move the files. However, what I'm unclear about is partitions. I want to keep my data files on a separate partition. When I reinstalled 16.04 and set the mount point for /dev/sda6 as /home, does this mean that all files in /home are stored on /dev/sda6?

---

### Post by mook765 on 2016-08-20
Yes, this means that all your files and folders in /home are on this partition (sda6).
The installer moved the content off your old  /home-folder ( which was on sda6 ) to /home/home/anne ( this is on sda6 too, as it is in /home ) to avoid complications with the old configuration-files which might be not valid for the new release..
So now you have moved all your data from /home/home/anne to home/anne.
If you don't want to keep the old configuration-files which are still located in /home/home/anne (these files are not in use in that location),  you may (not must, or you can do it later) delete the folder /home/home/.
You can do that with your file manager (rightclick on the folder > delete or move to trash)
or you can use the command```
 rmdir /home/home
```.
But I think it is better to delete that later and keep this folder for the moment.
Some of the configuration-files might be useful. If you use firefox and/or thunderbird, we can restore the profiles, so you don't need to setup firefox and thunderbird again.
Interested?
Congratulations, you installed a new release without any trouble...
Which distribution do you use ? Ubuntu, Lubuntu, Xubuntu, Kubuntu ?
Good luck...:)

---

### Post by longsjos on 2016-08-20
Thanks very much for explaining what happened during the installation process and the necessary commands for moving things around.  
I'm using Ubuntu.

---

### Post by mook765 on 2016-08-20
I am happy that this was successful.
So what about restoring firefox or thunderbird profiles.
We could do a workaround, but not tonight, for me it is four o'clock in the morning, I get a bit tired just right now.
Just let us know...

---

### Post by longsjos on 2016-08-20
Thanks for the offer. After your hint that it could be done, I looked around and managed to restore the firefox profile. I have not used thunderbird so no profile to restore.

---

