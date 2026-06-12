---
title: "Installation question"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by JerseyDevil1111 on 2007-06-10
I couldn't find the FAQs so here's the question. If I burn the 7.04 file to a CD and I boot from the CD, what will happen? Will the screen let me choose which OS to run, UB or XP. Is there an install Ubuntu option that puts Ubuntu on the Hard drive alongside XP? Do I have to manually partition the drive in order to put Ubunto on?

---

### Post by abn91c on 2007-06-10
use wubi go here to get it  [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
it installs like a windows program from within windows, make sure you defrag windows first and follow the on screen installation instructions. You need a broadband connection since it will download ubuntu during setup, also patience it will take soemtime to download depending on your connection speed.

---

### Post by merlinus on 2007-06-10
You can boot from the cd, and when it is up-and-running, click the Install icon on the desktop to start the process.

Best to defrag your windows partition several times first.

After answering a few questions about language and keyboard, you will get to a partitioning screen.  Do not select Use Entire Disk (or something to that effect), or windows will be gone.

Use Guided if possible, Manual if not.  You will be able to re-size your windows partition to make room for ubuntu.

You can then install ubuntu in the freed-up space, leaving room for a swap partition that is about 1.5 times your RAM.

You will need a partition for /, and I suggest you also make one for /home.  These are best formatted as ext3, and you will need to specify these mount points.

After installation, when you reboot there will be a menu (grub) that will allow you to choose between ubuntu and windows.

Have fun!

-merlin

---

### Post by HunkirDowne on 2007-06-10
Burn, baby, burn!

Seriously.  what you will get is a "live" cd that you can boot from and play around with, see if you like it.  My advice is to live with it for a bit before you decide.  If Ubuntu doesn't work for you there is Kubuntu which has a bit edgier interface -- better for multimedia they say.  

(Ubuntu generally uses Gnome for a desktop, whereas Kubuntu uses KDE.  I don't care as much about multimedia but I do like a good spreadsheet and Gnome has OpenOffice which started out life as StarOffice, IIRC.)

Ubuntu *can* live alongside XP but there are some caveats.  For instance, if you use XP after installing Ubuntu, your system could freeze at boot.  This is not a major hassle -- it happened to me earlier this weekend and I recovered fairly quickly.  But to save you some heartache and pain take a look at the link below.  It's pretty technical (for some) but looks like a good idea before you install Ubuntu to the hard drive.  I ran Ubuntu off of the CD for several weeks before committing and wished I'd read/followed the stuff in the aforementioned link.

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

Bottom line, Windows likes to think it's the only operating system on your computer.  When you install Linux and it installs the Grub boot loader in the master boot record (MBR), Windows might overwrite it.  Whether Microsoft does this on purpose or just by default is probably up for debate-- as much as I'd like to think otherwise, I think it's the latter to be honest.

By using the NTLDR, Windows boot loader, you avoid that issue as Grub will not overwrite NTLDR if you are careful not to install Grub to the MBR like I did.

The devil is in the details, as they say, and the details are in the weblink above.

Burn the CD.  Give it a whirl.  Notice this: When you are using the CD the system will slow down as it has to access the CD.  This is only momentary.  Then in Windows, notice how often and how long the hard disk is accessed.  I can't say my Linux system never slows down, but it does so less frequently than it does in Windows.


HTH!

---

### Post by JerseyDevil1111 on 2007-06-10
Great. How exactly do I run Ubuntu from the CD, without installing it? Boot up from the CD and then...

---

### Post by HunkirDowne on 2007-06-10
> **merlinus said:**
> 
You will need a partition for /, and I suggest you also make one for /home.  These are best formatted as ext3, and you will need to specify these mount points.


ext3?  Why not reiserfs?

Seriously, no argument -- I'm no expert, but I've had better success with the latter.  I had an old disk that was otherwise irreparably damaged (superblocks, I think).  DOS/Win couldn't touch it, ext3 (ext2? yikes, don't recall!) was taking bloody forever; mkfs reiserfs, fsck went like greezed lightnin'.  All the data was toast but long backed up anyway, but I had a good-sized hard disk back and it's been running great ever since (what's that smell?...:-D)

Anyway, just thought I'd put that out there.  I figure at least one of us will learn something and it's usually me if I haven't stuck my foot to far in my mouth.  ;-)

---

### Post by merlinus on 2007-06-10
> **JerseyDevil1111 said:**
> Great. How exactly do I run Ubuntu from the CD, without installing it? Boot up from the CD and then...

Yes.  Select the first option from the opening menu.  It will allow you to run ubuntu before installing it, so you can check to see that everything is working properly.

-merlin

---

### Post by merlinus on 2007-06-10
I do not know much about reiserfs, but there is a driver (ifs) that allows me to read and write to ext3 partitions from windows.

It comes in handy every so often, usually when burning cds or exporting data from the one windows app I still need.

-merlin

---

### Post by JerseyDevil1111 on 2007-06-11
The PC won't boot from the CD I burned. I copied the 700 mb file to a cd and then turned on the PC. But I did download Wubi 7.0. If I click on the Wubi desktop icon and follow the procedure will XP get overwritten or is this a safe way to try Ubuntu?

---

### Post by merlinus on 2007-06-11
You need to burn the downloaded file (,iso) as a disk image, not a data disk.  Most cd burning programs have an option for this in one of the menus.

If you look at the contents of the cd in windows and do not see listings of folders and files but only one file, then you did not burn it correctly, and it will not boot your computer.

That may be the problem.

-merlin

---

