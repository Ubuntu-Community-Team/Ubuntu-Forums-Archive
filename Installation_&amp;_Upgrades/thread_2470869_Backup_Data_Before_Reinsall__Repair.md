---
title: "Backup Data Before Reinsall / Repair"
date: 2022-01-14
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2022-01-14
I want to use RSync to back up my data before reinstall or repair. What's the best way to do that. I booted off a flash drive into Lubuntu. In KDE Partition Manager I can see the Toshiba drive with system, root, and home. But in PacManFM-QT QT File Manager I don't see that drive. Is that drive mounted? Will I need to do something so that I can access the files and copy them to an exernal drive? I ran into problems when trying to RSync all the files to the external drive.

---

### Post by oldfred on 2022-01-14
This old post from 2009 is a very simple script which I started with. Other time then I have added commands.
[https://ubuntuforums.org/showthread.php?t=868244&page=2&p=7015603#post7015603](https://ubuntuforums.org/showthread.php?t=868244&page=2&p=7015603#post7015603)
You do have to create a mount point & set ownership & permissions, script has /media/backup, I use /mnt/backup.

I do not mount the backup in fstab, so not always available.
Once I forgot to manually mount & it created a mount in / and copied everything into / filling it. oops.

So I added a check on mount & then mount if not mounted.

```

my_mount="/mnt/backup"
my_user="/home/fred"
# /dev/sdb4 backup_b partition on Z170, became sda4 with new NVMe drive
if grep -qs "$my_mount" /proc/mounts; then
  echo "It's mounted."
else
  echo "It's not mounted. Trying mount"
  /usr/bin/mount -t ext4 /dev/sda4 $my_mount
  if [ $? -eq 0 ]; then
   echo "Mount success!"
  else
   echo "Something went wrong with the mount..."
   exit $?
  fi
fi

```

Typically do not backup system as that is on my flash drive installer.
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)

My rsync backup script file includes list of apps also. I run the command to update list and save in /home so included in backup.  The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)


I also then added another file listing all the temporary folders to exclude.
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by MAFoElffen on 2022-01-15
You said "before you reinstall or repair"...

Like TheFU, my idea of a revoevry plan has evolved over the years.It went from doing full images, and trying to rebuild/recover RAID arrays, to incremental's, to backup data and config files beyond a fresh install. That is the quickest way t get back online, and to migrate.

I run this periodically as a schedule job, to be able to migrate an installation to a newer version, or to keep a list of what I might need to do to recover during a disaster:

Everyone tells people "to get a list of what is installed..." That is  too much information, convoluted and very confusing. What you really  need is: What was installed manually by you, beyond what was the base  initial installation.
```

comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc  /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort  -u) >> ~/manually_installed.txt

```
And then I use that to look at those packages and see what is currently  available... I use that list to make a plan  to retrieve the config  files for those packages, to update for a new system if I am planning on a migration... And I use that to adjust my backups for recovery.

You will be surprised, that once you see "that list", of how much less  daunting and simpler things will seem, in how to get from Point A to  Point B in a recovery or migration... There are a lot of things that are in a default installation. I used to do just image everything and restore. Years ago. I found that if I do a clean install, and restore just what is different, it is light years faster to recover. I think both TheFu and I have a migration or recovery down to about 20 minutes or so. (with scripting)

I use this to look at current systems, to audit what was installed  during the system's life-cycle, to see what is really used versus  unused... to  remove things that were installed as a 'test' or 'trial'  of something, to make decisions to remove unneeded packages that are no  longer needed in the current system. That way things are backed up that are current, and things brought forward in a migration are not fluff or bloat, but what is needed and relevant.

Hmmm. I've use it enough, that I think it is also a good diagnostic tool to include in my UbuntuForums 'system-info' script...

---

### Post by webmanoffesto on 2022-02-05
I run
sudo rsync -rltgoDv --progress --exclude=".*" /media/ubuntu/Home/tom/tom/ /media/ubuntu/Backup\ Plus/Toms.Laptop.Backup..2022.02.05 --log-file=mylog.log

It seems to stall and 

Log File says:
2022/02/05 22:20:19 [19843] building file list
2022/02/05 22:20:19 [19843] rsync: link_stat "/media/ubuntu/Backup" failed: No such file or directory (2)
2022/02/05 22:20:21 [19843] rsync: mkdir "/home/ubuntu/Plus/Toms.Laptop.Backup..2022.02.05" failed: No such file or directory (2)
2022/02/05 22:20:22 [19843] rsync error: error in file IO (code 11) at main.c(682) [Receiver=3.1.3]

