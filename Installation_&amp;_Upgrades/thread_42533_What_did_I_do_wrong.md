---
title: "What did I do wrong?"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Lorraine on 2005-06-18
So, I finally got around to installing Ubuntu on its very own drive.  I had been thoroughly pleased using the Live CD.  I figured that the full installation should work as well as the Live CD and probably even better.  Well, that's not happening.  I'm having issues with the full installation that I didn't have with the Live CD.  The three main issues that I'm having are as follows:

1) The internet connection isn't working.  It worked fine using the Live CD.
2) GRUB is not booting to Windows when Windows is selected (obviously that's not an issue I would have with the CD, but it is now an issue nonetheless)
3) My computer is freezing under Ubuntu.  

Here is more of the background information:

**_System:_**
Motherboard: Epox 8kta3pro
Processor: AMD Duron 900
RAM: 384MB
Graphics Card: ATI Rage Pro 128 (AGP)
SCSI Card: Promise ATA 100 (Windows drive is on this card)
NIC: PCI Ethernet DEC 21041
DSL Modem: Qwest Actiontec 
Sound Card: Creative SoundBlaster 16 (ISA)
TV Tuner: ATI TV Wonder
OS: Windows 98 & Ubuntu 5.04 Hoary
[B][U]
Configuration of Drives:[/U][/B]
Promise ATA 100
·	Master - Maxtor 40GB – Windows 98 Drive 
·	Slave - WD 80GB – Data & Backup Drive

Motherboard EIDE 1
·	Master - Plextor CDRW
·	Slave – Toshiba DVD-ROM

Motherboard EIDE 2
·	Master – Maxtor 45GB – Ubuntu Drive
·	Slave – WD 80GB- Media Drive

Other:
·	Buslink External USB HDD 60GB (I'm not sure if Ubuntu sees this drive)

**_Install Issues:_**
"fontconfig error" - I have no idea what that means in terms of the overall setup.  I just listed it because I saw it while I was installing Ubuntu, and figured there was an off chance that it could be important.

There was also something about run '/etc/root… as daily.  I didn't catch the whole message but it seemed strange at the time.

Also, there was a series of messages where the install was indicating that certain things could not be installed and asked me if I wanted to continue.  It happened maybe four or five times.  I just entered yes each time.

**_Boot up Issues:_**
·	“Configuring network interfaces” (when booting to Ubuntu) - hangs for at least a minute at this line.  Is this normal, or does the hanging indicate a bigger issue?
·	“temporary failure in name resolution” - this doesn't show up on every boot up 
·	I set up to be able to Dual Boot with Windows 98.  GRUB does not boot to Windows 98 when it is selected.  It spits out the following lines:

Booting 'Windows 95/98/Me'
root		(hd2, 0)
	Filesystem type is fat,  partition type 0xc
savedefault
makeactive
chainloader +1

Then it spontaneously prints out the screen on my HP Deskjet.  Finally, the cursor randomly jumps around on the screen every couple of minutes.  However, it never boots to Windows.  I can get my system to boot to Windows on its own if I set the BIOS to use the SCSI drive as the first boot drive instead of HDD0, which would use the Ubuntu drive to load up GRUB.

**_General:_**
·	DSL internet connection, which worked perfectly fine using the Live CD, no longer functions under the full installation.  The lights are on, but no one's home.  All the lights on my modem are lit as though the connection should be working, but I can't actually load any websites.  I've gone under about:config to deal with the IPv6 issue in Firefox, but still nothing.
·	Unable to initiate updates (probably due to the fact that I can't connect to the internet)
·	I seem to be having some freezing issues.  It happened as I was typing up my list of general issues.  I tried CTRL + ALT + BCKSP to try to log back in, but to no avail.  I had to completely restart the computer.  I'm not sure that it's not the drive itself.  Has anyone else had freezing problems with Ubuntu or Linux in general?
·	Sound Issues – that was to be expected.  My ISA card wasn't automatically configured using the Live CD either.

I'm not sure where to start or if I'm even asking the right questions.  I really want this to work, but these are not the issues I was expecting to have.  I was expecting sound and video issues and having to learn how to use apt-get, etc.  I got spoiled with the Live CD; I thought the basic issues would be taken care of during install.

---

### Post by diebels on 2005-06-18
You have burned the cd yourself? Checked it with md5sum? When you get error messages about things not installing from the cd, it's probably broken.

---

### Post by Lorraine on 2005-06-18
I checked it with md5sum and this is what I got: f6b3f164c99761234858a4d2c12d0840    ubuntu 5.04 install i386.iso

It seems to be okay.  I downloaded the image straight from the Ubuntu website.  Do I need to have the CD mailed to me to have any hope of a clean install?  Or is there another issue?

---

### Post by diebels on 2005-06-20
> Promise ATA 100
· Master - Maxtor 40GB – Windows 98 Drive
· Slave - WD 80GB – Data & Backup Drive
There has been some driver problems with promise sata. Not sure if this is still the case.

> Motherboard EIDE 2
· Master – Maxtor 45GB – Ubuntu Drive
· Slave – WD 80GB- Media Drive
Putting 2 harddisks on one ide channel kills performance. Don't think it can cause data corruption though.

You could try putting in "noapic nolapic" boot parameters in /etc/grub/menu.lst . I had some problems before I put that in.

> Do I need to have the CD mailed to me to have any hope of a clean install?No, if your cd is ok, it's the same as the one you get in mail(except for nice label)

---

### Post by Lorraine on 2005-06-21
> **diebels]There has been some driver problems with promise sata. Not sure if this is still the case.[/QUOTE]
Hopefully, that's not the issue, because I sort of need that card in order to fit all of my drives.  However, I don't think that's the problem in terms of Ubuntu installation, as the drive to which I'm actually installing Ubuntu is attached to my motherboard IDE said:**
> You could try putting in "noapic nolapic" boot parameters in /etc/grub/menu.lst . I had some problems before I put that in.
This seems like something more feasible for me to try right now.  However, being new to Linux, I understand about half of what you're saying here.  I understand adding boot parameters, but I'm often at a loss when it comes to navigating my way around this system.  Is /etc/grub/menu.lst a file that I can get to just by going through the folders, or do I need to open up a root terminal in order to add these parameters?  Explicit instruction would help.  Thanks.  :)

