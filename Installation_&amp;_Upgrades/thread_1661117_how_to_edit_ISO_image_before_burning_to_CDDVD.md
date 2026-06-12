---
title: "how to edit ISO image before burning to CD/DVD?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by saschap on 2011-01-06
Hi, I plan to make multi boot linux DVD, with help of SarduCD software, so, I have one question. 
configured Linux ISO image is not as I would like, I would like to change appearance and to add some softwares, in that way I will not have to change and install it every time I use live DVD in the future. 
I have now already installed 4 linux in one DVD but evey time I use it, I must change and install softwares, now I want to install on DVD the newest version of Ubuntu and Kubuntu, beside puppy and some other distros, and my question is:
**how to edit K/Ubuntu ISO image with aim that I don't need to change anything anymore after I burn it on DVD? **

I suppose I should unpack and edit ISO image (add softwares and change appearance) and after that pack it again in ISO image. Maybe it is easier to burn Ubuntu to CD, to change and install what I want, into Live CD, and then to extract such Ubuntu to ISO image, then it would be ready to burn it together with other distros into DVD?

Some advices how to do it, from windows or from linux operating system?
I suppose, process is the same for Ubuntu and Kubuntu...

---

### Post by saschap on 2011-01-08
I think this is the solution:

To  make an ISO from your CD/DVD, place the media in your drive but do not  mount it. If it automounts, unmount it. (ubuntu automount so you need to  unmount, that's quite easy, just choose the option unmount from the  shell).
Command is: 
dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

uh, it is not solution, I would have to use Ubuntu, to change settings and add softwares and then to extract CD or DVD to ISO file. in that way I save settings.

---

### Post by dandnsmith on 2011-01-08
[tells how to make customised CD](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
[customise install CD](https://help.ubuntu.com/community/InstallCDCustomization) is another one
and I feel I have seen a tutorial on making a CD from your current installation.

As you say, the dd process isn't the correct way to go - it only makes one more stage (adding CD to iso to the iso to CD which youve probably already done).
Better to loop mount the iso, so you can extract the file content ready to modify it.

---

