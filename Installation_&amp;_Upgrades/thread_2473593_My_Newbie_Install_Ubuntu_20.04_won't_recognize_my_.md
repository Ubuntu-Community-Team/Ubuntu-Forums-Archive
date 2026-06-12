---
title: "My Newbie Install Ubuntu 20.04 won't recognize my files"
date: 2022-04-07
forum: Installation &amp; Upgrades
---

### Post by Iatros on 2022-04-07
Just completed my first install of Ubuntu 20.04 in place of Windows 11 and I am seeing a puzzling problem:  the OS won't show many of my files, especially 'app' files.  I assume the problem is the permissions of the file.  When I do 'ls -la' most files have drwx across the line, so what permission is missing?  Is there a way to do a global 'chmod' to stop the OS from preventing my seeing the files??  I also wondered if I could change my path or $PATH to alleviate part of the problem.

---

### Post by ActionParsnip on 2022-04-08
Are you trying to access an NTFS partition or something? What are these "files"? Can you please give some details

---

### Post by Impavidus on 2022-04-08
If a line of output of ls -al starts with drwx, it's a directory where the owner has full permissions. Usually the owner has so.

What do you mean by "'app' files"?

If you just installed Ubuntu, you won't find any of your files on Ubuntu's root partition, or its home partition, if you created one. You'll only find some default files. Your files will still be on a Windows partition (assuming you kept it), which you should be able to find in your file manager, but it may be a bit difficult to access if fast startup was still enabled in Windows. Furthermore, your files should be on your backup drive, where you can find them when you plug it in.

So where exactly do you try to access your files?

---

### Post by yancek on 2022-04-08
> Is there a way to do a global 'chmod' 

Yes and that is the simplest way to completly, unrecoverably DESTROY the OS completely.  More info asked for above is required.

---

### Post by ActionParsnip on 2022-04-08
I think you should just use plain language and state what you are trying to achieve / do

---

### Post by TheFu on 2022-04-08
> **Iatros said:**
> Just completed my first install of Ubuntu 20.04 in place of Windows 11 and I am seeing a puzzling problem:  the OS won't show many of my files, especially 'app' files.
What is an 'app' file?  Where are you looking?  All Unix-like OSes use directories and paths to denote where a file is located.  It doesn't have drive letters ... actually, MS-Windows doesn't really have drive letters, since even Windows doesn't mount a drive, it mounts a partition with a file system, just like every Unix-like OS does.  

> **Iatros said:**
>   I assume the problem is the permissions of the file.  When I do 'ls -la' most files have drwx across the line, so what permission is missing? 
I wouldn't assume anything yet.  
```
$ ls -la 
```
isn't useful without knowing the pwd - present working directory.  I.e., which directory is the shell running inside?  
pwd will provide that answer, so will showing the full command line and output with:
```
ls -al
```
assuming you haven't changed the default prompt or shell.  Please help us out. Don't make us guess.

> **Iatros said:**
>    Is there a way to do a global 'chmod' to stop the OS from preventing my seeing the files??  
Yes. You can, but it is a terrible idea and likely won't achieve what you really want. There are many areas of the file system that should not be available for view, much less write, by normal users.  As others said above, doing a global chmod is one of the quickest ways to trashing a Unix OS and will require a re-install to get it working again.  But if you really want to do it, I'm happy to provide the command if you ask 2 more times.  But you've been warned.

> **Iatros said:**
>   I also wondered if I could change my path or $PATH to alleviate part of the problem.
the $PATH environment variable works the same on Unix as it does on Windows. I doubt it will help at all.
You can use the **cd** command to change directory as you like.  Most 'newbies' would likely prefer to use a file manager application, however.  I don't use file managers very often, but I've been at this over 25 yrs and know nearly all the shell tricks to move around very fast in a directory structure.  For me, file managers are too slow.  Of course, if you installed Ubuntu Server, then you don't have any GUI and are likely staring at a **xxxxxx@yyy:~$** prompt.  That prompt is full of information.
The xxxxx is your current username.
The yyy is the current hostname.
the ~ is your cwd/pwd.  Always good to know.
and the 
$ says you are using a normal userid, not root.  If it was root, then you'd see a '#' instead.  That is a universal standard.

