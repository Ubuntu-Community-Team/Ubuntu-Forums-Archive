---
title: "Bootup freezes at 'Checking Battery State'"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by Nick_C on 2012-05-21
Install problem with 12.04LTS, bootup freezes at 'Checking Battery State'.

I can still get to other tty terminals to do stuff but what do I do to solve this?



Not solved despite [SOLVED] in thread prefix, can't see how to edit this back to [Ubuntu]?

---

### Post by bogan on 2012-05-22
Hi!,** Nick-C,**

A hang-up after  'Checking Battery State     [OK]' is usually a sign of Video card problems.

Please Post output of:```
 /usr/lib/nux/unity_support_test --print
```Though I suggest you do it in a new Thread as well, and Post a link in this one, with an explanatory note.

You could also ask a Moderator to fix it.

Chao!, **bogan**.

---

### Post by plucky on 2012-05-22
> Not solved despite [SOLVED] in thread prefix, can't see how to edit this back to [Ubuntu]? 

Have a look in [Thread Tools] at top of page and mark as [Unsolved]

Good luck

---

### Post by Nick_C on 2012-05-22
> **plucky said:**
> Have a look in [Thread Tools] at top of page and mark as [Unsolved]

Good luck

Thanks plucky, now marked as unsolved.

---

### Post by Nick_C on 2012-05-22
> **bogan said:**
> Hi!,** Nick-C,**

A hang-up after  'Checking Battery State     [OK]' is usually a sign of Video card problems.

Please Post output of:```
 /usr/lib/nux/unity_support_test --print
```Though I suggest you do it in a new Thread as well, and Post a link in this one, with an explanatory note.

You could also ask a Moderator to fix it.

Chao!, **bogan**.
Unfortunately directory /usr/lib/nux does not exist.

---

### Post by Nick_C on 2012-05-22
I have now removed any nVidia drivers which I had previously installed with nVidia-current.  It now gets one line further before freezing:
Stopping System V runlevel compatibility

---

### Post by bogan on 2012-05-22
Hi!, **Nick_C**,

You Posted: ```
Unfortunately directory /usr/lib/nux does not exist.
```Are you sure?? 

Edit: Typo??

What version Linux are you using ??  Post ' uname -r'

In that case Please Post:```
 lspci -nnk | grep -i VGA
``` &```
 echo $DESKTOP_SESSION
``` & ```
sudo hwinfo --gfxcard
``` If you do not have 'hwinfo' ,. first run: ```
sudo apt-get install hwinfo
```Chao!, **bogan**.

---

### Post by bogan on 2012-05-22
Hi! again,** Nick_C**,

I Googled the unity test script and found it is part of a package called 'nux-tools', which should come as part of ubuntu 10.10 upwards.

I tried to install it in 10.04 LTS and it could not be found in the ppa's of that version, though in 12.04 LTS it is listed in both Ubuntu Software Canter and Synaptic Package Manager, as well as being available from a terminal if you have 12.04, with: ```
sudo apt-get install nux-tools
```If the code I suggested: 'echo $DESKTOP_SESSION' returns a blank line, try entering either ```
sudo service lightdm start # if you have 11.10 or later, 'gdm' intead of 'lightdm' if earlier,
# OR:
sudo startx
``` and report what, if anything happens.

You may have to enter 'Ctrl+Alt+F2-F6' and log-in again, or 'Ctrl+Alt+F7' to check the graphics.

If that gets nowhere, try rebooting to a tty terminal and entering ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```Chao!, bogan.

---

### Post by captainron042 on 2012-05-23
> **bogan said:**
> Hi!,** Nick-C,**

A hang-up after  'Checking Battery State     [OK]' is usually a sign of Video card problems.

Please Post output of:```
 /usr/lib/nux/unity_support_test --print
```

Chao!, **bogan**.

Hello, I'm having the same issue as OP. I've searched high and low for an answer that would fix it, but other's posts either haven't been answered or doesn't fix my situation.
This command returned "Error: unable to open display"

---

### Post by captainron042 on 2012-05-23
> **bogan said:**
> Hi! again,** Nick_C**,


