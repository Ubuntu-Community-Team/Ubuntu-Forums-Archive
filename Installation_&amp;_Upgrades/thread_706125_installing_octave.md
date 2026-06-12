---
title: "installing octave"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by makrox on 2008-02-24
Hello,
i am new, both with Ubuntu and in this forum,...

and so i have a question,...

I want to install octave to my system, but i have no idea how to do it?? You know, today it's my second day of using Ubuntu,...

What packages must I download and how can i install them :confused:

This is the download site, but i don't know what i need from there?
[http://www.gnu.org/software/octave/download.html](http://www.gnu.org/software/octave/download.html)


Thank you in advance for ......   
mx

PS:
I use ubuntu 7.04 (or 7.4 i'm not sure)

________________
If there are any grammatical mistakes, please don't kill me,
english isn't my native tongue

---

### Post by agim on 2008-02-24
Boy are you going to love Ubuntu.
To install octave you can do two things.

1) Go to a command line and type this

sudo apt-get install octave

2) or you can open the Synaptic package manager, search it, click it, and install it.

You don't have to worry about dependencies

Edit: I would try Synaptic, after double checking, there are two versions of Octave

---

### Post by makrox on 2008-02-24
Thanks a lot :-D,
it worked without any problems,...

and now i tried to install Scilab but sadly there isn't any package in the Package Manager, 
I've download the install-file for Linux from: [http://www.scilab.org/download/](http://www.scilab.org/download/)
(what should i use, file version or source version??, and how can i use it??)

so far so good, but i have again no idea what to do with this folder
there are many files, i tried to add them to Synaptic:
file--> add downloaded packages--> then searched the folder (i saved it on the desktop)
Name: scilab-4.1.2-src.tar.gz

but the folder isn't active, i can't choose it.

How can i install the downloaded file??

Greetings
mx

PS:
I was wrong, i have Ubuntu 7.10

________________
If there are any grammatical mistakes, please don't kill me,
english isn't my native tongue

---

### Post by makrox on 2008-02-24
Well, i've done it...

This helped
$ sudo apt-get install scilab scilab-doc
$sudo apt-get install gnuplot

but one last question,....

if i want to install the newest version, how can i handle that??

I've downloaded two versions (binary file and source), but i don't know which version is the right, i think the binary file will be the one??

But how can I install the software, because it is just a folder, Synaptic didn't know that i want to install this software. How can I tell it to Synaptic or how can i install it with the terminal (GUI i think)

Thanks a lot in advance for...
mx

________________
If there are any grammatical mistakes, please don't kill me,
english isn't my native tongue

---

### Post by makrox on 2008-02-24
Well I've done it, i think?

This way i did it:
Right click the folder named "scilab-4.1.2.bin.linux-i686.tar.gz"
and chosen "extract here"
then in the Terminal:
/home/makrox/Desktop
and then the command "make" (like the readme said)

Well after installation i'm not sure if it works...
i installed version 4.1.2 but if i open the scilab it shows 4.1.1.

hm,...:confused:
what do you mean, did I sth. wrong??

regards
mx 

__________________________
If there are some grammatical mistakes, please don't kill me,
english isn't my native tongue

---

### Post by makrox on 2008-02-25
Hey folks,
i just want to renew my post...

---

### Post by chronographer on 2008-02-25
Hi

I am relatively new, but I think I can cover some Linux installation basics!

SO there are many ways to install with Linux, the old way is compiling yourself, this is what you read in the scilab readme. This involves usually 3 steps after you have extracted the tar.gz file and cd'ed into the directory. 1/ "./configure" (the "./" tells bash to stay in the folder you are in and execute) 2/ make and 3/ make install. This is usually unnecessary these days as someone else has probably compiled it before and you can download his/her files.

The BEST way to be safe and install software is if its in official repositories, this is set by Ubuntu and you can then add unofficial repositories in the text file "/etc/apt/sources.list" try doing "gedit /etc/apt/sources.list" and see if you can make sense of it, read a forum to find how to use it!

Once you have repositories like medibuntu or wine etc. set up you can use "sudo apt-get install scilab" which will install it and its dependancies. IF you don't know the name of software you can use "apt-cache search scilab" which returns a list of packages with that in their title or description.

If all else fails and you can't find a repository, some software like Deluge Torrent have files called ".deb" which Debian based distro's. like Ubuntu use to package software. You can double click a deb, or type "sudo dpkg -i scilab.deb"

I hope this isn't too wordy or obvious, and I hope it helps!

Alex

---

