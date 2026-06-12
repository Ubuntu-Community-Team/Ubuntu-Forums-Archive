---
title: "dpkg error"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2010-03-30
Have been running Lucid since alpha 3. Have updated everyday. Haven't had any problems till last week I suddenly started getting error relating to dpkg. Please see screenshot below

[IMG]http://i39.tinypic.com/2cmvnvd.jpg[/IMG]

Any ideas my fellow ubuntu brothers and sisters?

---

### Post by ArtemNY on 2010-03-31
I got the same error trying to install updates on 9.10

---

### Post by gmargo on 2010-03-31
Look at the file dpkg is complaining about and see if it looks trashed.  It should be a list of files and directories.  

See **/var/lib/dpkg/info/system-config-printer-udev.list**

---

### Post by vishnumrao on 2010-03-31
Hi Gmargo,

I found some info on [launchpad]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/78863"). 


I tried the steps mentioned that bug report. Made some progress, but ended up with other errors. As soon as I would rm the problem_package.list file from /var/lib/dpkg/info/ , I would get another problem package. After about 10 sudo rm problem_package.list (10 different problem packages), I decided to sudo rm *.list to remove all .list files. I assumed that the .list files would get re-built or re-downloaded. 

I now have a different set of problems. But its some progress. Will update the thread later in the day.

Can you give me your inputs on the removed .list files?

---

### Post by gmargo on 2010-03-31
You didn't comment on what you found in the .list file in question, or the ones that turned up later.  They shouldn't have gotten corrupted.  Missing maybe but corruption surprised me.

Anyway, since this is Lucid, perhaps the best thing is to just wipe it and install the beta (and the boatload of updates since).  Alternatively, in another thread I posted a script that will regenerate the content of /var/lib/dpkg/info/, if you want to try that.

