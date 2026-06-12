---
title: "Nautilus/SMB"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by jdavis on 2006-06-01
I am having a problem with Samba after upgrading to Dapper Drake.

After I upgraded to dapper my machine hung during booting for around a minute (On the "Hardware Abstraction Layer" bit) before continuing, when it finally booted it was very sluggish. A quick google showed samba was the problem and by commenting out the share I was mounting from the fstab and rebooting this fixed the boot hang and the sluggish performance.

Unfortunately this means I cannot mount samba shares in ubuntu now, I also cannot access any samba shares at all.

Nautilus gives <"smb:///" is not a valid location."> whenever I attempt access. Although strangely I can access samba shares through Konqueror and other apps, but not through nautilus?

Anyone any ideas?

thanks, Jonathan

---

### Post by justmehere on 2006-06-02
I am getting a very similar problem. I'll see what I can find out. I'm just downloading a new iso and I've got another disc so I may try a clean install on that disc and see it the problem is a result of something in my upgrade process from 5.10. I'll try to post back here if I find anything that could be helpful.

:¬}

---

### Post by Doomhammer on 2006-06-03
Not sure if it's related, but now I'm getting "Failed to start HAL!" whenever i log into GNOME... And there's also an error during boot, but because neither I nor (apparently) anyone else knows where to find the log of system boot, I don't know what it says...

Ubuntu 5.10 was (IMO) the greatest distro out there at the time, but Dapper is tuning out to be a huge buggy mess.  Maybe I'll just switch back to Gentoo, if crap like this keeps happening.

---

### Post by Doomhammer on 2006-06-03
Apparently I'm having this issue: 
[https://launchpad.net/distros/ubuntu/+source/dbus/+bug/31517](https://launchpad.net/distros/ubuntu/+source/dbus/+bug/31517)

The questinon is, how to fix it ?

---

### Post by 8oluf7 on 2006-06-03
I've updated two machines from Breezy today. The first has an Athlon 64 processor and I was using the K7 kernel (after comments that Breezy 64-bit was buggy and because some of the things I wanted to use were only available in 32-bit). This machine upgraded with only minor problems already covered on the Forum. The SMB network link to my Windows XP machine worked seamlessly. The second machine is a Dell Latitude C600 laptop that was running the generic 386 kernel. This one has the problems you describe. The icon for the shared area on the windows machine is still present, but clicking on it produces an error message. The menu indicates that it is mounted - but clicking on 'Unmount Volume' produces the information that the share is 'Not mounted'!

I re-established connection by using Places > Network Servers from the bar at the top of the screen. Click on Windows network icon, then the specific network then the other machine and the shared folder is revealed. Right click and click on 'Connect to this server'. Job done. 

So - can anyone tell me how to remove the inoperative icon and stop the boot sequence hanging on 'hald'?

---

### Post by 8oluf7 on 2006-06-03
I think I've solved my own question. I edited /etc/fstab (using sudo gedit) to remove all reference to the shared folder on another machine. The entry starts with a double slash followed by a network address//<xxx.xxx.xxx.xxx>. On my machine the text wrapped onto a second line - remove the lot. It would appear that SMB on Dapper keeps its information somewhere else. After a reboot the boot sequence didn't hang on hald and the non-working icon disappeared. Also, as far as I can tell, the responsiveness of the system has improved significantly.

**Update** Yes this is all true - but I can't now open a file on the shared drive by double-clicking as I used to. I'll have to revisit the solution in the Guide I used last time this happened - but not for a day or so, as I'm away from my machines.

---

### Post by jdavis on 2006-06-04
Take a look here, looks like more of the same:
[http://www.ubuntuforums.org/showthread.php?t=186393](http://www.ubuntuforums.org/showthread.php?t=186393)

---

### Post by aoakley on 2007-05-28
This issue appears to be solved (for me, in 6.06) by going into Synaptic Package Manager and adding the package **libgnomevfs2-extra** .

This package is included in the ubuntu-desktop final release, but if, like me, you install ubuntu package-by-package from the minimal/server distro, you may have neglected to install it. The issue may also occur during upgrade from Hoary to Dapper under certain situations.

More discussion _[here]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/41107")_.

This thread is ranking high in Google when you search for: nautilus smb "is not a valid location"

---

