---
title: "Installing Ubuntu on a USB stick ?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2008-05-24
With the prices of 4-8 Gb USB sticks declining I was wondering if you can use a USB stick as a removable drive where you install the full Ubuntu OS on.

And if you can will you be able to use it on different computers then your own,wich have different mobo/graphics ?

I'm planning on using it as a boot drive trough the BIOS so I'm not planning to start it trough GRUB.

---

### Post by Herman on 2008-05-24
Yes, I have one that I just installed the normal way and it works fine. 
Hardy Heron uses the latest [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/") and it automatically configures the video display in my three very different computers that can boot a USB.

There is another thread I posted in a week ago on this and the subject of wear in the USB flash memory was brought up. I have read a lot about that since then, but I have not yet decided if it's really an important issue or not.
I'll see if I can find a link to that earlier thread, another poster recommended the Persistent LiveCD install from Pendrive Linux.com because of a specially modified initrd.img that's supposed to make the flash memory last longer.
If you are not planning on using your Ubuntu USB as your full time (main operating system), like me, then wear in the flash memory is probably nothing to worry about.

EDIT: Here's the link, [COLOR=#980101]****[/COLOR] 			 			[How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528")

---

### Post by Hagar55 on 2008-05-24
Thancks for the info,


How large is your memory stick ?

---

### Post by animefan82 on 2008-05-24
One problem with the USB-stick, though, is that since it's flash-based, it'll support a write-cycle of 50-100.000 writes. With continous writing on the stick, it'll have about a year to live (8GB stick)
if the stick is 2GB, a couple of weeks (again, with continous writing)

---

### Post by Hagar55 on 2008-05-24
I thought you mainly read from the stick using the OS and only write when you make changes or save things (like documents for instance).

---

### Post by Herman on 2008-05-24
I have some 4 GB flash memory sticks and recently I have tried out a new 8 GB flash memory stick which I was hoping would be better. 

Someone asked in the other thread if being 'Vista Compliant' is a sign of a better quality flash memory. All I can say for sure is, my new 'Enhanced for Windows Ready Boost' 8 GB flash drives are extremely slow. It took three hours to install Hardy Heron as opposed to one hour for a normal USB stick. Of course, the flash memory will last longer, because I won't be using it, it's painfully slow to run an operating system in too. 
I guess I just had bad luck and chose the wrong product. 

Normally, I would think the larger the flash memory we can buy, the better.

As for wear in flash memory, I'm not an expert of flash memory. I'm just another user.
I have been using flash memory sticks for only around a year so, but I don't expect to use a USB flash memory for my main operating system, I have hard drives for that. I only use flash memory stick installations occassionally.

Here's a link from the Wikipedia, [Flash Memory]("http://en.wikipedia.org/wiki/Flash_memory"), it's important to read it all, notably, there's this quote from down close to the bottom of the page,
> There is also some concern that the finite number of erase/write cycles of flash memory would render flash memory unable to support an operating system. This seems to be a decreasing issue as warranties on flash-based SSDs are approaching those of current hard drives.[[14]]("http://en.wikipedia.org/wiki/Flash_memory#cite_note-13")[[15]]("http://en.wikipedia.org/wiki/Flash_memory#cite_note-14")
Here's a link to a .pdf file download, [WPaperWearLevelv1.0.pdf]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.filewatcher.com%2Fm%2FWPaperWearLevelv1.0.pdf%2Cv.141708.0.0.html&ei=qPw3SMfAM5O6gQOwxfCXBA&usg=AFQjCNFF_8_2AaP59DkCQ-OOCk_zchY7Jw&sig2=Isr6wGFvnqJuGpIP0wygMA"). My interpretation of that gives me the impression that flash memory will last for quite a while without the need to do anything special for it.

And then there's Re: [ext2 on Flash Memory]("http://lkml.org/lkml/2007/6/14/266"), by Jörn Engel.
Followed by, [LogFS: A new way of thinking about flash filesystems]("http://www.linux.com/feature/114295") from Linux.com, and [[FONT=Arial,Helvetica][SIZE=2]About the built-in Flash memory support in kernel 2.4.x[/SIZE][/FONT]]("http://www.linuxdevices.com/articles/AT8473001566.html").

Finally (for now), here's another Wikipedia link, [Wear Leveliing]("http://en.wikipedia.org/wiki/Wear_leveling").

What I haven't found yet, is some indication of how many times a day a Linux operating system will write to the flash memory and some actual tests where one or more flash memory sticks have been tested to destruction by running a Linux OS in then until they die.
We all know that hard disks will eventually expire too, and some of those fail prematurely.
> One problem with the USB-stick, though, is that since it's flash-based, it'll support a write-cycle of 50-100.000 writes. With continous writing on the stick, it'll have about a year to live (8GB stick)
if the stick is 2GB, a couple of weeks (again, with continous writing)     Where did you get that information from, animefan82, and what does 'continuous writing' mean exactly? Will Ubuntu really write to the flash memory continuously?

---

### Post by animefan82 on 2008-05-24
Yep, that's mostly true. I don't know the specifics of when Ubuntu writes or doesn't, but if you put a swap partition on the flash-disk, that'll get written into. Memory states, among other things are stored in the swap partition when ram isn't enough. Plus it's somehow faster to retrieve physical data than ram data, which I think is weird. As to why, again, I won't go into detail. Too technical to explain without flashy pictures (for me).

---

### Post by eldragon on 2008-05-24
> **animefan82 said:**
> Yep, that's mostly true. I don't know the specifics of when Ubuntu writes or doesn't, but if you put a swap partition on the flash-disk, that'll get written into. Memory states, among other things are stored in the swap partition when ram isn't enough. Plus it's somehow faster to retrieve physical data than ram data, which I think is weird. As to why, again, I won't go into detail. Too technical to explain without flashy pictures (for me).

if you are installing on a flash drive, you should not place a swap partition in the flash drive.

i was planning on doing this when i bought this notebook, just to find out the card reader in it isnt supported :( (ala completely freezes the kernel). so im left in the cold with a 2gb card unused.

anyway, as i found out later, reading from a flash drive isnt as fast as i thought it would be, so the project got left out.

---

### Post by animefan82 on 2008-05-24
> **Herman said:**
> 
Where did you get that information from, animefan82, and what does 'continuous writing' mean exactly? Will Ubuntu really write to the flash memory continuously?

Continuous writing means just that. Writing continuously, like when copying a file, only all the time. And no. Ubuntu will NOT write to the flash memory continuously. If there's a swap partition on the flash drive, it'll store memory-state information more often than not, but still, not continuously. Another thing about the "continuously" part is that it means the very least the flash memory will last if you write to the whole thing all the time until it "dies".

As for where I got my information about the cycles, I'll get right on it. I know it's somewhere here on the forum site somewhere. The info about the swap I got from my teacher at school.

---

### Post by Herman on 2008-05-24
:) According to this link, [Flash Solid State Disks - Inferior Technology or Closet Superstar?]("http://www.storagesearch.com/bitmicro-art1.html")
 > Flash chips with 300,000 write cycles are common, and currently the best flash chips are rated at 1,000,000 write cycles per block (with 8,000 blocks per chip).  Now, just because a flash chip has a given write cycle rating, it doesn't mean that the chip will self-destruct as soon as that threshold is reached.  It means that a flash chip with a 1 million Erase/Write endurance threshold limit will have only 0.02 percent of the sample population turn into a bad block when the write threshold is reached for that block.  The better flash SSD manufacturers have two ways to increase the longevity of the drives: First, a "balancing" algorithm is used.  This monitors how many times each disk block has been written.  This will greatly extend the life of the drive.  The better manufacturers have "wear-leveling" algorithms that balance the data intelligently, avoiding both exacerbating the wearing of the blocks and "thrashing" of the disk:  When a given block has been written above a certain percentage threshold, the SSD will (in the background, avoiding performance decreases) swap the data in that block with the data in a block that has exhibited a "read-only-like" characteristic.   Second, should bad blocks occur, they are mapped out as they would be on a rotating disk.  With usage patterns of writing gigabytes per day, each flash-based SSD should last **hundreds of years**, depending on capacity.  If it has a DRAM cache, it'll last even longer.

---

### Post by animefan82 on 2008-05-24
Hey, that's just about the same quote I read a couple of days back when researching whether I should install hardy on a flash-drive... Seems I don't need to search the exact post I began searching for after all.
I stand corrected on the 50-100.000 cycles, although that's what I read. I just found the same information [here]("http://en.wikipedia.org/wiki/USB_flash_drive"). that's 2-1.

---

### Post by Herman on 2008-05-24
I would be interested to hear from someone who has used Ubuntu in a flash memory stick and had the flash memory stick die on them. 
It would be interesting to read about some actual real experiences, since we really don't know exactly where the authors of web sites get their information from. :)

Any information from some properly controlled tests and experiments would be even better.

---

### Post by Herman on 2008-05-24
> I stand corrected on the 50-100.000 cycles, although that's what I read. I just found the same information [here]("http://en.wikipedia.org/wiki/USB_flash_drive"). that's 2-1.     
:) Thanks for the link, animefan82, I have read it and added that one to my bookmarks.

