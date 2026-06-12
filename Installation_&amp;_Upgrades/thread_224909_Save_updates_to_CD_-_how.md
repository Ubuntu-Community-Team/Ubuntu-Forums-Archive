---
title: "Save updates to CD - how?"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by fatalGlory on 2006-07-28
Hi, I've got a friend who I've convinced to switch to ubuntu from winXP.  He's not particularly a techie so it surprised me when he got comfortable with it even faster than I did, lol.

But he has a problem, his net connection at home has a very woeful 250Mb a month cap shared between 6 people.  He wants to use update manager (not to mention apt-get) to update his system from the shipit CD install but just doesn't have the bandwidth.  I on the other hand have a 20Gb cap - much more than I've ever needed.  Is there any way for me to save all the updates from update manager to a CD and give them to him?

Anyone who could point me to useful info/tuts/howtos would be great.

Cheers

---

### Post by yopnono on 2006-07-28
Download all the packages you like to keep then just move them to a new folder named like dapper_debs put this in you cd.

Then if you like to install IE: gimp type "sudo dpkg -i gimp" in the terminal, in your cd folder that have all the .DEB files.

---

### Post by fatalGlory on 2006-07-28
So, just saving the debs and manually installing via dpkg doesn't break apt's database of dependencies or anything?  If I do this, will update manager recognise that the updates have been installed?

---

### Post by yopnono on 2006-07-29
> **fatalGlory said:**
> So, just saving the debs and manually installing via dpkg doesn't break apt's database of dependencies or anything?  If I do this, will update manager recognise that the updates have been installed?

This works for me. The .deb will tell you if you need some more files.
And yes the synaptic recognise all the files installed and update them when needed. 

other way is to copy all the deb in to the "/var/cache/apt" and select the files you like to update /install from synaptic. 

Then synaptic will use the files in you cache, so it don't need to download them.

---

### Post by Matchless on 2006-07-29
Hi,
   Hope this helps, as I use this method quite a lot:

How to make your own repositories:

Packages or applications are normally kept in repositories that can be accessed from the Internet. These repositories contain tested and specially compiled versions of  software packaged for a specific flavour of Linux. The unfortunate thing is that if you can only access the Internet with a dial up connection it takes very long to get what you want and if you have to reinstall or install on another PC then you have to spend a lot of time on the Internet downloading again. An example of this would be when a new kernel version is released and all the packages have been recompiled, as such a download in the past has taken 6 to 12 hours to download on a dial up line. If you  have off line access to these updates after the first download you can update all your other PC's within minutes. This is the best way of keeping all the programs you have installed and/or downloaded for re-use without losing them and having to download again. 
Ubuntu comes with Synaptic installed by default which is an excellent tool for managing your software packages. Unfortunately Kubuntu again comes with Adept, which is not all that great, but this can easily be solved by just installing Synaptic from the Ubuntu CD or using Adept download and install it from the repositories. 
I am hoping that someone would one day write an option for Synaptic that would give it an option from the gui to save your packages to a local repository. 
Note: If you do not yet have Synaptic installed and would like to do so, use the Ubuntu Install CD or your own local repository CD, put  in drive and type sudo apt-cdrom add, you will be asked for a name of your choice in some cases, add anything you prefer. Now use sudo apt-get install synaptic or any other files without going online.
It is also a very good idea to install Krusader just after Synaptic as it has great file managing features, especially in root mode and can be used to set up your folders etc. Unless you prefer or understand how to use Konqueror or Nautilus.

Creating your own local repository:

1)Create a folder on your Desktop called Repos, by right clicking on the Desktop, Create new, Folder and enter Repos. Open this folder and use the same method to create a folder called Cache and another called Extras. The Cache folder will be for the downloaded and installed .deb packages copied from your cache and the Extras will be for any other packages that you download and install without a package manager and may or not be .deb files, msttfonts, modem drivers, full applications, templates etc.
2)When you have a bunch of .deb files and you require your package manager to be able to see these you need to have a file created called Packages.gz. Basically this file contains a list of the latest versions of the packages in the folder.
3)Now use Krusader  (in root mode) (or your favourite file manager) and open /var/cache/apt/archivers, select all the files in there and copy then to your new local repository /home/<username>/Desktop/Repos/Cache
4)Open the konsole and 
cd Desktop/Repos/Cache
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz  
this creates the Packages.gz file
5)Now use Krusader, select Cache, Properties, Permissions, to set the permissions for the Cache folder including all the files and sub folders to be read and written to by anyone – this is to allow the file to be copied to a CD and used on another PC without permission problems.
6)Every time you change the Cache folder by adding another file you must recreate this Packages.gz file before the package manager will see it.
7)Now just copy the complete Cache folder to a CD. You can now pop it into any Ubuntu PC, open Synaptic, click Add CD, give it any name you want and then start installing or updating via Synaptic from the CD. It may also be a good idea to disable any other repositories in Synaptic while using the CD.

---

