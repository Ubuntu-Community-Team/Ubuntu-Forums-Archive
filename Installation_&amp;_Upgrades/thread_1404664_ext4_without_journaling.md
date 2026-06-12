---
title: "ext4 without journaling"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by gabrielcik on 2010-02-11
Hello,

I want to use the ext4 since i had problems with ext2.

I have a sdd and i heard it would be better to remove the journaling...

I found on the net this command for to remove it:
sudo tune2fs -O ^has_journal /dev/sdXN

is it safe? or maybe it is better to leave it on?

Thank you

---

### Post by khelben1979 on 2010-02-12
If you feel uncertain, I would recommend to use the default settings of [EXT4]("http://en.wikipedia.org/wiki/EXT4") or read the wiki document and see if it gives you something.

---

### Post by dabl on 2010-02-12
> **gabrielcik said:**
> 

 i had problems with ext2.



What does this mean -- what problems?

I cannot think of a "ext2 problem" that will be solved by using ext3 or ext4, except for the lack of a journal and extents.  :?

---

### Post by gabrielcik on 2010-02-23
With ext2 it happens that after a simple crush (due to the gnome power control which didn't switch off the pc on low battery) the system didn't restart anymore.

In the same time with ext2, when the pc reboot after i update ubuntu packages the system restart making a file system check.

With ext4 journaled the restart is fine without any particular check...

Thank you

---

### Post by Herman on 2010-02-23
I have an SSD and I use ext4.

There was only ext2 and then file system journaling was added to make ext3.
If you remove or turn off the journaling you have ext2 and if you turn it on again you have ext3. (Basically speaking in simple terms). 
Following are some interesting links for you to read if you want to know more details, [Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html") , [EXT3, Journaling Filesystem]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html") , and  **[Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html")**.

The new version of ext3 is called ext4 and it is excellent to use for SSD drive and all kinds of flash memory. [Ext4]("http://kernelnewbies.org/Ext4") - kernelnewbies

[Theodore Ts'o]("http://en.wikipedia.org/wiki/Theodore_Ts%27o") - Wikipedia link
Theodore Ts'o is the lead developer and maintainer of e2fsprogs and a maintainer of the ext4 file systems and he knows a lot about SSD drives too. 
We are not 'left out in the cold', here is a link to blog he wrote on this subject,  [Archive for the &#8216;SSD&#8217;]("http://thunk.org/tytso/blog/category/computers/ssd/").

If you can spare the time, I recommend thoroughly studying all of those links and also the good quality sub-links those pages contain. There's a wealth of information there for you if you have the time to absorb it all. 
I have been interested enough to read them all repeatedly myself. The short answer in my opinion is to use file system journaling, meaning we should use ext4 (with journaling).

---

### Post by gabrielcik on 2010-02-25
And what about to add noatime, is it really good for ssd?

---

### Post by dabl on 2010-02-25
> **gabrielcik said:**
> With ext2 it happens that after a simple crush (due to the gnome power control which didn't switch off the pc on low battery) the system didn't restart anymore.

In the same time with ext2, when the pc reboot after i update ubuntu packages the system restart making a file system check.

With ext4 journaled the restart is fine without any particular check...

Thank you

You _need_ to have the filesystem checked periodically, and especially after you lose power.  It is not a bad thing that ext2 requires a filesystem check after a hard power-off.  ext3 and ext4 also require a fsck after hard power-off.

The Ted Ts'o article recommends the noatime option on ext4 if you want to minimize disk writes.

---

### Post by Herman on 2010-02-25
> And what about to add noatime, is it really good for ssd?
I think it's best to use noatime for installations in all kinds of flash memory, I think that Mr Ts'o probably knows what he's talking about. 
It's easy to do that by editing the /etc/fstab file.

I also like to set swappiness to 10 in my /etc/sysctl.conf file so the operating system will prefer to use RAM but will use the swap file or swap area if it needs to.  [Performance tuning with 'swappiness']("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") - Ubuntu Community Docs.


I like to add the boot option 'elevator=noop' to my grub.cfg too, [Noop scheduler]("http://en.wikipedia.org/wiki/Noop_scheduler") - wikipedia.

I use these settings to get the best performance from my SSD or flash drive. So far I have not noticed any problems with flash memory wearing out.

Let me know if you want more details on anything, I'll elaborate if you're interested.

---

### Post by gabrielcik on 2010-02-26
How can i use this option (elevator=noop) in Karmic?
I know it uses grub2 and so there is not more menu.lst...

Thank you

---

### Post by gabrielcik on 2010-02-26
I have one more question, what about trim on karmic?
I have found this application Disk Trim but i don't know exactly what to do with it...

Thx

---

### Post by Herman on 2010-02-26
> How can i use this option (elevator=noop) in Karmic?
I know it uses grub2 and so there is not more menu.lst...
An I/O scheduler is used by the linux kernel for sequencing writes to hard disk drives.
For a hard disk drive with read an write heads pivoting on actuator arms seeking data on a disk platter or searching for an empty place to write to, it's advantageous to have the linux kernel organize the data so that disk writes that are physically close to where the hard disk's read and write heads may happen to be at a point in time will be done first. Data to be written somewhere far away on the disc surface will be held temporarily until a more convenient time, when the read and write heads happen to be passing through that neighborhood. That's a more efficient way to manage mechanical hard disks, and it usually results in better performance.  As far as I have been able to find out by googling and reading, cfg is the default I/O scheduler for Ubuntu.

Flash memory doesn't have any read-write heads or controller arms, so we don't need to wait for any complicated I/O scheduling at all, for us it might even slow things down. We can let the SSD's [Flash Memory Controller Chip]("http://www.extremetech.com/article2/0,2845,2329594,00.asp") have control of the reads and writes to the flash memory. 
The [Flash Memory Controller Chip]("http://www.extremetech.com/article2/0,2845,2329594,00.asp") governs the interaction between software we're using and the hardware inside the device and is the most important thing to consider when shopping for an SSD drive or USB flash stick. When we pay extra money for a good quality SSD drive or flash memory stick we're mainly paying for a better controller chip.

To set GRUB2 to pass the "elevator=noop" to the linux kernel at boot time, we just need to edit our /etc/default/grub file and then run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' to write the changes to our grub.cfg and make that persistent.
```
gksudo gedit /etc/default/grub

``````
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**[COLOR=Blue]elevator=noop[/COLOR]**"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

```Type (or copy and paste) the words **elevator=noop** in between the inverted commas, save and close the file.```
sudo grub-mkconfig -o /boot/grub/grub.cfg

``` This command scans your computer for operating systems and writes you a new grub.cfg automatically according to the information in files such as the one we just edited and adds all operating systems it detects in your computer to the boot menu.

---

### Post by gabrielcik on 2010-02-27
Thank you, i follow you instruction and i added elevator noop.

I didn't see so far a difference in performances during the boot... maybe it is coz it goes already fast with a ocz ssd.

Btw, is it not necessary to run also update-grub?

And what about trim?

Thx

---

### Post by Herman on 2010-02-27
Yes, I have an OCZ Vertex here and mine boots in about 7 seconds from the GRUB menu to the desktop, (not counting the time it takes me to type my big long password at log-in).
It's hard to tell if something is an improvement when it's already so fast, but I suppose everything we do that's right helps a little bit.

I'm not up to date about the ata trim command, I read a long time ago that the ext4 file system has inbuilt support for the trim command. 
According to the following linked thread our kernel has support for trim too, [[all variants] Use trim command for ssd? ]("http://ubuntuforums.org/showthread.php?t=1231627&highlight=trim")
For the ata trim command we need to be using an SSD that supports the trim command in the firmware, (controller).

According to the following link we probably don't need to worry about it too much because if we're using an OCZ SSD with an indilinx controller it's already taken care of. The indilinx controller will do the job by itself without waiting to be told, [Indilinx firmware cleans dirty SSDs, restores performance while idle]("http://www.engadget.com/2009/08/10/indilinx-firmware-cleans-dirty-ssds-restores-performance-while/"). 
We would need to check if we have the right firmware update for that to work.

EDIT: more googling has turned up these two links which you might find interesting,  
[Linux ATA Trim support]("http://old.nabble.com/Linux-ATA-Trim-support-td23421821.html") - nabble, and [Trim function works well on Linux/Ubuntu 9.10 64-bit]("http://communities.intel.com/thread/8481;jsessionid=FC1F17EA74B7C955F513FC5FCC070542.node5COMS?tstart=0") - Intel support community

EDIT: Here's some more recent news, [Linux 2.6.33 Kernel Released]("http://ohioloco.ubuntuforums.org/showthread.php?t=1415272") - Ubuntu Web Forums, Lucid Lynx discussion

EDIT: Thread: [wiper.sh discussion thread (Linux TRIM tool)]("http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-%28Linux-TRIM-tool") - OCZ Forums

EDIT: [DiskTRIM]("http://disktrim.sourceforge.net/")  & [DiskTRIM Download]("http://sourceforge.net/projects/disktrim/") - sourceforge

---

### Post by Herman on 2010-02-27
> is it not necessary to run also update-grubNo, we don't have to because we used a different command instead, which does the same job, 'grub-mkconfig -o /boot/grub/grub.cfg'.

The 'update-grub' command is more well known, and is easier to type, but the 'grub-mkconfig' command is a slightly better command because it's much more versatile.
I like to make people aware of the grub-mkconfig command and that's the one I prefer to use myself whenever the occasion arises.

---

### Post by Herman on 2010-02-27
[LIST]
[*]To use DiskTRIM we first need to have wiper.sh installed in our system. DiskTRIM won't work without it.
[*]Wiper.sh does not come in DiskTRIM, but instead comes in the newest versions of hdparm.
[*]Ubuntu does not seem to have the aforementioned recent versions of hdparm in the repos so we need to download a tar.gz file and install it the old fashioned way.
[/LIST]
Download link for hdparm: [http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/)

How to install hdparm: [COLOR=black][http://articles.techrepublic.com.com/5100-10878_11-5031573.html](http://articles.techrepublic.com.com/5100-10878_11-5031573.html)[/COLOR]
EDIT: See [post #43 in this thread]("http://ubuntuforums.org/showpost.php?p=8927002&postcount=43") for a the way i think is the best way to install hdparm.

How to run DiskTRIM: Thread: [DiskTRIM - Automated graphical user interface for wiper.sh ]("http://www.ocztechnologyforum.com/forum/showthread.php?64684-DiskTRIM-Automated-graphical-user-interface-for-wiper.sh")- OCZ Forums

EDIT: [COLOR=Red]WARNINGS: This is experimental software that is not yet included in the official Ubuntu Repositories, so don't blame me or Ubuntu if anything bad happens.
Be sure to read all instructions and all other warnings and back up your data.
[/COLOR]

---

### Post by Herman on 2010-02-27
**Benchmarking**

In case you missed it there's a nice little script by b2bde4 for benchmarking read speeds, the link to the page it's on is somewhere in the other links I already posted. 
To make it easier to find, here is the URL, [http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=396928#post396928](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=396928#post396928)

I also like bonnie++, which is available from the approved Ubuntu Repositories.
```
sudo apt-get install bonnie++
```

---

### Post by Herman on 2010-02-28
**Before** running DiskTRIM (which runs wiper.sh)
```
herman@ocz-lynx:~/Software$ sudo ./benchmark.sh /dev/sda
[COLOR=Blue][block_size][%][read_speed]
Graph limit: 300MB/s
Test file: 100MB

   [2kB][==                            ][24MB/s]
   [4kB][====                          ][42MB/s]
   [8kB][======                        ][63MB/s]
  [16kB][========                      ][86MB/s]
  [32kB][===========                   ][114MB/s]
  [64kB][============                  ][128MB/s]
 [128kB][============                  ][129MB/s]
 [256kB][=============                 ][131MB/s]
 [512kB][=============                 ][131MB/s]
[1024kB][=============                 ][131MB/s]
[2048kB][=============                 ][131MB/s]
[4096kB][=============                 ][131MB/s]
[8192kB][=============                 ][132MB/s][/COLOR]

```**After** running DiskTRIM (which runs wiper.sh)
```
herman@ocz-lynx:~/Software$ sudo ./benchmark.sh /dev/sda
[COLOR=Red][block_size][%][read_speed]
Graph limit: 300MB/s
Test file: 100MB

   [2kB][==                            ][24MB/s]
   [4kB][====                          ][42MB/s]
   [8kB][======                        ][63MB/s]
  [16kB][========                      ][86MB/s]
  [32kB][===========                   ][115MB/s]
  [64kB][============                  ][128MB/s]
 [128kB][=============                 ][130MB/s]
 [256kB][=============                 ][131MB/s]
 [512kB][=============                 ][132MB/s]
[1024kB][=============                 ][131MB/s]
[2048kB][=============                 ][131MB/s]
[4096kB][=============                 ][132MB/s]
[8192kB][=============                 ][134MB/s][/COLOR]

```Not as much difference as I was hoping in the read speeds.

The results shown here are not as good as the results posted in OCZ forums for the same test, maybe it's because I was in a hurry when I installed and didn't use any special partition and file system alignment tweaks, I'm not sure.

EDIT: Maybe it's showing me I have some other kind of hardware limitation and it's hitting a wall at around 134MB/s. That would be unfortunate since I purchased the motherboard I'm using specially to suit the SSD drive's SATAII interface and the motherboard is advertised as SATAII capable.

---

### Post by Herman on 2010-02-28
**Before** running DiskTRIM (which runs wiper.sh)
```
[COLOR=Blue]herman@ocz-lynx:~/Software$ bonnie++ -d /tmp/bench/ -s 4096 -m OZC-Vertex
Writing a byte at a time...done
Writing intelligently...done
Rewriting...done
Reading a byte at a time...done
Reading intelligently...done
start 'em...done...done...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
OZC-Vertex       4G   **525**  98 **22043**   2 **19977**   2  **1813**  99 **151905**   8  **2126**  10
Latency             15784us    5523ms    2241ms    7829us   12639us    3669us
Version  1.96       ------Sequential Create------ --------Random Create--------
OZC-Vertex          -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               432us    2318us     742us     167us     108us      95us
1.96,1.96,OZC-Vertex,1,1267315786,4G,,525,98,22043,2,19977,2,1813,99,151905,8,2126,10,16,,,,,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,15784us,5523ms,2241ms,7829us,12639us,3669us,432us,2318us,742us,167us,108us,95us[/COLOR]
```**After** running DiskTRIM (which runs wiper.sh)
```
[COLOR=Red]herman@ocz-lynx:~$ bonnie++ -d /tmp/bench/ -s 4096 -m OZC-Vertex
Writing a byte at a time...done
Writing intelligently...done
Rewriting...done
Reading a byte at a time...done
Reading intelligently...done
start 'em...done...done...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
OZC-Vertex       4G  ** 542**  99 **106074**  13 **57630**   9  **1628**  97 **223982**  16  **3540**  43
Latency             15038us    1043ms     389ms   32032us    3742us    3010us
Version  1.96       ------Sequential Create------ --------Random Create--------
OZC-Vertex          -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency              1327us     645us     679us     174us      24us      45us
1.96,1.96,OZC-Vertex,1,1267346928,4G,,542,99,106074,13,57630,9,1628,97,223982,16,3540,43,16,,,,,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,15038us,1043ms,389ms,32032us,3742us,3010us,1327us,645us,679us,174us,24us,45us[/COLOR]
```The difference I was hoping for is apparent in the bonnie++ output.

EDIT: I'm reviewing how to use bonnie++ properly, I think I made some mistakes with my testing methods so the above results may be misleading. I'll leave them there for now anyway ...

Booting seems pretty quick too but I haven't timed it yet.

---

### Post by Herman on 2010-02-28
It's hard to tell if there's any improvement in the boot speed because the boot speed is already pretty quick and I'm probably just testing my own reflexes to see how fast I can hit 'start' and 'stop' in the stopwatch program I'm using from my other Ubuntu computer beside the one with the SSD in it.  :D

---

### Post by gabrielcik on 2010-03-02
Thank you for all these info.

I tried system monitor and it give me this result:

Timing cached reads = 610.66 MB/sec
Timing buffered disk reads =  82.38 MB/sec
(i don't know if it is a true benchmark)

As for booting, it is quite fast, a couple of seconds from grub to the login, but then it takes about 11-15 seconds to show the desktop. (i have awn at the startup).

---

### Post by Herman on 2010-03-03
I found a thread where it is mentioned that ATA TRIM will be available in the Linux 2.6.33 kernel, [Linux 2.6.33 Kernel Released]("http://ubuntuforums.org/showthread.php?t=1415272&highlight=trim") - Ubuntu Web Forums.
I have the vmlinuz-2.6.32-10-generic kernel here at the moment and trim is working fine by using DiskTRIM, although I did need to install software that's not yet in the repositories to achieve that. I presume the posters in that thread mean we won't need to install any extra software.
Common sense tells me that it will still need to be enabled in the firmware of the SSD though first before the kernel will be able to do anything. 

I had to flash my OCZ drive with firmware updates to try to get mine to work with DiskTRIM.
First I tried the 1.41GC firmware update, which is available as an .iso file from OCZ. DiskTRIM still couldn't do anything with 1.41GC, probably I should have chosen Vertex 1.4 TRM update instead, for operating systems with TRIM enabled, (only Windows 7 according to the download page, so I didn't install that one).
 GC stands for 'Garbage Collection', probably that's the firmware the article I linked to in an earlier post was about -  [Indilinx firmware cleans dirty SSDs, restores performance while idle]("http://www.engadget.com/2009/08/10/indilinx-firmware-cleans-dirty-ssds-restores-performance-while/"). I probably could have left well enough alone with the 1.41GC firmware.
Instead I flashed with the 1.5FW (firmware update) from OCZ in order to eventually get DiskTRIM working properly.

There will be all kinds of other brands of SSD drives out there and it will be up to the owners of the various hardware to shop for new SSD drives that support TRIM in their firmware or at least have flashable firmware if they want to get ATA TRIM to work even with added softwares or with some kind of inbuilt (automatic I presume) kernel support.

It's nice to think I'm doing my best for my nice hardware. 
At the end of all that I'm still playing around trying to learn more about how to benchmark with bonnie++ to see if I can prove whether it really made a lot of difference to my already fast enough SSD drive's performance.   :D
I'm sure it has helped and I'd like to be put some numbers to it with confidence that I'm using the benchmarking software correctly.

---

### Post by Herman on 2010-03-04
To get DiskTRIM to start automatically at every boot-up, we just need to add it to 'Start-up Applications'.

1. Go 'System'-->'Preferences'-->'Startup Applications', to open the Startup Applications Preferences dialog.
2. Click the 'Add' button for the 'Add Startup Program dialog.
3. Fill in the fields - 
   (i) Name: DiskTRIM
   (ii) Command: /usr/bin/DiskTRIM
   (iii) Comment: DiskTRIM
4. Click 'Add'
5. Click 'Close' and reboot to make sure it works. :D

EDIT: This didn't turn out to be the best idea because when it came time for DiskTRIM to run wiper.sh for me, it gave me an error message to say it could not run wiper.sh because it didn't have root preveledges, and recommended me to use a sudo command and run wiper.sh myself from a terminal. 
I just closed DiskTRIM and reopened it again. I was asked for my password to reopen it, then I clicked the 'manual trim' button at the bottom right in the status tab, which ran wiper.sh for me.
Maybe the DiskTRIM programmer will add more code to a future version to get it to ask the user to type a password when it's time to run wiper.sh, but for now maybe we don't really need to add it to our startup programs. I'll leave the information here anyway.

---

### Post by gabrielcik on 2010-03-04
Hello,

I have noticed that inside synaptic is present a version of hdparm (ver. 9.15) but seems there is not wiper inside it.

If i install as described the last version of hdparm, what will happen to the one present in synaptic, will i have two versions installed in the same time?

I have also noticed that is possible to download only wiper-2.5.tar.gz, maybe i can only install this package, if yes how?

thanks

---

### Post by Herman on 2010-03-04
:KS How did you find wiper-2.5.tar.gz?

Or more importantly, _where_ did you find it? (URL please).

I searched and searched for wiper.sh with all the combinations of search terms I could think of and and I kept finding myself back at the DiskTRIM page at sourceforge, it almost drove me crazy before I learned it comes included in hdparm-9.27. :D

DiskTRIM is very nice and I can recommend it, but really you can get away with just wiper if you prefer. DiskTRIM keeps track of disk IO and time since the SSD was last trimmed, and runs wiper for you when needed.

If you want to run wiper.sh manually, it's up to you. Probably you just need to right-click on the tar.gz and click: 'extract here', or you can use the traditional command for extracting a tar.gz file,
```
tar -xzvvf wiper-2.5.tar.gz
```I copied mine to /sbin in order for DiskTRIM to find it there.
```
sudo cp wiper.sh /sbin/wiper.sh
```To start it try a command something like this```
/sbin/wiper.sh /dev/sda1
```Where: /dev/sda1 is your partition, if not then replace '/dev/sda1' with something else, according to the resulst from 'sudo fdisk -lu', ot 'sudo blikd', or GParted.

If it doesn't work then try making sure it's executable with,
```
sudo chmod 755 /sbin/wiper.sh
```It might be possible that you'll be able to do the same thing easier by double-clicking on the script in your home directory and clicking 'run in terminal', but I'm not sure. Most scripts can be started like that and sometimes I'm lazy. 
It's useful to learn the command line though, and well worth the extra effort for the skills you will acquire.

---

### Post by gabrielcik on 2010-03-05
Here is the link:
[http://sourceforge.net/projects/hdparm/files/](http://sourceforge.net/projects/hdparm/files/)

At the bottom of the file list there is: wiper-2.5.tar.gz
[http://sourceforge.net/projects/hdparm/files/wiper-2.5.tar.gz/download](http://sourceforge.net/projects/hdparm/files/wiper-2.5.tar.gz/download)


As for me there is not any problem to use hdparm, but since it is already installed i don't want to create some conflict between these 2 versions (maybe i can simply uninstall the previous one...)

btw, can i run wiper even if the partition is mounted and in use?

Thank you for the help:)

---

### Post by Herman on 2010-03-05
:D Thank you for those links, they will probably be useful to someone.
> I have noticed that inside synaptic is present a version of hdparm (ver. 9.15) but seems there is not wiper inside it.No, I didn't expect it to. 
The maintainers of the official Ubuntu do a wonderful job. One of the main reasons why we would choose Ubuntu compared with some other distro is because of the hard work these good people do for us, making sure new software is safe and compatible with every other program before adding it to the official Ubuntu repositories.
However, I imagine they're already working as hard as they can. Probably they will update our hdparm to a newer version with wiper.sh in it sometime soon.
We just need to be patient and remember that there are lots of other people who want all kinds of other things at the same time. 
I think SSD drives are becoming more and more popular but right now we're in the minority so we'll just have to fend for ourselves a little until others catch up with us. 
> As for me there is not any problem to use hdparm, but since it is already installed i don't want to create some conflict between these 2 versions (maybe i can simply uninstall the previous one...)You are right to be cautious. 
In my case I just installed the newer version of hdparm  from a tar.gz file using the old fashioned commands and I was lucky. Everything turned out okay for me (this time, at least as far as I know so far). I didn't bother uninstalling the previous one, I just went right ahead and installed the newer version. Somehow Ubuntu seems to be smart enough to know which one to use. The new version turned up in the list in synaptic package manager, after I installed it, I checked. :)

Since you can get wiper.sh there's probably no need to install the newer hdparm and it's probably best to wait for it to be given to you in an update.
I'm not sure, back up your data first to be safe in case wiper.sh needs something in the newer hdparm.

---

### Post by Herman on 2010-03-05
> btw, can i run wiper even if the partition is mounted and in use?:D Good question.
It seems odd that we can run wiper.sh in a running operating system's own file system while the operating system is booted and in use, given that other kinds of file system and hard disk type of maintenance tasks require working from a Live CD on an unmounted file system. 
I don't understand the mechanics of TRIM, all I know is it seems to be working fine for me and I'm just running it in the operating system's own partition while the operating system is running. 
No unmounting seems to be required.

Here's an example of the feedback from DiskTRIM's log,
```
Start TRIM operation: 2010-03-06 04:11:55

>/sbin/wiper.sh  --commit --verbose /dev/sda1
 
wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord. 
rootdev=/dev/sda1 rdev=/dev/sda1 
fsmode2: fsmode=read-write 
/: fstype=ext4 
freesize = 48911520 KB, reserved = 489115 KB 
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /). 
 
This operation could silently destroy your data.  Are you sure (y/N)? y 
Creating temporary file (48422405 KB)..  
Syncing disks..  
Beginning TRIM operations.. 
get_trimlist=/sbin/hdparm --fibmap WIPER_TMPFILE.1849 
 
/dev/sda: 
trimming 96844816 sectors from 1646 ranges 
succeeded 
Removing temporary file.. 
Syncing disks..  
Done. 

TRIM operation stopped: 2010-03-06 04:12:08
```I don't know why it says 'stopped' at the end rather than 'completed' or 'finished', but I think it has been completed successfully, at least I hope so. It always says that.  :)

---

### Post by gabrielcik on 2010-03-05
Hello,

Today, I have finally installed everything was required and trimmed the ssd...

At the end, I installed the whole hdparm... since as far as i understood wiper doesn't work with the older versions of hdparm.

I had also to install a package called gawk.

It was not possible to uninstall the previous version since it would remove several other packages probable needed by the system.

thx

---

### Post by psusi on 2010-03-05
> **gabrielcik said:**
> Hello,

I want to use the ext4 since i had problems with ext2.

I have a sdd and i heard it would be better to remove the journaling...

I found on the net this command for to remove it:
sudo tune2fs -O ^has_journal /dev/sdXN

is it safe? or maybe it is better to leave it on?

Thank you

Turning off journaling is not a good idea since it leaves your filesystem vulnerable to corruption if you crash.

> **dabl said:**
> You _need_ to have the filesystem checked periodically, and especially after you lose power.  It is not a bad thing that ext2 requires a filesystem check after a hard power-off.  ext3 and ext4 also require a fsck after hard power-off.

No, you don't; that's the whole point of journaling.  As long as you have the journal, you DON'T need a fsck after a crash, or ever really, unless you think something went horribly wrong and corrupted your filesystem.

> **Herman said:**
> 
According to the following link we probably don't need to worry about it too much because if we're using an OCZ SSD with an indilinx controller it's already taken care of. The indilinx controller will do the job by itself without waiting to be told, [Indilinx firmware cleans dirty SSDs, restores performance while idle]("http://www.engadget.com/2009/08/10/indilinx-firmware-cleans-dirty-ssds-restores-performance-while/"). 
We would need to check if we have the right firmware update for that to work.


That's exactly what the TRIM command is for; to tell the drive what blocks are free so that it CAN clean them.  This article seems to be misleading in that it suggests that their firmware does it by magic rather than with TRIM.

---

### Post by Herman on 2010-03-05
:D Ah, okay, very good, I'm happy you are successful.

:D  Meanwhile, my SSD's read speed test results have improved,
```
herman@ocz-lynx:~/Software$ sudo ./benchmark.sh /dev/sda1
[sudo] password for herman: 
[block_size][%][read_speed]
Graph limit: 300MB/s
Test file: 100MB

   [2kB][==                            ][24MB/s]
   [4kB][====                          ][42MB/s]
   [8kB][=====                         ][57MB/s]
  [16kB][======                        ][65MB/s]
  [32kB][============                  ][121MB/s]
  [64kB][=================             ][173MB/s]
 [128kB][===================           ][190MB/s]
 [256kB][===================           ][197MB/s]
 [512kB][====================          ][206MB/s]
[1024kB][====================          ][206MB/s]
[2048kB][====================          ][203MB/s]
[4096kB][====================          ][209MB/s]
[8192kB][====================          ][206MB/s]

```

---

### Post by Herman on 2010-03-05
:D Hello psusi, welcome and thank you for joining this thread. 

 I agree with you most emphatically on this point.
> Turning off journaling is not a good idea since it leaves your filesystem vulnerable to corruption if you crash.


---

### Post by Herman on 2010-03-05
I beg to differ with you on your opinion about whether or not to run a file system check after a crash or hard power-off.

> Quote:
                                                                      Originally Posted by **dabl**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8880087#post8880087")                 
                 *You _need_ to have the filesystem checked periodically, and especially after you lose power. It is not a bad thing that ext2 requires a filesystem check after a hard power-off. ext3 and ext4 also require a fsck after hard power-off.*
                                 
No, you don't; that's the whole point of journaling. As long as you have the journal, you DON'T need a fsck after a crash, or ever really, unless you think something went horribly wrong and corrupted your filesystem.Quoted from, [Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html"), which I think I linked to earlier in this thread,
> **Q: If a system shutdown hard, even with journaling is it at all necessary to run e2fsck? **

Theodore Ts'o said: 
  [I]It's best to just always run e2fsck. [...]
E2fsck will run the journal automatically, and if the filesystem is otherwise clean, it skip doing a full filesystem check.
If the filesystem is not clean (because during the previous run the kernel noticed some filesystem inconsistencies), e2fsck will automatically do a full check if it is necessary.
If you have multiple disks, fsck will run multiple e2fsck processes in parallel, thus speeding up your boot sequence than if you let the kernel replay the journal for each filesystem when it tries to mount it, since then the journal replays will be done sequentially, instead of in parallel.[/I]
EDIT: Well, I guess after reading that again, it looks like we should run e2fsck and let e2fsck decide whether a full check is necessary or not,
> [I]E2fsck will run the journal automatically, and if the filesystem is otherwise clean, it skip doing a full filesystem check.
If the filesystem is not clean (because during the previous run the kernel noticed some filesystem inconsistencies), e2fsck will automatically do a full check if it is necessary.[/I]
EDIT: So you're right, it seems to be a matter of interpretation.
The way I read it, the first line ' *It's best to just always run e2fsck. [...] ' *seems to be the most important line.
However, if we emphasize the line '*E2fsck will run the journal automatically, and if the filesystem is otherwise clean, it skip doing a full filesystem check.',* then you are correct. :)

---

### Post by Herman on 2010-03-05
> Quote:
                                                                      Originally Posted by **Herman**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8891866#post8891866")                 
                 [I]According to the following link we probably don't need to worry about it too much because if we're using an OCZ SSD with an indilinx controller it's already taken care of. The indilinx controller will do the job by itself without waiting to be told, [Indilinx firmware cleans dirty SSDs, restores performance while idle]("http://www.engadget.com/2009/08/10/indilinx-firmware-cleans-dirty-ssds-restores-performance-while/"). 
We would need to check if we have the right firmware update for that to work.[/I]
                                 
That's exactly what the TRIM command is for; to tell the drive what blocks are free so that it CAN clean them. This article seems to be misleading in that it suggests that their firmware does it by magic rather than with TRIM.Thank you, yes , that makes sense, I guess that's probably right. 
So maybe I should have stuck with the 1.41GC firmware update and let that care care of my OCZ SSD automatically in the background, that would have been the easiest and most convenient way of doing things. 

Thanks for all your comments. :D

---

### Post by Korkskruv on 2010-03-05
> **Herman said:**
>  Good question.
It seems odd that we can run wiper.sh in a running operating system's own file system while the operating system is booted and in use, given that other kinds of file system and hard disk type of maintenance tasks require working from a Live CD on an unmounted file system.
I don't understand the mechanics of TRIM, all I know is it seems to be working fine for me and I'm just running it in the operating system's own partition while the operating system is running.
No unmounting seems to be required.

That's because wiper.sh will create a large temporary file on the mounted file system. This file will then be used to decide which blocks is available for trimming. Not every file system is able to create an empty file (without filling it) and then report back exactly which sectors on the block device that the file maps to.

> **Herman said:**
>  Here's an example of the feedback from DiskTRIM's log,
[...]
I don't know why it says 'stopped' at the end rather than 'completed' or 'finished', but I think it has been completed successfully, at least I hope so. It always says that. 

No reason at all. It did complete successfully because that's the line printed when DiskTRIM detects that the tread running wiper.sh has terminated. Finished (or completed) might sound better though.

---

### Post by Korkskruv on 2010-03-05
> **Herman said:**
> Thank you, yes , that makes sense, I guess that's probably right. 
So maybe I should have stuck with the 1.41GC firmware update and let that care care of my OCZ SSD automatically in the background, that would have been the easiest and most convenient way of doing things. 

Thanks for all your comments. :D
1.5 equals 1.4 (with trim) AND 1.41 (with garbage collection). That's why there's only one version now. ;)

---

### Post by Herman on 2010-03-05
> 1.5 equals 1.4 (with trim) AND 1.41 (with garbage collection). That's why there's only one version now. :wink:Oh, okay, thanks, that's good to know. 


About wiper.sh (and DiskTRIM) being able to run in a running operating system while the file system is mounted:
> That's because wiper.sh will create a large temporary file on the mounted file system. This file will then be used to decide which blocks is available for trimming. Not every file system is able to create an empty file (without filling it) and then report back exactly which sectors on the block device that the file maps to.
:idea: Aha! Thank you for that information too, Korkskruv.


On DiskTRIM log reporting 'stopped' after completing a TRIM operation:
> No reason at all. It did complete successfully because that's the line printed when DiskTRIM detects that the tread running wiper.sh has terminated. Finished (or completed) might sound better though. Yes, it would be nice to be re-assured that the task has been completed successfully and isn't stuck or aborted. :)

Thanks for taking the time to clear up those points. 

Hey, are you the developer of DiskTRIM or wiper.sh, or have you something to do with OCZ?  Because if so, thanks for all your work, us Ubuntu users are really lucky to have you guys around. Even if you're not, at least thanks for stopping by here and making the effort of sharing your knowledge. :D

---

### Post by Korkskruv on 2010-03-06
I'm the developer of DiskTRIM. :)
wiper.sh was developed by the same person who created hdparm.

---

### Post by gabrielcik on 2010-03-06
Hello,

> 1.5 equals 1.4 (with trim) AND 1.41 (with garbage collection). That's why there's only one version now.

so if i have firmware 1.5, i don't need to trim with wiper, is it true? i thought i had to wait untill the next realese of ubuntu.

A last question, do u know how to remove the previous version of hdparm (installed by default on Ubuntu) if i have already installed manually the last version of the same program?

If i run hdparm from therminal i get version 9.27 but if i check inside synaptic i still have the old package 9.15.

Thank you

---

### Post by Herman on 2010-03-06
> I'm the developer of DiskTRIM. :smile:
wiper.sh was developed by the same person who created hdparm.
:D Cool! You guys rock! :guitar:

---

### Post by Korkskruv on 2010-03-06
> **gabrielcik said:**
> Hello,

so if i have firmware 1.5, i don't need to trim with wiper, is it true? i thought i had to wait untill the next realese of ubuntu.

A last question, do u know how to remove the previous version of hdparm (installed by default on Ubuntu) if i have already installed manually the last version of the same program?

If i run hdparm from therminal i get version 9.27 but if i check inside synaptic i still have the old package 9.15.

Thank you
Trim works much better than garbage collection and yields perfect results. Garbage collection tries to rearrange data internally to prepare free write blocks in advance. Because the controller can't read the file system it doesn't know which blocks contains real data. That's why the effect of garbage collection in most cases will be limited. At worst it's a wasted effort, at best it will yield moderate results with a temporary speed up at best.

Sadly, trim won't be supported by Ubuntu until the October release because of the kernel used in the next release is insufficient.

You only need to trim the disk once in a while. About once each week is enough unless you have lots of disk activity.

When you manually installed hdparm you replaced the originally binary file. Don't worry about the package numbering. It won't create any problems. If you receive an updated version of the package in the future your customary binary will be replaced. The hdparm package probably won't be updated until you start the upgrade for Ubuntu 10.04 (Lucid Lynx).

---

### Post by Herman on 2010-03-06
> A last question, do u know how to remove the previous version of hdparm (installed by default on Ubuntu) if i have already installed manually the last version of the same program?

If i run hdparm from therminal i get version 9.27 but if i check inside synaptic i still have the old package 9.15.Probably either of the following two commands will work, you can choose one or the other,
sudo apt-get remove, 
```
sudo apt-get remove hdparm
```or sudo dpkg --remove,
```
dpkg --remove hdparm
```The problem is, I don't know if either of those will give you a choice about which hdparm to remove.
Here's the link I got those from, [The Debian GNU/Linux FAQ - The Debian *package* management tools.]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&ved=0CAkQFjAA&url=http%3A%2F%2Fwww.debian.org%2Fdoc%2FFAQ%2Fch-pkgtools.en.html&rct=j&q=dpkg+remove+package&ei=_s2SS-rlPNWgkQXF1MmHDQ&usg=AFQjCNHNvv4AqB63Iguxf23ypsiZbB2J4w&sig2=cgx3q7rIRaOw1ms2HOgpXQ")

---

### Post by psusi on 2010-03-06
It will remove the package that is installed, of which there is only one version.  If you want to then build your own version from source you can do that after.

---

### Post by Herman on 2010-03-06
I decided to try to find out exactly what is the very best way to install hdparm from a tar.gz file and explain it every step in case it helps anyone new following this thread.
I have lots of Ubuntu installations so I went to a different Ubuntu which has not yet been upgraded with hdparm-9.27, 

**1.** I read the following web pages, 
Ubuntu Documentation > Community Documentation >   [CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo?action=fullsearch&context=180&value=linkto%3A%22CompilingEasyHowTo%22")  ... and ... [How to install Linux / UNIX *.tar.gz tarball files]("http://www.cyberciti.biz/faq/install-tarballs/") - NixCraft

**2**. I made a list of only the commands I think we need and left out the ones we probably can skip.

**3.** I ran those commands in a different computer to check and make sure they work.

**4.** Here are the commands,
To install software for installing other software,
```
sudo apt-get install build-essential checkinstall
```To change directories into the one where my downloaded tar.gz file happens to be located,
```
cd Downloads
```Now here's the command for extracting the files out of the tar file,
```
tar xzvf hdparm-9.27.tar.gz
```We should have a new folder named 'hdparm-9.27', and now we want to go inside it,
```
cd hdparm-9.27/
```Next we assemble the software,
```
make
```Now we install it.
```
sudo checkinstall
```NOTE: I received the following,
```
checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
```We can make anything up here, so I typed: 
```
>> hdparm is for managing firmware in hard disk drives and Solid State Drives                               
>> 
``` ... and I pressed ENTER twice ....

Then I saw,
```
*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@amd-karmic ]
1 -  Summary: [ hdparm is for managing firmware in hard disk drives and Solid State Drives ]
2 -  Name:    [ hdparm ]
3 -  Version: [ 9.27 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ hdparm-9.27 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ hdparm ]

Enter a number to change any of them or press ENTER to continue:

``` ... and I pressed ENTER to continue ...

And finally I saw,
```
Installing with make...Installing with install...

========================= Installation results ===========================
if [ ! -z  ]; then install -m 755 -d  ; fi
if [ ! -z /sbin ]; then install -m 755 -d /sbin ; fi
if [ ! -z /usr/share/man ]; then install -m 755 -d /usr/share/man ; fi
if [ ! -z /usr/share/man/man8/ ]; then install -m 755 -d /usr/share/man/man8/ ; fi
if [ -f /sbin/hdparm ]; then rm -f /sbin/hdparm ; fi
if [ -f /usr/share/man/man8/hdparm.8 ]; then rm -f /usr/share/man/man8/hdparm.8 ;\
    elif [ -f /usr/man/man8/hdparm.8 ]; then rm -f /usr/man/man8/hdparm.8 ; fi
install -D hdparm /sbin/hdparm
if [ -d /usr/share/man ]; then install -m 644 -D hdparm.8 /usr/share/man/man8/hdparm.8 ;\
    elif [ -d /usr/man ]; then install -m 644 -D hdparm.8 /usr/man/man8/hdparm.8 ; fi

======================== Installation successful ==========================

Copying documentation directory...
./
./README.acoustic
./Changelog
./TODO
grep: /var/tmp/tmp.FkZm5SMYrw/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/herman/Downloads/hdparm-9.27/hdparm_9.27-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r hdparm

**********************************************************************

```:D And now the latest hdparm-9.27 is installed in my system and comes up both in Synaptic Package Manager as the installed program and also in terminal.

---

### Post by Herman on 2010-03-08
The partition I made in my OCZ SSD wasn't aligned with the erase blocks because I was in a hurry the day I installed Ubuntu Lucid Lynx in this SSD.

Now that my operating system is already installed it's too late to change things ... or is it? ...

Today I decided to make a dd backup of my entire operating system to a file in another disk. Next I set a new MBR in my SSD with a special partition table which will align the file system up on the flash memory's erase block boundaries for best performance and to prolong the lifespan of the SSD. Then I copied the entire operating system back into the SSD drive again.

It sounds simple enough, but there are a few tricks to know about before starting this kind of an operation and a few things I learned along the way that I can pass on to others who might be considering doing something similar.

1. Partition editing,
Working from a Live CD or Ubuntu in a USB, (I prefer the latter if possible), I resized the Ubuntu partition in the SSD drive to a smaller size.
The reason for doing so is that we can use the dd command to copy a partition to a larger partition, but not the other way around. The dd command copies exactly what's on the disk and that includes the empty spaces. I'm going to be reducing the size of my SSD drive's partition by a few sectors when I set the new partition table. That means if I don't reduce the size of the backup when I start, I'm not going to be able to restore it later. It simply won't fit. I resized mine almost as small as it would go using GParted.

2. The dd command,
Be very, very careful with the dd command. It can be dangerous in the wrong hands, that's why Partimage and clonezilla or good. Some people might prefer to use one of those programs to run commands for them to be safer. I'm going to run the dd command myself to save time.
```
sudo dd if=/dev/sda1 of=/media/OCZ_SAVER/ocz.image bs=4096 conv=notrunc,noerror

```This command will copy my Ubuntu partition sda1 in the SSD, turn it into a file and put it in the file system I have mounted as /media/OCZ_SAVER, which is in a special partition I made for the purpose, (optional).

There's a reason why I decided to make it into a file instead of just copying it to the other partition as is. 
The file system UUID number will be copied perfectly by the dd command, and having another exact copy of the same file system causes issues with GRUB and booting, turning it into a file avoids those problems.

3. Next I created the new partition table in my SSD with fdisk by following this thread from OCZ Web Forums, [Linux - Tips, tweaks and alignment ]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment"). You may need to register at OCZ Web Forums to see that link properly, I'm not sure.
```
herman@ocz-lynx:~$ sudo fdisk -lu
[sudo] password for herman: 

Disk /dev/sda: 64.0 GB, 64023257088 bytes
**[COLOR=Blue]32 heads, 32 sectors/track[/COLOR]**, 122114 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
**[COLOR=Blue]Sector size (logical / optimal IO): 512 bytes / 512 bytes[/COLOR]**
Disk identifier: 0x389fe78f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            **[COLOR=Blue]1024[/COLOR]**   125044735    62521856   83  Linux
```4. With the start of the partition now set to sector number 1024 rather than the traditional sector number 63, I then copied the entire operating system back into the SSD by reversing the dd command,
```
sudo dd if=/media/OCZ_SAVER/ocz.image of=/dev/sda1 bs=4096 conv=notrunc,noerror
```5. I used GParted again to resize it to fill up the entire disk and give it a file system check just to make sure everything will be right.

6. I reinstalled GRUB2, that's a mandatory step. Here's a link about how to do that,                          [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900").

7. Finally I'm going to try aligning the ext4 file system to erase blocks, also as mentioned in OCZ Web Forums, [Linux - Tips, tweaks and alignment ]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment"). 
The command given in the link is the mke2fs command, for making a new ext file system. That means it's something to be done before the operating system is installed. In my situation, I need to tweak my existing file system, with the operating system already installed in it. Luckily with the ext series file systems we can easily tweak the file system while it's in place simply by using the tune2fs command. 
```
 sudo tune2fs -E stripe_width=128 /dev/sda1
```8. Reboot and enjoy.

NOTES:
(a) For some people it might be quicker to just re-install instead of using the dd command or some program to make a backup and restore it. Installing Ubuntu is pretty quick. It's just the updates after that and any extra tweaks, customizations and settings that take time. (But hey, that's part of the fun!).

(b) There's a secondary benefit to following this procedure.  I didn't bother deleting the file I made in the other disk when I was finished. It can remain there as a backup copy of my entire operating system in case some kind of disaster happens some day. I can restore Ubuntu in my SSD drive fairly quickly.

---

### Post by Herman on 2010-03-09
:D  It used to be as fast as lightning.

Now it's as fast as greased lightning. 

My new boot time is just 6.09 seconds according to bootchart, you can see it in this page, [**Re: Post your Lucid bootcharts or boot times!**]("http://ubuntuforums.org/showthread.php?t=1343305&page=20")

Thanks to Ubuntu Lucid developers, hdparm & wiper.sh developer Mark Lord and DiskTRIM developer Korkskruv and others from OCZ for the software, firmware and hardware that did that for me, Theodore Ts'o  for the ext4 file system and gabrielcik for getting me interested in doing all this tweaking. You guys rock!  \\:D/

UPDATE: It keeps getting faster, 5.35 seconds now.

---

### Post by Herman on 2010-03-14
In case anyone's interested, I found this interesting blog, [Mount options to improve ext4 file system performance]("http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/")  - smartlogicsolutions.com

I did,
```
sudo tune2fs -o journal_data_writeback /dev/sda1
``````
gksudo gedit /etc/fstab
``````
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdi1 during installation
UUID=51e9238e-90f1-4ef8-8a36-9c631511b3ec /               ext4    noatime,**[COLOR=Red]data=writeback[/COLOR]**,errors=remount-ro 0       1
  [COLOR=Red]**#**[/COLOR] UUID=51e9238e-90f1-4ef8-8a36-9c631511b3ec /               ext4    noatime,**[COLOR=Red]data=writeback,barrier=0,nobh[/COLOR]**,errors=remount-ro 0       1
/swapfile          none         swap       sw           0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```If you read the link you'll know what I'm talking about here.
It can boot in 4.46 seconds now. - [URL="http://ubuntuforums.org/showthread.php?t=1343305&page=21"]Re: Post your Lucid bootcharts or boot times!
[/URL]

---

### Post by ShadowDragon on 2010-03-16
> **Herman said:**
> [...]I have the vmlinuz-2.6.32-10-generic kernel here at the moment and trim is working fine by using DiskTRIM, although I did need to install software that's not yet in the repositories to achieve that.
[...]

How are you sure that TRIM is working? Have you done some sort of test, like making a file -> find the associated LBA's -> read out those sectors with dd with direct flag -> remove the file -> reread those sectors and see they are empty?

Because on my drive it also seems that it worked but the test described above was a fail...

---

### Post by psusi on 2010-03-16
The drive doesn't have to erase the blocks right away when it gets a TRIM command, it just notes that it CAN erase it when it needs some space for its balancing algorithms.

---

### Post by ShadowDragon on 2010-03-16
Ehm, interesting statement, can definitely be true. So would this mean that if you don't get an error from the application you are using to TRIM the drive, you can only hope that it worked and that there was no silent error? Spooky...

---

### Post by fjf on 2010-03-17
Anyone tried the new kernel 2.6.33 with the discard mount option?.  This should activate trim automatically without those tweakings, but I've found no detailled info about it.

---

### Post by ShadowDragon on 2010-03-17
I'm having a 2.6.33 kernel option here on my system, but like I said, if the TRIM commands aren't processed immediately, then you can't inspect the drive to know if it worked or not...

---

### Post by DariusTriplet on 2010-04-11
> **Herman said:**
> :D Ah, okay, very good, I'm happy you are successful.

:D  Meanwhile, my SSD's read speed test results have improved,


I'm curious as to how you're getting those numbers.  I recently installed 10.04 on my laptop with a new 30GB OCZ Vertex, using ext4 and the tweaks outlined [here]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/"), and I'm getting numbers closer to your first chart.

I did align the drives properly (512k cylinders), and I'm using 2.6.33, so I do have TRIM support.

---

### Post by Herman on 2010-04-11
:)   Thanks for your link, [Tuning Solid State Drives in Linux]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/"), that's an interesting read. 

I paid the most attention to [OCZ web forum stickies on the subject]("http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-on-Linux-and-Apple-OSX"). 
I have elaborated on everything I did to tune my OZC SSD right here in this thread, so if you have read it you know as much as I do already. 
As far as I know, the improvement was the result from using DiskTrim to run wiper.sh which runs TRIM.

---

### Post by DariusTriplet on 2010-04-12
I'm using the following mount options with ext4 (journaling disabled):

discard,noatime,data=writeback,barrier=0,nobh

And here's my results from the script from the OCZ forums

```
shaqfu@epoch:~$ sudo ./bench.sh /dev/sda
[sudo] password for shaqfu: 
[block_size][%][read_speed]
Graph limit: 300MB/s
Test file: 100MB

   [2kB][=                             ][13MB/s]
   [4kB][==                            ][25MB/s]
   [8kB][====                          ][41MB/s]
  [16kB][====                          ][49MB/s]
  [32kB][=======                       ][72MB/s]
  [64kB][=========                     ][95MB/s]
 [128kB][===========                   ][112MB/s]
 [256kB][============                  ][123MB/s]
 [512kB][=============                 ][131MB/s]
[1024kB][=============                 ][132MB/s]
[2048kB][=============                 ][133MB/s]
[4096kB][=============                 ][134MB/s]
[8192kB][=============                 ][135MB/s]

```

Although I think my problem is my laptop's SATA 1.5Gb/s controller.  From Wikipedia:

[quote="Wikipedia"]First-generation SATA interfaces, now known as SATA 1.5 Gbit/s, communicate at a rate of 1.5 Gbit/s. Taking 8b/10b encoding overhead into account, they have an actual uncoded transfer rate of 1.2 Gbit/s (1500000000*8/10/1024/1024/8 &#8773; 143.05 MiB/s).[/quote]

Which is in line with what I'm finding.  So I'm hitting a bottleneck at my laptop's SATA controller now, instead of the drive.  It's still fantastically better than my aging 5400rpm drive, but I'm not getting the most out of my Vertex.  C'est la vie.  It's still awesome to see programs load with no wait time, though.

(EDIT) Although I'm curious as to how you're getting much higher speeds across the board.  Even if I'm capped at the top, I'm still considerably slower than your Vertex at smaller files.

---

### Post by Herman on 2010-04-12
You might need to try a few experiments of your own to see if you can optimize your SSD's performance to suit your own particular hardware.
Web pages are a good start, but they often reflect the author's opinions and impressions they have as a result of their own experiences with their hardware and may not be universal.

Some web pages which contain advise to turn swappiness to zero, and the one you liked to advises setting swappiness to 1. 
Personally, I found setting swappiness to around 10 seemed to work the best for me, or at least that's how it seems with the hardware I have.

One thing I haven't tried yet is turning of the file system journal. I have been saying for years now that it's okay to run a file system with journaling in flash memory but not too many people agreed with me. I felt so alone until I read Mr T'so's blog and then I finally felt that my opinion was vindicated.
Do you think removing the file system journal is worth it?
How much of a performance improvement do you get?

Even if you reported a small speed boost I would be reluctant to do without file system journaling. As a matter of fact only this evening when I arrived home from work my UPS was off and I couldn't get it going again. My wife told me she had a kitchen fire and ran to the power box and turned everything off at the main switch. Now my UPS won't come back on again. I know it was getting old, but it's an expensive one and I expected more from it. I'll give it a day or so to recharge the batteries and see what happens then. In the meantime, I'm thankful I have file system journaling. (By the way, the fire went out by itself. I'm happy I still have a house too). (LOL).  The moral of the story: 'You never know when things might go wrong'.

There's a lot of information to read in the links I provided throughout this thread. I did a lot of reading, thinking and experiments before I was able to get mine performing the way it is now. I agree with the author of the website you linked to that not all the informationis available in one site, (unless it's in the OCZ site). I also agree that it won't be very long before more people will be using SSD drives and not only will they be better supported, but the drives themsleves are improving all the time. Soon we won't need to do anything special to get the most out of our SSD. 
   ... although, that will be kind of sad in a way ... it's fun to dare to be different and to have a challenge and see how well we can overcome it. 
 ... but .. I suppose there will always be new challenges ...   (LOL!)

---

### Post by DariusTriplet on 2010-04-12
I'm running my SSD in a laptop that's usually on AC power, so the chance of a power outage is nil.  I'm more than certain that disabling the journal was the right call here, since I'm on a battery backup.

I was just thinking, would you be interested in working on a HOWTO for SSDs?  The biggest nightmare in setting one up is how all the information is scattered about, and so much is outdated (it's not very useful to have kernel tweaks for pre-TRIM...).  I'd be more than happy to help out, if only to save others from having to look through dozens of different sources to find the proper drive alignment, mount options, filesystem/kernel settings, etc.

(EDIT) I disabled swap in the kernel (under General Setup), so my swappiness is functionally 0.  My rationale is that my laptop is mostly an archetypical "email machine" with some general-use applications (GIMP, mplayer, Liferea), so if I ever need more than the 2GB in there, I'd likely want to shut down anyway. ;)

---

### Post by ShadowDragon on 2010-04-12
@Herman: I personally think that disabling the journal for home-usage ain't a good idea. The idea behind disabling the journal is to reduce the additional overhead for each write-instruction that is inherent with a journal. The second argument for disabling the journal is the less you write to your drive, the less erase-cycles you use.

But, SSD's don't suffer more from the journal as your HDD does. SSD's are equally sensitive to the overhead as your HDD. So if you didn't disable it on your HDD, why would you do it on your SSD? You would gain a marginal performance, so small that the user don't notice it during usage (only in syntetic benchmark) as a trade-off for loosing the safety of your journal, which you DO notice as a user.

The argument they used back in 2008-2009 was there was still uncertainty about the lifetime of SSD. With improved recyclers, maintance-algorithms and TRIM-functionality and warranties of 3 year or more, you SSD will live as long as your HDD, maybe longer. (HDD do die of usage aswell, don't forget that). So that argument for removing the journal doesn't stand eigther.

In enterprise-usage, where all performance is needed and where backups / data-integrity and etc. is handled by more advanced structures, you can ditch the safety of the log for performance, because you loose less functionality and gain more performance. But for home-usage where most user don't understand every process in there system, I would discourage for losing the safety of the log for a speed-gain you'll never notice.

---

