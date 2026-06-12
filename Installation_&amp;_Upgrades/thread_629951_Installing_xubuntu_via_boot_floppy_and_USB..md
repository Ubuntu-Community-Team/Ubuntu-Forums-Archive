---
title: "Installing xubuntu via boot floppy and USB."
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by sun.stalker on 2007-12-02
Hello I have been trying to install Xubuntu on an old laptop. (IBM thinkpad 770e)
It has no CD drive, and no network.  However it does have a floppy drive and a USB port.  

I have looked through all the user documentation for installing from floppies and installing from USB.  However I am finding they did not work for me.  ( I am very new to linux :), also right now I am using a windows computer and I find the documentation is mostly written for linux users)  

While trying out the USB boot procedure, I found that the BIOS does not support USB booting, therefore I thought why not use a debian boot floppy and from there use a USB with Xubuntu on it?  

When I use the boot floppy I end up with a screen like this:

                Insert the root floppy or plug in a USB storage device.
                Press Enter when ready, or type a command:

is it possible to configure a USB drive to take over from here? If so how does one go about doing it?  
I have a 1GB USB stick waiting for instructions...

---

### Post by daengbo on 2007-12-02
So just inserting the USB storage device that you tried before didn't work when you pressed enter?

---

### Post by baxterdog on 2007-12-02
Read, read, read. I too I am new to Ubuntu, but every problem I found was fixed within minutes by searching first, asking second. Most likely there is someone with the same issue. The guy that got me into linux told me that the best thing you could do is to type into a search engine was your machine and OS. It works.

---

### Post by sun.stalker on 2007-12-03
When I insert the USB stick it does nothing, however I am in no way sure that what I have put on the USB stick is what I am supposed to be putting on it.  I have tried the installation of syslinux, however some of the steps mentioned in the documentation didn't seem to work for me. And I have tried just sticking it in with an image file. :confused:  No luck. 

The documentation covers how to create a boot USB stick.  But wouldn't it be possible to bypass using syslinux on the USB stick because I am already booted using a version of syslinux?  If this is so, what does one put on the USB for the Root step?  For the drivers setup one would obviously use the xubuntu image file, wouldn't they?

Perhaps it is just a matter of me finding the answer in the forums as baxterdog suggested.  Though for the record I have been at this for about a week now, and have read most of the documentation that I can find. :neutral:

---

### Post by daengbo on 2007-12-03
Well, don't give up, and be sure to write all this down in a howto when you get finished ;).

My suggestion is to use that method to install an old command-line version of Debian (not testing or unstable), then get an Ubuntu Gutsy CD, apt-cd add it, and do an upgrade. It **might** work. Who knows.

---

### Post by logos34 on 2007-12-03
Dose this Thinkpad still have windows on it, or is the drive wiped?

---

### Post by dan_hurst on 2007-12-03
I'm trying to do the exact same thing, I'll let you know if I manage to get anywhere.
Don't give up I'm sure it must be possible, sorry I'm not more help at the moment but It's always nice to know you are not alone with these things.
:wink:

---

### Post by sun.stalker on 2007-12-03
Windows is gone, and was useless anyway as I had acquired the laptop in a slightly illegal way, and therefore had no access to the administrator account. :mad: 

And no chance of me giving up as I am having far too much fun.  

Definitely keep me posted Dan! and I will see what I come up with as well.

---

### Post by dan_hurst on 2008-01-21
Well, It's been a while but I think I'm nearly there, unfortunately not an all linux solution but works so Im happy.

I found this site:
  [http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/)
and thought I could use it to prove my hardware can use a boot floppy to kick off a USB stick installation.

However, the boot floppy didn't work, (it couldn't find the linux USB stick).  So after much web searching I came across this:
[http://ubuntuforums.org/showthread.php?t=244918&highlight=linld+install+floppy+usb](http://ubuntuforums.org/showthread.php?t=244918&highlight=linld+install+floppy+usb)

I managed to create a (DOS) boot floppy that loads the USB drivers, detects the USB stick, mounts it and runs linld to boot linux.

Now that I know its possible I'm sure I can make it boot an xubuntu installation from the USB mem stick.

Will let you know how I get on.

---

### Post by dan_hurst on 2008-01-27
I came to the conclusion that ubuntu from a memory stick just isn't going to work so I googled for linux distributions for old hardware and came across Zenwalk.

It worked just fine for me - very impressed that installing Ndiswrapper WiFi drivers was built into one of the desktop menus and worked with very little fiddling.

The old laptop now opens all office documents and allows web browsing at a very impressive speed for such an old machine.  Looks like I'm going to have to find another excuse to by an eeePC :)

---

### Post by MightyAtomz on 2008-01-28
sad to see dan_hurst have given up on ubuntu. I've been searching for a way to boot from floppy and install from USB for a while too. (My laptop also doesn't support usb boot and the optical drive no longer works) 

