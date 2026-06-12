---
title: "Get rid of desktop folders?"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-04-15
Not sure if this is actually particular to Lucid but I can't for the life of me work out how to stop folders in my home directory showing on the desktop.

I'm used to having ONLY mounted volumes show on the desktop and nothing else so it's looking very messy, especially now I have all my music, video photos folders etc.

---

### Post by mc4man on 2010-04-15
Look in gconf-editor - /apps/nautilus/preferences and make sure desktop_is_home_dir is not enabled.

or may something like this
```
gconftool-2 --set /apps/nautilus/preferences/desktop_is_home_dir --type boolean false
```

---

### Post by ajgreeny on 2010-04-15
Which folders show on your desktop that you don't want?  The only ones I have are **home** and **computer**, because I choose to have them, but they can easily be removed by using *gconf-editor ->apps ->nautilus ->desktop* and removing the selections from the appropriate buttons.

---

### Post by x-shaney-x on 2010-04-15
It isn't just the standard Home, Computer etc, it is showing ALL non-hidden directories on the desktop.

For example, I installed banshee and it created new folders in my home directory and they instantly appeared on the desktop.
I created a link to Downloads (downloads, with a lower case "D") and that appeared on the dekstop. 

@ mc4man
That option is already unchecked, although the behaviour is exactly as if it wasn't.
Though it is ONLY showing folders and not files/documents etc.

---

### Post by mc4man on 2010-04-15
I don't see any straightfoward way to show only the home dir.'s on the desktop - files are also shown. I guess you could take a look at this file and see if anything is amiss (doubtful



> doug@doug-laptop:~$ cat ~/.config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"


---

### Post by x-shaney-x on 2010-04-15
Turns out it is also showing non-directories.  All the other files were hidden files, I created a text doc and it showed up on the desktop instantly.

Also, when I go to Menubar > Places > Desktop
It opens my home directory in nautilus :|  I have double checked and that option in gconf about desktop as home directory is DEFINITELY unchecked.

@ mc4man

Something was certainly amiss with that file, on mine it simply showed "$HOME/" for each entry.
I corrected it and replaced all entries with the ones you listed and after rebooting it kept all the entries except the XDG_DESKTOP_DIR one, which has switched back to "$HOME/" instead of "$HOME/Desktop" and I still have all the icons on desktop.

Odd, very odd.

---

### Post by andrewabc on 2010-04-15
Is this a new feature in 10.04?

I don't remember ever having my /home directory non hidden folders ever showing up on desktop. Only mounted filesystems.

---

### Post by mc4man on 2010-04-15
Maybe try deleting that problem line, running this and a restart

```
xdg-user-dirs-update
```

Otherwise you may need to dig a little deeper - with that line @ 
"$HOME/" you will see your home (dir.'s and files) on desktop

---

### Post by Starks on 2010-04-15
> **Chauncellor said:**
> For a nice GUI that will change that, search the repos for Ubuntu Tweak. There's an option in there to get rid of them.
Seconding that. I did it once and was horrified by the result.

---

### Post by mc4man on 2010-04-15
May also be worth taking a look here


> doug@doug-laptop:~$ cat /etc/xdg/user-dirs.defaults
# Default settings for user directories
#
# The values are relative pathnames from the home directory and
# will be translated on a per-path-element basis into the users locale
DESKTOP=Desktop
DOWNLOAD=Downloads
TEMPLATES=Templates
PUBLICSHARE=Public
DOCUMENTS=Documents
MUSIC=Music
PICTURES=Pictures
VIDEOS=Videos
# Another alternative is:
#MUSIC=Documents/Music
#PICTURES=Documents/Pictures
#VIDEOS=Documents/Videos


---

### Post by x-shaney-x on 2010-04-15
Problem solved-ish.  I say ish because I still don't know what caused it.

On closer inspection of my desktop and home directory, I noticed some of the folders listed in the user-dirs.dirs that mc4man posted were missing (Desktop, Pictures, Documents and Public).

So I manually created these folders, ran xdg-user-dirs-update and all the folders on the desktop vanished :)  presumably because the "Desktop" folder now exists.

After a reboot everything is still working as it should.
Can't work out why the folders were missing since I certainly haven't deleted them but all is well now.

Thanks for the help and suggestions.

I've still got that annoying "Blank CD-ROM Disc" icon on the desktop that won't go away though :(

---

