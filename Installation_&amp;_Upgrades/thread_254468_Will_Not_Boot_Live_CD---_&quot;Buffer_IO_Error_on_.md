---
title: "Will Not Boot Live CD--- &quot;Buffer I/O Error on device hdc-logical block...&quot;"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by Maya_Iz on 2006-09-10
Whenever I try to boot the live CD, it will return to the black screen with "Uncompressing Linux..." and it will not boot. The errors read "Buffer I/O Error on device hdc- Logical Block...." 

Is this a problem with the CD? I have gone to the "Check Cd for Errors" and I had no errors. Please help!!! I have also tried on several machines and all return the same error. I have also re-downlaoded the ISO file and re-burned using several disks.

---

### Post by confused57 on 2006-09-10
> **Maya_Iz said:**
> Whenever I try to boot the live CD, it will return to the black screen with "Uncompressing Linux..." and it will not boot. The errors read "Buffer I/O Error on device hdc- Logical Block...." 

Is this a problem with the CD? I have gone to the "Check Cd for Errors" and I had no errors. Please help!!! I have also tried on several machines and all return the same error. I have also re-downlaoded the ISO file and re-burned using several disks.

Here's a guide for burning an iso:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

You should do a md5sum of the iso and burn "as an image"(not as data) at a low burn speed(8x or less).

---

### Post by Repus on 2006-09-10
Maya

I have the same problem with one of my systems. The image works well on other machines. However I have one system that generates the same errors that you are getting.

I do not have a solution, im chalking it up to the reader on the supect machine not liking the disc, or its brand, or the writer it came from etc. Should I get it to work I will post a solution.

good luck to you

ps. Having said the above, if anyone else knows what the problem may be I would love to know. I have a perfectly usable cd that simply will not work on one particular machine.

update:
I swapped out the cd drive and the new(er) one works fine. It must have been some combination of my suspicion mentioned above. I hope the same works for you too maya, good luck.

---

### Post by hkgonra on 2006-09-12
I am getting that same error on a Prsario 5000 series ( 1300mhz duron ) and a newer emachines system with an athlon 3000+ , but it works on my OLD celeron 600mhz laptop all with the same cd. ](*,)

---

### Post by danielchase on 2006-09-12
I get the same message (17179701.716000 "buffer i/o error on device hdc, logical block 0"... message repeats through logical block 7).  My machine is an IBM NetVista 6794-FGU w/ 2.0 ghz pIV, 512 ram, CD, 40gig hd, and a Nvidia video card.

Some additional info which may or may not be useful:  
(1) Same disk was used to successfully install Ubuntu on a Toshiba laptop;

(2) Neither Freespire nor Linspire would install either, however they eventually generated different error messages ending in kernal panic

(3) Red Hat 9.0 installs just fine

I am guessing the root of the problem lies with Debian and a piece of hardware, with the Nvidia card being the most likely suspect.  

Very frustrating!

---

