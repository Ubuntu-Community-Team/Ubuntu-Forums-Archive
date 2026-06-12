---
title: "Upgrade to 12.04 gives many errors and Windows affected too"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by murphyac on 2012-05-20
Background: Dell Dimension 4700 desktop, Pentium 4, 2.8 GHz, 2 Gb RAM, 2 SATA disks: 80 Gb and 320 GB - Windows XP SP3 on 80Gb, Ubuntu on 320 Gb disk - 11.10 upgraded to 12.04 last Sunday, dual boot.

I hope someone can help with this.  After the upgrade to 12.04, I started getting "system error" messages, at first sporadically, now constantly.  Some programs, like Thunderbird and Firefox started crashing.  Until last night, I was able to recover by logging out and restarting, but last night, when I was reading some web email, Firefox crashed and kept crashing.  Ubuntu kept sending in reports and reports on the system errors, until finally, it said the report mechanism was broken.  Then it would let me log in, but not start any applications.
  I tried to go to Windows, but I got a blue screen.  It booted on the second try, but every browser I tried - Firefox, Chrome, Internet Exploder - crashed.  I tried rebooting again, blue screen: IRQL_NOT LESS_OR_EQUAL and when I tried again, blue screen: PAGE_FAULT_IN_NONPAGER_AREA.  When it let me boot, I could not get into any programs.
   I don't know what is going on, if it is hardware or software, if the Ubuntu and Windows problems are related, if my MBR is corrupted or what.
   I have an Acronis backup of Windows and a Clonezilla backup of Ubuntu.  Should I try to restore the system to what it was before the upgrade?  I used my laptop to download the iso of 12.04 and burned it to a CD - should I try to reinstall?
I am confused and upset.  This never happened with the other upgrades: 10.04 to 10.10 to 11.04 to 11.10.  I would be eternally grateful for any advice and help anyone can give me.  If it involves using the terminal, advice would need to be very detailed.  I'm not good at using it.  Thanks for reading this long screed.
Angela C. Murphy

---

### Post by jadtech on 2012-05-20
im no expert  how ever this is looking like something to do with CPU or mother board going blue screen on windows  page faults are rarely  good news ..

could try to open it up  clean everything inside up remove fans give them a good clean up check all the connections dont think this is software related   been wrong before I mean it could be the hard drive  just dont believe it is  ..

if it was me I would try to boot to recovery do a memory test make sure  you havent got  some ram going bad , since the problem is on both ubuntu and window  good bet this is hardware related

---

### Post by wilee-nilee on 2012-05-20
The windows bluescreen should have errors post them if so. Uaually windows errors are something like 0.00000004746, an estimation here.

Boot the live cd of 12.04 and see if the problems are there as well. You can run a memory test from the live cd I would let it run over night. I would run a HD check from the disk utility as well using smart data on the live cd.

That many upgrades with ubuntu I would not trust myself, or at least expect problems.

Might be hardware, but I would bet on software myself.

Windows needs chkdsks run every so often to be running well, as well.

---

### Post by BenginM on 2012-05-21
Salutation.

as the fellow Ubuntites suggested the memest check if the ram is healhy .. I'd also run a file system check.

---

### Post by murphyac on 2012-05-21
To answer post #2 - I ran 2 passes of memtest+ from the GRUB menu, passed twice.  I will run it overnight from the CD.
The windows codes:
for IRQL_NOT_LESS_OR_EQUAL : 0x0000000A
for PAGE_FAULT_IN_NONPAGED_AREA : 0x00000050
for the one when I tried to print my Dell owner's manual : 0x0000008E