If that gets nowhere, try rebooting to a tty terminal and entering ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```Chao!, bogan.

I tried this as well, and after a bunch of coding stuff, says E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)

typing```
sudo apt-get -f install
``` returned:
"dpkg: error: parsing file '/var/lib/dpkg/status' near line 27509 package 'xmind':
blank line in value of field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)"

---

### Post by bogan on 2012-05-24
Hi!,** captainron042**,

You Posted:>  ... command returned "Error: unable to open display"Which confirms it is a videocard/driver problem.

For the other errors, apart from editing out the Blank line complained of,  the other command you could try is:```
sudo apt-get update
sudo dpkg-reconfigure -a
```This carries a warning that it will take a long time: on my set-up it took 15-20 minutes, without any screen messages - unless it finds errors - just wait it out and then reboot.

Please Post the output of:```
 lspc -nnk | grep -i VGA
  hwinfo --gfxcard
```If you do not have 'hwinfo', run: ```
sudo apt-get install hwinfo
```Chao!,** bogan**.

---

### Post by captainron042 on 2012-05-24
> **bogan said:**
> ```
sudo apt-get update
sudo dpkg-reconfigure -a
```

returned:
dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 27509 package 'xmind':
blank line in value of field 'Description'
/usr/sbin/dpkg-reconfigure: acidrip is not installed

Please Post the output of:```
 lspci -nnk | grep -i VGA
```
(I added the "i" there, as you said on first page. I couldn't figure out how to get the pipe character before:
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1)

  ```
hwinfo --gfxcard
```
'hwinfo' is currently not installed

If you do not have 'hwinfo', run: ```
sudo apt-get install hwinfo
```
returns a bunch of coding, ending in 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)


I have everything important backed up on external hard drives. I'm not against completely swiping the drive clean and installing Ubuntu fresh. I've looked at "clean installs" before, but the instructions don't seem to really start with a swiped hard drive, only partially. Would you recommend doing this?

---

### Post by bogan on 2012-05-25
Hi!,** captainron042**,

The '|' pipe character is on the shifted key next to the lefthand 'Shift' key on a UK keyboard, and on a US keyboard, on the shifted key above the righthand shift key, next to 'Enter'.

I do not know enough about your set-up to give considered advice, hence these queries:

Does your system boot and run OK from a Live CD/USB?

Is yours an update or a direct install, dual boot or wubi?

Have you installed the latest nvidia driver?

There certainly seem to be several things amiss, but I would suggest trying the nvidia driver first before going to the purge and fresh Install.

On the other hand, if you have tried the nvidia driver, either with nvidia-current from Additonal Drivers, or from the nvidia download .run file; the other option with 12.04 is to uninstall and purge the nvidia installation and try out the default driver.

On my system, and I know many others, the included default Nouveau driver is very effective, even though in previous versions it was not.

As far as your installation query is concerned the first option will clear the whole drive, or you can choose the last 'other method' option and select the 'format' button for the Linux partition. Alternatively, use Gparted to remove all the partitions and let the Installer use the unallocated space.

Chao!,** bogan**.

---

### Post by captainron042 on 2012-05-25
> **bogan said:**
> 
Does your system boot and run OK from a Live CD/USB?

I haven't tried that yet. I'm setting up a USB now

> **bogan said:**
> 
Is yours an update or a direct install, dual boot or wubi?

It's an update from the previous version, 11.10. It's only ever had Ubuntu since I bought it from Dell in 2008

> **bogan said:**
> 
Have you installed the latest nvidia driver?

I'm not sure. How can I check, and/or install it via terminal?

> **bogan said:**
> 
On the other hand, if you have tried the nvidia driver, either with nvidia-current from Additonal Drivers, or from the nvidia download .run file; the other option with 12.04 is to uninstall and purge the nvidia installation and try out the default driver.

I apologize for my ignorance, but I'm really lost on how to change the drivers or uninstall/purge from the terminal screen I'm getting.


Thanks so much for your help.

---

### Post by captainron042 on 2012-05-25
> **bogan said:**
> 
Does your system boot and run OK from a Live CD/USB?

No, it does not. It says simply "boot error" pressing Alt+F5 returns "root error"

---

### Post by captainron042 on 2012-05-25
I tried 
```
sudo apt-get purge nvidia-current
```
and got "E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)" again.

---

### Post by captainron042 on 2012-05-25
Since I'm getting a "boot error" for the USB (after even redownloading the image and creating a new USB), I decided to try DBAN to erase the disk and start fresh. 
[http://www.dban.org/download](http://www.dban.org/download)

Even that says "boot error". I entered the boot order menu to make sure it was using the USB, and it was correct.

---

### Post by bogan on 2012-05-25
Hi!, **captainron042**,

First a response to your:>   I'm really lost on how to change the drivers or uninstall/purge from the terminal screen I'm getting.Setting aside the other issues for now.

Extracted and modifed from **MAFoElffen**'s How To in Post#280 of the 'Blank Screen' Sticky at the top of Installations & Upgrades Forum.

 1. To remove existing nvidia drivers and any remnants:
```
sudo apt-get update
sudo apt-get upgrade
sudo nvidia-installer --uninstall
sudo apt-get remove --purge nvidia-*
```You may get some file not found messages. That is okay., continue. We just want to make sure that older modules are not there to cause a conflict.

Reboot and see what effect the default Nouveau driver has, if necessary, try using 'nomodeset' in the grub menu edit 'Linux' line.

 2. To install the latest nvidia driver: 

You need an operating Internet connection for this.

 Down load the appropriate driver from nvidia.com .
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html). 

That is for the 32.bit version, make sure you have the correct one.

Run 'uname -r' and insert the output in the following command, substituting it for 'uname -r', for example: "sudo apt-get install linux-headers-3.2.0-24-generic-pae".```
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
```To install the downloaded driver, Xorg cannot be running so you need to shut down the GUI X-Session. In the terminal enter:```
sudo service lightdm stop # If using 11.10 or earlier use 'GDM' in place of 'lightdm'
```You will get a black screen; if it does not have a login prompt, press 'Ctrl+Alt+F1'to get one, login, enter your password.

Alternatively, reboot into a TTY Text Console and login:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR]

Change directory [cd] to the directory where you saved the nvidia....run file. 
Run 'ls', this will confirm you are in the right place and you can be sure the spelling is correct - enter 'NV' and pressing 'Tab', will Auto-complete the file name.

 Mark the downloaded file as executable:```
