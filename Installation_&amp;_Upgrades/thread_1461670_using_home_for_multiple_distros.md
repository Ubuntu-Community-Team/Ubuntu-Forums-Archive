---
title: "using /home for multiple distros"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by otetiani on 2010-04-24
Ok, I dual boot multiple distros of Ubuntu and I'm trying to use my /home from 9.10 for 10.04 also.

Is this possible?

If not, does anyone know if I can copy sections of my 9.10 Crossover files to my 10.04 /home.  Biggest thing is for WoW which takes forever to load each new distro I upgrade to.

Thanks in advance!

---

### Post by srs5694 on 2010-04-24
It's possible; however, sometimes different versions of programs have different configuration file formats. Thus, if you use, say, Ubuntu 9.10 and 10.04, the 10.04 version (or specific programs it uses, to be more precise) could update some user configuration files, which could then confuse the earlier versions of the programs that use those files in 9.10. This problem can be even worse if you mix distributions (Ubuntu and Fedora, say), since files like icons might be stored in different places in the two distributions, so references that work for one distribution might not work for another.

Usually, when I install multiple distributions on one computer, I do share /home; however, I create different user home directories for each distribution. I still use the same UID number for both distributions, so I can easily access either home directory from either distribution. I can copy or create symbolic links of files or subdirectories when that's convenient.

---

### Post by otetiani on 2010-04-24
That makes sense, and exactly what I was thinking which is why I didn't try to use /home for both.

Thanks

---

### Post by oldfred on 2010-04-24
You should not share /home but you can share all the data. When I converted to Karmic I reorganized and moved all my data out of /home. I now have /home sitting in a 100GB partition and using 1GB.

How to Multi-boot (Maintain more then 2 OS) 
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by srs5694 on 2010-04-24
> **oldfred said:**
> You should not share /home but you can share all the data. When I converted to Karmic I reorganized and moved all my data out of /home. I now have /home sitting in a 100GB partition and using 1GB.

I disagree with this. The Unix (and hence Linux) tradition is to put user data in user home directories, which in Linux's case are in /home. A single Linux system can support more users than anybody is likely to be tempted to create, so you can have /home/fred, /home/sally, /home/george, /home/judy, and so on. When multi-booting two or more installations, you can easily give yourself different home directories in each installation -- say, /home/fred1 and /home/fred2. These won't interfere with one another, even if they're on the same /home partition. Creating user data partitions and mounting them in some non-standard location while keeping minimal /home directories in each installation is an ugly kludge, IMHO.

Keeping user data in /home (with a few files in other well-defined areas, such as /tmp and /var/spool/mail) has certain advantages over creating partitions and dropping user data in random locations willy-nilly. For one thing, you can easily search for user files in /home, without worrying about any other locations you might have used. Another advantage is one of standardization -- if you use another Linux system, or if somebody else needs to use yours, there'll be less confusion about where things go, at least if everybody involved know the rules. (See the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) to learn the rules.) Similarly, when you ask for help, the most experienced Linux people are likely to assume you're using a standard configuration with user data in /home. Putting user data in your own directory also means you can use the tilde character ("~") to refer to that home directory on the command line, as in "less ~/somefile.txt", vs. using a complete path, as in "less /some/random/mount/point/somefile.txt".

Note that the /home directory name specifically is just a convention. Some Unix-like systems user other names for this, such as /users; and big systems often create site-specific subdivisions or expansions, such as /home/faculty (holding /home/faculty/schaeffer, /home/faculty/hamilton, etc.) and /home/students (holding /home/students/t.brown, /home/students/l.wu, etc.). I'm not arguing against such deviations from the defaults; but if your home directory on a personal system is /home/brennan, creating a Linux user data partition to hold all your user data and mounting it at /media/MyData makes little sense. It's simpler to just mount that partition at /home instead.

IMHO, the practice of creating "extra" partitions for data and then mounting them outside of /home is a holdover from Windows drive-letter thinking ("oh, I'll put it on the E: drive...."), which in turn is a holdover from DOS, which inherited this practice from CP/M. Unix did it better to begin with, and Linux inherited the superior Unix unified directory tree. It's better to use it as it was intended: Create a separate /home partition and store all your user data there. Deviate from this only for specific purposes, such as accessing dual-boot shared-data partitions or removable disks.

---

### Post by oldfred on 2010-04-25
Not to get into a discussion, but anyone sitting at my system will see the standard folders in my /home. It is just that each of the folders is a link to my data partition. 
When I convert to Lucid I will actually move my /home back into root as their is no advantage of a separate /home for new installs for me. Home is so small I easily back it up and copy it to a new install. Data is still in a separate partition and linked into home. The data has no relationship to system files. But then it is easy to mount & link the data into every install.

To srs5694's point, I think I did find one script that expected a folder and did not follow the link so it did not save to the correct location. But I thought links were a standard linux feature.

It may be the difference between a separate /home and separate data is splitting hairs. If you were mounting data all over the place then I would have to agree with srs5694.

---

### Post by srs5694 on 2010-04-25
I suppose, oldfred, that I was mainly responding to your claim that one "...should not share /home..." -- as if doing so were dangerous or inadvisable in some way. It's not. Linking from your /home/{whatever} directory to a data partition mounted elsewhere helps with many of the issues I identified. Still, I don't see the point. At best, the method you're advocating is no worse than the method I suggested. At worst, it's more complex and can lead to some subtle complications, like the utility you mention that didn't properly follow symbolic links.

Then too, I've been using Linux for fifteen years, and other multi-user systems for a decade or so longer than that. Many of these systems have been multi-user in reality, not just in name, so I fully appreciate the advantages of keeping users' data in their own home directories as much as possible, rather than scattering it about (symbolic links or no). On a single-user Linux system, some of the imperatives of a true multi-user system may not be as important, but my instinct is to stick to the Unix conventions.

---

