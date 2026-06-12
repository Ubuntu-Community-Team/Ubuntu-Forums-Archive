---
title: "Install hangs at &quot;configuring hardware&quot;"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by don-bothell on 2010-11-07
After burning 5 CD's  for both 10.10  and 10.04 which checked OK but though the install seemed
to complete on some occasions (some showed an error, but no diagnostic) the restart would
stop on a blank screen.

I gave up and asked for a disc by mail.  I was sent a 10.10 and after several tries on both
hard drives the install always hangs (stopped for hours) at "configuring hardware".

I have been able to re-install my Ubuntu 7.10 from its original downloaded install disk and
everything seems fully functional.  Would like to upgrade but how do I proceed ??

System:  AMD Athlon 64     AMIBIOS 8.00.09    1800MHz    ASUS K8N-E board   One GB ram

---

### Post by dino99 on 2010-11-07
you might install by adding either: nomodeset, nolapic; noapic, noacpi, irqpoll on the boot line (F6 if i remember)

noacpi often do the job

---

### Post by sikander3786 on 2010-11-07
As mentioned by dino99, adding some boot parameter might help.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

7.10 is no longer supported so I wouldn't advise to install it.

The black screen problem with 10.04 could have been fixed by nomodeset parameter also.

Does the Live session itself run properly? Are you sure there isn't actually any problem with the hardware itself?

---

### Post by don-bothell on 2010-11-07
> **sikander3786 said:**
> As mentioned by dino99, adding some boot parameter might help.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

7.10 is no longer supported so I wouldn't advise to install it.

The black screen problem with 10.04 could have been fixed by nomodeset parameter also.

Does the Live session itself run properly? Are you sure there isn't actually any problem with the hardware itself?

7.10  is working fine but I do not want to stay with a non-supported platform.
The live session for 10.10  is what I am using to send this - even though the
hardware test program under systems says my keyboard does not work !!

How are boot parameters added ?
I suspect  the ASUS drivers need updating but cannot find them anywhere on the web, though
they do offer lots of help  for windows users.

You ask about hardware problems ?  when in 7.10  there seem to be none.  But the live session
10.10  has no sound output and reports incorrectly that the keyboard is non-functional.

---

### Post by sikander3786 on 2010-11-08
> 10.10 has no sound output and reports incorrectly that the keyboard is non-functional.

If you are having those problems from the Live CD, they will continue to appear after a complete install. You will need to look for some workarounds regarding your hardware on the forums/web. Or give 10.04 a try.

You can add boot parameters by pressing F6 at the Try Ubuntu/Install Ubuntu page. See the page I linked in my above post for an explanation.

Edit: > the restart would stop on a blank screen.

If you got were able to install 10.04 successfully. And if all your hardware was working, we can solve that problem much easier than the one's with 10.10. In my opinion, if 10.04 works, it would be better to install that. You just need to add **nomodeset** and then install the graphics drivers for you card. Blank screen problem should go away by that.

---

### Post by don-bothell on 2010-11-08
> **sikander3786 said:**
> If you are having those problems from the Live CD, they will continue to appear after a complete install. You will need to look for some workarounds regarding your hardware on the forums/web. Or give 10.04 a try.

You can add boot parameters by pressing F6 at the Try Ubuntu/Install Ubuntu page. See the page I linked in my above post for an explanation.

Edit: 

If you got were able to install 10.04 successfully. And if all your hardware was working, we can solve that problem much easier than the one's with 10.10. In my opinion, if 10.04 works, it would be better to install that. You just need to add **nomodeset** and then install the graphics drivers for you card. Blank screen problem should go away by that.

I tried the nomodeset option on the install but it still hangs at "configuring hardware".
Earlier, I downloaded a CD image for 10.04 which would not install either that's why
I opted for the mailed disk hoping download issues might have been a problem - but
Iwas sent the disc for 10.10 which not only will not install but fouls up 7.10 on my
other drive, though I specifically limited the install to the non-7.10 drive. Fortunately
I have been able to re-install 7.10 but that gets tobe time consuming.

