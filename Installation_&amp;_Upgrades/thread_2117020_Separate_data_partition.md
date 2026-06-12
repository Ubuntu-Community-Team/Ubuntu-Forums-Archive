---
title: "Separate data partition"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2013-02-17
I want to try the separate data partition idea as per this quote
by oldfred.
> I would not try to share /home although since so closely related it might work. Better to just create a /mnt/data partition and you can store data in that and mount it in all three partitions.
  The mount point/mnt/data desn't seem to be an option in
gparted, can i just apply my own label?  Or what mount point is
recommended?

Is there a way to use the command line to mount the data partition
in the partitions containing the OS's?  Can't find the tools to do
this in unity.

Thank you.

---

### Post by nothingspecial on 2013-02-17
You have to add it to your /etc/fstab file. Mine goes like this (note that I have it mounted at /mnt/media rather than /mnt/media)

```
LABEL=media  /mnt/media  ext4  defaults 0  0
/mnt/media/Music  /home/rob/Music  none  bind
/mnt/media/Videos  /home/rob/Videos  none  bind
/mnt/media/Pictures  /home/rob/Pictures  none  bind
/mnt/media/rob/Documents  /home/rob/Documents  none  bind

```

So the partition is mounted at /mnt/media but the last 4 lines put the folders in my home directory.

Please be more specific, ie what the partition is labled as, where you want it mounted and what exactly you want to do.

---

### Post by Bucky Ball on 2013-02-17
Apply your own label. The defaults are the most commonly used but not compulsory. At the partitioning section of the install, if you are installing, just create /mnt/data.

If you have installed already, you can still create that partition and I suggest copying the folders in your existing /home directory to the partition, deleting the folders in the /home directory and creating symlinks to the copied folders in the /mnt/data partition. For every consequent install you can do the same; delete the (empty in a new install) folders in the /home directory and link to the existing ones in /mnt/data.

There are other ways.

And +1 to nothingspecial's post regarding fstab alterations, etc.

---

### Post by offgridguy on 2013-02-17
Thank you, nothingspecial and Bucky Ball, I think i am getting the 
idea.
I have currently 3 OS's installed all linux, also a 25gb partition
created, not yet labeled or mounted which i want to use as a data
partition to write data to and access from any of the other OS.

Probably some trial and error now on my part and i should have it.
Thanks again.

afterthought; maybe for now i will stay with trying to get a separate data partition for
only one OS, get that under my belt first.

---

### Post by Bucky Ball on 2013-02-17
If that partition is mounting at boot then you are part way there already. One thing though; 25Gb is pretty small for a data partition, but having said that, this obviously must suit your purpose. ;)

---

### Post by nothingspecial on 2013-02-17
In that case I would use an ext4 partition. Use gparted to label it, whatever, lets say "data".

Put all your data in that partition, organise it however you like, but  we'll do the example with a Music folder.

Create a folder /mnt/data and make it so you own it.

```
sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
```

To mount the partition at boot you would need, in your /etc/fstab file

```
LABEL=data  /mnt/data  ext4  defaults 0  0
```

Now you need an empty Music folder in your home directory. To mount put the contents of the Music folder in your data partition in the one in your home folder you need a line


```
/mnt/data/Music  /home/[COLOR="Red"]offgridguy[/COLOR]/Music  none  bind
```

Repeat with the other folders.

You can do these fstab modifications with a command but it would be specific to your folder structure and what you want to do.

The line that mounts the partition at /mnt/media has to be before the others as the file is read one line at a time.

Always make a back up of your fstab file before you mess with it, just in case you muck it up, your system will not boot if you make a hash of it.

The process is the same for all the linux OS's, the fstab file should be the same, assuming you have the same username on all of them.

You need the same uid and gid too. If your user is the same for all the installations, and the one that was set up at install time, and all your distros are Ubuntu based then you will be fine. If not, there are potential, if not unfixable, problems.

---

### Post by offgridguy on 2013-02-17
> **Bucky Ball said:**
> If that partition is mounting at boot then you are part way there already. One thing though; 25Gb is pretty small for a data partition, but having said that, this obviously must suit your purpose. ;) 
25 gb is small, i do have it located as the last logical to the 
right side with lots of unallocated behind it, just so i can resize, which I will do straight away.
edit; resized,screenshot attached, so then the actual label  makes no difference as long
as i know which partition i am dealing with, correct?

As you can see i have 4 unused logical's as i sometimes have more
than 3 OS, installed.

---

### Post by offgridguy on 2013-02-17
@ nothingspecial, thanks for the reply,  I am puzzling over this.

> Now you need an empty Music folder in your home directory. To mount put the contents of the Music folder in your data partition in the one in your home folder you need a line

Does this mean the data is in  {both} folders or simply accessible
to the home folder?

---

### Post by nothingspecial on 2013-02-17
> **offgridguy said:**
> @ nothingspecial, thanks for the reply,  I am puzzling over this.


Does this mean the data is in  {both} folders or simply accessible
to the home folder?

The data physically resides in the /mnt/data folder, but when you bind it appears in your Music folder in your home. Whatever you add, remove, modify etc etc in the Music folder in your home applies to the actual folder in /mnt/data. Think of one folder in 2 places.

---

### Post by offgridguy on 2013-02-17
> **nothingspecial said:**
> The data physically resides in the /mnt/data folder, but when you bind it appears in your Music folder in your home. Whatever you add, remove, modify etc etc in the Music folder in your home applies to the actual folder in /mnt/data. Think of one folder in 2 places.
Ahh, Thank you very much, that helps:D

---

### Post by oldfred on 2013-02-17
Morbius1 and a few others prefer bind, I have used linking & it works for me. I believe the advantage of bind has to do with seeing the folders thru network connections. I have only copied data from the underlying data partition to another machine not from my link.

 Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

some of the discussion has been in these threads.
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

I found I was doing the same tasks with each new install and especially when testing a new version and reinstalling, it became just easier to list my history and convert that to a small bash file. I now run that in every new install. It automatically updates fstab and adds links.

---

### Post by offgridguy on 2013-02-17
Thanks oldfred, for the advice and the links.:D
edit; Lots of interesting reading, i like the sound of formating to NTFS.

I do quite a few installs and uninstalls myself, and am finding out what you mean by
doing the same tasks with each install, i have to learn a better way.;)

---

### Post by JKyleOKC on 2013-02-17
> **oldfred said:**
> I found I was doing the same tasks with each new install and especially when testing a new version and reinstalling, it became just easier to list my history and convert that to a small bash file. I now run that in every new install. It automatically updates fstab and adds links.This is an excellent idea! I do something similar when trying to do a task that I believe will be repeated, to create a script for it. Basically, I work out the task (by trial and error -- err and err and err  again, but less and less and less, to quote Piet Heim -- and then open ~/.bash_history in a text editor, copy out the block of lines that do the job, paste them into a new blank file, add the shebang line at the top plus doing any minor edits necessary such as replacing file names with parameter references, save it in my ~/bin directory, and make it executable.

---

