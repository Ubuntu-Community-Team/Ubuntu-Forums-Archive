---
title: "Can't boot ubuntu! Need to take backup."
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by rajneesh2k10 on 2012-01-04
I had ubuntu 10.10 installed inside my windows. It was working smooth for last 1 year. I tried to install some packages related to customization and after that its not at all booting. After loader menu if I select windows, it goes fine. But after selecting ubuntu, it drops me to grub shell. :(
I have critical information in my home directory. I can re-install ubuntu but I want those data back. From windows file system if I go to ubuntu install directory and try to access disks directory from there, it says the directory is corrupt. How can I get my data back?? Please help... :confused:

---

### Post by ottosykora on 2012-01-04
as this is a wubi install, the whole linux is installed inside a virtual drive, which is for windows just a big file containg just rubbish at any time.

So to recover the data from the windows is not likely.
Installing the ubuntu again this way (wubi) will just create new such 'disk' and so all will be lost anyway.

There might be ways to repair the grub to make it booting the current version again, but I tried this number of times and never succeeded on a wubi install, thought I have not done any wubi for some time now.

On the other hand, giving you the grub shell is not bad either, it could be much worse.

---

### Post by bcbc on 2012-01-04
See this for instructions to recover: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by rajneesh2k10 on 2012-01-06
Thanks bcbc!! Worked great. My ubuntu is up and running again.

Still I wonder if there is a program which can read ubuntu raw disks in wubi install ??  Anyone help.
One thing I can think of is (if the disk is in place), install a new ubuntu and copy and replace the new disk with the old one. Done! Anything else?

---

### Post by bcbc on 2012-01-06
There is a tool that can read a root.disk from Windows, but your problem was due to corruption so I didn't mention it. You can find it at [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) 
I don't think I'd want to run it regularly, but it's convenient for some to extract data on an emergency basis.

Note, reinstalling Wubi will always remove the existing install - so if you try this you need to copy the root.disk (and other .disk files) somewhere safe first - outside of the \ubuntu directory.

You should try to figure out what caused the corruption. If it happens again and it's bad enough you can lose all your data. (So you should make sure you're backing it up regularly.)
But if the corruption is due to you doing hard shutdowns (i.e. because the ubuntu install is hanging) then it's safer to use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") to safely reboot.

---

### Post by darkod on 2012-01-06
And one thing not mentioned so far: Since you have critical data inside wubi and it seems you plan to use ubuntu long term, start thinking about a proper dual boot ASAP.

Wubi is just for a short try inside windows, not to run it long term. Not only that updates inside wubi can break it down, also any problem inside windows can break it down too since it's inside windows.
Having a proper dual boot makes ubuntu independent of windows.

---

