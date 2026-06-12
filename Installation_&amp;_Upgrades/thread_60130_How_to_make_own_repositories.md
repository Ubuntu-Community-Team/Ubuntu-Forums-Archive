---
title: "How to make own repositories"
date: 2005-08-26
forum: Installation &amp; Upgrades
---

### Post by Matchless on 2005-08-26
Hi,
    A lot of this has been published and I found the info a bit confusing and used it to compile this How to for my simpler mind. I could not figure out how to use an external USB CDrom to read the CD repository. To make a CD/DVD repository of your favourite apps and upgrades to eliminate downloads is very easy if used in conjunction with Synaptic.
Please let me know if it needs updating or changes.

_How to make your own repositories:_
Last updated: 2005/08/24 by Andre
This is the best way of keeping all the programs you have installed and/or downloaded for re-use without losing them and downloading again and I would have appreciated it if Synaptic could get such a facility added by the developers in the next releases.
1) Create the folders for the files you would like to keep in your own repository. The following examples are shown. On the desktop create a new folder called "Repositories" to keep all your separate repository folders in. Inside this, create new folders called  Cache_deb_D1, Extras_deb_D1, Extras_deb_D2 etc. This is just to ensure that you use the next folder once your collection exceeds the size of a CD, if you are writing to one. If using a local folder or a DVD you obviously have higher limits to keep in mind.
2) The next step is to copy all your xxx.deb files to the folders. Go to /var/cache/apt/archives and copy all the files to your folder Cache_deb_D1.
3) cd in to your folder  cd    /home/<username>/Desktop/Repositories/Cache_deb_D1
Now do the next command to create the Packages.gz file that is needed to read the contents for Synaptic     to see your repository.
dpkg-scanpackages   .   /dev/null   |   gzip   -9c   >   Packages.gz
4) Please note that every time you add any more xxx.deb files to this folder, you have to create a new    Packages.gz file as above before your file will show when reading your repository..

5) There are a couple of ways to use your own repositories:

	a) Keeping the files on your own PC
	Edit the /etc/apt/sources.list file by adding the following lines
	
## My local repository
	deb file:/home/<username>/Desktop/Repositories/Cache_deb_D1 /
	deb file:/home/<username>/Desktop/Repositories/Extras_deb_D1 /
	
etc. and do this for all your folders with .deb files.
Once the bug in Synaptic is sorted out you will be able to add a repository directly in Synaptic, at the moment if you click on add it opens the edit window erroneously.( my copy of v0.56)
Now open Synaptic, click on reload, and your new file will be recognised and you will be able to install from it without going online and downloading.
	
b) Using a CD/DVD as a repository
Burn a CD containing all the .deb files and the Packages.gz file as from above.
	Put the CD in the drive and go to Synaptic, Edit, Add CD Rom.
You will be asked to type in a description of the repository, type in name such as: My repository Disk 1 or whatever you want.
You can now install the files from the CD/DVD instead of downloading.

	c) Keeping repository on your local server
Put the above folder (in a) with .deb files and the latest Package.gz on your server and serve this directory over http and/or ftp by typing the following:

	sudo 1n -s /<path>/Cache_deb_D1 /var/www/
Assuming that the URL for the repository directory being served is [http://localreposerver/Cache_deb_D1](http://localreposerver/Cache_deb_D1)    or   [ftp://localreposerver/pub/Cache_deb_D1](ftp://localreposerver/pub/Cache_deb_D1) 

You now have to configure each remote machine that uses this server to see the repositories. Edit each machines /etc/apt/sources.list  to contain the following line:
	deb [http://localreposerver/Cache_deb_D1](http://localreposerver/Cache_deb_D1) /
		or
	deb [ftp://localreposerver/pub/Cache_deb_D1](ftp://localreposerver/pub/Cache_deb_D1) /
		or use the IP address
	deb [http://192.168.0.1/Cache_deb_D1](http://192.168.0.1/Cache_deb_D1) /

A suggestion is to always add these entries in the Sources.list at the top just below the original Ubuntu or Kubuntu CD entry as the fetch from repositories is done from the top down, local install CD, then your repository, then the Internet repositories etc. You do not want to first download something you already have. If this causes problems, just go to sources.list and comment out the internet sites or even easier, use Synaptic and go to Repositories and uncheck the other sites and only check your CD and then the only repository source will be your checked own file and/or CD/DVD.

Tips on the use of Synaptic to find programs:
Ensure that Synaptic is installed and at the latest version. It comes with Ubuntu, but not with Kubuntu. Install Synaptic by using Kynaptic and uninstall Kynaptic as soon as possible, as it is just too weak for proper use.
Ensure that all repositories are enabled and use Synaptic to reload the lists. Now have a loom at the Synaptic settings. I suggest you decide if you always want to get the highest/latest version or if you want to stick to the “hoary” version. Also ensure that you have checked the box that allows the file to be kept in the cache, otherwise you will just have to download it again if you uninstall it or need it again.
Use the ‘search’ function in Synaptic to search for the program by typing the name or any part of the name in search and the repositories in your updated list will be searched to see if such a program is available. If you have done the above, and have the install CD’s as well as all your own programs available in a repository of your own, life will be sweet.
When the program is found and the square is green it means it is already installed on your ubuntu. If the square is blank with an Ubunto icon next to it, it means it is ready for ubuntu from the ubuntu repositories. These are normally stable installations that have been tested.
If the square is blank, it means that the programs shown are available on the repository, scroll the list and mark by right clicking and select for installation. You can also select to just see the uninstalled programs and by i.e. only looking at your repository you will see what programs you still have that has not been installed etc.
Once you have marked all the files you want to download, go to Apply in Synaptic and click. You will be asked if you want to download only or install. In both cases the downloaded files are stored in the cache. You can use the download only option to download programs while you are connected to the Internet for use or installation later or just to fill up your own repository.  If you click install, you can test the application and later go exactly the same way with Synaptic and just select remove. The files will stay in the cache and can be installed again later without going on line again. Here it is rather suggested that you copy them from the cache to your own repository. If you ever tick the Synaptic option to not keep the files it seems as if the cache is cleared and the downloaded files are lost.
The idea now is to save all these preferred files to a folder or CD as shown above and if Ubuntu is reinstalled for any reason all the updates and extra installations can be done from the CD and eliminate another few hours on line downloading again.
Finally also make a copy of your /etc/apt/sources.list file and keep it in your repository as well. You can then just overwrite the old one on a new installation with this one.

Regards
Matchless

---

