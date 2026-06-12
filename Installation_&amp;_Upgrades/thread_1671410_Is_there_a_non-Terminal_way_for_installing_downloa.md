---
title: "Is there a non-Terminal way for installing downloaded apps?"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by Nitrozzy7 on 2011-01-20
Hello,
I've downloaded an app called "Processing" and -to my BIG surprise- it didn't performed the installation. This happens with every app that I download. Cinelera is one of those apps.
So what's the deal with this user-hostile problem?
Isn't it possible for a program to install without me having to contact you?
I would really appreciate if you wouldn't gave me a command to run in the Terminal. On second though... I will not use any command in the Terminal. For Ubuntu's sake this will be solved by non-Terminal and User-friendly means.
It's really frustrating not to be able to use the apps I just downloaded.
Btw, I opened it with the Archive Manager and then I hit Extract.

Thunx.

---

### Post by nomko on 2011-01-20
As long it is a .deb file you can double click on the file and apt-get will launch. If you have a .tar or .tar.bz2 file, you have to install it manually.

---

### Post by Nitrozzy7 on 2011-01-20
Do I really need to point out how much this sucks?
Anyway why is that?
Why can't it be as simple as 1,2,3???
Seriously, every other big OS solved this problem ages ago!
I will not accept any "run-this-in-Terminal" help.
Nice avatar btw and thunx for replying.

---

### Post by nomko on 2011-01-20
Linux isn't Windows or Mac and Windows/Mac isn't Linux. That's as easy as 1,2,3. I consider it as normal to install a tarball manually. If you have troubles with it or find it difficult, i'm not sorry for that. It's a matter of attitude or exceptence. If you want it the easy way: Windows.

And like i said, Ubuntu uses the .deb format and as long as you download a .deb file, the installation will be easy. Just double click on the .deb file and apt-get will execute the installation. Just like Windows (double clicking an .exe file). The only difference is that in Linux you don't have to perform all those time consuming steps which you had/have under Windows (agree with the installation path, etc.). 

If you download a tarball, unzip it and you will find a readme file or installation file with instructions how to install the program/application. 

But again, for Ubuntu use a .deb file. 

















.

---

### Post by PrivateSNAFU on 2011-01-20
If you don't want to use the terminal stay away from source code and only use debs.  These will install fine in GUI.

---

### Post by coffeecat on 2011-01-20
> **Nitrozzy7 said:**
> Do I really need to point out how much this sucks?

No it doesn't suck. (Most) Tarballs contain source code which need to be compiled. They are available mainly for two reasons. For developers, and because of the open-source licence - source code must be freely available.

If you want point and click, then download deb files as others have said. They are easier to install than exe installers in Windows.

If you do come across apps which are only available from source code then give them a wide berth. If the application developers haven't  prepared packages for the most popular Linux distribution then it's more than likely there are other reasons you may find the application unsuitable for your needs.

---

### Post by bikodog on 2011-01-20
> **Nitrozzy7 said:**
> 
It's really frustrating not to be able to use the apps I just downloaded.


The difference with FOSS is that you [U]can[U] use the programs; in anyway you see fit within the boundaries of the GPL.

If you are trying to install FOSS, you must remember, it was written by kind folks who had/saw a need and have shared it with the global community. They weren't paid to do it. If you are going to limit your possibilities to the extent of your index finger; stick with the paid stuff. At least then there would be grounds for complaint.

The only thing preventing your programs from working, exactly how you want them to work, is yourself. Be patient and learn how to interface with your machine (yes this includes the command line) and you will realize how much simpler it really is.

---

### Post by Nitrozzy7 on 2011-01-20
What is your point? That I souldn't be frustrated?
Well, I am frustrated!
All I know is that I can't do a simple install operation without contacting the comunity. If I can't do it, then my friends can't do it, then my mom can't do it.
You want to give the Terminal solution? Fine. I want a solution after all... Still it won't have solved the fundamental problem of Ubuntu; User Hostility.
Cheers!

---

### Post by coffeecat on 2011-01-20
> **Nitrozzy7 said:**
> 
Well, I am frustrated!

Then don't download and try to install source code. You don't download and compile source code in Windows - which you could if you wanted to. Therefore, don't download and compile source code in Linux. You have the official Ubuntu repositories and Software Centre which make installing most apps far easier than in Windows. And for **reputable** 3rd party apps which are not in the repositories there are usually downloadable deb packages which you simply double-click on - just as in windows.

---

### Post by nomko on 2011-01-20
> **Nitrozzy7 said:**
> What is your point? That I souldn't be frustrated?
Well, I am frustrated!
All I know is that I can't do a simple install operation without contacting the comunity. If I can't do it, then my friends can't do it, then my mom can't do it.
You want to give the Terminal solution? Fine. I want a solution after all... Still it won't have solved the fundamental problem of Ubuntu; User Hostility.
Cheers!
 
For the 3th time:
 
**For Ubuntu just download the .deb file and double click on it. Apt-get will start the installation procedure and there's nothing the user has to do!**
 
How easy do you wanna get it???
 
Oh yes, another advise:
**Stop downloading source files and try installing those!!!**
 
It might help you not getting frustrated.....

---

### Post by sisco311 on 2011-01-20
Processing is a java application. It comes in an archive file. (1) You have to extract the archive. Navigate into the extracted directory. (2) Right click on the *processing* file. Select *Properties*, then in the *Permissions* tab select *allow executing file as program*. Close the *Properties* window and (3) double click the file *processing*, select *Run*.

You can install Cinelerra from [this PPA]("https://launchpad.net/~cinelerra-ppa/+archive/ppa") repository. For installation instructions check out the community documentation: [uhelp]community/Repositories/Ubuntu#Adding PPAs[/uhelp]

---

### Post by Nitrozzy7 on 2011-01-20
Nice one sisco! An actual answer!
Thunx!

---