sudo chmod a+x NVIDIA-Linux-x86-295.53.run
```Run the file to Install drivers:```
sudo sh NVIDIA-Linux-x86-295.53.run
``` Ignore error messages, follow screen prompts using arrow keys to navigate and press 'Enter' to accept the 'OK's.

When complete reboot.

[Note: I have deliberatly left out the instructions to add Blacklists as in 12.04, blacklisting the Nouveau driver does not seem to be necessary, indeed if depending on that default driver, removing the blacklist may be necessary.]

Check the /etc/modprobe.d/blacklist.conf file.

Chao!, **bogan**.

---

### Post by LancerNZ on 2012-05-25
I'm thinking that what you're seeing is a failure for the newer Ubuntu (after update) to correctly kick in your graphics card. This is likely because Ubuntu have altered how the bootloader uses graphics so that they can have ultra high-resolution boot up screens. A mistake, in my opinion because for that luxury; a lot of Nvidia cards don't like it including many of the latest cutting edge models.

I think what you need is to add the "nomodeset" option to grub.

To test whether this is the case; can you boot a live CD for 12.04 LTS? If it hangs at start up (e.g. black screen) or also has errors, try the following...
[LIST]
[*]Boot from the 12.04 LTS CD Rom (not the USB)
[*]As it starts up, there should be a stage where you see a keyboard and a person at the bottom of your screen. At this point hit any key.
[*]From here choose your language, then hit F6 and select the "nomodeset" option. Use [ESC] when done and resume boot.
[/LIST]
I'm thinking you will now be able to boot into the live CD but won't otherwise be able to from the standard "don't touch anything" default.

Please test this to rule out the nomodeset issue. If it is the case, then the Grub script of your current install needs to be updated with the option.

---

### Post by captainron042 on 2012-05-25
Thank you, Lancer. I just tried a live USB on a different USB thumbdrive, and it still gave me an error.

I saw the recommendation for "nomodset" in GRUB, but I couldn't follow the instructions there. It said to hold shift to get to GRUB, but it didn't seem to do anything different. So, basically what I'm asking, can you tell me how to do that? :)

I'll try to round up a blank CD to do a liveCD (it actually needs to be a dvd, right?) I haven't burned a disk for anything in years, lol.

---

### Post by LancerNZ on 2012-05-25
Just the CD version should be fine. Burn as disk image from the i386 version of 12.04 LTS as supplied by ubuntu.org.

The reason I'm suggesting to do this is it is a non destructive (won't change anything) test to see whether your computer has issues with the default boot versus your graphics card. If booting from the live CD causes something like a boot screen lockup or a black desktop with no keyboard life, then it might be that yours (like mine) is one of the machines using an Nvidia card which needs nomodeset in order to avoid the recent changes to boot graphics which tend to put some cards off kilter.

---

### Post by captainron042 on 2012-05-25
Ok, well, I was using the Startup Disk Creator on my laptop to write the Ubuntu ISO image to the USB, along with whatever it is that the program put in there. The program wouldn't acknowledge a writable CD or DVD, though. So, I burned the ISO image on the disk alone. When booting to my problematic desktop pc, I got:
> Boot from CD:
No boot device available, Press ENTER to retry
SATA -0: Installed
SATA -1: Installed
SATA -4: None
SATA -5: None
I then burned the files from the USB to a disk, but got the same error

---

### Post by LancerNZ on 2012-05-26
The Ubuntu startup disk creator should be fine, but I know the Windows based one works differently. That's why I said to boot from CD-Rom for this... while USB is faster it adds another level of what can go wrong. Do you get these errors if booting straight from the CD-Rom? It's from the CD-Rom that you should hit the key at the right time, choose language, select [F6] etc.

---

### Post by captainron042 on 2012-05-26
Yes, I insert CD and restart computer. I press F12 and tell it to boot from the CD ROM, ENTER. Screen goes black for a second and displays that error message.

---

### Post by LancerNZ on 2012-05-26
Okay - the "no boot device available" error means that the computer can't see a valid bootable filesystem on the CD-ROM.

If the iso file to make the CD is corrupt, it often results in this error. Do you know how to perform an MD5sum check of the downloaded file you're burning the disk from?

The other thing I'm wondering is whether you burned the iso file as a disk image or whether you simply added it like an ordinary file to the contents of the disk. There's a difference. Only by burning as an image will you end up with a bootable filesystem.

---

### Post by captainron042 on 2012-05-26
> **LancerNZ said:**
> 

The other thing I'm wondering is whether you burned the iso file as a disk image or whether you simply added it like an ordinary file to the contents of the disk. There's a difference. Only by burning as an image will you end up with a bootable filesystem.

That's probably the prob. I just dragged it to the CD and told it to burn it, using GnomeBaker.

---

### Post by LancerNZ on 2012-05-26
Okay... how about if you right click the iso file? If the list of choices includes something like "Write to Disc..." then use that.

---

### Post by captainron042 on 2012-05-26
That option isn't there.  Just Open with.. and the other normal commands liked copy, ect.
I had to download GnomeBake, as I didn't see any other way to burn the CD. All the instructions I can find just say download the file and put i on a disc with no detailed instructions. I'm not sure why I'm having such a problem here.

---

### Post by captainron042 on 2012-05-26
The MD5SUM checked out. Am I maybe downloading the wrong version?

d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso

My desktop is a Dell Inspirion 530

---

### Post by captainron042 on 2012-05-26
I checked the Gnomebaker program again. The opening wizard gives an option for Data or music only, but I found in the menu an option for "burn an image". That worked correcly, and the disk is booting up in my desktop seemingly fine.

---

### Post by captainron042 on 2012-05-26
success! I now have a fresh install of Ubuntu 12.04. Thanks a lot for your help, guys. I hope OP didn't mind the threadjack and has his problem fixed as well.

---

### Post by bogan on 2012-05-26
Hi!, **captainron042**,

Great news, glad you got it all OK.

Perhaps **Nick_C **will now reappear and Post some info, or Mark This thread as 'Solved'.

Chao!, **bogan.**

---

