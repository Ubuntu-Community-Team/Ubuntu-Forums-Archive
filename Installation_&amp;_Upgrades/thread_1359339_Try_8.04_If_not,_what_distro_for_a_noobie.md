---
title: "Try 8.04? If not, what distro for a noobie?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by cheesefry on 2009-12-19
I just put 9.10 on my netbook and am running into lots of problems from wireless not working to booting problems. I am thinking of trying 8.04 before going back to Win XP.

This is my first experience with Linux, and would like to stay around. Need some suggestions for the best distro for my Gateway LT20 netbook and most importantly how to get a good install from my now 9.10 OS. Can I just burn a CD and let it take over as I did when switching from Win XP to UNR 9.10?

---

### Post by raymondh on 2009-12-19
> **cheesefry said:**
> I just put 9.10 on my netbook and am running into lots of problems from wireless not working to booting problems. I am thinking of trying 8.04 before going back to Win XP.

This is my first experience with Linux, and would like to stay around. Need some suggestions for the best distro for my Gateway LT20 netbook and most importantly how to get a good install from my now 9.10 OS. Can I just burn a CD and let it take over as I did when switching from Win XP to UNR 9.10?

Hi,

Sorry to hear you're running into problems.  

For Ubuntu, try 9.04 (jaunty) as Hardy may be a 'little' old for newer vintage netbooks (am not saying that 8.04 will not work)..... driver-wise.  The new LTS (long-term-support) version is due to be released in 4 months (april 2010).

For Ubuntu flavor .... try MASONUX.

From your post, I assume you decided to remain sole-boot (just ubuntu).  If you wish, you can re-install XP and then dual-boot ubuntu .... that way, you have the choice of both OS' should one of them bork or hiccup.  There are various methods to  install a dual-boot.  Post back if you need guidance should you decide you wish to do that.

Regards,

---

### Post by cheesefry on 2009-12-19
Willing to try a new distro, but not that interested in dual-boot. Want one OS so I can just do my thing. I dig the 9.10 layout, and realize I have a lot to learn, but just want something stable. I would like it to start up when needed, and need to wireless to work. If i decide to go to 8.04, or any of the others, can I just burn a disk and take of? do I have to go another rout do to the way Grub handles things?

---

### Post by darkod on 2009-12-19
Just curious, did you try to troubleshoot the wi-fi thing? I know it can be frustrating, but sometimes few commands will solve it and it will work from there on.
Usually netbooks use similar adapters, I'm surprised it didn't work. On my NC10 it worked straight away. Do you know the adapter chipset by any chance?

---

### Post by jerrrys on 2009-12-19
just burn another disk and during setup and use the use entire disk option.  THIS WILL ERASE EVERYTHING if thats the route you want to go.  

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by cheesefry on 2009-12-19
I tried several things for the wi fi stuff, and when I installed 9.10, I used the whole dick when installing. I am having horrible trouble upon startup every time now. It prompts me to either Grub Loading .... then a blank everlasting screen with just a cursor, or brings me to a menu with my kernel # and kernel# (restore). If I pick the first on the list it brings me back to the blank screen, if I pick the restore one, it asks me to log-in, then waits for my command says "name@gateway~$:"  I don't know what to wright for a command for this thing to boot up. Sux!!!

---

### Post by darkod on 2009-12-19
> **cheesefry said:**
> I tried several things for the wi fi stuff, and when I installed 9.10, I used the whole dick when installing. I am having horrible trouble upon startup every time now. It prompts me to either Grub Loading .... then a blank everlasting screen with just a cursor, or brings me to a menu with my kernel # and kernel# (restore). If I pick the first on the list it brings me back to the blank screen, if I pick the restore one, it asks me to log-in, then waits for my command says "name@gateway~$:"  I don't know what to wright for a command for this thing to boot up. Sux!!!

That doesn't sound like it installed OK at all. Of course, you can try 9.04 or any other OS, your choice.
But I don't think 9.10 is to blame, it sounds like bad install. Maybe bad cd created from ISO corrupted during download, badly burnt cd, etc.

---

### Post by cheesefry on 2009-12-19
The download was re-checked, as well as the burn was re-checked after completion. Could it still be bad?

---

### Post by darkod on 2009-12-19
> **cheesefry said:**
> The download was re-checked, as well as the burn was re-checked after completion. Could it still be bad?

Unfortunately, in some situations, yes. That's technology. :) Have you tried installing from bootable usb stick? That's one of the options I know it worked for people also thinking their cd was good.
And just to reconfirm, the cd should not be burnt at more than 8x, even better at 4x. With todays burning speeds lots of people think even 20x or 30x is slow, but for a good quality OS install cd, that's too fast.

