---
title: "Using the terminal to access .tar.gz file, need help!"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by myromance123 on 2008-07-10
Basically Im trying to install a program called Alice and I have been trying to follow the below instructions, I do not know where else to post this so I am posting it here (got removed from other sections already)

 I am stuck at the bit where it tells me to 'Open a terminal to the directory where you downloaded the file.'  How do I do that ?
 Since Im using ubuntu 8.04 would it mean I already have the opengl drivers as well?? If not how do I access/get/download them?

  This is the original instructions:
> Linux-only instructions (Thanks, Charles!):

Alice needs 250MB of free space.
Please have opengl drivers and a Java Runtime Environment([http://www.java.com/en/](http://www.java.com/en/)).

Download the file Alice-2.0.0.tar.gz.
Open a terminal to the directory where you downloaded the file.
Run the command: tar xvfz Alice-2.0.0.tar.gz then run: cd Alice/Required then run: ./run-alice

---

### Post by Rallg on 2008-07-10
What it wants you to do is open a Terminal windows (Start menu, Accessories, Terminal). Then change directory (cd command) to wherever that *.tar.gz file is located.

If you downloaded the file to your home directory, you are already there when you open the Terminal, so you don't have to change directory. If you downloaded it to your Desktop (which is a sub-folder of your user Home), then

cd Desktop

takes you there. Or, you can always use an absolute path, beginning with the slash (which means your file system's top level):

cd /where/ever/you/put/it

Until you close the Terminal or tell it to go elsewhere, you remain in the same folder. So when you unpack the *.tar.gz file, the process creates sub-directories there. When you then

cd Alice/Required

you are going to a newly-created subdirectory. The following

./run-alice

presumably begins some sort of configuration.

I don't know about your opengl drivers.

---

### Post by myromance123 on 2008-07-12
Thank you very much, I got through the instructions with your help :D

 Cheers ~  :lolflag:

---

