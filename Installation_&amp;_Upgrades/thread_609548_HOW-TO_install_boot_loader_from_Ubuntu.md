---
title: "HOW-TO install boot loader from Ubuntu"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by roastgarlic on 2007-11-11
In SUSE (YAST) there is a utility "Boot loader" that installs (menu.lst ?) to the hard drive's boot sector.

Does UBUNTU have such a utility ? If so, what is it ?

(... and, maybe more to the point, if it is there why is it so difficult to find ? where is its documentation ?

---

### Post by Herman on 2007-11-11
I normally use a GRUB shell to install GRUB's IPL somewhere.

To open a GRUB shell you just open a terminal and type 'sudo grub'
```
sudo grub
```You will notice that you'll have a grub>_ prompt.
```
grub>_
``` Your GRUB shell will have a prompt like the one shown above, for the rest of this post I won't show the prompt, only the commands to be typed after it.

Then you use a test to see where the main part of GRUB is located, because you will need to know for your next command. 'find /boot/grub/stage1', or 'find /boot/grub/menu.lst' or something like that will do.
```
find /boot/grub/stage1
```The feedback from that command (above) should be something like (hd0,1) or (hd1,2) and that will tell you what partitions you have containing GRUB. 
Maybe I have Ubuntu in partition (hd0,1) and SuSe in (hd1,2), I can choose whichever one I like to install to MBR.
You need that information to type into the next command (below)
```
root (hdx,y)
```Where: x is the hard drive number and y is the partition number of a partition containing GRUB files. 
Like (hd0,1) for first hard drive, second partition, or (hd1,2) for second hard drive, third partition, or whatever it is your answer was for the 'find' command.
[A Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

The you do 'setup (some device)'. Your device could be a partition or a hard drive or a USB flash memory stick or anything like that.
```
setup (hd
```'setup (hd0)' will install GRUB to MBR in your first hard disk.
'setup (hd0,0)' will install GRUB to the first sector of your first partition.

**But wait a minute, don't complete the whole command yet....**
A useful trick is to just type 'setup (hd' ...and then press your TAB key. Either the line will be automatically completed for you or you will get feedback that says 'Possible disks are: hd0 hd1' or something like that.
Then you just need to pick which device you want from that list and install GRUB to it.

If you're not sure which disk is which and you want to check to make sure you are installing GRUB to the right device, you can use GRUB's geometry command.
Let's say you think it will be (hd0) that you want to install GRUB to but you want to make sure. You expect (hd0) will be your first hard disk and (hd1) to be your USB flash memory stick which happens to be plugged in right now. ```
geometry (hd0)
``` That will return some feedback that will give you some good pretty clues about which disk is which, for example,
```
drive 0x80: C/H/S = 7296/255/63, The number of sectors = 117210240, /dev/sda
Partition num: 0, Filesystem type is fat, partition type 0x6
Partition num: 1, Filesystem type is fat, partition type 0xc
Partition num: 2, Filesystem type is ext2fs, partition type 0x83
Partition num: 3, Filesystem type is fat, partition type 0x6
Partition num: 4, Filesystem type unknown, partition type 0x82
Partition num: 5, Filesystem type is ext2fs, partition type 0x83
Partition num: 6, Filesystem type isext2fs, partition type 0x83

``` Okay, that confirms my guess was correct and (hd0) is in fact my first hard disk where I want to install GRUB to on this occasion.
So I can go ahead with the setup command and press 'Enter'
```
setup (hd0)
``` That command will install GRUB to MBR in my first hard disk. There will be some feedback to show me what happened, it will probably say something like this,
> [FONT=Bitstream Vera Sans Mono]Checking if "/boot/grub/stage1" exists... yes[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                 Checking if "/boot/grub/stage2" exists... yes[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                 Checking if "/boot/grub/e2fs_stage1_5" exists... yes[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                succeeded[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                2 /boot/grub/menu.lst"... succeeded[/FONT]
                                               [FONT=Bitstream Vera Sans Mono]                                Done.[/FONT]
```
quit
```Finally, to exit the GRUB shell you just type 'quit'.

Here is a link to explain the same thing again in case you need it, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

...or you could use a [Super Grub Disk]("http://supergrub.forjamari.linex.org/")  if you prefer.

Regards, Herman :)

---

### Post by NavyRSt on 2007-11-11
Herman,
You seem to know what you are talking about when it comes to the MBR and booting. I've been having an issue with booting any kind of ubuntu (and even DSL) with the computer. I've gotten superGrub to work a couple of times (although the last two times I couldn't hardly see the text on the screen) and it had worked as a bootdisk and then didn't work anymore. I've used GAG, but gotten nowhere with it and now it says something to the effect of, "No boot sector" whenever I select a section to boot from on a fresh install.

I've installed grub to the MBR (the find; root; setup dance) tons of times, but it hasn't made a difference. 

Do you have a suggestion for my predicament? Maybe there is a way to clear the MBR's?

Thanks,
Brett

---

### Post by Herman on 2007-11-11
Hello NavyRSt,
I think I would be checking over my hardware by the sounds of things.
What kind of computer do you have and how old is it?

Check out my [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm") and go into your BIOS (yours will likely be different from mine, I know, but I made that page as an example anyway, it's the best I can do), and give me your BIOS's [Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information")  please.
Is your hard disk being properly detected and set up in your BIOS?

Also, tell me all about this computer, what kind of (and how many) hard disk(s) do you have, how many GB?

Also, can you please post the output from 'sudo fdisk -lu'?
```
sudo fdisk -lu
``` Thanks.

Regards, Herman :)

---

### Post by NavyRSt on 2007-11-11
For the computer specifics, I'll go into the bios and check it out after I post this....

The hard drives: 3 total
-hda 16 gig IDE
-hdc 25 gig IDE
-sda 17 gig SCSI

The hard drives are being detected on auto by the BIOS upon bootup after the memtest.

This is the "sudo fdisk -lu" output

> Disk /dev/hda: 17.2 GB, 17280442368 bytes
255 heads, 63 sectors/track, 2100 cylinders, total 33750864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6629aafe

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    32242454    16121196   83  Linux
/dev/hda2        32242455    33736499      747022+   5  Extended
/dev/hda5        32242518    33736499      746991   82  Linux swap / Solaris

Disk /dev/hdc: 27.2 GB, 27226644480 bytes
255 heads, 63 sectors/track, 3310 cylinders, total 53177040 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00014182

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63    53175149    26587543+  83  Linux

Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders, total 35843670 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000869aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    35841014    17920476   82  Linux swap / Solaris

I was messing around with the HDD's and what not yesterday and today. I had tried to install DSL on hdc, but didn't get any better response than with ubuntu software. So, thats why it may look funky. If there is something that may need cleaned up tell me and I'll try to do what I can with partition editor.

Thanks,
Brett

---

### Post by NavyRSt on 2007-11-11
OK, this is what I gather from the BIOS:

There isn't a "product information" page in the bios for this motherboard.

From the startup I gather that it's a Tyan S1854 trinity 400 with a rev 1.07 (BIOS??)

I'm not totally sure how much RAM I have now, but on the BIOS  it says:
Base=640k
extended=523246k
other=384k
total= 524288k

I thought I saw DSL say that I have 256k
But, I'm not 100%

Graphics: 32Mb nvidia GeForce MX VGA card

I went through the BIOS and tried to set the hard drives so that it's not on auto anymore.

But, when I restarted there was a secondary slave failure text (it's the CD/DVD drive that I use to run the live CD) and there wasn't anything that said anything about the hard drives like it normally does. So, I just set them all back on auto again.

---

### Post by Herman on 2007-11-12
Hello NavyRSt,
Thanks for all the info, I'll google for details about your hardware as soon as I can.

Meanwhile the thing that interests me right away is the fact that you have three hard drives, two IDE and one SCSI.
That sometimes seems to cause some confusion between which hard drive your BIOS thinks is number 1, and which hard drive GRUB thinks is number 1 hard drive.

It looks to me from looking at your fdisk output that your hda 16 gig IDE should be your first hard drive.
It is quite possible that for some reason GRUB is being installed to MBR in your third hard drive, sda 17 gig SCSI by mistake.

If you have a computer that can bring up a boot device selection menu by pressing your F8 or F12 key during boot-up where you can choose to boot your second or third hard disk, you could try that and see if you can boot from one of the other hard disk's MBRs.
Or maybe you can try changing your hard drive boot order around in your BIOS and see if that helps at all.

Another thing to check is whether there is a MBR write protection feature or boot sector antivirus turned on in your BIOS. You would need to go into your BIOS and turn anything like that off to install GRUB to MBR. 

I think having your BIOS set to 'auto' for you hard disk is correct.

Thanks again for that info I'll look into all that and see what I can find out.

Regards, Herman :)

---

### Post by NavyRSt on 2007-11-12
> **Herman said:**
> Hello NavyRSt,
Thanks for all the info, I'll google for details about your hardware as soon as I can.

Meanwhile the thing that interests me right away is the fact that you have three hard drives, two IDE and one SCSI.
That sometimes seems to cause some confusion between which hard drive your BIOS thinks is number 1, and which hard drive GRUB thinks is number 1 hard drive.

It looks to me from looking at your fdisk output that your hda 16 gig IDE should be your first hard drive.
It is quite possible that for some reason GRUB is being installed to MBR in your third hard drive, sda 17 gig SCSI by mistake.

If you have a computer that can bring up a boot device selection menu by pressing your F8 or F12 key during boot-up where you can choose to boot your second or third hard disk, you could try that and see if you can boot from one of the other hard disk's MBRs.
Or maybe you can try changing your hard drive boot order around in your BIOS and see if that helps at all.

Another thing to check is whether there is a MBR write protection feature or boot sector antivirus turned on in your BIOS. You would need to go into your BIOS and turn anything like that off to install GRUB to MBR. 

I think having your BIOS set to 'auto' for you hard disk is correct.

Thanks again for that info I'll look into all that and see what I can find out.

Regards, Herman :)

HERMAN I COULD KISS YOU!!!

It was the SCSI/IDE/first disk thing!

I don't know how that got past me so many times!

Thank you so much!

Brett

PS: If I ever come back to Australia (I'm an American sailor), I'm tracking you down and buying you way too many beers!

---

### Post by Herman on 2007-11-13
Hello NavyRSt, 
Nice motherboard,  [trinity400]("http://www.google.com.au/search?hl=en&q=Tyan+S1854+trinity+400&btnG=Google+Search&meta="). 
It looks like you already have the latest BIOS update for it too, with a rev 1.07 BIOS. 

I'm glad I was able to help you. :)
Did you end up switching the hard disk boot priority around in your BIOS? 
Or do you need to use the F8 or F12 key every time you boot?
Or did you do something else like install GRUB to the MBR that the BIOS thinks is number1 and configure GRUB from there?
I'm interested in learning what's the best or what's the easiest for people so I can decide how to help other people with similar problems better in the future.  :)

Thanks for the positive feedback. :)

I also googled Portsmount VA, [**Portsmouth**, **Virginia** - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FPortsmouth%2C_Virginia&ei=THs5R5j6D5qmpwT_pbi5DA&usg=AFQjCNF1bOCQsKT9IXrZz8O8OFp8wCOeWg&sig2=grhD8UEw_klmFGKsk43whw") It looks like a fascinating place! 

All the best, and bye for now,
Regards, Herman :)

---

### Post by NavyRSt on 2007-11-13
> **Herman said:**
> Hello NavyRSt, 
Nice motherboard,  [trinity400]("http://www.google.com.au/search?hl=en&q=Tyan+S1854+trinity+400&btnG=Google+Search&meta="). 
It looks like you already have the latest BIOS update for it too, with a rev 1.07 BIOS. 
Thanks, I got really lucky with this box. I was sure, that it was going to be nothing but troubles. But, the guy that gave it up is an IT guy by profession (he just didn't want to mess with the dinosaur when he had so many shiny new computers to mess with at home). He lived in the Washington DC area, which is the IT capital of the east coast. So, with this being a PC store "special" back then, they didn't mess around.

> I'm glad I was able to help you. :)
Did you end up switching the hard disk boot priority around in your BIOS? 
Or do you need to use the F8 or F12 key every time you boot?
Or did you do something else like install GRUB to the MBR that the BIOS thinks is number1 and configure GRUB from there?
I'm interested in learning what's the best or what's the easiest for people so I can decide how to help other people with similar problems better in the future.  :)

Thanks for the positive feedback. :)
I just changed the BIOS settings to boot off of a different set of hard drives. Unfortunately, the BIOS isn't as customizable as yours and has a set three that it cycles through. I just messed with it till it ran. That was easiest for me, but I'm sure there is a better or more correct way of fixing what I had wrong.:lolflag: I'm not computer ignorant, by any means, but I'm more adept behind the wheel of my Subaru or wrenching on something than trying to troubleshoot computers!
I haven't tried the F8/12 key yet, and I keep meaning to, I just forget.

> I also googled Portsmouth VA, [**Portsmouth**, **Virginia** - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FPortsmouth%2C_Virginia&ei=THs5R5j6D5qmpwT_pbi5DA&usg=AFQjCNF1bOCQsKT9IXrZz8O8OFp8wCOeWg&sig2=grhD8UEw_klmFGKsk43whw") It looks like a fascinating place! 

All the best, and bye for now,
Regards, Herman :)

I've never wiki'd Portsmouth, but a lot of that info is really good. There is a TON of history steeped in this entire region. The wiki page talks about the Hampton Roads, and the Seven Cities (I don't think it said anything about tidewater or peninsula, but that is another way of "naming" the area those of the south and north sides, respectively,  of the James river) which in a whole was a VERY large stepping stone of colonizing the US. The state of Virginia is a "southern" state (dictated by the US civil war), and I'm a Northerner through and through. I don't HATE this area, but if I had a choice, I would live somewhere else in the country. The area is cool if you are visiting, studying, vacationing, etc. but, it's not my plan to live here till I'm old and grey. Another thing the wiki only shines on, with the is the Navy in this region. There is the US Navy's LARGEST base in Norfolk (only a tunnel away, and where I primarily work), but that's not enough. There is a Navy Air Station, an Amphibious base, a weapon's station, and a SEAL/SEABEE (construction guys)/training facility in this area alone, and that's just the Navy! There are also Army, Air Force, Coast Guard, and NASA facilities in this area! There are also, at least, 5 other commercial Ship Yards/Builders here. But, there really isn't any metro area to speak of, it's kind of the way that Virginia does it's counties (townships, manors, parishes, what ever you call them).

Boy was that a rabbit trail from hell! I guess I'll end the thread hi-jack here.

Brett
<<hoping he doesn't get yelled at for jacking the thread too bad!

---

### Post by Herman on 2007-11-17
:) Hello NavyRSt, 
> I just changed the BIOS settings to boot off of a different set of hard drives. Unfortunately, the BIOS isn't as customizable as yours and has a set three that it cycles through. I just messed with it till it ran. That was easiest for me, but I'm sure there is a better or more correct way of fixing what I had wrong.:lolflag: I'm not computer ignorant, by any means, but I'm more adept behind the wheel of my Subaru or wrenching on something than trying to troubleshoot computers! To the contrary, that is the way I now think is the best way to deal with that type of problem. Thanks for your helpful reply, I will be advising more people to try doing it that way if they can.

The other ways to do it are both harder. 

One way I used to advise people was to ask them to boot and get [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and re-install GRUB to their first hard disk, (hd0) from there and boot. They would probably need [Super Grub Disk]("http://supergrub.forjamari.linex.org/")  to do that, or they could use F8 or F12 keys for a BIOS bootable disk menu.

Another way to do it is by [**Editing GRUB's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map") file and re-installing GRUB, 

If you look in that last link you'll see that I have added a link in there back to this thread as an example of the best way to solve the problem. :)
I hope that's okay with you, by the way. Let me know if you object and I can remove it. 


I'm originally from Nova Scotia, Canada, just up the shore from you a few hundred miles. I spent seven years at sea myself, working on all kinds of different small vessels. I'm landlocked now though, it's dry and dusty where I am now. I'm in [**Hughenden** in Outback QLD]("http://www.google.com.au/url?sa=L&ai=BhDzNRnk-R4fkGKeqpATO4KGsBoiI9S7o57mdA5zOqqsLgPEECAAQAhgCKAI4AFCcgvWk-v____8BYKWglYCYAcgBAakC5yqijbjMrT7IAvyX_QLZA1QHDMrpcRKC&q=http://www.hughenden.com&usg=AFQjCNF8TMxQzJHVyqgAK430op8qN3ZhGA"). Population 2000 and a few dogs, horses, camels and sheep, miles from anywhere. :)
How I got here is a long story.
If you clicked on the link you'll realize why I have a windmill in my avatar. We have lots of windmills here and it's also a place where there are lots of old fossils, especially dinosaur fossils, so dinosaurs are an icon of this area too.

Thanks for your kind and helpful feedback, you have helped me as much as I've helped you. I'm interested in finding the easiest way to cope the the kind of problem you had. :)

Bye for now, Regards, Herman :)

---

### Post by sandysandy on 2007-11-17
hi

i am facing problem in dual booting Win XP and Ubuntu 7.10. Been tying out various methods, but have only got varying success.

system specs Pentium D 3.0 GHz, 1GB RAM, 160Hdd SATA hdd ( WinXP - 2 partitions), 40Gb IDE Hdd (Ubuntu 7.10 & Mandriva). Booting sequence is 40GB hdd first.

Here's a link to my thread in this forum

[http://ubuntuforums.org/showthread.php?t=596704&page=5](http://ubuntuforums.org/showthread.php?t=596704&page=5)

thanx

---

### Post by Herman on 2007-11-17
:) Hello sandysandy

[Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information") What is your motherboard, and/or what is your BIOS version and  all that kind of stuff? Can you post something like that so I can google it for you and try to find out a little more about your hardware? :)

While you are in your BIOS settings already anyway, please take a look around and see if you need to [Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect").
         

Also, if you can shine a light around inside your computer case, (being careful not to touch anything in there), what color are the plugs on the ends of your IDE cable and is it a 40 conductor cable or an 80 conductor ribbon cable?

If you can see at all, what position is the jumper setting in? ('M' ,Master, 'S', Slave or 'CS', Cable Select?
How about your CD/DVD ROM drive, does the have a jumper setting too? What position is that one set to?
If you can't see what the jumper settings are we can leave that for the time being, don't try too hard, just if it's easy to see.

That's all for now,
Regards, Herman :)

---

### Post by sandysandy on 2007-11-18
> **Herman said:**
> :) Hello sandysandy

[Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information") What is your motherboard, and/or what is your BIOS version and  all that kind of stuff? Can you post something like that so I can google it for you and try to find out a little more about your hardware? :)

While you are in your BIOS settings already anyway, please take a look around and see if you need to [Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect").
         

Also, if you can shine a light around inside your computer case, (being careful not to touch anything in there), what color are the plugs on the ends of your IDE cable and is it a 40 conductor cable or an 80 conductor ribbon cable?

If you can see at all, what position is the jumper setting in? ('M' ,Master, 'S', Slave or 'CS', Cable Select?
How about your CD/DVD ROM drive, does the have a jumper setting too? What position is that one set to?
If you can't see what the jumper settings are we can leave that for the time being, don't try too hard, just if it's easy to see.

That's all for now,
Regards, Herman :)

hi

the motherboard is FC Gigabyte FSB 1066 GA 945 GC MX S2
THE IDE Cable is 40 connectors and the cable color is white while the cable connectors are black.

how does one turn off anti virus/ write protect. i did not get the options in BIOS as illustrated in ur website for the product information and anti virus feature.

today i disconnected the 40gb ide hdd and then installed Open SUSE 10.3 on the 160 GB SATA drive. The GRUB is giving both options - Win XP and Open SUSE and i am able to boot them.
Earlier i had the same luck with Mandriva also. Its only with ubuntu that i am facing problem. i am looking forward to ubuntu on my desktop.

thanks

---

### Post by Herman on 2007-11-18
>  the motherboard is FC Gigabyte FSB 1066 GA 945 GC MX S2Thanks, I'll google that as soon as I can.
>  THE IDE Cable is 40 connectors and the cable color is white while the cable connectors are black. How many **wires** does it have? If it only has 40 wires throw it away and go buy yourself an 80 conductor IDE cable. They only cost a dollar or so, last time I was in a computer store they gave me a handful of them for free. 40 conductor IDE cables are obsolete and shouid be replaced with 80 conductor IDE cables.
> how does one turn off anti virus/ write protect. i did not get the options in BIOS as illustrated in ur website for the product information and anti virus feature. Okay, possibly your BIOS doesn't have that (MBR antivirus) feature, only a few BIOSes have that, but it can cause problems when trying to install GRUB to MBR. Just something to check, that's all. Thanks. for checking.
>  today i disconnected the 40gb ide hdd and then installed Open SUSE 10.3 on the 160 GB SATA drive. The GRUB is giving both options - Win XP and Open SUSE and i am able to boot them.
Earlier i had the same luck with Mandriva also. Its only with ubuntu that i am facing problem. i am looking forward to ubuntu on my desktop.Yeah, but disconnecting the hard drive that seems to be causing the problems is cheating! That's not a valid comparison. :lolflag:

Okay, it seems to me as if your problem has to do with the 40 GB IDE drive and how it's plugged in and jumpered.

Please take a **good look** at your hard drive jumpers and also the jumper setting on any other IDE devices you might have, like your CD/DVD drive.

If you have an 80 conductor IDE cable with black plugs, the hard drive and DC/DVD drive jumpers should be set in the Master and Slave position.

I'm not certain if all motherboards support cable select, check at your computer store whether you can upgrade or not. If you go buy a new cable and it has a blue plug, a black plug and a grey plug, you need your jumpers both/all set to Cable Select.
The blue plug goes to you motherboard, the black one to Master, and the grey to Slave drive.
All cable select IDE cables are 80 conductor cables.


 You should probably take your computer back to who-ever installed your hard drives and get them to check that for you, unless you know how to do that yourself. Stickers on top of the drives will tell you what the jumper settings should be for each particular drive.
 
Regards, Herman  :).

---

### Post by sandysandy on 2007-11-18
thanx.

i will check out the 80 conductor IDE cables.

regards

---

### Post by Herman on 2007-11-19
(post deleted, this post was the same as the one below, double post for some reason, sorry, my bad.)

---

### Post by Herman on 2007-11-19
Okay, does this look like your motherboard's web support main page?
[http://www.giga-byte.com/Support/Motherboard/BIOS_Model.aspx?ProductID=2521](http://www.giga-byte.com/Support/Motherboard/BIOS_Model.aspx?ProductID=2521)

Nice hardware! :)

I downloaded the motherboard manual for your motherboard from [here]("http://www.giga-byte.com/Support/Motherboard/Manual_DownloadFile.aspx?FileType=Manual&FileID=17917").  I have read the manual. I don't see any obvious problem there. Your motherboard has an Award Modular BIOS which is quite a popular and well known BIOS. 

I think the 80 conductor IDE cable will be an improvement, the rest of  your hardware is too good for an old 40 conductor IDE cable. Your motherboard has four SATA ports and only one IDE port. The IDE cable was probably just provided for a CD/DVD drive. Your motherboarsd manual does stress the importance of using the approriate jumper settings if you install an IDE hard drive. The hard drive and CD/DVD drive jumper settings are more important than the type of cable as far as booting goes though.

Now I need some time to read through your whole other thread and think about the problem some more and come up with some test that you haven't already tried and see if I can help you solve the problem. (If replacing the IDE cable with a better one doesn't fix it). You already have some excellent expert help in that other thread.  Please check your CMOS settings are okay according to the manual and your hard disks, especailly the IDE one are properly set up and detected in your BIOS. 
Thanks for your patience.

Regards, Herman :)

---

### Post by meierfra on 2007-11-19
Herman: There is more than just one other thread. You might want to look at all of them. I have read them all, but this case is outside of my area of expertise. Also it is very confusing, since sandysandy has been installing and deleting OS's various times.

---

### Post by meierfra on 2007-11-19
Just a few things which I think haven' t been investigated enough:

> after installing 7.04 and trying to boot from hdd the following message comes

booting from local disk
Isolinux: Disk error 01, AX=0201, drive 80
Boot failed: press a key to restart.


> i typed: map (hd0) (hd1)
map (hd1) (hd0)
live swap
it showed file system type is iso9660, using whole disk.



> 
i disconnected the 160GB drive and reinstalled Ubuntu 7.04 on the 40 GB drive.
the booting priority was set to the 40 GB HDD.
while booting the message came" Disk boot failure reinsert system disk and press enter"

Will try and reinstall GRUB. maybe it will help


---

### Post by Herman on 2007-11-20
Thanks for the tip, meierfra, I have now investigated and I see what you mean, I have scanned through some of them now. Thanks. 

Notably, in this thread, **[[B]mbr**]("http://ubuntuforums.org/showthread.php?t=574597"),[/B]
>  i must be the 100 th guy who's messed up his mbr. but with this forum i am sure some one will help me out.

specs of my machine Pentium D 3 ghz. 1 GB Ram, 2 HDD
first hdd 40gb - ubuntu 7.04
second hdd 160 gb - win xp (installed first) & Ubuntu 7.04

i can boot from live CD, but cannot boot from hard disk as the following message comes
[COLOR=Red]Isolinux: Disk error 01, AX=0201, drive 80[/COLOR]
  az thinks it could be a buggy BIOS.
I respect az's opinion. He is not often too far wrong.

[ISOLINUX]("http://syslinux.zytor.com/iso.php"), is a boot loader used for booting in [CD-ROM]("http://en.wikipedia.org/wiki/CD-ROM") [ISO 9660]("http://en.wikipedia.org/wiki/ISO_9660") filesystems.

So it appears as if sandysandy's BIOS is trying to boot the CD-ROM drive instead of the 40.0 GB IDE hard drive.

The quotes you posted in you post right above this one suggest the same thing, meierfra. It seems to me as if sandysandy's BIOS is getting confused between which is the IDE CD-ROM drive and which is the IDE 40.0 GB hard disk drive, whenever the 40.0 GB hard disk drive is plugged in.

If there is no bootable CD in the CD-ROM drive, the BIOS skips it and falls back to booting the next device in the boot order, which is the SATA, resulting in Windows booting every time instead of GRUB.
If there is a bootable CD-ROM in the CD/DVD drive, it attempts to boot the CD-ROM, but fails with the error message quoted above.
Does that sound like a plausible theory?

So it could be a buggy BIOS, a damaged or wrongly plugged in IDE cable, wrong jumper settings, or, (but I doubt it), there could be something unusual about the hard disk drive that means GRUB or Ubuntu don't seem to be able to work in it.

We're already getting a better IDE cable. If that doesn't fix sandysandy's problem then the next steps and possible solutions depend on what resources sandysandy has available and is willing to put into this computer.

Checking the jumper settings (again) would cost nothing and only take a short time.

Installing Mandriva or some other Linux in the IDE disk and see if any other operating system can boot in it would be interesting.

Also, it might be interesting to see if unplugging the CD/DVD drive as well as the SATA might help the IDE drive to boot.

If another computer is available that has another IDE hard drive, a simple test would be to try the other computer's hard drive and see if that hard drive will work. 
And try the 40.0 GB hard drive in the other computer and see if it boots okay in the other machine.

An idea, even if the computer has a buggy BIOS or something is different about the hard drive making booting impossible, would be to install Ubuntu in the SATA disk, and use the 40.0 GB IDE for data storage.
Or, buy another SATA drive, and only install operating systems on SATA disks in this machine, and use the 40.0 GB IDE drive for data.
This motherboard has connectors for four SATA drives, with a data transfer rate of up to 300MB/s.
For the IDE interface I think it would be possible to get 133MB/s data transfer with the 80 conductor cable, but the 40 conductor cable would have limited that to around 40 MB/s I think.  (If the stuff I'm reading is correct). 
Also, reading and writing between the IDE disk and the CD/DVD drive will be slow when those are both on the same IDE ribbon cable. 
Therefore, even if we succeed in getting Ubuntu booting and working in the 40.0 GB IDE, it's performance might not be as good as it could have been if it was installed in a SATA disk. So it would be nice to see Ubuntu being installed on another SATA disk, that would be a lot better for an operating system. The IDE disk is better used for data. That, again, depends on how much money sandysandy feels like spending on this machine. Normally I try not to advise users to buy anything.  I prefer to help them use the hardware they already happen to have.

We must now wait until we hear from sandysandy again.

Regards, Herman :)

---

### Post by sandysandy on 2007-11-22
hi

thanx.

i reformatted the 40 gb ide hdd and reinstalled 7.10 after i disconnected the SATA drive.

the installation went ok.

however i am unable to boot as usual.

i tried SGD also, but the disk partitions are not visible as before.

will try and change the cable soon.

the output of sudo fdisk -lu is as follows:-

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009a393

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris


regards

---

### Post by Herman on 2007-11-22
:) Hello sandysandy,

Do you understand what I mean by 'jumper settings' to set the IDE hard drive up as 'Master', 'Slave' or 'Cable Select'?  :)
Have you found those on your IDE hard disk and on your CD/DVD drive yet and checked that they are set correctly?  :)

Here are two links with pictures about how to install IDE hard drives, 

**[Guide to Installing [B]IDE** devices]("http://www.google.com.au/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Ffreepctech.com%2Fpc%2F001%2Finstalling_ide_devices.shtml&ei=6s9FR7a9FqGqpwTkl5CtCw&usg=AFQjCNEC3FxARIc8jprrBAmPdXmFdrEVcg&sig2=hfESBtRoYSJmJIVQZ3w5gA")[/B]

**[Install [B]Hard Drive** - A guide to installing a **hard drive** (IDE)]("http://www.google.com.au/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.helpwithpcs.com%2Fupgrading%2Finstall-hard-drive.htm&ei=B8xFR_rsC5aspwSk65S2Cw&usg=AFQjCNEHQ3cBi4bXL4JmnICE5Vo1jiyZNQ&sig2=w1MQAiRGkZ9UQk5BLMMw9A")[/B]

The CD/DVD drive was probably set as master IDE drive, and you should set the jumper for it to 'Slave' position when you install a hard drive on another plug on the same IDE cable. 
Then you can set the jumper for the 40.0 GB hard drive in the 'Master' position. 
Either that or leave the CD/DVD drive set as Master, and set the IDE hard drive as 'Slave'.

I need you to confirm that you have understood what I mean by 'IDE jumpers settings' and have set your IDE drive jumpers correctly before we can go any further. :)

Regards, Herman :)

---

### Post by sandysandy on 2007-11-22
hi herman


thanks for the tutorial links.

i had changed the jumper setting of the 40gb IDE hdd to Cable Select, while leaving the DVD drive untouched prior to reinstalling Edubuntu 7.10.

will check the DVD drive jumper settings also and change the configuration of one as master and the other to slave (DVD Drive & HDD). 

regards

---

### Post by Herman on 2007-11-23
Hello sandysandy,
:) Yes, that's good! The best thing to do would be to set the 40.0 GB iDE hard drive to 'Master' and the CD/DVD drive to 'Slave'.
I expect that will fix your problem with your BIOS.

Then you will just need to re-install GRUB to  (hd0) again, like I already explained in post #2, back in page 1 of this thread. 
This time your BIOS will recognize your 40.0 GB IDE hard drive as (hd0) instead of the CD/DVD drive, and you should be able to dual boot with GRUB from now on. :)

Regards, Herman :)

---

### Post by sandysandy on 2007-11-25
> **Herman said:**
> Hello sandysandy,
:) Yes, that's good! The best thing to do would be to set the 40.0 GB iDE hard drive to 'Master' and the CD/DVD drive to 'Slave'.
I expect that will fix your problem with your BIOS.

Then you will just need to re-install GRUB to  (hd0) again, like I already explained in post #2, back in page 1 of this thread. 
This time your BIOS will recognize your 40.0 GB IDE hard drive as (hd0) instead of the CD/DVD drive, and you should be able to dual boot with GRUB from now on. :)

Regards, Herman :)

hi Herman

in the meantime i disconnected the 40gb ide hdd and successfully installed Edubuntu 7.10 from alternate CD on the 160gb hdd. Now i have triple boot - Win XP, Open SUSE10.3, and Edubuntu7.10 on the SATA drive.

however, i have not given up on the 40gb IDE hdd yet and will follow ur advise on configuring it and DVD ROM in master-slave mode and reinstall ubuntu on it shortly.

thanks and regards

---

### Post by meierfra on 2007-11-26
sandysandy:  You might want to have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=622850]("http://ubuntuforums.org/showthread.php?t=622850")

---

### Post by Brain_of_J on 2008-03-06
I'm currently also trying to dual boot XP and Ubuntu.  But on a laptop.
When in the grub command line I get an 
Error 15: File not found
when trying to run find /boot/grub/...

This is a fresh Ubuntu 7.10 install.

Ideas?

---

### Post by Herman on 2008-03-06
Make sure you open a GRUB shell with superusers priveleges, by using 'sudo'. 
Type 'sudo grub', not just 'grub'.
```
sudo grub
``````
find /boot/grub/stage2
```If you just type 'grub' to open a GRUB shell, you will get a GRUB shell but it will only work for some commands and you'll see error messages.
 Regards, Herman :)

---

