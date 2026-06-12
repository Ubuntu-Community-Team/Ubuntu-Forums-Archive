---
title: "Installing 6.10 on MS VPC 2004/2007"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Tinaja on 2006-11-06
I'm trying to test Ubuntu by installing in a virtual PC instance.  I would use the VMware player if you had an appliance created already, but VPC is free.

So I started with these instructions:  [https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004) 

When I launch Ubuntu in either start/install or start in safe mode, the screen is unreadable - looks like a bad frequency setting.  I can see the mouse, and I can see the outlines of dropdowns, but it is impossible to navigate.  I can't even get the OS installed to the point of making the changes to xfree86.  The same behavior is exhibited in both VPC 2004 and 2007 (beta).

Please create a VMware appliance for the current release of Ubuntu, or help me solve this problem.

Thanks in advance....

---

### Post by Madstone on 2006-11-06
I think what you are looking for is specified in section 4b in the same document you referenced earlier.  If you have the document open look for the section headline "Be prepared to hit the Esc key when the GRUB loader appears" the notes below that should help you get going.  

If your able to get past the video issue then you will also find out the sound doesn't work either but add the following line to the /etc/modules file and reload the modules or restart the VPC

snd-sb16

Currently I have Edgy running fine in VPC 2004 for testing.  Let us know if these steps work for you.

---

### Post by Tinaja on 2006-11-07
The problem is that the instructions tell me to make changes to a file, and until I have ubuntu installed the OS is running off an ISO image.  Am I missing something here?](*,)

---

### Post by Tinaja on 2006-11-07
I reread the instructions, and tried to follow 4b, but when I do ctrl-alt-F1 I end up with a screen full of screwed graphics instead of a command line interface.

You folks should really consider spending a few $$'s to buy VMware and create an official vmware appliance so people can test this software more easily.  

I'm an IT consultant for several $20-100M companies by trade.  I've been a reasonably staunch Microsoft supporter for years because, for all of its faults, Windows *works*.  They have torqued me off enough in the past few months, though, that I would like to find an alternative.  I had hoped Ubuntu might be a  solution but once again, Linux is clearly too brittle to be used in a real-world environment.  Oh, I'm sure it's my fault - I don't have exactly the right hardware to support Ubuntu, but neither do my clients.

Very frustrating.

---

### Post by Madstone on 2006-11-08
If you are looking for a VMWare appliance there is one available for Dapper Drake (Edgy Eft is not available yet) here:
[http://www.vmware.com/vmtn/appliances/directory/ubuntu.html](http://www.vmware.com/vmtn/appliances/directory/ubuntu.html)

If you would really like to get this working with MS VPC then read on...
Everyone likes a challenge right?...:) 

Load up VPC and select the Ubuntu ISO and allow it to load
When you get to the screen that gives the options
"Start or Install Ubuntu"
"Start Ubuntu in Safe Graphics Mode"

Select F4 from the list below and select 1024x768 16bit color
(Be sure to select 16 bit color here or this may not work)

Then select "Start or Install Ubuntu"
Allow this to load until you notice the screwed up cursor and what appears to be a dialog box then execute Ctrl-Alt-F1
From this point you should be at a command line similiar to:
ubuntu@ubuntu:~$

At this point you should pick up section 4b in that document you mentioned and do the following:
ubuntu@ubuntu:~$sudo dpkg-reconfigure xserver-xorg

Be patient after executing that command it may take some time depending on the performance of your hardware.

Then just finish the steps in 4b and don't forget to change the color depth to 16bit here also and you should be good to go.

Let us know the results.

---