---

### Post by mingus on 2005-06-21
Hmm . . . where to start . . .

First, it is not uncommon for something to work with the Live CD but not after installation, at least at first.  The CD does hardware detection on the fly and does not use some of this data, e.g., the partition table (because its only in RAM), while after installation the kernel is looking at the configuration and drivers setup on the disk by the installer program.  As you referred to, sound or video working with the CD but not after install is a typical example; the necessary drivers weren't installed yet.  

To reply to your specific questions, can you post back:

* When you installed Ubuntu, did you successfully reboot into and complete the second stage?  In particular, how did you configure apt-get - to use the CD to install packages, or the network?  Were the packages successfully installed?  What we're trying to determine here is whether all the software you need was actually installed.

* When you boot now you get the grub menu, and can boot into Ubuntu, but get an error booting to W98, yes?  When you mount the Windows drive while in Ubuntu, what is its designation - /dev/???.   Your grub thinks that the W98 drive is the 3rd drive as numbered by the BIOS.  There is a file that grub uses to associate its mapping with the system's, /boot/grub/device.map.  Could you post back that file?  Also do $sudo cat /proc/partitions, and post that.

* For your network connection, what do you see in Network Settings?  Are you using DHCP?  Have you tried to ping?  Open a terminal and do $sudo ifconfig, and post that back.

The install msg re "could not install, continue?", don't worry about.

The sound driver will need to be configured as an added kernel module, we can do that later.

---

### Post by mingus on 2005-06-22
and while your at it, also post back the result of doing $sudo lspci . . .

---

### Post by Xanthous on 2005-06-23
[QUOTE=diebels]

Putting 2 harddisks on one ide channel kills performance. Don't think it can cause data corruption though.
[/QUOTE]

Would it work (be better/perform better), if I were to put (instead of putting 2 (2x 80 gb)harddisks on one ide channel ), put HD Master on IDE0 and DVD/HD Slave on IDE1 ?
make sense????

Thank you for shedding light on this.

---

### Post by mingus on 2005-06-23
[QUOTE=Xanthous]Would it work (be better/perform better), if I were to put (instead of putting 2 (2x 80 gb)harddisks on one ide channel ), put HD Master on IDE0 and DVD/HD Slave on IDE1 ?
make sense????

Thank you for shedding light on this.[/QUOTE]

Placing 2 drives on separate channels is a good general guideline because the controller can overlap the accesses rather than having to perform them sequentially on the same channel, thereby improving performance.  However, sometimes it is not this simple.  For example, modern drives with large cache significantly reduce the same channel penalty because seeks can be queued faster than the head can move.  If there is an optical drive then it gets a bit more complicated.  The benefit gained by placing the second drive on the second channel is reduced if it is the slave behind an optical master (as you describe).  However, if the HDD is on the master and it is being actively accessed (for example, Windows swap), the performance of the slaved optical drive may be a problem - depending upon that optical drive's characteristics and how it is being used.   Bottom line, I would first try using separate channels but with both drive's on a master, and then see if my DVD still performs adequately.

---

### Post by Xanthous on 2005-06-23
[QUOTE=mingus]Placing 2 drives on separate channels is a good general guideline because the controller can overlap the accesses rather than having to perform them sequentially on the same channel, thereby improving performance.  However, sometimes it is not this simple.  For example, modern drives with large cache significantly reduce the same channel penalty because seeks can be queued faster than the head can move.  If there is an optical drive then it gets a bit more complicated.  The benefit gained by placing the second drive on the second channel is reduced if it is the slave behind an optical master (as you describe).  However, if the HDD is on the master and it is being actively accessed (for example, Windows swap), the performance of the slaved optical drive may be a problem - depending upon that optical drive's characteristics and how it is being used.   Bottom line, I would first try using separate channels but with both drive's on a master, and then see if my DVD still performs adequately.[/QUOTE]


