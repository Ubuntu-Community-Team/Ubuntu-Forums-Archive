---
title: "From Windows to Ubuntu on ThinkPad T61, cannot install."
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by catchagato on 2008-08-13
When I first installed Ubuntu, everything went well, but then when I had restarted my laptop, it gave me a screen that said it cannot boot from any device. So, I tried to re-install using the Ubuntu CD that I made, and then when I tried to install it now, I keep getting these repeated lines of numbers and messages that say things like, "ata1.00: status, error, excerption Emask..."
I really don't know what's wrong, and I can't get to the desktop or anything. If anyone can help, that would great. Thanks in advance!

---

### Post by KWM987 on 2008-08-13
Can you boot the LiveCD or does it not let you boot from anything?  

If you can get in, run GParted and wipe your drive by deleting all of the paritions, and see if it helps the install get anywhere.

---

### Post by catchagato on 2008-08-13
It doesn't even let me boot from anything. If I put in the CD, I get to the Ubuntu screen that lets me choose to Install Ubuntu, so I select "Install Ubuntu" but then it takes me to a screen which keeps repeating these numbers and words. I can't get into the desktop or anything.

---

### Post by KWM987 on 2008-08-13
Rather than install it right off the screen, select to Try Ubuntu with no change to the system.  That should load you into a Live Session where you might be able to work out the problems preventing the install.  

As I said, if you can get into there, run GParted to delete any existing partitions and reformat the drive.  Then select the Install icon on the desktop.

---

### Post by catchagato on 2008-08-13
Here are 2 pictures of the screen I get when I try to Install Ubuntu using the LiveCD. First, it goes to the Ubuntu logo with the progress bar, then afterwards it goes into this:

[IMG]http://i115.photobucket.com/albums/n314/catchagato/T61_screen001.jpg[/IMG]
[IMG]http://i115.photobucket.com/albums/n314/catchagato/T61_screen002.jpg[/IMG]

---

### Post by KWM987 on 2008-08-13
What version of Ubuntu is your CD? and further, does it allow you to get to a Live Session?

---

### Post by catchagato on 2008-08-13
It's the version I downloaded for standard personal computers, and it's the Heron (the newest one out now), the i386 or something. I don't know if it allows me to get a Live Session, how do I find out?

---

### Post by KWM987 on 2008-08-13
Select the first option from the list it gives you, when the disc first boots up.  It should say something like "Try Ubuntu with no change to my computer".

---

### Post by catchagato on 2008-08-13
I have tried it already, and it still gives me the same screenshots above.

---

### Post by catchagato on 2008-08-13
Ok, I just let it run longer without shutting off my laptop, and then new things started to appear on screen. Then, the desktop came back on! Now, I'm going to click on the "Install" on the desktop and see how it goes this time...

---

### Post by wenuswilson on 2008-08-13
As KWM987 stated, in the live session go to Gparted. And wipe out the whole partition and reformat in ext3.

---

### Post by catchagato on 2008-08-13
I can't seem to find GParted anywhere. Do I need to download and install it?How do I reformat in ext3? I really apologize for being a beginner at this.

---

### Post by wenuswilson on 2008-08-13
In the live session System > Administration > Partition Editor.

(Or in the terminal "sudo gparted")

