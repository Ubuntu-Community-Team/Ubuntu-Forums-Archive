---
title: "Be careful if you use the new gParted for new partitions"
date: 2016-08-12
forum: Installation &amp; Upgrades
---

### Post by yoshii on 2016-08-12
Be careful if you use the new gParted for new partitions.  It uses newer filesystem tools and can format some new features into the new partitions that your system probably isn't new enough to be able to handle. 

> 
Looking at:  [http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

You can see that gParted uses [e2fsprogs]("http://e2fsprogs.sourceforge.net/") ([1.43.1]("http://downloads.sourceforge.net/e2fsprogs/e2fsprogs-1.43.1.tar.gz")) , but a lot of distros aren't using those essential filesystem tools that new yet.  
I learned this after getting some non fatal errors and from using an older version of gParted that complained about the new unsupported features.  

It's also worth knowing that although gParted tends to be reliable, it's not actually based upon Debian Stable.  It's based upon Debian "Sid", which is either UnStable or Testing, I forget which.  
This might not be really bad in terms of bugs, but it's bad in terms of incompatibility.  

Because of the issues I've seen with this, my fsck isn't new enough to fix my drive if it crashes even though it works fine on older filesystem implementation.  
And it could be years until my distro updates it's repositories with versions of e2fsprogs as new as the ones gParted is using.  

So be wary.  And know that even if you format with ext3 instead of ext4, it's still using the newer version of e2fsprogs, so you might still have the same issue.


EDIT (August 13th, 2016)

I need to say that if you have the opportunity to avoid use of ext4 and to install ext3 instead, it's still worth it.  I have discovered that ext4 is still very much in development and is not complete.  Some implementations of it, such as in gParted, are based upon Debian UnStable ("Sid").  

If you use ext4 you might have some complications with other ext4 filesystem drivers and software.  Some of the features are not implemented 100% so some software will do it, and some will reject it with error messages and will not be able to complete normal ext4 tasks.  

I was able to mostly recover from some of these compatibility issues, but not all.  I had none of these issues at all when I was just using ext3 which is still pretty advanced and stable.  To get things working, I had to carefully download ALL of the e2fsprogs files from 
[https://pkgs.org/download/e2fsprogs](https://pkgs.org/download/e2fsprogs)

I had to select the Debian "Sid" ones, and also to be sure to check every listing's dependencies because there are more files needed that aren't shown in the initial results.  

After that, I used GDebi Package Manager to get an idea of the file contents and their uses.  I also used it to show which .DEB archives were needed in terms of dependencies.  Still, GDebi Package Manager couldn't be used to install the two main files needed because they are both dependent upon each other and GDebi doesn't know how to reprioritize it's own installs so that they won't fail.  

I took a risk and used sudo dpkg -i *.deb to install instead.  However, because it doesn't always use the right order of precedence, I had to run it twice for everything to work OK.  

Important to notice also, is that during the successful run, it automatically updated initramfs which is needed for kernel booting.  This is important because it's otherwise very difficult to manual update the initramfs boot archive.  However, the update only affected my most recent kernel, and I couldn't get it to update my other kernels even after I rebooted into them.  

Luckily, updated e2fsprogs with these files eliminated most of the errors I was getting and as far as I can tell the system is able to check itself now, whereas before it had an operational snafu halt, yet reported no errors (whatever that means!).  Now the main error I get is when I try to enable journal checksumming for both speed and stabilility that feature option is ignored and a minor error message about it displayed.  

As far as I know, ext3 is no longer in development and is just stable and ready for use.  

The other thing to know about ext4 is that it's not 100% backwards compatible with ext2 and ext3.  From what I can tell, ext3 is the best at being both backwards and forwards compatible.  If you format as ext4, you can't go back and easily convert or transfer to ext3.  Even trying to copy all your files from ext4 to ext3 probably won't work because of symbolic links and protection issues.  

So for all these reasons, I recommend staying with ext3 instead of migrating to ext4 no matter how you would do it.  
The other advantage to staying with ext3 is that there are alot more tools and techniques for mounting and fixing ext3 than for ext4 since it's stable and not in development and no more features are being added to it.  And you still have the option to upgrade to ext4 later on, when it's stabilized.

---

### Post by #&amp;thj^% on 2016-08-12
Just for clear definition [https://raphaelhertzog.com/2010/12/20/5-reasons-why-debian-unstable-does-not-deserve-its-name/](https://raphaelhertzog.com/2010/12/20/5-reasons-why-debian-unstable-does-not-deserve-its-name/)
> Debian "Sid"
Debian Unstable (also known as sid) is one of the 3 distributions that Debian provides (along with Stable and Testing).

But Thanks for the heads up on Gparted.
Regards

---

### Post by wildmanne39 on 2016-08-12
I have never used Debian but that link you posted has some interesting information.
Thanks

---

### Post by yoshii on 2016-08-13
Thanks for clarifying what Sid is.  I will try to remember "Sid Vicious" as a mnemonic device :D

EDIT (August 13th, 2016)

I need to say that if you have the opportunity to avoid use of ext4 and to install ext3 instead, it's still worth it.  I have discovered that ext4 is still very much in development and is not complete.  Some implementations of it, such as in gParted, are based upon Debian UnStable ("Sid").  

If you use ext4 you might have some complications with other ext4 filesystem drivers and software.  Some of the features are not implemented 100% so some software will do it, and some will reject it with error messages and will not be able to complete normal ext4 tasks.  

I was able to mostly recover from some of these compatibility issues, but not all.  I had none of these issues at all when I was just using ext3 which is still pretty advanced and stable.  To get things working, I had to carefully download ALL of the e2fsprogs files from 
[https://pkgs.org/download/e2fsprogs](https://pkgs.org/download/e2fsprogs)

I had to select the Debian "Sid" ones, and also to be sure to check every listing's dependencies because there are more files needed that aren't shown in the initial results.  

After that, I used GDebi Package Manager to get an idea of the file contents and their uses.  I also used it to show which .DEB archives were needed in terms of dependencies.  Still, GDebi Package Manager couldn't be used to install the two main files needed because they are both dependent upon each other and GDebi doesn't know how to reprioritize it's own installs so that they won't fail.  

I took a risk and used sudo dpkg -i *.deb to install instead.  However, because it doesn't always use the right order of precedence, I had to run it twice for everything to work OK.  

Important to notice also, is that during the successful run, it automatically updated initramfs which is needed for kernel booting.  This is important because it's otherwise very difficult to manual update the initramfs boot archive.  However, the update only affected my most recent kernel, and I couldn't get it to update my other kernels even after I rebooted into them.  

Luckily, updated e2fsprogs with these files eliminated most of the errors I was getting and as far as I can tell the system is able to check itself now, whereas before it had an operational snafu halt, yet reported no errors (whatever that means!).  Now the main error I get is when I try to enable journal checksumming for both speed and stabilility that feature option is ignored and a minor error message about it displayed.  

As far as I know, ext3 is no longer in development and is just stable and ready for use.  

The other thing to know about ext4 is that it's not 100% backwards compatible with ext2 and ext3.  From what I can tell, ext3 is the best at being both backwards and forwards compatible.  If you format as ext4, you can't go back and easily convert or transfer to ext3.  Even trying to copy all your files from ext4 to ext3 probably won't work because of symbolic links and protection issues.  

So for all these reasons, I recommend staying with ext3 instead of migrating to ext4 no matter how you would do it.  
The other advantage to staying with ext3 is that there are alot more tools and techniques for mounting and fixing ext3 than for ext4 since it's stable and not in development and no more features are being added to it.  And you still have the option to upgrade to ext4 later on, when it's stabilized.

---

### Post by yoshii on 2016-08-13
Just a quick follow-up...

as it turns out, the newer version of e2fsprogs (essential filesystem tools) might be available via "snap" on Ubuntu systems, but not all Ubuntu systems come with snap enabled by default.  Maybe none of them.  
I was able to install snap with some warning message about an error overwriting some snapd files.  However, I have no idea how to use snap for individual files instead of gigantic distro packages.  

Snap doesn't work like apt, and there's not much easy to read documentation yet.  So basically, it's not really available to the average user.  

I don't actually use Debian most of the time, I use some Ubuntu variants.  But because Ubuntu is based upon Debian, the risks turned out to be not quite as bad.  
Ubuntu and Debian tend to still have a lot in common so some of the archives go both ways, some go halfway.  But still it's probably not entirely safe.  

Always read the release notes/changelogs of whatever you use, and you can notice stuff like this.  That's how I found out about gParted.  It wasn't explicitly listed on their webpage, but it's in the release notes/changelog and also shows up as a clue on the boot screen if you turn off the splash screen.

---

### Post by wildmanne39 on 2016-08-13
I am curious what kind of issues were you having that you think ext4 caused, I have used it for a few years now without issue but I am running ubuntu mate 16.04 now and I have been having strange issues with files and file browser, and gparted does show a difference in block size but it can not repair it.
Thanks

---

### Post by yoshii on 2016-08-13
@Wild Man,

Sorry you are having issues.  

The errors I experienced weren't operating system or program errors.  They were filesystem and maybe kernel errors reported during boot and during a few certain specific runs of an older version of gParted.  
In my grub, I have splash and quiet removed so that I can see all the success and failure messages during boot.  I want to know what's happening with my system instead of just seeing a graphical wheel spin forever.  

I also looked at $ dmesg > bootlog.txt
But the boot screen itself has more info.  
And when running gParted, if you expand all the infos (click on the tiny triangles), you'll see more info and progress bars.  

Also, I recently downloaded the source files for ext4 and even though I never mess with compiling, I read the included notes and it's clear that ext4 is still very much an incomplete work in progress.  

The main issues I was having was errors 2 or 8.  2 means there were errors that were fixed, and 8 means an "operational error" which is different from a filesystem error.  But it said that fsck failed implying that it wasn't able to completely run.  It's too much for me to explain all the error messages from 0 to 128.  
Read $ man ext4  or $ info ext4 to learn about those errors.  Essentially, I was usually getting error 8 and it was remounting with some ext4 features I had requested in etc (according to the manuals) disabled.  
At earlier times it was saying that a file was missing also.  

Now that I have successfully updated the e2fsprogs with that newer version that gParted uses, it's booting a lot faster and I think the errors are mostly gone because the screen doesn't pause on the mounting ext4 filesystem stage.  $ dmesg > bootlog.txt still reveals however that it's remounting for some reason instead of just mounting.  

I keep checking the filesystems with gParted (the new version and the old version) and both now report no errors. 
At an earlier time, the older version of gParted showed an error message saying that some newer ext4 features weren't compatible with gParted or something like that.  I forget the exact text.  
But now it doesn't do that because it's able to access the newer e2fsprogs, which includes fsck.  

I am going to keep investigating this and probably email the ext4 developer to make sure that I get a satisfactory stable system.  

I hope this answers your question.  From what I can tell, ext4 bugs are STILL being squashed, so I wish I had stayed with ext3, but now I can't go back since all my data is ext4 now.  
I don't know how to copy all of it onto an ext3 partition as files without protection errors, even as root.  

Sorry I don't know how to help you with the errors you are having.

---

### Post by wildmanne39 on 2016-08-13
Thank you yoshii for your thorough reply, I will continue to look for answers.

---

### Post by mikodo on 2016-08-13
Thank you, yoshii and must say Wild Man for your continuing to look for answers.

I am sitting here with only ext4 partitions and use gParted for partitioning. 

What should be done to "be careful" using: 

```
$ dpkg --status gparted | grep ^Version
Version: 0.25.0-1
```

```
dpkg --status e2fsprogs |grep ^Version
Version: 1.42.13-1ubuntu1
```
I wish I could go back to ext2, as a casual user, I have no need for journaling and its' added expense on ssd's.

I do have 16.04 installed. The forum won't let me upgrade my profile.

---

### Post by yoshii on 2016-08-16
@Mikodo, 

From what I understand, gParted is a front-end for e2fsprogs.  So if you upgrade the e2fsprogs on the system that is running gParted, it should upgrade the functionality of gParted.  
I was able to do this to a LiveCD.  It couldn't upgrade everything, but it seemed to enable the checkdisk scanning and other procedures to be run with updates assuming that the printed tool versions were correct.  

I think ext3 is probably a good compromise between the advantages of ext2 and ext4.  
You could probably turn off journaling using tune2fs or whatever it's called, and check the disk for errors afterwards, but I haven't done that and am not speaking from experience.

---

### Post by bcschmerker on 2016-09-05
**Thanks for a clue to a problem that I encountered** while installing Ubuntu® 16.04rc (since upgraded to 16.04.1-LTS) back in April:  The Partition Tools in both 14.04.4-LTS and the 16.04 install ISO ran into errors with my then-new Toshiba® MQ01ABD050 2.5" hard drives (installed, partitioned and formatted on SATA ports in the Intel® Advanced Host Controller Interface protocol), and more specifically were unable to set the first partition (/dev/sdb1 in ext4, /dev/sdc and /dev/sdd in BTrFS) to start at Track Zero, unlike the Western Digital® WD1600JS at /dev/sda (which found Track Zero as planned and has /dev/sda1 for boot).  All three MQ01ABD050's consequently have offsets.  What corrective measures might be useful short of a re-install (which would be necessary to re-build the partitions in Native IDE)?

---

