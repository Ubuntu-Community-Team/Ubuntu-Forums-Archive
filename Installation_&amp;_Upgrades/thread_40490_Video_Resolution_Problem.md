---
title: "Video Resolution Problem"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by Larrymocurly on 2005-06-09
I'm reposting this from the Beginner Forum since I didn't get any response!  Hopefully, I will have better luck here!

I installed Ubuntu today on a PC using Microsoft's Virtual Machine. Everything went well until the GUI came up in 1600x800. Neither the monitor nor the video card is capable of that resolution. I can barely make out about every fourth word. Not being familiar with Linux nor Ubuntu, I would never be able to figure out where to click on this distorted page to get to a place I could change the resolution. I went so far as to reinstall in order to pick the right resolution but even though I picked 1280x1024 it still came up 1600x800. Any help, tips, hints would be greatly appreciated.  ](*,)

---

### Post by Joeb on 2005-06-09
In Microsoft's Virtual Machine, can you set what the maximum resolution of a session should be?  It sounds like during the install when Ubuntu queries the system to determing the resolution, the VM is returning the higher value.  If you could set it lower and then reinstall it should take care of it.

Otherwise, you need to edit your X configuration file to set the resolution manually.  You should be able to get to the console by hitting ctrl-alt-F1.

---

### Post by Larrymocurly on 2005-06-09
Thanks Joeb for your reply.  I had set the display under Microsoft Virtual PC to "Use guest operating system screen resolution."  But I still come up in 1600x800.  The cntl alt f1 did get me to a command prompt but being a newbie to Linux, I have no idea how to get to the x configuation info and where to change it.

---

### Post by Joeb on 2005-06-09
[QUOTE=Larrymocurly]Thanks Joeb for your reply.  I had set the display under Microsoft Virtual PC to "Use guest operating system screen resolution."  But I still come up in 1600x800.  The cntl alt f1 did get me to a command prompt but being a newbie to Linux, I have no idea how to get to the x configuation info and where to change it.[/QUOTE]

I think, because of the way Virtual PC works and Linux works, that when Linux goes to test for the resolution and asks what's the highest resolution you support, Virtual PC responds back with 1600x800 (which is true, even though your hardware doesn't actually support that, VPC does) and whamo, you have your problem.

You could try setting it to a specific resolution in Virtual PC or editing the configuration file.  I won't be a linux box until tonight :(  so I can't tell you what to change in the configuration file until then.  Since the x configuration can be sensitive to typos, I don't want to tell you what I "think" needs to be changed vs. what actually needs to be changed.

So, if someone hasn't responded on this thread with how to change it, by tonight when I get home, I'll post again.

---

### Post by Larrymocurly on 2005-06-09
Again, Joeb,  thanks for sticking with me.  The resolution I'm using on the PC is 1280x1024, so when I specified to Virtual PC to "use the guest operating system resolution," I thought Linux would come up 1280x1024.  Something I just thought about, if I do find out where to change the resolution in Linux and change it, will a reboot reset it to the 1600x800?  :???:

---

### Post by Joeb on 2005-06-09
[QUOTE=Larrymocurly]Again, Joeb,  thanks for sticking with me.  The resolution I'm using on the PC is 1280x1024, so when I specified to Virtual PC to "use the guest operating system resolution," I thought Linux would come up 1280x1024.  Something I just thought about, if I do find out where to change the resolution in Linux and change it, will a reboot reset it to the 1600x800?  :???:[/QUOTE]


Ok, you are going to have to edit the file at /etc/X11/xorg.conf and you will need to do it as root.   First, you want to make a backup of it, so enter 
     sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak


 Next, you will want to type sudo nano /etc/X11/xorg.conf  to start the nano editor with root permissions and edit the xorg.conf file.

You will want to page down until you get to the section that says "Screen".  In that section is a line that says DefaultDepth.  This is the colordepth and relates to how many bits are used for color depth.

Anyway, you will want to page down throught the various "Display" subsections until you find one that matches your colordepth (each section has a item called depth).

You will want to edit the "Mode" line in that subsection and remove the resolutions that aren't applicable for your monitor/video card.  

