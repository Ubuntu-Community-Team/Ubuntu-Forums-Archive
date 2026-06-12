---
title: "Old hardware, install hangs in detecting HW"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by CyberBob on 2005-09-22
PROBLEM SOLVED!  SEE LAST MESSAGES IN THREAD

I have been unsuccessful (for three evenings now) at installing Hoary on my old PC.  ](*,)   Here's a snapshot of the hardware:

PCChips M571 motherboard/TX ProII chipset/onboard vga
Cyrix 300Mhz cpu
AMI bios
128 MB ram
4 GB hda
300 MB hdb

So far I have made some progress (in disabling all of the shadow ram in the bios), and finally this evening I even got past the network config and it found the ubundu mirror site.  However, the "detecting disks and all other hardware" screen has maintained at 0% progress for nearly an hour now.  :-\"

 I guess this is as far as I can get without some help from anyone out there with a similar problem who might have figured this out already.

I have scanned and searched these forums and found one other post similar to mine (posted a long time ago), but alas, no replies with a fix.

Can somebody help me? :-?


Thanks in advance ...

Bob

---

### Post by CyberBob on 2005-09-24
... Anybody?

---

### Post by Herman on 2005-09-24
I have an old 'Book PC' (Bki 810 v1.6a) which I used for installing 'Warty' on maybe fifty times! (Because I'm one of those weird people who get a kick out of installing, then formatting and re-installing just to play with the installer and partitioner). When I got my new Hoary CD's, I had a similar problem as you just described.
    I was able to install 'Hoary' on all our newer computers fine, but the old 'Book PC' seems to be only good for 'Warty'.  I suggest you try installing 'Warty' and you'll probably find it'll go right in without a problem. Or maybe even skip them both and try advancing right to 'Breezy'!
          I was reluctant to answer for a while because I'm not sure about what you meant about disabling something in your BIOS? I'm still not sure about that bit, but good luck, I hope it all works out for you!

---

### Post by CyberBob on 2005-09-25
Thank you Herman - I did as you suggested and I was able to progress through partitioning and into the ubuntu base system install section ...

Then the base system install stops with errors:

1st time - debootstrap program exited with an error, checking console 3 revealed -

dpkg: error processing debconf (--install):
subprocess post-installation script killed by signal (illegal instruction)

2nd & 3rd attempt - different packages returned errors on install

4th try -  same as first attempt but debconf error was killed by a segmentation fault instead of an illegal instruction.


My frustration level is high but I am tenacious ...

I have also tried installing Debian 'Woody' and 'Sarge'  which take me no further than I have progressed here - either the install 'hangs' or I get a segmentation fault before even getting to partitioning.  

Also my very first attempt was to install the Breezy preview release (which I installed flawlessly on an old IBM PL300 that was sitting idle at work), but this (very same) CD would not even boot on the current machine.  All other install CDs boot fine - and by the way all CDs were burned at 4x.

I will not give up ... any other suggestions??

Replies with best guesses are always welcome!!

---

### Post by Teroedni on 2005-09-26
Do you got 2 Harddrives
If so remove the small one and try with the biggest
May be an explination  why it stops

Worth a try atleast;)

---

### Post by CyberBob on 2005-09-26
Thank you for the suggestion, Teroedni.  I just tried this but alas, I still get an error during base system install:

this time it is -  Couldn't retrieve e2fslibs ...

... so I selected <Go Back> and attempted to redo the base system install step.

this second attempt (w/o hdb installed) gave another error, about 40% into the install base system step, of debootstrap system exiting install .. checked console 3 and found that:

dpkg: error processing /var/cache/apt/archives/libc6... blah blah blah,
similar subprocess errors that I have previously encountered.  Interestingly, they are never in the same place twice - even if I just reboot and keep all other variables unchanged.  Hmmm???

It was worth a try, but it seems that the second HD is not the culprit in my old PC having install problems.

Other suggestions/ideas/hunches always welcome!!

---

### Post by CyberBob on 2005-09-26
A new observation and curiosity - comparison with Live-CD

I am now running Hoarty Live-CD off of my Compaq Presario laptop.  The live CD booted up flawlessly on this machine.

When this live CD autodetected my network settings it did so automatically without problem through my router.  However, in many attempts at trying to install Hoarty or Warty (or Woody or Sarge for that matter) the autodetect failed - I had to unplug the old PC from the router and go direct through my cable modem to get it to autodetect successfully.  Wonder why this is so??