Now, unless it is some obscure hardware problem, I am going to bet it's software.  I am writing this message from the same computer, same hard disk that has Ubuntu, but not from Ubuntu, but Xandros Linux 4.5, which I was going to erase and now am glad I didn't.  Xandros is an older type of Debian-based Linux and is no longer supported, which is why I switched to Ubuntu.  It uses GRUB 1, which is why I was able to put it in the GRUB menu. (The older Xandros 3 used LILO, and I no longer boot from it).  I did hard drive checks from the Dell pre-boot setup menu - both listed as OK.  I got desperate and tried to boot Xandros 4.5 - booted perfectly.  All its programs are old (Firefox 2!), but it does show that my computer itself is working.  I have network connectivity - I'm posting this, aren't I.  It seems my CPU is OK and my memory is probably OK.  My onboard network connector is working and also my onboard graphics connector, although Xandros uses a lower resolution than Ubuntu.

OK - big question - I followed all the procedures to the best of my ability.  Tried to boot to a lower kernel, one of the 2.6s, got a kernel panic right after the opening screen appeared when I logged in.  Can somebody please give me some explanation of what is going on and how I might repair it?!
Angela C. Murphy

---

### Post by wilee-nilee on 2012-05-21
> **murphyac said:**
> To answer post #2 - I ran 2 passes of memtest+ from the GRUB menu, passed twice.  I will run it overnight from the CD.
The windows codes:
for IRQL_NOT_LESS_OR_EQUAL : 0x0000000A
for PAGE_FAULT_IN_NONPAGED_AREA : 0x00000050
for the one when I tried to print my Dell owner's manual : 0x0000008E
Angela C. Murphy

