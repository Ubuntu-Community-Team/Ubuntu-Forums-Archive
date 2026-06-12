---
title: "Edubuntu install help"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Renost on 2008-02-19
I was given a burned edubuntu live cd with version 7.10.
When it was installed on another computer to demonstrate how to do so it worked fine..
When i brought it home it would boot up nicely then when id choose an option id would say"I/0 error:Error reading boot cd"


The computer is.
Pentium 3
no os due to errors int he system i need to reinstall windows but still the same has no operation system..


I doubt its the burn speed if it worked on a Pentium 4 computer with ease...
What could it be please help.
Thanks in advance.
sorry for multiple threads first was in wrong section

---

### Post by radiocognition on 2008-02-20
One of the things you can do to verify a disk image before burining it is run an md5 checksum and compare it to the standard edubuntu checksum value.  This is fairly standard procedure to check for download errors or copy errors in your disk image file.  Seeing as the same disk was able to run on another computer, the likely problem is something with your hardware configuration. 

Let me see if I am understanding you correctly . . . Edubuntu is BOOTING correctly from the CD, including the GUI and other system processes, but when you try opening a program you get this error message?

---

### Post by RJ Hythloday on 2008-02-23
I have been using kubuntu gutsy and dl a live cd of edu for a friends install. I dl the .torrent as they are supposed to be better w/ hash checks etc. K3B verified the .iso .md5. I burned 2 copies at 8x. First one booted to live cd, install hung at 66% I got the same message as you. I know the hdd is good, I've had another install on it recently. I tried the second cd and it didn't even get to the live portion. It hung up w/ the splash screen loading the orange bar.

That was late last night, and I put my kubuntu hdd back in for the fam, I'll let the cd check itself when I go home.

Any idea which mirror your friend dl it from, .torrent or direct?

edit: my search on this site has showed alot of edu install problems! I'm thinking I will install xubuntu and then```
sudo apt-get install edubuntu-desktop 
```

I just gotta go find the command for x!

---

### Post by RJ Hythloday on 2008-02-25
Not sure what happened, but I threw the live cd back in and this time it installed flawlessly. I'm now trying to figure out how to get the fluxbox desktop loaded. I don't have an option at login for which desktop.

---

