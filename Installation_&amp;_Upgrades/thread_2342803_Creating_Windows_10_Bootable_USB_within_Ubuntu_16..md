---
title: "Creating Windows 10 Bootable USB within Ubuntu 16.04."
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by arthur24 on 2016-11-10
I'm using Ubuntu 16.04LTS.
I'm not that much of a Windows user, but I need it for a course I'm following and one specific videogame I really like.
So I head out to the internet, got the win10 x64.iso from microsoft and searched for any procedure on how to get a windows 10.iso on a flash drive in Ubuntu.
It's probably easy as pie, but the procedures I'm finding through google are either written for 14.04, 15.04 or they oftenly suggest the application UNetBootin. That application however doesn't work for me. 

Because when I want to browse directories to select the iso image the Unetbootin application only shows the ./ (root) file structure. And it doesn't show any other location besides root within that folder tree.
Which isn't where my ISO images are located obviously.
So why I can only navigate the root directory within UnetBootin, I really don't know. But I can't use the application properly because of it.

Anyway to fix this anomaly in Unetbootin? Or is this application simply incompatible with 16.04 and thus only shows me root folders.
 Is there a much better alternative for installation?

---

### Post by yancek on 2016-11-10
If you read the home page of Unetbootin, it states specifically that it is designed to create a bootable "Linux" usb and won't work on other operating systems.  Meaning windows.  

If you are using Ubuntu to do this, you need to first loop mount the windows iso file, then copy the windows folders/files to your usb which should have an ntfs formatted partition.  There are several other steps involved and I'll refer you to the link below which I have used successfully myself.  I would suggest reading through the page before beginning so you have an understanding.  If you have problems with it, post back.

 [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by C.S.Cameron on 2016-11-10
Found out just the other day that Sudodus has added Windows 10 boot disk to mkusb.

Used to be you could just format the drive NTFS and extract the iso to it.
I think MS is trying to tighten things up so that you need to use their tool.

see
[https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011](https://ubuntuforums.org/showthread.php?t=2328513&p=13557011#post13557011)
post7

---

### Post by arthur24 on 2016-11-10
@yancek.

Thanks for your advice. If I mount and copy the iso contents isn't it likely to go over 4GB total? (the iso image is 3.8gb so I'm sure this is the case) 
That means I need a UEFI boot device right, meaning I require most of all the extra steps that your guide explains.
No problem, although unfortunate. I'm going to spend my time reading it and getting it done. I'll surely post back if I run into any trouble or if I'm successful.

@C.S.Cameron.

Thanks to you aswell. Mkusb definitely would make the process alot easier, so I hope it works.

---

### Post by Mark Phelps on 2016-11-10
You do know that NOW, Win10 is no longer free, right? Unless you purchased a license from Microsoft, your Win10 will not activate.

---

### Post by yancek on 2016-11-10
> f I mount and copy the iso contents isn't it likely to go over 4GB total? 

No.  It should be the same size when copied to the flash.  The windows iso I used was 3.2GB and was exactly that size when copied to the flash drive. You're just copying folders/files so there is no reason to expect any difference in size.  If you have other data on the flash, I could see where it would be a problem.  Why the 4GB limit?  Is that the only size flash drive you have?  I'm not sure what you are asking about UEFI.  I still use MBR so that wasn't applicable in my case.

---

### Post by C.S.Cameron on 2016-11-10
Another option might be to run Win 10 in a VirtualBox.
VBox adds a layer of slow but I find it acceptable for most of my Windows needs.

---

### Post by arthur24 on 2016-11-11
I know windows 10 isn't free and I got a discounted version cheapish from a webshop (product key only)
The reason I brought up the file size is because I thought Microsoft compressed their ISO files so the content would go over it's original 3.8gb after mounting and extracting the contents.
This seems not to be the case like you people say.

Good news. The guide provided by Yancek worked fine and Windows is up and running.
As for the Virtual box suggestion, that serves the requirements for the software I use during my course. But it will not run the videogame I wish to play, and badly with the 1 or 2 Vbox workarounds I ran across. 
But a Vbox should suffice in most cases, I agree.

---

### Post by yancek on 2016-11-11
> The reason I brought up the file size is because I thought Microsoft  compressed their ISO files so the content would go over it's original  3.8gb after mounting and extracting the contents.

The iso files are compressed and when installing window (or Linux for that matter) you will see that after installation, it takes up much more space than the iso.  In the situation you describe, you are simply copying the extracted file and not de-compressing so it should not matter.  

Glad you got it working.

---

