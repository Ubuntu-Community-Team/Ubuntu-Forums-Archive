---
title: "New Program to apt-get --download-only"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by scrooch on 2006-11-29
Since shortly I also feel the pain of running a stock Edgy install without an Internet connection. This is a problem for me because:

-I would like to use vlc
-Specific gstreamer packages and codecs
-Some games from the reps
-Some other meta packages.

The advice to users given is to apt-get install package on the off line system, write down all packages and dependencies and download them via a computer with a network connection. 

So I tried tracking down dependencies and downloading them to get vlc working. There are so many dependencies, of which half is already installed by default. Besides that, if you add sources like universe to an off line system, it won´t be able to find vlc and its deps in the first place.

So I came up with this idea:

A multi platform apt-get --download-only command / program! Hit apt-get -d vlc and have all packages automatically being download to a directory. 

A nice option would be if you could preselect if you use for example dapper, edgy or feisty so apt-get knows what sources.list to use. And if you can select which packages you already installed so your to download dependencies could be trimmed down.
It could also be used to get security updates / bugfixes on offline systems.
And you should be able to select to only use official reps, multiverse, universe, add sources yourself, etc

I´m not a coder myself but it seems possible to me. Although a multi platform gui program would be excellent, just a command line tool would be awesome as well (as long as it´s also possible to use on windows, most of us probably only have internet at work if we don´t have it at home)...

Let me know what you think.

For example, would it be possible to port Synaptic to be platform independent, specialised in cases described above?

---

### Post by az on 2006-11-29
> **scrooch said:**
> Since shortly I also feel the pain of running a stock Edgy install without an Internet connection. This is a problem for me because:

-I would like to use vlc
-Specific gstreamer packages and codecs
-Some games from the reps
-Some other meta packages.

The advice to users given is to apt-get install package on the off line system, write down all packages and dependencies and download them via a computer with a network connection. 

So I tried tracking down dependencies and downloading them to get vlc working. There are so many dependencies, of which half is already installed by default. Besides that, if you add sources like universe to an off line system, it won´t be able to find vlc and its deps in the first place.

So I came up with this idea:

A multi platform apt-get --download-only command / program! Hit apt-get -d vlc and have all packages automatically being download to a directory. 

A nice option would be if you could preselect if you use for example dapper, edgy or feisty so apt-get knows what sources.list to use. And if you can select which packages you already installed so your to download dependencies could be trimmed down.
It could also be used to get security updates / bugfixes on offline systems.
And you should be able to select to only use official reps, multiverse, universe, add sources yourself, etc

I´m not a coder myself but it seems possible to me. Although a multi platform gui program would be excellent, just a command line tool would be awesome as well (as long as it´s also possible to use on windows, most of us probably only have internet at work if we don´t have it at home)...

Let me know what you think.

For example, would it be possible to port Synaptic to be platform independent, specialised in cases described above?

I think there is already a spec for this and it is in the works.

Otherwise:

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

or create a file with all the packages to download and then download them on a net-connected box:

sudo apt-get install --print-uris vlc > file

Once you download the deb, you can turn that directory into a repository by running 

dpkg-scanpackages . /dev/null > Packages

Which will create a packages file for your repo.  The add the directory as a

deb file 

entry in your sources list.

---

### Post by yota on 2006-11-29
Hi,

some time ago I've made a script (in attachment) that downloads a package and all its dependencies for a friend that has only a dial-up connection at home, but plenty of bandwidth at work.
It's very simple, and does not satisfy all your requests, but I think it can come handy.
It works only on a box with the same debian version of the "target", checks if a package has already been downloaded and support resume of partially downloaded files.

