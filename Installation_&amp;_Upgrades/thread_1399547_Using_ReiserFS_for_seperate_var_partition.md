---
title: "Using ReiserFS for seperate /var partition?"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by VCSkier on 2010-02-05
So I'm about to do a fresh install on a new computer, and I plan to dual boot with Arch Linux and Ubuntu.  I've been doing some reading on Arch Linux, and apparently one of the little tweaks that many Arch users use to increase performance is to put /var/ on it's own partition using a file system that is good for quickly writing many small files, namely, ReiserFS.  I was wondering if this would do any good for Ubuntu.  Is Ubuntu's usage of /var similar to Arch's, and if so would using a similar partition setup provide any performance increase?

Thanks!

---

### Post by Herman on 2010-02-06
I noticed a big difference between ext3 and reiserfs when I was trying out file systems for flash memory and bench testing with bonnie++. The differences were not so apparent in the benchtesting results to be honest, but the operating system performed much better with Rieserfs in a way that I could feel. There was a noticeable and annoying lag with ext3 when I moused over the 'Application', Places' and 'System' menus and I was left waiting for the icons to appear, and the selection bar would be stuck for what seemed like several seconds sometimes.

With ext4 though, that problem seem to be gone. I can't really pick the difference between ext4 and Reiserfs, so I think now that ext4 is now my preferred choice.
You can probably just create one large / partition and just format it all ext4.

That's only my opinion. :D

---

### Post by Herman on 2010-02-07
Your question aroused my curiosity so I made two USB flash memory installations in LVM (with LUKS).

In one USB I followed Martti Kuparninen's installation procedure, [Hard Drive Encryption in My Ubuntu Installation]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html") , but I made more partitions than the linked how-to illustrates.
I formatted the /boot, /tmp and /var with reiserfs, with mount options nolog, notail, noatime.
I made / (root),  /home, and /usr formatted with ext4, with mount option notaime.

I have it up and running and I have started to tweak it a bit for speed. 
It's only a USB drive so I don't expect much in the way of speed, but I can say already that it does seem pretty snappy for a USB flash memory stick.

I have another USB flash memory which is exactly the same make and model and I installed a one-piece installation in it, also LVM - LUKS, made by the guided partitioning option in the alternate CD installer, all ext4.

Both USB flash memory sticks are 16 GB Kingston DataTraveler 2G models.
They're both newly installed with Ubuntu Lucid Lynx Alpha 2.

It could be some time before I have any results or opinion about which USB is faster.
 
If the multi-partition USB drive turns out to be any faster than the single partition one, I might consider making a multi-partition installation in my OCZ Vertex SSDrive to see how fast it will be in that.
I'm not sure if I can improve that very much, it's pretty fast already, I think it boots in about ten seconds but I'm not quite sure.

The single partition installation was much simpler to install of course and will probably be simpler to take care of too, which is an important factor to consider.
I do appreciate responsiveness and speed in an operating system though too. :D

---

### Post by VCSkier on 2010-02-07
Very interesting Herman.  I'm curious to hear your results.  For the record, [Arch Linux's Wiki]("http://wiki.archlinux.org/index.php/Beginners_Guide#Partition_Scheme") is where I got the idea.  Under Partition Schemes, it describes some different possibilities, and then under "Set Filesystem Mountpoints," it suggests ReiserFS as a particularly good fit for /var, because of it's handling of large quantities of small files.  I am at least planning on doing this for my Arch installation, and possibly for Ubuntu as well.

The downside is that Reiser is certainly slower at mounting, so it will probably negatively influence boot time, but for a desktop system that is rebooted once a day at most, that is a minimal sacrifice.

---

### Post by MisfitI38 on 2010-02-07
> **VCSkier said:**
> Very interesting Herman.  I'm curious to hear your results.  For the record, [Arch Linux's Wiki]("http://wiki.archlinux.org/index.php/Beginners_Guide#Partition_Scheme") is where I got the idea.  Under Partition Schemes, it describes some different possibilities, and then under "Set Filesystem Mountpoints," it suggests ReiserFS as a particularly good fit for /var, because of it's handling of large quantities of small files.  I am at least planning on doing this for my Arch installation, and possibly for Ubuntu as well...

