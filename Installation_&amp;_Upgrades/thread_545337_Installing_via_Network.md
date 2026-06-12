---
title: "Installing via Network"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by scawa on 2007-09-07
I am running several computers on a home network.   My main interface is a Microsoft Vista installed computer.   I have another computer on my home network with Gentoo Linux installed.

I want to replace Gentoo Linux with Ubuntu Linux on that computer, but the CD drive is fried.  Is there something out there on installing Ubuntu Linux from my Vista computer over the old Gentoo Linux system over a network.    The last article I found on your site was geared toward a Mac and was last updated in 2005.

Thank you for your help in advance.

Stephen McConnell

---

### Post by Pumalite on 2007-09-07
Network Install

For those people using a Windows machine as the source for a network install, it can be done. Hopefully below will help someone one day with this exact scenario.

1 - Use TFTP.exe to serve as a network boot DHCP (instructions at this post) - [http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)

2 - Disable IIS (temporarily) - IIS has problems with some of the file name and file structures

3 - Extract the ISO to a folder on your harddrive (approx 7.5GB of space needed)

3 - Install Apache HTTP, edit the http.conf file change the "Document Root" (line 149) to the folder on your harddrive where you extracted Ubuntu and also change line 177 to the same directory. Do not use backslashes eg. c:\ubuntu must be in the http.conf file as c:/ubuntu

4 - Around line 203 of the http.conf file add "Allow from x.x.x.x" where XXX is the IP address of the computer you are installing from. OR (but be careful) you can say "Allow from all"

5 - Check that you can access this in your browser. (depends on how you config'd your apache)

5 - Then start TFTP.exe

6 - Set the remote machine to boot from network (check in your bios settings)

7 - It should boot from network and start installing.

A couple of posts that helped me out (which may help someone else in turn one day):
-----------------------------------------------------------------------------------
[https://help.ubuntu.com/community/In...sServerNetboot](https://help.ubuntu.com/community/In...sServerNetboot)
[http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)
[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)
[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)

---

### Post by scawa on 2007-09-07
Ok, I think I understand the process.  First I need to make my Windows Vista computer be a file server.

To do this, I need a couple of things.

1) The Ubuntu ISO on the Server computer... My Vista System.
2) Apache HTTP installed and acting as a file server using the folder that Ubunto ISO is in as the "Document Root"
3) Configure the "Allow From" to my computers IP address on the network.  

QUESTION HERE:   Do I need to use some sort of network mask here for use in my local network?

4)  Dissable IIs  (Which my version of Vista is not running).

5) TFTP.exe    running.

I could not find the article you talked about, but Vista does not have TFTP on it.  But isn't TFTP a single command that is used to transfer a single file to and from the host to the target?  And is it required for this process?

I can see that if you configure through BIOS to configure the computer to boot from a remote computer that this would work, but I don't see how to configure BIOS to do this.


Thanks again for your help.

Stephen McConnell

---

### Post by Pumalite on 2007-09-07
If that didn't work, try this then:[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by scawa on 2007-09-07
Thanks!!!!!!

Inside that article was one pointing to EXACTLY what I needed...

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

I'll keep you posted on how it works.  It may be a couple of days.  But I'm looking forward to doing this.
As always the Linux community is great about helping out.


Stephen McConnell

---

### Post by Pumalite on 2007-09-07
You are welcome. Good luck with your NetBooting.

---

