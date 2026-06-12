---
title: "Replace Windows, HP dv6911 om laptop, new hard drive"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by AlphaMero on 2012-03-12
Hello everyone,
 
 
I am new to the ubuntu world, first off i want to say ):P. Very happy about stumbling onto the world of linux. I was wondering if anyone would be interested in helping a complete newbie try and install ubunto on a computer with some issues? I dont really want to post a novel and have no responses. I have done this many times and have basicaly gotten a "good luck with that" response
 
basics
 
computer wont fully boot
vista home premium 32x; normal startup once every 30 or so boots
error sometimes (not often)= missing operating system
sometimes boots from disk
installed Ubuntu and it boots around once every 15 power ups.
new 500G hdd, same problems as above
 
Can anyone walk me through fixing this? so far what I come up with is I need to set up a new partition and add a master boot record. I have no idea how to do this and cant seem to find info that would go with my situation. How do open "shell" for commands? Are there any programs that i can load to disk or usb, to be able to actualy control computer? Do i have to have vista installed on the machine in order to run? Any help greatly appreciated, im willing to try all possible fixes before I smash this thing to bits Office Space style. 
 
Thank you so much for your time
 
Mero
 
What we're working with:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01512668&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3747900](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01512668&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3747900)

---

### Post by oldfred on 2012-03-12
Welcome to the forums.

If two different operating systems and two different hard drives only let you boot one out of 15 times, something else must be wrong. 
Are all connections tight?

You do not have to have Vista installed to fully boot and run Ubuntu or any other system.

But I would backup Vista just in case. We have many users come back and want to reinstall Windows as that one application does not have a good equivalent in Ubuntu. Ubuntu is not Windows.:smile:

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Some examples of dual booting with screenshots so you can see how an install works.
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by 2F4U on 2012-03-12
Is the liveCD running fine? If thats the case, it may be  a hdd issue (since the liveCD does not access the hdd). Did you run memtest from the liveCD? If not, let it run at least for two iterations.

---

### Post by Mark Phelps on 2012-03-12
Having to guess, I'd go with failing hard drive.  

One of of 15 or one out of 30 implies that the filesystems are so corrupted that filesystem errors are stopping the boot process from succeeding in either OS.

While reinstalling MIGHT fix that (if the current stuff is installed to bad sectors), since a new install will automatically skip over bad sectors -- but with this history, even if it did, you're booting would be failing again in days (or hours).

---

### Post by AlphaMero on 2012-03-12
thank you for your replies, i appreciate it!

  I did the mem test. this is a new hardrive. Im just not sure how to properly create a partition and master boot record. Almost positive thats the case. I've read and tried almost everything I have read. From BIOS problem troubleshooting. reingstalling os over and over again.ultimate Windows boot cd troubleshooting. I'm actualy typing this from the laptop running ubuntu right now. Il try those links out thank you OldFred

If by liveCd you mean the download from ubuntu.com? Should i be using the long term support version? Or is there another download that is specificaly "LiveCD" when i insert disc in it just asks me if i want to install Ubuntu. Theres no troubleshoot/options prompt. Il read up some more thank you again for your help

---

### Post by oldfred on 2012-03-13
Memory test is RAM memory. Grub menus have a test as one of the boot choices.

Some have had RAM issues and test by removing one then the other memory stick (if you have 2) and see if system still works. You just need enough RAM left to be able to boot. Some have cleaned (carefully) connections on the RAM. Not sure what is best way now, used to use eraser, then clean eraser bits with alcohol. 

LIveCD is most(all?) of the Ubuntu desktop ISO when installed correctly on a CD or USB. Instructions on the download site. The alternative installer is not a liveCD and is text based. The alternative has additional software for servers and some added drivers, but then does not have room for the live (workingCD) version.

You can install LTS which is 10.04 now. The new 12.04 will be out the end of April and is in beta now. Or you can install 11.10.  Because it is so expensive to install both (about an hour depending on speed of your system) you can try both. :)

---

### Post by AlphaMero on 2012-03-14
When I run from disk the only option it gives is install. I will try system rescue cd, maybe that will help configure some of the settings. If not, I will try reformating my hdd and installing LTS.   Il post any success. Dont really think I will have any luck though because this is about the tenth time I will be installing an OS. I would think by now everything would be reset and in working order. Ah well.. 
 
 
Thanks,
Mero

---

### Post by lkraemer on 2012-03-15
It sounds as if you have some type of hardware problem or a timing issue.
It's possible it could also be a Power Supply Issue, if the Power Supply
isn't bringing up the +12, -12, +5 in the proper order.  You might want to
borrow a Power Supply and use it as a test.  

