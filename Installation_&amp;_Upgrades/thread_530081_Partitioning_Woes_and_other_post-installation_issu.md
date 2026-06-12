---
title: "Partitioning Woes and other post-installation issues."
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by Rockman4140 on 2007-08-20
I am attempting to switch to Ubuntu after reading some horrifying things about Vista having 20+ programs actively collect and send information to M$. I just kludged through the Ubuntu installation, having to reconfig X Server. I had my HD partitioned off for Ubuntu, but I forgot to reserve space for a FAT32 partition. Here is what I have.

1.46 GIG, EISA Partition (Toshiba backup Partition)
29.79 GIG Primary Partition (Ubuntu Filesystem)
1.91 GIG Primary Partition (Swap)
85.73 GIG NTFS Primary Partition (Vista)
30.14 GIG Free Space

Did I partition them wrong of does Vista really take up 80+ GIGS for no reason? I'm attempting to shrink down the Vista partition to get a decent amount of space to share.

I also have a few post-installation problems. I need a Wireless connection but I cannot find ndiswrapper on Ubuntu anywhere. I don't know how I could fetch it with no net connection, and with no common filesystem, am I SOL? With the net driver I could probably kludge my way through getting my Video Card and Sound Card working.

Any help would be so appreciated. I tried Ubuntu when my girlfriend's XP computer crapped out on her, and I've been so wanting to dual boot on a stale system. That, and with my fellow geek friend ranting on how Beryl kicks Aero's behind, I've been wanting to stick it to M$.

On one last note, I'm pretty sure my Laptop is a 64bit, would it be bad to downgrade back to 32bit? I saw quite a few things would not work in the Synaptic Packet manager because I was using amd64. How would one go about that?

---

### Post by Rockman4140 on 2007-08-21
Still no luck with ndiswrapper, I read it was on the Live CD, but how do I accomplish getting it from there? I used the Synaptic Packet Manager to get it, but I need net access to download it.

---

### Post by Midahed on 2007-08-21
Can you still boot into Vista?  If so, and if you have a USB memory stick, you could use Vista as your means of access to the net, get the tools you need to finish your Ubuntu installation and put them all on the memory stick.

I had to do something similar when I was getting my system working first time round.  All that re-booting is tedious, but if you don't have a second PC kicking around.....

As far as the 32bit-v-64bit thing goes, yes, there are some extra frustrations with 64-bit at the moment.  I was tempted to go back to 32-bit but, so far, I've stuck with it.  So much of the decisioon depends on what you want to do with your system and the extent to which you are prepared to fiddle around with it to overcome the occasional problems.  The best this is to trawl through a few of the (many) 32bit-v-64bit discussions on the 64-bit section of the Ubuntu forum.

Mike

---

### Post by Rockman4140 on 2007-08-22
Yeah, I'm gonna pick up one of those tomorrow after work, I was actually thinking of this solution today, Heh. Thanks very much though. I'll tool around in the 64bit forums.

If anyone could please shed some more light on my partitioning issue (If it is an issue), it would be very much appreciated.

---

### Post by merlinus on 2007-08-22
You can only have four primary partitions.  Is the Toshiba backup one of them?

IF so, then create an extended partition, which can contain many logical ones.

Also, vista almost certainly wants to be ahead of any other os.

Before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

Use vista's disk manager to resize its partition.

-merlin

---

### Post by Rockman4140 on 2007-08-27
If I've already Installed Ubuntu and uninstall it, will I still have the GRUB, or will Vista's boot manger take over?

I'm going to stick with the amd64 build I guess since I have the processor for it, and I'll try to see what I can get to work. It just sucks my wifi card won't work or is too difficult to get to work. I can't give up Vista until then, but my goal would be to become 100% Vista free, and with how the Linux community is coming, I can see that will be very soon.

It's really sad that many people will blindly follow Microsoft, and that many people are expecting to get treated like crap, The concept of Ubuntu is very much how thins should be.

---

### Post by fumduck on 2007-08-27
you can reinstall grub from live disc if necessary
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")


[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

good luck

---

### Post by Pumalite on 2007-08-27
And this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by khughitt on 2007-08-27
To find out how much space is being used on the vista partition, try loading the [vista partition manager]("http://www.pro-networks.org/forum/viewstory.php?t=78111"). You may be able to shrink the partition right inside vista, but if not [Gparted]("http://gparted.sourceforge.net/") (which should be already installed on Ubuntu), should do the trick.

For the wireless issue, what adapter are you using? If you still have Ubuntu installed, and are not sure about the wireless, open up a terminal ([FONT="Courier New"]Alt+F2 --> "gnome-terminal"[/FONT]), and run the following two commands:

```

lspci
lsusb

```

copy the results to a text file ([FONT="Courier New"]Alt+F2--> "gedit"[/FONT]), and copy them to a cd / usb stick, then post them on the forums here.

---

### Post by Pumalite on 2007-08-27
The partitioning HAS to be done with the Vista partitioner; otherwise Vista will not let you run anything in that computer.

---

### Post by Rockman4140 on 2007-08-30
After using the Atheros.cz drivers, I now have the ability to see access points. My issue now is that I cannot connect to my home AP(Linksys WRT54G) for some reason. I have WEP as the wireless security setting, and I have my laptop whitelisted with it's MAC address. None of the WEP keys I've entered work, and it tries for about a minute with no luck. They are 128bit Hex keys, and my router is using the "auto" authentication type. I'm going to attempt to tinker more, but if anyone knows what I'm doing wrong, it would be greatly appreciated if you could help.

EDIT: Yeah, I dropped my network security on the router, and I still couldn't connect to it. I'm gonna go ahead and say I screwed up somewhere. If I need to dump a config file, I'd be glad to if I knew which one I should. Thank you guys so much for dealing with my inexperience, I found a link to free Linux books, and I hope that they will better me so y'all won't have to put up with me.

---

### Post by Rockman4140 on 2007-09-02
I made a small temp Fileswap partition, and here is a log of some stuff that may help. I'm still attempting to figure out what it means, but maybe someone could help. I am using a Linksys WRT54G, BellSouth DSL (Will have to Edit with name of new modem), and my Atheros card. Any help would be appreciated more than words could describe.

```
wlan0:avahi IP4 - 169.254.0.1 255.255.0.0 169.254.255.255 (Interface doesn't exitst (When Asked to Configure))
wlan0

daniel@daniel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:0F:DA:D4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:38:0F:DA:D4  
          inet addr:169.254.8.69  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158114 (154.4 KiB)  TX bytes:158114 (154.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:f8200000-f8210000 

wlan0:ava Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:169.254.0.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f8200000-f8210000 

daniel@daniel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@daniel-laptop:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```

---

### Post by Pumalite on 2007-09-03
Try 'Networking'.

---

### Post by Rockman4140 on 2007-09-05
> **Pumalite said:**
> Try 'Networking'.

I'm in roaming mode currently. After supplying the hex key, I can connect at 0%, or not connect at all. Using the manual configuration won't connect me either. I added the IP of my router as a DNS server, I guess I may have to do that with my modem too...

---

### Post by Pumalite on 2007-09-05
I meant the sub-forum Networking and Wireless. Did you try it?

---

### Post by Rockman4140 on 2007-09-05
...Wow, Yeah, I'm a moron, I guess I should probably look there more, eh? Alright, thanks for all your help.

---

