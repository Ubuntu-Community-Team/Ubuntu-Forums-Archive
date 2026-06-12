---
title: "dumping HD and starting fresh"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by penholder on 2010-08-28
this is where my naiveness shows.  i have never totally cleaned a comp before-let alone one with Ubuntu which i am brand spanking new to.  

can some nice person give a pretty lady a stop by step please?  you don't need to link-i can google etc.  just the overview is fine.  i am currently downloading 10.04 and am going to disc that for install.  

thanks #-o

---

### Post by xtracool_protik on 2010-08-28
Hey by cleaning up - I would assume formatting complete HDD?
If thats the case u should take backup of everything thats important.
And then pop in Ubuntu CD, reboot while going through installation there will be a step it reads "Erase entire Hard Drive" or "Use entire Hard Drive" check it and go ahead u'll have cleanest possible Ubuntu installation
If u want to install ubuntu on some partition then u need to check manually mange partitions and then need to select options according to ur needs

---

### Post by penholder on 2010-08-28
thank you!  i think was just going to do what i needed to do without a reinstall, but considering that i haven't put anything on there yet and that it is running 8.10 i figured it was the most perfect upgrade time ever.  i might never get an experience as virgin as this.

---

### Post by penholder on 2010-08-28
ok.  i sat thru an hour download and then burned to CD and guess what? my thinkpad won't recognize the cd.  HELP ME!  can i do a straight upgrade since i am wired right now? would that have the same effect?

---

### Post by freezkatlodge on 2010-08-28
oops

---

### Post by freezkatlodge on 2010-08-28
what model Thinkpad? 

You are running 8.10 LTS?

10.04 hase a very similar appetite for system resources as XP.

It likes at least 1GB Ram and a 2GHz CPU

8.10 ran nice on a 800Mhz Pentium3 I had but 10.04 wasn't fun at all

Don't use CDRW media, CD-R seems to work best, Record at 2x or less speed

If you have a really old Thinkpad in the boot options menu type in boot=nocdma or ide=nocdma

that should get you there

---

### Post by penholder on 2010-08-28
it is a t21. got it cheap because i needed a workhorse.

i am wiping out ubuntu 8.10-NOT windows.  there is literally nothing on this comp that i can see, however i don't think i can see everything since i am locked out of admin and that pisses me off.  i have no way to get the password to unlock and erase, so i am chooseing to wipe clean before my semester starts.  then i have a fresh and clean comp that is strictly mine.

---

### Post by penholder on 2010-08-28
> **freezkatlodge said:**
> If you mean you are wiping out a Windows machine and starting fresh...STOP!!!!!!!
If you want to clean up because of malware and you can't get rid of it yourself take your computer to somebody that can. There is a bit of a learning curve and jumping in head first will end up being very painful. Starting out with a ***live cd*** is easiest. Then most people go with a dual boot set up. They can use either windows or Linux on the same machine.
[COLOR=Purple]
 i am doing ubuntu on ubuntu.[/COLOR]  
 
If you wipe your HDD and erase windows you will be very sorry. Linux is a lot easier than it used to be but it isn't as widely supported as windows. Things to consider: Do you have access to another computer? What amount of computer experience do you have? What peripherals you have? What office applications you need to maintain?  How old of a computer do you want to change? Do you enjoy movies and other media on your computer? Do you do any gaming on the computer? 

[COLOR=Purple]i have 2 other comps both windows based. not worried about that. i am taking to linux because i feel like i have been made stupid by windows.  i want to really learn what to do, not just go thru the MS motions.  i also just have a general dislike for MS[/COLOR].

If you want to change an old windows98 PC, Ubuntu 10.04LTS will run like mud.
Lexmark printers are not supported.
While most of anything you want to do on your computer can be done with Linux, you almost always need to put something together yourself. Like furniture from IKEA. Except for software updates, nothing is automatic.

Don't let me scare you. It's worth the effort. It's fun. It's kinda like camping. It's really cheap too. Most importantly there are literally hundreds of thousands of experts out there that are willing to help you, just because they believe in the generous Linux community and the freedom of open source software.

[COLOR=Purple]love that![/COLOR]

---

### Post by freezkatlodge on 2010-08-29
I saw later you were doing ubuntu to ubuntu I would stick with 8.10 and just reformat.

10.04 is kind of a system hog. don't event think of kde on a 800Mhz

Isorecorder in windows works great for burning cd-rom

---

### Post by penholder on 2010-08-29
thanks.  i just burned 10.04 for the 2nd time.  guess i will go and try 9.  can't find a 8.10.

---