Here is something you might also want to verify.  Take a look at the IDE port
that the Hard Drive is connected to.  Make sure you know how many devices
are connected on the end of the IDE cable for each Port.  It's usual for
those older computers to have Primary and Secondary IDE Ports.  If your
Hard Drive is on the Primary Port, as it should be, make sure there is an
80 Conductor Cable, versus 40 Conductor cable on that Port.  The cable may
have a bad connection on one of the conductors, so you may want to try a
SPARE cable to see if that helps with your problem.  If you don't have one,
borrow one form a buddy for testing.  Then buy one if it fixes the problem.

Also the Hard Drive on the Primary Port should be Jumpered as MASTER and the
other Device should be jumpered as SLAVE.  The Hard Drive should be on the
END of the Cable and the CDROM or DVD should be closer to the end that connects
to the Motherboard.

The same type setup should be used for the Secondary IDE Port.  If there is
just one device on the Secondary Port, there is typically no jumper on the
device.  (I don't use or recommend using Cable select, but some Computer
Manufacture's might have used it on yours.)

Now, boot your computer and watch to see what the BIOS detects.  Your
Hard Drive & CDROM should be detected by the BIOS and displayed quickly on the
screen each and every time you boot.  You may also want to go into the BIOS and
VERIFY the settings, while looking for incorrect settings.
That will depend on the BIOS manufacture.

Since you have replaced the Hard Drive, the old one isn't the problem, and the
new one is unlikely to have the same type problem.  I'd rule out the Hard Drives,
but the 80 Conductor Cable, the Primary IDE Port, the BIOS settings, and the
MASTER/SLAVE jumpers are suspect.  I'd also start a RAM Memory test and let it run
for at least 8 hours to VERIFY your RAM.

lk

---

### Post by AlphaMero on 2012-03-16
-The old hard disk did fail, according to the disk test (lost alot of data)
 
-The new hdd does get detected on every boot, when I can enter the system config menu (bios) it shows everything running normaly. 
 
-I did hear that this series was having trouble with battery, but I have mine plugged in. Could battery cause a black screen/blinking cursor? wouldnt it be indefinite and not a variable startup problem? Sometimes the black screen will come up and after a minute or so it will boot up ubuntu. You can hear hdd and cd drive searching/loading.
 
-Mem tests are normal for ram and hard disk now
 
-The hdd connections seem fine, I really dont think its the actual hardwar in any way. I've been messing with this laptop a whole lot lateley. If I go into boot option and manualy select boot from hard disk i have a higher OS loadup rate. I think Its something missing, some sort of boot configuration thats not reading the OS. Something was deleted or tampered with by like a virus or something. 
 
Its a laptop, is there still a way to configure the master/slave settings? It would only have one IDE port right? I did see multiple
configurations/ pin settings...
 
My latest fix attempt is rescue disk, Im not too sure how to use rescue disk, have to look into the comands and all. If anything I will use ultimate boot disk to erase everything and start over. This is an awesome learning process.
 
Would you, or anyone for that matter know of any other boot discs that can completely reconfigure/reset the system? Just want to start from scratch.
 
Thanks again.

---

### Post by Mark Phelps on 2012-03-17
> **AlphaMero said:**
> -The old hard disk did fail, according to the disk test (lost alot of data)
Tried to tell you that in post #4 -- 5 days ago!
 
> -I did hear that this series was having trouble with battery, but I have mine plugged in. Could battery cause a black screen/blinking cursor? wouldnt it be indefinite and not a variable startup problem? Sometimes the black screen will come up and after a minute or so it will boot up ubuntu. You can hear hdd and cd drive searching/loading. That's not a battery problem.  Sometimes, booting just takes a while -- a minute or two is not unusual.  IF it never comes up, that is a different problem.
 
> Something was deleted or tampered with by like a virus or something.  Given the extreme rarity of Linux viruses, this is extremely unlikely.
 
> Its a laptop, is there still a way to configure the master/slave settings? It would only have one IDE port right? Laptops typically have only one builtin hard drive connector -- so they take only one drive.  Some have expansion ports where you can use a special adapter to plug in a second drive (I have a Tablet PC that does that), but the internal drive is still always seen as Primary.
 
> Just want to start from scratch.]
Only really good way to do this would be to erase the partitions on the drive and reinstall from scratch.

---

### Post by AlphaMero on 2012-03-19
And that is what im down to. Will reformat and reinstall. If that does not work im going to smash it to bits in a furious rage. Thank you for your help.

---

