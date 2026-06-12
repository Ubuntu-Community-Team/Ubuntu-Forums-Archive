---
title: "How to you download anything in Kubuntu???"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by baileybarber on 2011-10-10
I'm trying to download new themes and firefox, but anytime i try to download anythign, it downloads all these zipped files, and I dont really know what to do with them! i highlight them, click extract, a window pops up and i say ok, and it says its extracting it but i dont know what happens after that! 

please, give me detailed instructions on how to download firefox... or really anything!

---

### Post by snowpine on 2011-10-10
Welcome to the forums! To install Firefox, simply use the Ubuntu Software Center or these terminal commands:

```
sudo apt-get update
sudo apt-get install firefox
```

I'm sorry but I don't know anything about Kubuntu themes. :(

---

### Post by oldos2er on 2011-10-10
Why not install Firefox from the repositories? Open up a konsole and enter ```
sudo apt-get update && sudo apt-get install firefox
```

You can use either kpackagekit or muon if you desire a GUI package manager; I prefer Synaptic myself.

[http://userbase.kde.org/KPackageKit](http://userbase.kde.org/KPackageKit)

[http://www.wonderly.com/2011/05/muon-kde-package-manager-and-software-center/](http://www.wonderly.com/2011/05/muon-kde-package-manager-and-software-center/)

---

### Post by haqking on 2011-10-10
> **baileybarber said:**
> I'm trying to download new themes and firefox, but anytime i try to download anythign, it downloads all these zipped files, and I dont really know what to do with them! i highlight them, click extract, a window pops up and i say ok, and it says its extracting it but i dont know what happens after that! 

please, give me detailed instructions on how to download firefox... or really anything!

as said above for firefox.

For your last part on installing anything then i suspect you refer to .tar files.

People are often scared or confused by installing software in Linux, there is no real reason it is usually straight forward.

**First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

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
Quick Links 
Have fun

Regards

---

