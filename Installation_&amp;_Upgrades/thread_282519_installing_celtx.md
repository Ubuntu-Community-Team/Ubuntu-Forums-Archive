---
title: "installing celtx"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Chickenfoot on 2006-10-22
Hey Everyone,

I'm having some issues installing Celtx. Iwas wondering if anyone could help me out.

I went to Celtx hope [page]("http://celtx.com/download.html") and got this

Linux Users:

   1. Extract the tarball to the directory where the celtx program will reside (eg. usr/local/celtx)
   2. Run the the "celtx" file (eg. /usr/local/celtx/celtx) via the command line or create an application launcher for it.

When I attempted to extract to the /users/local folder, I got an error stating that I did not have permission.

Then I went to the [Install anything on Ubuntu]("http://www.monkeyblog.org/ubuntu/installing/") page.

That gave me this:

chickenfoot@spanky:~$ cd /home/chickenfoot/Desktop/celtx
chickenfoot@spanky:~/Desktop/celtx$ ./configure
bash: ./configure: No such file or directory
chickenfoot@spanky:~/Desktop/celtx$ make
make: *** No targets specified and no makefile found.  Stop.
chickenfoot@spanky:~/Desktop/celtx$

Not to be deterred, I did some more reading and came up with this:

[Installing Software in Ubuntu]("http://psychocats.net/ubuntu/installingsoftware")
[COLOR="RoyalBlue"]
I followed this part:

The first thing you'll have to do in Ubuntu is install a meta-package called build-essential (a meta-package isn't a real package--it's a pointer that tells Synaptic/Adept/aptitude to install a bunch of other real packages):

sudo aptitude update
sudo aptitude install build-essential[/COLOR]

THen I wrote this in:

tar -xvzf celtx.tar.gz
cd celtx
./configure
make
sudo make install

But I'm still getting this error:

Fetched 7B in 1s (6B/s)
Reading package lists... Done
chickenfoot@spanky:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
chickenfoot@spanky:~$ tar -xvzf celtx.tar.gz
tar: celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
chickenfoot@spanky:~$


So what am I doing wrong? Any help will be appreciated.
[/COLOR][/COLOR]

---

### Post by CeltxGuy on 2006-10-24
Hi,

If permissions are a problem then you can just extract the tarball to your home folder then create a launcher for the "celtx" file in the celtx folder.

Cheers,
CeltxGuy

---

### Post by Karma_Police on 2006-10-24
You can't "./configure && make && make install" because it's not a source package. It has pre compiled binaries. As it says in the instructions, you have to extract it to the folder where you are going to use it. If it's only you in that computer that will use the program, you can extract it to a folder in your home, and just use from there. You wont have permission issues, because everything belongs to you :). on the folder you extracted the files, double click the celtx file and it should work. if not, try to change the permissions to executable.

If you want to put it somewhere else, open up the terminal, and do
```

sudo tar -xvzf celtx.tar.gz
sudo mv celtx /usr/local/

```

I'm sorry if something is confusing, but I'm not in front of my ubuntu pc... I'll check this thread later to see if you solved it or not.

---

