---
title: "boot from CD cannot mount /dev/loop0"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by wolf99 on 2010-08-19
Hi Folks

I just dl'ed and burnt a 10.04 ubuntu disk (using infra recorder), and popped it in, the ubuntu load screen showed and progress got nearly done then a message shows:

"(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error.

Can not mount /dev/loop0 (cdrom/casperfilesystem.squashfs) on //filesystem.squashfs."

Can I rescue this disc?

thanks

EDIT: I did have a 9.1 disc somewhere that did work OK before now (but lost is :( )

---

### Post by Kiesel on 2010-08-26
same here, the 64 bit doesnt mount with that exact same error) but the 32 bit version of lucid lynx does.
i found the 32 bit version somewhere in my box so i guess its not the snapshot but the 64 version is.
im runing out of cd's here ;)
i will try to use a pendrive installation and see how that goes.
greets, kiesel

/edit: i decided to go with the dvd instead of the cd. the dvd is still 10.04, not 10.04.1. Everything worked fine :)

---

### Post by kc5hwb on 2010-08-31
I'm getting this error with 2 burned CDs and on 2 separate computers.  One was my laptop which is a Toshiba Satalite P105 and one is a desktop that I built myself, which has an ABIT MB and AMD64 CPU.  I downloaded and burned Lucid 10.04 and got this error on these 2 machines so I went ahead and burned the ISO again to another CD, and I am still getting this same error.

I am trying the DVD download now and will attempt install from there.

---

### Post by kc5hwb on 2010-09-02
UPDATE:
I downloaded and installed the DVD version of 10.04 and it is working great.  I have Googled this error and found a couple of other sites that talk about having this issue when installing for the CD burned from the ISO from ubuntu.com.  Is there a known issue with this release?

---

### Post by horbrastar on 2010-09-03
I'm seeing exactly the same error --- anyone know what the cause is?

---