---

### Post by jerrrys on 2009-12-19
not that i know of, but what was your burn speed?

---

### Post by cheesefry on 2009-12-19
I made sure to go with 8x speed as I heard a bad dick can cause horrible problems. Does anyone have a suggestion as to a command to get this to boot? Time to get out the hammer!

---

### Post by cheesefry on 2009-12-19
DISK, DISK....I mean DISK!

---

### Post by jerrrys on 2009-12-19
do it, but before you commit, run it from cd drive first and see if it works...

---

### Post by darkod on 2009-12-19
Do you have a usb stick to use, at least temporarily? Another computer to work with? Although you can create the usb stick on your own computer using this same CD.

---

### Post by cheesefry on 2009-12-19
That's the thing, I did just that. Ran it and everything was great. Performed the install and it worked great. started and booted fine, all was well (except for the wireless). shut down last night, now it will not boot. I tried to reinstall from the same CD. It recognizes the drive, but will not run the disk. Don't know where to go from here. My son just woke up from his nap, gotta go for now. I will chack back tonight if anyone has any more suggestions as how to get this fixed. Thnx

---

### Post by cheesefry on 2009-12-19
Tried again and the same thing. 

GNU GRUB Version 1.97 beta 4

Ubuntu Linux 2.6.31-14 
Ubuntu Linux 2.6.31-14 (Recovery Mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial consol 11520)

This is what I get.
1) If I select the first one, it gives me a blank screen with a cursor, won't let me do anything at all
2) If I choose the second one, it runs thru a program and alows me a login prompt
3) after login it comes up with "Username@gateway~$:" from there I can type what I desire. I do not know linux enough to give any commands. 

I plugged in my USB CD/DVD drive with my install dick and tried again. I hit F2 at first start and it gives me a menu and allows me to select where to boot from. I chose USB CD/DVD drive. and great, it boots from the disk. but will not allow for a re-install, just makes the system run as usual. If I shut down, it is the same process. What can I do to re-install this disk?  can I re-boot while the system is now up and running? 
:confused:

---

### Post by darkod on 2009-12-20
> **cheesefry said:**
> 
1) If I select the first one, it gives me a blank screen with a cursor, won't let me do anything at all


That can also mean problem with the video driver. If you have ATI or Nvidia try this:
Select the recovery mode entry. In the next menu choose something like "root with networking" to have internet access. When it loads the command prompt install EnvyNG package with:
sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

From the menu select your manufacturer. No need to remove current driver. Follow the instructions, it will download and install a driver itself. After all is done, reboot and this time from the menu select the normal mode entry. See if it works.

---

### Post by cheesefry on 2009-12-20
How do I know if I have ATI or Nvidia. How do I find out? I just don't want to make things any worse. I am now affraid that since I did a complete install, my System restore dick for Win XP wont work if needed.

---

### Post by darkod on 2009-12-20
Sorry, I just checked your first post again, google says Gateway LT20 has Intel graphics. That package can't help with Intel graphics as far as I know.
I'm not sure what to try next honestly...

---

### Post by robio376 on 2009-12-20
I don't know if this will help. I have an Acer Netbook with similiar specs as your. I just don't have bluetooth or (WAN) cellular card. When I used an external USB dvd-drive Ubuntu wouldn't install correctly. But when I tried with a USB stick it worked perfectly. If that doesn't work I would redownload and make sure you have nothing else downloading in the background, and burn at the slowest speed possible.  As far as your system restore (For XP) read your manual for boot options such as F12 key at boot, mine I had to but with syslinux on a thumbdrive and make my recovery partition active then reboot.

Heres how to activate recovery for your gateway:

Enable disk-to-disk recovery
To enable disk-to-disk recovery (hard disk recovery), activate the BIOS utility,
then select Main from the categories listed at the top of the screen. Find D2D
Recovery at the bottom of the screen and use the <F5> and <F6> keys to set this
value to Enabled

---

### Post by cheesefry on 2009-12-20
Thanks dude. I havent given up yet, but it's nice to know I still have options. I may try the USB thing next. Actually the netbook is going thru a bunch of updates via the update manager. Maybe this will help??

---

### Post by robio376 on 2009-12-20
I did the updates for my netbook and everything works. Good Luck!

---

### Post by cheesefry on 2009-12-20
Even your wireless? My boot problem seems to have gone away, but still no wireless.

---