I want to back up /media/ubuntu/Home/tom/tom/ 
to
/media/ubuntu/Backup\ Plus/Toms.Laptop.Backup..2022.02.05
I don't see a problem with the paths.

What is the problem here?

---

### Post by linux-sysop on 2022-02-06
Timeshift is the best backup utility for your OS.  It takes a snapshot and can be set up to schedule system snapshots on a regular basis.  It can use both RSync or BTFS to store the snapshot.  Snapshots can be stored externally, I keep mine on a 32 GB USB thumb drive.  It has a friendly GUI, saved me several hours on repairing system errors I have created through tinkering with the OS.

---

### Post by webmanoffesto on 2022-02-06
I'm getting "No space left on device" messages. I'm running Ubuntu 20 on a 32G flash drive, with a persistent sector of about 1Gb. Is it the persistent sector that's causing the "No space left on device" error?
It seems to me that I had fewer problems when I ran Lubuntu without a persistent sector.

---

### Post by MAFoElffen on 2022-02-06
Okay... What you just "might have said" changes things...

How is Linux Installed on your PC and how does it run? You mentioned persistent sector" which implies a portable USB Live CD type of environment with persistence...

What you just mentioned confuses the situation of it being installed as a traditional installation.

But it ends up the same if you think of it as a migration to another release...

---

### Post by him610 on 2022-02-07
@MAFoELiffin
>  I think it is also a good diagnostic tool to include in my UbuntuForums 'system-info' script...
I was wondering why your 'system-info' doesn't have its own sticky in either Hardware or General Help.  It is a really good utility.

---

### Post by MAFoElffen on 2022-02-07
> **him610 said:**
> @MAFoELiffin

I was wondering why your 'system-info' doesn't have its own sticky in either Hardware or General Help.  It is a really good utility.

@him610

Thank you. I appreciate that.

I dedicated it to Ubuntu Forums and the User's here that help other Users, as a diagnostics tool. To help them help others. The Moderators and Admin's (Admin Council) approved and endorsed it... They made me the Admin for the UbuntuForum GitHub (Stable) Repo for it, so I could manage it and it's changes... I also am an Admin for the DEV repo for it.

The first thing they said was that the Hardware Section already has about 8 sticky's... So that was saturated already. That was 'specifically discussed.' LOL.

At first, I thought it would be announced "somewhere", put into a sticky, or at least one of them post the announcement "somewhere" in a post... But they told me that now-a-days, no one seems to look at or pay attention to Sticky's. I've found that to be true with my "Graphics Resolution" Sticky... I support the Linux Graphics Layer (not just here) and you would be surprised how many people iI refer back to that for their solution. Wildmanne39 has the same with his 'wireless-info' script and sticky... What was decided was that we should spread the word on our own. I had about 10 people who helped test the snot out of for about 5 months while I made changes and improved it. Those are recommending it to people they help now.

I looked into announcing it at Ubuntu Discourse, or the Weekly News Letter. The Weekly Newsletter scrapes things that are trending from 'other' sources. One of which is from Ubuntu Discourse. I joined there... I went through their vetting process of so many posts before you can actually start a thread. The community there... Well... I don't like to talk about anyone, but their focus is not like here. It is not for support of Users.  (Their focus on marketing hype. I'll leave that as that.) I asked myself why go outside of the Forum, to announce something for 'here'? I'm active here and on Launchpad. I contribute to other projects like helping Yann with 'boot-info'...

I'm just here to help, and to help people to be able to help others, but I haven't figured that "spreading the word" part out yet. LOL Yes, I'm still trying to figure that out.

I would invite your ideas on how you might think would be a good way to do that.

---

