---
title: "Ubuntu 9.10/Kubuntu question"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scratman on 2009-08-24
I had Ubuntu 9.04 until 2 days ago.  I felt like a change do I upgraded to the latest alpha of 9.10.  Everything seems to work, pretty much.  I've had a problem when trying to ```
sudo gedit /etc/apt/sources.list
```  It asks for my password, and then gives the error ```
Segmentation fault (core dumped)
```

It's not exactly a nightmare, but I'd like to know what I'm doing wrong.  I'd also like to know how to swap to Kubuntu.   Any help gratefully received.

---

### Post by Hospadar on 2009-08-24
Well it shouldn't be segfaulting, that is undoubtedly a bug.
Whether that's a bug in sudo or gedit is sort of hard to say (or most likely there are some interesting interactions causing the crash).

I would try a couple things to be sure:
--open gedit normally and make sure it works without sudo.
--try sudo-ing a different command to make sure it works, for example 'sudo lshw' (lists out hardware info)
--Assuming the above two things work, there is probably some strange interaction going on.  My first guess would be old configuration data hanging around.  I suspect it is located in .config somewhere, you could try poking around, rename stuff (instead of deleting it) and see if that helps.

Alternatively, try just using a different text editor, I really like nano (it's terminal based) and kate from kde is really nice too.

To install kde 'sudo apt-get install kubuntu-desktop' and then select kde when you log in.

---

### Post by bodhi.zazen on 2009-08-24
Moved to Karmic Testing and Development.

Since you are willing to run and Alpha release I hope you are also willing to test and report bugs =)

---

### Post by taavikko on 2009-08-24
gedit is prone for segfaulting if opened with "sudo"
One should always remember to start GUI apps with "gksudo"

There's no need to manually change sources to point to karmic,
cause you can use "update-manager -d" or
"sudo do-release-upgrade -d" to upgrade release.
If prompt is set to normal in 
"/etc/upgrade-manager/release-upgrades/

---

### Post by scratman on 2009-08-25
OK, so I tried ```
gksudo gedit /etc/apt/sources.list
``` and that didn't work, either.  No error message, just nothing happens.  I went the other way around, navigating to /etc/apt/ and opening sources.list with right click > gedit, and that worked fine.

My desire to edit my sources.list was in order to comment out the line ```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
``` as running ```
sudo apt-get update
``` was giving this error message:- ```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
```.  Turns out that all I had to do was add the GPG key using the following commands ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` and ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8AC93F7A
```

Everything seems to be working just fine now, apart from the fact that neither sudo gedit nor gksudo gedit appears to be working.  This has been filed at Launchpad.  Thanks for the help everybody.

---

