---
title: "How I got my Hardy Nvidia problems sorted"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by simbahome on 2008-05-06
Hi,

my Hardy upgrade went well, and all the trouble started when I wanted to enable the cool new visual effects. The error message was that the Nvidia drivers were not installed. No problem I thought, lets go to System - Administration - Hardware Drivers and enable them there. 
That is when I was dumped in driver hell!!

I only had 800*600 vesa, and it killed my keyboard layout. In trying to fix the video problem, I killed my sound as well. 

With lots of work, everything is working now thanks to the following kind souls who posted the help.

What I did to get it sorted:
1) Found out that I was using the wrong kernel. I wanted 2.6.24-16-generic, which was also enabled in my synaptic, but grub menu.lst had  2.6.24-16-rt in first place. So I needed to edit the menu.lst to boot the right kernel.

2) To fix the sound, i used the following guide.
[http://ubuntuforums.org/showthread.php?t=769850](http://ubuntuforums.org/showthread.php?t=769850) message #6

3) To fix the keyboard was as simple as going System-Preferences-Keyboard and clicking on the Layouts tab and filling in the details.

4) To fix the Nvidia was a bit more tricky. My Geforce 6200 now works due to the following :
[http://ubuntuforums.org/showthread.php?t=779655](http://ubuntuforums.org/showthread.php?t=779655) message #7.
It executed as expected, without any errors, but it didnt do anything. (apparently). then i did message # 9 , which also didnt do anything. I then redid message #7 and guess what, it worked!!! (dont ask me why) So a big Thank You to PmDematagoda 
[http://ubuntuforums.org/images/smilies/eusa_clap.gif](http://ubuntuforums.org/images/smilies/eusa_clap.gif)

---

