---
title: "Dreamweaver mx 2004 &amp; wine -- please help"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by MindFork on 2007-06-01
After extensive searching, I was able to install Dreamweaver but it won't run.  Here's what I did:

I installed wine 0.9.33 via Synaptic.  I installed mdac 2.8 and IE6 (first) through Wine.  IE6 only shows a white window when I try to run it from the wine file browser, but it's there...sort of.

I installed Dreamweaver MX 2004 and was successful enough to have applications > wine > programs > macromedia > macromedia dreamweaver mx 2004 with the green icon.  But when I click it, nothing happens.  Nothing...no errors, nada.  Same if I try to run it in the browser.

The MM extension manager is also there, and appears to be working fine. (Like that really helps...)

Any suggestions on how to get DWmx working in wine?

Thanks

---

### Post by MindFork on 2007-06-01
bump

---

### Post by MindFork on 2007-06-01
Well, I tried Dreamweaver 8 and the tutorial linked from this thread: [http://ubuntuforums.org/showthread.php?t=400604](http://ubuntuforums.org/showthread.php?t=400604)

And I can get the program to launch, then it tells me there was a problem with my installation and that I need to install again. 

Surely *someone* has made this work!  Please help.

---

### Post by MindFork on 2007-06-01
OH HELL YES!  I got this ugly bitch to work!

I found the same set of instructions for DW8 here: [http://bkcreation.info/Blog_Macromedia8OnWine.html](http://bkcreation.info/Blog_Macromedia8OnWine.html)

BUT in the comments, somebody mentioned that there is a crack by "fff" that needs to be applied to the Dreamweaver 8.exe for people getting the "reinstall your program" error like I was.  I googled "dreamweaver fff crack" and found it.  After cracking the exe, THE PROGRAM WORKS.

I don't get the file branch on the right side to expand, but I don't really care.  I added a site that was in my /home/mydir/websites folder, set it to ftp files to the server on save (hugely convenient or a huge PIA depending on the type of site, but something I use often) and it all worked fine.

I hope this thread is helpful for future dreamweaver ubuntu wine users.  

To recap, you need to use Dreamweaver 8 and install it on a windows box first.  Make sure you run the program and enter your serial before copying files to your linux box.  You may also need to install mdac / ie6, which is what I did first...maybe not, though.  The best tutorial is here: [http://blog.publicidadpixelada.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/](http://blog.publicidadpixelada.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/)

Once that is done, google the dreamweaver fff crack, unzip it, move all files into the dreamweaver install directory and run the crack through wine.  It will back up your exe for you.

Good luck, and good hunting.

---

### Post by geovino on 2007-06-02
I did all the steps in [http://bkcreation.info/Blog_Macromedia8OnWine.html](http://bkcreation.info/Blog_Macromedia8OnWine.html)
except I think I messed up on the exporting of the reg file. it's rather confusing. Can you explain this last step a bit more clearly:

..."then export the HKEY_LOCAL_MACHINE/Software/Macromedia/ key from your registry on windows XP ( "regedit" in execute ) and convert it to ascii using "$ recode ucs-2..ascii yourfile.reg" and run it in wine with "$ wine regedit yourfile.reg"

All the other files are in their proper files. If I can get the reg file to work I may have it.

---

### Post by MindFork on 2007-06-02
find the macromedia key in regedit, right click on it and export it to an easy folder to remember.  Then switch to your ubuntu machine and copy it over there.  Once it's on your ubuntu rig, open up terminal, change into the directory where the .reg file is and run the conversion command.

Don't forget the fff crack if you get the "you need to reinstall the software" error.

---

