---
title: "More &quot;newbie&quot; questions - multiple"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by lm77054 on 2011-10-19
This is my second post.  As I indicated in the first one, I'm getting really close to going to UBUNTU.  Now I have a couple more questions.

1.  Is there FREE software that will allow me to image and restore my disks under UBUNTU, like Norton Ghost, or Paragon Software backup and recovery, which is for windows?

2.  Is it possible to "ZIP" (or the LINUX equivalent) file via commandline?  I backup things on Windows using a combo of WINZIP/WINZIP Commandline Utility and BATCH (script) files?

3.  Is there a way to change the default location of the "home" directory for a user.   Under Windows, I changed it to C:\MyData, and I'm just wondering if changing the "home" directory is possible.

4.  Is it possible to change the default security that UBUNTU assigns when files are created?

5.  In GEDIT, is it possible to: (1) make it always use a specific coding (e.g. western iso.... WITHOUT SELECTING IT EACH TIME; (2) make it use Windows end-of-line, WITHOUT SELECTING IT EACH TIME; and finally (3) make it use the extension ".txt" all the time, unless I specify it different, without having to type it in each time?

Thanks for tolerating this (possible) newbie's questions.

---

### Post by Ignatius Reilly on 2011-10-19
System images: you may want to use [Clonezilla]("http://clonezilla.org")

Saved my life after a recent catastrophic upgrade to 11.10 that f*** down everything. I restored a 11.04 image in no time.

---

### Post by luvr on 2011-10-19
> **lm77054 said:**
> 2.  Is it possible to "ZIP" (or the LINUX equivalent) file via commandline?  I backup things on Windows using a combo of WINZIP/WINZIP Commandline Utility and BATCH (script) files?
Absolutely! The ***&#8220;zip&#8221;*** command works great under Linux.

The *&#8220;native&#8221;* data compression and archive file handling tool under Linux (and any Unix-like system), however, is ***&#8220;tar&#8221;***; creating a compressed archive goes something like this:
```
tar -czvf *name-of-archive*.tar.gz *list-of-files-and-directories*
```
where:
[LIST]
[*]the *&#8220;c&#8221;* option stands for *&#8220;create&#8221;* (an archive);
[*]the *&#8220;z&#8221;* option stands for *&#8220;gzip&#8221;* compression;
[*]the *&#8220;v&#8221;* option runs the command in *&#8220;verbose&#8221;* mode, and is optional;
[*]the *&#8220;f&#8221;* option specifies that the immediately following argument is the archive file name;
[*]the *&#8220;.tar.gz&#8221;* extension on the archive file name ensures that the archive can easily be recognised as a *&#8220;gzip&#8221;* compressed archive.
[/LIST]

Unpacking the archive works as follows:
```
tar -xzvf *name-of-archive*.tar.gz
```
where the *&#8220;x&#8221;* option stands for *&#8220;extract&#8221;* (files from an archive). You may follow the name of the archive file with a list of the files that you want to extract from it (to extract only these specified files).

You can list the contents of the archive as follows:
```
tar -tzvf *name-of-archive*.tar.gz
```
where the *&#8220;t&#8221;* option stands for *&#8220;test&#8221;* (the contents of an archive).

There are far more options to the command; but the ones that I describe above should allow you to get started (and, for everyday use, they may be all that you will ever need from the command).

> 3. Is there a way to change the default location of the "home" directory for a user. Under Windows, I changed it to C:\MyData, and I'm just wondering if changing the "home" directory is possible.

4. Is it possible to change the default security that UBUNTU assigns when files are created?
These two are perfectly possible, too. Documenting them would take a little more time than I have right now, however. If no-one else jumps in, then ask again, and I may be able to write something up.

---

### Post by papibe on 2011-10-19
> **lm77054 said:**
> 3.  Is there a way to change the default location of the "home" directory for a user.   Under Windows, I changed it to C:\MyData, and I'm just wondering if changing the "home" directory is possible.
Yes, you can move your home directory to a new partition, new disk, etc.

However note that the home's file system can't be NTFS. That doesn't mean that your Music, Videos, Documents, and others can be on pretty much anything you want.

Regards.

---

### Post by lm77054 on 2011-11-12
Hi all:  I appreciate the replies, and I said in other posts, I'm getting more and more comfortable with UBUNTU.  For now, I'm running it in a limited size Windows App'd version (inside Windows).  I looked at what &quot;Ignatius Reilly&quot; suggested, and on the surface it looked like a plan (THANKS FOR THE SUGGESTION).  However, after I did a little more digging about the program, I've decided against using it.  So for now, it looks like when I convert over to UBUNTU, I will be running it in a permanent Windows App'd environment.  The reason behind this, is that I then can use programs like Norton Ghost or Paragon's Backup and Recovery program, which have a proven track record.  With Paragon's Backup and Recovery I can backup my computer from a CD boot, or from within Windows (see note below).  NOTES:  1.  The reason I won't use CLONEZILLA is because of the country of origin.  All programs that I downloaded from the country of origin of CLONEZILLA had malware in it, so I've sworn off all software fromthe country of origin of CLONEZILLA.  2.  If I go to this method (Windows App'd version), Windows will only be the OS and nothing else.  What I mean is that with in Windows Environment, it will only have the OS, no patches, updates, etc, except for Paragon's Backup and Recovery program, and within Windows, Internet access will be disabled.  The only reason that I'm looking at this, is the cloning (imaging) of the disk.  I tried to use Paragon's Backup and Recovery on a Virtual Machine, and it worked AOK, but it then talked about re-initing.  I had a post on that ([http://ubuntuforums.org/showthread.php?t=1866792](http://ubuntuforums.org/showthread.php?t=1866792)), with no replies, and I haven't been able to locate a good description/instructions on &quot;re-initing&quot;.  If I can get an answer to that question, whether here or finally locate it myself, then the system will not be the Windows App version (98% change) will go away.

