---
title: "Installing Ubuntu (with existing XP) on T60 ThinkPad 2007-73U"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by archer6 on 2008-03-11
I am new to this forum and to Linux. 

I have a ThinkPad T60 (2007-73U) with 2GHz Core Duo, 2GB ram, 100GB HD, WinXP Pro SP2  and the standard (hidden) Rescue and Recovery partition which I want to retain. My goal is to partition the drive to create a space for Ubuntu (latest ver) and set it up to dual boot. 

My question is what is the easiest way to accomplish this? 

Your suggestions and feedback are greatly appreciated

(I hope that I have posted in the correct location, as this is the first day using the forum)

Thanks!

---

### Post by Fire_Chief on 2008-03-11
Here is a site that should help some with installing and configuring Ubuntu on your T60.
[http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60]("http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60")

As for installing to have dual boot with XP/Vista. Here's one article on the steps
[https://wiki.ubuntu.com/Dual_boot_Vista_and_Gutsy_on_Thinkpad_x61s?highlight=%28boot%29%7C%28dual%29%7C%28gutsy%29]("https://wiki.ubuntu.com/Dual_boot_Vista_and_Gutsy_on_Thinkpad_x61s?highlight=%28boot%29%7C%28dual%29%7C%28gutsy%29")

And another one here [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

And here's one with screenshots [http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

Cheers!

---

### Post by archer6 on 2008-03-11
Thanks for your fast response and the links. I will follow them to see what I can learn in order to accomplish this task. 

Cheers!

---

### Post by archer6 on 2008-03-11
> **Fire_Chief said:**
> Here is a site that should help some with installing and configuring Ubuntu on your T60.
[http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60]("http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60")

As for installing to have dual boot with XP/Vista. Here's one article on the steps
[https://wiki.ubuntu.com/Dual_boot_Vista_and_Gutsy_on_Thinkpad_x61s?highlight=%28boot%29%7C%28dual%29%7C%28gutsy%29]("https://wiki.ubuntu.com/Dual_boot_Vista_and_Gutsy_on_Thinkpad_x61s?highlight=%28boot%29%7C%28dual%29%7C%28gutsy%29")

And another one here [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

And here's one with screenshots [http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

Cheers!

Just out of curiosity, how much time should I expect to spend performing this install ? I know it varies from user to user, but a rough idea would be beneficial. Also do you have a suggested method of creating the partition for Linux? Would it be done with Partition Magic or other utility? 

Thanks Again, I can see where this forum is going to be very informative, useful and enjoyable to participate in. 

Cheers!

---

### Post by Fire_Chief on 2008-03-11
For the partitioning, I've had great success with GParted (bootable CD).
[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

*Note* You don't actually have to create a partition for the Linux system. You just have to shrink the Windows partition to leave some free (read unpartitioned) space on the disk. The Ubuntu installer will ask you how you want to use the disk (use all, use free space, etc.). If you're feeling brave, you can even let the Ubuntu installer do the Windows partition shrink for you and carve out it's own space to install on.

The entire install should really take less than or close to 1 hour. The updates time will vary depending on your Internet connection.

---

### Post by sandysandy on 2008-03-11
here are some other links to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

 BACK UP data and de-fragment ur windows drive before resizing ur windows partition.


regards

---

### Post by archer6 on 2008-03-11
Now that I've read up on it, the only questions that remain are as follows.

1) The MBR (master boot record) question: leave it as is or?

2) Remembering that I wish to protect & keep the hidden rescue & recovery partition ( which restores the computer to it''s out of box state in the event of a major crash) is there any other considerations that I should be aware of? 

3) In general I have a fairly high level of competency with Windows XP, just haven't had a chance to play around with Linux and thus the desire to delve into the Linux world by setting up my ThinkPad so I can still do my windows work, but also have the ability to boot to Linux, learn it, get proficient and then decide where I want to go from there.

Thanks again for you very timely responses, as I plan to do this asap. 

Cheers!

---

### Post by archer6 on 2008-03-11
> **sandysandy said:**
> here are some other links to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

 BACK UP data and de-fragment ur windows drive before resizing ur windows partition.


regards

I'm very impressed with the terrific help and reponses I have recieved in just a matter of hours since joining this forum!

Thanks Sandy, I will explore these links. I'm very eager to get my T60 ThinkPad setup with ubuntu linux and then begin the learning process and what promises to be a very interesting journey!

Cheers!

---

### Post by Fire_Chief on 2008-03-11
> **archer6 said:**
> Now that I've read up on it, the only questions that remain are as follows.

1) The MBR (master boot record) question: leave it as is or?

2) Remembering that I wish to protect & keep the hidden rescue & recovery partition ( which restores the computer to it''s out of box state in the event of a major crash) is there any other considerations that I should be aware of? 

