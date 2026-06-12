---
title: "Guide: How to Install Ubuntu 12.10 with newer Nvidia cards"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by zite83 on 2012-11-13
[SIZE=4]**THE ZITE WAY**[/SIZE]

I am posting this because I want to share my way of installing Ubuntu 12.10 x64 with a newer Nvidia card.  The problem happens on install with 12.04 and 12.10 x64.   The problems with nouveau drivers that prevent progress to an install screen or really to do anything. They just don't seem to work well with the newer cards.   I always used an alternate install CD but that is no longer an option.  This is a step by step guide how to install Ubuntu 12.10 x64 with a new Nvidia card with out any kind of rigging to get it to work (installing on another computer transferring hard drive or installing with another video card) NOTE: I have no clue if this works with 32bit or that this is even a problem. I found out this way of doing it by finding so many different post across the internet, about 30 installs, and just blind luck.  I have this process down in my head and I have done it about 10 times so far with it always turning out the same way.  I also can't be much help as I don't know that much about Linux, I just some how get things done that I want.  I hope this is a problem other people are having or I will feel a little awkward typing all this up or that this same guide exists some where else..  If this is helpful please spread it around so others can find this.  I had no luck Googling this issue as Nvidia Ubuntu Install Freeze etc is flooded with so many other issues. 

(updated to larger images) 

**Boot from your Ubuntu 12.10 x64.  Once the Ubuntu screen pops up hit F8 quickly.  Choose your language.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0003.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0003.jpg)

 ** Next hit F6 to bring up other options and select nomodeset and hit ESC.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0004.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0004.jpg)

**Install Ubuntu as you normally would.** [B]It will be in a low graphics setting. I choose not to install updates or third party programs during install. You can do this after the install.  Lets make sure you pull out as many things that can go wrong during install.  We already are having enough issues as is.
[/B][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0006.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0006.jpg)
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0007.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0007.jpg)
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0008.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0008.jpg)
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0012.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0012.jpg)[B]

Reboot computer.

During the BIOS boot up hold down your shift key until the grub boot menu pops up. Select Advanced options for Ubuntu.
[/B][URL="http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0014.jpg"]http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0014.jpg
[/URL] 
**Next select Recovery Mode**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0015.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0015.jpg)
[B]
In recovery mode now just select resume normal boot.[/B]
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0016.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0016.jpg)


**You will get a warning about graphical drivers, this is what we want, just hit OK**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0017.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0017.jpg)
[B]
Now just login.[/B]
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0019.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0019.jpg)

**Open Firefox and navigate to Nvidia's website and download the proper drivers.  This will differ for you depending on your card, for me it was 500 series Linux-64x.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0020.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0020.jpg)

**You may get a few errors along the way just click Leave Closed.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0021.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0021.jpg)

**Navigate to where you downloaded your file. Right click on the file and go to properties.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0023.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0023.jpg)[B] 

Change the permissions so you can execute the file.[/B]
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0024.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0024.jpg)

**Next we need to edit a file so open a terminal window by either Ctrl+Alt+T or through unity.**

[PHP]sudo nano /etc/modprobe.d/blacklist.conf[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0027.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0027.jpg)

**Navigate to the bottom of the file and insert the following code.**
[PHP]blacklist amd76x_edac  #this might not be required for x86 32 bit users.
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0028.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0028.jpg)

**Save and exit editor.**

**Now type the following commands**
[PHP]sudo apt-get remove --purge nvidia*[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0029.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0029.jpg)

[PHP]sudo apt-get install build-essential[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0030.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0030.jpg)

[PHP]sudo apt-get install linux-headers-$(uname -r)[/PHP]** If for some reason (name -r) part does not work just type uname -r and copy what it prints out to the end of linux-headers-**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0033.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0033.jpg)

**Once finished with that close your terminal and logout of Ubuntu**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0034.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0034.jpg)

**Once at the login screen press Ctrl+Alt+F1 which will bring you to command promt. Type in your username and password.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0035.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0035.jpg)

**Type in the following command to stop x-server.**
[PHP]sudo service stop lightdm[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0036.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0036.jpg)

**Navigate to your download directory or where ever you saved your drivers from Nvidias website.**
[PHP]cd Downloads[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0037.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0037.jpg)

