---
title: "Why not single file installer for softwares"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by alokmystic on 2012-07-17
Hi to all, 

First of all I want to say thanks to all the developers of Ubuntu. I hate Mircosoft and love open source philosophy  , hence installed ubuntu on my system. I can do everything in ubuntu, whatever I was doing in windows, but in addition, as we all know its fast and secure. I really love it , and want to promote it among my other friends who are using windows, and this is where my problem starts.


After installing ubuntu as we know we need to intall Gstreamer Extra or some other codec pack. without these codec pack , computer is useless for non-programmers, as common people use computer for audio, video and internet. 

Now dont you think that there should be some easy way to install these Codecs (and all other softwares offline). Now I know there is a thread in this forum ,something like "offline software installation", but as far as I can understand that thread, that thread simply tell me a procedure to create installer from all of the softwares installed on my system.  So that I can install all software in another ubuntu system. 


But the thing is , why cant we have seprate installer of each software like a single .deb file . or a folder containing a deb file. 

When open source is all about transparency, why something mysterious happens in software center. we dont come to know what files it is downloading, even if we check files in chache folder, we come to know that for a single software it downloads many .deb files, so in which order we should run those file . 

similarly in case of gimpshop (windows intaller). It needs internet,. Why they dont provide a complete installer, so that it can also be installed on computers who dont have Internet connection .

this thing in my opinion somehow restricting the reach of open source software among masses.  Why they force us to use internet, why they dont promote sharing these softwares offline.


So my request is

plz tell me a way to make a dvd collection of all softwares of ubuntu, like we can make collection of windows software and can install them separately. 

Thanks in advance

---

### Post by Cheesehead on 2012-07-17
> **alokmystic said:**
> Now dont you think that there should be some easy way to install these Codecs (and all other softwares offline).

There are several easy ways. The easiest for offline is the apt-zip package, assuming you have an online linux system to execute the apt-zip scripts. If not, then use the debs from [http://packages.ubuntu.com](http://packages.ubuntu.com).



> **alokmystic said:**
> But the thing is , why cant we have seprate installer of each software like a single .deb file . or a folder containing a deb file.

Double-clicking on a deb file launches the standard installer. No additional software is needed.

It seems like you are using the wrong tool to install. Don't blame the tool. Of course Software Center cannot install gimp without downloading it first. Ubuntu has many tools. If you need help choosing the right one, just ask and describe your needs.

Software Center can be a handy catalog of what's available, but there are others, too, just as good (and faster and easier to use).



> **alokmystic said:**
> When open source is all about transparency, why something mysterious happens in software center. we dont come to know what files it is downloading, even if we check files in chache folder, we come to know that for a single software it downloads many .deb files, so in which order we should run those file . 

similarly in case of gimpshop (windows intaller). It needs internet,. Why they dont provide a complete installer, so that it can also be installed on computers who dont have Internet connection .

this thing in my opinion somehow restricting the reach of open source software among masses.  Why they force us to use internet, why they dont promote sharing these softwares offline.

This section is very funny. Er, please try to avoid the crazed, accusatory ranting. Other community members who could help will quickly learn to ignore your posts.



> **alokmystic said:**
> plz tell me a way to make a dvd collection of all softwares of ubuntu, like we can make collection of windows software and can install them separately.

If you are not going to use apt-zip, then:

1) Use Software Center or apt-cache or Synaptic or another catalog to figure out which packge you want.
2) Use apt-get --simulate or Synaptic to list all the packages (including dependencies) you need to install.
3) Online, download the list of debs from [http://packages.ubuntu.com](http://packages.ubuntu.com)
4) Put the debs in /var/apt/cache/archives
5) Use Software Center or Synaptic or apt-get or dpkg to install the debs (so they will automatically install multiple dependencies in the correct order).

---

### Post by ajgreeny on 2012-07-17
There is a big difference in the way that Linux handles all the libraries and dependencies that are needed for an application to be installed, compared with windows applications.

Normally a windows setup.exe file that  installs a program will contain all the libraries (dll) files etc etc that are needed for it to run, or they will be on folders in the archived installation medium. Therefore there is not often a need to install other applications just to get the first one to work.  This often results in a duplication of libraries, and an incredibly unwieldy filesystem, with files from an installation spread all over the multitude of folders both in the windows filesystem and the users own section, Documents and settings, or whatever it's called.

Linux, however, uses a system  of dependencies for installing any package (application) and the installer looks to see if these exist in the filesystem already; if they do it does not need to pull in any more copies of the same thing from the repositories of the distro.  If there are no dependencies available, which can happen when you try to install something from a source other than the official repos, you end up in what came to be known as "dependency hell" where application A needs package B, which in turn needs package C, and so on.

