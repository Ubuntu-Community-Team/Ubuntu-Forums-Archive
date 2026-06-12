---
title: "Help Installing on Toshiba Portege M200"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by skidoo on 2007-05-08
I've seen that several people on this forum have Ubuntu installed on the Toshiba Portege M200 (running WinXP Pro Tablet Edition), but there was very little detail as to how they got it to work. 

Details: This laptop has no CD/DVD drive or floppy drive. It does have 2 USB ports, but the BIOS does not recognize them for booting. As well as a PCMCIA slot (if you have a 'supported' PCMCIA CD drive then it boots, which I do not). It can boot from an SD-Card, but it is only good with a valid 'boot image', if I found a boot image that supported an external USB CD drive, I'd be good to go. Otherwise you can boot via the network (PXE protocol), but I do not have an install server available.

Here is what I've been looking at:
-[Fedora Core 4 Install]("http://www.freewebs.com/duckzland/m200.html"), the SD-Card + USB drive method seems possible, but where do I get the Ubuntu 'boot image' (for the SD-Card) and would it recognize my USB CD drive?
-The [Smart Boot Manager]("http://sourceforge.net/projects/btmgr/") looked like an option but after trying it and reading its documentation it looks like it does not support USB CD drives. 
-Looked at modifying the WinXP boot loader's boot.ini file to attempt to boot from a USB CD drive, but I have not found any documentation for this to work.
-Tried [USB under DOS]("http://www.addonics.com/support/faqs/windows_OS_installation.asp") as a boot image for my SD-Card, it recognizes my USB CD drive like a champ, but don't know how to get the CD to boot itself from there.
-Looked at [GRUB for DOS]("http://sarovar.org/projects/grub4dos/"), but cannot figure how to get it to recognize a bootable USB CD drive. If I could get it to boot from a USB jump drive that would be fine too, but how?
-A possibility I found tonight was [instlux]("http://sourceforge.net/projects/instlux"), which looks promising but I'd like to know it worked installing the newest Ubuntu for someone with an M200 before I jump into the fray and fry my drive. Plus I could find no documentation anywhere on it.
-There is also the option of putting the hard drive in a different laptop, installing Ubuntu onto the drive and then putting it back into the M200, but before I do that I'd really like to find a solution that lets me boot from the USB CD drive. I've also seen that you have to change your gnome settings and possibly other settings to match the new system with this method.

This is where I am at so far, suggestions and comments are welcome!
It would be terribly convenient to find a solution that would allow me to boot from my USB CD drive, to install the normal way, as well as have the ability to re-install WinXP via DVD if something goes wrong in the future.

Thanks,
skidoo.

---

### Post by slartimitvar on 2007-05-25
The m200 bios does support booting from usb but there are only a few usb cd or dvd drives which work with it.  I installed Ubuntu on my m200 using a Lacie usb dvd burner.

Check out this thread on [tabletpcbuzz]("http://tabletpcbuzz.com/forum/topic.asp?TOPIC_ID=12697") for a few that work.

---

### Post by ndavenport on 2007-05-27
The way I did it was using the TFTP32 server for windows and doing a net install.

Once you have done that there is some playing around with xorg.conf and stuff to get the automatic rotation working but just  pm me and I will give you my email and walk you through it if you like.

I did this install about a week ago so it's fresh in my mind :-)

---

### Post by ManOfMilk on 2007-05-31
I've also got this installed on my laptop and it works great.

I'm interested to hear how you got the screen to auto resize... are there any linux tablet programs that do the journal features, or handwritting recognition?

I'm new to linux in the tablet world...

-G

---

### Post by ndavenport on 2007-05-31
Hi,

I mashed up a few different xorg.conf's the get the resolution right and I use a small script I also mashed up from different sources to handle the screen rotation, it uses RRand that comes with the propriety nvidia drivers.

Xournal is good, apparently its like Microsoft's Journal but I haven't used that one, it also anotates pdf files so if you want to make notes on a business presentation or university lecture you can just scribble on the pdf and save it.  Very handy.

No handwritting recognition yet, found a press release saying it was comming and a online utility that can be used but quite frankly it's not up to scratch.

You can use xKbd for a nice onscreen keyboard but until someone does handwritting under X the linux tablet dream will only be half filled.

---

### Post by Riven on 2007-06-01
I have the very same notebook and want to rotate the screen too, i'm sending you a PM ndavenport :)

---

### Post by skidoo on 2007-06-10
Well, I tried to netboot using tftpd, I got it to work but I think I had the wrong files from the ubuntu install netboot directory. 

