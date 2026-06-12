---
title: "install ubuntu for the first time on an old computer :("
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by rig the gear on 2011-02-16
I had get back an old computer that use belong to me. it is a gateway pc (by this you can guess that it is real old pc)

spec are:

127 Ram
Intel celeron
install Window ME(aka Multiplier Error)
5.99 GB on harddrive


i use this pc to learn basic ubuntu but it kept give error signs. i will like to know if i can use this program or "Lite version" or old version i can use? because i real want to know ubuntu 


thank you

---

### Post by sikander3786 on 2011-02-17
Try Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

With 128 MB RAM, it is impossible to run the regular Ubuntu with GNOME.

---

### Post by Stephann on 2011-02-17
You'd really be helping yourself if you could round up at least half a gigabyte of RAM.  That said, you should be able to run Xubuntu just fine (a little more 'normal' features than Lubuntu, but still pretty user friendly.)  

While you're at it, this would be a *really* good time to pick up a used or cheap IDE hard drive, as a 6 gig drive is old enough that it could die on you at any minute, nevermind that 6 gigs really isn't barely enough space to do anything.

Good luck!

---

### Post by rig the gear on 2011-02-17
ok i try that lubuntu now it error coming again like before

1. "cannot updack d:\\wubi.exe
2. "cannot copy c:\\windows\temp\pyl73A2.tmp.exe

i found about the motherboard is an flex-atx

General Features:
Intel 810E chipset
Socket 370
Flex ATX form factor
133 MHz FSB
Supports up to 512 MB PC100 SDRAM 
Integrated video
Integrated audio
Two (2) IDE controllers
One (1) Floppy controller

Expansion Slots:
Two (2) PCI slots
Two (2) 168-pin DIMM slots

I/O Ports:
One (1) 15-pin VGA connector
Three (3) USB ports
One (1) RJ-11 modem port
Line-in, microphone, and line-out jacks

Supported Processors:
Intel Pentium III processors with 133 MHz FSB
Intel Celeron processors with 133 MHz FSB

Regulatory Approvals:
FCC
CE
cULus
C-Tick


so i dont know what to do kill it or try to replace some part and just wait till i had a better parts i can build it from ground up

again thanx

---

### Post by Old_Man_Unix on 2011-02-17
> **sikander3786 said:**
> Try Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

With 128 MB RAM, it is impossible to run the regular Ubuntu with GNOME.

Moreover, you cannot use the graphical installer (Ubiquity)  or the full installation for Lubuntu.  You must use the "**mini.iso[B]"**[/B].  Please make sure that you download that iso and not the regular one.

Please follow the instructions here:

 [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

A suitably installed version of  Lubuntu* will* run on your system but don't expect any performance magic.

---

### Post by Stephann on 2011-02-17
Yep.  Download the 'mini.iso' disc, burn it, and then boot your gateway PC with that disc.  

You won't have enough space on the drive to install it next to Windows, without a larger drive, so you'll have to install Lubuntu (or Xubuntu) over Windows.

---

### Post by rig the gear on 2011-02-17
so i download this and i found some ram found from tigerdirect.

[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=423457&csid=ITD&recordsPerPage=10&body=REVIEWS#tabs](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=423457&csid=ITD&recordsPerPage=10&body=REVIEWS#tabs)

i just want to make sure this is right parts that i need to order. also want to order X2 with this  hard drive from same site

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3554367&CatId=524](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3554367&CatId=524)

with this two upgrade will i had power to run any type of linux program?

i not use the internet or anything else, i just want to work on my command line so that will not get scared when i install in a full rig that i can builded.

thanx again #-o

---

### Post by rig the gear on 2011-02-17
ok after burn and install mini.iso.

than i reboot my desktop and boot for mini.iso menu comes up

i select install and hit enter, than screen start to flash and little white line start come up. best why to full understand it if you was look at a old tv with a hander for att. computer full frozen is their way to fix this? or i **** out luck till i upgrade the ram and hard drive?

once again thanx

---

### Post by rig the gear on 2011-02-17
ok i final get to start to install. i hit help than F2 than enter

so when i hit mirror section
this i choose USA than i hit enter than this comes up

"Bab Archive mirror 
An error has been detected while trying to use the specified:
mirror is not available (possibly due to an unreliable network connection); mirror us broken (for example because ab invalid release was found): mirror does not support the correct Ubuntu version.

additional detail maybe available in /var/log/syslog or virtual console 4

Please check the specified mirror or try a different one."


someone tell me what i do wrong? is it act this way because i dont had connect to net? do i need it connect to net all the times or only when i install it?

also name a host? 

1. it has to be Ubuntu
2. i can name it like i name my computer

i try need help and like if someone can give me an answer soon as possible for i can fix this now i been try for five days i final can to forum last night and give all help :)

again thank

---

### Post by Stephann on 2011-02-18
The host name doesn't matter.

The problem you're experiencing probably has to do with configuring your network.  When you get to the mirror selection menu, press ALT+F2 and you'll see a terminal.  Hit 'enter' to activate that terminal, and try typing 'ping amazon.com' and see if it connects.  If not, you may have to use the manual configuration option to set your network up.

---

### Post by Kirboosy on 2011-02-18
> **rig the gear said:**
> so i download this and i found some ram found from tigerdirect.

[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=423457&csid=ITD&recordsPerPage=10&body=REVIEWS#tabs](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=423457&csid=ITD&recordsPerPage=10&body=REVIEWS#tabs)

i just want to make sure this is right parts that i need to order. also want to order X2 with this  hard drive from same site

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3554367&CatId=524](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3554367&CatId=524)

with this two upgrade will i had power to run any type of linux program?

i not use the internet or anything else, i just want to work on my command line so that will not get scared when i install in a full rig that i can builded.

thanx again #-o

Those parts should work just fine with your computer. After the upgrade your computer will still by no means be a powerful computer but I know you will be much happier with it in the long run. :)

[Cheaper RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820146079")


[Cheaper Hard Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136112")

Just trying to save you a little money. :)

---

### Post by Stephann on 2011-02-18
Some brief advice?  Depending on where you live, of course, you could probably score a computer with more RAM, bigger hard drive, better graphics, and faster processor on craigslist for about $100.  

I live in the San Francisco Bay area, so here's some examples near me:

[http://sfbay.craigslist.org/sby/sys/2220785138.html](http://sfbay.craigslist.org/sby/sys/2220785138.html)

[http://sfbay.craigslist.org/nby/sys/2220851014.html](http://sfbay.craigslist.org/nby/sys/2220851014.html)

[http://sfbay.craigslist.org/eby/sys/2221138302.html](http://sfbay.craigslist.org/eby/sys/2221138302.html)
[RIGHT]
[/RIGHT]

---

### Post by snowpine on 2011-02-18
A huge +1 to Stephann. Installing Ubuntu for the first time on obsolete hardware really is not a fun introduction to the wonderful world of Linux. If you can get a Pentium 4 or better with 512mb or more of RAM, you'll have a much smoother experience. There are a lot of used computers out there looking for a good home. :)

---

### Post by rig the gear on 2011-02-19
Thanx guys all ur help trust me it not fun but i want to learn Ubuntu/Linux program specialty commands lines. 

i plan to upgrades. i go to use newegg.com to get upgrade parts and get the this old pc some life.

---

