---
title: "The option to activate text files is very dangerous for my taste"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-23
i have a text file with many commands one wrong click and who knows what damage it might do i think that by default the behavior should be to open file not to ask every time or some other solution should be implemented.

---

### Post by jfernyhough on 2010-04-23
A file shouldn't be set executable by default; you have to set it (unless it's on a FAT/NTFS drive in which case changing the mount options would fix that).

You can change the prompt by Nautilus in the Nautilus settings (setting open by default, for example).

---

### Post by aviramof on 2010-04-23
i know i can change the prompt but you just finishe installing ubuntu you have more urgent things to do and yes i keep my files on my ntfs partition while i format my ext4 partition.
so like i said it's dangerous and i did have a problem with that in the past.

---

### Post by Longinus00 on 2010-04-23
Mount the disk with noexec.

---

### Post by cariboo on 2010-04-23
I put executable scripts in /usr/local/bin, there's no chance of accidentaly clicking a script unless you're in that specific directory.

---

### Post by powder on 2010-04-23
The problem is your files are losing their permissions when you copy them over to the NTFS partition.  When you copy them back over to the EXT partition they will all be marked as executable.  You should backup your files to an EXT volume so that this doesn't happen.

Otherwise, use this command to change the file permissions back to defaults.

find . ! -type d -exec chmod 644 {} \;

---

### Post by aviramof on 2010-04-23
yeah but when i install ubuntu i usually format the entire linux partitions or even erase them completly  i have only one ext4 partition and one for the swap and i backup all my 
files on my ntfs partitions before that.

---

### Post by SgtPepperKSU on 2010-04-23
> **aviramof said:**
> i backup all my files on my ntfs partitions

That's your problem right there.  That's a bad idea.  NTFS doesn't support file permissions or ownership flags.  You lose all of that as soon as you copy it to an NTFS partition.

If you're willing to live with the inherent consequences, using NTFS as backup for EXT4 is fine.  But, it seems you aren't happy with that (I wouldn't be either).

In short, don't do that. :smile:

---

### Post by aviramof on 2010-04-23
in short there is not much i can do about it ubuntu is not my only os i have windows 7 and windows server 2008 also installed here and i can't see my ext4 partition from any of them 
so backing up files on ext4 partition want work so well.

any case i just think that by default it should be set open files and not ask every time it safer like this for everyone.

---

### Post by SgtPepperKSU on 2010-04-23
Since there is no flag to indicate what can and can't be executed, the only alternative is not allowing anything at all on an NTFS partition to be executed.  You can accomplish that by mounting with noexec as has been mentioned.

---

### Post by wilee-nilee on 2010-04-23
(sarcasm)
You were given the reasons for your problems, and great solutions, back up the command list, or use a method as suggested. It is always a good chuckle when a OS doesn't do what a single person wants, even when given answers that will fix the problem. I wish my computer would have my coffee made and a cigarette lit for me when I get up. oh and and wash my delicates, but it will never happen. ;)

---

### Post by aviramof on 2010-04-23
ok that an idea the question is how can i do it from ubuntu or from the live cd when i install ubuntu?

the first part i can probably find for my self the second part might be more difficult if not impossible.

---

### Post by rifak on 2010-04-23
ahhhh, this has been puzzling me also for a week now. when i installed the beta, i copied all my old files onto a fat32 external, and when i transfered everything over, they were all executable. it all makes sense now. any reason for this?...like, is it a purposeful feature implemented? or just a byproduct of how different file systems transfer files?

edit: the previous post about ntfs not having file permissions answered my question.

---

### Post by BrokeMahPC on 2010-04-23
Interesting post by aviramof - he finds some stuff doesn't he?!!

This code:
> Otherwise, use this command to change the file permissions back to  defaults.
```
find . ! -type d -exec chmod 644 {} \;
```

Do you simply cd change to the directory with your ntfs contaminated files and run it or what?

---

### Post by Longinus00 on 2010-04-23
Why bother with find? Why not just use chmod -R a-x+X ?

---

### Post by forcecore on 2010-04-23
strange is that if files on Windows is set read only then coping to Ubuntu makes all copied files exec permission on by default

---

### Post by Didius Falco on 2010-04-23
For future upgrades/reinstalls, just make an EXT partition to use for backing up Ubuntu (or any other linux) stuff.

I barely trust Windows with Windows files - no way am I trusting it to keep my linux stuff safe.

---

### Post by aviramof on 2010-04-23
> **forcecore said:**
> strange is that if files on Windows is set read only then coping to Ubuntu makes all copied files exec permission on by default

that sound like something that should be looked at.

---

### Post by BrokeMahPC on 2010-04-23
Nice idea "chmod -R a-x+X ". Will that work on all files in the /home partition
I have some files in another storage partition that were moved from windows, how would you change them?

chmod
-R = recursively
a-x = all users, Deny execute permission
+X = Execute only if the file is a directory or already has execute permission for some user

---

### Post by Longinus00 on 2010-04-23
> **BrokeMahPC said:**
> Nice idea "chmod -R a-x+X ". Will that work on all files in the /home partition
I have some files in another storage partition that were moved from windows, how would you change them?

chmod
-R = recursively
a-x = all users, Deny execute permission
+X = Execute only if the file is a directory or already has execute permission for some user

chmod -R a-x+X /path/to/wherever ?

---

### Post by forcecore on 2010-04-23
test and you see, set files on Win to read only then copy to Ubuntu...

---

### Post by BrokeMahPC on 2010-04-23
> chmod -R a-x+X /path/to/wherever ?

thanks - worked perfectly

---

### Post by nystire on 2010-04-24
What may be better that simply copying your files is using Archive Manager or the command line to create a compressed file containing all the files you wish to backup/save. When you create the file, you can choose to save the current permissions (Read, Write, Execute). Then copy that one file to the Windows partition. After you install, you simply extract the files that you want from the archive and they should have the permissions that they had on your old install.

---

### Post by aviramof on 2010-04-24
that sound like a good idea i should try it next time but if the default ubuntu option would be to open text files and not ask every time it would have been much better.

---

### Post by Miguel on 2010-04-24
For the people doing backups in FAT32 and NTFS partitions, in case they want to preserve all the permissions and all that, they can, instead of copying all the files to the partition, create a tarball of the files they want to backup. As a bonus, you can compress your data.

---

