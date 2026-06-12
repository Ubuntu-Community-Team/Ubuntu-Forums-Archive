---
title: "HOW-TO: Fix F-Spot time adjustment via patch (for Lucid LTS)"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by seanlano on 2010-03-13
This is a tutorial, based on information gathered [_here_]("http://f-spot.org/How_To_Build_from_HEAD"), [_here_]("http://f-spot.org/How_To_Test_a_Patch") and [_here_]("http://www.sucka.net/2009/08/installing-adobe-cs4-in-wine/"). I chose to modify the original instruction at the first link so that we build and install the stable version, rather than the latest unstable version. Please read through the whole tutorial before you begin, so that you know what you are getting yourself in for. If you don't feel comfortable with this then don't take the chance, you might ruin something if you do it wrong. 
This tutorial is based on a previous one that I made [_here_]("http://ubuntuforums.org/showthread.php?t=1265030"). This version is updated for the latest 10.04 Lucid Lynx release, using F-Spot 0.6.1.5. The old tutorial will not work for Lucid. 


**Backup F-Spot db**
Just in case something screws up...
```
cp ~/.config/f-spot/photos.db ~/.config/f-spot/photos.db.Stable

```

**Remove existing F-spot**
We will be installing a different version of F-Spot, so we need to remove the old version first. 
```
sudo apt-get remove f-spot
```

**Install Prerequisite packages**
We need to make sure all dependencies are satisfied, so that we can compile and install the fixed f-spot. 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mono-mcs libmono-cairo2.0-cil automake automake1.9 libtool
sudo apt-get build-dep f-spot

```
NOTE: You will need to have "Source Code" selected in *System->Administration->Software Sources*

**Create Directory for source code**
```
mkdir -p ~/source
cd ~/source
```
**Download Source code**
This will download the f-spot source code from whatever repository you have specified in your *Software Sources*. This will normally just be the main Ubuntu repo. 
```
apt-get source f-spot
```
NOTE: Do **NOT** specify "sudo" in front of this command, or the files will go to the wrong place.

After that you will need to extract the source file from the tarball. The easiest way is (from Nautilus, the file manager) *Right Click on the archive -> Extract Here*. 

**Get the patch**
The patch I specified in my previous version of this tutorial doesn't work with the latest version of F-Spot, so I used a different patch. [_It is available here_]("http://launchpadlibrarian.net/35518041/no-timestamp-adjust.patch"). However, it was made for 0.6.1.4, so it was necessary to go through and replace all reference to 0.6.1.4 with 0.6.1.5. No big deal. For efficiency, I have uploaded the modified patch to this thread. Please download it, extract it (the same way as above), and save it in ~/source

Then run:
```
cd "~/source"
patch -p0 < no-timestamp-adjust.patch
```

***Optional:* Apply official Ubuntu patch**
I don't think this step is entirely necessary, but it might be useful to apply the changes the Ubuntu developers make to the F-Spot package that is available from the repos. Then we can avoid any incompatibility issues.  You can [_get it from here_.]("http://archive.ubuntu.com/ubuntu/pool/main/f/f-spot/f-spot_0.6.1.5-2ubuntu4.diff.gz") Again, save the archive to "~/source" and extract it as before. Then drag 'n' drop the file (f-spot_0.6.1.5-2ubuntu4.diff) into the "/f-spot-0.6.1.5" folder. 
Now run:
```
cd "~/source/f-spot-0.6.1.5"
patch -p0 < f-spot_0.6.1.5-2ubuntu4.diff
```

**Compile, build, install**
```
./configure
make
sudo make install

```

Hopefully this has worked for you. It took me a while to get it right, the "./configure" and "make" commands kept failing because I didn't have the right prerequisites. If this happens for you, try using Synaptic Package Manager to locate and install the package that is called for. This my be a bit tricky, for example the first time I ran "make" it said that "/usr/lib/mono/1.0/mcs.exe was not found". I had to install the "mono-mcs" package to get this to work. You could try a similar approach if you encounter "file not found" errors during the compile and make stages.

Make sure you keep the ~/source directory, if you need to uninstall later, then run:
```
cd "~/source/f-spot-0.6.1.5"
sudo make uninstall
```

You can now unselect "Source Code" in *System->Administration->Software Sources*. We don't need it anymore, and it will otherwise just take up more of your bandwidth unnecessarily.

---

