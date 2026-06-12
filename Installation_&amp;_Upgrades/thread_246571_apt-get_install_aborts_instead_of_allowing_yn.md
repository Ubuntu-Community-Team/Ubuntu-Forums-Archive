---
title: "apt-get install aborts instead of allowing y/n"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by pulper on 2006-08-29
hi everyone:

i'm trying to install ubuntu on my second computer now and got a list of the installed packages from my first computer and want to use that to clone the installation.  i'm running into a problem in that, the final line doesn't allow me to continue and selects abort.  Here's what i'm doing:

i copied the sources list from computer#1 to new computer
on computer#1, i did the following:
  sudo dpkg --get-selections | grep '[[:space:]]install$' | \
  awk '[print $1]' > package_list
i saved this to a floppy drive and put in the new computer
on the new computer, after updating the sources list, i did:
sudo apt-get update
finally, to do the update of the packages, i did the following:
cat package_list | xargs sudo apt-get install

the screen scrolls for a few seconds and then the final lines show up as such:

0 upgraded, 748 newly installed, 3 to remove and 0 not upgraded.
Need to get 970MB of archives.
After unpacking 3122MB of additional disk space will be used.
Do you want to continue [Y/n]? Abort.

then i'm given my normal prompt.  no chance to select "y".

any idea what is happening here?  any suggestions are appreciated.  Thanks,

Paul

---

### Post by az on 2006-08-29
Use 

dpkg --set-selections to input your list and then

sudo apt-get dselect-upgrade

Redo your list by using

sudo dpkg --get-selections > file

and then transfer it and run

sudo dpkg --set-selections < file
sudo apt-get dselect-upgrade

You can also use synaptic to do that graphically.

---

### Post by pulper on 2006-08-29
thanks for the help, but what am i doing wrong here?

my current file is "package_list"

sudo dpkg --get-selections > package_list
sudo dpkg --set-selections < package_list
sudo apt-get dselect-upgrade

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

i know there are a number of files in "package_list", so i'm not sure why this isn't working (ie nothing to upgrade/install).  any advice?

Thanks again,

Paul

---

### Post by pulper on 2006-08-29
i got it to work.  thanks!

i thought you were referring to using my previous file that was obtained the way i mentioned in the first thread.  i used computer#1 to make the list again with your instructions and right now it is downloading.  Thanks again,

Paul

---