You are probably right that since 7.10, the improved Ubuntu's have left my hardware
unsupported, though I tried hard when building this computer to use generic stuff.

My searches for hardware support are so far barren.  ASUS offers lots of automatic
help for their windows users but does not even mention Linux

I have opened a thread to ask for what motherboard I should change to with some 
assurance that the next Ubuntu release will not leave me behind again.

---

### Post by don-bothell on 2010-11-09
I have downloaded the "alternate"  version of 10.04
It gets to about 70% complete and gives a message:
  Please insert disc labeled Ubuntu 10.04.1 LTS-Lucid Lynx release .......
 
This is the disc that I am trying to install from, and reinserting does nothing.

I checked a thread for this error and found many people with this problem,
but no resolution.

On restarting the install and trying "Fix broken system"  I can get a shell and look
into all the files but I don't know what to check to heal the system ???

---

### Post by sikander3786 on 2010-11-10
> **don-bothell said:**
> I have downloaded the "alternate"  version of 10.04
It gets to about 70% complete and gives a message:
  Please insert disc labeled Ubuntu 10.04.1 LTS-Lucid Lynx release .......
 
This is the disc that I am trying to install from, and reinserting does nothing.

I checked a thread for this error and found many people with this problem,
but no resolution.

On restarting the install and trying "Fix broken system"  I can get a shell and look
into all the files but I don't know what to check to heal the system ???
If the installation stuck at 70%, I don't think it would be healable.

I feel it is a bug with your hardware. You can submit a bug at launchpad and let the developers track it down for you.

Instructions on submitting a bug report, post # 7 in this thread.