[http://support.microsoft.com/kb/314063](http://support.microsoft.com/kb/314063)
[http://support.microsoft.com/kb/329293](http://support.microsoft.com/kb/329293)
[http://support.microsoft.com/kb/315335](http://support.microsoft.com/kb/315335)

The MS support in the order you have them listed. This is the best way to find answers using the error numbers in a web search. I searched with just the numbers.

So lets even make this a bit easier so we can be of the best help. Be sure to keep it simple use separate paragraphs for a single problem. Be careful with using one thread to address multiple problems, it can be the thread header that brings the help to start with. 

Mainly a wall of text and no paragraphs make it really hard for many of us to tease out the problems. :)  It is not real bad here but a bunch of text with multiple problems and comments gets really hard to follow.

---

### Post by roelforg on 2012-05-21
This kind of stuff is usually related to bad ram.
My friend's desktop's ram blew (out of the blue) a bad chip and he had those exact errors, one ram-swap later, everything was smooth sailing again (smoother then before because he decided to get that ramupgrade he was putting off as well as he was replacing ram anyways).

---

### Post by wilee-nilee on 2012-05-21
> **roelforg said:**
> This kind of stuff is usually related to bad ram.
My friend's desktop's ram blew (out of the blue) a bad chip and he had those exact errors, one ram-swap later, everything was smooth sailing again (smoother then before because he decided to get that ramupgrade he was putting off as well as he was replacing ram anyways).

There was a memory check.

---

### Post by roelforg on 2012-05-21
> **wilee-nilee said:**
> There was a memory check.

I know, i just wanted to confirm that it's a good idea.

---

### Post by jadtech on 2012-05-21
I am doubting this is a software issue  if both windows and Ubuntu are  being effected on the same computer the only thing they have in common is hardware..

suggestions to discover if this is motherboard, CPU or RAM related be it shorting, heating or just  giving up dust dirt and heat are the enemy not only does the dust and dirt insulate  causing heat build up some dust  is conductive meaning can get between tiny pins and connectors and short things out  reek havoc unseen also dust  carry s static and can be or become magnetic reeking havoc in other ways unseen  .. 

Memory test try several like 10 or 20 if  just one fail  ram some where is bad if you have only one bank of on board ram shift it from one slot to the other see if this helps if the slot is starting to shot or have bad connections from heat dust   or wear if this is no help and one of multiple  test one ram fail time to replace the ram .. 

if ram has no problem try to rule out CPU issues including dirty fan heat sink and bad or lost thermal jell seal, clean the computer completly inside and out if this is a desk top that including clean all the openingand such in the power supply removing the CPU fan and cleaning it inside and out heat sink new thermal jell put the cpu through a stress test of  6 , 8 or 12 hours see if this causes issue  to rule out CPU problems .. processor Ram and  most other computer componts are built and put together in dust free rooms a tiny microeconomic speck of dust  in the CPU  can short  it out turn it in to trash in milliseconds  

 mother board problems and other hardware, pull everything that is plugged in slotted on the mother board you can and have the computer still boot see if the  errors still happen  then start replacing parts one at a time to see if the problem is happening .. 

hard drive problems first is cable and connection are they tight  try new drive cable in pluged in the other onboard slot , if problems still persist try running  loike from live CD or bootble USB  and running from that for a while and see if you get errors if there is no problem you know its possible the hard drive or some connection to it and the mother board  is not good .. 

the bootable  uses all the hardware on your computer but the hard drive  :) 

lastly  though not least if you are finding  you have less problems with less hardware  hooked up  the issue could be power supply related , when everything gets running it is possible it might no longer provide enough to power everything fully ..

---

### Post by wilee-nilee on 2012-05-21
> **jadtech said:**
> I am doubting this is a software issue  if both windows and Ubuntu are  being effected on the same computer the only thing they have in common is hardware..


That is a faulty cause and effect, that would not fly in any scientific inquiry analysis.

Not saying it is not possible, but that is a dichotomy, hardly anything in life is right or wrong, or good or bad. There is always a continuum between two exact points.

---

### Post by murphyac on 2012-05-21
I'm having a hard time figuring out how it could be hardware if Xandros 4.5, which is on the same disk as Ubuntu, just a different partition, boots and works perfectly.  I can also see my Windows files if I log in to Xandros as root. 

Willee-nillee, thanks for the links to Microsoft.  It looks like the Windows problems might be memory related, since Windows puts more demands on the memory than Xandros.

I don't know if this still holds true, but at one point Ubuntu had a problem with Intel onboard graphics chips.  I seem to remember having to get some extra software some time ago.

I will run the memory test overnight from the CD.  2 passing tests are not a big enough database. 

I will also clean the inside of the computer.  If all else fails, I will try to use my backups to get the computer back to the pre-upgrade state.
Angela C. Murphy

---

### Post by murphyac on 2012-05-21
Another thing to consider: the Dell Dimension desktop has a series of 4 LED lights on the back.  These can either be green or yellow and the positions of the green and yellow lights indicate where a failure has occurred.  The lights on the back of my computer are all green, as they have always been.  No yellow lights at all.
Just another point in favor of a software failure rather than a hardware failure.
Angela C. Murphy

---

### Post by murphyac on 2012-05-22
Well, I'm chomping on a bit of crow today.  As suggested by roelforg (post # 7) I seem to have a memory problem.  I ran memtest86+ overnight and woke up to lots of red and about 190,000 errors.  Not good.  Looks like I'll be cleaning and swapping slots (and I might as well clean the whole inside of the computer while I'm at it) and then running memtest86+ again.

If I still get errors, it's time to buy new memory.  It seems that Xandros is working just because it is not as memory-intensive as Ubuntu 12.04 and WindowsXP.  Joy.
Oh well, it's better than nothing.  If new memory solves the issue, I'll come back and mark this thread as solved.

Thanks to all for your suggestions.
Angela C. Murphy

---

### Post by murphyac on 2012-05-27
Did a few more tests, switched positions of DIMMs, still lots of errors.  Then I put the DIMMs in separately.  I had one good DIMM and one bad DIMM.  Since my desktop needs matched pairs, I went out and bought 4, 1GB DIMMS in 2-packs.  Installed them and ran memtest86+ again, and kept running it for 5 passes with no errors.  I'm now doing better, but I still have system errors and update manager, synaptic and software center are not working.  There are also still some problems in Windows, and I'll run chkdsk there.

I will start another thread to ask about trying to re-install 12.04 from the CD, but for now this thread is solved.

Thanks to all who tried to help me.
Angela C. Murphy

---

