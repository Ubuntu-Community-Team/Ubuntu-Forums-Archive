---
title: "Guide to install Ubuntu 9.04, 10.04, 10.10 with NVIDIA 310M Graphics"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Aitaix on 2010-10-11
I've seen a few threads about this. I too had this problem with a black  screen with Nvidia 310M graphics card. I am using a Dell Latitude E9510  to show you how I installed 9.04 | 10.04 LTS | 10.10



1) Boot from a Ubuntu 9.04 CD/DVD
2) Push ESC when the language screen comes up
3) Push F6 for other options
4) Then ESC, a line of text is shown at the bottom of the screen. 
The last few words say "quiet slash --"  delete all of that and instead put in "nomodeset" 
so it should read "... ... ...initrd=/casper/initrd.lz nomodeset
 
5) Push F4 and select safe graphics mode
6) I chose to run Ubuntu live
7) If Ubuntu boots up. I then installed it off the desktop...why, I don't know. I just did.
Install ubuntu as normal....

9) When your computer restarts. At the grub2 menu push 'e' before the timer runs out. Then 'Esc' 

10) You should be back at the Grub2 menu. Use the arrow keys and highlight 2.6.31-14-generic and push 'e'

11) What you now want to look for is 'ro quiet splash'

12) edit this again by deleting 'quiet splash' and typing in 'nomodeset'
13) push ctrl+X to boot
14) **HOPEFULLY** you were able to boot to Ubuntu desktop with crappy graphics. Now if you have another computer and a flash drive use it to put the drivers on because this is a lot easier then using your laptop without graphics drivers installed anyways....
Download the drivers [here]("http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html") and put them on your desktop or somewhere easy to get to.

15) Once they are on your desktop. Open up terminal and you want to stop X server from running. You can do this by "sudo /etc/init.d/gdm stop" and then enter your password. 

You should see a window pop that says "Please wait a minute for x server to stop" click okay as you will wait awhile....

16) Now login using your username and password....hopefully you're now at a shell

17) enter 'cd Desktop'

18) now 'sudo sh NV{tab to complete} and then your password


19) If you are at the next step. This should be straight forward.

20) I didn't install the 32 bit compatibility OpenGL drivers.....because I'm cool
21) Yes you would like the nvidia-xconfig utility to automatically update your bla bla bla

22) You're now at a command prompt....well restart your computer and read steps 10-13 

23) HOPEFULLY if this guide works...you should have Ubuntu running with stunning graphics....


24) If you want to put 10.04 LTS or 10.10 on it's your choice. 
I haven't had any success using the "Hardware Drivers" that are not activated so I don't recommend using them.

I used the update manager to update to 10.04 LTS

After restarting....at the grub menu remember to add in "nomodeset"

If you get to a Ubuntu 10.04 desktop...follow step 15 and onward again to get your graphics back and same thing for 10.10..

umm search Ubuntu Forums for away to edit Grub2 to insert "nomodeset" permanently so you don't have to keep adding it.


This worked for me. Hopefully it works for you. I am no means a guru with linux....so if I messed up your computer. I probably...have no idea how to help you. Sooo use at own risk! :guitar:

---

### Post by mörgæs on 2010-10-12
Thanks for the guide. Does this mean that one can not install 10.10 directly?

---

### Post by Aitaix on 2010-10-13
My guess is that you'd have to install the drivers off of a flash drive, which I don't know is possible from a command prompt.


I'm so curious to see if it would work now.....hmm I might just try it!

---

### Post by nono_123 on 2010-10-13
thanks man
will try that on my sony vaio laptop ans post the results

---

### Post by mörgæs on 2010-10-13
If it is possible to install directly, by any means go for it. Generally a double upgrade does not help to make a system more stable. 

If you use USB, 10.10 seems to work best when created with Unetbootin.

Looking forward to hearing the results!

---

### Post by Aitaix on 2010-10-24
just want to say you can ignore that guide. 

Install 10.10 from USB/CDROM/DVDROM as normal.

just make sure you put in "nomodeset"

and it should work fine!

All is good here :)

---