### Post by tonyb_uk on 2006-09-14
I had this problem. I have 2 optical drives on my PC. The primary (Boot) drive was the original 8x DVD drive. I changed the primary drive to be my second optical drive (CD read writer) by changing the jump settings on the back ot the drives (usually marked MA (Master) and SL (Slave). Once this was done, this error was not displyaed and Ubunto was installed on my second hard drive without any problems.\\:D/

---

### Post by wpshooter on 2006-09-14
Is the firmware on your CD drives up-to-date ???

---

### Post by d-train3054 on 2006-09-14
I absolutely hate it when someone offers the most oddball piece of advice to solve a problem. Unfortunately, that person is me today!!!

Check to see how many sticks of ram are installed. If there is more  than one (and you are using SD-RAM or DDR) take all but one stick out and try the install. As a Windows pro/developer many cd-rom read issues are related to multiple sticks of ram and/or different brands (go figure).

I had this same problem on two of my P4 3.2Ghz machines on which I was attempting to install Ubuntu (with 2x1GB sticks of DDR ram). Removing one stick of ram seemed to solve it on both. 

Once installed, I was able to reinsert the other stick.

---

### Post by kauf on 2006-09-14
I wonder if that will work for me - the live cd runs fine (but I get those I/O errors when loading it, they don't prevent it from loading - just prolong it).  The installation messes up, I have 512MB of RAM, 2x256mb (dur).  I think 256 is the minimum you need to run the live CD and make sure everything runs... I'll try it later.  Thanks for the oddball advice (though not aimed for me).

---

### Post by Zinoc on 2006-09-15
I got this error fixed by burning knot 3 at 4x.

---

### Post by SweetDragonlady on 2006-10-08
Oh great... all suggestions which I cannot use! How frustrating.:( I only have one cd drive, and only 128 RAM (which happens to be the minimum needed to load the thing so if I take any out it won't even begin to load):-| oof ... now what??? The disk worked perfectly on hubby's computer...](*,)

---

### Post by DoubleDutch on 2006-10-19
Hi all I have the same problem as above. 
Since a few weeks I've been studying like a lawyer on the (K)Ubuntu KDE Debian Gnu history... (pro-contra)
I thought: Great, let's put this on two free-to-use pc's in my bar! (Compaq pc's)
My own assembled PC eats Ubuntu easily! My evo's FSS strangely enough seem to be allergic to ubuntu... (P4 designed for Windows, could this be an issue ?)
The cd readers didn't see the iso at first...
Now, thanks to a bootfloppy as proposed in one of the fora, they do...
Sometimes I get the error message as above or sometimes after another (ctrl+alt+del)Ubuntu starts mounting: essential drivers, root file sys...
Uncompresses Linux...ok, booting the kernel.
and then the prompt blinks and nothing happens...

Or also: sometimes an X blinks in left upper corner. When you strike a key, again: Uncompressing Linux...ok-booting kernel.

Then a message appears: 
Busybox v. 1.01 (Debian1:1.01-4 Ubuntu 3)
Built-in shell(ash)
Enter 'help' for a list of built-in commands
/bin/sh: cant't access tty; job control turned off
#
and still nothing...

Apparently the soft is definitely not compatible to any machine (esp. not Compaq) without changes (as the many communities show...) and alot less, plug and play, although I would love to see it the other way round! I also see that my description contains fragments of other threads. Could it be that experienced programmers (try to) solve small details of a bigger launching issue? So many questions... Anyway gonna check out GNU and Debian now.

Thanks in advance and I'll keep following Ubuntu's growth.

---

### Post by nadamsieee on 2006-10-23
[http://ubuntuforums.org/showthread.php?p=1653927](http://ubuntuforums.org/showthread.php?p=1653927)

---

### Post by Mark Stosberg on 2006-10-23
I ran into this yesterday with a Dell L433C. A solution that worked was to use the alternate install CD instead. (In this case, the 6.06.1 LTS CD). 

Mark

---

### Post by wb114 on 2006-11-04
I was getting a bunch of this error and read this thread.  I swapped out the older LiteOn 52x24x52x CDRW drive that I was using to read the install CD.  Then I used my other LiteOn 52x32x52x CDRW -- it read the CD much faster and no errors.  Weird..

---

### Post by Pricey on 2006-11-05
I had this when loading on an old P3.  I swapped the cd rom drive for another old one and problem solved.
Thanks to all for previous discussion.

---

### Post by bobbybobington on 2006-12-05
I've successfully installed Ubuntu dapper on my old compaq 4550, but I partitioned it incorrectly so I used up my hd and as a result cannot login. So I figured that I could just as easily install xubuntu without a hitch, plus it would be faster. Wrong! I boot, but I get the buffer I/O error on device hdc. along with something about squashfs. The md5 sum for the ISO is fine, and the cd check shows no errors. So im not sure that this is a cd hardware problem. 

So now im just considering reinstalling ubuntu dapper (fixing my  partitioning stupidity), and then install xfce.

Does this sound like a good idea? 

p.s. im downloading the alternate xubuntu right now, so ill see if that makes a difference

---

### Post by xavier_m on 2006-12-17
I had the same problem with disks I burnt, and not only with ubuntu, also with other distributions. I replaced de cd-writer, the hard disk,  a spent maybe 10 hours testing what was going wrong. 

Finally I discovered that in my case the problem was the way I burnt the cds (from xp!),... windows....

To solve it I followed the instructions in [BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") and used InfraRecorder. The most important detail is to choose raw96r as method for burning the iso image (and it isn't explained in the help page). You can also compare the hash with hashtab.

Probably the problem is only the way you burn your cds, too!! (nero shows track-at-once by default...)  grrrrrrr.

Hope it helps, regards,
Xavier

---

### Post by caterminator on 2006-12-20
Yes, I think you're rigth! I had exactly the same problem and it was solved by following the instructions!
Thanks!

---

### Post by okipatrick on 2006-12-22
> **Maya_Iz said:**
> Whenever I try to boot the live CD, it will return to the black screen with "Uncompressing Linux..." and it will not boot. The errors read "Buffer I/O Error on device hdc- Logical Block...." 

Is this a problem with the CD? I have gone to the "Check Cd for Errors" and I had no errors. Please help!!! I have also tried on several machines and all return the same error. I have also re-downlaoded the ISO file and re-burned using several disks.

I battled this very issue for ~3 days with the dapper live CD.  After I had similar install issues with openSUSE 10.2, LinuxXP, and Fedora 6 I decided to download the edgy desktop CD, which installed flawlessly with irqpoll specified in the boot options.

---

### Post by blx_286 on 2007-01-24
I also had the same problem with a Dell Inspiron 7500 laptop that I was installing to. I tried various CDs that were burned at 4x, but received the same error. So I downloaded the Alternate CD again and burned it at 2x.

On the new Alternate 6.06.1 LTS CD, I received the same error and I was given a message box that I could continue the install, but there might be other install problems. I continued and I was then prompted with another message box that stated that some Dell laptops might require "exclude port 0x800-0x8ff". I added this in the message box and the install is running now.

There is more on the subject at [http://www.linuxhowtos.org/PCMCIA/PCMCIA%20Howto.pdf](http://www.linuxhowtos.org/PCMCIA/PCMCIA%20Howto.pdf)

---

### Post by studio56 on 2007-01-26
I was having this problem as well. First I had a CD that would boot the live part fine, but when I would try to install it would always hang at 'copying files 45%' I was afraid I had a bad hard drive, so I tried another CD and it would not even boot. I created a third CD from the same ISO, but set my burner to 4x. It took longer to burn of course, but it fixed the problem. That CD ran the Live part fine, and has since installed Ubuntu on my computer. So before trying any component swapping, try making a new CD burned at a slow speed. Hope this helps.

---

### Post by preciousnightmare on 2007-02-03
I got the same error when I was installing the cd. It had about 20 messages of those.. But it continued installing until it was successful. So I dont really know if thats a good thing or not..:confused:

---

### Post by maykevin5 on 2007-02-08
The problem with all of this lies with the CD-ROM. If you are having problems with the buffer on the cd rom, that meens that the CD-ROM can't read the CD-RW disk that you burned the image on. Its maxing out the buffer and causing a stop error. Change CD-ROM with newer one and your back in buisness.

---

### Post by BillRebey on 2007-02-17
Maykevin5, I think what you mean is CD-ROM *_drive_*  The media IS the ROM.  Leaving the word "drive" out can create confusion.

At any rate, I completely agree with you!  I'm sure there are other problems that might cause this problem, but for me all it took was a trip to Staples and $39 to solve it.  Before resorting to that, I went through all the checksum-checking hoops, re-burned at a slow speed, disassembled the drive and cleaned the laser lens wtih alcohol, etc.  In the end, a new drive with the original CD burnt at 24x worked like a champ.  

I replaced an old 24x CD-ROM drive with a 52x CR-RW drive, so I got twice the speed, write capability, and...well...it WORKED....all for forty bucks.  What a deal!

The installation went flawlessly once the new drive was installed.  

Thanks to everybody on the thread for the insight!

---

### Post by ddreier on 2007-03-01
I'm having the same trouble with Xubuntu 6.10 Live CD, but it eventually boots... It's a OLD Dell Latiude CP M200SD

---

### Post by macuser9214 on 2007-03-11
Run in safe graphics mode.  
-works fine for me.

except now I get the infamous GNOME Daemon error


but gnome starts.

---

### Post by believekevin on 2007-03-20
My students and I just encountered this with some old Dell Optiplex PCs.  Check our wiki page for more details: [http://students.mypha.org/wiki/Solving_the_Buffer_I/O_Error]("http://students.mypha.org/wiki/Solving_the_Buffer_I/O_Error")

---

### Post by JohnG on 2007-04-18
I have the same problems and given up trying.  Is there any help out there, a small cup of ubuntu will help so many.

I can see I am not alone

---

### Post by kalariwarrior on 2007-05-03
believekevin's link  and advice ([http://students.mypha.org/wiki/Solvi...ffer_I/O_Error](http://students.mypha.org/wiki/Solvi...ffer_I/O_Error)) worked!

Worked as in swapping my existing Samsung cdrom for a random generic drive allowed Ubuntu to do it's thing on an old beater Dell Dimension L550r. I actually had to try 2 drives before it took so maybe it's some weird driver issue with the installer?

The Samsung drive is a "CD-Master 40E" Model SC-140. The other drive that didn't work was an HP FX48B1M - 8220. The one that DID work was a "Lite-On I.T. Corp" Model LTN-486S.

Thanks Ubuntu forum! :popcorn:

---

### Post by kalariwarrior on 2007-05-04
OK, so the new cdrom (LTN-486S) got me past the "Buffer I/O Error" and the "unable to mount cdrom" error but then gave me a whole new error and glitched out when installing the Edubuntu software package. It said I could skip that step and continue with the installation but just wouldn't successfully load the software part of the installer despite repeated tries.

I then tried installing with a factory Ubuntu disk (the ones you can get for free...) instead of my home burned copy and everything worked fine.

So my advice is:

1. Try a "real" Ubuntu cd (or see the previous posts about burning properly) 

2. Try a new cd drive

3. Try both at once!

:guitar:

---

### Post by pvcrisp on 2007-08-08
Here is another success with changing the cd drive!  

PS- I love the support for ubuntu!  I googled my problem, found this thread, and in 5 min had my problem fixed!  Thanks everyone!

---

### Post by BigDaddy-CF- on 2007-08-26
Ok DELL XPS 1710. I had already checked the MD5 due to my first disk having the "error reading boot cd" error" due to my ISO image being corrupted. So I burn again with CDBurnerXP Pro 3 in windows XP at full speed and get the dreaded buffer i/o error. So I follow the rules and use infarecorder to burn the disk at full speed. Again no go buffer i/o error. So I burn again but this time at 2x speed and it works. Thanks for the help fellas

---