**Now lets execute the drivers.  (??? =  what ever version you downloaded)  A quick tip for less typing just type sudo ./N  then hit your tab key.**
[PHP]sudo ./NVIDIA-LINUX-x??_??-???.??.run[/PHP][http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0039.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0039.jpg)

**Click Accept**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0040.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0040.jpg)


**Might say script failed ignore and hit ok.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0041.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0041.jpg)


**Should start building your drivers.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0042.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0042.jpg)

 **Yes to 32bit OpenGL drivers, even though the picture says no**.
The 32bit openGL stuff is important to 64bit users with 32bit apps including wine.. Thanks [BicyclerBoy]("http://ubuntuforums.org/member.php?u=816321")
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0043.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0043.jpg)

**Click Yes for nvidia-xconfig**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0044.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0044.jpg)


**Next screen should ask for some clean up, click ok.**
[http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0045.jpg](http://i284.photobucket.com/albums/ll35/zite83/ubuntu_large/IMAG0045.jpg)


**You should now be back at the command prompt. Now reboot.**

[PHP]sudo reboot[/PHP]Everything "should" work.
[IMG]http://i284.photobucket.com/albums/ll35/zite83/Ubuntu/IMAG0002420x253360x217.jpg[/IMG]

[IMG]http://i284.photobucket.com/albums/ll35/zite83/Ubuntu/IMAG0047420x235360x201.jpg[/IMG]

[IMG]http://i284.photobucket.com/albums/ll35/zite83/Ubuntu/IMAG0048420x284360x243.jpg[/IMG]

---

### Post by mof920 on 2012-11-16
Okay, so here's my issue. I can't run 


sudo apt-get install build-essentials

From what I saw, it's that this was deleted from the repositories. What do?

---

### Post by zite83 on 2012-11-17
> **mof920 said:**
> Okay, so here's my issue. I can't run 


sudo apt-get install build-essentials

From what I saw, it's that this was deleted from the repositories. What do?

First always make sure you do an update

[PHP]sudo apt-get update[/PHP]Also make sure you are doing build-essential with out the S.  I've made the mistake before.

[PHP]sudo apt-get install build-essential[/PHP]

---

### Post by bogan on 2012-11-17
Hi!. **zite83**,

Nice job on the 'How To' for the newer 64 bit Nvidia cards. All the illustrations were a good idea, pity they are not easier to read.

Actually, all you suggest is equally applicable to 32 bit cards.

My version follows much the same route, with acknowledgement to my main source: **MAFoEllfen**'s Magnum Opus in the Installation & Upgrades Forum 'Blank Screen' Sticky.

See Post #36: [http://ubuntuforums.org/showthread.php?t=2075318](http://ubuntuforums.org/showthread.php?t=2075318)

And the Sticky, Post #280:[http://ubuntuforums.org/showthread.php?t=1743535&page=81.]("http://ubuntuforums.org/showthread.php?t=1743535&page=81")

The only thing I would question is the nouveau blacklist does not include the blacklists that both Nvidia-installer and Jockey/nvidia-current put in the blacklist files they create: 
> # Added for nvidia driver. 
 blacklist nouveau 
 blacklist lbm-nouveau 
 options nouveau modeset=0 
 alias nouveau off  
alias lbm-nouveau off I have no idea if they are all necessary, but I have found, and others have Posted, that: "blacklist nouveau" alone, is not always effective.

Chao!, **bogan.**

---

### Post by BicyclerBoy on 2012-11-17
re: the 32 bit openGL build question in nVidia installer.

The 32bit openGL stuff is important to 64bit users with 32bit apps including wine..

Before 12.04 this required you to install ia32bit-libraries..
With 12.04 & later this seems to have disappeared into a multi-arch library.
 
For old legacy programs you may need to install
- ia32-lib-multiarch
Multi-arch versions of former ia32-libraries

The better way for headers files is:
```

apt-get install linux-headers-`uname -r`

```

I think the blacklisting & the headers packages is probably all that is needed to allow "jockey" to work.

---

### Post by zite83 on 2012-11-17
I will update the images, I wish I could give my sources but found out how to do this from many websites over a long period of time. Will update this as more help comes out.  Thanks for the replies.

---

### Post by BicyclerBoy on 2012-11-17
Correction
The right way to do the linux headers is via a meta package so it always matches & is auto updated.

apt-get install linux-headers-generic

You need a warning about rebuilding the nVidia kernel interface with every kernel update or is this now handled with dkms ?

---

### Post by bogan on 2012-11-18
Hi!,** zite83 & BicycleBoy**,

I agree about the warning of the possible need to reinstall an Nvidia downloaded driver after a kernal update.

In theory Nvidia drivers from v304 onwards are DKMS compatible and the need should no longer exist.

In practice - vide the most recent update - if the header files are not correctly updated, or DKMS has been 'Cleaned', or is not available, the kernal module does not get recreated for the new kernal, result -  disaster, with no warning up front.

This last update to 3.5.0.19-generic left me with a very low res and no Launcher or Toolbar, with both 304.51 and 310.16. I WAS VERY DISAPPOINTED!

On further reading of "THE ZITE WAY", using the recovery mode approach can lead to problems as it can be very unstable and unpredictable in 12.10. 
It also leads nvidia-installer to require resetting the level to 3 [ 'telinit 3' ] and restarting the installation.

Another minor point, with the NVIDIA-XXX-XXX.run file, several option defaults are set to 'NO', so there is a need to navigate to your choice with the 'Tab' or 'Arrow' keys. Something not obvious to a first comer or 'noob', several Post report 'failed installations', due to that.

I fully realise, from personal experience, that trying to cover every known possible difficulty leads to an intimidatingly long screed, and is to be avoided.

Chao!,** bogan**.

---

### Post by bogan on 2012-11-18
Hi!, **zite83**,

In my last Post I wrote: ```
...  the recovery mode approach can lead to problems as it can be very unstable
 and unpredictable in 12.10
```In your PM you wrote:>  I would just mount and enable networking and use wget to get my drivers  but for some reason, when I try to do that in recovery mode with 12.10  it just locks up and I can't get to a tty screen.That is precisely what I was referring to.

However, there is a 'Workround' -  in fact, 3 - when it hangs, either press 'Ctrl+c', which - after a pause - will take you to a TTY root login prompt, or 'CTRL+Alt+Del', which will take you back to the Recovery menu.

Alternatively, in the Grub menu script edit mode - press 'e' - edit the Linux boot line to read:  "rw single --verbose text"  instead of: " ro recovery nomodeset"; which - after a display of system messages - will go direct to the TTY root login prompt, in Read/Write mode.

Chao!, **bogan.**

---

### Post by ryanvade on 2013-01-20
I know this is old, but I just want to add somethings.  First off, I added those entries to blacklist.  I rebooted and nouveau is still loaded.  second, after I login (if still using nouveau  because they were still loaded and after installing the nvidia drivers) unity is broke.  You mentioned that above I think.  The only way I can get around this is to put ```
nouveau.blacklist=1
``` to the kernel line in grub.cfg.  What am I doing wrong?  Is it because I am using the liquorix kernel?

---

### Post by bogan on 2013-01-21
Hi!,** ryanvade**,
  
You Posted:>  Is it because I am using the liquorix kernel? 	Liquorix is not something I know about; what version is it?

Have you checked that the correct linux-headers and linux-source are installed, as well as build-essential,  prior to installing or re-installing the driver ??

If not, install them, remove --purge the installed nvidia driver and re-install it - or a later version. 

Chao!, **bogan**.

---

### Post by BicyclerBoy on 2013-01-21
Loosely quoting from nVidia HDMI audio readme: Some distros require the boot image to be updated after editing module options.
Not to much of a stretch to guess this could apply to blacklists especially drivers with built-in kernel modules (nouveau) & KMS functionality.

nVidia recommend (for ubuntu):
$sudo update-initramfs -k all -u

---

### Post by LinuXXuniL on 2013-03-27
Thank you Zite83 for this nice post. I've been looking for it since the release of 12.04 and meantime I had my doubts about using ubuntu again, but I never ceased to belive that someone will find a solution to this problem. 
Now that I have found this post I want to thank you again, because you made a very good job and now I can use Ubuntu again. It works like a charm!
By the way, this is very comprehensive work and easy to understand.
Anyway, everything worked fine until system applied the updates, after that the resolution became 640x480 and I can't change it because it doesn't recognize the driver.

---

### Post by dioariete on 2013-04-01
you are the beeest !!!!

grazie

---

### Post by slybootz on 2013-04-19
THANK YOU FOR THIS GUIDE!  Helped a ton since I'm getting back into Ubuntu after a few years without it.  This guide worked perfectly for my geforce 570 GTX using NVIDIA-Linux-x86_64-310.44.

---