Hey look, here's a new page from Pendrive Linux : [Ubuntu 8.04 USB Hard Drive install]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372") (How to install Ubuntu to a USB flash memory stick just as in the same way you would install Ubuntu to any other kind of drive).

...and here is another interesting link, [Squeak! - How Solid is Hard Disk's Future?]("http://www.storagesearch.com/hardwayaheadforhds.html")

---

### Post by Rebelli0us on 2008-05-25
I too was curious about longevity of flash drives, and I couldn't find anyone that had reported a failure.

Well mine did after 2 months

[http://ubuntuforums.org/showthread.php?t=711245](http://ubuntuforums.org/showthread.php?t=711245)

It was 4gb A-data and it was replaced under warranty. It cost about $30 from newegg, so it could have been just crappy quality flash.

---

### Post by Herman on 2008-05-25
:) Thank you Rebelli0us, that may be useful information. If more people report that a USB can be expected to last only about two months then I will only recommend installing Ubuntu in flash memory sticks breifly for special purposes. Perhaps for rescue operations or for performing further installations. (Installling to hard drive when there's no useable CD-ROM drive.)
I don't think two months would be good value for money.

Regards, Herman :)

---

### Post by jward3010 on 2008-05-25
I know someone with a 16GB flash which works for about a week until it needs a full reformat to use it again. Flash memory has its flaws and the bigger the stick the higher the chance of losing everything spontaneously. I'd reccomend to those that are suggesting bigger than 8GB drives to try no to go over that limit of 8GB unless you are completely guaranteed of their performance. USB installs are great for LiveUSB OS's like Ubuntu, Backtrack 3, PCLinux etc. but not for permanent systems realistically. Also modern S-ATA II hard disks are much quicker.

---

### Post by Herman on 2008-06-12
The [Asus eee pc]("http://en.wikipedia.org/wiki/ASUS_Eee_PC")  is a miniature notebook computer, (called a 'sub-notebook), and measures only about 9" x 6 1/2" x 1.4 ". 
It comes with Xandros Linux when it's new and uses a [solid state drive]("http://en.wikipedia.org/wiki/Solid-state_drive") of 2, 4 or 8 GB and that has been **estimated to last probably around 25 years under normal use**, refer: [SSD Write Limit]("http://wiki.eeeuser.com/ssd_write_limit").
:)

---

### Post by Herman on 2010-02-06
:D Well my Asus EeePC 4G was purchased on 23rd Sept 2008, I still have the receipt, and it's now the 7th Feb 2010 so it's well over a year old now.
It has been left running 24/7 most of the time but the flash memory has not worn out yet so far.

I have Ubuntu Intrepid Ibex in it and recently I re-installed it with Ubuntu Karmic Koala.
Its little 4 GB SSD drive is just about full, I have too much software installed.
A flash memory disc that's twice or four times the size with more free space in it should I imagine last a lot longer than twice or four times as long since there would be a disproportionate number of empty blocks for the wear levelling process to rotate and the writes to disc and spread the wear around. 
So I'm creating a worse case scenario here.

I'll be sad when the flash memory drive finally wears out some day, but I would have to say it's doing well for such a small flash memory disc with Ubuntu running in it 24/7.

**So far it has blown the doors off the 2 month prognosis.**

... and it has a swap file in it too!
... and I use file system journaling!  ):P

