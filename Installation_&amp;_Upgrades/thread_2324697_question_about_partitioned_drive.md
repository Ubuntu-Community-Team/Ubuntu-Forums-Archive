---
title: "question about partitioned drive"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by scott_2 on 2016-05-15
I want to install Ubuntu on a partitioned drive. I already shrunk my C drive by 100gb. Should I assign a drive letter to this drive? Or just leave it unallocated?

---

### Post by Impavidus on 2016-05-15
The drive is the entire physical device. That C thing is only part of the drive and is called a partition. Unfortunately Windows call it both a drive.

Leave the free space unallocated. Windows doesn't understand Linux partitions.

---

### Post by Mark Phelps on 2016-05-15
BEFORE you do anything about installing Ubuntu, reboot into Windows a couple of time to let it make any needed filesystem adjustments from the resizing you did.

If you just rush into the install without doing this, you risk being left with a corrupted Windows filesystem, which (since you have to boot into it to fix it) will be VERY HARD to then fix.

Good Luck

---

### Post by scott_2 on 2016-05-15
Hello Ubuntu support community!

Here's what I want to do:

I want to dual boot windows 10 and Ubuntu. I want it so that when I turn on my PC, I will have the choice to boot into Windows, or Ubuntu. Is this possible? I see a lot of talk on here about something called GRUB, and I get the impression thi is something I will need to be able to do that. Is this correct?

I have a Lenovo laptop PC. Its only about a year old. I think I have already successfully turned off fast boot/UEFI. I have also shrunk about 100gb from my drive for Ubuntu. 
I want Ubuntu to be installed on a partitioned drive.

At any rate, How do I make this happen? That is, choosing which OS to go into upon startup.

---

### Post by grahammechanical on 2016-05-15
Grub = GRand Unified Bootloader. You do not have to worry about getting Grub. The bootloader is installed as part of the normal Ubuntu install process. There are a couple of things that you do need to worry about.

Windows 10 will be installed in what is called EFI mode and Ubuntu must also be installed in EFI mode. Otherwise we will not get an effective dual boot between the two. So, you must run the Ubuntu live session in EFI mode and not BIOS/legacy/CSM mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That 100GB must also be unallocated space and not a partition. This is what you will see during the install process.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

This is how to create a DVD disc installer on Windows

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

This is how to create a USB memory stick installer on Windows

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

This is where you get the Ubuntu ISO image from

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Regards.

---

### Post by grahammechanical on 2016-05-15
Please do not in effect make duplicate posts. I answered in your second post. 

[http://ubuntuforums.org/showthread.php?t=2324705](http://ubuntuforums.org/showthread.php?t=2324705)

---

### Post by oldfred on 2016-05-15
Threads merged.

Please post only one thread per topic. And best to have good description in title, so those that may be able to help will open your thread for more info.

       From the Posting Guidelilnes:
[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)
> Do not cross post, or post the same thing in multiple locations.

---

### Post by scott_2 on 2016-05-16
Thanks for the help so far. 

> **grahammechanical said:**
> Grub = GRand Unified Bootloader. You do not have to worry about getting Grub. The bootloader is installed as part of the normal Ubuntu install process. There are a couple of things that you do need to worry about.

Windows 10 will be installed in what is called EFI mode and Ubuntu must also be installed in EFI mode. Otherwise we will not get an effective dual boot between the two. So, you must run the Ubuntu live session in EFI mode and not BIOS/legacy/CSM mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

That 100GB must also be unallocated space and not a partition. This is what you will see during the install process.



To be honest, even this is a little too advanced for me. So I get that I don't need GRUB. That's great! But I can't make heads or tails of the quoted link above. It may as well be written in greek. I don't understand all this UEFI stuff.

I can't make sense of what I need to do to prepare my computer to install Ubuntu to dual boot with windows. 

I actually just did a clean install of Windows 10. So all drives are merged as one unified C drive.

What should I do next?

Edit: I do have a USB ready to go, and the Ubuntu ISO downloaded

---

### Post by yancek on 2016-05-16
A fairly straight forward explanation of UEFI and dual booting with windows/Ubuntu is at the link below.  If you don't understand it  either don't do anything or come back here with a sepcific questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> What should I do next?

You need to shrink the windows C:\ partition to create unallocated space on which to install Ubuntu.  There is no point in creating a partition for Ubuntu in windows.  Just leave it as unallocated space.  Use whatever software you want to put the Ubuntu iso on your usb drive (pen drive linux, unetbootin, etc.) and reboot and begin the install after reading the link above carefully.

---

### Post by scott_2 on 2016-05-16
> **yancek said:**
> A fairly straight forward explanation of UEFI and dual booting with windows/Ubuntu is at the link below.  If you don't understand it  either don't do anything or come back here with a sepcific questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)



You need to shrink the windows C:\ partition to create unallocated space on which to install Ubuntu.  There is no point in creating a partition for Ubuntu in windows.  Just leave it as unallocated space.  Use whatever software you want to put the Ubuntu iso on your usb drive (pen drive linux, unetbootin, etc.) and reboot and begin the install after reading the link above carefully.

I'm sorry, I was under the impression that "what do I do next" was a pretty specific question.

I don't mean to be rude, but like I said in my previous post, the above link makes no sense to me at all! I can't ask a specific question because I can't even make sense of the first paragraph.

I am very interested in learning to use ubuntu and I really want to do this, but I'm very new to this and I need help, in very layman's terms. So if it's okay, I'd like to ask questions sort of one step at a time here, in this thread, instead of trying to read a guide that is too advanced for me. And believe me, I did read through it, very carefully, more than once.

If I'm too noobish, or if you think me incapable of doing this, feel free to say so.

All of that being said, my next question would be:

I recall seeing somewhere, and I can't find it again, that Ubuntu will automatically allocate space for you when you go to install it. Is this true? Or do I need to set some space aside in windows first?

---

### Post by oldfred on 2016-05-16
While auto install will shrink NTFS partition and set some default size for / (root) and swap it is better to manage yourself.

Some have reported issues using Linux to resize NTFS partitions. May normally work but better to use Windows tools for Windows and Linux tools for Linux.

So use Windows own partitioning tools to shrink the NTFS partition and reboot immediately so it can run chkdsk. Chkdsk always required after a resize, and that cannot be done from Linux.

And if Windows 8 or later make sure fast start up is off.

Summary install instructions in link in my signature and links to details if summary not well understood.

---

### Post by scott_2 on 2016-05-17
Ok. I successfully got it installed! It even automatically lets me choose Ubuntu or Windows upon startup. However, I am unable to connect to my wifi. I searched online for help but really couldn't find any help. Here is a screen shot of what it looks like: 

As you can see, there are no networks even listed. Am I looking in the wrong place?

My girlfriend uses Ubuntu, and when she installed it, our network was right there. All she needed to do was click on it and enter the password and wallah she was on. 

So my question is: How do I get onto the internet with Ubuntu?[ATTACH]269138[/ATTACH]

---

### Post by oldfred on 2016-05-18
Best to start a new thread with wireless and model of wireless chip in title.
Then those that know those issues may offer to help, but they will not find this thread.
They often ask for this:
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
OR:
[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)

---

### Post by scott_2 on 2016-05-18
Thank you sir. You have been very helpful so far!

---

