---
title: "Tried to install ubuntu 12.04 but it all ends rather abruptly"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by Maximus123 on 2012-12-22
Hello everyone. 

I am trying to install ubuntu 12.04 on my laptop. My laptop is HP compaq presario CQ56. My current operating system is Windows 7. I downloaded the .iso file from the ubuntu website and burned this image to a CD. I then booted my PC from the CD drive and all was going fine.

My computer took me through the installation process. I selected to "install ubuntu within windows 7" (Which I'm not 100% sure is the option I wanted, as I wanted to have both OS's on my laptop and select which one to boot into upon start up, but that's a separate question.). Then I hit continue and upon hitting continue a black screen came up with some white writing on it that I couldn't make much sense of and my cd tray popped open. Pressing enter got rid of this screen and the computer started normally with no ubuntu OS installed. I did this several times and the same thing happened every time. Anyone know what's happening?

I have attempted to attach a photo I took of this screen, I hope it works. 
[IMG]http://ubuntuforums.org/<a href=&quot;<a href=http://www.flickr.com/photos/74271946@N04/8298227330/&quot; target=_blank>http://www.flickr.com/photos/74271946@N04/8298227330/&quot;</a> title=&quot;20121222_193713 by zwap091, on Flickr&quot;><img src=&quot;<a href=http://farm9.staticflickr.com/8493/8298227330_0330d016e3.jpg&quot; target=_blank>http://farm9.staticflickr.com/8493/8298227330_0330d016e3.jpg&quot;</a> width=&quot;500&quot; height=&quot;375&quot; alt=&quot;20121222_193713&quot;></a>[/IMG]

---

### Post by sammiev on 2012-12-22
Hi and welcome to Ubuntu. Does the live CD work by itself? Test as many features as possible before any install. Adding Ubuntu to Windows7 is not the same as adding it along side of Windows7. I prefer along side of Windows7 and it is then referred to as a Dual boot system. :)

---

### Post by Maximus123 on 2012-12-22
> Hi and welcome to Ubuntu. Does the live CD work by itself? Test as many  features as possible before any install. Adding Ubuntu to Windows7 is  not the same as adding it along side of Windows7. I prefer along side of  Windows7 and it is then referred to as a Dual boot system. :smile:The live CD does work by itself in the sense that when I put it into the PC as I would a normal CD, the autoplay opens and gives me the option to install ubuntu.

thanks
:)

---

### Post by Maximus123 on 2012-12-22
But this just means the live CD is working. I still don't get why my laptop ejects the cd and doesn't install. Has anyone seen that screen before?

---

### Post by darkod on 2012-12-22
No, what he meant by live cd working is booting from the cd and selecting the Try Ubuntu option so you can see if it works in a live session running from the cd.

What you are doing is putting the cd in with windows already running, and it simply opens it and offers to install inside windows. That is called a wubi install, and it is only meant to be a short try. You can use it for longer, but it wasn't designed like that so you might start seeing problems.

A proper dual boot on its own partition is when you boot with the cd and install on unpartitioned space, outside windows. It needs to work on linux partitions. For that you need to have unallocated space on the disk not belonging to any ntfs partition. And the total number of partitions you have right now should be 3 or less. You can check how many partitions you have in windows Disk Management.

---

### Post by Maximus123 on 2012-12-23
Thank you all for your input so far, I think I am getting there. My apologies, I am new to linux but very keen to eventually leave windows behind so I appreciate all the help.

I see now where I was going wrong. The dialogue box that was coming up was giving me three options, one was to install within windows (which is the option I originally selected), the second was to replace windows with ubuntu (not quite ready for that) and the third was 'something else', which is the option I have now selected.
The disc tray was opening because the computer was (as I understand it) exiting the install so I could go into windows and do it from inside windows (which was the option I originally selected). 

Anyway I have now selected 'something else' option and I have attached a jpeg of the screen I have now reached. In the tutorial I have been using they did not mention this screen and I really don't want to mess up this step so could someone please tell me what I ought to do next.

thanks a lot

---

### Post by darkod on 2012-12-23
You already have four primary partitions on the disk (sda1 to sda4). That is the maximum. You can't create any more partitions right now.

You would have to delete one of them, and that will allow you to create logical (NOT primary) partitions for ubuntu (it can be more than one).

It is up to you which of the existing partitions you want to delete, plus don't forget that you also need unpartitioned space for ubuntu. For example if you delete sda4 that will allow you to create new logical partitions, but because sda4 is very small you will only have 100MB of unpartitioned space. That is too little for ubuntu.

Ideally you need about 20-25GB at least. In that space you will create a larger root (main) partition and a smaller swap partition.

---

### Post by blackbird34 on 2012-12-23
Hi Maximus123
I have almost the same computer as you, I remember my rocky start with Ubuntu on it :) (but now I love it). [Here]("http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/")'s a decent tutorial to guide you.
**_First of all_** though your attachment shows that your hard drive has four partitions on it, which is the maximum possible. The HP/Compaq people seem to always put four: two "utilities" partitions (the 2 small ones), a recovery partition (the blue one) and your main Windows partition (orange). You will need a new partition for Ubuntu to install properly in a dual boot (easily done once you get your head round it).

You will have to boot into Windows and find the windows partitioning tool in the start menu (explained [here]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")). Choose "shrink volume" as per the linked tutorial and reduce the C: partition by at least 10-20 GB. I would then suggest deleting the fourth partition, the one formatted as fat32, so that Ubuntu can be allowed to create its own partition. DO NOT delete the 16 gigabyte recovery partition as you may need it one day, you never know.

That's all, then boot off your live CD/USB again. The list of available partitions should now show some "free space" in which to create an "extended" partition for Ubuntu (a container to put your swap and root partitions in). You can then proceed normally, the rest of the install is very easy.

---

### Post by Maximus123 on 2012-12-23
Thanks blackbird34 (and everyone who has helped), that has been very clear, I will try this and let you all know how it has gone.

And thanks for the tutorial as well, much better than the one I was using.

---

### Post by blackbird34 on 2012-12-23
You're welcome.

Good luck and if you need specific help post again in the thread, plus there is also IRC @ webchat.freenode.net, channel: #ubuntu

---

### Post by sammiev on 2012-12-23
Hi Maximus123, I see a few other very good folks added to the thread and all raised great points to carry on with a install along side of windows. 20-25GB would get you started for a while and you can always increase this down the road if needed with programs from Linux. Good Luck and hope to read more from you soon. :)

---