So, if my prompt is "thefu@istar:~/TV$"
what does that say?

BTW, in a different terminal window, my prompt is: "thefu@hadar:/TV/Recordings$"
What does that say?

---

### Post by Iatros on 2022-04-08
Well, if ignorance is bliss, I should be very blissful right now.  OK here is what I am doing.  I have done a full install of Ubuntu on a machine that I formerly used for Windows 10, then 11.  The system disk is an 1 TB SSD that seems to be in good shape.  Ubuntu 20.04 is on the first part of the SSD (I don't see a partition on it).  With Ubuntu up and running, I am trying to install some of my favorite programs, which I incorrectly called Apps when I downloaded them from the Ubuntu store.  Most I have downloaded from websites of the various companies I use.  Among these would be PyCharm, IntelliJ IDEA, LibreOffice, and such.  All were downloaded in compressed formats.  Large files were in tar.gz formats, others were packaged.  Initially I had a lot of trouble mastering the cd, mv, ls and other simple commands because many of the files that I know were downloaded into my /Downloads/ directory did not show up with the mv command (my idea was to create a dir for each of the large programs and extract them in that dir.  My initial question on this forum was how to keep those files visible.  I assumed I have a problem with permissions as well as the path.  Does this explain enough for you guys to understand?

---

### Post by Iatros on 2022-04-08
I may see one problem:  my prompt in Terminal lists my  username @machine name , then a colon: BUT then the root tilde ~$.  Is this incorrect?

---

### Post by Iatros on 2022-04-08
I erased all Windows partitions before the Ubuntu installation.  I wanted a clean install.  The downloads are placed in ~/username/Downloads/ and I want to move the large, frequently used files to each's own directory to unpack. So PyCharm would wind up in its own  directory /user/pycharm/ and so forth.

---

### Post by ubfan1 on 2022-04-08
Sounds like your files should be in the Downloads directory.  Look there from the "Files"  app on the launchbar on the left.  Permissions should be correct on files you download, so something else may be the problem -- for instance, you are not typing the names with the correct case.  Windows may not be case sensitive for filenames, but Linux ext4 (and most others) is.  Check first for things like LibreOffice being in the standard repos instead of grabbing a tar file.  sudo apt-get install libreoffice   should install in a system location, and will get updates along with other things.

---

### Post by TheFu on 2022-04-08
Ok, I'll try to split this 1 at a time.  Please forgive me if I go too technical. I've been a Unix admin nearly 30 yrs. I used to be a cross-platform programmer, including Windows, but I find MSFT extremely frustrating and only boot into a Windows VM for about 15 minutes each week to update finance records. I've never seen Win8 or later.

> **Iatros said:**
> Well, if ignorance is bliss, I should be very blissful right now.  OK here is what I am doing.  I have done a full install of Ubuntu on a machine that I formerly used for Windows 10, then 11.  
Which flavor of Ubuntu? A flavor typically has a specific DE.  Gnome3, Mate, LXQt, KDE, there are probably 10 others.
Also, which version?  20.04 is what someone brand new to Ubuntu should install today.  In June, you should migrate to 22.04 and keep that for the next 2 yrs until 24.04 + a few months.  These are all LTS releases.
All the other releases are beta and where Canonical tries new stuff - sometimes it is great new stuff and other times it really sucks or is just a little too early for mass use.  Stay with official LTS releases (even years, April) and you'll avoid most dumb bugs.

> **Iatros said:**
> The system disk is an 1 TB SSD that seems to be in good shape.  Ubuntu 20.04 is on the first part of the SSD (I don't see a partition on it).   
There are always partitions. Always.  To see the disk layout, use
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
I have an alias for that command so I don't have to type all those options over and over.
When providing data here, please ... er ... don't that this the wrong way ... but I want to see proof to back up any statement.  Proof is provided by running a command that shows whatever you are claiming.  So, to show the disk layout, there are a few different command which can do it, but that lsblk command above is probably the best.  Also, whenever posting terminal stuff, 
a) always show the command
b) always show the relevant output. If the output is less than 30 lines, show it all. Otherwise, remove the junk.
c) always post in these forums using 'code tags' - The advanced editor has a # button. That's a code wrap feature which works just like bold, underline, quote ... sometimes I don't bother with the advanced editor and just use one of those others, but change the vbulletin code from quote-->code. That works too.