Linux users need to forget the ways of windows, where you search online for an application, download it and then double click on the setup file and hope that all is well.  Use the official repos, or at least stay within trusted third party repos, eg ppa repos, and I think the Linux way is much easier to use, and much more secure, of course, than the windows system that you seem to want.

---

### Post by Mark Phelps on 2012-07-17
> When open source is all about transparency, why something mysterious happens in software center. we dont come to know what files it is downloading, even if we check files in chache folder, we come to know that for a single software it downloads many .deb files, so in which order we should run those file .

Open Source is "all about" -- the ability to obtain and modify the source code yourself. That is NOT about transparency -- unless by that, you mean the ability to see "into" the software to see the actual code.  It has nothing to do with how the software behaves.  If you don't like what it does, or how it does it, open source gives you the option of changing it yourself.

> similarly in case of gimpshop (windows intaller). It needs internet,. Why they dont provide a complete installer, so that it can also be installed on computers who dont have Internet connection .
There are literally tens of thousands of packages -- far beyond the capacity of even a blue-ray disk to hold. They DO provide a complete installer -- it's just that you have to go to the repositories to get the packages.

> this thing in my opinion somehow restricting the reach of open source software among masses. Why they force us to use internet, why they dont promote sharing these softwares offline.
 You keep beating the drum of "open source" -- which would be OK, except that obtaining Linux apps using the Internet has nothing to do with open source.

---

### Post by Frogs Hair on 2012-07-17
One reason the Ubuntu restricted extras package is so named is because the codecs included are restricted in some countries/areas and can't be distributed with the ISO. Proprietary and/or possibly restricted packages have to installed by the user.

---

### Post by alokmystic on 2012-07-18
> **Cheesehead said:**
> There are several easy ways. The easiest for offline is the apt-zip package, assuming you have an online linux system to execute the apt-zip scripts. If not, then use the debs from [http://packages.ubuntu.com](http://packages.ubuntu.com).

as my aim is to install software offline, choosing second option I went to the url , what next I should do? I went to [http://packages.ubuntu.com/precise/debian-installer/](http://packages.ubuntu.com/precise/debian-installer/)

now where is the .deb file of Gstreamer Extra, there is not the word codec anywhere on the page. Consider me a complete beginer , and kindly  tell me what should I do on the link provided by you to get the offline installer of Gstreamer Extra.




> **Cheesehead said:**
> Double-clicking on a deb file launches the standard installer. No additional software is needed.

that I know , but when software center install any software, for example when it install gimp it download many .deb file (as found in cache folder). so if I copy all these .deb file from cache folder, in which order i need to double click the various .deb files, this is the question. 

> **Cheesehead said:**
> It seems like you are using the wrong tool to install. Don't blame the tool. Of course Software Center cannot install gimp without downloading it first. Ubuntu has many tools. If you need help choosing the right one, just ask and describe your needs.

I never said that software center should not downloading software, because even I know that without downloading it how software center can install it. but my question is in windows first I donwload a software, then either I get a single exe file or a zip file containing all files which can be extracted in a folder, so after installing the software I can copy the downloaded file in a dvd and can install the same software offline in as many system as I want. Here after the software system download a particular software, you finds many .deb file (for the same same software), now if you copy these .deb files and write it on a dvd , in which order you need to run the different .deb file to install it offline, in another system. for example in my archives folder right now I can see the following files 

gstreamer0.10-ffmpeg_0.10.13-1_i386.deb
gstreamer0.10-fluendo-mp3_0.10.15.debian-1ubuntu1_i386.deb
streamer0.10-plugins-bad_0.10.22.3-2ubuntu2_i386.deb
gstreamer0.10-plugins-bad-multiverse_0.10.21-1_i386.deb

similary for gimp I have the following files in archive folder

gimp_2.6.12-1ubuntu1_i386.deb
gimp-data_2.6.12-1ubuntu1_all.deb
gimp-help-common_2.6.1-1_all.deb
gimp-help-en_2.6.1-1_all.deb

Now if I copy these files and double click it , will it be installed in another ubuntu computer, if yes then in which order I should click it (which file first and which one last)[/QUOTE]





> **Cheesehead said:**
> This section is very funny. Er, please try to avoid the crazed, accusatory ranting. Other community members who could help will quickly learn to ignore your posts.
If this section sounds funny to you, then answer a simple question by me. I have a computer in which I have windows xp, and I want to install gimpshop ([www.**gimpshop](www.**gimpshop)**.com) offline, that is first I want to download gimpshop in some other system which has internet and want to write gimpshop in a dvd, then want to install it on the system which doesnt have the internet , from that dvd. gimpshop official website doesnt provide any offline installer. so if my question was funny, what is the answer of this question?[/QUOTE]





> **Cheesehead said:**
> If you are not going to use apt-zip, then:

1) Use Software Center or apt-cache or Synaptic or another catalog to figure out which packge you want.
2) Use apt-get --simulate or Synaptic to list all the packages (including dependencies) you need to install.
3) Online, download the list of debs from [http://packages.ubuntu.com](http://packages.ubuntu.com)
4) Put the debs in /var/apt/cache/archives
5) Use Software Center or Synaptic or apt-get or dpkg to install the debs (so they will automatically install multiple dependencies in the correct order).

