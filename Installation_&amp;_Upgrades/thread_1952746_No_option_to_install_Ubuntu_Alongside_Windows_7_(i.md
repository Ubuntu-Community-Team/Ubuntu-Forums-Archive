---
title: "No option to install Ubuntu Alongside Windows 7 (installing each OS on separate SSDs)"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by ensignlee on 2012-04-04
Hi y'all,

Here is my system configuration as far as hard drives go:

1 128GB Crucial C300  (~90GB of 120 used for windows, applications, etc)
1 128 GB Samsung 830 (0Gb of 128 used)
3 HDDs, 500GB, 1.5TB, 2TB (for media and documents)

And here's the rest of the system:
i5-2500k
P67 UD4
16GB DDR3 1600 CL9
2x ATI 7970
Blue Ray Drive (this is how I'm installing Ubuntu)

I just got the Samsung 830 yesterday, and was excited to put Ubuntu on it. My plan was for my C300 to hold Windows and my 830 to hold Ubuntu 11.10

First, I tried disconnecting all my drives except the 830 and installing Ubuntu by itself. Worked great, but then when I attached all the other hard drives again, I kept getting "read error" failures. No biggie; googled the problem and it seems like I should keep all the hard drives installed so that way the boot loader can load on my C300 (since it is the primary drive according to my BIOS).

So I connected everything and went to install Ubuntu. At this point, I still had the "install alongside" option. However, it would only let me choose one of my HDDs to install it on. There was no option at all to install Ubuntu on my 830.

So I unplugged all of my HDDs, hoping that this would then force the installer to choose my 830. Well...then I lost the "install alongside" option! My only options are to write over Windows 7, and the custom one. Even after I reconnect all 3 HDDs back to the system, I still no longer have the "install alongside" option.

What did I do wrong? :(

edit: additional info. I am installing using AHCI, not IDE.

---

### Post by ensignlee on 2012-04-04
Update: So on a whim, I decided to burn another .iso with the installer.

I got the option to install alongside back! :)

BUT...it will only let me install Ubuntu on one of the HDDs. I try to click on what looks like a dropdown where it has the 500GB HDD selected and all it does is highlight the text in orange. I would think that clicking there woudl allow me to choose other drives? :/ What's going on?

---

### Post by oldfred on 2012-04-04
Most suggest uninstalling the other drives to insure grub2's boot loader is installed to the same drive as your system. If you keep more than one drive plugged in, you have to use manual install so you get the option on where to install grub2's boot loader. Best to partition in advance and for SSD with only Linux gpt is preferred now (see Arch site).

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

---

### Post by ensignlee on 2012-04-05
Update:

So when I finally got the option back to "install alongside", I figured I'd disconnect my 3 HDDs, so that my comp would only see the 2 SSDs.

It worked!

HOWEVER...

So obviously in order to install Ubuntu via CD, I had to change my BIOS boot order to CD/DVD, THEN SSD/HDD.

I went to change it back to straight load off my SSD/HDD, and now every time I boot up my computer I get to a screen saying "loading operating system: boot error". I can't even get to the screen where it lets me choose what operating system to boot to.

If I change the boot order back, then it's fine. WTF?!??! I assume it has something to do with how Grubw as installed. Any thoughts?

In case anyone is wondering why I don't just live with it, I want it to skip going to CD/DVD first, since doing so adds an additional 15 seconds of loading time while it waits to see if there's some sort of program in the CD/DVD tray. That waiting time easily doubles my load times and is kind of the entire reason I have SSDs to begin with.

---

### Post by chris.olive on 2012-04-05
Somewhat the same problem, new computer HP dv6 i3 6gb ram, loaded my disk of Ubuntu 11.10 32bit totally corrupted system and had to reload win 7 etc [twice] so downloaded a copy of 64 bit would not load correctly and would not run the 'auto partition' when trying to install program.
Never had this trouble before on my [very] old laptop.
Somewhat nervous of trying again.
Chris

---

### Post by Mark Phelps on 2012-04-05
> **chris.olive said:**
> Somewhat the same problem, ...

The original problem here is still unsolved.  You're only muddying the waters by hijacking this thread for YOUR problem.  Keeping the two problems, and their different solutions, separate is going to make the situation very confusing.

Please don't hijack an unsolved thread with your own problem.  Please start your own thread.

---

### Post by ensignlee on 2012-04-05
*bump*. Help? :(

---

### Post by Mark Phelps on 2012-04-05
You were obviously able to change the BIOS boot order previously to put the CD/DVD first.  Are you saying now that you're unable to get back into the BIOS to change that back?

You're pressing the same key you did earlier and now, it doesn't get you into the BIOS setup screen anymore?

---

### Post by ensignlee on 2012-04-05
No, I can get into the BIOS setup screen just fine. Problem is that when I switch the boot priority from 1) CD/DVD 2) HDD/SSD to 1) HDD/SSD

, all I get is "loading operating system...read error" whenever I try to boot to an OS.

If I switch the boot priority back to 1) CD/DVD 2) HDD/SSD, things work again, but I don't want to have to deal with a 20 second delay every time I boot my machine because of my boot priority.

---

### Post by oldfred on 2012-04-05
With HDD/SSD setting there should be another menu item in BIOS. Either clicking on the HDD setting opens up which HDD or another setting sometimes on even a different page should let you choose which drive to boot from. You also should have a one time boot key (f12 on mine) to choose just once which drive to boot from. I normally use that to boot CD, USB or different drive, and I have BIOS set to boot drive I use the most and let grub give me choices for other drives. 

If you want to know where everything is installed. Run the boot info script.

This is a good tool to have and it also runs script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.


and/or to run script from an install or Ubuntu liveCD or USB:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

