---
title: "Installing Xubuntu on Tablet"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by otherguy on 2006-09-20
Hi all. I have a Fujitsu Stylistic LT c-500 tablet that i'm trying to install Xubuntu on. 
This is kind of a unique installation, being relitively new to the linux world (as far as installing it goes) I need a little help.

This tabled doesn't have a built in NIC, a CD rom drive or a floppy drive. It also cannot boot from USB. It does have a PCMCIA slot and i can connect to my WAP (after the OS is intalled).

I can however place the hdd into my laptop and computer to transfer files/install/setup whatever i need to do. The laptop has network and bootable CD and floppy if needed.

My friend previously installed ubuntu on the tablet but i'm not sure on the specifics. I do know that he managed to download all the required packages using my laptop, then initiated the installation inside the tablet. Once linux was installed he then setup the wificard in the tablet, and finished getting the rest of the installation.

I've looked through the documentation and guides on the wiki but i dont see a method that would work in my case.

Can anyone give me a link to a guide which is relevant or some help getting started?
I have absolutely no problem reading guides... i just cant find one.

Thanks in advance,
Jim

---

### Post by otherguy on 2006-09-21
bump

---

### Post by otherguy on 2006-09-24
honestly,nobody can think of a way to do this?

---

### Post by dan_kent on 2006-09-25
hello

I've got a Fujitsu Stylistic 3400 with similar probelms as yours - no nic, cd drive etc.

The way I managed to install xubuntu was as follows

Remove the hard drive
Get an ide to laptop drive converter cable (only a couple of quid)
Connect the converter cable to a donner pc and install x/ubuntu
When the install has finished reboot and install the pcmcia packages
Shut the pc down, remove the drive and put it back into the fujitsu
Boot the tablet. X will fail to start but you can do 'sudo dpkg-reconfigure xserver-xorg' and this will let you reconfigure x
You should then have a working laptop

---

### Post by otherguy on 2006-09-26
Yea, this is actually exactly what I ended up doing (but i installed ubunto in my laptop, although i  do have the 2.5 to 3.5 IDE adapter you're talking about).

Is this an appropriate way to install though? My laptop has a P4 and the tablet has a celeron i think. Are the packages not compiled for the processor using the live CD or something?
As i said before, I'm new to the linux installation world.

It appears as though everything's functional. I'm working on getting the touchscreen drivers working. I've found a few pages outlining the process, but for some reason their instructions arn't working.

---

### Post by dan_kent on 2006-09-27
the p4 and the celeron are effecily the same same thing the linux kernel, you should find that either the 386 or 686 kernels will work for you. If you wanted to you could recompile the kernel to make it more specific but it's probably not worth the bother.

Any pointers to those how to for the touch screen would be great.

---

### Post by otherguy on 2006-09-27
for the sake of people stumbling across this post in the future, i'll include the relevant portion of the e-mail I sent.

> The links which i was looking at specifically reference the [fpit driver]("http://packages.ubuntu.com/dapper/x11/xserver-xorg-input-fpit") (link: ubuntu fpit driver package)

If you're not familiar with the fpit driver, it's designed specifically for the fujitsu tablet touch screens.
more info on fpit [here]("http://www.xfree86.org/current/fpit.4.html"), as well as a guide to getting the screen working (didn't seem to work for me).

And another similar guide to the one on the fpit page is [here]("http://www.neurath.org/stylistic_lt_c500/"), check section 4.2.
It seems that the person that made this page outlined the installation process, but they used SUSE.

If i end up getting it working i'll update w/ more info.

And if anyone out there has any info on how to get the touchscreen working on a Fujitsu Stylistic tablet, feel free to let me know :)

---

### Post by otherguy on 2006-10-27
Still no ideas?

---

### Post by john_spiral on 2006-10-28
hard disk install?

(1)place drive into another computer
(2)format drive into 2 partions (ext2), one just large enough to take xubuntu .iso, initrd.gz and vmlinuz files

pickup files from below

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

(3) place above files into smaller partiton
(4) Install grub onto drive, edit menu.lst with xubuntu boot options, search forums for installing from hd or
 hardisk
(5) throw drive back into machine
(6) viola? Hopefully all should work a treat?

johne

---

### Post by john_spiral on 2006-11-06
any progress on this otherguy?

---

### Post by bcw on 2006-11-16
Please check these options:
[http://www.ubuntuforums.org/showthread.php?t=224191](http://www.ubuntuforums.org/showthread.php?t=224191)
[http://www.ubuntuforums.org/showthread.php?t=244918](http://www.ubuntuforums.org/showthread.php?t=244918)

I have Kubuntu and Xubuntu Dapper on my Fujitsu ST3400s and ST5032. The floppy drive helps with the ST3400s. As Ubuntu auto-detects hardware at boot, there is no real problem installing to the hard drive in another machine first.

Cheers,
Bret

Handwritten with the stylus via xstroke on a ST5032.

---

### Post by benpleasedover on 2007-07-04
Hi all,

I wanted to do the same thing, I basically did the same thing that "john_spiral
" mentioned above, then I found this forum. The thing is that Grub hangs with a "GRUB _" message now. I assume stage one of Grub is hanging because the device map (the thing that maps bios hardware addresses to Grub addresses is all wrong. Its wrong because I installed Grub on another machine, or thats my guess. Anyone out there try the same method? and how can I edit grub without pulling out the hard drive again? Lastly, how can i find out the correct device map for this Stylistic LT?

Thanks

P.S. Whats better, Ubuntu or Debian

---

### Post by bcw on 2007-07-06
Hi,

Try this:
[http://www.linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://www.linuxmint.com/wiki/index.php/How_to_repair_your_grub)

> P.S. Whats better, Ubuntu or Debian

This is a nonsensical question.  The proper question is "What's better for me, Ubuntu or Debian?"

How would we know?

Cheers,
Bret

---

### Post by benpleasedover on 2007-07-19
i ended up installing debian  using another machine, then when it came time for the first reboot, i popped the hard drive into the tablet pc, and it worked.

thanks!

---

### Post by themischiev on 2008-06-26
Stylistic 3400 Harddrive Image For Download?

Please Someone Have An Image Of The Fujitsu Stylistic 3400 Hard Drive With Ubuntu Installed That I Could Download And Copy To My Stylistic 3400 Hard Drive?

---