The closest I've came is 
[http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies](http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies)
Which boots from floppy and can find my usb drive, but wouldn't continue as it only seems to support KNOPPIX. 

Also will instlux work for 7.10? the download site only support up to 6.06. Has any one tried it for 7.10?
(I still got a working XP home in the laptop)

I am very new to linux, but I'll keep searching around.

---

### Post by Stephen Winters on 2008-03-01
> **dan_hurst said:**
> I came to the conclusion that ubuntu from a memory stick just isn't going to work so I googled for linux distributions for old hardware and came across Zenwalk.
The old laptop now opens all office documents and allows web browsing at a very impressive speed for such an old machine. 

To Dan,
   Could you give the links to how you got Zenwalk installed on your old laptop without a CD? I also have an old laptop that doesn't have a working CD and am looking for option of how to get my laptop up and running. I really like what you said that "*The old laptop now opens all office documents*" Was there a tutorial as to whatever your solution was, getting Zenwalk installed without the CD? I'd like to know more. If getting Xubuntu installed on my laptop it too much trouble, I may want to try Zenwalk. It sounds like your solution might also work for me.

**[SIZE=2]To Any Ubuntu Users[/SIZE]**
I also have an old laptop (Sony Vaio PCG-9411 - 550 Mhz with 640K system RAM and 187M Extended RAM ) that has two USB slots, the CD doesn't work, the HD has been reformatted (nothing on it), and it has a working floppy drive and a telephone jack. The bios will only allow booting from the HD, floppy, and CD (which doesn't work). I'd rather get Ubuntu  installed on the laptop. But I imagine I'll have to install Xubuntu because of the low Mhz and low RAM of my laptop. Any help or suggestions would be greatly appreciated.  (just a note, if I were to find a way to add more RAM, would Ubuntu work on the  laptop (assuming I can find a way to get it installed)? I really like Open Office 2.3 and would like to be able to run it on the laptop, if possible)

I'm a new Ubuntu user. Because I have Ubuntu on another computer,   I'd like to stay with some form of Ubuntu, BUT, I'm open to whatever will work. I want to get my laptop up and working very soon (even if with another Linux, such as Zenwalk) than have it remain unusable. So, it you have a link of someplace to use a floppy to boot some Linux from USB, much appreciated.
[B][SIZE=3]
Boot From a USB Drive?[/SIZE][/B]
Now, with that said, I did come across this website. [WeetHet - Boot from USB Flash drive]("http://www.weethet.nl/english/hardware_bootfromusbstick.php")   I don't have time to try this out yet (Being new to Ubuntu, a lot of this stuff is new to me so I'd have to study out a lot of it, which would make it take longer.), but hope to try it out later when I get some free time. I thought some of you more knowledgeable Ubuntu users might be able to test it in the mean time.

Best Wishes,
Stephen

---

### Post by theonlygolux on 2008-03-01
I had the same problem and overcame it (at least partially) by taking the hard drive out of the old laptop and putting it into a laptop with a CD drive, then I just ran the Xubuntu boot disk I had on CD.  Worked, only it didn't install the GUI, so I am left with a command line I don't know how to use, being new to this.  I am still trying to find a way around this that doesn't involve doing the whole thing over again, but theoretically it should work, I was just unlucky with my laptop.

---

### Post by dan_hurst on 2008-03-09
Hi, I managed to get the Zenwalk installer to run from a USB flash stick using the DOS boot disk method described in one of my previous posts.  If you need help getting this to work let me know, it took a bit of playing with batch files to get it to work.

However, part way through the installation process (I think just after I told it how to use the whole HDD for the installation) the system seemed to hang.  I think this may be because it was trying to use loads swap space on the flash memory stick and this was way to slow.  My laptop only has 128M of RAM.

Out of desperation I tried the CDROM drive again (that I thought was broken) and Zenwalk installed fine.  Must have been a corrupt sector that Ubuntu needed but Zenwalk didn't.

Another option may be to get a usb CDROM drive and install from that - don't know how hard that would be to make a boot disk for but probably do-able.

---

