---
title: "Installing programs via terminal"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Pr0t3us on 2011-10-16
First let me say i am linux noob; now with that said how do I use the terminal to install stuff? I've tried looking at a couple guides listing commands but they didnt seem to tell me how to do it.

One thing i have been trying to do is install a driver for my graphics card; at first when i downloaded it i went to my download folder and tried to execute it from there except nothing happens. Some googling has lead me to believe it needs to execute with superuser acces? could this be true? How can i install it with the terminal?

---

### Post by haqking on 2011-10-16
> **Pr0t3us said:**
> First let me say i am linux noob; now with that said how do I use the terminal to install stuff? I've tried looking at a couple guides listing commands but they didnt seem to tell me how to do it.

One thing i have been trying to do is install a driver for my graphics card; at first when i downloaded it i went to my download folder and tried to execute it from there except nothing happens. Some googling has lead me to believe it needs to execute with superuser acces? could this be true? How can i install it with the terminal?

depends what you are installing.

for super user access then you need to read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

[B]First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)
[/B]

You can also use synaptic, apt-get or aptitude from CLI.
see here [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
and here [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set ;-)

Have fun

Regards

haqking

---

