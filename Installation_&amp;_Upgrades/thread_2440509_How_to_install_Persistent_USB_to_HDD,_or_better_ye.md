---
title: "How to install Persistent USB to HDD, or better yet convert to ISO"
date: 2020-04-11
forum: Installation &amp; Upgrades
---

### Post by mattzab on 2020-04-11
I used mkusb to make a persistent Ubuntu system on a 128GB USB Drive.
I've gotten this thing customized and it's all working magnificently.
I'd like to be able to install this system as-is, if possible.
Better yet, How can I make this into an ISO that can be distributed?

For making an ISO, would I be safe enough to just rsync /home/ubuntu over to /etc/skel and then build the ISO?
I'd like to keep my customizations, basically make this thing into a live system that could be shared.

I've followed the CustomizeUbuntuLiveCDFromScratch manual (back when I could access the wiki, I'm being throttled for no reason, some kind of glitch)
I get the idea of how to make custom live systems, but I've only successfully done so with the debootstrap method, not from a live filesystem.
I attempted to do it with a live system, but it was disastrous. The ISO I generated couldn't boot- got an error saying no boot disk. And also some of the changes made during the process corrupts the UID for the user, so I can't even make changes when chrooting into my formerly working install.

To wrap this up, I feel like I'm overcomplicating this. There must be some kind of tool or method that is more simple than what I'm doing. I came across linux-live.org, but that didn't work at all. (Neither of the images created worked)

A little help?

Would it be reasonable to try to follow the custom scratch guide and after the debootstrap, just run aptik to restore everything, then rsync that to /etc/skel, then build?

What would you do?

Thanks!
(Currently the best I can do is distribute a copy of a bare-metal-backup, but my friends have to have a 128GB drive to dd this big ole image to)

---

### Post by C.S.Cameron on 2020-04-11
If you are not intent on mass distribution, perhaps creating an image file is a good start.
Disks comes with Ubuntu, you can use it running on a live USB to create an .img file of your persistent USB or of a Full install.
The image can be written to HDD using Disks, balenaEtcher, or mkusb. There is also a Windows version of Etcher.

---

### Post by dragonfly41 on 2020-04-12
I would explore using CUBIC to customise your ISO.

---

### Post by oldfred on 2020-04-12
One of the nice things about Linux is that you can do everything from command line.
And then you can put all those lines into a script.

I typically install Ubuntu multiple times and every new version. And found I was doing the same changes over & over manually. So I found command line ways to do most of the changes I want. And in most cases those also work when I change to a newer version or different ISO. Then you do not have to create a new custom ISO for every release. First time I just did commands from terminal, partially to know they worked & partially to understand them. Then I copied list of commands from terminal into a bash file.

---

### Post by Redalien0304 on 2020-04-12
Cubic is Good i am using it Currently for a Custom ISO now.

---

