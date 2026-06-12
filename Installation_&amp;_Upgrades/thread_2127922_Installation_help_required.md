---
title: "Installation help required"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by BeverlyStacey on 2013-03-21
I've noticed firefox won't open on my laptop (ubuntu 10.4) and I've downloaded via pen drive from a windows computer, the file firefox-19.02.tar.bz2. That is as far as I've got. I don't know how to go about installing from the pen drive.

Please assume I'm a novice and know very little about ubuntu and linux but have had 20 years experience in mainstream computing - mainly microsoft.

Thank you for your help in advance!


ETA, apparently I've got a broken update manager and synaptic package manager...

---

### Post by papibe on 2013-03-21
Hi BeverlyStacey. Welcome to the forums ):P

I wouldn't try to install the file you got from your USB.

Let's see if we can get more message errors to diagnose the problem.

Open a terminal and run:
```
firefox
```
Then paste here any message the terminal displays after that.

Let us know how it goes.
Regards.

---

### Post by TheFu on 2013-03-21
Downloading files directly is the hard way to install on Linux systems. We have had package managers since the mid-1990s, which make everything easier around installing and maintaining current versions of programs. You probably know this already.

Also, 10.04 desktop support ends next month, so it would be a good idea to migrate to 12.04.  I suspect this might be the reason you downloaded the firefox file directly. Sometime last fall, firefox builds stopped being produced for 10.04  - at least that was my experience. Other programs will stop building for 10.04 this month. It is time to move forward.

Ok, if you must have that version of firefox AND you cannot find it in a repository or PPA, then these are probably the instructions you want:
* bunzip the file - **bunzip firefox-19.02.tar.bz2**
* de-tar the resulting file - **tar xvf firefox-19.02.tar**
* inside the directory just created for you, there is probably a setup or install or README file. This will explain how to install for 1 user or for the entire system.  Follow those instructions.  
* After the installation is complete, you can remove the .tar file and the newly created subdirectory.

There might be an archive manager that will bunzip/detar the file too - I don't use those. I'm a shell/CLI person. It is easier to share CLI commands than screenshots with arrows pointing at things, IMHO.

Package managers is a primary reason that I run Linux over all the other OSes available. [http://blog.jdpfu.com/2009/10/06/easy-software-updates-and-patches](http://blog.jdpfu.com/2009/10/06/easy-software-updates-and-patches) explains more.  **Package managers completely Rock!**

If something doesn't work, please post the exact command AND the **relevant** output here.

---

### Post by BeverlyStacey on 2013-03-21
> **papibe said:**
> Hi BeverlyStacey. Welcome to the forums ):P

I wouldn't try to install the file you got from your USB.

Let's see if we can get more message errors to diagnose the problem.

Open a terminal and run:
```
firefox
```
Then paste here any message the terminal displays after that.

Let us know how it goes.
Regards.


Thank you for the lovely welcome! - the message is "segmentation fault".

---

### Post by BeverlyStacey on 2013-03-21
The Fu, thank you for that, I've got a few questions, sorry...

does bunzip mean the same as unzip?
how would I de-tar a file?
will the newly created directory open itself for me? I can manage to read a readme :)
where would I remove the .tar file and the newly created subdirectory from?

---

### Post by grahammechanical on 2013-03-21
> [COLOR=#000000]where would I remove the .tar file and the newly created subdirectory from?[/COLOR]

Think "remove" = "delete." Use the File Manager (nautilus) to send the file and folder into the rubbish bin. Then empty the rubbish bin to remove the file and folder completely. Once you are sure that you definitely no longer need them.

I am not sure about 10.04. It is so long ago but try using the File Manager. Right click the file and see what options you are offered. File Manager might open an archive manager from you that will let you extract the file, which is the same as unzipping it.

Wherever you downloaded the file to the extraction process will create a folder in that place. And that is where you will find the files that come out of the compressed file.

Regards.

---

### Post by papibe on 2013-03-21
How far did yo go trying to install the tar file?

Are you able to update your repositories?
```
sudo apt-get update
```
Regards.

---

### Post by TheFu on 2013-03-22
The **bold items** in my first reply are the exact commands to be used from a terminal or xterm or gterm or rvterm - whatever terminal you like.  I don't really use the gui - it is too specific for every release and distro to bother learning. Give me an xterm any day.

No, unzip is not the same as bunzip.


Sorry, I'm terrible at explaining things. Hopefully someone else can translate for me.  It is my failing. Those commands need to be run from the same directory as the firefox*whatever file.

---

### Post by BeverlyStacey on 2013-03-24
Thank you all for your posts.  I'm sure I would have got it sorted with your help but I had to have it looked at as more and more odd things were happening.  It appears the hard drive is failing.  

How can I mark this solved, TheFu?

Thanks again everyone, I very much appreciate your help with this.

---