3) In general I have a fairly high level of competency with Windows XP, just haven't had a chance to play around with Linux and thus the desire to delve into the Linux world by setting up my ThinkPad so I can still do my windows work, but also have the ability to boot to Linux, learn it, get proficient and then decide where I want to go from there.

Thanks again for you very timely responses, as I plan to do this asap. 

Cheers!

I personally prefer to install GRUB to the MBR and manage my dual (or multi) boot system from GRUB. It's pretty straightfoward and easy to recover should something ever break.

The recovery partition will stay put (assuming you don't delete it during install). You may see it try to be mounted in Linux once you are logged into the Desktop but you can unmount it and then comment out the line for that partition in the /etc/fstab file to prevent it from mounting in the future. The recovery partition is accessed directly from the boot process prior to any OS load (I think). Do be aware that the recovery process will most likely destroy your Ubuntu installation in favor of the default Windows setup that came on the system.

Good luck with your learning!

---

### Post by archer6 on 2008-03-11
Ok, I'm now ready to proceed and install ubuntu on my ThinkPad.

 However I have one serious problem, I downloaded the file to burn to CD and my optical drive has failed to burn it. It still reads ok but for some reason it will not burn the image. I tried burning some regular files to CD and my burner is just out of order. Yet when I put in a MS Office install disk it's ok and will install that. So again, it's reading ok, but not burning. 

Is there a fast way to get a copy of ubuntu on disk already?

And should I use 7.04 or 7.10 version of ubuntu.

Thanks!

---

### Post by sandysandy on 2008-03-11
> **archer6 said:**
> Ok, I'm now ready to proceed and install ubuntu on my ThinkPad.

 However I have one serious problem, I downloaded the file to burn to CD and my optical drive has failed to burn it. It still reads ok but for some reason it will not burn the image. I tried burning some regular files to CD and my burner is just out of order. Yet when I put in a MS Office install disk it's ok and will install that. So again, it's reading ok, but not burning. 

Is there a fast way to get a copy of ubuntu on disk already?

And should I use 7.04 or 7.10 version of ubuntu.

Thanks!

u will have to burn the file as image. not as data cd etc. when u burn it ok u will just see the iso image of ubuntu on cd and no other file.

do u have image burning software. which program are u using to burn.

try 7.10 as it is the latest and will be supported till end april 08 after which 8.04 will be released.

regards

---

### Post by sandysandy on 2008-03-11
here are some links 

Back up MBR

[http://ubuntuforums.org/showthread.php?t=56723&highlight=bs%3D446&page=5](http://ubuntuforums.org/showthread.php?t=56723&highlight=bs%3D446&page=5)

Burning Iso Image

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

regards

---

### Post by egalvan on 2008-03-11
osdisc.com sells most all Linux distros, and has rather fast shipping. They even have a set of the Official Repositories (*5 DVD set with 17.2GB of software*),
or go to a an Internet cafe or hot-spot that will allow downloading & burning.

IBM/lenovo RescueRecovery -- USE WITH CAUTION... WILL ERASE THE ENTIRE HARD DRIVE IF USED TO RESTORE.

It's main use it to restore the machine to an "AS SHIPPED" condition, and that means Windows-only. No Linux. No Choice.

I have a T60P, and dual-booted with W-XP & 7.10.
Used JkDefrag (under windows) to defrag/compact my hd, then GParted LiveCD to shrink windows to 10gBytes. Created a swap and / partitions. 
Liked it so much, I ordered the R&R CD's from IBM, erased the drive using DBAN (Darik's Boot And Nuke) then loaded 7.10 with swap, /, /boot, /home  partiions. 
Now I'm in the process of learning how to dual-boot 32bit and 64bit versions of 7.10.

---

### Post by sandysandy on 2008-03-11
> **egalvan said:**
> 
Now I'm in the process of learning how to dual-boot 32bit and 64bit versions of 7.10.

dual booting 32 bit and 64 bit together is no problem. i am dual booting Gutsy 7.10 of both versions with no problem. the steps are the same as for other dual boots.

regards

---

### Post by archer6 on 2008-03-11
> **sandysandy said:**
> u will have to burn the file as image. not as data cd etc. when u burn it ok u will just see the iso image of ubuntu on cd and no other file.

do u have image burning software. which program are u using to burn.

try 7.10 as it is the latest and will be supported till end april 08 after which 8.04 will be released.

regards

Ok, I'm back...pesky work meetings....:)

I use BurnAware for creating disc images. (.ISO) so this program should do it. I've used it a lot without fail. 

I must say that I am stumped at what went wrong, I have used ThinkPads for years as my main computer and never experienced this issue. Also my T60 is just over a year old and the optical drive has only been used about 10 times. 

Any suggestions? 

And thanks sandysandy for your diligence in helping.....:D

---

### Post by archer6 on 2008-03-11
> **egalvan said:**
> osdisc.com sells most all Linux distros, and has rather fast shipping. They even have a set of the Official Repositories (*5 DVD set with 17.2GB of software*),
or go to a an Internet cafe or hot-spot that will allow downloading & burning.

IBM/lenovo RescueRecovery -- USE WITH CAUTION... WILL ERASE THE ENTIRE HARD DRIVE IF USED TO RESTORE.

It's main use it to restore the machine to an "AS SHIPPED" condition, and that means Windows-only. No Linux. No Choice.

I have a T60P, and dual-booted with W-XP & 7.10.
Used JkDefrag (under windows) to defrag/compact my hd, then GParted LiveCD to shrink windows to 10gBytes. Created a swap and / partitions. 
Liked it so much, I ordered the R&R CD's from IBM, erased the drive using DBAN (Darik's Boot And Nuke) then loaded 7.10 with swap, /, /boot, /home  partiions. 
Now I'm in the process of learning how to dual-boot 32bit and 64bit versions of 7.10.

