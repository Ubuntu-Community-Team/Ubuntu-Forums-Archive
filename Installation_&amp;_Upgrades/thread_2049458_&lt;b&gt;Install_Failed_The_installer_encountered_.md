---
title: "&lt;b&gt;Install Failed: The installer encountered an unrecoverable error.,&lt;/b&gt;"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-28
Hi Members,

I tried to install Ubuntu numerous times and continue to receive an error message that says, 

&#8220;The installer encountered an unrecoverable error. A desktop session  will now be run so you may investigate the problem or try installing  again.&#8221;  -end-

 I&#8217;m at my wits end as I have no idea what to do next to get Ubuntu  successfully installed. I did look at the forums and many people have  the same problem but I see no basic fix. I tested my hard drive for  errors &#8211; tested OK, I disabled my on-board RAID (read that in a forum  post) and reduced the swap file to 2000MB which Ubuntu says&#8230;

 &#8220;On 32-bit architectures (i386, m68k, 32-bit SPARC, and PowerPC), the maximum size of a swap partition is 2GB.&#8221; -end-
 source:[https://help.ubuntu.com/12.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/12.04/installation-guide/i386/apcs03.html)

 No matter what I do, I keep receiving the same error message.  I even  burned numerous copies of the install ISO image. It was suggested that  burning the iso image at the slowest speed would reduce errors.  Unfortunately I continue to receive the same error message no matter what CD I use to install.

During another install attempt, I waited for the install CD to copy all files before clicking "continue" on the final window that asked me if I wanted to, "select any accounts I would like to import". No fix. I received the same error message.

Then I removed my windows hard drive completely. Set the 80 gig Ubuntu drive as "master" and ran a clean install and received the same error message.

What is strange is that the same "Ubuntu Live CD" that allows you to test drive Ubuntu (that contains the installer as well) worked fine.

Any suggestions would be kindly appreciated.

Thank you.

---

### Post by critin on 2012-08-28
Unless I'm missing it somewhere, you don't say which version you're trying to install.  It isn't 12.10 is it?
It really sounds like it is.  
What is the size of the install partition?

The link says:

>  However, if your partition is larger than around 6GB, choose ext3 as your partition
 I've not ever seen that recommendation before.  Most everything goes on ext4, though I know ext3 is used sometimes.  

That article may be out of date according to the size of hard drives/partitions it mentions.

That's not the issue here though.

---

### Post by WindsOfChange on 2012-08-28
Hi Critin,

**[COLOR=Blue]>>>you don't say which version you're trying to install.  [/COLOR]**

Sorry about that. I am trying to install Ubuntu version 12.04 (The latest version as downloaded from Ubuntu's web site).

**[COLOR=Blue]>>>What is the size of the install partition?[/COLOR]**

I created four partitions on my 80 gig drive. This 80 gig drive was erased and tested ok by western digital's drive utility software prior to Ubuntu installation. All space on this drive is devoted 100% to Ubuntu. The partitions created are:

1st partition: /boot: 500MB
2nd partition:  /: 15,000MB (15 gigs)
3rd partition:  /home: 50,000MB (50 gis)
4th partition:  Swap file: 2000MB (2 gigs)

Free space remaining about 12,500MB (12.5 gigs)

I have a dual processor pentium III (2GHz) system and 1 gig of DDR RAM. Total RAM available to install is 4 gigs.  I am running windows 2000 on my "master" drive (total space: 40 gig drive). I am trying to Install Ubuntu on an 80 gig drive set to "slave".

The BIOS recognizes both hard drives correctly. I can pretty much install anything on this system and its been rock solid for years. 

I am also running a matrox G450 dual head video card. During the install of Ubuntu, both screens are displaying the install screen (as if I have two seperate computers). In other words, the other screen is not acting like an extended desktop like it usual is under windows 2000. Not a big deal. I did not expect Ubuntu to run two screens using the Matrox G450. I haven't tried turning off the other screen display in the Matrox properties box during "another" Ubuntu install as I figured that was not the issue. I just wanted to mention that fact. 

[COLOR=Blue]**>>>The link says:**

[/COLOR]       [COLOR=Blue]Quote:[/COLOR]
                   [COLOR=Blue]                               However, if your partition is larger than around 6GB, choose ext3 as your partition                      [/COLOR]           
[COLOR=Blue]I've not ever seen that recommendation before.  Most everything goes on ext4, though I know ext3 is used sometimes.  

That article may be out of date according to the size of hard drives/partitions it mentions.[/COLOR] [COLOR=Blue]

That's not the issue here though.      [/COLOR] -end-

Yes I did read that as well and assumed the same thing. I am using Ext4 File system. By the way, the file system on my windows 2000 drive is NTFS.

I used this excellent web site as a "How to" for my installation.

Page 1 : 

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/comment-page-1/#comment-13440](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/comment-page-1/#comment-13440)

Page 2

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)

Thank you. Any further suggestions would be appreciated very much.

---