### Post by Tadaen_Sylvermane on 2022-02-08
```
[COLOR=#000000][FONT=&amp]comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc  /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort  -u) >> ~/manually_installed.txt[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Getting incorporated to my backups now. Very nice and much appreciate the sharing.

*EDIT* I'm assuming this is bash. It failed with my /bin/sh script. I'm not good at differentiating the differences. As such I've changed to accommodate.

[/FONT][/COLOR]```
NOW=$(date +%F-%H%M)
apt-mark showmanual | sort -u >> /tmp/aptmark."$NOW"
gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | \
sort -u < /tmp/aptmark."$NOW" > ~/manually_installed.txt
rm /tmp/aptmark."$NOW"
```

---

### Post by MAFoElffen on 2022-02-08
> **Tadaen_Sylvermane said:**
> ```
[COLOR=#000000][FONT=&amp]comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc  /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort  -u) >> ~/manually_installed.txt[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Getting incorporated to my backups now. Very nice and much appreciate the sharing.

*EDIT* I'm assuming this is bash. It failed with my /bin/sh script. I'm not good at differentiating the differences. As such I've changed to accommodate.

[/FONT][/COLOR]```
NOW=$(date +%F-%H%M)
apt-mark showmanual | sort -u >> /tmp/aptmark."$NOW"
gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | \
sort -u < /tmp/aptmark."$NOW" > ~/manually_installed.txt
rm /tmp/aptmark."$NOW"
```
Good catch. Yes, it is BASH, that I transformed into a single CLI terminal command so that people can cut and paste, and be easy to run.

In my own coding style of scripts, I (also) like cut things into logical sections. I do that in Scripts, so that it is easier to read and debug, with plenty of room to add comments. Not just to jog my own memory, but for others to follow (if need be), as if it was telling a story.

That also makes it easier down the road, that if in a Script, something is done more than once, to break it out, and transform that process into a function, to be reused.

---

### Post by MAFoElffen on 2022-02-09
> **Tadaen_Sylvermane said:**
> ```
[COLOR=#000000][FONT=&amp]comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc  /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort  -u) >> ~/manually_installed.txt[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Getting incorporated to my backups now. Very nice and much appreciate the sharing.

*EDIT* I'm assuming this is bash. It failed with my /bin/sh script. I'm not good at differentiating the differences. As such I've changed to accommodate.

[/FONT][/COLOR]```
NOW=$(date +%F-%H%M)
apt-mark showmanual | sort -u >> /tmp/aptmark."$NOW"                               # This would append
gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | \
sort -u < /tmp/aptmark."$NOW" > ~/manually_installed.txt                              # This is missing the compare of the two outputs
rm /tmp/aptmark."$NOW"
```
*** This is missing the "compare" of the two outputs... 
What I do is to exclude those packages that are default installed at installation and not in the list of manually installed packages... Then I exclude packages that are in both lists... Those can be packages that were default installed at installation, but later reinstalled by the User. That would change the status of the package to "manually installed", even though it was there already. 

This is the function I came up with for that...
```

function GetUserInstalled ()
{
    ## Get a list of User Installed Packages
    
    echo -e "   --- User Installed Package List:"
    # Use apt-mark to list all packages marked as manually installed. 
    apt-mark showmanual | sort -u > ./ManuallyInstalled.tmp
    # Get the list of default installed packages at initial installation.
    gzip -dc /var/log/installer/initial-status.gz | \
        sed -n 's/^Package: //p' | \
        sort -u > ./DefaultInstalled.tmp
    # Use compare, to exclude those defaults that are unique, AND exclude defaults 
    # that are presently marked as manually installed. (Those 'may' have been changed.)  
    comm -23 ManuallyInstalled.tmp DefaultInstalled.tmp > ./UserInstalled.tmp
    # Print the list in two columns
    awk 'NF' ./UserInstalled.tmp | pr -2T  # You can remove the filter to pr on this to keep in a single column...
    nl # Add newline in report
    # Remove the temporary files
    rm ./*.tmp
}

```
If you keep the file or list in a single column, then you can use a for each loop to read the packages and install all of them from that list for a Migration... In this function, I printed it in two columns to fit better in the 'system-info' report

---

### Post by Tadaen_Sylvermane on 2022-02-09
indeed. ok added that. think my function is now nearly the same structure save the awk line.

```
dump_manual_packages() {    
    apt-mark showmanual | sort -u > /tmp/pkglist1.temp
    gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Packages: //p' \
    | sort -u > /tmp/pkglist2.temp
    comm -23 /tmp/pkglist1.temp /tmp/pkglist2.temp > /etc/manually_installed.txt
    rm /tmp/pkglist1.temp
    rm /tmp/pkglist2.temp
}
```

---

### Post by MAFoElffen on 2022-02-10
I added it to my system-info script last night... Did testing on it this morning on some of my test-case machines. I had to tweak it for General User Use.

Your use is more controlled and predictable. You know what is there and can verify that...

If someone's system is a pre-built System Image, for example for Raspberry Pi, or cloud images, then the initial-status.gz file does not exist. I guess you could say that a system pre-built image isn't installed. It is generated.I had to create some error checking and fallback to allow General Ubuntu User just in-cases... LOL.

---

### Post by webmanoffesto on 2022-02-11
I'm running this as root but I'm getting "failed: Operation not permitted (1)"
How do I get around that? Should I assign to myself "ownership" of the folders and then run rsync?
How would I do that?

Does this advice make sense?
```
Remove se attribute for the following file:
attr -S -r <Attribute> path_to_file (source: [https://help.onapp.com/hc/en-us/articles/222048388-Rsync-fails-to-finish-the-operation](https://help.onapp.com/hc/en-us/articles/222048388-Rsync-fails-to-finish-the-operation))

```I don't understand that.

---

### Post by MAFoElffen on 2022-02-12
Who are you addressing? And you didn't post the command you tried (exactly) that failed... Which would be useful for someone to see what went wrong.

---

### Post by webmanoffesto on 2022-02-12
The command I ran
sudo rsync -rltgoDv --progress --exclude=".*" /mnt/toms_home_folder/tom/ /media/ubuntu/Backup\ Plus/Toms.Laptop.Backup..2022.02.05 --log-file=mylog.log 

I thought this was running fine. But hours later I come back to the laptop and it seems to be frozen. the screen shows:
```
tom/Documents/Artisans_Asylum/Electronics/SparkFun.Weevil.Eye/how-to-solder---through-hole-soldering_files/f95i88OSWB4_data/
tom/Documents/Artisans_Asylum/Electronics/SparkFun.Weevil.Eye/how-to-solder---through-hole-soldering_files/f95i88OSWB4_data/XK1Wmv1w0DW2pGZQiuauyJFq6_RKmUyI09l1c9PyGCs.js
          9,402 100%   71.18kB/s    0:00:00 (xfr#713, ir-chk=1012/1920)
tom/Documents/Artisans_Asylum/Electronics/SparkFun.Weevil.Eye/how-to-solder---through-hole-soldering_files/f95i88OSWB4_data/watch_as3.swf
        297,523 100%    2.03MB/s    0:00:00 (xfr#714, ir-chk=1011/1920)
tom/Documents/Artisans_Asylum/Electronics/SparkFun.Weevil.Eye/how-to-solder---through-hole-soldering_files/f95i88OSWB4_data/www-embed-player-vflatXVas.css
         32,768  19%  217.69kB/s    0:00:00  


```

The log file from today is very long.
Log File: [https://pastebin.com/BqJvLNt9](https://pastebin.com/BqJvLNt9)

The directories are getting confusing, but
Copy from: /mnt/toms_home_folder/tom/tom/Documents = 80GB
Copy to:
/media/ubuntu/Backup Plus/Toms.Laptop.Backup..2022.02.05/tom/Documents = 420MB
There is also
/media/ubuntu/Backup Plus/Toms.Laptop.Backup..2022.02.05/Documents = 1.2GB

I tried this running deja-dup as sudo. I got errors
```

Traceback (innermost last):
  File "/usr/bin/duplicity", line 106, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 92, in with_tempdir
    fn()
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1525, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python3/dist-packages/duplicity/commandline.py", line 1175, in ProcessCommandLine
    globals.backend = backend.get_backend(args[0])
  File "/usr/lib/python3/dist-packages/duplicity/backend.py", line 225, in get_backend
    obj = get_backend_object(url_string)
  File "/usr/lib/python3/dist-packages/duplicity/backend.py", line 211, in get_backend_object
    return factory(pu)
  File "/usr/lib/python3/dist-packages/duplicity/backends/giobackend.py", line 82, in __init__
    ensure_dbus()
  File "/usr/lib/python3/dist-packages/duplicity/backends/giobackend.py", line 37, in ensure_dbus
    output = p.communicate()[0].decode("utf8", errors="replace")
 AttributeError: 'str' object has no attribute 'decode'

```

This post [https://itectec.com/ubuntu/ubuntu-first-full-backup-on-usb-permission-denied/](https://itectec.com/ubuntu/ubuntu-first-full-backup-on-usb-permission-denied/) says that Deja-Dup doesn't "play well" with sudo. It recommends
... sudo chmod -R a+rwX,o-w /media/aaaa
    ... sudo chown -R $USER:$USER /media/aaaa
Does that seem reasonable?

---

### Post by webmanoffesto on 2022-02-13
I'm in the middle of running it again. Using "--no-o --no-g"

I found, "The permission problem occurs whenever you don't have the permission to change file permissions on the destination of rsync. However, you can avoid this error message by using the two additional arguments --no-o and --no-g."
[https://unix.stackexchange.com/questions/12203/rsync-failed-to-set-permissions-on-error-with-rsync-a-or-p-option](https://unix.stackexchange.com/questions/12203/rsync-failed-to-set-permissions-on-error-with-rsync-a-or-p-option) 
And [https://serverfault.com/questions/364709/how-to-keep-rsync-from-chowning-transferred-files](https://serverfault.com/questions/364709/how-to-keep-rsync-from-chowning-transferred-files) 
I hope this helps.

---

