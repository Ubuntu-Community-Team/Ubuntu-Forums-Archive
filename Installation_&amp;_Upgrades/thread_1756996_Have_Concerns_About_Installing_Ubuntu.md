---
title: "Have Concerns About Installing Ubuntu"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by boxfresh on 2011-05-12
So I am really interested in installing Ubuntu 11.4 but have a few questions/concerns. The biggest one is that I am an amateur photographer and I use Adobe Photoshop cs5 and Adobe Bridge frequently. I did some searching and I see that Wine supports both of these programs, but the steps to make it work make me nervous. I am not a complete noob when it comes to computers and I can follow most instructions, but I am doubting myself. If I do get it to run, will it run as seamless as it does on my Windows 7? 

Another question, if for whatever reason I choose to go back to Windows 7, am I able to without buying it?

I think I may do the dual boot option at first to try out Ubuntu, I have seen a few different way of doing this. Any chance anyone can point me in the right direction? I will back my media up onto my external harddrive, but am still worried about my cs5 torrent.

Thanks for the help. I appreciate it.

Here are the links to the Wine website showing the steps to make Bridge and Photoshop work.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6813](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6813)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)

edit: I just found this really good video. Still doesnt answer all my questions though. [http://www.youtube.com/watch?v=u3XM5Q-G8Pw](http://www.youtube.com/watch?v=u3XM5Q-G8Pw)

---

### Post by tommcd on 2011-05-13
If you need Photoshop, then I would definitely dual boot with Windows 7. It is possible to get many Windows programs running under Wine, but this can often be problematic. It will not hurt at all to try running Photoshop under Wine in Ubuntu though.

It is easy to dual boot with Windows. See this site for tutorials on dual booting Ubuntu with Windows 7: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
The safest way to dual boot with Windows 7 is to use Windows own partitioning tool to make room for Ubuntu. The tutorial I linked to illustrates using Ubuntu's partitioning tool GParted to make room for Ubuntu. Be sure to defragment Windows before shrinking Windows to make room for Ubuntu.
There is a linux photo editing tool called *Gimp* that you can install on Ubuntu. Gimp is not as versatile as Photoshop from what I have read though.

Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by Hedgehog1 on 2011-05-13
I also use Photoshop CS5, and I dual boot to get the GPU speed enhancements in Windows 7, but then use Ubuntu for most everything else.

The dual boot is the best way to go in your situation.

Your Windows 7 computer most likely did not come with Windows 7 install disks.  You can create a set of 2 DVDs using Windows 7 to 'restore windows'.  Most folks don't know about this - it is a good idea to create these disks even if you never choose to dual-boot with Ubuntu.

I would suggest a dual-boot installation that looks something like this (assumes 1 internal hard drive):

```
/dev/sda1 ntfs 100 meg system reserve
/dev/sda2 ntfs Windows 7 partition (called 'C:' in windows)
/dev/sda3 ntfs Common storage are to be used by both Windows and Ubuntu
/dev/sda4 extended parition
__/dev/sda5 ext4 '/' (root) partitons for Ubuntu
__/dev/sda6 ext4 '/home' partition for local Ubuntu data
__/dev/sda7 Linux Swap (size of RAM + 10%)
```

***The Hedge***

:KS

---

### Post by tommcd on 2011-05-14
> **Hedgehog1 said:**
> 
 You can create a set of 2 DVDs using Windows 7 to 'restore windows'.  Most folks don't know about this ...
I didn't know this either. How exactly do you create restore discs with Windows 7?

---

### Post by Hedgehog1 on 2011-05-14
Whenever someone drops by to setup their we windows 7 computer, I always have them run all the updates, and then create a system image and a repair CD.

[IMG]http://img402.imageshack.us/img402/8894/systemimage.png[/IMG]

On a new system, this usually fits onto two DVDs, and will allow them to reload to 'factory settings' with whatever proprietary drivers for that laptop or PC also captured in the restore image.

***The Hedge***

:KS

---

### Post by tommcd on 2011-05-14
That was a quick answer! Thanks. 
I have only limited experience with Windows 7. I did not know there was an option in the control panel to create restore discs.

---

### Post by boxfresh on 2011-05-14
Wow, thank you for the super helpful responses, and fast too! That was exactly what I was looking for. Hopefully I will get around to installing Ubuntu 11.04 within the next week, I am super excited. 

My ram is 3gb, how should I set up the partition? Should I make it 50-50 or should I give Windows slightly more, since it requires a bit more? I will most likely only be using Windows to run Photoshop/Bridge.

---

### Post by wilee-nilee on 2011-05-14
> **tommcd said:**
> That was a quick answer! Thanks. 
I have only limited experience with Windows 7. I did not know there was an option in the control panel to create restore discs.

If you have W7 pro and above you can also backup and image the OS as many times that you like.

> **boxfresh said:**
> Wow, thank you for the super helpful responses, and fast too! That was exactly what I was looking for. Hopefully I will get around to installing Ubuntu 11.04 within the next week, I am super excited. 

My ram is 3gb, how should I set up the partition? Should I make it 50-50 or should I give Windows slightly more, since it requires a bit more? I will most likely only be using Windows to run Photoshop/Bridge.

So we are presuming you know the limitations on how many partitions and partition types on a single hard drive, this is very important.

Size is up to you of the set up the partitions use your common sense or post a screen shot of the disk manager in W7.

All the instructions and links here are very good, but the partition  amount question is important, I felt it needed to be mentioned .

---

### Post by NormanFLinux on 2011-05-14
Run GIMP. It will do nearly everything Photoshop can do. Even in Windows for simple fixes, I run Picasa. Its sufficient for my work.

---

### Post by mörgæs on 2011-05-14
Agree on trying Gimp first. It is a great program, and there are lots of tutorials on Youtube.

The only advice I would add is to install 10.10, if 11.04 does not behave.

---

### Post by Hedgehog1 on 2011-05-14
> **NormanFLinux said:**
> Run GIMP. It will do nearly everything Photoshop can do. Even in Windows for simple fixes, I run Picasa. Its sufficient for my work.

GIMP does many useful things; but if you are a Photoshop Power user, it is limited in comparison.  

I use GIMP when in Ubuntu, and for things I cannot do in GIMP I turn to Photoshop.  It does reduce the number of re-boots into Windows for 'basic' graphic editing. 

GIMPs ability to do drop shadows and other effects between layers is one area where it is weak - however it's color correction and cropping it works fine.  It is well worth learning.


***The Hedge***

:KS

---

### Post by tommcd on 2011-05-15
There are a great many tutorials online about using Gimp. Depending on what you need in a photo editor, it is entirely possible that the Gimp may be all that you need in a free (as in freedom, and free as in beer) software package.
See these sites for some tutorials:
[http://meetthegimp.org/](http://meetthegimp.org/)
[http://gimp-tutorials.net/taxonomy/term/19](http://gimp-tutorials.net/taxonomy/term/19)
[http://vntutor.blogspot.com/2007/08/10-gimp-video-lessons-online.html](http://vntutor.blogspot.com/2007/08/10-gimp-video-lessons-online.html)
[http://www.techdrivein.com/2010/09/12-useful-gimp-video-tutorials-for.html](http://www.techdrivein.com/2010/09/12-useful-gimp-video-tutorials-for.html)
[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)
In case you are wondering why it is called *Gimp*, the name gimp is an acronym for GNU Image Manipulation Program. See this site for what GNU (FOSS software) is all about: [http://www.gnu.org/](http://www.gnu.org/)

---

### Post by tommcd on 2011-05-15
> **boxfresh said:**
> 
My ram is 3gb, how should I set up the partition? Should I make it 50-50 or should I give Windows slightly more, since it requires a bit more? I will most likely only be using Windows to run Photoshop/Bridge.
The partition sizes that you allocate for Windows and Ubuntu will depend on the size of your hard drive(s), how much free space is available, and what your future needs for extra hard drive space may be.

I dual boot with Windows XP. I have a 40GB partition for XP. I use Windows very rarely these days. So 40GB for Windows is more than enough for me.
Windows 7 does require more room than XP though. Also, keep in mind that in order to completely defragment Windows, you need at least 15% of the Windows partition to be free space. At least that is the case for XP anyway.

For Ubuntu, the ideal situation is to create 3 partitions: root, swap, and home.

1. Root can be 10-20GB. This is where the operating system and all of your programs live.

2. Swap is analogous to *virtual memory* in Windows. This is hard drive space that is reserved to swap out programs from memory if you run out of physical RAM.
With 3GB of RAM, it is likely that you will rarely touch your swap partition in normal use. Make the swap partition 1GB. This will be plenty. I'm not sure how much memory the Gimp requires, but 3GB of physical memory should be more than adequate.

3. The rest of the hard drive will be the home partition. This is where your personal data and all of your user specific settings are stored. Think of the home partition as the *My Documents* folder in Windows.
The site I linked to earlier has excellent tutorials for dual booting Ubuntu with Windows 7: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