> **Iatros said:**
> With Ubuntu up and running, I am trying to install some of my favorite programs, which I incorrectly called Apps when I downloaded them from the Ubuntu store.  Most I have downloaded from websites of the various companies I use. 
Apps are for phones and tablets.  OSes have applications. ;)  Downloading programs outside the package manager is a bad idea for someone new. That will lead to dependency hell in a few months.  You probably will ignore me. I did when I was new to package management and thought I needed the latest version of everything. That just isn't true.
There are a few different package formats.  Canonical has been pushing something called "snap packages" for about 2 yrs.  These are highly constrained - like mini-Linux containers and don't allow the program to interact with other programs or access storage outside your HOME directory.  If you run **snap list**, you'll see the installed snap package on a system.  None are mandated in 20.04 or on Ubuntu Server.  Snaps are Canonical's version of a flatpak, which is what Redhat and others have gotten behind.  There are pros and cons to each.  Eventually, you'll be burned by a program in a snap preventing you from doing something you want. Then, you'll need to learn more or just remove the snap package and find a normal, Debian/Ubuntu version of that package. Then any constraints applied are your choice --- or none.
In short, don't download any programs outside the package manage. And if you want to avoid snap, then use a package management front-end that doesn't try to trick you into installing snaps like the default Ubuntu Store does.  You can use apt, aptitude, Synaptic ... all of those won't show a list of packages that aren't standard, old-school, debian files from Canonical's repos. If you manually download a .deb file and install it, you've likely just broke some APT dependencies. The issues will start slowly at first, but grow until you have a system that cannot be patched and is a security nightmare. By that point, you'll have forgotten the 20 manually installed packages and your system will be unmaintained for a few months - available to be hacked.

> **Iatros said:**
>   Among these would be PyCharm, IntelliJ IDEA, LibreOffice, and such.  All were downloaded in compressed formats.  Large files were in tar.gz formats, others were packaged.   
LibreOffice is in the repos. Use that version, or setup a PPA from the libreoffice project team. I don't know much about the others. I don't do Python or Java.  My systems only have 32G of RAM, so java development isn't possible - I'm joking ... er ... sorta. Java is a hog.  I do perl these days, but did C/C++ for 15 yrs professionally.
Files as tgz/tar.gz with programs/libraries are a bad idea. Programmers should be using a version control system like git if they are modifying the code. Otherwise, they should be using either the packaged version or a PPA or for something like Python, use the normal python module management virtual environment solution.  Keep this in mind. NEVER change the python on your Linux system for a different release in a way that changes which version the OS sees.  It is fine to have multiple python version inside different virtual environments controlled by your userid, but leave the OS python alone.  Changing it will break the OS and likely prevent it from booting.