I already explained why I cant use apt-zip(offline option not available as per you), option 3) (unable to find gstream extra on this page or on [http://packages.ubuntu.com/precise/debian-installer/](http://packages.ubuntu.com/precise/debian-installer/)) and option 4) (multiple .deb file for a single software and dont know in which order I should run it)

regarding command line option, as I am a normal computer user, not a programmer, plz guide me line by line, how I can extract the files in a dvd so that dvd can be used to install gstream extra offline on other computers having ubuntu. 

Thanks in advance
:)

---

### Post by alokmystic on 2012-07-18
> **Mark Phelps said:**
> Open Source is "all about" -- the ability to obtain and modify the source code yourself. That is NOT about transparency -- unless by that, you mean the ability to see "into" the software to see the actual code.  It has nothing to do with how the software behaves.  If you don't like what it does, or how it does it, open source gives you the option of changing it yourself.


There are literally tens of thousands of packages -- far beyond the capacity of even a blue-ray disk to hold. They DO provide a complete installer -- it's just that you have to go to the repositories to get the packages.

 You keep beating the drum of "open source" -- which would be OK, except that obtaining Linux apps using the Internet has nothing to do with open source.

What you said is technically 100% correct, no doubt about it, as per the technical and legal definition this is what open source is all about, (ie any one can see source code). 

But the context in which I asked the question is , open source movement started in a response to the restrictions put by proprietary softwares, so in a way we can say that open source movement want people to use open source software instead of proprietary software (now it depends upon opinion). that is why I am asking, what is the point of not providing offline installer.  If I say to my friends that open source softwares are better, they first want to try it on their existing windows system, rather then installing linux on their system. now suppose they want to try some image manipulation software, and if they have internet , I can easily tell them to install gimshop ([www.**gimpshop](www.**gimpshop)**.com) and they like it, as it is almost like photoshop, but I cant do the same with my friends who doesnt have internet, so dont you think this will some how ristrict the popularity of gimpshop (which is an opne source software). Now technically you can say that being open source doesnt mean it should provide offline installer. but practically many people still dont know about gimpshop and use pirated version of photoshop, just because they dont have internet. they can bring a pirated version of photoshop on a dvd and can install it on their system , but they cant do the same with gimshop, if open office can provide its offline installer, why cant gimpshop do the same.

---

### Post by UltimateCat on 2012-07-18
> **ajgreeny said:**
> There is a big difference in the way that Linux handles all the libraries and dependencies that are needed for an application to be installed, compared with windows applications.

Normally a windows setup.exe file that  installs a program will contain all the libraries (dll) files etc etc that are needed for it to run, or they will be on folders in the archived installation medium. Therefore there is not often a need to install other applications just to get the first one to work.  This often results in a duplication of libraries, and an incredibly unwieldy filesystem, with files from an installation spread all over the multitude of folders both in the windows filesystem and the users own section, Documents and settings, or whatever it's called.

Linux, however, uses a system  of dependencies for installing any package (application) and the installer looks to see if these exist in the filesystem already; if they do it does not need to pull in any more copies of the same thing from the repositories of the distro.  If there are no dependencies available, which can happen when you try to install something from a source other than the official repos, you end up in what came to be known as "dependency hell" where application A needs package B, which in turn needs package C, and so on.

Linux users need to forget the ways of windows, where you search online for an application, download it and then double click on the setup file and hope that all is well.  Use the official repos, or at least stay within trusted third party repos, eg ppa repos, and I think the Linux way is much easier to use, and much more secure, of course, than the windows system that you seem to want.

I learned my lesson with that .run file
Root should be taken seriously; thanks again ; ajgreeny

---

### Post by darkod on 2012-07-18
First of all, please don't imply only programmers need to know to use the command line. When it was mentioned, your reply is that you are a normal computer user not programmer.

Programmers and software developers develop software, and in lots of cases it has nothing to do with command line.

As a computer user you should know how to open a terminal and type a command once in a while. Even in windows I regularly do this. If you don't want to do it, that's your problem.

Then, is it really that impossible to connect that computer to the internet at least temporarily, and install what you want to install? Due to the different nature of how linux installs software, there will be many depending packages you need to download, and some of them may also depend on other packages. So, you are looking into lots of packages that you need to chase by hand, download, move to the other computer just so you can execute one installation.

As far as searching the packages is concerned, don't go to the link you posted (inside the precise version), go to the link cheesehead posted, the general packages link. In the middle of the screen there is a search field. Put the name of the package you want in there, there is another drop down box where you select the version (it should be precise by default), and click the search button.

That will show you the found packages. Click on the package you want, and it will show you all the packages it depends upon.

Once you see the list, I assume you will want to connect the computer to the internet and do it the easy way. :)

