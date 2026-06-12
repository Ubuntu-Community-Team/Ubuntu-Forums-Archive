---
title: "Attempting 10.10 Fresh Install"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by jda8818 on 2011-03-05
Hello All:

Attempting new 10.10 (32 bit) install on Asus P4C800E motherboard (2GB).  Fairly early on in the process I get the following series of messages.  This is approximate since I copied it down w/pencil and paper:
```

BusyBox v1.15.3(Ubuntu 1:1.15.3 - 1ubuntu5) built-in-shell (ash)
Enter Help for a list of commands

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed. Input/Output error

Can not mount /dev/loop0/ (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

udevd[73] worker[116] unexpectedly returned with status 0x100

udevd[73]: worker[116] failed while handling '/devices/virtual/block/Loop0
```And then nothing happens for a long time (until I give up).  Has happened several times, different CD's, different CD drives, checksums OK.

As always, any and all suggestions are appreciated!

JA

---

### Post by jda8818 on 2011-03-06
Hello, All!

While hoping for a reply to my new thread, I thought it might be enlightening to try to find out what the odds were that there would ever be any response at all, in other words I'm asking myself "is it really worth it to check the "Installation & Upgrades" forum (& email) repeatedly during the day (after day) looking for a response that might never arrive?  

Well, the column headers allow a sort by column, which in this case allows one to arrange the (Normal) threads both chronologically and by number of replies.  It turns out that there are over 710 pages of unanswered threads (zero replies) at 20 threads per page going back to April 24 of 2008.  That's 14,080 unanswered threads over 1,046 days.  Some of these unanswered threads have been viewed thousands of times.  

On the other side of the coin, at the present time there are 3,811 pages of normal threads, or 76,220 threads in total of which 81% receive a response. That's 4 out of 5.   Not bad.  Of course one might have to wait several years ...

How many of these threads with replies were SOLVED?

What is the mean number of replies per thread?  The average delay to the first reply ...  

I have lots of material to post replies to my own thread,  maybe someone will notice ...

Thanks in advance!

JA

---

### Post by Quackers on 2011-03-06
Have you tried booting from the live cd and selecting "try ubuntu"? Do you get to a desktop?
Have you checked the cd for errors?

---

### Post by jda8818 on 2011-03-06
Hi Quackers, Thanks

I downloaded the latest ubuntu-10.10-desktop-i386.iso from the main download site, burned the image to a CD using InfraRecorder on a windows machine. and then booted from that CD on my target machine.   The installation fails as I described before I ever get to a desktop. 

The md5sum of the .iso file is correct.  The CD that is created shows files and directories, etc. rather than the .iso file.

I've tried this several times on two different machines, one of which successfully runs 10.04.2 installed from a CD.  I've used different CD's, different drives, etc.  No luck.

How do you want me to check the CD for errors?

Once again, Quackers, Thank You,

JA

---

### Post by Quackers on 2011-03-06
Did you select "burn image" when burning the .iso, or just burned the files?
The .iso file must be burned as an image.
If you did that, and when booting from the disc, do you get to a purple screen that has a little man icon at the bottom?

---

### Post by jda8818 on 2011-03-06
right, little man in a circle, then the ubuntu 10.10 logo in the center of the screen with the 4 little progress dots below it.

Fails as I described. or most recently, never fails explicitly but just goes on and on without any disk or CD activity with the progress dots ticking along forever.

How do you want me to check the CD for errors?

Thank you Quackers!

JA

---

### Post by Quackers on 2011-03-06
Ok, reboot again please. When that first purple screen appears (with the little man icon) press any key. Then choose your language and on the next screen you'll see some options. One of the options is to check for errors. See if that runs ok.

---

### Post by jda8818 on 2011-03-06
OK Quackers:

Check for errors reports:

```
Check finished: errors found in 1 files!
pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-1_all.deb:
```So I'll create another CD and report ...

Thank You!

JA

---

### Post by Quackers on 2011-03-06
You're welcome.
One error is one too many I'm afraid.
When you burn the image again, try selecting the slowest speed available, and, if possible, verify the burn as well.
Good luck.

---

### Post by jda8818 on 2011-03-06
Success!

Thank you Quackers!

All is Well!

JA

---

### Post by Quackers on 2011-03-06
Aha! Excellent news :-)
Enjoy!

---

### Post by GameboyRMH on 2011-03-19
I'm having a similar, baffling problem. I've downloaded ubuntu 10.10 i386 via bittorrent, and I'm getting the same error, but I haven't burned the CD - I mounted the .ISO image in a VM and got this error when running the check. I've re-hashed the torrent to confirm it's valid. Any ideas?

---

### Post by jda8818 on 2011-03-20
GameboyRMH:

In my case, the .iso file md5sum was correct, but apparently I picked up an error during the burn process.  I reburned and all was well.

In your case, If the md5sum of the downloaded file is correct, you're probably OK as far as that is concerned, but about the VM process I'm not so sure ...

why not burn a CD and try the install that way?  You can check the files within the image as I did; I have no idea how to check the individual files in a VM setting ... possibly you could look up the checksums of the individual files on the Ubuntu website and run checks on each file.  Easier, tho, IMO, to just burn the CD.

good luck!

JA

---

