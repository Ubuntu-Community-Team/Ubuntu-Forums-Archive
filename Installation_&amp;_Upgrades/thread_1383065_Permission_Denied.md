---
title: "Permission Denied"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by Phantomhive on 2010-01-16
[SIZE=3][COLOR=#ff9600][FONT=Arial][SIZE=2][COLOR=Black]An error occurred: Permission denied. 

For more information, please see the log file: c:\users\owner\appdata\local\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/SIZE][/FONT][SIZE=2]

[/SIZE][SIZE=2][COLOR=Black]I'm running Windows 7 on an HP Pavilion laptop and am trying to install Ubuntu through Wubi (9.10) but this error comes up about an hour into the installation. Any ideas?[/COLOR][/SIZE]
[/COLOR][/SIZE]

---

### Post by howefield on 2010-01-16
> **Phantomhive said:**
> please see the log file: c:\users\owner\appdata\local\temp\wubi-9.10ubuntu1-rev160.log

What does the log say ?

---

### Post by Phantomhive on 2010-01-16
01-16 19:39 DEBUG  WindowsBackend: Could not find bcd id

I noticed this in there among a bunch of other stuff...

[http://www.mediafire.com/?lhzdt4jygmg](http://www.mediafire.com/?lhzdt4jygmg)

^ Here's the log

---

### Post by phillw on 2010-01-16
> **Phantomhive said:**
> [SIZE=3][COLOR=#ff9600][FONT=Arial][SIZE=2][COLOR=Black]An error occurred: Permission denied. 

For more information, please see the log file: c:\users\owner\appdata\local\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/SIZE][/FONT][SIZE=2]

[/SIZE][SIZE=2][COLOR=Black]I'm running Windows 7 on an HP Pavilion laptop and am trying to install Ubuntu through Wubi (9.10) but this error comes up about an hour into the installation. Any ideas?[/COLOR][/SIZE]
[/COLOR][/SIZE]

Hi and welcome to the Forums,

For whatever reason, Win7 & Wubi are not playing together happily at the moment. There are frequent issues with Wubi (which has worked well for years) and Win 7 (which.....)

If you have 10GB of hard drive space free, I'd really recommend putting Ubuntu on as a dual boot system - They live side by side okay.

It's not painful to do, use the partition manager within Win 7 to make some space as per this --> [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)   You want about 10GB

Once you've got the free space, ignore the rest of that post. Reboot to Win7, make sure it is happy (it may want to do a disk check), Then pop in the LiveCD and tell it to install onto the unused area that you made for it.


Regards,

Phill.

---

### Post by Phantomhive on 2010-01-16
I've got more than 10GB free and am trying to install 30GB.

I thought Wubi installs Ubuntu to be dual booted by default?

---

### Post by howefield on 2010-01-16
> **Phantomhive said:**
> I thought Wubi installs Ubuntu to be dual booted by default?

A "real" dual boot would have Ubuntu on its own partition/disk with its own file system whereas Wubi installs Ubuntu to a file which resides within your windows file system.

One of the advantages in using Wubi is that it lets you try out Ubuntu without the scary thought of having to partition your drive.

---

### Post by Phantomhive on 2010-01-16
Yeah, but I really don't feel like spending the time doing that at the moment what with midterms coming up; don't wanna risk my computer.

So any other ideas on Wubi?

---

### Post by pastalavista on 2010-01-16
Wubi makes Ubuntu seem like a Windows game. If you don't want to spend the time, why even bother with Ubuntu at all? What do you want from Ubuntu?

---

### Post by Phantomhive on 2010-01-16
> **pastalavista said:**
> Wubi makes Ubuntu seem like a Windows game. If you don't want to spend the time, why even bother with Ubuntu at all? What do you want from Ubuntu?

Naw, it's just that I don't want to get to involved if anything goes wrong, or having to start setting up a bunch of stuff because now is midterms and I really should study. Plus I'm not sure if I have a Windows 7 disk to follow all the steps of some other sites; I have three recovery disks that came with this laptop, maybe it's on there.

From Ubuntu, I want security, more free applications, no viruses, etc etc. I also really like the GUI of it. xD

---

### Post by Phantomhive on 2010-01-17
I burned the Ubuntu folder to a disk and was trying to get the boot helper from the demo/full installation but an error comes up now too.

An error occurred:


Could not retrieve the required installation files

For more information, please see the log file... same as above.


I've turned off my user account settings thinking that would help, but still no. I may just try downloading 9.4 for now and seeing if that will work and from there upgrade to 9.10...

---

### Post by tona_107 on 2010-03-14
Anyone have any ideas on this one? I'm having the same problem.

---

### Post by only4manni on 2010-04-18
> **howefield said:**
> What does the log say ?
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'


Hello sir i'm also running the windows 7 and somewhat i think i have the same problem.Please can you help me

---

