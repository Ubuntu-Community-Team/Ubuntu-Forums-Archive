---
title: "update-manager-core 7.04 install hang"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by RadarListener on 2007-06-13
I am not sure whether or not update-manager-core should take ten minutes to install, so I'm posting here.

I have tried installing 7.04-server over 6.06-server due to some problems we were having where it wasn't detecting packages. The original 6.06 install worked fine and I was able to get into installing the packages that I wanted, but found that some packages (mainly nginx) were not able to be installed!

For the install for 7.04-server: When it gets to "selecting and installing programs" (I think that's what it's called), it hangs on update-manager-core. I've left it there for around 10 minutes now and it hasn't done anything.

Also this person is experiencing a same problem (but I am not trying to install LAMP)

[http://ubuntuforums.org/showthread.php?t=459909](http://ubuntuforums.org/showthread.php?t=459909)

I am installing this on a NEC VERSA M400 laptop.

---

### Post by RadarListener on 2007-06-13
I have just tried installing this on a completely different box and it hangs on the same spot, 85% @ update-manager-core.

I am going to leave it on overnight as I feel I am not being patient enough with the installs. 6.06 didn't take that long so I'm automatically assuming 7.04 shouldn't take that long either.

---

### Post by RadarListener on 2007-06-13
I left it overnight and around 20 minutes after it popped open the cd-drive and completed the installation.

---

### Post by buddykaru on 2007-06-27
I had the same issue with both Ubuntu 7.04 Server and Alternate Installation CD. When it hangs at 85%; using Ctrl + Alter + F4 (I think) you can get the installation log in tty4. In my case it was a network timeout with APT. 

So I opened up tty2 (ctrl+alt+f2); ps | grep -i apt; got the PID of 'apt-get update'  and killed it (kill PID) and the installation continued successfully. 

Hope this will help somebody out there.

---

### Post by jms1024 on 2007-06-28
how get graphical interface on 7.04 server? 

--------------------------------------------------------------------------------

I had some trouble installing 7.04 server on a Dell PowerEdge 1850. It kept getting stuck (or taking a VERY long time) after the point in the software install where it said "Installed update-manager-core".

I read this post:
[http://ubuntuforums.org/showthread.p...e-manager-core](http://ubuntuforums.org/showthread.p...e-manager-core)

and after trying a new CD and seeing the same "hang" I tried the Ctrl-Alt-F4, which took me to an install log. After seeing several (about 10-11) messages of:
in-target err [http://us.archive.com](http://us.archive.com) fiesty/main Packages (and "restricted Packages, and Sources) and ...archive.com fiesty_updates/main Packages etc
it finally started scrolling up the log and defaulted thru the GRUB loader and ejected the CD.

So with Ctrl-Alt-F2 (for tty2 I think) at the prompt I typed "exit" and the system rebooted.

Now I can get into 7.04, but I don't have any GUI. And all attempts to "initx" or "startx" etc just tell me to do things like "sudo apt-get install xinit" which tells me that xinit doesn't exist and try x11-common. I try that and the system says:
Media Change: please insert the disc labeled '/cdrom/' and press enter.

I do that and it when I press enter it just scrolls up asking me to do that again.

So, (phew) here's what I want to do:
1) Get to a graphical UI
2) Install an FTP server (for clients to have their own logins going to only their own drop off folders)
3) Install Webmin and create a non-admin group so others can add FTP accounts with the correct permissions for new clients.

Any and ALL help will be HIGHLY APPRECIATED.

Thanks in Advance!

Note I also posted this in the "absolute beginners" forum.

---

### Post by RadarListener on 2007-07-01
For the first one, apt-get install xserver-xorg and gnome-common, and maybe something else.

---

### Post by jms1024 on 2007-07-02
Thanks.  I finally figured out what was going on.  It was obfuscated by the fact that I could ping the update locations, but couldn't get to them.  Turns out it was a firewall issue on our network.

Once I figured that out I was able to reinstall the OS successfully and then the other apps I needed.

Thanks!

---

### Post by sparklyprgs on 2007-09-04
> **buddykaru said:**
> I had the same issue with both Ubuntu 7.04 Server and Alternate Installation CD. When it hangs at 85%; using Ctrl + Alter + F4 (I think) you can get the installation log in tty4. In my case it was a network timeout with APT. 

So I opened up tty2 (ctrl+alt+f2); ps | grep -i apt; got the PID of 'apt-get update'  and killed it (kill PID) and the installation continued successfully. 

Hope this will help somebody out there.

Certainly did!  When I switched to install log it was obvious - linux was trying to get to the web but the machine wasn't on a network yet!

killed the apt process and bam - server install finished and up it booted.

thanks buddykaru

(plus useful to know keys for future installs)

---

### Post by gtdaqua on 2007-09-06
Same happened to me - figured it must be trying to reach the internet. Connected the correct NIC and bam - installation was complete. 

Thanks to this thread!

---

### Post by honeydew on 2007-09-19
> **buddykaru said:**
> I had the same issue with both Ubuntu 7.04 Server and Alternate Installation CD. When it hangs at 85%; using Ctrl + Alter + F4 (I think) you can get the installation log in tty4. In my case it was a network timeout with APT. 

So I opened up tty2 (ctrl+alt+f2); ps | grep -i apt; got the PID of 'apt-get update'  and killed it (kill PID) and the installation continued successfully. 

Hope this will help somebody out there.


nice.. helped me.. I was having the same issue and this worked like a charm.  

big ups!

---

