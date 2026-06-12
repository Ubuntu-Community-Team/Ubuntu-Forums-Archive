---
title: "Feisty Install seems corrupted"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by kathmary on 2007-04-25
I had an install of Edgy and upgraded to Feisty...seems I got overzealous when uninstalling vmware and deleted necessary folders.  I took this opportunity to try the Feisty alternate cd in  hopes that my hardware (monitor) would be detected better.  The screen is still offset horizontally to the left.

In addition, the installation will stop at 85%, at the point where "brltty is installed".  Eventually it will start again and perform a "clean up" and finish.  It looks like everything may not be getting installed.  When I boot the OS, there are many files I do not have have permission to access.  The" Lost and Found" folder is one of them.  I do not remember seeing this on my first edgy install.     

Could someone give me a clue about how the installation is supposed to look?  Is the "Lost and Found" folder supposed to be owned by root?  I don't remember whether I changed some file permissions or if this is just a bad install.  I would sure appreciate some help as I am still a fairly new user to linux ...

Thanks!

---

### Post by jda1701 on 2007-04-25
I've only used the LiveCD to install.  Feisty has given me better support on my 22" Widescreen Westinghouse LCM-22w2 monitor.  As far as the alternate CD install goes I haven't used it.  I just checked my install though (upgraded from edgy during HERD 1 release) and lost+found (and for that matter all items in '/' are owned by root/root (doing an ls -l /)

Its possible you might need to backup what data you have and try the liveCD install.  If the Feisty LiveCD can accurately set up your monitor then the settings should be copied over during the install.  


Good luck!

---

### Post by kathmary on 2007-04-25
Thanks for your answer! I will try the live cd (it did work with edgy)...  I just downloaded it and will give it a shot now!

---

### Post by kathmary on 2007-04-26
It appears that Feisty will not install correctly on my hardware from the live cd or the alternate.  I redownloaded the alternate cd and downloaded the live cd yesterday.  I checked the md5sums and burned them to cd, both disks were valid.  

I retried the alternate cd install...and had the same results.  The install stops for a long time, maybe 20 mins at 85% brltty-x11  and then starts again.  When the OS is booted there are files I cannot access, namely the "Lost + Found".  These files are marked with a red square and they are also listed as unreadable.  If I try to open one of them, I get an error that says I do not have the proper permission.

I then tried the live cd and also ran into the same error as above.  This time, the installation pauses at 83% saying that the language packs are being downloaded.  I used the option to skip this that is displayed.  I do not have an internet connection going during install.  It will finish, but I get the same results as above.

I then went back to my installation cds and retried edgy.  Just as I thought, this problem did not occur in edgy on my hardware, which is : Compaq Presario 6326se Desktop 2 ghz 1 gb ram and Compaq 7550 crt monitor.  It has the onboard intel graphic 845.  

Anybody have an idea what is happening?  I am trying to get a clean install of feisty if possible.  I would appreciate some feedback on what I can do next.  Thanks for all your help!

---

### Post by zvacet on 2007-04-26
yes I can tell from my expirience that when it comes to brltty-x11 you have to wait for some time and after that installation complete.that fact made me nervous during installation but everything comes to the happy end.Try this

```
sudo aptitude update && sudo aptitude upgrade
```

If that doesn´t give any result you can try upgrade from Edgy with alternate CD.

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by kathmary on 2007-04-27
I tried again to install Feisty and got the same problem.  I did try sudo aptitude update && and sudo aptitude upgrade.   It was very hard to get the repository list to update.  Finally, the main server worked.  After updating 6 packages, I still have the problem... the Lost + Found  folder is unreadable along with other files.  I don't think my install completed or something of that nature.   It doesn't seem like I have been shown all the updates even though I have the repos enabled.  Feisty just does not want to install!  It is not my installation  disks because I have downloaded from more than one site with the same results, and I have made several disks that create the same install.   Each download and disk has been checked  for validity.  The only success I had was updating from edgy and I hoped I wouldn't have to install it again just to upgrade. 

Does anyone know how to install in debug mode?


BTW....Thanks for your answers!

---

### Post by asgard123 on 2007-07-17
I get this problem as well. I am on a macbook pro 17" with core duo 2.16

Did anyone solve the problem?

---