I think the hundreds of years or even 25 year predictions might be a little on the optimistic side though.

:D We'll have to wait and see ...

---

### Post by Herman on 2010-03-19
[**ASUS Tech Support Confirms Two Year Hardware Warranty Details.**]("http://darkertechnologies.com/notes/2008/01/26/asus-tech-support-confirms-two-year-hardware-warranty-details-im-getting-2gb/")  - Posted by rmrubin in Jan 2008 - darker technotes.

Judging from the information in this  (above)  link it looks like it will probably take a while yet before I'll know how long my EeePC's 4 GB SSD (flash) drive will last before it wears our from too many disk writes. :D

---

### Post by Herman on 2010-05-01
Hey everyone, my ASUS EeePC, with only a 4GB flash memory SSD drive for the operating system plus an SD card for storage  is 19 months old and has now been re-installed with Ubuntu Lucid Lynx and it's still working great. No problems to report at all.     ):P

---

### Post by Herman on 2010-10-10
:) My Asus EeePC 4G was purchased on 23rd Sept 2008, I still have the  receipt, and it's now the Monday, October 11 2010 so it's a little over a 2 years old and still going strong.

I still have Ubuntu Lucid Lynx running in it and I have TangoGPS installed in it now and and I use it often for important work driving around collecting geodata and road information on 2000 km of dusty washboard roads. Fortunately it has good, sturdy hinges for the monitor. I mean really, no other computer would be able to stand the shaking, vibrations and occasional impact shocks that this tough little netbook handles with ease.  Certainly if it had a hard disk drive as opposed to a flash memory SSD it would have died for sure withing the first week if not the first day.