Thank you, that was quite insiteful.  Now, before I go ahead and do that, I want to make sure that I can boot again when the hardware changes are done.  My problem here, if you have a moment to check it out: [http://www.ubuntuforums.org/showpost.php?p=225737&postcount=3](http://www.ubuntuforums.org/showpost.php?p=225737&postcount=3)

---

### Post by mingus on 2005-06-23
[QUOTE=Xanthous]Thank you, that was quite insiteful.  Now, before I go ahead and do that, I want to make sure that I can boot again when the hardware changes are done.  My problem here, if you have a moment to check it out: [http://www.ubuntuforums.org/showpost.php?p=225737&postcount=3](http://www.ubuntuforums.org/showpost.php?p=225737&postcount=3)[/QUOTE]

I took a look at the other thread.  I'm not sure what you are asking.  If you are referring to what will happen if you take hdb off of the first EIDE channel as slave and put it on the second channel as far as your booting is concerned, then I think the answer = nothing.  Grub numbers the devices as the BIOS does.  As long as the same drive that was hda is still hda, and that is the device setup in the BIOS to boot from, then nothing will change regardless of what you do with the second drive; it is only mounted as a data drive and not touched in the boot at all.

Hope that helps.

---

### Post by Lorraine on 2005-06-24
> **mingus]
To reply to your specific questions, can you post back:

* When you installed Ubuntu, did you successfully reboot into and complete the second stage?  In particular, how did you configure apt-get - to use the CD to install packages, or the network?  Were the packages successfully installed?  What we're trying to determine here is whether all the software you need was actually installed.[/QUOTE]I don't think that I actually configured apt-get.  I just ran the install CD.  I did complete the second stage of installation said:**
> * When you boot now you get the grub menu, and can boot into Ubuntu, but get an error booting to W98, yes? Yes
> **mingus] When you mount the Windows drive while in Ubuntu, what is its designation - /dev/???.[/QUOTE] /dev/hde1
[QUOTE=mingus] Your grub thinks that the W98 drive is the 3rd drive as numbered by the BIOS.  There is a file that grub uses to associate its mapping with the system's, /boot/grub/device.map.  Could you post back that file?  Also do $sudo cat /proc/partitions, and post that.[/QUOTE]
/boot/grub/device.map - I forgot this one said:**
> * For your network connection, what do you see in Network Settings?  Are you using DHCP?  Have you tried to ping?  Open a terminal and do $sudo ifconfig, and post that back.
I see my Ethernet Connection as active.  There's a Hostname, a couple of DNS numbers.  domain.actdsltmp is listed under the "Search Domains" tab.

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:C5:5F:58:42
          inet6 addr: fe80::200:c5ff:fe5f:5842/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:823064 (803.7 KiB)  TX bytes:823064 (803.7 KiB)
 	
[QUOTE=mingus]and while your at it, also post back the result of doing $sudo lspci . . .[/QUOTE]0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
0000:00:0b.0 Unknown mass storage controller: Promise Technology, Inc. PDC20267 (FastTrak100/Ultra100) (rev 02)
0000:00:0c.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

---

### Post by mingus on 2005-06-24
Late here and I'm rushing offline, be back in a few days . . .

Took a quick look at your post back:

If you completed the second stage, then you did configure apt-get.  I missed this the first time, too.  You are asked where you want to install packages from; if you say the net, it adds the repositories to /etc/sources.list and tries to download them.  I inadvertently said yes (my wireless wasn't set up yet) and got the same errors you did.  Once your network connection is up, you can do $sudo base-config and this second stage will be repeated and you can get the rest of that software installed and configured.

Re the network.  Your NIC is recognized; it uses the tulip driver.  I suspect it's a matter of tweaking the configuration, which with dsl is specific to your ISP setup and how you are using the modem.  Probably a forum search will retrieve dsl config info.

I'll look into the dsl and grub issues when I return; hopefully others will have chimed in before then.   BTW, if possible, also pls post your /etc/fstab and the results of:  fdisk -l

---

### Post by mingus on 2005-06-25
Again re your network setup . . . assuming your ISP is using pppoe, try . . .

$sudo pppoeconf

pppoe is the protocol most dsl ISP's use, although some use pppoa, entirely different.  It might be helpful if you know this already (the manual or the interface should show you this)

Found posts on google indicating the Actiontec works under Linux no prob; however, over time there have been diff models using diff chipsets.  If you google your model you can find the chipset quickly and then also quickly check for posts indicating issues.

you can also try forum searches . . .

---

### Post by mingus on 2005-06-25
Re grub W98 chain-loading error . . .

gonna need to see device.map, fdisk -l, and /etc/fstab . . .

---