[http://ubuntuforums.org/showthread.php?t=1611252](http://ubuntuforums.org/showthread.php?t=1611252)

---

### Post by don-bothell on 2010-11-10
> **sikander3786 said:**
> If the installation stuck at 70%, I don't think it would be healable.

I feel it is a bug with your hardware. You can submit a bug at launchpad and let the developers track it down for you.

Instructions on submitting a bug report, post # 7 in this thread.

[http://ubuntuforums.org/showthread.php?t=1611252](http://ubuntuforums.org/showthread.php?t=1611252)


I followed your link, then searched for Mythbuntu but found blank page for amd64.
How do I get to install in debug mode ??

---

### Post by boylejv on 2010-11-14
I had the same problem trying to install Ubuntu 10.04.1 on an old Pentium III Compaq (600 MHz), with 512 MB RAM and a 10 GB hard drive.

I would install the Live CD and select to Install and the installation would progress to 93% and stall at either "Configuring hardware ..." or "Starting PC Card services...".

I tried all of the boot parameters mentioned at various websites including acpi=off, noapic, nolapic,, etc and also tried passing the hw-detect/start_pcmcia=false option as well.  None of these worked.

What I finally did get to work took 4 hours.   Instead of selecting Install, I selected to Try Ubuntu and let my PC boot up (which it did every time with the Live CD).   There was an Install icon on the desktop to perform the install.   Rather than using the icon, I copied the command from the icon's properties and pasted it into a terminal window hoping that I would get more information on stderr.   I got no messages at all that way however.

The install continued and after seeing that the terminal window was not providing any information, I put the install into the background (CTRL-Z and then bg <process id>) and closed the terminal window.

The install proceeded again until 93% and stopped at "Configuring hardware..."    In an attempt to see what might be happening, I reopened a terminal window and ran "ps -ef" to see what processes were running.  The processes were changing and this showed me that the install was still doing something but very slowly.   Eventually though it appeared to hang with only the install.py process running.

So I decided to take a look at the Python code and I opened a file browser from the Places->Computer menu item.   And low and behold, the install proceeded to "Starting PC Card services..."

Each time after that when the install seemed to hang again, I opened the file browser using Places->Computer and this seemed to work each time in making the install continue.   Sometimes it did not fix it right away but if I waited until the install.py process was all that was running, it seemed to work.

Needless to say, this was an onerous process.   It took about 3 more hours to get through the install this way.  At one point, the progress bar actually regressed from 98% back to 94%.   I can't explain that at all.

It isn't just waiting for a slow install to finish.  I ran it once overnight and it was still stuck at "Starting PC Card services..." 7 hours later.   It seems that some interaction with the computer like opening a file browser wakes up something and the install proceeds again.   Perhaps the second IDE drive I have is going into hibernation or something and the file browser wakes it up.   This is just speculation.

I hope this sheds some light on the install problem for someone who knows the process in detail.   Why would starting the file browser make a difference?   Perhaps then we could get to the root cause(s) of the problem and others wouldn't have to do this 3 hour manual process.

---

### Post by boylejv on 2010-11-14
One other thing that I did during the install was I set the partition sizes manually.   The default for my 10 GB hard drive was to set the swap to 472 MB and the rest for the ext4 filesystem.   472 MB seemed low for swap space so I increased it to 1 GB.   I read that swap needs to be at least the size of RAM.  I have 512 MB so I doubled it for the swap partition size.

I had done this before to see if it helped the install succeed.  The install still failed with the increased swap and only the interaction with the PC by opening a file browser seemed to prompt the install to proceed.  I just mention that I increased the swap partition just for completeness.

---

### Post by don-bothell on 2010-12-05
I have managed to upgrade from 7.10 to 8.04
The problems in trying to go up to 10.04  or  10.10  remain.
Why would my sound card work fine in 7.10 and 8.04 but then fail in 10.10 live CD ?

---

### Post by Quackers on 2010-12-05
From time to time as I understand it, support is dropped for some hardware. I get the impression that it can be caused by the hardware manufacturer rather than a Linux thing. But I could be wrong :-)

---

### Post by don-bothell on 2010-12-16
I have now had success installing 10.04.1   32 bit on my Athlon amd64.
I used the terminal from the try-it mode implementing command found at the
 Properties for the Icon to Install.  This was a suggestion from another user
 and may not have been needed with this new iso download. It does seem 
  like a way to get a little more info about what is happening - and a way to
  access the system if it hangs.:p

---

### Post by Blaab on 2011-01-25
Hi All

I'm having the same problem.

I'm installing to a new partition ext4 formated (part of the install) and all runs fine untill it reaches the 'Configuring hardware' stage at which point it does seem to tick over every few mins but i left it over night last night (roughtly 8 hours) and it was still on the same spot.

I know its not the CD wich we created from the ISO download, as this was used to install a version on my friends laptop. I'll try the boot options as mentioned, but was wondering if this issue has other possible solutions?

[B]
MY SPEC:[/B] AMD Duel Core 64 (2.3gh), SLI nVidia graphics, 4gb ram, 140g partition.

Thanks in advance :D

---

### Post by Blaab on 2011-01-26
A Quick Update!

Last night i tried both 32bit and 64bit of 10.10 and also 32bit 10.4 but all versions still just seem to come to a stop. both versions of 10.10 stop at 'Configuring hardware' while 10.4 got past that but then hung with just a blank desktop background.

If anyone has any ideas i would be most greatful!

---

### Post by trendle on 2011-07-10
Well.. it's now 11.04 and guess what.  I'm getting a blue screen just after configuring hardware hits ~97%  on an install off the alternate install disk.  No way to see anything about the cause.
If I hit <CTRL>C then it flashes the 97% and goes back to the blue screen.

So no progress from the previous poster's problems on older versions.  :(

It's totally depressing, I'm wasting so much of my life trying to work around flakey software.  Time to go back to M$ if this doesn't get fixed.:(

I'm using an atom D510 MB  with an 4 port sata expander in the ide.  But the live cd has no obvious problems.  

The main problem is that you do not seem to be able to setup an LVM home partition from a live install.

@Quackers@  You may be right, but that doesn't excuse leaving 'hopeful' ubuntu users hanging in limbo for hours.  

What about a quick 'unsupported hardware' message.  It doesn't help spread the word.

---

