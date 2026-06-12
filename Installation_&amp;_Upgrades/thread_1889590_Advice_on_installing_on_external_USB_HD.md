---
title: "Advice on installing on external USB HD"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by km6xz on 2011-12-01
Hello 
I have a 64 bit version of Windows 7 on my HP laptop which I wanted to dual boot but found out that there is a limit of 4 partitions that can be used. My original Windows and HP specific partitions totals 4 so I can't create a new partition for Ubuntu 11.10...as I understand it. 

If that is the case, I am interested in installing 11.10 on a 500gig external USB HD. I have the USB flash drive with 11.10 on it and it boots and allows me to try out Ubuntu. 
When the USB HD is connected it mounts it with out problems.
I selected "Install to HD", the first option on the Unity left column bar.
The choices for installation are side by side in dual boot, replace Win 7 or Other. Selecting the Dual boot option the installer gives me the installation drive as the USB HD. So far so good. My question is, if installed this way does GRUB2 install on the internal hard drive and give the option of OS at start up? What if the USB HD is not connected, does the boot into Windows remain an option?

If the boot record is put on the external drive instead, does Windows boot normally if the external drive is missing?
I don't want to proceed until I figure out how the installation impacts Windows.
What I would like is have the option of booting Ubuntu when the USB is connected from start up, and not interfere with Windows if the external drive is not connected at startup.

If any of this makes sense any suggestions would be a big help.

---

### Post by efflandt on 2011-12-01
For installation on an external drive, I would be apprehensive (scared) to let Ubuntu do that automatically.

I would select "Other", set up partition(s) how I wanted, and make certain that you **pay attention to the drop down list at bottom of partitioning install screen to put grub on the mbr of the USB drive**.

Then when you boot, you might have to press a key during BIOS splash screen to select the USB boot drive, even if you set BIOS to boot USB before hd with some computers.  Windows should boot normally when the external drive is not connected.  I do that with my business laptop which has no free partitions.

Note that some computers may have trouble booting far out on a 500 GB external drive even if they have no trouble booting from a larger internal drive.  I have that problem with a Dell desktop from 2010, even though Dell and Toshiba laptops from 2006 have no trouble booting the same 500 GB USB drive.  64-bit Ubuntu on a 160 GB drive can boot from any of those PC's or even an old HP Athlon64 desktop from 2004 (which also cannot boot the 500 GB USB drive).  So it is not that the drive ends up as a different sd device (since UUID's are used) or different video drivers (using defaults), it is some other unknown issue that dumps certain PC's into grub rescue with large external drives.

---

### Post by critin on 2011-12-01
Have you considered using Wubi?  It will install inside windows as a reg. program does and will still dual boot.  It works well in cases like this and if you later want to redo your partitions to install ubuntu more permanently, Wubi can be uninstalled through the add/remove windows menu.  It (wubi) also can be moved intact according to some tutorials I've seen.

---

### Post by km6xz on 2011-12-01
Thank you both for the suggestions. I like the idea of having a permanent install on the external drive but did not know anything about how Wubi works...time to read up. 

I think I will try the "Other" method for install on the external drive, regardless, because that drive can work on other machines. 

Thanks for two good options. I will report back the results

---

### Post by oldfred on 2011-12-01
Just to add a little bit. Herman has pictures. 

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

wubi is fine for those who do not want to repartition. It is not meant for a long term install as it is just a file inside the Windows NTFS partition that runs as a full Ubuntu. But any issues will NTFS or Windows will prevent you booting wubi.

To go along with efflandt's comments, we have seen users with large / (root) partition have issues. I would keep a smaller / and have /home, data or shared NTFS partitions for most of the drive. If data is elsewhere root can be 10 to 20GB, but if installing in a 500GB drive use 25GB or so. On my 640GB drive I have a couple of 100GB data partitions and the rest are slowly becoming every install since 9.10 and a few others in 25GB / partitions. I still have some unallocated, but keep adding another / to try something.

---

### Post by collisionystm on 2011-12-01
You can install onto the external usb drive 

just have it plugged in when you run setup

choose it durring setup

hit the 'choose boot device' hot key during computer startup and choose usb drive to access ubuntu

---

### Post by collisionystm on 2011-12-01
its no different than a live usb

---

### Post by gordintoronto on 2011-12-01
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. fullcirclemagazine.org

Issue 47 has details about installing on an external drive.

---

### Post by km6xz on 2011-12-02
Wow, what great advice, all viable solutions. The article in FullCircle was perfectly on-point. Here is the plan. to follow the suggested manipulation of the recover and HP tools partitions to install Ubuntu normally as dual boot on the internal drive. Second, to use the external drive for another installation that can be used for testing other machines and playing. 

For those who have not seen FullCircle Magazine, I hadn't, it is really a professional looking and interesting resource. I downloaded a number of podcasts to listen while walking to work this morning. 
One of the, or THE best thing about Ubuntu is the community's willingness to share the accumulated wisdom with patience.

---

### Post by km6xz on 2011-12-03
I installed on both the internal hard drive and a USB hard drive. The USB seemed almost as fast as the internal drive but after a few hours the external 500gig drive died and not readable at all. I am assuming it has nothing to do with the Ubuntu install and will get another one, they are so cheep nowadays. But both methods work and the only issue is that the wireless adapter connects at only 5mb/s regardless of settings. The wired connection works well at 100mb/s. 

I just wrote this update to let people know who have Windows 7 taking up all the allotted primary partitions, or people who might be interested in booting from an external hard drive, both work using the advice in this thread.

---

### Post by collisionystm on 2011-12-03
> **km6xz said:**
> I installed on both the internal hard drive and a USB hard drive. The USB seemed almost as fast as the internal drive but after a few hours the external 500gig drive died and not readable at all. I am assuming it has nothing to do with the Ubuntu install and will get another one, they are so cheep nowadays. But both methods work and the only issue is that the wireless adapter connects at only 5mb/s regardless of settings. The wired connection works well at 100mb/s. 

I just wrote this update to let people know who have Windows 7 taking up all the allotted primary partitions, or people who might be interested in booting from an external hard drive, both work using the advice in this thread.

Sweet! Glad to hear it! Now just get a smaller compact usb hard drive that you just carry in your pocket lol. Carry your computer with you

---

### Post by Basher101 on 2011-12-03
> **collisionystm said:**
> Sweet! Glad to hear it! Now just get a smaller compact usb hard drive that you just carry in your pocket lol. Carry your computer with you


With a fresh install that is below 20 GB after installing programs and configuring, you can use Remastersys to make a **_[COLOR="Red"]Bootable[/COLOR]_** live .iso from your install. This is IMO the best backup tool you can use. Just pop in your self-made Live CD/USB and reinstall it like usually and BANG you got everything the way it was AND it is portable. I got 3 "self-made" versions on my 4 GB stick, one with office stuff, one with entertainment and one with web-diagnosis stuff.

---