### Post by gibbogle on 2010-09-04
I am seeing this error as well.  Not a good introduction to ubuntu :-(.
Did the previous post mean that burning a DVD instead of a CD is a solution?

---

### Post by LMD on 2010-09-04
I just confirmed the above solution. I burnt the iso on a DVD Media and it worked fine. Confirming that the iso does not work when burning on CDR media. At least on my IBM ThinkPad T41.

---

### Post by captlogic on 2010-09-04
I'm having the same issue, however when I burn the ISO to a dvdr media I still get the same issue.

I will try a previous version.

---

### Post by gibbogle on 2010-09-04
I decided to try downloading the iso again.  To my surprise the size of the .iso that I received was much different (bigger) than the previous one.  I burned another CD, and this one works.  Just to be sure, I did the md5sum check:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and confirmed that the new .iso is correct.  I don't know why the first one was so wrong.  It seems that there can be a problem with the download, and this might explain many of the issues that people are reporting here.

---

### Post by sflesch on 2010-09-28
FWIW This thread helped me to take a look at my ISO. I discovered the download size was 154MB and saw that the 64-bit version was 686MB. I then went back to the download site and started the download again. Lo and Behold it is currently downloading 686MB for the 32-bit version, so my money is on a bad ISO somewhere.

Kind of odd though that a bad ISO was still bootable though, isn't it?

I hope this helps someone! :guitar:

---

### Post by nutznboltz on 2010-10-10
> **sflesch said:**
> Kind of odd though that a bad ISO was still bootable though, isn't it?
Only a portion of the CD is used by the bootstrap.

---

### Post by Domar on 2010-10-10
Same problem here with the 10.10 on dvd-rw

md5 is ok, maybe it is because of the rw?

---

### Post by javila01 on 2010-10-18
How about from a USB drive my friend cause I have no DVD nor CD drive.

Thank you!

---

### Post by katiepea on 2010-11-01
same error here, 5 different cdr's, all different brands, 2 computers, 2 dvdrw's, wow ubuntu, you seem to have an iso posted that works on nothing.  not good for people reading that linux is easy these days.

---

### Post by wyllie on 2010-11-18
> **katiepea said:**
> same error here, 5 different cdr's, all different brands, 2 computers, 2 dvdrw's, wow ubuntu, you seem to have an iso posted that works on nothing.  not good for people reading that linux is easy these days.

I really hate it when people bitch and moan without reading the rest of the thread.  I mean you spent the time to burn 5 cds on different computers, etc. and finally decide it's the ISO posted on the site thats bad which seems unlikely as there would be hundreds if not thousands of messages in this thread if it was a problem with the ISO.  Did you ever think that maybe the problem is that you did not get the whole ISO downloaded?

---

### Post by Mudmanc4 on 2010-11-28
I had the same problem , but it is my own fault for not checking the size of the download. i used two disks because i failed to look into it as i should have. 

Seems were all so used to bad cd/dvd media that we automatically assume it was a bad burn. sad

 As for any of you new to ubuntu , ubuntu is likely the best linux distro out there for every day ease of installation , not to mention use. You'll likely have your system up and running including you laptop users wireless , in under an hour , many cases well under an hour in including the burn , installation and configure. 

 The community has really taken to this distro over the years and committed to developing every aspect of it making something very complex simple and easy to use , not to mention super fun !

---

### Post by williewonka on 2010-12-08
I have tried the usb, cd and dvd to no avail still getting stuck at the loop0 screen.

Just went back and clicked on download from the ubuntu download area. The new file that has started to download is 693MB and the file I left downloading the other night is 298MB.

I still have to wait about an hour for the new download to finish but it looks obvious that the original download was flawed. Not saying it is going to fix the problem but good place to start.

I am going to look into the MD5 checksum instructions as mentioned by gibbogle. I have never used MD5 checksum before. I have seen it around alot on Microsoft website but never really knew what it was for.

---

### Post by ground on 2010-12-15
I downloaded the 64 bit version of 10.10 this morning and it gave me the same error.

[B]Solution:
[/B]I took the CD and put it in an actual CD drive, not a DVD drive that can read CDs.  It seems as though the DVD drive that I was originally using did not want to play nice with the installation CD.  So, my recommendation is to use an old CD drive you have lying around and do the installation that way.

---

### Post by Awareness on 2010-12-25
same error
I checked the checksum of the iso and it is perfectly fine. I am using a cd on a dvd drive.

> **ground said:**
> I downloaded the 64 bit version of 10.10 this morning and it gave me the same error.

[B]Solution:
[/B]I took the CD and put it in an actual CD drive, not a DVD drive that can read CDs.  It seems as though the DVD drive that I was originally using did not want to play nice with the installation CD.  So, my recommendation is to use an old CD drive you have lying around and do the installation that way.

This seems probable. I have not a cd drive available to check it out tho.

did it worked out for you? this seems a bug tho.

---

### Post by resqguy on 2010-12-25
I'm having the same issue and have done some troubleshooting.  Here is what I did:

Downloaded Ubuntu image
Checked the file - checksum OK
Burned CD - install failed
Ripped CD back to iso on my XP box - checksum failed on saved iso file

Something is going wrong on the CD burn.  In InfraRecorder there are a few options for Write method:
SAO
TAO
TAO with pregap
raw96r
raw16
raw96p

I've been using SAO with the slowest write speed.  Does Ubuntu care about the Write method?

---

### Post by Awareness on 2010-12-26
I dont really know where all the problem come from. I finally fix it burning a the cd iso in a dvd. My drive is a dvd. 

I wish ubuntu had more engineering power instead of lots of folks saying "me too!" on the forum threads and on the bug reports :(

I have like 10 bugs open with nothing but "me too!" :(

---

### Post by resqguy on 2010-12-26
I tried to use a DVD but still have the same problem.  I was eventually able to use a USB flash drive and a card reader.

With both CD and DVD the file that I ripped back to my desktop was a different size than the file I started with.  The check sum wasn't close.  In both cases I used InfraRecorder to create the CD/DVD disc and to rip it back.  I think the problem lies there.

---

### Post by wdqss on 2011-01-06
> **resqguy said:**
> I tried to use a DVD but still have the same problem. I was eventually able to use a USB flash drive and a card reader.
 
With both CD and DVD the file that I ripped back to my desktop was a different size than the file I started with. The check sum wasn't close. In both cases I used InfraRecorder to create the CD/DVD disc and to rip it back. I think the problem lies there.
 
 
I burn iso use DVD driver,But the error as normal.I tried use ohter download iso,the same.so i dont konw what will do!!

---

### Post by mollamahmutoglu on 2011-01-08
same problem
 
tried two desktop amd64 iso with two different cds with no luck. then downloaded dvd version burned and now it is working. I burned it with a dell desktop optilex 960. hope this will help someone.

---

### Post by jdieter on 2011-01-19
Tore my hair out on this one. My fix was to use the alternate install CD. Worked like a champ.

---

### Post by dfrankow on 2011-02-03
> **gibbogle said:**
> I decided to try downloading the iso again.  To my surprise the size of the .iso that I received was much different (bigger) than the previous one.  I burned another CD, and this one works.  Just to be sure, I did the md5sum check:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and confirmed that the new .iso is correct.  I don't know why the first one was so wrong.  It seems that there can be a problem with the download, and this might explain many of the issues that people are reporting here.
 
This helped me. Thanks!

---

### Post by Nemo_bis on 2011-02-18
It's strange because I had this problem with a CD I had just used to install Ubuntu on another machine; I've just redownloaded it (because I had deleted the iso) and burnt it. If you download the torrent, the hash is automatically verified, AFAIK, and Brasero checks the integrity of the disc after burning it.

---

### Post by cabalon on 2011-04-12
Thanks for this.  I'd never have thought to check the size of the ISO.  Even months later, the solution is helpful.

:KS

---

### Post by goscuter1 on 2011-04-24
> **Awareness said:**
> I dont really know where all the problem come from. I finally fix it burning a the cd iso in a dvd. My drive is a dvd. 

I wish ubuntu had more engineering power instead of lots of folks saying "me too!" on the forum threads and on the bug reports :(

I have like 10 bugs open with nothing but "me too!" :(

Oh wow I think that's unfair Awareness. 

Perhaps you should check check yourself before you wreck wreck yourself.

Everyone knows that ubuntuforums are full of geniuses with answers. Of course, I've never found one on ubuntuforums. An answer, that is. 

I have, however, had threads locked where I was abused by idiot after idiot for my confronting evidence suggesting the above:

[http://ubuntuforums.org/showthread.php?t=1733022](http://ubuntuforums.org/showthread.php?t=1733022)

For what it's worth I have the same problem as everyone in this thread. For what it's worth, this is the 4th thread I've found where no one has the answer. 

Launchpad is your best bet. There are some great guys on there. And also Canonical have a Home User service now I've been meaning to try but I'm just trying to get my systems up for long enough to gulp in some air.

---

### Post by Morgan74 on 2011-05-17
I had the same issue when booting from a USB drive.  I downloaded a new iso file and that fixed it.  I downloaded 11.04 the day it came out, and I know my ISP was having stability problems that day.  Maybe the download got cut off mid way.  The funny thing is that I did two Wubi installs just fine with this drive.

---

### Post by ragb1 on 2011-06-01
Hi:

I had the same problem trying to install Ubuntu 10.04 on an old PC. I tried the install DVD on another computer and it works fine.

Finally, I connected an external usb DVD unit, and no problem at boot.

---

### Post by a.chaos on 2011-06-23
Hi...

I'm really new to this and don't understand how to fix this problem other than downloading all over again. 

Checked the md5 hash and mine matched the one provided on this page: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

The download seems to be the right size ...685.3 MB


I read the thread and all I got was to keep downloading away... should I just download the alternate?  



:KS

---

### Post by mörgæs on 2011-06-23
Hi, welcome to the fora.

Wait a moment before downloading... If the problem comes from booting a CD, I would recommend trying a USB stick.

---

### Post by wutzerface77 on 2011-06-27
I have the same exact problem! I'm not sure what to do...:icon_frown:

---

### Post by mörgæs on 2011-06-27
It is not clear what you mean by 'same'. Which releases of Ubuntu have you tried, and did you boot from CD or USB? 

Please give a complete description in all details.

---

### Post by howler99 on 2011-06-30
@mörgæs I'm having a similar problem, didn't see a response so I thought I would jump in. 

Created Xubuntu live CD 11.04 and later 10.04. After reading here, I verified the MD5SUM for both images. In both case when I try to boot my Lenovo T41 (1gb RAM) from CD. 

- language selection screen (English selected)
- xubuntu menu screen (Try Xubutntu without installing selected)
- xubuntu splash screen
- BusyBox v1.17 starts up
- error message displayed - (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed

I looked at the BIOS options, but I was also wondering if any of the options on the Xubuntu might have an impact here. 

Also, I should mention I have a SliTAZ Live CD created essentially the same way (and same brand CD) that works flawlessly. 

Let me know if you need anything else. Thanks for any assistance.

---

### Post by mörgæs on 2011-06-30
Hi, welcome to the fora.

If your BIOS supports booting from USB: Try downloading the alternate ISO from the link in my signature and create a USB stick with Unetbootin.

---

### Post by howler99 on 2011-06-30
That worked great except it's USB 1.0. I'm probably missing something, but are there any guidelines/FAQs/howto for getting a USB boot to cache on the hard drive.? 

I kind of like the workstation on a thumbdrive, and not having to modify my HD partitions, but the USB 1.0 speed is a little painful.

Thanks.

---

### Post by mörgæs on 2011-07-01
You can have a complete Ubuntu system (including your modifications, settings and user files) installed on a USB drive, so you have everything ready no matter which computer you are using. Just google for a 'persistent' USB install.

If you set it to cache on the hard drive, it will be less portable. 

On a computer with only USB 1 ports I would rather do a classic install to the hard drive.

---

### Post by Pimpn8ezy on 2011-07-03
xubuntu 11.04 x86

Using live CD image on a DVD drive.

Booting from a CD resulted in the 'cannot mount ...' error

Booting from an image burned on a DVD instead and everything worked fine.

---

### Post by jRdbRR on 2011-07-17
any idea on what causes this problem? I'm experiencing the same error message with my attempted BackTrack 5 live USB.  (md5 is correct).  
No help from their worthless forums, of course...

---

### Post by j*tech on 2011-08-26
I've been trying to download the iso from the Ubuntu homepage and I haven't even been able to complete the download...It gets half way or so then gives me an error box...Tried on Firefox and IE...Anyone else having this problem?

---

### Post by mörgæs on 2011-08-27
You could try downloading from 
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

---

### Post by j*tech on 2011-08-29
Thnx :guitar:

---

### Post by doriandeluca on 2011-09-08
FYI, I've had success after receiving this error by downloading the ISO, verifying that it was correct and installing it via USB.

---

### Post by beguelin on 2011-09-29
Same issue here. Check md5 sum of iso was ok. Burn CD, got above error.
Solution: I burned the image to a DVD instead of a CD. That worked.

---

### Post by suryasaha on 2011-10-25
I was having the same problem with a old Dell Optiplex desktop and 10.04.3 LTS even after checking md5sums. The problems was that I was using a rewritable CD (only those were handy). 

**Solution** for me was to use a standard CD-R to create a bootable disk and it worked like a charm. I checked each file on the CD using md5sum.txt in the root directory of the CD (md5sum -c md5sum.txt).

---

### Post by maureenc on 2012-01-31
I had this problem today loading a 10.4.3 LTS Live CD.

The first time I had burnt it with Brasero on Macxmum speed... accidentally

Same messages about /dev/loop0 Initramfs and BusyBox etc.

I brunt the same ISO again using the slowest speed and it has loaded OK.

Am currently logged on using the Live CD version.

.

---

