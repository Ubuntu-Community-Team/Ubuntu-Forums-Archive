---
title: "[SOLVED] How To Make Automatic Backup To USB Hard Drive?"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-24
I'm using Intrepid and I bought a 500GB external hard drive so that I can store backups on it. Back in Hardy, I used to use Unity to synchronize data between my desktop and laptop and that worked nicely. I tried to install Unity on Intrepid, but it's nowhere to be found. (Maybe it requires a certain repository)?

Anyway what I liked about Unity was that if I deleted a file, it was synced. If I changed a file, it was synced. If I created a new file, it was synced. I was thinking that Unity would be a great solution to backup to my external hard drive but it's gone.

What do you guys suggest for this? I'd like my Home directory to be syncronized to my external hard drive whenever I run a script or something. That way if my computer blows up I'll have some sort of backup.

---

### Post by Seren on 2008-09-24
There is a tool called **rsync **which has only a command line interface.

I have never used it myself, but I have seen references on the ubuntu forums. It looks rather powerful.

There are plenty of tutorial on Internet about this tool.

[http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html)

from the link :
> 
Rsync is a fast and extraordinarily versatile file copying tool. It can copy locally, to/from another host over any remote shell, or to/from a remote rsync daemon,...

...

Rsync finds files that need to be transferred using a "quick check" algorithm (by default) that looks for files that have changed in size or in last-modified time. Any changes in the other preserved attributes (as requested by options) are made on the destination file directly when the quick check indicates that the file's data does not need to be updated. 

...


---

### Post by [Neurotic] on 2008-09-24
I use Simple Backup and Restore, which is as pretty basic utility which will do timed backup, both full and incremental.

---

### Post by Gina on 2008-09-24
I've used rsync to update ISOs but not yet tried it for backups.  Looks like it should work for that too.  I just use drag-n-drop copying for backing up ATM but a backup app or script would be more efficient, of course.

---

### Post by beercz on 2008-09-24
[http://rsnapshot.org](http://rsnapshot.org)

---

### Post by ntetreau on 2008-09-24
I'm using rnapshot as well, so far so good... although I wish it could recognize when I'm pluging in the USB drive and start rsnapshot automatically (or better yet, popup and ask me if I want to backup now!)



> **beercz said:**
> [http://rsnapshot.org](http://rsnapshot.org)

---

### Post by rogerdean on 2008-09-24
Very flexible and simpler than it sounds, I made a little script to back up my stuff...

cd /media/Shared
#switches to my second hard drive

rm backup.tar.gz
#deletes the previous backup

tar -pczvf backup.tar.gz /home/roger/Desktop /home/roger/Documents /home/roger/Pictures /home/roger/Podcasts /home/roger/Techie /home/roger/Work /home/roger/.fonts /home/roger/.googleearth /home/roger/.gtodo /home/roger/.mozilla /home/roger/.mozilla-thunderbird /home/roger/.openoffice.org2 /home/roger/.Skype /home/roger/.tomboy
#zips up the directories i need

---

### Post by jlacroix on 2008-09-24
I don't prefer rsync all that much. I miss Unity. Is it really gone in Intrepid or am I just typing a wrong command? Theoretically, it could be used to back up to an external hard drive, correct?

---

### Post by olskar on 2008-09-24
Unison!:)

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

Think its in the repos

---

### Post by reh4c on 2008-09-24
I think the conduit package may be a good option to perform backups.

---

### Post by jlacroix on 2008-09-24
> **olskar said:**
> Unison!:)

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

Think its in the repos

Thank you!!! Why the heck was I calling it Unity? LOL!

Here is my unison script that works with syncing my laptop and desktop. What changes would I make in making it back up to my external hard drive that is attached to the same computer?

```
### ROOT SYNC PATHS ###
 
# first root is my home directory on this laptop
root = /home/jeremy/
 
# second directory is my desktop's home folder over SSH
root = ssh://jeremy@192.168.2.50//home/jeremy/

log = true
logfile = /home/jeremy/.unison/unison.log

follow = Name *

### PATHS TO SYNCHRONIZE ###
 
# gaim/pidgin IM client logs and settings
path = .purple/

# Personal folders
path = Shared/
path = Documents/
path = Pictures/
path = Videos/
path = Music/
path = Roms/
#path = .zsnes/
path = Themes/
 
### IGNORE RULES ###


```

---

### Post by Seq on 2008-09-24
tee hee!

EDIT: Edit :-\"

---

### Post by jlacroix on 2008-09-24
> **Seq said:**
> tee hee!

Whoops! *Edited*

8-[

---

### Post by Johnsie on 2008-09-24
Is there anything for Ubuntu that can do subfolders recursively? I would like something like this to back up my /htdocs and any sub-folder contained in htdocs in case my server ever breaks down.

---

### Post by jlacroix on 2008-09-24
I think I got this figured out. :) Thanks guys.

---

### Post by beercz on 2008-09-25
> **Johnsie said:**
> Is there anything for Ubuntu that can do subfolders recursively? I would like something like this to back up my /htdocs and any sub-folder contained in htdocs in case my server ever breaks down.
I was going to suggest rsync

---

### Post by jethro10 on 2008-09-25
> **jlacroix said:**
> I think I got this figured out. :) Thanks guys.

Could you tell us how, just incase it helps others? (like me!)

Ta
J

---

