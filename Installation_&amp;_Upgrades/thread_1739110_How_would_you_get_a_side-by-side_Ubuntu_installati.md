---
title: "How would you get a side-by-side Ubuntu installation back into pristine shape?"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by rocksockdoc on 2011-04-25
About six months ago I installed Ubuntu 10.04 on my laptop and I was happy with the stability (over the prior Windows installation as it only killed me once in all that time when the home-directory encryption went whacko and I lost all my data). 

I was happy the next six months, with an entire new installation.

However, this week, Ubuntu pulled the Windows trick again, and chewed itself up (I think it ruined itself when I had to kill an update in progress - but that doesn't matter at this point). What mattered is that it would not recognize the USB ports (and the laptop, a Lenovo X61 doesn't have an internal disc drive) so I had to re-install the original Ubuntu 10.04 side-by-side with the old Ubuntu using my original installation disk (in order to save the data).

None of that matters much now ... what matters now is that I have, unfortunately, two side-by-side Ubuntu 10.04 installations, and with my data on the wrong side! :)

**What would you suggest I do to return this Ubuntu installation to just one operating system (and with the data protected from either the home-directory encryption bugs or the OS chewing itself up again)?**

Note: Since this is the second time Ubuntu chewed itself up on me, I'm also in need of advice as to how to partition the setup so that my data is NOT in a user directory (where the buggy encryption killed me once) nor in the OS partition (which killed me this time).

Thanks, in advance, for your helpful advice!

---

### Post by Dutch70 on 2011-04-25
Probably easier to reinstall with a separate /home. Not sure about the encryption thing.
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")
Having a separate /home will allow you to reinstall or upgrade without losing your data or settings. 
I would also use ext4 and make the swap partition equal to your physical RAM.

If you use google, you can find other tutorials for this.

---

### Post by d3v1150m471c on 2011-04-25
When you refuse to reinstall every time you botch your system it'll help you in the long run, and you'll become more familiar with preventing and fixing problems in the end. Most problems can be fixed by booting into a root terminal at the grub menu in recovery mode and reinstalling and/or reconfiguring issues. If you have trouble a lot of the people at the forums are good at pinpointing and providing solutions. Might as well take a stab at it before reinstalling, wouldn't hurt. Also, keeping regular backups is a good habit to get into.

---

### Post by Dutch70 on 2011-04-25
+1 on d3v1150m471c statement.

