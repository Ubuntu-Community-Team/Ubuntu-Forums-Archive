---
title: "Restoring A Backed Up Home Folder"
date: 2019-12-24
forum: Installation &amp; Upgrades
---

### Post by uzzo23 on 2019-12-24
Hello folks, I need a little help restoring my backed up home folder. I just did a clean install with xubuntu 18.04 from ubuntu 16.04 but backed up my home folder from the ubuntu distro using deja dup. I've got it on an SD card but cant figure out how to get it installed into my new home folder with xubuntu.

---

### Post by CelticWarrior on 2019-12-24
There's no installation *per se*...

If backed up with Deja Dup you use the same program to recover the contents to the same locations as before. Differently, if you had a separated /home partition you would have to select it (and no format, of course) during the installation using "Something else..."

---

### Post by deadflowr on 2019-12-25
In deja-dup go to Storage Location and set it to Local folder.

Then select the Choose Folder option and click on the sd card in the list of devices 
(removable devices should be listed in the left panel area that shows when selecting the choose folder option)

Then navigate the sd cards contents till you find the contents with a bunch of duplicity files.

Once you find them click Ok and then go back up to Overview and click Restore.

If you set a password for backups you'll need to use it to unlock the backups.

If deja-dup is not installed then go ahead and install it.


Hope that makes sense.

---

### Post by uzzo23 on 2019-12-25
> **deadflowr said:**
> In deja-dup go to Storage Location and set it to Local folder.

Then select the Choose Folder option and click on the sd card in the list of devices 
(removable devices should be listed in the left panel area that shows when selecting the choose folder option)

Then navigate the sd cards contents till you find the contents with a bunch of duplicity files.

Once you find them click Ok and then go back up to Overview and click Restore.

If you set a password for backups you'll need to use it to unlock the backups.

If deja-dup is not installed then go ahead and install it.


Hope that makes sense.

I tried that, unfortunately I get an error that says that there are no backups to restore. I don't know if it makes a difference or not but deja dup came with the ubuntu version I had. I had to install it with this fresh xubuntu install. I don't know if that makes any difference or not. The files are on the SD card, I just don't know how to unpack and restore them as my home folder.

[ATTACH=CONFIG]284678[/ATTACH]

---

### Post by deadflowr on 2019-12-26
This user had a similar issue:
[https://ubuntuforums.org/showthread.php?t=2384934]("https://ubuntuforums.org/showthread.php?t=2384934")

And here's deja-dup's *if nothing works try these*:
[https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase]("https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase")

---

### Post by uzzo23 on 2019-12-29
> **deadflowr said:**
> This user had a similar issue:
[https://ubuntuforums.org/showthread.php?t=2384934](https://ubuntuforums.org/showthread.php?t=2384934)

And here's deja-dup's *if nothing works try these*:
[https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase](https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase)

Sorry for the lag, it's been kind of crazy around here the last several days. I read the post from the user that had the same issue as me. That fix didn't work for me so I read the wiki. I went to the section about restoring a backup and tried to run the command in the terminal it said to run for the restoration. I got an error with that too.

```
patrick@patrick-OptiPlex-360:~$ duplicity --gio file:///media/patrick/756B-3441/tmp/restore
Warning: Option --gio is pending deprecation and will be removed in a future release.
Use of default filenames is strongly suggested.
Command line error: Expected 2 args, got 1
Enter 'duplicity --help' for help screen.

```

---

### Post by deadflowr on 2019-12-29
/media and /tmp are separate entries like
```
duplicity --gio file:///media/patrick/756B-3441 /tmp/restore
```
hence the output: *Expected 2 args, got 1*

---