Everyone here is so helpful, I'm really happy I found this forum. 

As far as rescue and recovery erasing the hard drive, while I was aware of that, I'm really happy that you reminded me. The main reason I want to keep it there is I travel constantly for work and as you know it saves me from having to carry discs. Also I'm used to using it every six months, just to wipe the drive and recover some speed. So now I'm thinking perhaps I should burn the rescue and recovery discs, since I'm going to add linux to the drive. This way I would have even more room to work with. My current HD is 100GB. 

Do you have any suggestions as to what size (partition)  is optimum to start with? I will still be doing a lot of windows work, so that will remain my main OS, until I become skilled Linux at which point things will probably change.

Thanks!

---

### Post by sandysandy on 2008-03-11
it will be ideal to have ubuntu root [COLOR="Blue"]/[/COLOR] partition of about 15 gb. the swap partition is generally twice your RAM size. if u want u can have /home in your ubuntu partition or it can be separate. 

the advantage of having a separate home partition is that even if u format ur ubuntu partition the home partition (storing ur personal files and work) is intact. a separate  /home partition size is whatever maximum u can spare. as ur going to use windows initially for majority of ur work, u can try 10gb for a separate /home partition.

for burning iso image u can give the following a try. may be it will help.

Infra recorder   [http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

ISO recorder    [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

regards

---

### Post by Fire_Chief on 2008-03-12
You could also try CD Burner XP Pro (it's free).
[http://cdburnerxp.se/]("http://cdburnerxp.se/")

---

### Post by egalvan on 2008-03-12
> Do you have any suggestions as to what size (partition) is optimum to start with? I will still be doing a lot of windows work, so that will remain my main OS

On mine, as I stated, I erased the R&R, and shrunk Win-XP down to 10g.Not much still running under Windows on this machine.  Swap was 1g, root set at 30g as I want to play with LOTS of Linux software, and Home got the 160g left over.
I then made a seperate folder under Home named WinXP, and installed the ext2 file system software that allows Window to understand Linux files (  [http://www.fs-driver.org/](http://www.fs-driver.org/)  ). This lets me put ALL my data on the 160g partiton.

---

### Post by egalvan on 2008-03-12
OK, maybe I should have told you HOW I decided to give Windows only 10g.

I migrated as much of my Windows-stuff data off the internal drive to an external drive, then checked how much space was being used... I had approx 6g still used...
:lolflag: applying FC, with KW factored in, I arrived at 10g:lolflag:

You could also, in the absence of a large-enough external storage, move the data to a separate directory, then figure the difference.
Or size it down to what it's using at the moment, and when you get more comfortable, start moving/resizing.


Remember that most programs need to know where their data is located, so you may need to re-adjust the options.

also remember that some Linux stuff runs under Windows, eg FireFox (browser), Thunderbird (email), the GIMP (image manipulation "photoshop stuff"), OpenOffice.org (office software...

I have FireFox set up to find it's 'profiles' folder in the Linux side, so I can surf while in Windows or Linux, and still have the exact same profile (bookmarks, addons, themes, etc).

I also back-up the profiles folder to a PortableApps thumbdrive so I can use it at another computer
(  portableapps.com  )

---

### Post by archer6 on 2008-03-13
To: 
Fire_Chief
sandysandy
egalvan

I am simply smiling and feeling so happy that I found this forum, and that the three of you have been so kind as to put so much time and effort into educating me. 

This is working out so well, as I have managed to harness some of my enthusiasm and hold back from a full on assault, to rush and get ubuntu on my ThinkPad. The more I read your posts, take my time and really think about the advice given it really is priceless. Everything that each of you has offered, makes a lot of sense, these are things that I understand once explained to me as I do have quite a bit of experience on the windows side, but walking into Linux nearly blind. As I'm literally beginning at ground zero knowledge wise. I love to learn, pick things up quickly and therefore I fully appreciate the quality of information you three have provided. 

I have been wanting to do this for some time, but I own a very large business and did not have time previously. Now that things have eased up, I decided to delve into this project. 

So please keep those cards and letters coming in folks......:) 

Every single piece of info is truly apprecatied, read carefully and put into my new approach which is to hold off for just a bit longer while I digest all the great info you have provided, and adjust my usage goals based on this new info you have been so kind to share. 

I am now looking at how I'm going to implement ubuntu through a new, clearer set of lenses that you have provided. Also as I may have mentioned in my first post, I'm very open minded and eager to hear any suggesstions, thoughts, or other experience that you wish to share. I can see now, that by spending a few days here and listening to you, learning from your wealth of knowledge, I'm going to encounter far fewer problems than I would have without your wisdom and guidance.

Thank You and Cheers!
Archer

---

### Post by sandysandy on 2008-03-13
good we could be of help.:)

best wishes

---

### Post by archer6 on 2008-03-14
> **sandysandy said:**
> good we could be of help.:)

best wishes

Thanks sandysandy!

I have a completely new idea:

My T60 ThinkPad Laptop  is my mission critical work computer as I'm a software engineer. 

After all the great info I have received here, I'm now thinking that rather than mess with my main laptop, and risk down time because of a mistake on my part. Here's what came to mind:

I have another ThinkPad that is for casual use at home. It's only about a year old, here are the specs:

ThinkPad R51e / Celeron 1.5 GHz / 768 MB ram / 40 GB HD / 1024x768 / ATI Radeon 200m / CD-ROM / 802.11 b / Win XP home

So, here is a computer that I would have no hesitation in loading Ubuntu on the entire hard drive, and getting rid of Windows.

What do you think of this idea? 
Does this computer have the resources to run Ubuntu properly ( I don't care about speed) 
If so, this would be the perfect "First Linux Box" for me to use to learn and practice on. Then upon ramping up my skills to an appropriate level I would either dual boot my T60, or get a dedicated T60 to put Ubuntu on. 

Your feedback is highly appreciated

Thanks.

---

### Post by egalvan on 2008-03-14
Well Archer, if you want to start flying Warp Speed, then maybe you can try what I did several years ago to learn Linux..

I cobbled up a machine from spare parts, and bought a (relativley) inexpensive TP-600x to play with.
Eveytime I crashed and burned, I just wiped the drive and tried again.
Not being afraid/nervous about munging my working machines gave me considerable freedom to expreiment....and I had a great time. :)

The TP-600 is gone to a freind, replaced by a T23.

The T60P is  a work-horse, so it´s gettintg the benifit of all the crashes and spills of it´s predecesors, I am NOT experiminting with this one.

:popcorn

---

### Post by sandysandy on 2008-03-14
>   I have another ThinkPad that is for casual use at home. It's only about a year old, here are the specs:

ThinkPad R51e / Celeron 1.5 GHz / 768 MB ram / 40 GB HD / 1024x768 / ATI Radeon 200m / CD-ROM / 802.11 b / Win XP home

So, here is a computer that I would have no hesitation in loading Ubuntu on the entire hard drive, and getting rid of Windows.

What do you think of this idea?
Does this computer have the resources to run Ubuntu properly ( I don't care about speed)
     

seems to be OK.

ur processor speed,RAM and hard disk size are more than sufficient for installing ubuntu.

regards

---

### Post by archer6 on 2008-03-14
Thanks egalvan & sandysandy

Wow...... this is too good to be true... both of you responding within minutes of my post. I'm so impressed. I look forward to the day when I will be skilled enough to give back to this community the way you two do. 

Let me ask, is the graphics card going to be compatible? I believe (99% sure) that it's a shared memory card. The computer came with only 256mb ram so I added another 512mb, thinking that again, I would only use it for casual surfing, report writing, etc at home. This was before I got the bug to migrate to Linux. I must admit half the reason I'm doing this is to learn, as I have a burning desire to continue to learn and grow. 

So if all the components pass your evaluation, then I'm going to use that laptop.
I'm not looking for a guarantee of course, as the list of components that  comprise the various configurations is mind boggling.  I'm just looking for a little reassurance that I'm in the ballpark.

I look forward to hearing back and then I will be able to proceed with peace of mind. And it's important to know that I'm not expecting perfection or a completely trouble free experience, as that's half the fun. However that said I simply want to be sure that the machine I'm starting with is good for a starting point, and that I'm not doing something stupid by choosing it for my first Linux experience.

_egalvan_, your explanation of how you began with a TP-600, then T-23 brought back memories as I have use those models in the past, as I began using ThinkPads for work about a decade ago. So I've had most of them and could not be happier.

---

### Post by souneedalink on 2008-03-14
get off the pot....just do it :)

if you burn the recovery CDs be aware it is like....10 of them or something

My R61e is happy that it no longer has to have a gimpy partition to 'recover' with.

---

### Post by archer6 on 2008-03-14
> **souneedalink said:**
> get off the pot....just do it :)

if you burn the recovery CDs be aware it is like....10 of them or something

My R61e is happy that it no longer has to have a gimpy partition to 'recover' with.

Sounds great to me ! Hmmm let me see now.... where is that hacksaw....oops wrong tool....:)

It just occurred to me that I have one remaining hurdle to clear. 

That's the CD-Rom which is read only on this R51, and the burner on my T60 just failed.....argggggh. It's $200 to replace it which I really don't want to spend as I normally hardly every use it, as I have that ultra bay occupied with a second hard drive as my normal working configuration. 

Any thoughts?

---

### Post by sandysandy on 2008-03-14
> **archer6 said:**
> Sounds great to me ! Hmmm let me see now.... where is that hacksaw....oops wrong tool....:)

It just occurred to me that I have one remaining hurdle to clear. 

That's the CD-Rom which is read only on this R51, and the burner on my T60 just failed.....argggggh. It's $200 to replace it which I really don't want to spend as I normally hardly every use it, as I have that ultra bay occupied with a second hard drive as my normal working configuration. 

Any thoughts?

have a look at this link for various ways to install Ubuntu which includes Server and network installations.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

regards

---

### Post by archer6 on 2008-03-14
I forgot to mention that I'm not worried about not being able to  burn recovery CD's for the Windows Home OS that came on it, as I'm migrating to Linux and not looking back. 

What I do need some advice on is what I will need in the way of a disk that is a CD (as opposed to DVD) that has Ubuntu on it for me to install, then if there are any other disks that I'm going to need.

Your thoughts? 

Thanks!

---

### Post by sandysandy on 2008-03-14
u could order a free Cd from the following link

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

it may take about 4 weeks though.

regards

---

### Post by archer6 on 2008-03-14
> **sandysandy said:**
> u could order a free Cd from the following link

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

it may take about 4 weeks though.

regards

Here is a copy and paste of the link you sent in your prior message:
______________________________________________________

Installation without a CD

The documents listed below provide instructions for installing Ubuntu without using a CD or CD-ROM drive.

    *

      SmartBootManager - Installing from a PC which will not boot from a CD.
    *

      Installation/FromUSBStick - Installing from a USB memory stick.
    *

      Installation/FromCForUSBStick - Similar to above but using grub.
    *

      Installation/WithFloppies - Installing without a CD drive over a network.
    *

      Installation/FromHardDriveWithFloppies - Installing without a CD drive or network capabilities from a hard drive.
    *

      Installation/FromWindows - Installing from Windows without using floppies, a CD, or any other removable media.
    *

      Installation/FromLinux - Installing using a spare partition from an existing Linux system to house the Ubuntu CD image.
_______________________________________________________________________________

Which one of these choices would be the best one for me to use?

I do like the idea of not having to use a CD, therefore eliminating the wait. 
Like everyone else time is always the limiting factor, and I'm ready to do it this beginning this afternoon. 
I have most of this weekend to dedicate to this project (which is rare) and I'm ready to get on with it.....:)

---

### Post by archer6 on 2008-03-14
Oh.... and I do not have access to a network, so this will be purely a download situation. At least I have a broadband connection for the download.

---

### Post by archer6 on 2008-03-14
Heres a link to what I  just found  on:[ Amazon]("http://www.amazon.com/Canonical-Ubuntu-7-10-PC-Edition/dp/B000XJLSKY/ref=pd_bbs_sr_1?ie=UTF8&s=software&qid=1205517928&sr=8-1")
I can overnight it and then I will have the CD right away.

Thoughts?

---

### Post by egalvan on 2008-03-16
[http://www.amazon.com/Practical-Guide-Ubuntu-Linux-R/dp/013236039X/ref=pd_bbs_sr_6?ie=UTF8&s=books&qid=1205684255&sr=8-6](http://www.amazon.com/Practical-Guide-Ubuntu-Linux-R/dp/013236039X/ref=pd_bbs_sr_6?ie=UTF8&s=books&qid=1205684255&sr=8-6)

[http://www.amazon.com/Ubuntu-7-10-Linux-Unleashed-3rd/dp/0672329697/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1205684255&sr=8-2](http://www.amazon.com/Ubuntu-7-10-Linux-Unleashed-3rd/dp/0672329697/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1205684255&sr=8-2)

either  include book & 7.10 DVD

personally, I like to have something to hold & read while working on the computer. Shows my age, I guess.

:popcorn:

---

### Post by archer6 on 2008-03-16
> **egalvan said:**
> [http://www.amazon.com/Practical-Guide-Ubuntu-Linux-R/dp/013236039X/ref=pd_bbs_sr_6?ie=UTF8&s=books&qid=1205684255&sr=8-6](http://www.amazon.com/Practical-Guide-Ubuntu-Linux-R/dp/013236039X/ref=pd_bbs_sr_6?ie=UTF8&s=books&qid=1205684255&sr=8-6)

[http://www.amazon.com/Ubuntu-7-10-Linux-Unleashed-3rd/dp/0672329697/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1205684255&sr=8-2](http://www.amazon.com/Ubuntu-7-10-Linux-Unleashed-3rd/dp/0672329697/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1205684255&sr=8-2)

either  include book & 7.10 DVD

personally, I like to have something to hold & read while working on the computer. Shows my age, I guess.

:popcorn:

Heh!... you and I are on the very same wave length. I am a voracious reader (read book addict) .....:)

I saw that, and frankly that's why I posted that I found the disk on Amazon, as I thought I would see what kind of feedback I got. This is perfect because I too am a very detail oriented guy that enjoys learning, and being well educated in the areas of interest that I have. In fact it's the very reason I'm taking on this Linux project, as it's something new. I get bored easily as I have a fairly high capacity for learning, so this is right up my alley.

I know I've said it before and not to be patronizing or over do it, but as someone who participates in a fair amount of forums, I'm just so impressed with this one. The courtesy, quick responses and helpfulness of those who have responded to my posts, is simply stellar. Also quite frankly the other forums I'm on are areas of my expertise so I"m the one giving help to others. I really enjoy it and I operate in the same way that you, sandysandy, and Fire_Chief have. It's great to help others and to give my experience to those who appreciate the help. 

Now that I'm on the other end and complete rookie here, it's nice to get that same first class assistance.

Finally, since you may know if you saw my earlier post, I'm slowing down a bit, (enthusiasm is something that I'm never short of) and not rushing into this and it's paid off as the additional thoughts and info you people have provided is greatly appreciated and will ensure that I get a good start. Along those lines, now I am happy that I did'nt place my Amazon order (yet) as I am going to go for the book and the disk now. 

As always... thanks to everyone who has contributed to my start in the new (to me) world of Linux-Land!

Cheers..........:)

---

### Post by sandysandy on 2008-03-16
all the best:)

regards

---

### Post by egalvan on 2008-03-17
One last thought re: bad cd drive..... you can find relatively cheap CD BURNERS, or a DVD-ROM/CD-BURNER on eBay... folks who up-grade to a Dual-Layer DVD burner or such often sell their older drives.

The T60/T60P uses a standard thin-form-factor  optical drive, it just has a flat plate added to the rear connector area attached with three or four screws. Don´t throw the old T60 drive out until you salvage those parts.
The thinness and the flate plate are all that make it IBM. Oh, and the ¨nothced¨ face plate......

Also, I the T4x line uses the same thickness optical drive, with a thicker notched face plate.


this one, eg,

[http://cgi.ebay.com/CD-RW-DVD-COMBO-DRIVE-IBM-THINKPAD-T40-T40P-T41_W0QQitemZ230232706768QQihZ013QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/CD-RW-DVD-COMBO-DRIVE-IBM-THINKPAD-T40-T40P-T41_W0QQitemZ230232706768QQihZ013QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

or this one, that has a nice carry case.... hm, I might bid on this just for the case...I don´t need the drive...

[http://cgi.ebay.com/Thinkpad-laptop-CD-RW-DVD-Combo-Drive-T40-T41-T42-more_W0QQitemZ290215100420QQihZ019QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Thinkpad-laptop-CD-RW-DVD-Combo-Drive-T40-T41-T42-more_W0QQitemZ290215100420QQihZ019QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

(I used ¨ t40 cd ¨ as the search terms)



(two examples using  ¨t40 dvd-rw¨  instead )

[http://cgi.ebay.com/IBM-ThinkPad-DVD-RW-MULTI-BURNER-T40-T41-T42-T43-T60_W0QQitemZ140215203664QQihZ004QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/IBM-ThinkPad-DVD-RW-MULTI-BURNER-T40-T41-T42-T43-T60_W0QQitemZ140215203664QQihZ004QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
[http://cgi.ebay.com/IBM-ThinkPad-Ultrabay-DVD-RW-Burner-T40-T60-X40-X60-Z60_W0QQitemZ160218699147QQihZ006QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/IBM-ThinkPad-Ultrabay-DVD-RW-Burner-T40-T60-X40-X60-Z60_W0QQitemZ160218699147QQihZ006QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)





All the best on this journey, and have fun!

Ernest Galvan
Lt, BFD.

:popcorn:

---

### Post by archer6 on 2008-03-17
> **egalvan said:**
> One last thought re: bad cd drive..... you can find relatively cheap CD BURNERS, or a DVD-ROM/CD-BURNER on eBay... folks who up-grade to a Dual-Layer DVD burner or such often sell their older drives.

The T60/T60P uses a standard thin-form-factor  optical drive, it just has a flat plate added to the rear connector area attached with three or four screws. Don´t throw the old T60 drive out until you salvage those parts.
The thinness and the flate plate are all that make it IBM. Oh, and the ¨nothced¨ face plate......

Also, I the T4x line uses the same thickness optical drive, with a thicker notched face plate.


this one, eg,

[http://cgi.ebay.com/CD-RW-DVD-COMBO-DRIVE-IBM-THINKPAD-T40-T40P-T41_W0QQitemZ230232706768QQihZ013QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/CD-RW-DVD-COMBO-DRIVE-IBM-THINKPAD-T40-T40P-T41_W0QQitemZ230232706768QQihZ013QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

or this one, that has a nice carry case.... hm, I might bid on this just for the case...I don´t need the drive...

[http://cgi.ebay.com/Thinkpad-laptop-CD-RW-DVD-Combo-Drive-T40-T41-T42-more_W0QQitemZ290215100420QQihZ019QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Thinkpad-laptop-CD-RW-DVD-Combo-Drive-T40-T41-T42-more_W0QQitemZ290215100420QQihZ019QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

(I used ¨ t40 cd ¨ as the search terms)



(two examples using  ¨t40 dvd-rw¨  instead )

[http://cgi.ebay.com/IBM-ThinkPad-DVD-RW-MULTI-BURNER-T40-T41-T42-T43-T60_W0QQitemZ140215203664QQihZ004QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/IBM-ThinkPad-DVD-RW-MULTI-BURNER-T40-T41-T42-T43-T60_W0QQitemZ140215203664QQihZ004QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
[http://cgi.ebay.com/IBM-ThinkPad-Ultrabay-DVD-RW-Burner-T40-T60-X40-X60-Z60_W0QQitemZ160218699147QQihZ006QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/IBM-ThinkPad-Ultrabay-DVD-RW-Burner-T40-T60-X40-X60-Z60_W0QQitemZ160218699147QQihZ006QQcategoryZ131540QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)





All the best on this journey, and have fun!

Ernest Galvan
Lt, BFD.

:popcorn:

Gee....... I could have had a V-8 (juice).... this falls into the "why didn't I think of this category". I'm glad someone's thinking here, even if it isn't me.........:)

You are so right, and since I always keep the little bits and pieces when something fails, I have everything I need for the ultra bay, except the actual drive itself. Thanks so much for doing the research on ebay and providing the links. This is the perfect solution.

 Thanks to this joint effort, I'm one step closer to Ubuntu Nerdvana......:KS

---

### Post by egalvan on 2008-03-17
> **archer6 said:**
> Gee....... I could have had a V-8 (juice).... this falls into the "why didn't I think of this category". I'm glad someone's thinking here, even if it isn't me.........:)

One cannot think of everything, but many can think of much....


> **archer6 said:**
> You are so right, ... I always keep the little bits / pieces when something fails, I have everything I need for the ultra bay, except ...drive itself. Thanks so much for doing the research on ebay and providing the links. This is the perfect solution.
Ubunut Nerdvana......:KS

OK, you're welcome, but I still get "DIBS" on that neat little carry-case.

ErnestG

:popcorn:

---

### Post by Ohwii on 2008-04-04
hi guys,

I, myself have a T60 and since the Thinkwiki has been down for a while, I just stumbled over some stuff on the internet. because I am working on ubuntu right now. 
Concerning :
> 
1) The MBR (master boot record) question: leave it as is or?


I found this 

> 
if you load GRUB on the MBR,

1) the ThinkVantage button will not work

2) the backup and rescue partition on the Thinkpad is lost.

If you dont care about the above two, you can load GRUB on the MBR and the installation becomes much simpler - you can just follow the standard installation procedure for Windows dual boot.


on this blog [URL="http://lifeisaventure.wordpress.com/2007/06/13/installing-ubuntu-feisty-fawn-704-on-a-thinkpad-t60/"]
[COLOR="Orange"]Here[/COLOR] 
[/URL]

I know It is an old blog, but could some verify or falsify the statement.:confused:

Talk to you Later,

Oh Wii-eee

---

