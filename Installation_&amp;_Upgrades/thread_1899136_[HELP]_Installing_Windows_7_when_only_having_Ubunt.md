---
title: "[HELP] Installing Windows 7 when only having Ubuntu 11.10"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by qjrmakstp on 2011-12-22
I need help installing Windows 7 on Ubuntu.

I'm on Ubuntu 11.10 right now. I have an iso image file of Windows 7 installation.
However when I mount the iso file, there is only a file named readme.txt in the mounted iso folder, and nothing else.

I've been searching around many ways to get this working.

1.  I tried Nautilus scripts and Kernel Loop. They didn't work. (*There is  possibility that I might have done them in wrong ways. If that's the  case, please explain the procedures to me in plain English rather than  broken programmer's slack language, and using proper grammar!) -  Although, I'm in an urgent situation and I'm having some personal  problems that are stressing me out at the moment, so I'm not paying  attention to so much on my writing right now. Sorry...
Anyway, I  succeeded writing the scripts for mounting and unmounting, but I got  stuck at the point where I had to enter the password for '/bin/echo 'got  r00t'' because neither 'Ubuntu' or my personal account password worked.  When I enter either of the passwords, an error message comes up saying  "ISO Mounter; Cannot mount /home/(username)/Desktop/Windows7.iso!"  (which is the directory where my iso file is).
And I wasn't completely sure how to approach on Kernel Loop. (Please help.)

2.  I don't have any USB sticks (I have one that's not big enough for the  iso file to go in), except I have one 640GB Portable/External Hard  Drive. However, using another computer in my household, I downloaded  Windows 7 USB/CD Download Tool(s) and tried to burn (or make a bootable  USB Hard Drive) the iso file onto the portable hard drive, but Windows 7  USB/CD Download Tool wouldn't detect any compatible USB drives even  though my hard drive is clearly connected to the computer. (Please help  with this issue, too, Windows users!)

3. I tried downloading  other useful Ubuntu iso-related softwares such as VirtualBox, but I am  currently having the problem where any downloading or updating wouldn't  work. The error message is: "Requires installation of untrusted  packages; The action would require the installation of packages from  unauthenticated sources."
I haven't tried any scripts to fix that  problem yet. Working with Terminal is too much for me... But if that'd  be the only case, I'll put up with it.

4. I don't own any DVD-R  nor CD that I can write/burn this iso file on. (As stated above, I only  have a 640-GB portable hard drive) I recently formatted that 640GB hard  drive (quick format because actual formatting took too long to wait...),  and it is NTFS, as far as I know.

Besides that... this is all my  fault. Shouldn't have switched to Ubuntu from Windows 7. My laptop  (that I'm using AND on Ubuntu at the moment, trying to switch back to  Windows 7 but not working) primarily had Windows 7 Home Premium  installed on. (It's a Hewlett Packard (HP))
I once switched to Ubuntu  11.10, and I couldn't get used to it. I've been a Windows user for more  than 10 years. I like Ubuntu Unity because it looks like Mac, but it  doesn't really do everything that Windows can. I trusted the 'media  talk' too early.

Please help!
How can I install Windows 7 (with the Windows 7 iso file) when I'm on Ubuntu, in the situation like this?
I want my Windows back.
A step-by-step instruction would be nice!
Ask me any questions in order to approach this problem in better ways, though.
Thank you.

-------------

I also posted this same post on another forum site.

[http://ubuntugeek.com/forum/index.php/topic,4552.msg6039.html#msg6039](http://ubuntugeek.com/forum/index.php/topic,4552.msg6039.html#msg6039)

---

### Post by Mark Phelps on 2011-12-23
You can NOT install Win7 from an ISO -- that simply will not work.

You have to expand the contents of the ISO -- either to a DVD or to a USB stick -- and install from that.

If you need help creating bootable media for Win7, suggest you check out the following section in the Win7 forums (sevenforums.com):

[=Installation%20and%20Setup"]http://www.sevenforums.com/tutorials/?filter[3]=Installation%20and%20Setup]("http://www.sevenforums.com/tutorials/?filter[3)

---

