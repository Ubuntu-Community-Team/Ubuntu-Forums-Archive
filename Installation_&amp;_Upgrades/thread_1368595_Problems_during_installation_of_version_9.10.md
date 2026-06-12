---
title: "Problems during installation of version 9.10"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Underestimatedkiller on 2009-12-30
Hi everyone.

First of all, I would just like to thank everyone who will post and  answer (or at least try if some answers fail) my question :) And I am  "sorry" for the huge length of the post. I wanted to post every-tiny-bit  of info I had, and there was a lot! :P

I became a bit curious about Linux a while ago, but didn't really have  the time to go through the partition resizing, and didn't have the time  to really get to know Linux, but now I do. So, I went and searched a  bit, and found Ubuntu 9.10 - Netbook Remix. Tried to install it  different ways, and each time, there is a problem.

Here is my **laptop's** configuration:

Windows 7 Ultimate
Gateway MX8734,
Processor T2060 Intel Dual Core @1.6Ghz
2 Gb of RAM DDR2 667 Mhz
Video card Intel Mobile 945 Express with 256mb or RAM
Hard Disk Drive of 150 Gb (Technically 160 but meh), Split in 3: 130 Gb  on main HDD, 15 Gb on secondary HDD (which is the installation  destination for Ubuntu), and a 4 Gb Linux Swap "HDD"

Having said that, here are all the problems I get:

I downloaded the file, then extracted it and tried running the  installation from the extracted files this exact way: Opened up  "wubi.exe", and here was the options I selected:

[LIST]
[*]Installation drive: E: (14GB free)
[*]Installation size:  7GB
[*]Desktop environment: Ubuntu Netbook Remix
[*]Language:  English (US)
[*]Username: Underestimatedkiller
[*]Password:  ********* (come on, ain't going to put my real password lol)
[/LIST]
And  then I pressed Install. Then it pops me this error message:> An  error occurred:

Cannot download the metalink and therefore the ISO

For more information, please see the log file:
C:\users\underestimatedkiller\appdata\local\temp\wubi-9.10ubuntu1-rev160.logI  of course went into the log, and it's telling me it was trying to fetch  a file on the internet, and the two metalinks were broken. Here is the  part of the error message(sorry for the length):> 12-30 00:02 DEBUG   downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink)  > E:\ubuntu\install
12-30 00:02 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink)  err=[Errno 14] HTTP Error 404: Not Found
12-30 00:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink)  > E:\ubuntu\install
12-30 00:02 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.metalink)  err=[Errno 14] HTTP Error 404: Not Found
12-30 00:02 DEBUG  TaskList: ### Finished get_metalink
12-30 00:02 ERROR  TaskList: Cannot download the metalink and therefore  the ISOSo there I got stuck.

After that, I decided to burn it on a CD, and to install it from  Windows. Opened up Nero, double-click on the Ubuntu iso file, and then  it pops me this error message, with the title "Foreign Image  File":> The entered block size does not correspond to the image  length. The block size may be wrong. Do you want to correct the value or  ignore the problem? Tried to correct it every way possible, it  wasn't letting me burn it.
I then tried to burn it with PowerISO directly, worked with no problems,  for some reason.
After that, I tried running it from the CD, and it popped me this error  message: > No CD detected, cannot run CD menuAnd it won't  let me install it.

I then tried to boot from the CD. I then got faced with 6 options, and  non were doing anything. There was (if I recall correctly, and not the  exact words):

[LIST=1]
[*]To try Ubuntu without changing  my computer
[*]To install Ubuntu on my computer
[*]***Can't  recall***
[*]***Can't recall***
[*]Test memory
[*]Boot  from main harddrive
[/LIST]
The only option that was working was the  6th one, which just booted my Windows 7 OS.

I completely am out of ideas, and I don't know what to do anymore to try  to make it work.

If anyone already had any of these problems, and managed to fix it, let  me know :)

And, before anyone says something, _**I do not have a USB drive to  try and install it from it, or even on it.**_

Thanks a lot once again to everyone who will answer me :)

Alex

---

### Post by gordintoronto on 2009-12-30
If Poweriso actually worked, the first option ("try Ubuntu without changing my computer") would work.  This is called, "running from a Live CD."  I have only used Nero to burn CDs from Windows (and it has always worked perfectly), so I can't really help you with Poweriso.

Your computer is not a netbook, so I wouldn't use the Netbook remix.  It is old/slow, so I would use Xubuntu.

---

### Post by Underestimatedkiller on 2009-12-31
Thank you for the answer.
Like I already said before though, none of the 5 (I said 6, there actually was 5, sorry) options were working, except the last one, to boot from the main HDD AKA Windows 7.

Just to satisfy my curiosity...what exactly is the definition of a Netbook? 
And well, since it does not seem like the Ubuntu Netbook Remix will work I'll just go install Xubuntu :)

---

### Post by gordintoronto on 2009-12-31
In Nero Smartstart, you need to select "Copy and backup"/Burn image to disk.  This has always worked for me.  You might have had a bad download.

A netbook has an Intel Atom processor, and a screen which is less than 11 inches, usually with a vertical resolution of 600 pixels or so.  The netbook remix has some special stuff to make the short screen OK.

The Atom is terrific for battery life, but it's S-L-O-W.

---

