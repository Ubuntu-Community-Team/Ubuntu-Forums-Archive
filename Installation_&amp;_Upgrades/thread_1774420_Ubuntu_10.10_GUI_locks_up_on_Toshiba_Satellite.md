---
title: "Ubuntu 10.10 GUI locks up on Toshiba Satellite"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by doswald on 2011-06-03
Hi all, 

Hope I'm posting to the correct group. 

recently I'm having a problem with an older Toshiba satellite laptop (L25-S119 - w 4GB ram) which I've been using for about a year without any issues. 
I have been running various versions of Ubuntu on the machine, but needed to do a fresh install of 10.10 yesterday (it was easier for me to re-image the hard disk - than to clean it all up). Historically I have had good results with both 10.04, 10.10, and 11.04 . 

The problems began during yesterdays new 10.10 install... Basically what I'm seeing is that the graphical interface to the machine (gnome-session) is completely freezing up on me, yet the machine is still operable. I can ssh into the box and the command line screens are working as one would expect from a normally operational machine. 

A bit more detail on the freezing of the GUI. The trouble is the freezing of the screen occurs randomly at different times and with different results. Here are some examples of what I see... 

- the system has automatic login and the login process will frequently stop with the system giving me the purple default desktop with no introductory sound no menu bars, messages or windows &#8211; usually the mouse works but right clicks on the desktop produce nothing.
- the system will auto-logon and have a completely ready GUI for me to use for some random amount of time (5-30 minutes) and then lock up on me... the clock will stop updating, windows can not be resized, minimized or closed - BUT the mouse is functional. Alt+tab will not cycle through open applications such as VirtualBox sessions... Very rude scene as those test machines are behind the NAT and can not be shutdown remotely.
- however the cntl+alt+F1 key does work and I can do things like apt-get install openssh-server to test if the system is in fact still operational, and that I can ssh into it. (that all works well). 
- doing things like killing the gnome-session will have the desktop environment restarting, but I have yet to actually get the GUI to come all the way back up. I have had to reboot several times in order to get an operational GUI again - and then its just a matter of it eventually locking up a again ... 
- I see this issue with the base installs from CDROM, and after upgrading, initially I thought the upgrade introduced this problem, but it occurs shortly after a fresh install. 

This is about as far as I've gotten in identifying the problem with the machine - and I am reaching out to the forum for some ideas as to what to look for. 

Some other things I've done - several months ago I had the machine open up and cleaned thoroughly as the dust was so heavy the machine was actually getting very hot and shutting down due to heat issues. At one point I thought I was smelling something burning. After physically cleaning out the machine I ran the machine until yesterday without any issues. 

Ive done several installations of 10.10, 10.04, and 11.04 from multiple CD-Roms, I know there are no issues with them. (and tested them on other machines - with no issues)

I have not tested other copies of Linux (RH or CentOS) although I might try a Centos image as I have some Tivoli code I need to test. I have not tested windows on the machine as that would be ... yucky and mostly pointless even if it did work out well. 

Is there some way for me to have a console open in screen F1 where I could do a tail -f on some file to observe what might be going on ?

Any idea on what I could look for next? 
 
Thanks in advance - Dave.

---

