---
title: "Buffer I/O error on device sr0, logical block"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Kalec on 2008-12-02
Whenever i try to install Ubuntu i get this error 
"Buffer I/O error on device sr0, logical block 1147534"
"end_request: I/O error dev sr0, sector9180280" the error just repeats over and over again. Any ideas?

---

### Post by __Ryan__ on 2008-12-02
This usually pops up when the installer can't read the CD. I had the same issue until I burned another ISO image.

---

### Post by Kalec on 2008-12-02
> **__Ryan__ said:**
> This usually pops up when the installer can't read the CD. I had the same issue until I burned another ISO image.

I've  burnt over 10 copies now, do you think its my disc drive? I thought it might be my disc drive earlier when i kept getting the error i was just hoping it wasn't because i only have one working disc drive.

---

### Post by __Ryan__ on 2008-12-02
Try the LiveCD on another computer.  It will either prove it is the CD or some other problem with the computer itself.

---

### Post by Wazzy on 2008-12-02
This error is telling you that you are unable to read the CD drive.

This doesn't necessarily mean that the disk has not been burned correctly. 

It could be a problem with the IDE...try the following:
[LIST]
[*]Put in the CD
[*]When you get to the menu press F6 (I think, don't have it in front of me)
[*] Add the following (without the quotes) to the end of the parameter list that appears at the bottom of the screen, "irqpoll all_generic_ide=1".
[*] Now try run it from the CD. You'll need to do this for the install and the live view.
[/LIST]

Check this works off the CD before installing.

Hope this helps.

---

### Post by Kalec on 2008-12-02
> **Wazzy said:**
> This error is telling you that you are unable to read the CD drive.

This doesn't necessarily mean that the disk has not been burned correctly. 

It could be a problem with the IDE...try the following:
[LIST]
[*]Put in the CD
[*]When you get to the menu press F6 (I think, don't have it in front of me)
[*] Add the following (without the quotes) to the end of the parameter list that appears at the bottom of the screen, "irqpoll all_generic_ide=1".
[*] Now try run it from the CD. You'll need to do this for the install and the live view.
[/LIST]

Check this works off the CD before installing.

Hope this helps.

I'm still getting the same error and i even switched disk drives to one i know is working.

Any ideas?

---

### Post by __Ryan__ on 2008-12-02
It looks like your not burning valid disks from that burner. You need to try burning a disk from another machine. It could be the software you are using to make the CD or the drive hardware itself I'm guessing.

---

### Post by Kalec on 2008-12-02
> **__Ryan__ said:**
> It looks like your not burning valid disks from that burner. You need to try burning a disk from another machine. It could be the software you are using to make the CD or the drive hardware itself I'm guessing.

Do you have any recommendations for software?

---

### Post by __Ryan__ on 2008-12-02
Are you burning the CD in Windows or Linux?

---

### Post by Kalec on 2008-12-02
> **__Ryan__ said:**
> Are you burning the CD in Windows or Linux?

Windows XP, I've tried bruning it with InfraRecorder and Burn my Files on 1x but even though i click 1x the programs seem to ignore that and write at like 2.4x-4x

---

### Post by Kalec on 2008-12-02
Nevermind this topic i tried my XP disc and it was working so i just installed it instead. Thanks for trying everyone i appreciate it.

---

### Post by __Ryan__ on 2008-12-02
Ouch...

---

### Post by kelean on 2008-12-02
One other thing it might be a bad batch of disks.  I had that same problem.  I bought a different brand and everything is good now.

---

### Post by aqws0987 on 2008-12-02
I am having this problem as well.

Any solution to this error

---

### Post by __Ryan__ on 2008-12-02
Again this is either Bad CD, Bad Burner, or Bad Reader.  Try the CD in another machine and see if the LiveCD will boot up. It will eliminate one of the possibilities.

---

### Post by timle53 on 2008-12-17
Not sure if this helps, from a long time Unix/linux user.

About 2 weeks after upgrading to 8.10 I could no longer write CD-Rs or DVDs.  I could read them ok and was kind of blaming 8.10.

After trying several applications to create a CD/DVD and all failed I looked in /var/log/messages and /var/log/syslog and saw my error that lead me here.

My resolution turned out to be replacing the CD/DVD burner.  It was less than a year old but - well it worked for me.

---

### Post by Aijse on 2009-01-01
Hi,
I also had this error.
Tried several destros several times, but none worked and all gave this error. They were all created on a winxp machine.
Then I popped in an old cd that I had burned on my macbook and this did work!
Now I burned a new cd from an Ubuntu machine and it works!
Hooray

---

### Post by br3athe on 2009-01-10
I had this same problem , looking around these forums it seems that you need to either burn the ubuntu image at a very slow speed ( which didnt work for me ) or burn an image on an existing ubuntu machine to a cd , this did work for me , so if you have a friend with ubuntu ( or I someone had had success burning the image on a mac ) then burn the image on the ubuntu machine and try again , this worked for me :)

---

### Post by ejprinz on 2009-02-01
I had the same issue on several PC's with a verified LiveCD iso image. The issue went away when I wrote the iso image onto a DVD instead of a CD. I now burnt another CD following the instructions at [http://www.troubleshooters.com/linux/coasterless.htm](http://www.troubleshooters.com/linux/coasterless.htm) and don't have the issue anymore. One has to add the "padsize", "-pad", and "-dao" options to cdrecord, e.g. "cdrecord dev=0,0,0 speed=10 blank=fast padsize=63s -pad -dao -v -eject".

---

### Post by fhco on 2009-02-01
I've thought of making a different thread, but this issue has stopped me from being able to use 8.10 (and the new Jaunty alpha as well), and I didn't get the error when trying to install from a disc.

I was using 8.04 successfully since its release, then when I used the software upgrade option to upgrade to 8.10, upon restarting the machine I got the continual I/O buffer errors. It was only after that, that I tried disc installs (CD, DVD, multiple copies, md5 checked), flash drive installs, and even Wubi installs, and none of them have been successful.

The fact that this error occurred just by doing a software upgrade says to me that it is a kernel issue in my case, not necessarily a media issue. I have been using Ubuntu since Dapper and I've never had anything like this happen that stopped me from using the software completely, but it is beyond frustrating.

---

### Post by Hexagrapher666 on 2009-02-03
I tested EJPrinz's notion that this is a kernel issue in 8.10 which prevents proper communication with certain optical drives.  I had a machine in which an 8.10 LiveCD produced a stream of I/O errors on dev sr0, but an 8.04 LiveCD booted without any errors.  

> **Kalec said:**
> Whenever i try to install Ubuntu i get this error 
'Buffer I/O error on device sr0, logical block 1147534'
'end_request: I/O error dev sr0, sector9180280' the error just repeats over and over again. Any ideas?

> **ejprinz said:**
> I had the same issue on several PC's with a verified LiveCD iso image. ...something is wrong in the 2.6.27 kernel for some CD drives.

---

### Post by FredCrocket on 2009-02-03
I have the same problem, with Ubuntu and Xubuntu. I tried an other Linux (TinyMe), burned a CD and tried it: no problem! Anyone any ideas?

---

### Post by Rudedawg on 2009-02-04
I too am getting a similar message: 

[ 303.720827] Buffer I/O error on device fd0, logical block 0  

that repeats with the initial numbers changing on each line. This error only comes up after making a selection from the ubuntu menu. I've tried the disk I just burned yesterday of 8.04LTS and a disk with 8.10 that I had and had used in the past for installs on other machines. 

I have 3 SATA devices in my box. The dvd drive, a HD with Windows Vista on it, and A 2nd HD that has no formatting on it yet. After work I'm going to try to unplug the unformatted SATA drive to see if that makes a difference since fd0 would seem to mean "fixed disk 0". Not sure what sr0 might mean though.

---

### Post by anandi on 2009-02-04
Is there a solution for this yet ?

In the end i created a usb boot disk, booted the machine using that, and then ran the install. But i do fear about the non working of the cd drive.

Searching on google revealed several people facing similar problems, however all suggestions mentioned failed for me.

---

### Post by Rudedawg on 2009-02-04
Most of the threads about this seem to recommend reburning the iso on a dvd instead of a cd. This could be viable since most pc's are now built with DVD-roms as a standard. I know I'm going to try it when I get home today.

---

### Post by DenesL on 2009-02-04
My 2 cents for what is worth:

Downloaded and burned 8.10, CD check says:
end_request: I/O error, dev sr0, sector 1305224
Buffer I/O error on device sr0, logical block 162153

Burned again, same error.

Replaced DVD with 50x CD including cable. Same error.

Downloaded 8.04.2 LTS, no problem (same burner).

Checksums: all OK.

---

### Post by ghettofreeryder on 2009-02-04
I believe if you burn using DAO instead of TAO, it will work.  It did for me and ubuntu server anyways

---

### Post by anandi on 2009-02-06
> **ghettofreeryder said:**
> I believe if you burn using DAO instead of TAO, it will work.  It did for me and ubuntu server anyways

And how to burn via DAO ? I had burned the iso image on my mac laptop (under osx). And if its just the burning issue, why doesn't it appear for LTS, and just for this very release ?

---

### Post by williamh120 on 2009-02-08
I'm having the same problem.

I've now burnt the CD twice, using the same drive and Nero 8 on both occasions, although at only 8x write on the second occasion.

I have had no difficulty in installing Windows XP on the drive in the PC I'm trying to install Ubuntu Server 8.10 onto, so I don't think there's anything wrong with the CD.

Interstingly, when doing a test boot from the PC I burnt the CD with (not the one I'm trying to install on), I also got these error messages when I used Ubuntu's own built-in CD checker on the disc, but after that it reckoned the CD was valid.

I don't get this at all.

---

### Post by jackblow33 on 2009-02-10
Have had the same problem, have tried some of your suggestions.
Heres my fix: 
Ive bypass the problem with a usb dvd rom drive.
The problematic optical drive was a s-ata on a dell dimension 521.

---

### Post by barraymian on 2009-02-11
dito here. I've tried everything. burned cds from different computers (all windows), different speeds, checksum of the iso was fine as well, downloaded iso again just in case, cds from different boxes, and i also tried different drives to read for my computer to no avail. The only thing i have not tried is burn the image on dvd so lets see. 

Ubuntu is supposed to be better, stable, secure and all of that compared to windows but if everybody is gonna keep having the basic issue of installation then wuts the point if in the end i am gonna bang my head on the computer. I do that with windows already but at least i've something working there, i can't even install Ubuntu. 

To be very honest, all the great things i heard about Ubuntu are kinda useless for me at this point, i am kinda disappointed. I am probably going to go back to piece of crap windows cause at least i can install if few more tries doesn't do it for me

oh i must mention, i did work once, it started installing but my luck would have it that i realized that it was installing on the wrong drive so i turned off the machine and it never worked again.

---

### Post by strack on 2009-02-17
Had the same problem. Burned to a CD-R didn't work. Threw up an endless list of the mentioned error.  Solved it by burning to a DVD-R. Everything worked. This was an older machine with a DVD drive in it.

---

### Post by redchuck on 2009-03-03
I've having an identical problem with an 8.10 based livecd.  The same physical CD works on other drives and other distro livecds work on this hardware, so it is not a hardware problem.  Something is broken with 8.10's cdrom support.

I'm going to play more with boot options (irqpool, all_generic_ide=1 and noacpi and been suggested), and burning to a DVD instead of a CD, but it would be nice if this worked out of the box.  I'm working on standardizing my enterprise on Ubuntu desktops and servers so I don't want to have to switch to Knoppix for livecd tools.

---

### Post by RDSR2k on 2009-03-04
I had burnt the Ubuntu v8.1 desktop installation to cdr on two different machines and tried three different cd rom drives to try and install and received this error everytime!  I found an article that discussed the following that I tried... I used the burning util "InfraRecorder" and burnt the iso at 2x on my recorder.  I'm not sure the application had so much to do with it as recording at the lower speed... but now it's installing fine.  Only thing now is...when the machine boots up, it allows me to login fine, with sound even, but ends up with just the mouse pointer, which works, and an orange screen. Any suggestions? My first time installing this Linux distro btw.

RD

---

### Post by Myxb on 2009-03-04
I am now in the middle of migration to a bigger drive. The system dual boot XP and Ubuntu 8.10. During initial installation everything went fine but when today I try to load from a CD with 8.10 Live, I get the message.

I burned the same image to a DVD disk (not a CD!) instead and then booted successfully.

---

### Post by nekorb on 2009-03-09
I've got a thread going on as well (nothing in it apart from suggestions to burn at a slower speed) but here's what I've tried to do so far & still getting the error:

- It is a new PC - Intel Quad core, Supermicro C2SEA mobo, SATA DVD drive & HDD.
- Downloaded the amd64 ISO twice (different mirrors to) & burned it once per download. At 1x speed also.
- Using the IDE DVD drive from old PC (which works fine with Ubuntu 8.10 x86 on my old PC) on the new PC.
- Using the Ubuntu 8.10 x86 CD on the IDE & SATA DVD drive on the new PC. Ubuntu is installed on my old PC with this exact same x86 CD.
- Kubuntu 8.10 x86 gives the same error (I had the CD floating about).
- Boot options I've tried various combos of the ones you get when you press F6, such as noapic, nolapic, acpi=off, acpi=noirq. With noapic, nolapic & acpi=off I got a new error before the one I'm posting about appears, it said "BIOS bug APIC #0 not detected. Forcing use of dummy APIC emulation".
- In the BIOS - changed APCI from 2.0 to 1.0 (no option to disable it). Setting the DVD drive to UDMA0 from UDMA2. Disabling all unused ports (serial, paralell, all the PCI, onboard VGA). Reset BIOS to safe defaults.
- Installing Debian 5 & Fedora 10 (both amd64) work fine. Downloaded & burned using my SATA DVD drive.

---

### Post by dar2kas on 2009-03-09
I have the same issue - In bios if u disable virtualization, so it's fine. I though there was a problem with my cpu - it doesn't support virtualizatyion, but I changed it still gives me the same error.

---

### Post by bsouth19 on 2009-03-10
i had this same problem.  about 30 minutes ago i popped in a dvd drive to my box and burned the 8.10 iso to a dvd.  i booted and it worked.  ubuntu installed just fine, however when i did the initial reboot it took a long time for the login screen to appear and once it did and i logged in, it just freezes at the orange background.  the mouse cursor is present and movable, but i just sit at a blank orange screen.

anyone?  help?  please?

---

### Post by betogf on 2009-03-13
If all suggestions fail, try 8.04 with 'all_generic_ide=1' appended at the end of the command you get when pressing F6 (but before '--'). Also, doing the install from the beginning (as opposed to load the live CD first) seemed to help me fix another problem I faced (errno 5). I have a Dell PowerEdge sc420. Don't give up and good luck!

---

### Post by betogf on 2009-03-13
I got rid of this error by typing 'all_generic_ide=1' in the F6 command. Also, if you face an errno 5 when installing, you might want to consider installing it from the first screen, as opposed to load the live CD and then install it from within. This all worked for me with 8.04. 8.10 was full of errors on my box (Dell PowerEdge sc420). Good luck!

---

### Post by dankles on 2009-03-21
I get this error as well on two different machines only with ubuntu 8.10.I can install despite the error, though its 3 times as long as it should on the commandline installer. Version 8.04 works, slackware works, opensuse works, centos works, fedora works.... 
I'm disipointed ubuntu!

---

### Post by The Pinny Parlour on 2009-03-25
Samsung optical drives? I get this error all the time whenever I use Samsung optical drives. The one I get errors with right now is: TS-H653

---

### Post by johnnyb0y on 2009-05-05
Ever since upgrading from Intrepid to Jaunty, I get the following error daily in syslog:

May  5 06:17:50 DOGGY kernel: [75610.795860] Buffer I/O error on device sr0, logical block 0
May  5 06:17:50 DOGGY kernel: [75610.795874] Buffer I/O error on device sr0, logical block 1
May  5 06:17:50 DOGGY kernel: [75610.795881] Buffer I/O error on device sr0, logical block 2
May  5 06:17:50 DOGGY kernel: [75610.795887] Buffer I/O error on device sr0, logical block 3
May  5 06:17:50 DOGGY kernel: [75610.795893] Buffer I/O error on device sr0, logical block 4
May  5 06:17:50 DOGGY kernel: [75610.795899] Buffer I/O error on device sr0, logical block 5
May  5 06:17:50 DOGGY kernel: [75610.795905] Buffer I/O error on device sr0, logical block 6
May  5 06:17:50 DOGGY kernel: [75610.795911] Buffer I/O error on device sr0, logical block 7
May  5 06:17:50 DOGGY kernel: [75610.795919] Buffer I/O error on device sr0, logical block 8
May  5 06:17:50 DOGGY kernel: [75610.795925] Buffer I/O error on device sr0, logical block 9

The tray of the CD-ROM/DVD drive is open so I don't know exactly what is going on here.

I always check my syslog and I know that I've not received this error before.

I'd love to know why it reports an error even when there's no CD/DVD AND the tray is open.

Perhaps it's BECAUSE the tray is open? Who knows?

Info on drive clipped from syslog shown below:

May  4 09:17:57 DOGGY kernel: [    2.528410] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.50 PQ: 0 ANSI: 5
May  4 09:17:57 DOGGY kernel: [    2.532769] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
May  4 09:17:57 DOGGY kernel: [    2.532772] Uniform CD-ROM driver Revision: 3.20
May  4 09:17:57 DOGGY kernel: [    2.532849] sr 0:0:1:0: Attached scsi CD-ROM sr0
May  4 09:17:57 DOGGY kernel: [    2.532880] sr 0:0:1:0: Attached scsi generic sg1 type 5

Regards

John Goodwin

---

### Post by snahrck on 2009-07-08
I'm having, the same issue using a USB flash drive. Detail: this USB flash drive boots fine in another computer. So, I don't thing it is media or drive related.

---

### Post by chappajar on 2010-04-28
This post is a bit late for this thread, but for any future viewers looking here for an answer to this problem:

obviously, like many other posts here already say, this is a cd burn/read/disc problem.

To maximise your chances of burning a usable disk (as well as using the lowest possible burn speed - Brasero won't let you select this but K3b will) only burn a MinimalCD, around 20 MB, which will download the install files from the internet as it installs.

 [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by spalj on 2010-05-02
I got past this error (and the many others) by cleaning (the very infrequently used) optical drive on the machine.  I used a cd cleaning disk.  Prior to cleaning the liveCD  disk, the integrity check would report errors.

---

### Post by kleinebre on 2010-08-13
> **Kalec said:**
> I've  burnt over 10 copies now, do you think its my disc drive? I thought it might be my disc drive earlier when i kept getting the error i was just hoping it wasn't because i only have one working disc drive.

You can verify if the disc is valid with the tools supplied on the disc.

If the disc is 100% you can still have a problem installing if your RAM memory is hosed- I've had this happen and it's no fun troubleshooting because bad RAM is the last place you'd normally look (this was after re-downloading, re-burning and replacing the CD-ROM drive and hard drive).

Try running MemTest86 and see what that gives you. Just mentioning because it's easy to overlook! 

In my case, surely enough MemTest86 showed errors. Once the RAM in said machine was replaced, all worked fine.

---

### Post by surfer on 2010-08-13
or, if you have an usb port, you can put the iso on a flash drive and install from there.

---

