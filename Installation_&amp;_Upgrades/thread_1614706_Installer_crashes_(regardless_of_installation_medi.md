---
title: "Installer crashes (regardless of installation media??)"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by travlemon on 2010-11-06
Hello Everybody,

Ubuntu, or any of its derivatives, have continued to be my favorite distros!  However, I am having quite a frustrating problem.  I have been trying to install Ubuntu 10.04 (and some derivatives too) on a Dell Inspiron 8100 laptop with 512mb of RAM and a 40gb hard drive. 

**_The Problem:_  **I can boot into the live CD fine, or just choose to install, and the installation wizard will start from either option.  However, 100% of the time, the installer crashes after clicking forward on the partitioning screen.  "ubi-usersetup* crashes with error code 139.  I will be given the options of quit, continue anyway, or try again.  Of course, "try again" brings the same error. "Continue anyway" seems like a bad idea, as there is obviously a problem here.  Occasionally it will crash at the keyboard setup part of the installation wizard in the beginning, but not often.

**_Trying to work around it:_  **It has done this when booting from either CD's (I have burned a couple at slow speeds to prevent bad data), and from two separate USB flash drives that I have.  I've tried a bunch of different Ubuntu based distros such as:  Pinguy OS, Mint, Xubuntu, Ubuntu 9.10, Ubuntu 10.10, Ylmf.  They all crash in the exact same way, I assume because they all use the same installer!

Also, I tried the Ubuntu 10.04 alternate disc, with the text mode installation.  That crashes for me as well, with the error "Failure while unpacking the required packages".  As a test, I'm installing PCLinuxOS, since it's completely different.  It seems to be installing fine.

**_Speculation:_  **I have had the the crashing issues before on desktop machines with terribly buggy CD-ROM drives, but booting from USB totally eliminated the problem.  That's not the case here, I have no idea how to make it work.  This laptop just seems to HATE the Ubuntu installers for some reason. 

Any help on this mystery would be GREATLY appreciated, 

Thank you!

---

### Post by mrcreativity on 2010-11-06
Same problem here. Installer crashes on my desktop now and then, I/O as often as hell, and when ubuntu does install, it runs pitifully. This happens regardless of the media used for installation.
Ubuntu 10.04 and 10.10 both give the same errors.

The desktop is rather old, with an AMD64 2800+ processor, 2 gb ram and a 7600gs nvidia pci xpress card.

The same media work fine one my laptop and netbook.

Any suggestions would be appreciated.

---

### Post by travlemon on 2010-11-08
> **mrcreativity said:**
> Same problem here. Installer crashes on my desktop now and then, I/O as often as hell, and when ubuntu does install, it runs pitifully. This happens regardless of the media used for installation.
Ubuntu 10.04 and 10.10 both give the same errors.

The desktop is rather old, with an AMD64 2800+ processor, 2 gb ram and a 7600gs nvidia pci xpress card.

The same media work fine one my laptop and netbook.

Any suggestions would be appreciated.

it's a little comforting to know that at least i'm not the only one experiencing this. i was able to get lucky and click "try again" a couple times and make it through to the part of the installation where the files are copied.  but even then, it gets close to the end and fails. then the system doesn't boot. 

i've been trying things since my original post, burned cd's at the slowest possible speed, using different flash drives again, using different programs to create the bootable flash drive. same outcome every time.  next, i will try to install puppy, since it's small. just to see if the **** thing can even make it through a tiny installation.

EDIT:  oh and i also tried the mini ISO image, which downloads all of the packages. and even THAT fails when trying to unpack the packages!  i don't know how many possible ways i can try to install this without getting errors.

---

### Post by mrcreativity on 2010-11-09
Have you been trying the 32bit or 64 version?

---

### Post by travlemon on 2010-11-19
> **mrcreativity said:**
> Have you been trying the 32bit or 64 version?

sorry for such a delay! i didn't receive any notifications that i received a response. i have to check my notification methods. 

i've been using all 32-bit versions, as it's an old laptop with a 32-bit processor.  i think i am going to have to assume there is hardware in this laptop that Linux just cooperate very well with.  the only one that installed and works ok is OpenSUSE.  though i'm really not too fond of openSUSE, i'll be using it on that laptop.  that OS must do things differently enough to the point where it loads the hardware slightly differently or something.

---

### Post by mrcreativity on 2010-11-24
I've been having a hell of a time trying to install ubuntu on my desktop.
All attempts to setup and run ubuntu/kubuntu on my desktop fail 

And when they do install successfully, i keep getting random crashes, updates fail most of the times and most packages do not install.

Furthermore, I have been unsuccessful in trying to install opensuse as i have not been able to make a bootable usb. A similar thing happens with fedora, the live usb works on my laptop, but fails to be detected by my desktop.

I'm not a big fan of mandriva and will not use it inspite of the fact that it installs and runs pretty well.

Any suggestions on how i can resolve my issues with ubuntu will be appreciated.

---

### Post by travlemon on 2011-01-27
> **mrcreativity said:**
> I've been having a hell of a time trying to install ubuntu on my desktop.
All attempts to setup and run ubuntu/kubuntu on my desktop fail

And when they do install successfully, i keep getting random crashes, updates fail most of the times and most packages do not install.

Furthermore, I have been unsuccessful in trying to install opensuse as i have not been able to make a bootable usb. A similar thing happens with fedora, the live usb works on my laptop, but fails to be detected by my desktop.

I'm not a big fan of mandriva and will not use it inspite of the fact that it installs and runs pretty well.

Any suggestions on how i can resolve my issues with ubuntu will be appreciated.


Sorry I haven't gotten to your response sooner, I haven't been on the forums in quite some time.  Nor did I receive an email notification of your reply, I must have forgotten to subscribe to my thread. 

I re-opened this thread, as this issue is driving me NUTS!  I installed DreamLinux flawlessly on the Inspiron 8100, not a single problem, which still gives me hope that any Ubuntu based distro should work.

I can answer your question about OpenSUSE.  OpenSUSE requires a proprietary utility to make your USB flash drive bootable.  It won't work if you simply use UNetBootin or any regular one.

Go here: [http://en.opensuse.org/SDB:Live_USB_stick#Create_a_Live_USB_the_easy_way_.28GUI.29](http://en.opensuse.org/SDB:Live_USB_stick#Create_a_Live_USB_the_easy_way_.28GUI.29)
and download the OpenSUSE image writer program.  You will need have a Windows computer handy, or a VirtualBox with Windows installed on it.  Then, you can use the image writer program to write the OpenSUSE ISO file to a USB flash device.  I think this may be the problem you were having, I had the same issue before I knew about the image writer utility.

As for the primary problem itself....I'm sorry, but I haven't made a bit of progress.  I tried downloading DVD versions of Ubuntu, as someone on another thread (for a similar issue) pointed out that the SquashFS (a way of compressing Ubuntu onto standard CD size) may cause that problem on some PC's.  No luck. 

Anyway, I finally had some extra time to grab the syslog file from one of my failed installations.  Hopefully someone will see it and make heads or tails of it, as I'm just not experienced enough in Linux to figure out what it means.

My log file is attached as a split zip file, since the txt file was larger than the upload limit. I had a lot of trouble attaching the zip files between size limits, and which file extensions are allowed.   To get the zip files to work right, the files need to be renamed as follows:

syslog1.zip = syslog.zip.001
syslog2.zip = syslog.zip.002

Any help on this issue is really appreciated!

---

### Post by travlemon on 2011-02-27
I'll be marking this issue as solved again.  For anyone else out there who is having the same issue...I'm sorry, but I just never found one!  My complete and final conclusion comes down to two possibilities:

1.  Linux just does not like this model laptop. Though I find it hard to believe, since Linux seems to have such solid hardware support out of the box.

2.  I have a possibly somewhat defective piece of hardware that maybe does its job enough not to totally fail, but causes issues such as the crashing.

I ended up putting XP back on the machine and giving up.  It's an old, heavy laptop, and not worth the time.

---