---

### Post by darkod on 2011-11-12
I ma not familiar with Windows App, what is it? When you say you are arunning it "inside windows", do you mean a wubi install?
Just to warn you that if you decided to keep running a wubi install long term, you are looking at loads of problems. Wubi is only meant as short term "do you like me" thing. Basically one step further than running the CD in live mode (you can easily add software in wubi and get the feeling of ubuntu).
Otherwise, running wubi as everyday system, stay away from it.

For the cloning thing.
Have you considered FSArchiver? [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
It's not strictly cloning software, but it is a good backup tool. When I was comparing it with clonezilla, if I remember correctly, clonezilla had a fault that it couldn't restore to a smaller partition than the source partition, even if there is enough space. So if you had only 50% used in your source partition, you still can't restore to smaller one.
FSArchiver can restore to any partition as long as it is slightly bigger than the backup size.
However this is not a partition or disk cloning software. For example if restoring on new disk apart from putting the data back onto the selected partition you will have to reinstall the bootloader too. Depending what kind of setup you have, restoring a bootloader is a 2min thing, but you might not want to bother with that.

Also, the latest 11.10 comes with built-in DejaDup backup software which I haven't had time to look at. You might want to read about it and test it how it works. The developers must think it does a good job since they included it since this version.

---

### Post by lm77054 on 2011-11-13
> **darkod said:**
> I ma not familiar with Windows App, what is it? When you say you are arunning it &quot;inside windows&quot;, do you mean a wubi install?
Just to warn you that if you decided to keep running a wubi install long term, you are looking at loads of problems. Wubi is only meant as short term &quot;do you like me&quot; thing. Basically one step further than running the CD in live mode (you can easily add software in wubi and get the feeling of ubuntu).
Otherwise, running wubi as everyday system, stay away from it.

For the cloning thing.
Have you considered FSArchiver? [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
It's not strictly cloning software, but it is a good backup tool. When I was comparing it with clonezilla, if I remember correctly, clonezilla had a fault that it couldn't restore to a smaller partition than the source partition, even if there is enough space. So if you had only 50% used in your source partition, you still can't restore to smaller one.
FSArchiver can restore to any partition as long as it is slightly bigger than the backup size.
However this is not a partition or disk cloning software. For example if restoring on new disk apart from putting the data back onto the selected partition you will have to reinstall the bootloader too. Depending what kind of setup you have, restoring a bootloader is a 2min thing, but you might not want to bother with that.

Also, the latest 11.10 comes with built-in DejaDup backup software which I haven't had time to look at. You might want to read about it and test it how it works. The developers must think it does a good job since they included it since this version.

 Short answer, yes, I mean wubi installer.  Now, please allow me to explain my reasoning for wanting to use wubi long term.  On my windows system, I will install the basic OS, ghost it (image it).  I will then install &quot;X&quot; stuff (e.g. drivers), image the system, and continue on, imaging the system at certain points.  I do this so if something happens, I can fall back to step &quot;Y&quot;, restore my system, and go forward.  These images don't contain my &quot;data&quot; files (meaning spreadsheets, documents, etc).  I back these things up on AT LEAST a weekly basis.  Now, I tried, in a virtual machine to use Paragon Backup and Recovery, which works on NTFS, FAT, FAT32, linux partitions and others.  However when I restored it, it talked about re-initing (the grub).  When I finally found out how to do it, I think (see my other thread), it seemed to be too much of a pain.  With using a wubi install, I simply restore the system, and I'm up and going without having to reinit things (GRUB).  This is why I decided on the wubi install.  The whole thing hinges on the imaging software.  If I can find (LINUX) software that images things fine, like Norton or Paragon (I prefer free), then I will abandon the idea of wubi.

---

### Post by darkod on 2011-11-13
The second part of my post was about few backup options.

---

### Post by lm77054 on 2011-11-13
> **darkod said:**
> The second part of my post was about few backup options.

I'll be looking at it later or tomorrow, it's wife time now.  Thanks.

---