base usage is:
```

aptree.sh <packagename> [target directory]

```
Multi platform can be achieved through vmware (the player is free): you can create a virtual machine with edgy and use it to download the packages to bring back home.
Pre-made VMs are availabe at [http://www.vmware.com/vmtn/appliances/directory/](http://www.vmware.com/vmtn/appliances/directory/)

Feel free to share your feelings.

---

### Post by scrooch on 2006-11-30
Well yeah, VMWare would be an excellent sollution. But it´s a but much to install Vmware and a complete Ubuntu install just to get a specific set of packages for another computer.

Somebody, please, just write a program in Java and or Mono which can do this...

Would it work if I mail a proposition to the Synaptic people to include something like Offline mode, where a file is created with all packages installed on the specific computer plus a program to run on a different computer... If you would write this program plus file to a disc and run it on a different computer, the program would exactly know how and what to install (incl dependencies) based on that config file build on base of Synaptic on the original system.

Are there objections to this idea? :rolleyes:

---

### Post by yota on 2006-11-30
Hi, I'll leech azz's suggestion trying to improve it:
```

apt-get -y --print-uris install *PACKAGENAME* |grep http |awk '{print $1}'|tr -d "'"

```
I've added a little cleaning and suppressed requests.
You can redirect output to a file in this way
```

apt-get -y --print-uris install *PACKAGENAME* |grep http |awk '{print $1}'|tr -d "'" > file.txt

```
Once you get to work you can use your downloader of choice to process the list like
```

wget -i file.txt

```
Obiously we can put the command in a script for ease and even make a graphic interface with zenity.
If you like this solution we can polish it a bit and go ahead (I suppose this would be more in the spirit of Free Software, than asking someone to do the work for you ;) )
Moreover synaptic is a frontend of apt so if you would like to port synaptic to java, you would have to port apt (which is a frontend to dpkg) too... IMHO this would be a lot of effort without sensible advantages.

---

### Post by scrooch on 2006-11-30
Thanks for your great reply Yota. I´ve written down the instructions, I´m going to try this asap and I´ll let you know if it worked.

This solution would fit all my needs... a GUI isn´t really necessary, its more like a nice gimmick or something. I´m very thankful for these commands above :-D

---

### Post by scrooch on 2006-12-01
Well the script mentioned here above didn´t work. The problem is we assumed that the sources.list was already complete and a apt-get update was performed on the offline computer.

The problem is I can't add online sources like multiverse and then apt-get update because this computer is only offline. When I want to generate the file with the metapackage and dependencies, like apt-get install vlc, you'll get a vlc not found error.

So maybe we should look for another approach. Is there anything I can do?

---

### Post by yota on 2006-12-01
You're right: I supposed that the network-less pc could at least do an 'aptitude update' on dial up.

If this is not the case, we have to do the update by hand, unfortunately I'm not sure of how the full process goes; AFAIK the repositories indexes are downloaded and decompressed into /var/lib/apt/lists/
and their names are derived from urls like:
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)
in this way:
[LIST=1]
[*]timming the "http://"
[*]substituting '/' with '_'
[/LIST]
the result is (in our example):
archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages

I think you should download the files for your repositories, put the uncompressed and correctly renamed results in /var/lib/apt/lists/ and finally issue an
```

apt-cache gencaches

```

This seems to me quite an effort... I suppose there're easier ways to get the thing done, if someone has better hints please post!

---

### Post by scrooch on 2006-12-04
It sounds like basically it comes down to 

1 a stand alone apt-get which automaticly downloads all the packages to install for your offline system
2 with the option to automatically import the reps of choice (dapper, edgy with each multiverse, universe etc)
3 able to create and use config files of offline system and apply this to the apt-get for windows


Now who´s has the skills for writing this peace of art? :confused:  Please don´t let this die :neutral:

This week I´m going to draw some mockups of a GUI, I hope to get some coders enthusiastic with this.

---

### Post by yota on 2006-12-04
Hi scrooch,

I saw that someone else is working on the same issue, have a look at this thread and let me know:

[http://ubuntuforums.org/showthread.php?t=310020](http://ubuntuforums.org/showthread.php?t=310020)

---

### Post by scrooch on 2006-12-15
Seems there was no windows version made there.

---

### Post by scrooch on 2006-12-18
I think I´ve got the solution. I download vlc and an ext3 driver for windows. This way I don´t have any dependency download-hell and with the ext3 driver I still can access all the data, but from windows.



](*,)

---

