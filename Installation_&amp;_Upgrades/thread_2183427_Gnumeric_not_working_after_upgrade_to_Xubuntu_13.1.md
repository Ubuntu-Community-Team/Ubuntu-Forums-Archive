---
title: "Gnumeric not working after upgrade to Xubuntu 13.10"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Alan.Brown on 2013-10-24
I have just upgraded to Xubuntu 13.10 from 13.04.

When I click on a **.gnumeric** file to open it Gnumeric fails to open and gives an error message **"/home/username/Documents/xyz.gnumeric - no such file"**.   In this message **username** is not my real user name so the path to the file is incorrect.

When I open Gnumeric from the menu it comes up OK but if I try to open a file from within Gnumeric the program just closes without any error message.

Before upgrading I have used Gnumeric extensively for years and never had any problem with it.

TIA

Alan

---

### Post by Alan.Brown on 2013-10-26
Exactly the same thing is happening after I upgraded from **Kubuntu 13.04** to **13.10**

Does anyone have any suggestions?   If I am posting to the wrong forum would someone please advise me.

TIA

Alan

---

### Post by vanadium on 2013-10-27
Difficult to pinpoint your issue. I don't find nothing in the internet, and I installed gnumeric myself, and it opened an old gnumeric file I still have without a problem. It is version 1.12.6 that comes with Ubuntu 13.10, so check wether you also have that version.

My system is a fresh install (i.e. after deleting the previous Ubuntu version), and not an upgrade over an existing Ubuntu 13.04. Upgrading may give issues, and that might or might not be one.

A way to try debugging the problem is to launch gnumeric from the command line. When gnumeric opens, load a file. If it craches, error messages might appear in the terminal and perhaps give an indication on the error.

---

### Post by Alan.Brown on 2013-10-27
[SIZE=+1][FONT=Arial]I have just done fresh install        (ie not an upgrade) of Xubuntu 13.10 and Kubuntu 13.10.   I am still having        exactly the same problems on both computers.
        
        The version of Gnumeric is 1.12.6
        
        In **xsession-errors** the only error I have is the        following -
        [B]"
        [/B]**openConnection: connect: No such file or directory****cannot connect to brltty at :0****Script for cjkv started at run_im.****Script for default started at run_im.****"**
        I do not know whether this is relevant
        
        I can open the file from Xubuntu 13.04 without any problem so I        think the file is OK

        Alan[/FONT][/SIZE]

---

### Post by vanadium on 2013-10-28
Strange you have the problem on two desktops and two different computers, whereas I do not see anything (on standard Ubuntu 13.10 with Unity). Can you create and save a new file and then open that from within the program or from within the file manager? This to exclude a problem with the files you are trying to open.

Needles to say that I have no clue on the error message you get.

---

### Post by mhhagen on 2013-10-29
I have exactly the same problems since the 13.10 upgrade of my xubuntu install.

The file I created about 18  months ago under xubuntu 12.04 worked fine till 13.04. I could open it, edit its contens and save it - no probs.
Then I did the upgrade to 13.10 and - bam! - doubleclicking the file leaves me with nothing but a crash-Message while openig the file in Gnumeric says "couldn't open file". That's all.

The file contains one spreadsheet and a seperate chart tab. Nothing special as I think.
I'll do a strace of gnumeric tonight and see if there's a clue what wents wrong.

Also I'm going to try to export the data using a 13.04 live-cd. The graphics are no magic then.

And yes: I can create, save and open new gnumeric files under 13.10.

---

### Post by Dennis N on 2013-10-29
I have a similar problem with Lubuntu 13.10. A difference is I can open one file only, either by double-clicking the file to open it in gnumeric, or start gnumeric first and then open it. Attempting to open a second file and gnumeric crashes.

Edit:

Some more testing shows this to be file specific: some files open, and some will crash gnumeric with a segmentation fault. Knowing which will open beforehand, I can open multiple files so that is possible.

---

### Post by Dennis N on 2013-10-29
**Fixed this problem in Lubuntu 13.10 by reverting to the previous version of gnumeric, which was 1.12.1-1ubuntu1**

1) Using Synaptic, removed completely **gnumeric** and **gnumeric-common**. (lubuntu-desktop was also removed)
2) Located the .deb files of the older version.

[http://packages.ubuntu.com/raring/gnumeric](http://packages.ubuntu.com/raring/gnumeric)
[http://packages.ubuntu.com/raring/gnumeric-common](http://packages.ubuntu.com/raring/gnumeric-common)

3) Verified by inspection that the dependencies shown were met on my system.
4) Download the files. 

5) Installed these with **gdebi package installer** - you must install gnumeric-common first.
6) Locked these two packages against upgrading in Synaptic package manager. Otherwise, you will be prompted to upgrade.

7) Tested. Everything works normally.
 
My system is Lubuntu 13.10. All this will probably will work out the same in Xubuntu, but that is not certain.

---

### Post by mhhagen on 2013-10-29
OK, downgrading gnumeric works - I already assumed that.
But is that the way to deal with those crashes? Staying on gnumeric 1.2.1 isn't very appealing to me...

Anyway will report on my progress later...

---

### Post by Dennis N on 2013-10-29
Works for me. Gnumeric 1.12.1 has all the features I need. Truth be told, I don't detect much if any difference from version to version. Perhaps there are some added features I would never use. I will be watching for any progress. Please post your solution if you find one. Good luck to you.

---