### Post by freezkatlodge on 2010-08-29
wouldn't upgrade. I would just start over with 8.10. 

Use the direct download iso image from the Ubuntu site link. Do not use any bit-torrents.

did you download and get a file that looks kinda like this?
[IMG]http://t1.gstatic.com/images?q=tbn:ANd9GcTiomRnUzIrVqA8tloU4a3IG3Y2LXJICCZoO_nrTVSOLod5Oq4&t=1&usg=__e1gDe6BaJiBfzYSPtvHSxUioZsc=[/IMG]
I like to use Isorecorder to burn bootable CDs on a windows machine.
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

When you download turn off all anti-virus and anti-spyware programs.  (this is critical. you will have gaps in the downloaded image if you  don't)
 
 Right click on the ISO image icon. Select. **Copy to CD** (it might say burn to cd I can't remeber)
Until it is done downloading leave that computer alone. Download it to some place easy to find like the desktop.

Put a new blank CD-R disc in your cdrw drive

Turn off all anti-virus and anti-spyware software (this is critical. you will have gaps in your recording if you don't)

Right click on the ISO image icon. Select. **Copy to CD** (it might say burn to cd. I can't remember)

There will be a preferences options tab click that and select a 1x writing speed.

Put the new cd in your thinkpad and restart it.

During the restart process you might be able to just let it go and it  will boot the Live CD on it's own. If so all you would need to do is  select the install to hard drive icon on the desktop. (The password for  the root user account on the live cd should be _root_)

If it doesn't go straight into the live cd, you will need to direct your  computer during the start-up process. While it is first starting you  will have options to go into BIOS or if you are lucky a  Boot options  menu.

If you have a Boot options menu. Watch during the start-up process watch  and it will tell you what to press to enter the boot options menu eg  Tab, F12.... Then  All you need to do is select the cd drive and press  enter. 

If you need to go into BIOS watch during the start-up process and it  will tell you what to press to enter BIOS. eg. Delete. Esc,  Then you  will need to find the boot device priority menu. It can have its own tab  or it can be under BIOS or Advanced BIOS options. Likely it will be set  to boot in this order: Floppy,Hard Disk,CD-ROM. You need the CD-ROM  drive to boot first.  Once you get that straightened out press F10 to  save and exit.

Then it should boot straight to the live cd and you can proceed with a full install or just play around with the live cd

---

### Post by mörgæs on 2010-08-29
Best is to forget everything about 8.10. It is unsupported and hence a security threat. 

Go for a clean install of 10.04.1, if you have enough RAM. If the regular install does not work, the text-based (alternate) is worth trying. Remember to have wired internet access while installing.

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

If you want something light on the resources (=fast), you could try this script:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

It installs only the parts of Ubuntu you choose.

---

### Post by freezkatlodge on 2010-08-29
I just tried 10,04 0n a 800Mhz computer and it sucks. Also they want to put in on an old laptop with most likely 256MB of pc100 sodimm on it. At maximum they could upgrade to 500MB. 

You tell me will 10.04, without chopping up the kernel will run on a laptop with a 800mhz cpu and 256mb of RAM?

I think 8.10 is a better option than going to a distro like DSL (DamnSmallLinux) Puppy Linux is pretty good. Wireless support is fair at best.

10.04 isn't a good option. I don't think penholder is ready to start assembling kernels, text editting and working in the command console*... just yet...give them some time.



(*aka. terminal, shell, konsole,  Dark & Spooky Scary old school Linux Land )

---

### Post by mörgæs on 2010-08-30
> **freezkatlodge said:**
> 
You tell me will 10.04, without chopping up the kernel will run on a laptop with a 800mhz cpu and 256mb of RAM?


Yes, I have one of these (except it is 500 MHz and not 800, Compaq Armada M700). Minimal install, of course. It takes a while to boot, but after the boot is finished normal use (for example Chromium with Flashblock) works fine. 

Damn Small Linux has been stalled for a couple of years. I doubt it will ever get in motion again.

---

### Post by freezkatlodge on 2010-08-30
How does somebody do a minimal install? 
Can apelike people like me figure it out ? 
I am only familiar with full installations. What isn't being installed?

Like I said before, chopping up an operating system to get it to work isn't something us Windows Converts are accustomed to. If there are customized ISO images available, that would be very helpful.

Puppy Linux is very fast and easier to use than before but the manual mounting of drives and starting of peripherals is clumsy.

---

### Post by mörgæs on 2010-08-30
It is not difficult, but it takes longer time than a full install.

Since a minimal install is cherrypicking, there is no one-size-fits-all ISO available.

Small:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

Extra small:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
There are many screen shots here, but it is easy.

---

