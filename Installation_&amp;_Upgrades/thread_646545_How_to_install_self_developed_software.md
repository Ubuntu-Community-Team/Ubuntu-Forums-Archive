---
title: "How to install self developed software?"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Gene Norris on 2007-12-21
I am VERY new to Linux; I have had Ubuntu installed for all of 3 days.

I also write code for my own use.  I have a compiler that allows me to write cross platform (Windows/Linux) code.  The compiler is Borland C++ Builder V6.  

To test the environment I wrote the typical "Hello World" program got to to the Ubuntu machine and double clicked the executable and it did not work.  I have been reading a lot online since then and frankly, I do not know where to start.  Any help will be appreciated.

Thanks, Gene

---

### Post by mellowd on 2007-12-21
You might need to change it to an excecutable format. Open a terminal, browse to the file and do this:

```
chmod +x filename
```

then run it like this:

```
./filename
```

---

### Post by RIchard James13 on 2007-12-21
> **Gene Norris said:**
> I am VERY new to Linux; I have had Ubuntu installed for all of 3 days.

I also write code for my own use.  I have a compiler that allows me to write cross platform (Windows/Linux) code.  The compiler is Borland C++ Builder V6.  

To test the environment I wrote the typical "Hello World" program got to to the Ubuntu machine and double clicked the executable and it did not work.  I have been reading a lot online since then and frankly, I do not know where to start.  Any help will be appreciated.

Thanks, Gene

Does Borland C++ Builder V6 run on Linux? If not then what you are trying to do is termed cross-compiling. In order for it to work your compiler has to be set up to specifically output Linux files, also if there are any libraries and since you use C there is one then you need a version of those libraries installed on the Linux machine. Your linker must link your code against those libraries as opposed to the MS Windows ones.

Once you have that set up you need also consider the permissions issues as outlined by mellowd. In Linux a file is considered executable if it has the right permissions for the right user or group. In MS Windows files are executable if they have the right extension on the end.

---

### Post by Gene Norris on 2008-01-02
Thanks to mellowd and james13 for their responses.  I did as mellowd suggested with chmod and now I get the error "cannot execture binary" or something like that.

To answer james13's question, Borland C++ does not run under Linux.  What I am able to gather from the help files in Borland for CLX (I was in error by referring to it as CTX in my orginal post) is that by using the CLX libraries during code developement and distributing a DLL, I believe it is called QTINIT.DLL, the program should run in Lunix.  It is referred to as "cross platform development."  

I must admit that I have searched the Borland forums and can find pratically zero info about CLX.  I even  ask a question there and have not gotten an answer as yet.  Of course I submitted the question just prior to New Years eve so I guess that no one has gotten around to it yet.

I even downloaded and installed Kdevelop for Ubuntu, but I am having a problem with that.  I am sure it is ingnorance on my part.  The main window opens and all of the applications appear to be there and since I am such a newbee I ask for help the first thing and get an error message the help center cannot be found.

Thanks again, Gene

---

### Post by RIchard James13 on 2008-01-04
> **Gene Norris said:**
> Thanks to mellowd and james13 for their responses.  I did as mellowd suggested with chmod and now I get the error "cannot execture binary" or something like that.

To answer james13's question, Borland C++ does not run under Linux.  What I am able to gather from the help files in Borland for CLX (I was in error by referring to it as CTX in my orginal post) is that by using the CLX libraries during code developement and distributing a DLL, I believe it is called QTINIT.DLL, the program should run in Lunix.  It is referred to as "cross platform development."
.dll are windows based libraries Linux ones end in .so
QTINIT.DLL seems to be QT based but I cannot find any other info on this other than CLX seems to be not any further in development than it was a few years ago. 

> I must admit that I have searched the Borland forums and can find pratically zero info about CLX.  I even  ask a question there and have not gotten an answer as yet.  Of course I submitted the question just prior to New Years eve so I guess that no one has gotten around to it yet.

I even downloaded and installed Kdevelop for Ubuntu, but I am having a problem with that.  I am sure it is ingnorance on my part.  The main window opens and all of the applications appear to be there and since I am such a newbee I ask for help the first thing and get an error message the help center cannot be found.

Ubuntu is a Gnome distribution and when you install KDE apps it doesn't quite get everything. I found to use Kdevelop I had to install the Kdevelop-doc files as well.

---

### Post by Gene Norris on 2008-01-06
Thanks for your efforts.  I finally was able to find some additional information about CLX.  It seems that the code developed under Borland Builder C++ via CLX has to be recompiled on the target machine.  

As you mentioned, it seems that the whole cross platform effort by Borland has died.  Their Linux product, Kylix, is no longer available.  They got to version 3 and then quit. 

Thanks again for your help.  Gene.

---

