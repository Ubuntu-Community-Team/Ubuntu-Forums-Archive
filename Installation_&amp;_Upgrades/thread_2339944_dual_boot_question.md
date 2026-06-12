---
title: "dual boot question"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2016-10-14
I have looked at a lot of posts but not seen this issue explained. I want to make a new windows 10 laptop dual boot and have  separate partitions in the ubuntu for / and /home ( and maybe swap). I tried this years ago but when I picked install ubuntu alongside windows you don't get the option for separate ubuntu / and /home. What is the best way to do this? I usually do something else for Ubuntu installs and have /, /home and /swap but haven't done this and still keep windows.

---

### Post by yancek on 2016-10-14
That would be a non-standard install and you would not have that option with the auto-install method, install Alongside.  You need to select the manual "Something Else" installation type to see those options.  Since windows 10 is probably using UEFI, the Ubuntu documentation on dual booting with UEFI at the site below should help.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Info on creating partitions for a dual boot is at the link below.  You need to scroll about half way down the page to see it.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2016-10-14
Some brands/models require work arounds to get Ubuntu to boot as default. And Windows may on updates keep reseting UEFI to make Windows default boot. 
Most UEFI will allow you to use UEFI's one time boot key which is a boot menu to choose the ubuntu entry.
With my UEFI, I had to turn off Secure Boot (Windows or "Other"), turn on allow USB boot, set UEFI only as USB drive boot option, turn off fast boot option(mine had setting for 3 sec delay which I used) and perhaps a few others.
I do prefer to use gparted to create partitions in advance, but you still have to use Something Else and choose(change button) each partition you want as /, /home, but it will auto find swap and install may be a bit faster as it will use swap if it exists in advance.

From my link below on installing:
 Summary UEFI install instructions:
Back up Windows, your data, and make a Windows repair flash drive.
Download and create Ubuntu 64 bit installer, flash drive or DVD.
Use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often better but not required to turn off Secure boot.
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
If Issue with install, more info needed, or terms not understood, see info & links below:

---

### Post by cmcanulty on 2016-10-14
thank you very much! I was just planning on having WIN 10 on virtual box as I only use it to research windows problems for the library, but apparently win10 won't work on virtual box at least it won't on my old laptop though it initially installed and worked OK until the big update, I hope there's a fix soon as my old laptop I upgraded to win 10 while it was free and now if I lose it I have to pay.

---

### Post by cmcanulty on 2016-10-14
thank you very much! I was just planning on having WIN 10 on virtual box as I only use it to research windows problems for the library but apparently win10 won't wok on virtual box, I hope there's a fix soon as my old laptop I upgraded to win 10 while it was free and now if I lose it I have to pay

---