When you are done making changes, save and exit the editor.  You will need to restart X for the changes to take place.  The easiest way to do that is to enter ctrl-alt-f7 which will take you back to your messed up X session and then enter ctrl-alt-backspace which will restart the X server.

Hopefully, that will fix your problem.

---

### Post by Larrymocurly on 2005-06-10
Joeb, the plot keeps getting thicker!!  I want bore with you with all of the mistakes I made following your instructions. (mistyping, capital letters, etc.)  

The problem seems to be that a S3 driver is loaded.  I have an ATI video card.  All color depths had 1280x1024 as they should but the driver is wrong.  Here is what I had:
Section      "Device"
                 "Identifier" "S3 INC. 86c 764/765  [Trio32/64/64V+]
                 "Device"    "S3"

Another interesting thing was when I het cntl alt F7 to go back, the display was stretched horizontal off the screen, but readable unlike when I started.  ](*,)

---

### Post by Joeb on 2005-06-10
I'm not at a linux computer right now, but if you go back into the xorg.conf file, at the top in all of the comments are some lines about what to install/run to re-configure your video.  You might try those steps.  Also, incase the steps don't specify it, you need to use sudo in front of the commands listed.

---

### Post by Larrymocurly on 2005-06-11
Hi Joeb,
I look at the top of the file but I didn't see anything about how to change the video driver.  Wow, you know this is just an installation problem we are dealing with.  I wonder if this is all worth it. :smile:

---

### Post by Joeb on 2005-06-11
Mine has listed at the top the following directions to automatically rebuild the xorg.conf:

cp /etc/X11/xorg.con /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg



I believe the first two lines are to keep what you have, just incase something screws up (assuming yours was already working, which it's not).  The last line is the one does the reconfiguring.

---

### Post by afonic on 2005-06-11
[QUOTE=Larrymocurly]Hi Joeb,
I look at the top of the file but I didn't see anything about how to change the video driver.  Wow, you know this is just an installation problem we are dealing with.  I wonder if this is all worth it. :smile:[/QUOTE]
 I really suggest using VMware Workstation 5.

It officially supports linux OS and there are drivers for it in Ubuntu, so everything will run 100% smoothly. (I am using Ubuntu inside VMware for Linux on a SuSE system -don't ask why), and I guess the windows version should run flawlessly too.

---

### Post by Larrymocurly on 2005-06-12
Your right the text you quoted was on mine too.  I just had no idea what it meant!  I tried to reconfigure but the system is not liking something(s)!  One of the things is the bus identifier.  I have no idea how to figure that out.  I google'd and found a treatise on reconfiguring the video card and it said to run "XFree86 -scanpci", but Ubuntu said there was no such command..

---

### Post by Larrymocurly on 2005-06-12
[QUOTE=afonic]I really suggest using VMware Workstation 5.

It officially supports linux OS and there are drivers for it in Ubuntu, so everything will run 100% smoothly. (I am using Ubuntu inside VMware for Linux on a SuSE system -don't ask why), and I guess the windows version should run flawlessly too.[/QUOTE]
 I think I messed up!  I thought I wa replying to Joeb but I just realized I had another post which I hadn't seen from afonic.  I have no idea what VMware Workstation 5 is. If it's virtual machine software, I already have Microsoft Virtual PC and since I'm running Windows that seems to be a good fit.

---

### Post by afonic on 2005-06-12
Yes it is a virtual machine software which I suggest you use insted of Microsoft Virtual PC.

**Microsoft DOES NOT support linux as a guest OS.**

Users have made it work, but it's much better to try the VMware as it most distros (Ubuntu included) have drivers for it included.

---

### Post by Larrymocurly on 2005-06-12
Thanks for the suggestion of the other VM.  I knew Microsoft did not officially support Linux with Virtual PC but I have several friends that have successully installed Linux. (Not Ubuntu)  Microsoft's VM is the only VM I have so I was trying to work with what I have.  I'm experimenting with Linux (trying to learn something new) and I do not want to mess up my Windows software which I know Virtual PC won't.  May be if I stick with it long enough I might learn something!:smile:

Of course what I might learn is not to use Virtual PC!

---