Both pacman and apt package caches reside under /var so there is a potential performance advantage for apt-based systems; it may be worth a shot. I cannot speak firsthand about any Debian system I've had, as they have all been short-lived and I never utilized a ReiserFS partition for /var on any of them, but this *does* work particularly well on Arch. (The ABS tree also resides under /var, further enhancing the effect when accessed.)
Another fun trick is to invoke pacman-optimize as root every so often, which will defragment the pacman cache.
Have fun.

---

### Post by Herman on 2010-02-07
The one with the entire disk guided installation, all ext4 boots in around 2 mins 30 sec to 2 mins 38 secs.

The one that has multiple partitions (or should I say LVs), is a little slower at boot time, that one takes somewhere between 2 mins 43 secons to 2 mins 50 seconds or so to boot.

I'm measuring from the time I hit 'enter' at the GRUB Menu until the password prompt for unlocking the encrypted file systems, then stopping the timer while I type the passphrase. Then I'm restarting the timer until the login password, stopping it for that, then timing until the desktop appears.
> The downside is that Reiser is certainly slower at mounting, so it will probably negatively influence boot time, but for a desktop system that is rebooted once a day at most, that is a minimal sacrifice.
So far that seems to be true, the installation containing half reiserfs does seem to be slower at boot time.

---

### Post by Herman on 2010-02-07
Okay, here's a real world scenario,

You have just booted up Ubuntu and the telephone rings. 
It's your boss.
He (or she) wants to know where you went yesterday, and some facts and figures from yesterday's work.
You need to open GIMP for your layered map, (I use Quantum GIS now but I used to use GIMP), and you need to open a spreadsheet and a word document.

It seems like it takes forever for those programs to get going while your boss waits impatiently on the other end of the phone line ...  

seconds turn into hours, or so it seems ...

SO, our next tests will be, 

1. Mousing over the menus for the first time after boot-up to see if there's a lag waiting for the icons to be drawn. Or if the the highlighted selection gets stuck on a menu item and the user had to wait for the item he or she wants to become highlighted. After all the menus get working they seem to remain working properly for the duration of a session, but I'm interested in how well they work right away after a reboot.

2. How many seconds does it take to open programs like GIMP, Open Office Spreadsheet, Open Office Word for the first time after a boot-up. Once they've been opened the first time they tend to open pretty quick after that. :D

---

### Post by Herman on 2010-02-10
[COLOR=Red]**Multi partition LUKS LVM installation with /tmp, /var and /boot partitions reiserfs**
open GIMP_________8_____4.8_____8_____5_____5_____6_____7_____6.4_______= 50.2 seconds to open GIMP on eight boot-ups
open spreadsheet____9_____8.7____11____11_____9_____10___10.5___12.7_____= 81.9 seconds to open a spreadsheet on eight boot-ups
open word file_______2_____1.6_____1_____1.6___1.6_____2____3_____1.9____= 14.7 seconds to open a word file on eight boot-ups
open firefox________________________________________5______4______5_____= 14 seconds to open firefox on three boot-ups
                                    _________________________________________________________**TOTAL_____= 160.8 seconds**[/COLOR]
                                    
                                    
    [COLOR=Blue]**Integral partition LUKS LVM installation all ext4**
open GIMP_________5_____7_____5_____5_____5_____5_____5.8____5.3_____= 43.1 seconds to open GIMP on eight boot-ups
open spreadsheet___12____11_____9_____9____12_____9____9.3___13.3____= 84.6 seconds to open a spreadsheet on eight boot-ups
open word file_______2_____2_____1.8___1.8___1.5___1.7____2.3____3.7____= 16.8 seconds to open a word file on eight boot-ups
open firefox___________________________________3.8____3.9____3.25_____= 10.95 seconds to open firefox on three boot-ups
                                    _________________________________________________________**TOTAL____=155.45 seconds**

[COLOR=Black]It look like it doesn't make very much difference whether a user goes to all the work of making a lot of separate file systems, at least from the results of these tests.
If anything, it could result in a slightly slower system.

The results of these tests could have been affected by other programs running in the background, especially as sometimes I didn't wait very long after the systems booted before running the tests. Also, these tests rely on human reflexes to start and stop the 'stopwatch' program which I used as a timer. More tests should be done to get reliable results, but this should be enough to give us an idea.

Remember too, that a real hard disk or SSD drive will be a lot faster than a USB flash memory stick, so the difference between the speed of two file systems would be less, and therefore harder to measure.


[/COLOR]
[/COLOR]

---