The eth0 on the old PC is a 'tulip' compatible pci card in the old PC ...  even though I have been "connecting direct" the old PC install continues to fail. :(

---

### Post by Teroedni on 2005-09-26
seems like something is unstable
Can you underclock your cpu to see if that helps??
To 250 or perhaps as low as 200mhz

---

### Post by az on 2005-09-26
It could be anything.  Bad memory, bad ide cables, broken fan.... anything.  Did that machine run another operating system recently?

---

### Post by CyberBob on 2005-09-26
Teroedni:  I must confess that I have no idea how to underclock the cpu.  Is it something that can be set in the BIOS settings at startup?

azz:  This machine has been sitting idle for a few years.  I *have* run Redhat 7.2 (I think) and Suse 6.3 on it several years ago (as you can tell from the version numbers)  - also ran Windoze 98 and 95 on it for a long while before then.  I mothballed it  a couple years back because I got frustrated with Redhat.  What I see happening now with ubuntu has rekindled my interest in Linux and I was hoping to get this old thing working for my two boys to dinker with.

---

### Post by CyberBob on 2005-09-26
After recounting my history with the old PC to azz, I figured I would try to re-install Suse Linux 6.3, hey what the heck?

Everything seemed to be going fine, and I was getting ready to announce my good news here, but just then afer sucessfully installing 505 packages and only with 66 to go, the install just hung there, like an outlaw on an old hickory tree.

I don't know what to do.  I really would like to get Linux, especially ubuntu, installed on this thing.  

azz said it could be anything:  bad memory?  the AMI Bios runs through a memory parity check every time it boots - you can see the number of bytes checked whizzing by.   I have never seen this fail ... nevertheless could it still be bad somehow???

ide cables?  the partitioning seems to run smoothly enough ... and it has gone through this about a dozen times now, never saw an error in preparing the drives so I assume the ide cables are ok.

the fan - I have the cover off and the cpu fan is running fine.

I'm willing to check out anything anyone else can think of - I do not know how to "underclock" the cpu - can somebody give me a hint??

Thanks to all who have contributed so far ...

Bob

---

### Post by az on 2005-09-26
I think the breezy install cd has memtest86, but not Hoary (not sure)

You can visit the memtest86 website and make a boot floppy.  Some memory errors take minutes to hours before you find them.  The boot-up test basically checks for the presence of the memory.

As for other test, maybe somebody else can point you to a useful utility cd of some kind...

(Maybe condensation on the optical drive (I recently fixed a cdrom by wiping the part which said in big red letters (DO NOT MAKE PHYSICAL CONTACT) with a Kleenex)

---

### Post by Teroedni on 2005-09-27
Heres an link for your motherboard

[http://m571.com/m571/jumpers.htm](http://m571.com/m571/jumpers.htm)

Try changing the internal clock settings

At the end of the site there is a link to a pdf download of the manual for your board

You can also try to change the ram timings if you have edo
choices here is 70 or 60 ns

Also see if you have installed the ram in the right slot for your amont (stands in the manual)

It may also be that your hardrives are dead
So _If_ you can try another hardrive 


Good Luck

---

### Post by CyberBob on 2005-09-27
I used memtest86 and let it run for almost 3 hours last night - it went through two full passes of all default tests with no errors.  RAM seems to be OK ...

I will try adjusting the internal clock settings this evening.  Thanks for the link, Teroedni.

I was thinking since last night that something might be wrong with the HD.  I have downloaded "Data Lifeguard Diagnostics" from the Western Digital website, and made a bootable mini CD.  

Once I check these items later today I'll update this post ...

OK, here goes:

1. I checked the HD (Western Digital AC24300, 4.3 GB) using "Data Lifeguard Diagnostics" from the Western Digital website and found NO ERRORS on the drive.  The secondary slave drive was totally removed from the box.

2. I checked the jumper settings on the main board and found that the cpu internal clock speed was already set at its LOWEST setting (1.5X/3.5X) per the manual cited by Teroedni in the link in his previous post.

So then, the RAM , HD and CPU all check out 'ok' as is.  When I attempt installing Hoarty, I get to installing the base system and run into an error,  "segmentation fault" when I check virtual terminal 3.  The lines immediately above this error read as follows:

insmod /lib/modules/2.6.10 etc ... many of these, then after the last one

File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
   No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
   No volume groups found
Reading all physical volumes.  This may take awhile ...
Segmentation fault
Segmentation fault
Segmentation fault


I find by searching with Google that a segmentation fault is when an application is attempting to access memory that it has not been allocated.  Is this happening with the installer or is my hardware the problem.  If hardware, where do I look next?

Thank you patient readers while I struggle with my old PC here ...

---

### Post by Teroedni on 2005-09-28
f1,5X/3,5X i think is for automatick config from monitor
when you have 300mhz on it i higly doubt it set at 1,5 you would need a high fsb then
I dont think your  motherboard support 200 mhz fsb and in such case it would be overclock
Edo on 200 mhz;-) 

Choose 2,0x 1,ox or anything below 3,5x;)

I found some info about cyrix fault and it metion  Sig 11 segmention fault

links
[http://www.bitwizard.nl/sig11/](http://www.bitwizard.nl/sig11/)

[http://gwyn.tux.org/~balsa/linux/cyrix/p10.html](http://gwyn.tux.org/~balsa/linux/cyrix/p10.html)

[http://gul.ime.usp.br/Docs/docs/HOWTO/other-formats/html/HOWTO-INDEX-html/Hardware-HOWTO-4.html](http://gul.ime.usp.br/Docs/docs/HOWTO/other-formats/html/HOWTO-INDEX-html/Hardware-HOWTO-4.html)

in the last one they recomend disable APM try that

Another thing you should try is disabling pnp(Plug and Play)

I wish you the best luck and hope you still have patience to fix this.
Regards Teroedni

---

### Post by Teroedni on 2005-09-28
Here is something to

yrix 6x86 CPU
I have many machines running linux on Cyrix 6x86 CPUs on ASUS P55T2P4 motherboards. The 6x86 gives Pentium Pro speeds (or pentium speeds at its "P" rating) but appears to the system as a 486. The only problem I have noticed under redhat 4.x is that the 6x86 does not support the Pentium Machine Specific Registers (MSRs), some of which can be rather handy in certain applications (the Time Stamp Register can give accurate time to 1 clock cycle). The Cyrix gives very good bang for the buck.

Actually, the cyrix does appear to support the MSR registers but the kernel thinks the cpu is a 486 (because it says it is) and so it doesn't use those features. Cyrix tech support was negligent, however, in not responding to my inquiry regarding support of the MSRs. Installing the 6x86 kernel patches may be sufficient to permit use of these registers.

There are problems running Redhat 5.0 on a cyrix machine which has not had any problem running Redhat 4.0/Linux2.0.27 for many months (uptimes of order 100 days). The problems manifest themselves primarily in two forms: the install program hangs ocassionally and GCC dies due to a signal 11 while compiling large packages (the kernel is a good example).

There is a linux 6x86 FAQ. Note, however, that the problems it mentions are apparently not the problems with boxes that have run older releases but are unreliable in redhat 5.0); they appear to be primarily problems with people who are running second rate machines. The Sig11 FAQ gives a little more upto date info. Redhat has been working on this problem, but they were unable to reproduce it on a newer Cyrix processor. In their this patch which adds a fair amount of support for cyrix chips. As far as I know, they do not supply a patched boot disk, which is unfortunate because they install process is one of the things which is unreliable. Redhat also mentions the older 6x86 chips in the errata and has an unofficial RPM update for gcc for this purpose. Newer 6x86MX chips may not suffer these problems. The changelog for one of the new gcc RPMs. mentions on dec 30, 1997: 'changed optimizer flags to -O2 for bootstrap to fix "broken" Cyrix chips.' This change was made by Make Wangsmo ".

I have seen mention of a set6x86 program. Here is the debian linux page for the set5x86utility; that page has links to the original tar file and a diff file which looks like it is probably debian specific.

---

### Post by CyberBob on 2005-09-28
Thank you for your recent posts, Teroedni.  It appears that I misunderstood the m571 manual regarding clock speed jumpers.

The current settings are:

External - JP5  66MHz
Internal - JP7   1.5x/3.5x

... and I found that this means (duh!) 3.5 x 66 MHz = 231 MHz

So, if I change the JP7 multiplier to 2.0x my (under)clock speed will be 132 MHz.  I will do this later today and retry the Hoarty install.

---

### Post by CyberBob on 2005-09-28
********************** S U C C E S S ************************
                         :smile: :smile: :smile: :smile: :smile: :smile: :smile: :smile: 

Teroedni, you nailed the problem down for me - THANK YOU VERY MUCH!!

After changing the JP7 multiplier to 2.0x my (under)clock speed is now 132 MHz and Hoary Hedgehog installs without incident!  The Cyrix MII 300 chip was the culprit all along.  I must also acknowledge an excellent reference for the M571 motherboard, Timmy's page, at:

 [http://m571.com/m571/](http://m571.com/m571/)

There is a wealth of information there for anyone who has this motherboard.  Given that I had to underclock this Cyrix cpu, I decided to order a new processor, the K6 2 500 as recommended on Timmy's page.  I found it available online for less than $20 USD.  This will make this old PC run at an acceptable speed.


Thanks to all that helped me in this thread:  Herman, azz, and especially Teroedni.


"There is no chance, no destiny, no fate, 
Can circumvent or hinder or control 
The firm resolve of a determined soul. "   Ella Wheeler Wilcox

---

### Post by Teroedni on 2005-09-29
Blushing:smile: 

Thanks

---

