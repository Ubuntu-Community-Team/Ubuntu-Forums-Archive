---
title: "Problem with External Hard Drive After Installing Ubuntu"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by Maziar_Kosarifar on 2014-08-04
I have downloaded Ubuntu the latest version. And followed the instruction in [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx) 

So now I can't use my external hard drive as a normal memory. 

And I don't want to remove or format the disk ( As I have all my memory and important files on that drive )

Any suggestions on how to retrieve my data from that file ? 

I'm using Macbook Air ( 64 GB 2012 ) 

( And obviously I don't have any other computer or external HDD so I only had my backup on that disk which is gone or at least not usable ) 

It is urgent and I really need to get to my files.

---

### Post by Bashing-om on 2014-08-04
Maziar_Kosarifar; Hi ! Welcome to the forum.

What do you see in the left pane of the file manager ? .. That external hard drive - when plugged in - should be accessable automagically from the file manager;

If that external drive is in a Mac-osx file format, it is foreseeable that additional tools will be needed to "see" that drive.
Please provide the output - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

``` in the event there remains a problem.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We will then see what there is to be done.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