What I ended up doing was installing with wubi, and it all works just fine now. Recognized my wireless and connected like a dream, my external usb cd/dvd drive is recognized and reading properly (have not tried to burn anything yet). The not open source nvidia driver was recognized as needed and installed just fine. I am familiarizing myself with the gnome and trying to make sure I have any alternatives I need for my windows programs.

Still need to install the screen rotation script and the tablet specific things. The installer already has the toshiba utilities installed, and the wacom driver. So the pen works, but no right click and I have no programs yet to "write on" with it, so that is still to do.

---

### Post by isaacjun16 on 2007-06-29
Hello, I have a Toshiba M200 and I'm using a external DVD-Rom Targus NWDVD04, I'm just worried if you had to use the Ubuntu Live CD or the Ubuntu Alternate to install Ubuntu because I having problems with the live CD.

/bin/sh: can't access tty; job control turned off

I little help!! :(

---

### Post by cb2001 on 2007-07-18
Can somone post a walkthrough of netboot ing for a Toshiba portege  m200. 

Some of the questions I had,

Did you use the install dir from a installation CD or download netboot.tar.gz?

Is the default netboot.tar.gz (feisty) enough, or do you need to get ethernet drivers on a SD card first?

TIA
-cb

---

### Post by hh93 on 2007-08-29
> **isaacjun16 said:**
> Hello, I have a Toshiba M200 and I'm using a external DVD-Rom Targus NWDVD04, I'm just worried if you had to use the Ubuntu Live CD or the Ubuntu Alternate to install Ubuntu because I having problems with the live CD.

/bin/sh: can't access tty; job control turned off

I little help!! :(

Try Wubi then, just like skidoo did.

---

### Post by isaacjun16 on 2007-09-13
Hello

When I install  Ubuntu 7.04 (Feisty Fawn) I was using an external DVD Targus NWDVD04 (PC Card DVD) I was able to boot from the CD of Ubuntu 7.04 Alternative and see the menu but when the installation attempt to look for CD-ROM hardware it didn't   saw nothing sow what i did was boot I connect two CD-ROM one was the  Targus NWDVD04 I use this one to boot and One in the USB Port (I think so it don't concern the model) both whit a CD of Ubuntu Alternative Inside   so when the installation look for the CD-ROM it found the one in the USB CD-ROM, after that I went great the installation.  

Good Luck and sorry for my English.  :guitar:

---

### Post by UofLSpeed on 2007-09-18
Here's a pretty good howto for setting up a PXE server on ubuntu.

[http://www.howtoforge.com/ubuntu_pxe_install_server]("http://www.howtoforge.com/ubuntu_pxe_install_server")

---

### Post by solar george on 2007-11-29
If any one is interested then [cellwriter]("http://risujin.org/cellwriter/") is a good handwriting recognition program for linux - I'm using it to write this post.

---

### Post by Danners on 2007-12-17
Hi,

I'm having no joy whatsoever getting ubuntu installed on my portege m200 :(

I've attempted a pxe install, that's throwing up a PXE-E53 error, no bootfilename received. It looks like my laptop is being assigned an IP ok, though. I've followed this guide ([https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)) as closely as possible, I am however running tftpd32 on my vista machine so I can't follow it exactly.

I've also tried a bootdisk install with an external usb floppy drive, that boots OK, but it starts installing debian and I can't figure out how to make it install ubuntu.

Anyone have any suggestions?

Thanks in advance.

---

### Post by solar george on 2007-12-17
> I am however running tftpd32 on my vista machine

Is this the machine running the dhcp server.

Make sure that any other dhcp servers are disabled.

Try to contact the server using a tftp client.

You could try using knoppix's built in network boot and swaping the files.

I would suggest that you use the net install images from [here]("http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/") instead of trying to boot a full livecd.

---

### Post by Danners on 2007-12-18
Cheers for the help, I did have DHCP disabled on my router, but it seems it was still interferring. I unplugged the router and it worked fine. Had to unplug the desktop and replug in the router once the installer had finished loading and redetect the network settings to be able to connect to the archive but other than that everything ran just fine!

I'm now a proud owner of an M200 with Ubuntu :D

---

### Post by Shrek X on 2008-02-06
Hi all

I figured this would be the best place to jump in here.  I also have the M200, and no OS on it at all except for DOS.  I have my PXE setup with no problem (vista system), but cant figure how to get the install started for ubuntu.  

Any ideas?  

Thanks in advance.

---