[http://ubuntuforums.org/showpost.php?p=8991214&postcount=19](http://ubuntuforums.org/showpost.php?p=8991214&postcount=19)

---

### Post by vishnumrao on 2010-03-31
I had already deleted the .list files. Hence I had no way to check the contents of the file.

I downloaded the .pl file and executed it

Here is the output:

```
vishnumrao@vishnumrao-desktop:~/Downloads$ sudo perl dpkg_info_recover_v1.pl
There are 1781 packages installed.
There are 283 packages already processed.
There are 24 packages ready to process.
There are 1474 packages with no candidate filename.
vishnumrao@vishnumrao-desktop:~/Downloads$
 
```

---

### Post by roynoblin on 2010-04-01
i just installed ubuntu and trying to run update manager but i get this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can anyone tell me what this means and what to do about it
thanks

---

### Post by pastalavista on 2010-04-01
> **roynoblin said:**
> i just installed ubuntu and trying to run update manager but i get this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can anyone tell me what this means and what to do about it
thanks

It means apt/dpkg failed somehow. Open a terminal (Applications-->Accessories-->Terminal) and enter these commands ```
sudo apt-get update && sudo apt-get -f install && sudo dpkg --configure -a
```

---

### Post by gmargo on 2010-04-01
> **vishnumrao said:**
> I had already deleted the .list files. Hence I had no way to check the contents of the file.

I downloaded the .pl file and executed it

Here is the output:

```
vishnumrao@vishnumrao-desktop:~/Downloads$ sudo perl dpkg_info_recover_v1.pl
There are 1781 packages installed.
There are 283 packages already processed.
There are 24 packages ready to process.
There are 1474 packages with no candidate filename.
vishnumrao@vishnumrao-desktop:~/Downloads$
 
```

This program does not need 'sudo' - If given the "--download" option, it recovers the files into a temporary directory; the user still has to copy them to the /var/lib/dpkg/info/ directory.

Have you done an 'apt-get update' lately?  I think you've found a built-in bug (feature!) in my code.  Since I wrote and tested it on a fully up-to-date system, I didn't write the code yet to go out and find old packages.  The current incarnation works off of the package lists fetched by 'apt-get update' (aka the latest-and-greatest packages).  Let me work on this a little today.

Curious - did you remove all the .list files?  According to that output, 283 .list files were found.

---

### Post by roynoblin on 2010-04-01
thanks pastalavista and if someone will tell me how to make a new post i will do so. 
i enter what you suggested and got this
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
i can not download anything

---

### Post by roynoblin on 2010-04-01
thanks for showing me Open a terminal (Applications-->Accessories-->Terminal)
from there i did a copy and paste
  	 	 	 	 	 	  sudo dpkg --configure -a
 it ran a bunch of lines like a dos window and now i was able to do the update
have a video error now but i at least have some idea how to fix it
thanks again:D

---

### Post by vishnumrao on 2010-04-01
> **gmargo said:**
> This program does not need 'sudo' - If given the "--download" option, it recovers the files into a temporary directory; the user still has to copy them to the /var/lib/dpkg/info/ directory.

Have you done an 'apt-get update' lately?  I think you've found a built-in bug (feature!) in my code.  Since I wrote and tested it on a fully up-to-date system, I didn't write the code yet to go out and find old packages.  The current incarnation works off of the package lists fetched by 'apt-get update' (aka the latest-and-greatest packages).  Let me work on this a little today.

Curious - did you remove all the .list files?  According to that output, 283 .list files were found.


@gmargo Yes, I deleted all the .list files. After that I ran a update and an upgrade, which seemed to install a few updates, but eventually failed. 

You based in Silicon Valley? Curious, where?

Thanks for your time.

---

### Post by vishnumrao on 2010-04-02
Update: Running update-manager and trying to install updates, does install some updates. 

After installing some updates I ran the perl script. This time the number of processed packages went up from 283 to 402. But "There are 24 packages ready to process". 

```
vishnumrao@vishnumrao-desktop:~/Downloads$ perl dpkg_info_recover_v1.pl
There are 1787 packages installed.
There are 402 packages already processed.
There are 24 packages ready to process.
There are 1361 packages with no candidate filename.
vishnumrao@vishnumrao-desktop:~/Downloads$ 

```

---

### Post by gmargo on 2010-04-02
Do you have all of the repositories enabled?  I'm having a tough time figuring out how the number of no-candidate-file can be so high.  The only packages that show no-candidate-file on my system are the packages for which I've installed a .deb file manually.

---

### Post by vishnumrao on 2010-04-02
This Lucid install is an upgrade from Karmic (which if I remember correctly, is an upgrade from Jaunty, I could be wrong). Over the past few months, I have enabled and disabled some repos. The upgrade from Karmic to Lucid, disabled some repos, but I have reinstated most like Chromium, Medibuntu, Ubuntu-tweak etc.

An observation: Since I installed a few of the updates, the number of "no candidate filename" has come down from 1474 to 1361. and the number of already processed went up from 283 to 402. So when I install an update for a package, I guess it automatically generates the .list file?

If I sent you a list of the 24 packages that are ready to process, could you send me the necessary info, like the .list files or status entries etc?

Thanks,
Vishnu.

---

### Post by gmargo on 2010-04-02
If you run the perl script with a --download option, then the 24 packages will be processed and the resultant files will be left in a $HOME/dpkgrecovery/info_add/ directory.  You'll have to manually change the ownership and move them to /var/lib/dpkg/info/.

I suspected this might be an upgrade situation.  Try this: Add karmic entries to your /etc/apt/sources.list (in addition to the Lucid entries), do an apt-get update, and then run the script again to see if it found more files (on the weak theory that some package are karmic and some lucid?).

---

### Post by gmargo on 2010-04-03
Ignore what I just said about a "karmic/lucid" mix.  Instead I think it's really "lucid/lucid" mix.  What I mean by that is that Lucid is currently a moving target, and the packages that were marked "no-candidate-filename" are ones that have been upgraded in Lucid; and the .deb files for the old versions are no longer available.  I will come up with a way to generate the info/ files from the newer .debs.

---

### Post by vishnumrao on 2010-04-06
> **gmargo said:**
> If you run the perl script with a --download option, then the 24 packages will be processed and the resultant files will be left in a $HOME/dpkgrecovery/info_add/ directory.  You'll have to manually change the ownership and move them to /var/lib/dpkg/info/.

I ran the perl script with the  --download option, and copied all the files from dkpkgrecovery/info_add to the /var/lib/dpkg/info/. But this still does not fix the problem. Running your script now shows:

vishnumrao@vishnumrao-desktop:~/Downloads$ perl dpkg_info_recover_v1.pl
There are 1782 packages installed.
There are 448 packages already processed.
There are 0 packages ready to process.
There are 1334 packages with no candidate filename.
vishnumrao@vishnumrao-desktop:~/Downloads$ 

Any ideas on how to fix this? Further information: here is the detailed error messages when I do a sudo apt-get upgrade

[http://dl.dropbox.com/u/184921/output.txt](http://dl.dropbox.com/u/184921/output.txt)

---

