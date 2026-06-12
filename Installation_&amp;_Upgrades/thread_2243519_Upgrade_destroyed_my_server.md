---
title: "Upgrade destroyed my server"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-09-09
I was having a bad day yesterday then to top it off my server said there was a newer version available to upgrade. I just clicked OK and it did the upgrade and when it rebooted it keeps crashing. Is there any way to get back to what I had. Everything is still there so I can boot with a live OS and get all my files. The questions I have are these:
If I have to reload the OS what files do I need so I will have all my server settings? I am thinking Apache cofig files? Server setting? I am running with a static IP so I would need all my network stuff also? I just want to make sure I get the right ones and get them all before I reinstall if that's what I have to do.
Thanks for the help

---

### Post by kansasnoob on 2014-09-09
I'm a desktop user and know nothing about the server edition of Ubuntu but if you describe the "crashing at boot" in more detail maybe another user could help you sort things out without having to reinstall. Did the upgrade process report any errors?

---

### Post by irv on 2014-09-09
No errors reported until it rebooted. When I say crashes what it does is a couple of error messages pop up and it give me the option to report it or click OK. If I click either one another error (like the one that just pop up) comes up again and then my mouse pointer stops working. Then the screen gets a crazy color pattern and then I have no choice but to power off. I tried going into recovery from the grub but it does the same thing. Maybe it loaded the wrong video driver? I am not sure.

---

### Post by oldfred on 2014-09-09
Even though a server did you have a proprietary video driver installed? That almost always causes issues on upgrades as it does not automatically get reinstalled.

I also am only a desktop user, but this is my backup list. I use rsync as I assume I can reinstall Ubuntu from scratch in about the same time as copy system back and then just copy /home and other configuration files. With a server you do have more settings in various places for Apache and related server data.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
If hard coded IP, it will be in /etc, so back that up also.

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

      
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by irv on 2014-09-09
Thanks again Oldfred, This will help me. It may be a coupe of days before I get at it but I will have too.
The real important stuff is all in the WWW directory. but my setting was what I was looking for. Like you said the etc directory..

---

### Post by kansasnoob on 2014-09-09
I'm guessing this was a Precise (12.04) to Trusty (14.04) upgrade so probably kernel series 3.2 to 3.13 - but that's a best guess. But I'm curious if you might be able to boot an older kernel from the grub menu? Should be in advanced options I think. Or maybe grub did not upgrade properly?

If it's a graphics driver issue you might be able to boot using the "nomodeset" boot parameter using grub, see the ***Temporarily Add a Kernel Boot Parameter for Testing*** here:

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Sometimes removing the "quiet splash" and replacing it with "nomodeset" will get things working just well enough to check out the Additional drivers in a desktop version of **buntu but I don't know about the server version :redface:

---

### Post by irv on 2014-09-13
Well today is the day I started to work on my server. But all I expect to get done today is the backups. About 250 gig of files. I keep all my audio recordings on my server so they get large is size. and a lot of them. About 10 to 12 years of them. I had them backup but I want to make sure I got the latest ones plus all my setting. If I lost the complete server I also have them on another server in another location. I try to cover all bases.
I will be gone today so my system can do it's backups and hopefully I start to reset it up next week. I am also thinking about changing hardware soon, because my server is getting old. all I have is a CD drive not a DVD so I have to use the mini version to reinstall the OS. The BIOS is so old it doesn't support booting from a USB. The USB ports are still USB 1's. Very slow. But once it's on line it works great with Ubuntu as the server's OS.
This is where Ubuntu really shines.

---

