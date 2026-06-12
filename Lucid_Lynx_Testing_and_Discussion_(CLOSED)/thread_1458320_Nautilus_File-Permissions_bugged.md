---
title: "Nautilus File-Permissions bugged"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lolpanda on 2010-04-19
I've got wine installed, copied a game folder over from a Windows 7 partition. When I went in to change the permission so the game could auto-update files, by giving myself Read-Write permissions, as well as Create-Delete. Before I even hit "Apply permissions to all subfolders" The dropbox containing "Read, Read-Write, ---- " switched from "read-Write" back to the default  " --- " 

Didn't matter how many times i tried to change it, I even ran Nautilus with gksudo rights, and it still automatically changed back before I hit Apply

This a known issue / Fixable issue? Tried a Google and forum search and came back with no results

---

### Post by powder on 2010-04-19
I usually use the command line to change the permissions on files copied over from FAT32 or NTFS volumes.  Just cd to the game directory and issue the command below.

find . ! -type d -exec chmod 644 {} \;

If there are multiple directories within the game folder you can use this command.

find . -type d -exec chmod 755 {} \;

---

### Post by QwUo173Hy on 2010-04-20
Lolpanda, I remember experiencing this in the past and it seems to happen only under certain conditions - eg, when you are not the owner of the file.

If you try to use nautilus to change the permissions of a new text file for example, I'll bet you have no problems. I think this is worth reporting - but at the time I didn't know enough to describe the problem.

If you could compare the permissions and ownership of a newly made text file, for example, with the files from your windows system, could you tell me the differences?

---

### Post by Lolpanda on 2010-04-20
> **powder said:**
> I usually use the command line to change the permissions on files copied over from FAT32 or NTFS volumes.  Just cd to the game directory and issue the command below.

find . ! -type d -exec chmod 644 {} \;

If there are multiple directories within the game folder you can use this command.

find . -type d -exec chmod 755 {} \;



Just to clarify this Powder, did

```
cd ~/.wine/dosdevices/c:/  
```That put me on basically Drive C in windows, giving  me access to Program Files, Windows, Temp everything, you said to run 


```
find . -type d -exec chmod 755 {} \;
```to cover all directories and subdirectories. 

Just to double check it, went back into my fake C drive, and brought up properties on a folder, permissions are the same as before. (Btw I AM the owner, supposedly, on the folder im trying to change.) 

If I missed something, or you assumed something, apologies from me lol. I'm used to command line for a lot, chmod isn't one I've had to use often though lol



> **jarlath said:**
> 
If you could compare the permissions and ownership of a newly made text  file, for example, with the files from your windows system, could you  tell me the differences?


I could change the permissions on a folder I JUST created myself, and on a .txt document inside of that folder, but on a hunch I went and tried to edit permissions on some folders I copied over from outside my Wine folder but still from Linux (was a torrent from a friend so it came from ~/Downloads)

And THOSE permissions also auto-change. 

On ANOTHER hunch, I checked to see who was the owner of .wine and /dosdevices/c:/ and I'm the owner of both. Going to Properties ~> Permissions on both of those folders, those permissions aren't bugged.

---

### Post by powder on 2010-04-23
The command you ran only affects the permissions for directories.  You need to run the other command for actual files.

---

