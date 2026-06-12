---
title: "trash does not work in ubuntu on chromebook"
date: 2023-01-13
forum: Installation &amp; Upgrades
---

### Post by srope01 on 2023-01-13
I am running ubuntu on an old (2014) Toshiba CB30 chromebook using crouton. I booted with the default (xfce xenial). In general I am pretty happy that with linux I can get extra mileage on a nearly useless chromebook. The problem is that the trash bin does not work. As I put stuff in the trash, the files seemingly disappear even without emptying the trash. But the trashed files remains somewhere as I can see that my home directory shows less space. A clip from df below. I started about 7.9 GB of available space and it has dropped to 1.4 GB after trashing several large files. Eventually I had no space left and I had to start all over after a powerwash.

Anyone has any idea on how to make the trash bin to work

> [FONT=Arial]localhost:~$ df -H[/FONT]
[FONT=Arial]Filesystem                                                    Size  Used Avail Use% Mounted on[/FONT]
[FONT=Arial]/dev/sda1                                                      12G  9.5G  1.4G  88% /[/FONT]


silverrope

---

### Post by ActionParsnip on 2023-01-13
Could try trash-cli

---

### Post by srope01 on 2023-01-13
> **ActionParsnip said:**
> Could try trash-cli

I installed trash-cli and although this did not solve the problem, it gave some further info. I downloaded a big file and I used trash-put. The file disappeared but df showed that it was still somewhere on the drive. Then with trash-list, I got the following:

```
trash-list
TrashDir skipped because parent not sticky: /home/user/Downloads/.Trash/1000
```

The big file was still in that directory. So neither the gui version of trash nor the trash cli works.

 Well, I will just manually rm on the command line each time. Not great, but I can live with this as the chromebook is only a spare computer. I guess getting a truly working version of ubuntu on a chromebook is impossible. Thanks for the suggestion anyway.

---

### Post by Impavidus on 2023-01-13
You mentioned xfce xenial. xfce is part of Xubuntu, not Ubuntu, so it only has 3 years of support. Xenial was 16.04, so that's almost 7 years old and well past end of life.

---

### Post by srope01 on 2023-01-13
> **Impavidus said:**
> You mentioned xfce xenial. xfce is part of Xubuntu, not Ubuntu, so it only has 3 years of support. Xenial was 16.04, so that's almost 7 years old and well past end of life.

True, but xenial is the default and only supported version that works with crouton. Unsupported versions of bionic, focal, and jammy are available, but unfortunately they crash while being installed in my chromebook. I looked at mrchromebox but given what one has to do get past hardware security plus the firmware updates, I don''t really want to risk ending up with a brick after the time and effort. Crouton isn't great, but it's fairly easy and safe and I can live with rm on the command line and old unsupported apps. I guess the chromebook community is not large enough to get volunteers to help support crouton.

---

### Post by guiverc on 2023-01-13
Ubuntu 16.04 LTS has ended it's *standard support cycle*.

It was released in 2016-April (thus is 16.04) with 5 years of support, which ended in April 2021.

I suggest reading [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/) or other notices, including [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm)

Xfce/Xubuntu had ended it's support earlier (3 years or 2019-April) as already outlined, but *xenial* or 16.04 is EOSS.

Have you *enabled* ESM to continue getting security upgrades?   Don't forget many original *deb* packages only gets fixes now if converted to *snap* packages with 16.04; ie. did you read the notices issues on switching from EOSS to ESM (eg. [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04) etc)

---

### Post by srope01 on 2023-01-13
Yes, I know about the end of support of 16.04. But with old chromebooks, it seems the only safe way to install ubuntu is through crouton and that is only community-supported. And unfortunately, 18.04, 20.04, and 22.04 are unsupported within crouton (and they crash when I try to install them on my chromebook). That's ok, I can live with 16.04.

---

### Post by srope01 on 2023-01-14
Good news. Following up on ubuntu on chromebooks using crouton, surprisingly, I was able to upgrade from 16.04 to 18.04 bionic! I thought that it would not be possible to reboot into the same environment after running the upgrade scripts but yes, when I restarted, the 18.04 upgrade was retained. It isn't robust because once you lose the crouton environment, one would have to restart all over again with xenial, But in principle, one should be able to upgrade even further possibly to jammy.

I post this here in case any chromebook owner was wondering how to upgrade within crouton.

---

### Post by srope01 on 2023-01-18
Following up on this thread, I have now run into the same problem of the trash bin not working but this time in the new upgrade installation of 18.04 bionic. Whenever a file on the home directory is trashed, it disappears and goes somewhere taking up space. This time however it is no longer placed in the**[FONT=courier new] .trash[/FONT]** directory but it goes somewhere and I cannot find it to **[FONT=courier new]rm[/FONT]** it. The strange thing is if I trash a file that is on the removable media drive (SD card /dev/sdb1 mounted on /media/removable/), then that file gets properly removed.

Does anyone know of possible directories where the supposedly trashed file could be placed?

---

### Post by TheFu on 2023-01-18
> **srope01 said:**
>  The big file was still in that directory. So neither the gui version of trash nor the trash cli works.

Understand that "trash" isn't supposed to actually delete files.  It moves them to a temporary location on the same file system where they are eventually removed.  Drives me nuts.  I hate the entire idea of "trash" and when I say to delete a file, I expect it to be gone, immediately.  If I need it back, that's why backups exist.

