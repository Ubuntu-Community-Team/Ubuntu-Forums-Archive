---
title: "Full audit of files on the hard drive.."
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by orkim on 2007-03-13
I've searched the forums high and low but I have yet to find an answer to this question.  Please forgive me if it has been raised/answered somewhere else and offer a link.

I've come across several great posts on how to see if there are packages "out there" on my system that are orphaned (deborphan).  I have seen some posts on tips and tricks on keeping the cruft out of your system.  There are even some excellent posts on building packages from source with apt-build an similar tools.

However, I have not seen a post that will preform a complete audit of the files on a system.  I think this may need a bit more explanation on my part so I will describe my ideal tool.

I would like a tool that will take the contents of all of the installed packages (list of files/checksums/etc) and compare them to the installed files.  This could ideally be used to find "extra" files that are in the file system but not in the installed package database.  I would assume that I could be able to specify directories like /home, /var/mail, and /proc to have the tool ignore though.  Also, this tool would hopefully located changed files (as compared to the file in the original .deb).

I think this would be a really powerful tool.  I'm assuming that I'm not the first person to think of this, so something must exist that can complete this task.  I know apt-file exists and it seems to do this job on a smaller scale.  It will at least tell  you what package a file belongs too.

Please let me know if you can offer any hints or suggestions as to where to go from here.  I appreciate it!

-orkim

---