This link may also help you.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1735797[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1735797")

---

### Post by rocksockdoc on 2011-04-26
> **Dutch70 said:**
> Probably easier to reinstall with a separate /home.

I'm sure that's good advice; but I'm not quite sure what a "separate home" actually means. My Ubuntu installer, by default, put the user's home directory in /home/username which is the 'same' partition as the operating system.

Googling for how to install ubunto 10.04 lucid with a separate home partition, I find a few good-looking tutorials for myself and others to reference:
- [How to: Install Ubuntu 7.10 with a Separate /home Partition]("http://ubuntuforums.org/showthread.php?p=4360347")
- [Solved: Setup Separate Home Partition During Installation?]("http://ubuntuforums.org/showthread.php?t=1635346")
- [How to Create a separate /home partition in Ubuntu]("http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html")
- [Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")
- [Creating a separate home partition in Ubuntu during installation]("http://www.psychocats.net/ubuntu/installseparatehome")

[Notable quote:]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml")
> 4. The fourth choice is "Specify partitions  manually" and it is recommended ONLY for advanced users, to create  special partitions or format the hard drive with other filesystems than  the default one. But it can also be used to create a /home partition,  which is very useful in case you reinstall the whole system.

---

### Post by rocksockdoc on 2011-04-26
> **Dutch70 said:**
> I would also use ext4.

Ah. That's the kind of advice that I wouldn't otherwise know (and neither would anyone looking to this thread for advice). 

Thanks for the advice. I have no idea what ext4 is ... but googing ... I find the Wikipedia article on it:
- [Wikipedia - ext4]("http://en.wikipedia.org/wiki/Ext4")

Which starts off explaining it's some kind of file system:
> The **ext4** or **fourth extended filesystem** is a [journaling file system]("http://en.wikipedia.org/wiki/Journaling_file_system") for [Linux]("http://en.wikipedia.org/wiki/Linux"), developed as the successor to [ext3]("http://en.wikipedia.org/wiki/Ext3").In reality, the Wikipedia ext4 explanation should more appropriately be titled "a history of ext4" rather than an explanation of what ext4 is ... but reading that article, I find out:

[LIST]
[*]Linux 2.6.28 is the first stable version of ext4 (so it should be available in Ubuntu 10.04)
[*]Google uses ext4 (ummm... ok ... I'm not sure why that matters to me, a mere user)
[*]Ext4 supports large files (the numbers quoted are huge but not relevant to a mere user)
[*]It's backward compatible with ext3 and ext2 (umm, ok. But what file system do I currently have?)
[*]"An extent is a range of contiguous physical blocks" (ok ... ok ... Wikipedia ... )
[*]etc.
[/LIST]
Ok. I just finished reading the Wikipedia on ext4 and really ... I still don't know 'what' it is other than it's a file system (I guess much like FAT & NTFS). My thoughts are ... ok ... what file system did Ubuntu 'put' on my disks then?

Googling for "[what is the default ubuntu file system]("http://www.google.com/search?client=ubuntu&channel=fs&q=how+to+install+ubuntu+separate+home+&ie=utf-8&oe=utf-8#hl=en&sugexp=ldymls&pq=how%20to%20install%20ubuntu%2010.04%20separate%20home&xhr=t&q=what+is+the+default+ubuntu+file+system&cp=35&qe=d2hhdCBpcyB0aGUgZGVmYXVsdCB1YnVudHUgZmlsZSBzeXM&qesig=-Ss6fkqKUM-vTJCGqZ1_fQ&pkc=AFgZ2tnL1L1-uH99gQUcEUMmmDB9jyv6b3zdFMHgdSM7n958d-ozLanL-hHzwLm5j1iQqtJYjqQCLTEY5Ju0wecPFhKC2EGXAw&pf=p&sclient=psy&client=ubuntu&hs=7Vx&channel=fs&source=hp&aq=0j&aqi=&aql=&oq=what+is+the+default+ubuntu+file+sys&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=efa329ff265db1bb")", I find 

[LIST]
[*][LinuxFilesystemsExplained]("https://help.ubuntu.com/community/LinuxFilesystemsExplained")
[*][Idea #8357: Abandon ext2/3/4 as default filesystem    ]("http://brainstorm.ubuntu.com/idea/8357")
[*][Ubuntu Wiki Lucid Lynx Release Notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes")
[*]etc.
[/LIST]
Notable quote:
> The default file system for installations of Ubuntu 10.04 LTS is ext4, the latest version in the popular series of Linux extended file systemsThe Ubuntu 10.04 re-installation of side-by-side operating systems created this /etc/fstab file by default:

```

UUID=1e5cedf6-5e87-471a-a16b-f5f03358f8b7 /  **[COLOR=DarkRed]ext4 [/COLOR]**   errors=remount-ro 0       1

```From this, can I "assume" I already am using ext4?

---

### Post by rocksockdoc on 2011-04-26
> **Dutch70 said:**
> make the swap partition equal to your physical RAM

Let's see what the Ubuntu 10.04 re-installer gave me as a swap partition:

```

$ grep swap /etc/fstab
...
UUID=2e843afe-269f-44a7-9b2a-82d2d5eb48e4 none   swap    sw   0   0

```Well, that didn't tell me much. Let's google "what size is ubuntu 10.04 default swap partition" and "how big is my ubuntu 10.04 swap partition"  ... . drat ... After reading a half-dozen or more links, I realize everyone 'talks' about swap sizes (like they talk about the weather) but they don't seem to explain how to tell how big the current users' swap size is. (Usually that means it's 'obvious' to those who already know how. :) )

Changing the search terms (by removing Ubuntu altogether), I find generic Linux help for figuring out the swap size (so now it's obvious to me too!). 
- [All about Linux swap space    ]("http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space")

Notable quote:
> To see what swap space you have, use the command swapon -sGiven that (now obvious) hint, I see the Ubuntu installer gave me 808 thousand kilobytes (i.e., 808 Mb) of swap space on the sda2 partition:
```

$ swapon -s
...
Filename Type Size Used Priority
/dev/sda7 partition 807928 0 -1 

```Now to figure out how much memory I have (I think it's 2GB but I need to doublecheck). Googling for "how to check ram in ubuntu", I find:
-[Ubuntu Check RAM Memory Chip Speed and Specification From Within a Linux System]("http://www.cyberciti.biz/faq/ubuntu-check-ram-memory-speed-specification-within-linux-machine/")

Notable quote:
> You need to use the [dmidecode command]("http://www.cyberciti.biz/tips/querying-dumping-bios-from-linux-command-prompt.html") which  is  a tool for dumping a computer's DMI (some say SMBIOS) table contents in a human-readable format. Now that it's 'obvious' to me how to check installed RAM size, here are my results:

```

...stuff...
Memory Controller Information
     ...
        Maximum Memory Module Size: 4096 MB
        Maximum Total Memory Size: 8192 MB
...
        Associated Memory Slots: 2
                0x0008
                0x0009
...
Handle 0x0008, DMI type 6, 12 bytes
...
        Socket Designation: DIMM Slot 1
...
        Type: DIMM SDRAM
        **[COLOR=DarkRed]Installed Size: 1024 MB[/COLOR]** (Double-bank Connection)
        Enabled Size: 1024 MB (Double-bank Connection)
...
Handle 0x0009, DMI type 6, 12 bytes
...
        Socket Designation: DIMM Slot 2
...
        Type: DIMM SDRAM
       **[COLOR=DarkRed] Installed Size: 2048 MB[/COLOR]** (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
...

Handle 0x0022, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x0023, DMI type 17, 27 bytes
...
        **[COLOR=DarkRed]Size: 1024 MB[/COLOR]**
        Form Factor: SODIMM
...
        Locator: DIMM 1
        Bank Locator: Bank 0/1
        Type: DDR2
...
Handle 0x0024, DMI type 17, 27 bytes
...
       **[COLOR=DarkRed] Size: 2048 MB[/COLOR]**
        Form Factor: SODIMM
...
        Locator: DIMM 2
        Bank Locator: Bank 2/3
        Type: DDR2
...

```So, from that, may I conclude my RAM is 1 GB + 2 GB = 3 GB?

If so, I 'should' have at least a 3 GB swap partition. Right? Or is that 6 GB?

---

### Post by rocksockdoc on 2011-04-26
> **d3v1150m471c said:**
> Most problems can be fixed by booting into a root terminal at the grub menu in recovery mode and reinstalling and/or reconfiguring issues.

That's good advice. But, what happened with the first time Ubuntu chewed itself to death was when my encrypted home partition suddenly wouldn't let me in even though I knew the encrypted partition password. 

It was a long sordid hassle to total failure:
- [Can repeated adding FNEK Signature auth tokens damage home directory encryption links]("http://ubuntuforums.org/showthread.php?t=1587340")

[B]End result: Never (ever) use Ubuntu home directory encryption!
[/B][SIZE=1] (Use truecrypt file encryption instead!).[/SIZE]

This second time (last week) Ubuntu suddenly chewed itself up happened when I had to kill a stalled automatic update. The result was suddenly absolutely no access to all the USB ports (which is inconvenient in a Lenovo X61 laptop that doesn't have an internal DVD-disc drive) and no wirless networking whatsoever and a host of other things such as no x-close buttons in x-windows and a screwed up login screen, etc., even to the point that Ubuntu 10.04 wouldn't shut down using the log-out commands and a host of other oddities caused by Ubuntu failures in the update manager.

**The moral of that story is still pending - but I've learned (the hard way) to never ever ever ever ever ever ever allow any Ubuntu update to die mid stream, even if it hangs for months! **

It was a miserable experience re-installing side-by-side Ubuntu operating systems without any use whatsoever of wireless networking nor any use whatsoever of the USB ports (and not having an internal dvd disc drive). :(

> **d3v1150m471c said:**
>  If you have trouble a lot of the people at the forums are good at pinpointing and providing solutions. Might as well take a stab at it before reinstalling, wouldn't hurt.

True. Good advice. But really (really) hard to follow when you have no access to the Ubuntu installation disc (because of no wireless networking and no use whatsoever of USB ports and no internal disc drive).

---

### Post by rocksockdoc on 2011-04-26
> **Dutch70 said:**
> 
This link may also help you.
[[COLOR=RoyalBlue]http://ubuntuforums.org/showthread.php?t=1735797[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1735797")

Thanks for that pointer. Unfortunately, I have two Ubuntu 10.04 side-by-side installations when I really only want one! :(

```

$ sudo fdisk -l
...
Disk /dev/sda: 120.0 GB, 120034123776 bytes
...
   Device Boot      Start         End      Blocks   Id  System
**[COLOR=DarkRed]/dev/sda1   *           1       11697    93953175+  83  Linux[/COLOR]**
/dev/sda2           11697       14594    23265281    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris
**[COLOR=DarkRed]/dev/sda6           11697       13894    17642496   83  Linux[/COLOR]**
/dev/sda7           13894       13994      807936   82  Linux swap / Solaris

```Downloading and running the suggested [Sourceforge bootinfoscript]("http://bootinfoscript.sourceforge.net/"), I get as results the following "boot info" summary:
```

             Boot Info Script 0.55    dated February 15th, 2010               

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

```And, the following drive partition information:
```

=========================== Drive/Partition Info: =============================

Drive: sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System
/dev/sda1    *          2,048   187,908,398   187,906,351  83 Linux
/dev/sda2         187,910,142   234,440,703    46,530,562   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris
/dev/sda6         187,910,144   223,195,135    35,284,992  83 Linux
/dev/sda7         223,197,184   224,813,055     1,615,872  82 Linux swap / Solaris

blkid -c /dev/null:

Device           UUID                                   TYPE       LABEL         
/dev/sda1        9807531b-98b3-4fb0-9cd9-91e726e5ac68   ext4                     
/dev/sda2: PTTYPE="dos"
/dev/sda5        b3921950-f471-4ce3-8fc6-c796c80cf46b   swap                     
/dev/sda6        1e5bedf6-5e08-471a-a16b-f5f05358ebb7   ext4                     
/dev/sda7        2e843eea-269f-44a7-9b1a-81d1d5eb488f   swap                     
/dev/sda: PTTYPE="dos"


```I don't really know how to 'clean this mess up'. 

What I'm most likely to do is save my data, and then start all over again with a clean installation (which is why I asked this question as to how best to install Ubuntu keeping data safe!).

---

### Post by rocksockdoc on 2011-04-26
BTW, one thing I'm slowly learning (after two Ubuntu disasters) is to start keeping a log of what I've installed.

At the moment, this is a manual process ... (see my ad hoc log text below, for example) ... but may I ask if there is an installation log feature in Ubuntu 10.04?

Here, by way of example, is my manual log since re-installing Ubuntu earlier this week:
```

20110422 Had to re-install Ubuntu 10.04 (very painfully) side-by-side (to save the old data)
20110422 Firefox installed Adobe Flash Plugin version 10 (asked for by speedtest.net)
20110423 Gnome update manager ran an automatic update (this one didn't crash & chew up the OS!)
20110423 Apps->Accessories->Terminal (RMB -> Add this launcher to panel)
20110423 Apps->Accessories->Take Screenshot (RMB -> Add this launcher to panel)
20110423 USC > nautilus-image-converter (mass resize images)
20110423 USC > exiftran (e.g., EXIF rotate) /usr/bin/exiftran
20110423 USC > GIMP Image Editor /usr/bin/gimp
20110423 USC > KolourPaint (Paint Program) /usr/bin/kolourpaint
20110423 USC > Feh /usr/bin/feh
20110423 USC > PAN /usr/bin/pan
20110423 WEB > downloaded truecrypt-7.0a-linux-x86.tar.gz (/usr/bin/truecrypt) (Never use native Ubuntu encryption!!!!!!!!!!!!!!!!!!!!
20110423 WEB > Keep a note of: To uninstall truecrypt, run: /usr/bin/truecrypt-uninstall.sh
20110423 USC > Install all GStreamer plugins to Totem Movie Player 2.30.2 (must be a better way to install all codecs at once!)
- gstreamer0.10-ffmpeg MPEG-1 Layer 3 (MP3) decoder
- gstreamer0.10-fluendo-mp3 MPEG-1 Layer 3 (MP3) decoder
- gstreamer.10-plugins-ugly MPEG-1 Layer 3 (MP3) decoder
- gstreamer0.10-plugins-ugly Advanced Streaming Format (ASF) demuxer
- gstreamer0.10-ffmpeg Windows Media Video 8,9 decoder
- gstreamer0.10-plugins-bad MPEG-4 AAC decoder
20110424 System > Preferences > Startup Applications > Blutooth Manager (off)
20110424 Had to work around Ubuntu 10.04 bug in USB wifi adapters from Realtek
http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    gunzip rtl8192sfw.bin.gz
    sudo mkdir /lib/firmware/RTL8192SU
    sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/.
20110424 Network Manager > Edit Connections -> Wireless -> Edit -> MAC address
   1. Right click on the Network Manager icon in the main Ubuntu 10.04 top menu bar
   2. Left click on Edit Connections -> Wireless tab
   3. Left click to highlight your desired connection & press the "Edit" button
   4. Left click on "Wireless" tab & enter desired MAC into the "MAC address" field
      * This option locks this connection to the network device specified
        by the MAC address entered here.
        -> 00:02:6f:36:b2:2b = desired
        -> 00:13:e8:23:e7:db = wlan0 (internal WiFi card)
        -> f8:78:8c:00:64:25 = wlan1 (external USB WiFi radio)
   5. Left click the "Apply" button
   6. Then, when you start up, the Network Manager should only use the wireless device with that MAC address.
20110425 sudo updatedb (so I can use the 'locate' command)
20110425 sudo apt-get install pdftk  (to edit PDF files)
20110425 sudo apt-get install pdfedit (to edit PDF files)
20110425 sudo apt-get install krita (to edit picture files)
20110425 sudo apt-get install inkscape (to create vector graphics files)
20110425 USC > Scribus
...

```

---

### Post by Dutch70 on 2011-04-26
You've really been doing some homework. That's a good thing to see.
In the future to know what file system you're using & the size of your swap partition, open Gparted, it's all right there in a GUI *(btw you have 2 swap prtns also)*. To know how much ram you have, open system monitor & click the "system" tab, or in the terminal type "free -m" without the quotes. 

In the link I gave you, the guy also had 2 installs of Ubuntu & only wanted one. 

On the following link, near the bottom of the tutorial there is some advice about how to reinstall and keep your programs, I've never used it, but I'll give it to you to check out. It starts after....**[COLOR="Red"]Well, I get your point,[/COLOR]** 
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1580857[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

You obviously ended up with 2 installs by trying to reinstall, right? I would normally advise you to delete your old one & one of your swap prtns, but your old one is in a primary prtn & your new one is in a logical prtn, and it's a good idea to have your main install in a primary prtn. Linux OS's are fine in a logical prtn, but I don't recommend it. If it's your only system, it's better that you have it in a primary prtn.

Open Gparted & take a screenshot, use the paper clip in the toolbar to attach it to your next post along with what you want to do, and I or someone else will be glad to help you with it.

---

### Post by rocksockdoc on 2011-04-26
> **Dutch70 said:**
> Gparted, it's all right there in a GUI

Thanks for the pointer to Gparted. That's the kind of help I need. Once I have a search term, I can use the tool - but - without the focus on a specific command, the whole (confusing) world is the search result. Am installing it now, as we speak.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190112&stc=1&d=1303848900[/IMG]

> **Dutch70 said:**
> *you have 2 swap prtns*Yuck. I noticed that from the "fdisk -l" output. I also notice one of the swap partitions is six times larger than the other! How did 'that' happen? And, how do I get rid of the one I don't need!  < / Yuck >

```

/dev/sda5           13995       14594     4805632   82 [COLOR=DarkRed] **Linux swap**[/COLOR] / Solaris
/dev/sda7           13894       13994      807936   82  **[COLOR=DarkRed]Linux swap[/COLOR]** / Solaris

```> **Dutch70 said:**
> To know how much ram you have, open system monitor & click the "system" tab, or in the terminal type "free -m" without the quotes

Again a great pointer! I did 'not' see that hint in my generic 'how to know your memory' searches. My results, see below, seem to indicate 2.9 GB of RAM memory; so it seems I only need swap space of 300,000 kbytes of RAM (whereas my /dev/sda5 and /dev/sda7 swap partitions are vastly larger than that!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190116&stc=1&d=1303849901[/IMG]

Interestingly, in that screenshot above, I notice my swap seems to only be 800 Megabytes (I'm not sure what a "MiB" is).
Googling for "Ubuntu MiB", I find it's "essentially" a more accurate Megabyte:
- [Wikipedia Mebibyte]("http://en.wikipedia.org/wiki/Mebibyte")

Notable quote:
> The **mebibyte** is a multiple of the unit [byte]("http://en.wikipedia.org/wiki/Byte") for digital [information]("http://en.wikipedia.org/wiki/Information"). The [binary prefix]("http://en.wikipedia.org/wiki/Binary_prefix") *[mebi]("http://en.wikipedia.org/wiki/Mebi-")* means 220, therefore 1 *mebibyte* is 1048576bytes. The unit symbol for the mebibyte is **MiB**.[[1]]("http://en.wikipedia.org/wiki/Mebibyte#cite_note-0") So, it looks like my swap is far too small for the amount of memory I have:

[LIST]
[*]RAM = 2.9 gigabytes
[*]SWAP = 800 megabytes
[/LIST]
Here are the results from the suggested "free -m" command:
```

$ free -m
...
             total       used       free     shared    buffers     cached
Mem:          2999       2398        600          0        123       1794
-/+ buffers/cache:        481       2518
Swap:          788          0        788                                                                      

``` > **Dutch70 said:**
> In the link I gave you, the guy also had 2 installs of Ubuntu & only wanted one

Oddly, I did 'not' notice that. I was more concerned with figuring out the meaning of the commands. I'll go back and re-read that, now that I have some background in the terminology & commands and my own situation (i.e., two Linux partitions and two swap partitions). 

> **Dutch70 said:**
> You obviously ended up with 2 installs by trying to reinstall, right? 

Here's the short story of my Linux 10.04 installations:

[LIST]
[*]In August of 2010 (my Ubuntu join date), I got tired of Windows chewing itself up
[*]So I installed Ubuntu 10.04 from a downloadable CDROM on the advice of a trusted Google developer friend of mine
[LIST]
[*]All was well until early October when my "encrypted home partition" chewed itself up somehow (my data was and still is trapped inside that encrypted user account)
[LIST]
[*][Failed attempt at saving damaged home directory encryption links]("http://ubuntuforums.org/showthread.php?t=1587340")
[/LIST]
 
[*]At 'that' time, I created a new user (and continued to attempt to resurrect the failed encrypted account, but to this day I have failed miserably)
[/LIST]
 
[*]Moving along ... I was doing fine until this week when both the automatic update and my hotspot connectivity failed at the same time ... for whatever reason ... the Lenovo X61 operating system hosed itself
[LIST]
[*]The main problems were that the wifi icon disappeared (so I had no Internet help)
[*]And all three USB ports were dead (so I had no access to the Ubuntu install disk)
[*]And the operating system was missing key items such as the ability to even shut itself down
[/LIST]
 
[*]I found it 'weird' (to say the least) that the USB ports were dead because they're supposed to be BEFORE the operating system - but dead they were.
[LIST]
[*]I could boot to the user account - but I couldn't fix anything as many commands were useless
[/LIST]
 
[*]Long story short, I finally removed the hard drive (hoping to replace it & re-install the OS)
[LIST]
[*]Amazingly (who knows why), with the hard disk removed, the USB ports started working again!
[*]So, I IMMEDIATELY booted to the original Ubuntu 10.04 cdrom
[*]I then found that I had to (while booted to Ubuntu) insert the hard disk back into the laptop
[*]And ONLY THEN could I install the operating system!
[/LIST]
 
[*]Since I realized it was a capricious act of God that the thing booted at all (only with the hard drive removed) I had only one shot at installing the Ubuntu OS (with the hard drive hastily ad-hoc reinserted)
[*]I opted for side-by-side installation (to preserve my data and to preserve my original encrypted /home user that never was resurrected)
[/LIST]
I hope 'that' summary explains what happened. Very little that occurred was by design. It was all simply my reaction to my fate.

> **Dutch70 said:**
> I  would normally advise you to delete your old one & one of your swap  prtns, but your old one is in a primary prtn & your new one is in a  logical prtn, and it's a good idea to have your main install in a  primary prtn.

Thank you for that astute advice. I had not realized these details. My main concern with the original Ubuntu installation was saving my data (some of which was truecrypt encrypted with a file size of 8 Gb that couldn't move over for some strange reason); and, of course, I was still hoping to preserve the failed encrypted user partition (which I discussed in this thread below):
- [Can repeated adding FNEK Signature auth tokens damage home directory encryption links]("http://ubuntuforums.org/showthread.php?t=1587340")

> **Dutch70 said:**
> Linux OS's are fine in a logical prtn, but I don't  recommend it. If it's your only system, it's better that you have it in a  primary prtn.

I will take your advice ... and am only concerned with preserving my data and (someday, somehow) accessing the failed user encrypted home directory.

> **Dutch70 said:**
> Open Gparted & take a screenshot ...and I or  someone else will be glad to help you with it.

It took me a while to create the screenshot as I want all my threads to be re-usable so that they help others at the same time they help me (it's the way I am).

For example, intuitively, I would have thought that Gparted would have ended up in the "Applications" menu; but it actually ends up in the System menu. So, to help others at the same time as you're helping me, I created this re-usable 800x600 screenshot for Gparted!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190120&stc=1&d=1303853167[/IMG]

---

### Post by Dutch70 on 2011-04-26
Nice, but you are running software center, where you install Gparted. We need to see your partitions while you're running Gparted, not software center. :D

Like this...

---

### Post by rocksockdoc on 2011-04-26
> **Dutch70 said:**
> We need to see your partitions while you're running Gparted

My fault.

I take a loooong time to reply because I respond to every pertinent issue and I take pains to edit the original quote to the essentials, and I add the courtesy of a well-formatted and well documented response. All this takes time (usually a half hour or more per post) but the darn Ubuntu forum kicks me off after a few minutes of what it deems inactivity. So I constantly risk losing my hard-earned data laboriously edited into my posts.

So, what I do is hit the SAVE button (in this case, it's the re-editing save button), answering each portion of your response, in turn, from top to bottom. As I do so, I run the risk of someone responding to a partially completed response (as how would they know that all this is because this Ubuntu forum erroneously kicks me off during almost every response because I take the time to give a well-formatted response). 
*[SIZE=1] NOTE: Other forums do not have such a ridiculously short attention span (presumably Linux gurus are more laconic & less fastidious than I!). :)[/SIZE]*

Anyway, our your kind response and my well-intentioned editing crossed in the ether. If you look again, I have now finished that post and pasted a screenshot of the Gparted results. 

You'll notice that I take pains to courteously show all the relevant information in the edits, so, I had to combine two screenshots (one of the menus as Gparted did not go into an intuitive location in the 'normal' Application menus but went into the System menus) - that took time.

Here is that screenshot (shrunk to 640x480 from the original).

BTW, it's worth helping me because I try to help others who come after me by documenting the process so that even a newbie could follow along ... and because I will USE the suggestions you provide.

For example, I used all of these threads of mine to make the screenshots:
- [What's a good curved ARROW drawing tool in Ubuntu (similar to Paint.NET on Windoze)?]("http://ubuntuforums.org/showthread.php?t=1575505")
- [What's the best (i.e., quickest and easiest) program to manually crop digital photos]("http://ubuntuforums.org/showthread.php?t=1570447")
- [How best to batch shrink JPEG file size (not pixels) to a given number of KBs?]("http://ubuntuforums.org/showthread.php?t=1720675")
-                           [Is there an extension to "Eye of Gnome" to RENAME or DELETE pictures while viewing?]("http://ubuntuforums.org/showthread.php?t=1737710")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190121&stc=1&d=1303853820[/IMG]

---