Nightly, during my pre-backup processing, I clear the expected trash locations.  This is the command I'm using:
```
        if [[ -f /usr/bin/gio ]] ; then
           echo "INFO: Empty GIO trash"
           /usr/bin/gio trash --empty
        fi

```
From the gio manpage:
```
       trash [OPTION...] [LOCATION...]
           Sends files or directories to the "Trashcan". This can be a different folder
           depending on where the file is located, and not all file systems support this
           concept. In the common case that the file lives inside a users home directory, the
           trash folder is $XDG_DATA_HOME/Trash.

           [b]Note that moving files to the trash does not free up space on the file system until
           the "Trashcan" is emptied. If you are interested in deleting a file irreversibly, see
           the remove command.[/b]

           Inspecting and emptying the "Trashcan" is normally supported by graphical file
           managers such as nautilus, but you can also see the trash with the command: gio list
           trash://.

           Options
               -f, --force
                   Ignore non-existent and non-deletable files.

               --empty
                   Empty the trash.

```

The manpage is full of ideas and different releases will have different locations for trash placement.  The key is that trash doesn't cross file systems, so if you have multiple partitions, trash won't cross that boundary.

You can use 'find' to locate files.  'find' is on of the commands where the manpage isn't clear without checking out 20-100 examples.  Luckily, there are "Top 20 Find Command Examples" webpages. Or use explainshell.com

---

### Post by srope01 on 2023-01-18
> **TheFu said:**
> 
You can use 'find' to locate files.  'find' is on of the commands where the manpage isn't clear without checking out 20-100 examples.  Luckily, there are "Top 20 Find Command Examples" webpages. Or use explainshell.com

Yes, I was thinking that using "find" would be the solution of last resort. I was hoping that someone knew what is the default location that the Trash bin would send the file for my installation. I am running release Ubuntu 18.04.6 LTS, xfce version 4.12 desktop environment. The GUI file app with the Trash icon is Thunar. I think the directory is supposed to be in the home directory under **.local/share/Trash** but looking there it doesn't exist. So the trashed file must be going somewhere else. Well, I might have to use "find" in the end.

---

### Post by #&amp;thj^% on 2023-01-18
My effort to help:
```
cd ~/.local/share/Trash


me on Wed Jan 18 at 02:38 PM in ~/.local/share/Trash branch: (HEAD) 
>> ls
files  info

```
Just now move a folder to Trash, found in "files" 
```
cd files && ls
Walls

```
Removed with:
```
rm -rf ~/.local/share/Trash/files/Walls


me on Wed Jan 18 at 02:52 PM in ~/.local/share/Trash/files branch: (HEAD) 
>> ls


```

---

### Post by TheFu on 2023-01-18
Ubuntu 18.04.6 LTS, xfce support ended 2 yrs ago.

As I said before, Trash is dependent on the file system and will not move across file systems. As I don't have 18.04 XFCE, I can't look where it puts the trash.  Usually, there is a directory named .Trash/ at the top level of the file system or somewhere in the user's HOME.  Search case insensitive to fine it.  I like to use 'locate -i', but this requires that the locate index has been recently built.

```

$ locate -i .Trash
/TV/.Trash-1000
/d/D1/.Trash-1000
/d/D2/.Trash-1000
/d/D3/.Trash-1000
/d/b-D1/.Trash-1000
/d/b-D3/.Trash-1000

```
Each of those locations is a different file system.

I'm guessing the "1000" is a mapping to the uid.  So, if I use the GUI to delete anything under /d/D2/ ... it is moved under /d/D2/.Trash-1000/ somewhere.
Knowing how to 'find' things is a basic skill.  [https://www.cyberithub.com/find-command-in-linux/](https://www.cyberithub.com/find-command-in-linux/) has lots of examples.  #26 is probably what you want.

---

### Post by srope01 on 2023-01-18
> **TheFu said:**
> Ubuntu 18.04.6 LTS, xfce support ended 2 yrs ago.

...

Knowing how to 'find' things is a basic skill.  [https://www.cyberithub.com/find-command-in-linux/](https://www.cyberithub.com/find-command-in-linux/) has lots of examples.  #26 is probably what you want.

I thought 18.04 end-of-support date wasn't until April but I now see that is only for gnome. OK, so I will soon upgrade to 20.04, although I suspect the missing trashed files problem will still be there. But in the meantime, while I am still on 18.04, I will use "find". Many thanks for the examples.

---

### Post by guiverc on 2023-01-18
> **srope01 said:**
> I thought 18.04 end-of-support date wasn't until April but I now see that is only for gnome. OK, so I will soon upgrade to 20.04, although I suspect the missing trashed files problem will still be there.

Don't forget Xfce or Xubuntu support on 20.04 ends in April 2023; three years after it's release in 2020-April.

Refer [https://fridge.ubuntu.com/2022/09/01/ubuntu-20-04-5-lts-released/](https://fridge.ubuntu.com/2022/09/01/ubuntu-20-04-5-lts-released/) which states

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. All the remaining flavours  will be supported for 3 years. Additional security support is available  with ESM (Extended Security Maintenance).

Xfce is a *flavor* support; ie. 3 years of support from initial release.  GNOME is supported on 20.04 until 2025-April.

Note:  It's still possible for *reported bugs* to be fixed after the initial 3 years of support (ie. during the 5 years that the repositories are open for main Ubuntu Desktop/Server/..), as any MOTU can file SRU fixes & submit them for 20.04 until 2025-April, but there is no guarantee of this after 2023-April for packages found in 'universe' (ie. community supported packages as used by *flavors* like Xubuntu)

---

### Post by TheFu on 2023-01-18
After 3 yrs, basically, only security stuff gets fixed, not features.  For as many people as want a behavior, there's that many that have counted on the current behavior.  That's the point of LTS releases - NO NEW FUNCTIONALITY or changes to existing functionality.  Businesses count on this.

---