---

### Post by mastablasta on 2012-07-18
> **darkod said:**
> Then, is it really that impossible to connect that computer to the internet at least temporarily, and install what you want to install? 
 
in some countries internet is extremely expencive for the people that live there. and not everyone in this world has internet access (no or poor infrastructure - it's not cool donwloading 200MB+ over expencive dialup) or portable computer to take it to nearest (free?!) wi-fi spot. which is why Mark Shuttleworth had a project where Ubuntu CD could be obtained at an ATM like maschine.
 
the question makes sense.
 
however, as i know Synaptic has an option to create a package for offline isntall, there is also at least one forum member's effort to provide offline installers.
 
additionally sometimes there are offline installers provided (for example script with all dependencies included). the user could also compile from source. the biggest issue are dependencies.
 
i don't know why Gimpshop doesn't use offline installer, however Gimp does have such an installer available.
 
i believe Debian has repositories available for offline install and it's 30+ DVDs.

---

### Post by darkod on 2012-07-18
> **mastablasta said:**
> in some countries internet is extremely expencive for the people that live there. and not everyone in this world has internet access (no or poor infrastructure - it's not cool donwloading 200MB+ over expencive dialup) or portable computer to take it to nearest (free?!) wi-fi spot. which is why Mark Shuttleworth had a project where Ubuntu CD could be obtained at an ATM like maschine.
 
the question makes sense.
 


I agree about the internet access, but I was under the impression the OP will still do the operation in the same country. So, unless you can go to a place with free internet to prepare the packages, you still have to download the same amount of data, only in a more complicated way chasing up the dependencies.

Even if we are talking about two locations, one with and the other without internet access, it's much faster moving the computer to the location with internet, than what he is trying to do.

ajgreeny explained it very well, that's how linux systems are set up. That's why you can install ubuntu on 4GB, try doing that with win7. And why the windows size grows so fast and big when starting to install software.
I guess needing internet for installing software is the "downside", you have to accept that.

---

### Post by alokmystic on 2012-07-18
> **darkod said:**
> First of all, please don't imply only programmers need to know to use the command line. When it was mentioned, your reply is that you are a normal computer user not programmer.

Programmers and software developers develop software, and in lots of cases it has nothing to do with command line.

As a computer user you should know how to open a terminal and type a command once in a while. Even in windows I regularly do this. If you don't want to do it, that's your problem.

Thanks for this discource, but I was expecting some line by line instruction about how I can do it in terminal, I know how to open terminal, and visit different directory in terminal. Plz instruct me the exact command that I need to type in terminal to get all the files of gstream extra, which can be used to install it offline. 

There was a time when linux was very bad as far as desktop environment was concerned, it used to crash a lot, and was very slow, I tried red hat linux many years ago, and it was slower than xp and used to crash a lot hence I switched back to XP. there was a genuine need to make more and more functions available in desktop mode, Ubuntu did the same , and hence today its a very popular among Linux versions, we still have scope of improvement in this area. Its a well know fact that most of the user who only use computers and dont have any interest in how it works , prefer GUI, instead of CLI. It's not only my problem , but its the problem of majority of computer users , (if you prefer to use word problem for it).  And as far as I know study of computer science includes topic like "how to make user friendly products". the recent use of ribbon instead of plain menu in office 2007 is an example of it. 

> **darkod said:**
> Then, is it really that impossible to connect that computer to the internet at least temporarily, and install what you want to install? Due to the different nature of how linux installs software, there will be many depending packages you need to download, and some of them may also depend on other packages. So, you are looking into lots of packages that you need to chase by hand, download, move to the other computer just so you can execute one installation.

Yes, it is . Perhaps you are not considering it, but still many people use desktop instead of laptop (including me), which is difficult to move from one location to another. I have a broadband connection which comes with phone line (its not wireless), hence its not possible for me to unplug my phone line from my system and take it to my friend's house, they dont have internet ,and wireless connection unlimited data plans are too costly, as I download a lot.  [/QUOTE]


> **darkod said:**
> As far as searching the packages is concerned, don't go to the link you posted (inside the precise version), go to the link cheesehead posted, the general packages link. In the middle of the screen there is a search field. Put the name of the package you want in there, there is another drop down box where you select the version (it should be precise by default), and click the search button.

That will show you the found packages. Click on the package you want, and it will show you all the packages it depends upon.

Once you see the list, I assume you will want to connect the computer to the internet and do it the easy way. 

I did that, I tried keywords "gstream extra" and "gstreamer both" and got the following as a search result

   *You have searched for packages that names contain [I]gstream extra* in suite(s) *precise*, all sections, and all architectures.       [/I]
[I]Sorry, your search gave no results

[/I]
I would be thankful to you if you try it yourself before suggesting it to a beginner like me, and give me a step by step instruction, like which key word you entered to get the package gstream extra:popcorn:

---

### Post by alokmystic on 2012-07-18
> **darkod said:**
> I agree about the internet access, but I was under the impression the OP will still do the operation in the same country. So, unless you can go to a place with free internet to prepare the packages, you still have to download the same amount of data, only in a more complicated way chasing up the dependencies.

Even if we are talking about two locations, one with and the other without internet access, it's much faster moving the computer to the location with internet, than what he is trying to do.

I dont know about the situations in your country, but here in India, among the people who have computer very few have Internet connections. most of the students buy, second hand desktops (not laptops), which is very difficult to move to a location of Internet access, moving a DVD to the  location of computer is much easier. 

> **darkod said:**
> ajgreeny explained it very well, that's how linux systems are set up. That's why you can install ubuntu on 4GB, try doing that with win7. And why the windows size grows so fast and big when starting to install software.
I guess needing internet for installing software is the "downside", you have to accept that.

I am not getting it, if a package is already installed , the offline installer can check it and would not make another copy of it, instead will use the same copy, as done by software center during installation. so the offline installer file collection it self can be too big (because it will include all library package) , but it can still install the same files that software center install during online installation, so ,how is it going to increase the size of installed software. It happens in windows, because microsoft is not concerned about users, and assume that we all have unlimited disk space.  if microsoft want even they can stop duplication of files in their OS

---

### Post by darkod on 2012-07-18
I think you are not understanding the complexity. We are not talking about installing 2-3 files, potentially it can be 20-30 files (packages) that you need.

For example, the search for gstreamer in Precise gives these results:
[http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all)

I don't know which one exactly you want.

Then, you need to open the link for that package, and check what other packages it depends on. For example, the first package in that list looks like this:
[http://packages.ubuntu.com/precise/gstreamer-dbus-media-service](http://packages.ubuntu.com/precise/gstreamer-dbus-media-service)

You see, it depends on four other packages (marked red). Then you need to check each of them on which packages it depends, and make sure you have them all.

I understand moving a desktop is not as easy as a laptop, but honestly that is much easier than the work you have ahead of you trying to figure out all packages, download and install them.

I can't give you step by step instructions because I don't know all the packages you need too, you will need to investigate that yourself. And I have never tried anything like this, so I don't know the exact steps too, just the general idea.

---

### Post by cortman on 2012-07-18
Since nobody has yet, I'll suggest [Keryx]("http://keryxproject.org/") which is a utility for offline package installation.
I've messed about with offline package installation myself a bit, and I've decided that the easiest way (outside of using Keryx, which I have not yet gotten to work) is to install Synaptic Package Manager and use download scripts.
Now this requires that you get your computer online at least once, for long enough to install Synaptic and update your sources.list, but once that's done it will be easy to get packages and all dependencies from another online computer and install them in the offline one. I even wrote a little[ program in visual basic]("http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/") that interprets Synatptic download scripts for Windows, so you can use the Windows machine to download packages.

---

### Post by alokmystic on 2012-07-18
> **darkod said:**
> I think you are not understanding the complexity. We are not talking about installing 2-3 files, potentially it can be 20-30 files (packages) that you need.

For example, the search for gstreamer in Precise gives these results:
[http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all)

I don't know which one exactly you want.

Then, you need to open the link for that package, and check what other packages it depends on. For example, the first package in that list looks like this:
[http://packages.ubuntu.com/precise/gstreamer-dbus-media-service](http://packages.ubuntu.com/precise/gstreamer-dbus-media-service)

You see, it depends on four other packages (marked red). Then you need to check each of them on which packages it depends, and make sure you have them all.

I understand moving a desktop is not as easy as a laptop, but honestly that is much easier than the work you have ahead of you trying to figure out all packages, download and install them.

I can't give you step by step instructions because I don't know all the packages you need too, you will need to investigate that yourself. And I have never tried anything like this, so I don't know the exact steps too, just the general idea.


I understand the complexity, but either you are not getting my question , or I am unable to ask it properly, Its not about the huge number of files, for example in ms office we have thousands of files arranged properly in folders, but the installer know the proper sequence of running the file. 

what exactly happen when I choose "gstream extra" in software center. It  download all the files required to install gstream and then install them , it also make sure, not to install any existing package twice.  During this process, either software center knows a complete list of files to download and the proper sequence of installing them one after another, or software center fetch this information from some location on Internet. 


Now why cant we download the same set of files in a folder and have a file like we have .bat file in window, which will run the file one after another in proper sequence, why we need to find out the proper sequence  , when it is already either inbuilt in software center or available at some location on Internet. (why software center doesnt reveal this information )

thats why I said that software center behave in some mysterious way.

further when I order software center to install gstream extra it doesnt ask me which package I want to install from the list available at (which infact I dont know, I just know that I need to play media files on my system)

[http://packages.ubuntu.com/search?ke...se&section=all]("http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all")

Like we have  codec pack in window, we simply double click it and it install all codecs, we dont know as a normal user which codec we need or which codec the installer is installing, we simply know that after this our computer will play most of the multimedia file. Cant we have something similar for ubuntu. 

One more question, if installing gstream extra is too difficult in offline mode, does the offline installer is available for vlc media player, if yes, will it run the media files, if I install it on ubuntu without installing gstream extra.

---

### Post by cortman on 2012-07-18
> **alokmystic said:**
> I understand the complexity, but either you are not getting my question , or I am unable to ask it properly, Its not about the huge number of files, for example in ms office we have thousands of files arranged properly in folders, but the installer know the proper sequence of running the file. 

what exactly happen when I choose "gstream extra" in software center. It  download all the files required to install gstream and then install them , it also make sure, not to install any existing package twice.  During this process, either software center knows a complete list of files to download and the proper sequence of installing them one after another, or software center fetch this information from some location on Internet. 


Now why cant we download the same set of files in a folder and have a file like we have .bat file in window, which will run the file one after another in proper sequence, why we need to find out the proper sequence  , when it is already either inbuilt in software center or available at some location on Internet. (why software center doesnt reveal this information )

thats why I said that software center behave in some mysterious way.

further when I order software center to install gstream extra it doesnt ask me which package I want to install from the list available at (which infact I dont know, I just know that I need to play media files on my system)

[http://packages.ubuntu.com/search?ke...se&section=all]("http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all")

Like we have  codec pack in window, we simply double click it and it install all codecs, we dont know as a normal user which codec we need or which codec the installer is installing, we simply know that after this our computer will play most of the multimedia file. Cant we have something similar for ubuntu. 

One more question, if installing gstream extra is too difficult in offline mode, does the offline installer is available for vlc media player, if yes, will it run the media files, if I install it on ubuntu without installing gstream extra.

That's what Synaptic download scripts are- based on what's installed on your machine, it will generate a text file with a list of all required packages. It's even arranged as a script, so you can make it executable and run it on an online machine and it will download the packages but not install them. You can take them over to the offline computer, navigate to the containing folder in your terminal, and run

```
sudo dpkg -i *.deb
```

and it will install them all.

---

### Post by darkod on 2012-07-18
> **alokmystic said:**
> I understand the complexity, but either you are not getting my question , or I am unable to ask it properly, Its not about the huge number of files, for example in ms office we have thousands of files arranged properly in folders, but the installer know the proper sequence of running the file. 

what exactly happen when I choose "gstream extra" in software center. It  download all the files required to install gstream and then install them , it also make sure, not to install any existing package twice.  During this process, either software center knows a complete list of files to download and the proper sequence of installing them one after another, or software center fetch this information from some location on Internet. 


Now why cant we download the same set of files in a folder and have a file like we have .bat file in window, which will run the file one after another in proper sequence, why we need to find out the proper sequence  , when it is already either inbuilt in software center or available at some location on Internet. (why software center doesnt reveal this information )

thats why I said that software center behave in some mysterious way.

further when I order software center to install gstream extra it doesnt ask me which package I want to install from the list available at (which infact I dont know, I just know that I need to play media files on my system)

[http://packages.ubuntu.com/search?ke...se&section=all]("http://packages.ubuntu.com/search?keywords=gstream&searchon=names&suite=precise&section=all")

Like we have  codec pack in window, we simply double click it and it install all codecs, we dont know as a normal user which codec we need or which codec the installer is installing, we simply know that after this our computer will play most of the multimedia file. Cant we have something similar for ubuntu. 

One more question, if installing gstream extra is too difficult in offline mode, does the offline installer is available for vlc media player, if yes, will it run the media files, if I install it on ubuntu without installing gstream extra.

Well, if you expect someone to name all packages one by one, I don't think anyone will have the time to dig them out. That's why I said, it's up to you to investigate on the packages.ubuntu.com website.

You start at the top, and write down and download all depending packages. After that you search for all of them if there are any depending packages, write down and download all of them. Then you keep doing that until there are no more depending packages needed.

Then for installing, you start from the other end. First the lower packages that don't depend on anything, then the second layer that depends on the first (but you already installed them so it should be fine), and so on, until you finally install the top, main package.

I am not aware of any tool that can do this on the computer where you do have internet, maybe someone has another idea.

---

### Post by alokmystic on 2012-07-18
> **cortman said:**
> That's what Synaptic download scripts are- based on what's installed on your machine, it will generate a text file with a list of all required packages. It's even arranged as a script, so you can make it executable and run it on an online machine and it will download the packages but not install them. You can take them over to the offline computer, navigate to the containing folder in your terminal, and run

```
sudo dpkg -i *.deb
```and it will install them all.


Thanks a lot, I have broadband connection on my system, hence downloading synaptic is not a problem, I am installing it right now, will inform you how it worked (it will take me little time to understand how to operate it properly, but I think this suggestion will work). :guitar:

---

### Post by alokmystic on 2012-07-18
> **darkod said:**
> Well, if you expect someone to name all packages one by one, I don't think anyone will have the time to dig them out. That's why I said, it's up to you to investigate on the packages.ubuntu.com website.

You start at the top, and write down and download all depending packages. After that you search for all of them if there are any depending packages, write down and download all of them. Then you keep doing that until there are no more depending packages needed.

Then for installing, you start from the other end. First the lower packages that don't depend on anything, then the second layer that depends on the first (but you already installed them so it should be fine), and so on, until you finally install the top, main package.

I am not aware of any tool that can do this on the computer where you do have Internet, maybe someone has another idea.

so you are saying that software center, download a package , then the package itself tells it which package it should download next, and this keeps on going until all the packages are downloaded, then software center runs it in reverse order, but to run it in reverse order the software center needs to create a log file while downloading the packages, so why cant we fetch this information from that log file.  In this way there is no need for any one to tell me the name of packages one by one, they only need to tell me from where I can look for that log file. And if that log file is temporary, then thats why I said that software center behaves in some mysterious way, and it will restrict ubuntu from growing.  

 the answer given by Cortman seems relevant to the question. I am trying it right now and will inform about it.

---

### Post by darkod on 2012-07-18
> **alokmystic said:**
> so you are saying that software center, download a package , then the package itself tells it which package it should download next, and this keeps on going until all the packages are downloaded, then software center runs it in reverse order, but to run it in reverse order the software center needs to create a log file while downloading the packages, so why cant we fetch this information from that log file.  In this way there is no need for any one to tell me the name of packages one by one, they only need to tell me from where I can look for that log file. And if that log file is temporary, then thats why I said that software center behaves in some mysterious way, and it will restrict ubuntu from growing.  

 the answer given by Cortman seems relevant to the question. I am trying it right now and will inform about it.

I wasn't talking about Software Centre, I was talking about the website packages.ubuntu.com. You didn't have a look at it, and the two links I posted as example? Can you see how it marks with red dots all packages needed, etc.

It's like a pyramid. You start at the top with a single package. But that package needs 4 packages. Any of those 4 can need another 3, etc. The number will grow and grow, with every level.

When you start installing, you do it from the bottom, with the lowest level, and towards the top.

---

### Post by cortman on 2012-07-18
> **alokmystic said:**
> Thanks a lot, I have broadband connection on my system, hence downloading synaptic is not a problem, I am installing it right now, will inform you how it worked (it will take me little time to understand how to operate it properly, but I think this suggestion will work). :guitar:

[Here's]("http://ubuntuforums.org/showthread.php?t=1900550") my old thread on the matter, should give you step-by-step instructions. If your online machine runs Windows and you'd like to use the program I wrote, see the link in my previous post.

---

### Post by Cheesehead on 2012-07-18
> **alokmystic said:**
> Now why cant we download the same set of files in a folder and have a file like we have .bat file in window, which will run the file one after another in proper sequence, why we need to find out the proper sequence  , when it is already either inbuilt in software center or available at some location on Internet. (why software center doesnt reveal this information )

thats why I said that software center behave in some mysterious way.

This already exists on your system. The package manager keeps a database of every available package, and a lot of data about each package, including dependencies, descriptions etc. This is the common list that Software Center and Synaptic and apt-get and other applications use.

For example, to see the database entry for the 'hello' package, try the command:
```
apt-cache show hello
```
Or take a look at the 'hello' package in Synaptic.

When you ask to install a package, the package manager performs a *recursive* search for dependencies. That means that 'hello' depends directly on three packages. The package manager checks to see which of the three are installed. If any are uninstalled, then it repeats the search for **each** of those uninstalled packages...then repeats again for the next series of uninstalled dependencies, etc. That is how the package manager builds it's list of what to download, and the order to install.

The easiest way to use this database is to use Synaptic.

Is locating and downloading 20 packages and then installing them in the correct order in Ubuntu difficult? No. Tell us what you want to install, and we will walk you through it.

---

### Post by oldfred on 2012-07-18
You can do offline updates:

Offline Synaptic Installation/Repository Updates 
[http://ubuntuforums.org/showthread.php?t=1901446](http://ubuntuforums.org/showthread.php?t=1901446)
[http://ubuntuforums.org/showthread.php?t=1900550](http://ubuntuforums.org/showthread.php?t=1900550)

Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by alokmystic on 2012-07-20
I created download script for kdenlive using synaptic, ran it in terminal , it downloaded two files

kdenlive_0.9.2-0ubuntu0~sunab~precise2_i386.deb
kdenlive-data_0.9.2-0ubuntu0~sunab~precise2_all.deb

I then uninstalled kdenlive from my computer and disconnected my net, and ran the following command in terminal  (to install kdenlive in offline mode)

sudo dpkg -i *.deb
but I get the following error

[IMG]http://freepicupload.com/images/152Screenshot_from_2012_0.png[/IMG]

Not only this after this when I tried to update my system I started to get the following error

[IMG]http://freepicupload.com/images/718Screenshot_from_2012_0.png[/IMG]

Am I doing something wrong, or what darkod is saying is correct, we need to find manually all the dependencies and download it.

---

### Post by alokmystic on 2012-07-20
> **Cheesehead said:**
> This already exists on your system. The package manager keeps a database of every available package, and a lot of data about each package, including dependencies, descriptions etc. This is the common list that Software Center and Synaptic and apt-get and other applications use.

For example, to see the database entry for the 'hello' package, try the command:
```
apt-cache show hello
```Or take a look at the 'hello' package in Synaptic.

When you ask to install a package, the package manager performs a *recursive* search for dependencies. That means that 'hello' depends directly on three packages. The package manager checks to see which of the three are installed. If any are uninstalled, then it repeats the search for **each** of those uninstalled packages...then repeats again for the next series of uninstalled dependencies, etc. That is how the package manager builds it's list of what to download, and the order to install.

The easiest way to use this database is to use Synaptic.

Is locating and downloading 20 packages and then installing them in the correct order in Ubuntu difficult? No. Tell us what you want to install, and we will walk you through it.

I tried this command for package kdenlive and it really showed all the dependencies and many other information. Using these information is something, that I am trying to learn, but thanks a lot, u really helped me to move one step further towards my goal.

the thing that attracted me most in your post, is the last line, So taking advantage of your **Generosity :) **I want to ask the following :-

 the task that we have is finding all dependencies and downloading them in a folder for the codec pack "gstreamer extra" , and then use this folder to install gstreamer extra on a fresh ubuntu installation (offline)

I would be grateful to you, if you can tell me a step by step instruction for this.

---

### Post by vasa1 on 2012-07-20
Alok, many people prefer that images are "attached" and not inline. You may want to click on the "paper clip" to attach images.

---

### Post by alokmystic on 2012-07-22
I was trying Keryx as suggested by [cortman]("http://ubuntuforums.org/member.php?u=1475465"). I downloaded the .deb file and got the following error while installing

guest@guest-desktop:/home/securelogin/Desktop$ sudo dpkg -i *.deb
[sudo] password for guest: 
Selecting previously unselected package keryx.
(Reading database ... 194893 files and directories currently installed.)
Unpacking keryx (from keryx_1.0-public21_all.deb) ...
dpkg: dependency problems prevent configuration of keryx:
 keryx depends on python (<< 2.7); however:
  Version of python on system is 2.7.3-0ubuntu2.
 keryx depends on python-support (>= 0.90.0); however:
  Package python-support is not installed.
dpkg: error processing keryx (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 keryx
guest@guest-desktop:/home/securelogin/Desktop$ 


tried to install it through software center and got the following error, trying to install using software center gives the error 
                                                                             **Dependency is not satisfiable : python (>=2.7)**



many other people are also facing the same problem, as evident from 

[https://answers.launchpad.net/keryx/+question/203574](https://answers.launchpad.net/keryx/+question/203574)

:confused::confused::confused:

---