### Post by Alan.Brown on 2013-10-29
Thanks for all your replies.  I am glad to see that others are having the same problems as I am - that means that the problem is not with me! 
I have about 8 gnumeric files and I can open them all under 1.12.1 in both Xubuntu 13.04 and Kubuntu 13.04. The files I cannot open under 1.12.6 are older than about 2 1/2 years - the newer ones I can open OK. 
If I open a new spreadsheet in Gnumeric **1.12.1** and open one of the older files in another copy of Gnumeric 1.12.1 and copy and paste the sheets one by one to the new spreadsheet then I can open the new file with **1.12.6**  So there seems to be something in older files that is incompatible with the new Gnumeric.
Since all my files are very important to me and I must continue working I have gone back to Xubuntu 13.04 and Kubuntu 13.04 with Gnumeric 1.12.1.    I shall over time convert all files to LibreOffice Calc and abandon Gnumeric altogether.
I now have an external Hard Drive and will always install any new upgrade to it and thoroughly test it before upgrading on my work computers.
I am disappointed that this kind of problem has been allowed to get through.

---

### Post by mhhagen on 2013-10-31
So I think I figured it out.

There's a bug filed in bugzilla for gnumeric resp. libspreadsheet: [**Bug 707047**]("https://bugzilla.gnome.org/show_bug.cgi?id=707047")[ -        segfault; error 4 in libspreadsheet-1.12.6.so]("https://bugzilla.gnome.org/show_bug.cgi?id=707047")
This bug causes gnumeric to crash when openig a gnumeric file containing split panes (to prevent the table headers from scrolling out of sight).
There's a fix filed on 28-aug-2013 that made it to gnumeric-1.12.7 released in September. Obviously that was to late for (x)ubuntus feature freeze.

I set up a fresh xubuntu 13.10 install, uninstalled gnumeric-1.12.6 and gnumeric-common, downloaded gnumeric-1.12.7 sources from [www.gnumeric.org]("http://www.gnumeric.org") and did the usual build and install steps.[B]
[*][/B]
Running the newly build 1.12.7 my old gnumeric-files opened fine.

Hope that helps. 

Last question: How do we get the maintainers of the ubuntu repo to update gnumeric to 1.12.7?

Greetings from Germany,
michael

---
[B]
[*][/B] - I had to install the dev-packages of gtk3, goffice and zlib and the intltool for the ./configure to end without errors. Make sure you direct configure to the right path for the install (--prefix=/usr).
So its
./configure --prefix=/usr
make
sudo make install
make clean

---

### Post by Dennis N on 2013-10-31
Nice work tracking this down and also confirming that the new 1.12.7 solves the issue in our systems. The 14.04 release will contain this new version, so I will probably stick with my 1.12.1 "substitution" in the interim - until April next year - since it is working without any problem for me in Lubuntu. (I mostly use the 12.04 LTS version on another machine and look at the version number I have there.)

It's not likely (but not impossible of course) that it will be upgraded through the regular Ubuntu repositories until the 14.04 LTS release, if the past is any guide. A PPA would be the only possibility, but I haven't seen a PPA offering gnumeric for Ubuntu.

Again, thanks for your update!

---

### Post by mhhagen on 2013-11-02
Living with this bug for half a year isn't very appealing.
Spliting panes in bigger tables is quite popular I think. 

The big point here is that one can create a file containing a split pane and work with it fine. But after saving you'll never be able to open it again.

---

### Post by Dennis N on 2013-11-02
But the Raring 1.12.1 version I am using doesn't have the bug. I am having no problems at all. I think the bug report said the problem first appeared with 1.12.4.

---

### Post by jcsjcs on 2013-12-27
I ran into the same problem. I solved it by installing the packages from trusty (V1.12.9):

Download the packages you need from [http://packages.ubuntu.com/search?suite=trusty&section=all&arch=any&keywords=gnumeric&searchon=names]("http://packages.ubuntu.com/search?suite=trusty&section=all&arch=any&keywords=gnumeric&searchon=names")

I had to download

gnumeric_1.12.9-1_amd64.deb
gnumeric-common_1.12.9-1_all.deb
gnumeric-doc_1.12.9-1_all.deb
libgoffice-0.10-10_0.10.9-1_amd64.deb
libgoffice-0.10-10-common_0.10.9-1_all.deb

Then I installed the packages

sudo dpkg -i gnum*.deb libgo*.deb

Good luck!

---

### Post by garethfoxwilliams on 2013-12-29
This is from the Ubuntu page referenced in the post above:

"If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/trusty/aptitude") or [synaptic]("http://packages.ubuntu.com/trusty/synaptic") to download and install packages, instead of doing so manually via this website.

 You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

```
**deb http://cz.archive.ubuntu.com/ubuntu trusty main universe**
```


Having added the line above to my sources and reloaded, Synaptic then offers me the choice of upgrading gnumeric, which I have done successfully.

---

### Post by jcsjcs on 2013-12-29
> **garethfoxwilliams said:**
> This is from the Ubuntu page referenced in the post above:

"If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/trusty/aptitude") or [synaptic]("http://packages.ubuntu.com/trusty/synaptic") to download and install packages, instead of doing so manually via this website.

 You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

```
**deb http://cz.archive.ubuntu.com/ubuntu trusty main universe**
```

If you do so, don't you run the risk of upgrading half your system without noticing if you run "apt-get upgrade" or have upgrades enabled automatically? I don't think the warning is meant for special cases like this. In this special case I see much more risk in adding a new source.

JCS.

---