Now that it's over two years old it's over it's warranty period for the little 4 GB SSD. It will be interesting to see how much longer the flash memory will last with a full Ubuntu install running in it and with a swap file and with normal file system journaling.

So far it seems like the people who keep saying you can't (or shouldn't) install a regular operating system in flash memory due to 'rapid memory wear' are wrong.

I have a few USB flash memory sticks and some of them have Ubuntu installations in them too. I have had one fail on me, but that one was almost new and it only had data in it, so I think it was just a factory defect and I'll send it back to the manufacturers. Most of my flash memory sticks are getting pretty old now. I must be phenomonally lucky with flash memory or the people who keep claiming flash memory will wear out 'rapidly' are exaggerating a lot.  :)

---

### Post by Herman on 2010-12-19
):P  Still working fine on Dec 20th 2010.

---

### Post by Shintek on 2010-12-19
Universal USB Installer.

---

### Post by kgarbutt on 2010-12-19
Hey Herman,

I have a ASUS eeepc 4G too and I like it. It has to be two to three years old know and I have been running 10.04 on it for sometime now.

As for installing Ubunutu on flashdrive, I use Netbootin. You should find it in the repositories or as a deb download from the website.

---

### Post by jimmers on 2010-12-20
Hi Guys,
I have a Kingston DataTraveler 16GB, and I have been running Ubuntu on it since Jaunty without any problems, I am running Lucid on it now, I did a standard install using the whole disk, it is a clone of my Lap Top, it gets updated as and when required, but I must stress that it is just a Back Up of my Lap Top and not used as a main OS, and not run every day.
I used to have a lot of problems with USB Sticks till I decided on Kingston, expensive (£40.00 UK Sterling) but worth it.

Well that's my Tuppence worth, whether or not it is worth anything to you all.

Hope you all, have an absolutely Brills Festive Season.

---

### Post by Herman on 2010-12-20
@ kgarbutt   & @ jimmers

:grin: That's exactly the kind of thing I'm hoping to be able to read. Thanks for posting!
Back when this thread first began, every time flash memory was mentioned in the forums there would be ten posters parroting off warnings that it would fail rapidly if an operating system is installed in it in any other than a 'persistence' type of install.
Nobody really knew for sure, or could provide any evidence to prove or disprove that at least some brands and models of flash memory sticks or SSDs are okay. At least one flash memory stick manufacturer I know of sells a model that's guaranteed for life. 
Now it looks like time is beginning to tell the real story and I hope a few others with positive experiences will be around. :)

@ Shintek,
Thanks for the link, and yes, 'Persistence' installs are great, I like that kind of flash memory installation too because they have the Ubuntu installer in them.
We need both kinds at different times, for slightly different purposes. :)

---

### Post by Herman on 2011-06-18
:D I'm still here and my EeePC 4G is still here too in June 2011 and still running just fine!

I just re-installed it with a fresh installation of Ubuntu 11.4 'Natty Narwhal' and I really love the new Unity Desktop, it's great for netbooks with small screens such as this, (only 153 x 92 mm).

I didn't make a swap file this time, and I installed '[dynamic swap space manager]("http://pqxx.org/development/swapspace/")' aka 'swapspace' from the universe repository instead. 
I'm still setting swappiness to 10 by adding a line in /sysctl.conf and I'm really impressed so far with the amount of extra disk space I have available now, thanks mainly to 'swapspace',
```
herman@eeepc-narwhal:~$ df -h
```> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.3G  1.2G  67% /
none                  996M  688K  995M   1% /dev
none                 1002M  152K 1002M   1% /dev/shm
none                 1002M  100K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
/dev/sdb1              15G  2.2G   12G  16% /home
As for flash memory wear, my EeeCP's little 4GB SSD is now about 2yrs 9months old and is still running / just fine. The original 4GB camera card I use for /home failed and I have replaced that with a 16GB one though. I don't imagine camera cards feature the kind of [controller]("http://en.wikipedia.org/wiki/Flash_memory_controller") with the same wear leveling capabilities as an SSD would be expected to and a flash memory stick should if it's a good quality product.

The EeePC is now my car computer and I take it with me everywhere I travel, it runs my USB GPS receiver and I use that a lot. I have other computers for doing most other kinds of work with though, and I don't need the EeePC on 24/7 now like I did when I was using it for skype.

I can hardly wait to get out and do some more GPS data collecting, it should be much more pleasant with the new unity desktop allowing me more screen  real estate for my maps. :)

---