Depending on what you want for your partition (the whole disk vs half of it, etc) select it, right click on it and hit delete, then right click on "format to" and select ext3. then hit apply. it should only take a few seconds to format. make sure you know what partition you changed (sda#) and then install Ubuntu.

---

### Post by KWM987 on 2008-08-13
If you're in a Live Session you can type: sudo gparted

and use the editor to delete any partitions on the disk and them attempt a reinstall.

If its not there you can still install and run it with: sudo apt-get install gparted

and run it with the first command.

It looks like you have problem with critical filesystem IO and access, possibly due to corrupted files on your disc or that got written to the drive and are preventing blocks from being read correctly.

Step one it to see if repartitioning helps with the steps above.  If that doesn't work, try downloading and burning the disc again (possibly a bad download and image you're using; you can even use 64-bit if you want, since the processors in the T61's support this) and following the same steps.  If you are still having the same issue, it could be a sign of hardware failure or major corruption that could mitigated with some advanced techniques, but most likely would need to be cured with drive replacement. (hopefully not)

---

### Post by wenuswilson on 2008-08-13
Ps, we were all beginners at this at some point.

---

### Post by wenuswilson on 2008-08-13
> **KWM987 said:**
> try downloading and burning the disc again (possibly a bad download and image you're using

The LiveCD should have a CD image integrity test on it to check if that is in fact the case.

---

### Post by catchagato on 2008-08-13
Yeah, I did the integrity test right after I burned the CD, and it was good. So I know it is not the CD that is bad.

---

### Post by catchagato on 2008-08-13
I don't have any partitions that show up in GParted. All I see is /dev/sda1 which is ext3, /dev/sda2 which is the extended, and then there is a sub-tab under that which is /dev/sda5 and it's the linux-swap.

---

### Post by wenuswilson on 2008-08-13
A little side note, if you plan on creating a dual boot, don't get rid of the Windows partition because it's a pain to install after Ubuntu becomes native. Unless of course you go the virtual drive route (wine or VirtualBox)

---

### Post by wenuswilson on 2008-08-13
> **catchagato said:**
> I don't have any partitions that show up in GParted. All I see is /dev/sda1 which is ext3, /dev/sda2 which is the extended, and then there is a sub-tab under that which is /dev/sda5 and it's the linux-swap.

Those are the partitions. sda1 and sda2.

---

### Post by KWM987 on 2008-08-13
> **catchagato said:**
> I don't have any partitions that show up in GParted. All I see is /dev/sda1 which is ext3, /dev/sda2 which is the extended, and then there is a sub-tab under that which is /dev/sda5 and it's the linux-swap.

Those are your partitions, delete all of them, and make new ones with the install.

You can make one big one on your drive before hand, have it format to something like ext3, and then delete it again to give it a cleaning in a sense.  Or you can just delete them and go to the installer, since Ubuntu will make the partitions and format automatically for you.

---

### Post by catchagato on 2008-08-13
I think my hard drive might be bad. Every time I try to install Ubuntu, it gets to a certain point where everything stops and freezes, and the hard drive light is solid green on my T61 all the time.

***I FINALLY got a successful install. BUT, during that install, a notice popped up and said to either check my cd/dvd or the drive, and make sure the optical lense is clean, or check my hard drive. So maybe I might have to replace my hard drive in the near future... I deleted all the partitions and formatted to ext3 like you guys said. In my system monitor, for the File Systems, my hard drive is 80GB, but under the Total, it says "70.9GB" and under "Free" it says, "68.8" and then Available, I have "65.2."
Can anyone let me know if this sounds about right, or if it's normal to have this much space after a new installation? Thanks!

---

### Post by wenuswilson on 2008-08-13
this is after you reformatted the entire system?

how old is the thinkpad?

or even see if you can put another os on there.

---

### Post by catchagato on 2008-08-13
I purchased this ThinkPad this previous December (07), so it's only 8 months old. Not old at all. It could be a defective hard drive.

---

### Post by KWM987 on 2008-08-13
> **catchagato said:**
> I think my hard drive might be bad. Every time I try to install Ubuntu, it gets to a certain point where everything stops and freezes, and the hard drive light is solid green on my T61 all the time.

***I FINALLY got a successful install. BUT, during that install, a notice popped up and said to either check my cd/dvd or the drive, and make sure the optical lense is clean, or check my hard drive. So maybe I might have to replace my hard drive in the near future... I deleted all the partitions and formatted to ext3 like you guys said. In my system monitor, for the File Systems, my hard drive is 80GB, but under the Total, it says "70.9GB" and under "Free" it says, "68.8" and then Available, I have "652."
Can anyone let me know if this sounds about right, or if it's normal to have this much space after a new installation? Thanks!

It's possible that the drive is gone, perhaps an actual result of the Load_Cycle issue that has been tossed around and related to another OS, or just general failure.  I would try installing another OS like has been suggested to see if it gives you similar behavior.

Also if you can still use Ubuntu in anyway install the smartmontools package to check the status of your drive.  If it's bad usually there will be a SMART error of some kind, and you can also check the Load_Cycles to see if you were a victim of that, amongst other things that could give you the satisfaction of possibly knowing what exactly made it go poof.

---

### Post by catchagato on 2008-08-13
Yeah, Ubuntu is running just fine right now. Nothing has gone wrong so far. How do I install the smartmontools package?

---

### Post by wenuswilson on 2008-08-13
> **catchagato said:**
> Yeah, Ubuntu is running just fine right now. Nothing has gone wrong so far. How do I install the smartmontools package?

system > administration > synaptic package manager > search > smartmontools

or in a terminal
> sudo apt-get install smartmontools


that's where it is but i don't know how to open it, "sudo smartmontools" is giving me a bash.

---

### Post by KWM987 on 2008-08-13
> **catchagato said:**
> Yeah, Ubuntu is running just fine right now. Nothing has gone wrong so far. How do I install the smartmontools package?

Go to:

> System > Administration > Synaptic Package Manager - smartmontools

Mark it for install and hit apply, alternatively you can use Terminal through:

> Applications > Accessories > Terminal

and issue the command:

> sudo apt-get install smartmontools


Once you get that you can check your Load_Cycle_Count through the command:

> sudo  smartctl -a $HDD | grep Load_Cycle_Count

If that does not work, you may need to enable SMART monitoring through the command:

> sudo smartctl -s on $HDD

The Load_Cycle_Count is an issue that has been a source of discussion recently, where frequent loading and unloading of the hard drive due to aggressive power management, will cause the drive to prematurely fail, possibly even within a time frame as short as that which you state you've owned the system.  You can search the forums in the Hardware & Laptop area for threads with much more detailed info on this.

If the number returned is exorbitantly high (600,000+) then that is probably the issue.  Otherwise it is probably just a generic defect.

After all this you should run a self test on the drive, with the command:

> sudo smartctl -l selftest /dev/sda

This will tell you of any errors the drive is experiencing and just how close to failure you might be.  Certain things like bad blocks can be mitigated with advanced use of the tool, and you can bring your drive back to life so to speak.

---

### Post by catchagato on 2008-08-13
I tried to install MediBuntu, but I typed "Medibuntu" wrong in a line in the Terminal, so how I cannot access Synaptics Manager, it gives me this error:

E: Type '--02:34:10--' is not known on line 1 in source list /etc/apt/sources.list.d/mdeibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How can I correct this? Or, delete this? Thanks!

***I got rid of the problem, but how do I delete the actual file in etc/apt/sources.list.d? It won't give me permission to.

---

### Post by wenuswilson on 2008-08-13
> **catchagato said:**
> I tried to install MediBuntu, but I typed "Medibuntu" wrong in a line in the Terminal, so how I cannot access Synaptics Manager, it gives me this error:

E: Type '--02:34:10--' is not known on line 1 in source list /etc/apt/sources.list.d/mdeibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How can I correct this? Or, delete this? Thanks!

***I got rid of the problem, but how do I delete the actual file in etc/apt/sources.list.d? It won't give me permission to.

in a terminal:
> sudo nautilus /etc/apt/sources.list.d
that should open the folder containing that file (it might be hidden so [view > show hidden files])

if you want to edit that .list file:
in a terminal:
> sudo gedit /etc/apt/sources.list.d/medibuntu.list



why would you want to delete that?

---

### Post by catchagato on 2008-08-13
I don't, I aciddentally mispelled "medibuntu" in the file name, so I want to delete that file and creat a new one. I got it already though. Thanks.

**I've reinstalled again, and I do think it is my hard drive that is not conistent. Sometimes I get a successful install, and sometimes it totally fails. I called Lenovo customer service today and they are sending me a new hard drive. It should get here this Saturday. I hope that this will fix the problem, and my laptop will be much more consistent.

---

### Post by KWM987 on 2008-08-13
> **catchagato said:**
> I don't, I aciddentally mispelled "medibuntu" in the file name, so I want to delete that file and creat a new one. I got it already though. Thanks.

**I've reinstalled again, and I do think it is my hard drive that is not conistent. Sometimes I get a successful install, and sometimes it totally fails. I called Lenovo customer service today and they are sending me a new hard drive. It should get here this Saturday. I hope that this will fix the problem, and my laptop will be much more consistent.

Nice, let us know if you have any more issues.

Optionally, you could search the model name/number of the drive they send you to see if it is an SATA II model or not, drives of this type are able to send data twice as fast as the original standard.  Most often, the drives come with a small jumper on the back that caps their transmission to the speeds of the original standard and that must be removed to enable full speed operation.  

By default I believe lenovo only uses the original SATA speed, even though the T61 is equipped with an SATA II port.  I made this adjustment and discovery when I upgraded the harddrive in my machine a few weeks ago.  Thus, doing a little research and making the small adjustment could be a small side project if you so wished or want to ensure you get every bit of performance you can.  The drive will function fine whether or not you remove a jumper like this.

---

### Post by catchagato on 2008-08-14
So, how do I remove this jumper?

---

### Post by KWM987 on 2008-08-14
> **catchagato said:**
> So, how do I remove this jumper?

If the drive has the feature, you just pull it off, it is not secured by anything other than the two pins it is bridging.  Granted, on laptop drives, they tend to be quite small, and by nature can then be difficult to get at with your fingers or other tool, despite being plainly visible and accessible.

Be sure you do your homework before removing anything to ensure you are removing the jumper for the right purpose.

The following image is just meant to illustrate what the jumper is and in a format similar to what your drive should look like on the back.  Ignore the labels and other instructions as they likely do not correspond to the make or model you are receiving.
[IMG]http://www.techarp.com/review/Western_Digital/Scorpio_320GB/jumpers.jpg[/IMG]

---

### Post by catchagato on 2008-08-14
Will there be any noticable difference when I remove the jumper and then run my laptop, or is the difference so small that it will help but not that much?

---

### Post by KWM987 on 2008-08-14
> **catchagato said:**
> Will there be any noticable difference when I remove the jumper and then run my laptop, or is the difference so small that it will help but not that much?

I found the difference to be noticeable, boot up is much quicker, and the system seems a little more responsive.  But for most things I doubt you will see any difference in the way it behaves in everyday tasks.

The change merely doubles the theoretical bandwidth of the hardrive's connection to the system, while this is an large difference mathematically, the difference to most applications cannot be seen unless the activity on the drive has reached near its limit where the added bandwidth can be put to use. (Example: if the original bandwidth is say 10 operations, and you are using only 1 operation, you will not see a difference in performance even if your bandwidth is 20 operations; but if you are using 11 operations, you would be seeing a performance penalty on your original 10 bandwidth drive, whereas the drive with a measure of 20 bandwidth would not have this problem) The difference is thus only really applicable in heavy drive use situations-- though many desktop users can see these situations using applications that make use of large files and large operations, but for regular usage there is no real difference.

Even though on average it is a small or negligible performance gain, I would still recommend using it if it's available, since the there is no real risk involved, and plus if you get enough small gains you'll eventually have a large one.

As I said before, you should still check the specifications of the replacement drive to see if this change is applicable, since if it isn't there is nothing to be concerned with.

---

### Post by wenuswilson on 2008-08-14
> **KWM987 said:**
> I found the difference to be noticeable, boot up is much quicker, and the system seems a little more responsive.  But for most things I doubt you will see any difference in the way it behaves in everyday tasks.

The change merely doubles the theoretical bandwidth of the hardrive's connection to the system, while this is an large difference mathematically, the difference to most applications cannot be seen unless the activity on the drive has reached near its limit where the added bandwidth can be put to use. (Example: if the original bandwidth is say 10 operations, and you are using only 1 operation, you will not see a difference in performance even if your bandwidth is 20 operations; but if you are using 11 operations, you would be seeing a performance penalty on your original 10 bandwidth drive, whereas the drive with a measure of 20 bandwidth would not have this problem) The difference is thus only really applicable in heavy drive use situations-- though many desktop users can see these situations using applications that make use of large files and large operations, but for regular usage there is no real difference.

Even though on average it is a small or negligible performance gain, I would still recommend using it if it's available, since the there is no real risk involved, and plus if you get enough small gains you'll eventually have a large one.

As I said before, you should still check the specifications of the replacement drive to see if this change is applicable, since if it isn't there is nothing to be concerned with.

I just removed the jumper, boot time was negligibly fast. Cool trick though. I used a safety pin to gently remove it.

The HDD is rated at 1.5Gb/sec. Just experimented by moving a few Gb's to different partitions, no change from the original 20Mb/sec or so. 

I am one for using multiple applications at once so this may come in very handy.

Now if only I could easily integrate to Ubuntu's 64 bit I would completely utilize my machine. But, I'm going to guess that a copy and paste of my entire OS from one partition to another would not work out in my favor.

---