> **Iatros said:**
> Initially I had a lot of trouble mastering the cd, mv, ls and other simple commands because many of the files that I know were downloaded into my /Downloads/ directory did not show up with the mv command (my idea was to create a dir for each of the large programs and extract them in that dir. 
See above. Don't download code.  Beginners shouldn't really need to use the terminal.  Programmers should learn to become power-users of the shell.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good introduction, with concepts and commands provided in the correct order. This will make for the quickest learning possible.

> **Iatros said:**
>   My initial question on this forum was how to keep those files visible.  I assumed I have a problem with permissions as well as the path.  Does this explain enough for you guys to understand?
They aren't invisible.  They are just in a directory.  The Gnome DE doesn't allow files on the desktop, if that was your hope.  Linux isn't Windows.  There are other DEs which do allow files on the desktop.  In general, I think that's a bad idea, but it is your machine.

Something to consider is that the GUI you interact with is just a program. Nothing special. There are 20 popular GUIs, so you can try different ones out, see which you like.  There are some important caveats to mixing DEs/GUIs using the same userid. I'll leave that until you specifically ask.

That's probably enough for this weekend. ;)

---

### Post by TheFu on 2022-04-08
~[COLOR="#FF0000"]/[/COLOR]username/Downloads
isn't a valid location.
~username/Downloads is.
Or if it is the current userid, 
~/Downloads

Details matter.  Hopefully, you are using tab completion 90% of the time, so that incorrect locations cause a beep.

---

### Post by yancek on 2022-04-09
As mentioned above, you should always check the Ubuntu repositories by using the Software Manager or the apt program to install software before going to 3rd party sites.  The software in the repositories is tested to work on the release.  If you need a newer version it may be available on the creator web site and the installation method will be different.

I'm not sure what the problem is with the software, you seem to indicate you are downloading software and it does not show in your user Downloads directory, is that the case?  If you want each program in its own directory, you should just use the mkdir command to create the directory under the /home/username directory.  Does that not work for some reason?

>   BUT then the root tilde ~$.  Is this incorrect? 		   


The '$' means you are logged in as a normal user, if the '$' is replaced by a '#', it means you have root permissions which are often needed to install software.

---

### Post by TheFu on 2022-04-09
~ is short for $HOME, not root (/).
Also, the root account has a HOME in /root/.  So the root directory is / and root's HOME directory is /root.  Now, we can also say root's HOME directory is ~root/, just like we can say Pete's HOME is ~pete.

Tab completion works with each of these.  The HOME directory for each account is a lookup in the local or remote password database.  On a system with only local accounts, that is the /etc/passwd file.  It is just text. Take a look at it.  It is made of : separated fields and 1 of those fields is the HOME for the username.

user == username == pete (should always be lowercase).
userid == uid== 1000 (a number)  
group == groupname == users  (ubuntu usually created a groupname that matches the username). I've never understood why. 
groupid ==gid == 1022 (a number)

To see the uid and gid, type '**id**'. That command has options to get just the userid, username, groupids or groupnames too. Being a member of multiple groups is very common, but when a process is running, it has 1 'effective' userid and 1 'effective' groupid.  Those attributes determine which files and directories can be accessed, read, written, used.

File permissions are THE core part of all Unix security.  Learn those by sitting down for 45 minutes, working through a tutorial, then setup 3 users with mixed and different matched groups and create a play directory structure under /tmp/foo. Open 3 terminal windows, 1 for each user, then start creating directories and files.  Then see which can be accessed by the other users. Try almost every combination of rwx on both directories and files. See how each user can and cannot access the files. Play with that until things click. Then spend 15 more minutes testing your new beliefs, finding flaws, until a full understanding is gained.  This 45 minutes will save you hours, days, weeks, months of frustration.  You'll learn 90% of what you need to know about permissions and the elegance of the solution will become clear. Once you work through this, it will be with you for ever (assuming you keep using any Unix-like OS).  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
File permissions all work the same for all Unix-like OSes, so all Android, BSD, UNIX, Linux, and OSX work the same.  In fact, parts of MS-Windows works this way too, though MSFT added a few extra bits that aren't necessary, but they wanted to be more complicated.  MSFT split their permissions complexity between what Unix has and what Novel Netware had(has?).

---

