---
title: "CD Integrity Check Failed"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Subbu_09 on 2009-11-21
Hi guys,
 
I have a Windows XP running on my Intel Celeron 1.7Ghz machine with 512 MB RAM and 40 GB HDD with 4 partitions of 10 GB each.
 
I am new to Linux and wanted to try it using a LIVE CD. But, by mistake I downloaded
an alternate CD, I went ahead and tried to install Ubuntu 9.10 yesterday.
I got the Karmic-alternate-i386.iso image bunt into a CD and tried to boot Ubuntu.
After passing thru' the language and keyboard detect steps, I got the following error.
----------------------------------------------------------
Load Installer Components from CD
There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD ROM.
Failed to copy file from CD ROM.
Retry? 
YES / NO.
-----------------------------------------------------------
Please let me know what does this error mean. Is there an issue with the CD-ROM
or the image I burnt OR the ISO file I downloaded and is there a fix for the issue?
Please help me, I am curious to see how Ubuntu 9.10 desktop looks.........
 
I also tried the option of "Check for CD defects" and after some time, I got the following error "CD integrity Check failed". What does this mean. My downloaded ISO file seems to be correct as I did the MD5 CHECKSUM and it matched with what was found with Ubutnu's official site. Should I try to Burn the ISO image again on another CD?
 
Also, I burnt this one at 8X speed, which is the lowest speed available with my Nero 6 version Burner software in Windows XP. But, I see from some forums that the CD should be burnt only at 4X speed. Is it necessary? Then how can I burn it with my Nero? Are there any other freeware available that will burn an IMAGE CD at 4X?
 
Please help. Also, let me know how to verify the burnt CD's MD5 CHECK SUM from Windows XP? The steps I find in Ubuntu's site is only for those who are already running Lunux and have a Terminal opened for checking the integrity of the CD drive.
 
Please help. Thanks a lot guys. you are all doing a wonderful job 24X7 helping others overcome their issues in just a matter of few minutes and hours. Keep it up!!!.
 
Thanks,
 
Cheers,
Subbu.

---

### Post by tommcd on 2009-11-21
You need to burn a new CD. Instead of using Nero try Iso Recorder or Infra Recorder. They are free and work well. Be sure to burn the CD at the slowest possible speed. 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot up the CD run the option to check the disc for defects.
If it still fails the md5sum check, then try downloading the iso from a different mirror. If the iso passed the md5sum check it is probably good though. You might also consider using a different brand CDR media if it still fails the md5sum check. Also use a CDR, and not a CDRW. I have seen CDRWs fail the md5sum check after they have been rewritten a lot of times.
See this for checking md5sums if you need it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Write back if you need more help.

---

### Post by Subbu_09 on 2009-11-21
> **tommcd said:**
> You need to burn a new CD. Instead of using Nero try Iso Recorder or Infra Recorder. They are free and work well. Be sure to burn the CD at the slowest possible speed. 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot up the CD run the option to check the disc for defects.
If it still fails the md5sum check, then try downloading the iso from a different mirror. If the iso passed the md5sum check it is probably good though. You might also consider using a different brand CDR media if it still fails the md5sum check. Also use a CDR, and not a CDRW. I have seen CDRWs fail the md5sum check after they have been rewritten a lot of times.
See this for checking md5sums if you need it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Write back if you need more help.
 
Hi Tom,
 
Thanks a lot for your inputs. Like you said, I am going to use the Infra Recorder OR the ISO Recorder for burning the LIVE CD - I plan to burn it at 4X speed. Hope this would be fine and try to boot it again. I will also use a different brand of CD-R and hope it will pass the test of "CHECK DISK FOR DEFECTS". And like you said, I have already verified the ISO image by doing an MD5 CHECK SUM and it seems to be good.
 
One more thing, using the alternate CD, can I choose a different partition (Drive F:)
in my machine, which is empty with 10 GB space and I have my Windows XP SP2 running in the C drive with D and E drives reserved for Data and other stuff. Can I do
like this and get a dual boot of Ubuntu 9.10 without affecting my Windows XP and other files / applications? Please confirm so that I can proceed. I don't want to mess up my Windows XP as I eagerly try Ubuntu 9.10 for the first time.....
 
OR would you advice me to go for the LIVE CD option first before using the alternate CD for instlalling in a different partition?
 
Thanks,
Subbu.

---

### Post by tommcd on 2009-11-21
> **Subbu_09 said:**
> 
One more thing, using the alternate CD, can I choose a different partition (Drive F:)
in my machine, which is empty with 10 GB space and I have my Windows XP SP2 running in the C drive with D and E drives reserved for Data and other stuff. Can I do
like this and get a dual boot of Ubuntu 9.10 without affecting my Windows XP and other files / applications? 

The alternate install CD is fine for this purpose. To make it easy for you to identify the correct partition from the Ubuntu CD, first boot Windows and delete the F drive from Windows disk management utility. Also fully defragment Windows before installing Ubuntu for best results.
Then boot the Ubuntu CD. When you get to the partitioning part of the install, choose manual partitioning. There should be 10GB free space on the drive after you have deleted drive F from Windows. Create these 2 partitions for Ubuntu:
root (simply denoted as / in linux) 9GB
swap 1GB
Then proceed with the install. The 9GB root partition will be fine for trying out Ubuntu.

---

### Post by presence1960 on 2009-11-21
Subbu, please refrain from creating multiple threads on the same topic.

You have a thread [here]("http://ubuntuforums.org/showthread.php?p=8359006#post8359006") for the same exact problem.

---

### Post by Subbu_09 on 2009-11-21
> **presence1960 said:**
> Subbu, please refrain from creating multiple threads on the same topic.
 
You have a thread [here]("http://ubuntuforums.org/showthread.php?p=8359006#post8359006") for the same exact problem.
 
Hi,
 
Since I am trying with both the LIVE CD and the Alternate CD and ending up with problems with both, I created two separate ones - hoping I would help for any one them. Also, when I started a thread with a different subject for the issue I encountered first, a couple of days ago - I did not get any response. I also did a follow up but to no avail. So, I thought of creating a new thread with a new subject line though combining my old problem and providing some additional details. I now seem to get a response only to this thread. However, I do understand the point you are making.
 
Thanks for all your help.
 
Subbu.

---

### Post by presence1960 on 2009-11-21
> **Subbu_09 said:**
> Hi,
 
Since I am trying with both the LIVE CD and the Alternate CD and ending up with problems with both, I created two separate ones - hoping I would help for any one them. Also, when I started a thread with a different subject for the issue I encountered first, a couple of days ago - I did not get any response. I also did a follow up but to no avail. So, I thought of creating a new thread with a new subject line though combining my old problem and providing some additional details. I now seem to get a response only to this thread. However, I do understand the point you are making.
 
Thanks for all your help.
 
Subbu.

I understand, but you did cover both Live Cd and alternate in previous thread. As far as no responses sometimes we have to wait & sit tight. We are not paid support. You may have to wait some time for someone with the knowledge of your situation to log in and read your post to reply. I think you will find you will get better help keeping one thread on a topic this way all who read your thread are up to date with all details including things you may have already tried to fix the problem. It makes helping you and you being helped a heck of a lot better.

---

### Post by Subbu_09 on 2009-11-21
> **presence1960 said:**
> I understand, but you did cover both Live Cd and alternate in previous thread. As far as no responses sometimes we have to wait & sit tight. We are not paid support. You may have to wait some time for someone with the knowledge of your situation to log in and read your post to reply. I think you will find you will get better help keeping one thread on a topic this way all who read your thread are up to date with all details including things you may have already tried to fix the problem. It makes helping you and you being helped a heck of a lot better.
 
Thanks for your understanding. I also do not wish to have multiple threads running as I have to go around and look for replies and remember what I typed where, etc. It is a one-off thing and it will not happen again. It is perfectly right to have only one thread running with all information one can provide, so it will help me and others who try to help figure out the problem / solution pretty quick.
 
Cheers,
Subbu.

---

### Post by presence1960 on 2009-11-21
> **Subbu_09 said:**
> Thanks for your understanding. I also do not wish to have multiple threads running as I have to go around and look for replies and remember what I typed where, etc. It is a one-off thing and it will not happen again. It is perfectly right to have only one thread running with all information one can provide, so it will help me and others who try to help figure out the problem / solution pretty quick.
 
Cheers,
Subbu.

No biggie, if that is the worst thing that happens today we are fortunate indeed! Usually a moderator will merge the threads if and when one of them notices such a thing. Just pointing something out so you can get the help you want.

---

### Post by Bartender on 2009-11-21
You asked if the CD HAD to be burned at 4X.  It doesn't.  That's just a nice, safe speed for most computers.  

I have a P4 3 GHz PC, built about 2005 or 2006, that's burned dozens of Linux CD's at 8X (just like you, the NTI software wouldn't go lower) successfully.

Rather than scrutinizing the exact specs of your PC, it's easier to just say "Burn at 4X" since that *should* be a safe speed for any PC built in the last decade or so.

---

### Post by Subbu_09 on 2009-11-21
> **Bartender said:**
> You asked if the CD HAD to be burned at 4X. It doesn't. That's just a nice, safe speed for most computers. 
 
I have a P4 3 GHz PC, built about 2005 or 2006, that's burned dozens of Linux CD's at 8X (just like you, the NTI software wouldn't go lower) successfully.
 
Rather than scrutinizing the exact specs of your PC, it's easier to just say "Burn at 4X" since that *should* be a safe speed for any PC built in the last decade or so.
 
Hi All,
 
I got a new brand of CD-R and used ISO Recorder and burnt the image at 4X speed.
I was hoping to see the LIVE Dekstop CD boot this time without any issues. But no luck. I could not even check the "check CD for defects" menu. I can only do the memory test and also "boot from primary partition" options. If I select and enter all other options, my system restarts. All the help menu items work though. I am still back to the same problem. Like I updated before I verified the MD5 CHECK SUM of the ISO image I downloaded (I downloaded it thru' a download manager - GetRight with multiple resume options, would that be a problem?) and the checksums matched.
 
So, what next should I try? Would the same LIVE CD work without any issues in some other computer?
 
Please help me.
 
Thanks,
 
Subbu.

---

### Post by tommcd on 2009-11-22
> **Subbu_09 said:**
>  I downloaded (I downloaded it thru' a download manager - GetRight with multiple resume options, would that be a problem?) and the checksums matched.
Just to rule out a bad download, try downloading the iso again without using GetRight. And download the iso from different mirror site this time. Then verify the md5sum.
 > **Subbu_09 said:**
> 
So, what next should I try? Would the same LIVE CD work without any issues in some other computer?
 
Well you could certainly try it in a different computer. It would be instructive to learn if it works on a different computer.
If the same live CD works on a different computer, then the computer you are currently using likely has a problem with the Ubuntu live CD.
If the same CD does not work on a different computer, then it is very likely that the CD itself is the problem.
Also try installing from the alternate CD just to rule out a graphics incompatibilty problem with your computer and the live CD. Use the 32 bit (i386) alternate CD for the most fail-safe install. You said in your first post that you were using the i386 CD. Stick with that.
What graphics (intel, nvidia, ati, via) does your computer have?

Also, perhaps try burning a new CD on a different computer to rule out a problem with the CD burner in your current computer.

---

### Post by Subbu_09 on 2009-11-23
> **tommcd said:**
> Just to rule out a bad download, try downloading the iso again without using GetRight. And download the iso from different mirror site this time. Then verify the md5sum.
 
Well you could certainly try it in a different computer. It would be instructive to learn if it works on a different computer.
If the same live CD works on a different computer, then the computer you are currently using likely has a problem with the Ubuntu live CD.
If the same CD does not work on a different computer, then it is very likely that the CD itself is the problem.
Also try installing from the alternate CD just to rule out a graphics incompatibilty problem with your computer and the live CD. Use the 32 bit (i386) alternate CD for the most fail-safe install. You said in your first post that you were using the i386 CD. Stick with that.
What graphics (intel, nvidia, ati, via) does your computer have?
 
Also, perhaps try burning a new CD on a different computer to rule out a problem with the CD burner in your current computer.
 
Thanks Tom for providing different options to solve my problem.
 
The graphics card / driver I use is S3 Graphics Prosavage (Microsoft Corporation).
If the graphics driver is the issue, then can I update this drive for free on-line?
 
With regards to may alternate CD, I have a different issue with the alternate CD.
Because, when I do a check CD for integrity, it fails - and it does not restart my computer. And I am also able to go thru' other options in the menu. But, not able to install it. Also, as I am new to Linux, I am afraid to go for a peramanent install thru' that alternate CD (if it works!). Because, I already have Windows XP and other software on it and I do not want to lose it. I have a partition around 10 GB fully free
to use for Linux. But, I am not sure how I can select it correctly from the alternate CD.
Because, I do not know the commands one would need to know to install Ubuntu thru'
the alternate CD. How about booting it with a LIVE USB drive? Can I get step by step
instructions for that so that I can give that a try.
 
Like you said, I also plan to try one of my LIVE CD's with another computer and also
try to burn the image from a different computer and see if it works in my computer.
 
I guess still a long way to go for me before I see what is there in Ubuntu.........9.10.
 
I will update this thread as and when I make any progress and thanks for your help.
 
Cheers,
Subbu.

---

### Post by phillw on 2009-11-23
Hi Subbu,

Blimey, you've been through the wars ... Sorry to hear you're still having problems.

Try booting a friends computer using the LiveCD in 'try without altering computer mode'. You could also check the md5 on the LiveCD via windows on a diferent machine, along with an iso image. If your iso image is check-summing okay - I'd rule out corruption, except that, in your case, we cannot rule anything out.

Another alternative, is to burn the cd on a different computer - but, for safety - I'd re-load the iso to that computer and check-sum it.

Hope that gives you some options.


If all else fails - I'll burn you one & post it to you - I can get a cd to USA in about 5 working days from the UK - I don't charge postage for people in your situation.


Regards,

Phill.

---

### Post by Subbu_09 on 2009-11-23
> **phillw said:**
> Hi Subbu,
 
Blimey, you've been through the wars ... Sorry to hear you're still having problems.
 
Try booting a friends computer using the LiveCD in 'try without altering computer mode'. You could also check the md5 on the LiveCD via windows on a diferent machine, along with an iso image. If your iso image is check-summing okay - I'd rule out corruption, except that, in your case, we cannot rule anything out.
 
Another alternative, is to burn the cd on a different computer - but, for safety - I'd re-load the iso to that computer and check-sum it.
 
Hope that gives you some options.
 
 
If all else fails - I'll burn you one & post it to you - I can get a cd to USA in about 5 working days from the UK - I don't charge postage for people in your situation.
 
 
Regards,
 
Phill.
 
Phill,
 
Thank you for your support.
 
Actually, I have now dowloaded Ubuntu 8.04 LTS Desktop version and successfully
MD5 check summed it. I use the Windows tool - winMD5Sum - to MD5 check sum
and it shows no error for all 3 ISO files (9.10 desktop / 9.10 alternate and now 8.04).
I will burn this at probably 2X speed(?!) and see if it boots. Because, one of the suggestions I got after failing multiple time with 9.10 was to try with the LTS version of
8.04, which I am doing as the next step. Because, that will let me know if 9.10 doesn't
like my hardware OR the issue is only with the CD-Rom OR the CD-Writer drive I am
using.
 
If that also fails, then I have to try the other options that is given here. Try those CD's
with other computers OR get the ISO burnt in another computer and try it.
 
Finally, I guess I have one more option. I have a 4 GB USB drive. Can I use that to
boot it in place of the LIVE CD. I heard that USB drives can also be tried to boot them
as LIVE USB's, with appropriate BIOS setting changes. And if I can boot into the USB,
then I guess I can also install Ubuntu permanently on the same drive as I have seen
others post in this forum.
 
I am running Windows XP. So, I would prefer to have a step-by-step approach to
using the USB drive as a LIVE CD and then for a permanent install of Ubuntu.
 
Thank you once again.
 
Regards,
Subbu.

---

### Post by presence1960 on 2009-11-23
just want to add that the Live CD will not work on every machine for one reason or another. maybe your machine is one of those on which the Live CD will not work.

---

### Post by tommcd on 2009-11-23
> **Subbu_09 said:**
> 
The graphics card / driver I use is S3 Graphics Prosavage (Microsoft Corporation).
If the graphics driver is the issue, then can I update this drive for free on-line? 
 There is a linux graphics driver for your card:
[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)
You can probably get that working in Ubuntu. First though, we have to get you a CD that passes the md5sum check.
> **Subbu_09 said:**
> 
With regards to may alternate CD, I have a different issue with the alternate CD.
Because, when I do a check CD for integrity, it fails - and it does not restart my computer.
I don't know why you are having so much trouble burning a CD that will pass the md5sum check. If you have:
tried using Iso Recorder or Infra Recorder.
tried burning the CD at the slowest possible speed.
tried downloading the iso from a different mirror site.
tried using different CDR media.
then perhaps your CD burner is failing to burn an accurate iso image. Burning an iso image of an operating system is a more exacting task, and less forgiving of errors than burning a music CD or a data CD. This is why we do the md5sum check.
Try burning the iso on a different computer. Also try booting the CDs on different computers and checking the md5sums.
If you just can't manage to produce a valid CD, you can purchase Ubuntu CDs very inexpensively here:
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)
The CDs (not the DVDs) are about 2$ US. 
 > **Subbu_09 said:**
> 
Because, I do not know the commands one would need to know to install Ubuntu thru'
the alternate CD. How about booting it with a LIVE USB drive? Can I get step by step
instructions for that so that I can give that a try.
 
This is why I suggested deleting the F partition from XP first. This will create 10GB free space. Then when you install Ubuntu and get to partitioning, choose manual partitioning and create 2 logical partitions in the free space that was created when you deleted the F drive (partition) from XP:
9GB for root
1GB for swap
Here is a good guide for installing from the alternate CD.
[http://members.iinet.net.au/~herman546/p3.html](http://members.iinet.net.au/~herman546/p3.html)
It covers a different partitioning scenario than what you have. The basic parts of the install are similar though.
Here is a guide for the live CD:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by presence1960 on 2009-11-23
> **tommcd said:**
> there is a linux graphics driver for your card:
[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)
you can probably get that working in ubuntu. First though, we have to get you a cd that passes the md5sum check.

I don't know why you are having so much trouble burning a cd that will pass the md5sum check. If you have:
Tried using iso recorder or infra recorder.
Tried burning the cd at the slowest possible speed.
Tried downloading the iso from a different mirror site.
Tried using different cdr media.
Then perhaps your cd burner is failing to burn an accurate iso image. Burning an iso image of an operating system is a more exacting task, and less forgiving of errors than burning a music cd or a data cd. This is why we do the md5sum check.
Try burning the iso on a different computer. Also try booting the cds on different computers and checking the md5sums.
If you just can't manage to produce a valid cd, you can purchase ubuntu cds very inexpensively here:
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)
the cds (not the dvds) are about 2$ us. 
 
 
This is why i suggested deleting the f partition from xp first. This will create 10gb free space. Then when you install ubuntu and get to partitioning, choose manual partitioning and create 2 logical partitions in the free space that was created when you deleted the f drive (partition) from xp:
9gb for root
1gb for swap
here is a good guide for installing from the alternate cd.
[http://members.iinet.net.au/~herman546/p3.html](http://members.iinet.net.au/~herman546/p3.html)
it covers a different partitioning scenario than what you have. The basic parts of the install are similar though.
Here is a guide for the live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

+1

---

### Post by phillw on 2009-11-23
If your BIOS supports USB booting, then using a usb boot would completely eliminate all the CD issues.  Some BIOS's do, and some don't. If your BIOS does support USB booting, then you can use either

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Who's system I know works, or you can use

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Both methods work, it is just a matter of I found pendrivelinux before I found unetbootin, so I use that one. (I'm probably in the massive minority here - lol)

There are a multitude of little gremlins that can cause problems, from the write laser-led being on it's way out - they have a finite life, which is surprisingly low. To a loose lead, to a dry solder joint  - all things have happened in the past and we ignore them at our peril !

Getting the cd ordered and being patient for delivery is certainly an option, or as I've already said - I'll burn & post one to you - delivery times are probably similar - although theirs will have the advantage of being a stamped cd-rom, as opposed to a cd-r from me. There is, however, no harm in trying both methods :D

If your system supports usb booting, you can also order a real cool 4GB usb drive, with 9.10 on it from here ....

[http://shop.canonical.com/product_info.php?products_id=577](http://shop.canonical.com/product_info.php?products_id=577)

I'm really looking forward to seeing this thread marked as [solved] - It's a real shame you are having so much grief.  (They call it 'character building' -- I call it a pain in the *** - lol)

Regards,

Phill.

---

### Post by Subbu_09 on 2009-11-24
Hi All,
 
Thanks for all your continuous support in getting my issue resolved and like all of you have mentioned, I am going to try all these different options given here (by the way, I have already requested for an official Ubuntu CD from their "shipit" site, and I hope to get that soon) and update this post as I make progress. Though, it would have taken  a little too longer for me to figure out, I am slowly trying all the options given here one by one and I am sure that I will hit Gold one day, very soon hopefully though.
 
First I will try the Live CD options, then go for the USB option and then try with the official Live CD. And also, the driver update suggestion given here. I guess I have all bases covered so far as solution options are concerned and the only thing is, I should try them out one by one and find out which one works and which ones doesn't.
 
I also would to see this thread marked as SOLVED pretty soon. However, the struggle I seem to have in getting it work would be a lesson or guidance for all others who may be having similar issues - if they not posted threads for that - and I hope would be eagerly watching my posts and the suggestions I get here.
 
Thanks again guys for all your support and I look forward to updating you with any progress I make, pretty soon.
 
Thanks and regards,
Subbu.

---

### Post by Subbu_09 on 2009-11-24
> **tommcd said:**
> There is a linux graphics driver for your card:
[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)
You can probably get that working in Ubuntu. First though, we have to get you a CD that passes the md5sum check.

I don't know why you are having so much trouble burning a CD that will pass the md5sum check. If you have:
tried using Iso Recorder or Infra Recorder.
tried burning the CD at the slowest possible speed.
tried downloading the iso from a different mirror site.
tried using different CDR media.
then perhaps your CD burner is failing to burn an accurate iso image. Burning an iso image of an operating system is a more exacting task, and less forgiving of errors than burning a music CD or a data CD. This is why we do the md5sum check.
Try burning the iso on a different computer. Also try booting the CDs on different computers and checking the md5sums.
If you just can't manage to produce a valid CD, you can purchase Ubuntu CDs very inexpensively here:
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)
The CDs (not the DVDs) are about 2$ US. 
 
 
This is why I suggested deleting the F partition from XP first. This will create 10GB free space. Then when you install Ubuntu and get to partitioning, choose manual partitioning and create 2 logical partitions in the free space that was created when you deleted the F drive (partition) from XP:
9GB for root
1GB for swap
Here is a good guide for installing from the alternate CD.
[http://members.iinet.net.au/~herman546/p3.html]("http://members.iinet.net.au/%7Eherman546/p3.html")
It covers a different partitioning scenario than what you have. The basic parts of the install are similar though.
Here is a guide for the live CD:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Hi Tom, Phill and all others,

Let me start with the word SUCCESS...........SUCCESS.........SUCCESS.......... as I was able to successfully use the LIVE CD now, at this very moment and in fact posting this update from my Live Ubuntu 9.10 desktop from the default Firefox browser........
If any one is wondering what made this work, it is simple. Like Tom and others suggested, there is an issue with my CD-RW drive, which is about 4 years old now and it is not capable of burning an ISO image any more into a CD-R. So, I burnt the ISO image from a different computer, that obviously has a different CD-RW drive and it worked wonders for me. In fact, I should say it was a simple solution in the end.

So, as we found in my case, there is nothing wrong with the brand of CD-R's I was using, or the ISO files I was using (because, they all passed the MD5 checksum test) and not with the computer hardware I am using (by the way, mine is a Intel 1.7 MHz celeron processor with 512 MB RAM, built about 5 years ago....) or the video driver, OR the CD- image burning software I was using (The CD that I was able to successfully LIVE boot was burnt from a Nero burner....). It is only the CD-RW drive that was the culprit. That made me go crazy and I burnt about 5 CD's with different makes, with different CD burning software and with different speeds (by the way, the one that is successful now was burnt at 8X speed, which is the lowest speed with Nero burner).

Anyway, it is a great experience figuring out where the issue finally was. So, I do not have to try the only other option, which is using my USB disk as a LIVE boot CD (which I would like to try little later though after going thru' what is actually there in Ubuntu 9.10).

Once again, thanks for every one who helped me with their bit and to Phill who was even ready to ship a Live CD for me free of cost. I appreciate your gesture......

Thanks and thanks and thanks to all....

Regards,
Cheers.
Subbu.

P.S. I will mark this thread as SOLVED after hearing any comments from you guys today.

---

### Post by tommcd on 2009-11-25
> **Subbu_09 said:**
> 
Let me start with the word SUCCESS... as I was able to successfully use the LIVE CD now, at this very moment and in fact posting this update from my Live Ubuntu 9.10 desktop from the default Firefox browser........

Glad you finally were able to burn a good CD and boot to the Ubuntu desktop. Welcome to Ubuntu!
So have you tried to install Ubuntu to any computer yet? Or are you just running with the live CD?

Here is a good site for getting started with Ubuntu. It also covers installing from the live CD in detail:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

If you plan to keep using the computer you mentioned in your first post, and if you can get Ubuntu installed on it and running ok, you would see a significant performance increase if you added more memory to the computer. The 512mb memory you have in that computer is (unfortunately) about the minimum amount of memory to run the Ubuntu desktop with any kind of decent performance. This is especially true when running off the live CD, since it runs entirely in memory. Upgrading the memory to 1GB would give you the best bang for your buck. More memory would be better if you plan to keep using the system into the future.
Adding more memory would also improve the performance of Windows XP as well, since 512mb is about the minimum for decent performance in XP also.

---

### Post by Subbu_09 on 2009-11-25
> **tommcd said:**
> Glad you finally were able to burn a good CD and boot to the Ubuntu desktop. Welcome to Ubuntu!
So have you tried to install Ubuntu to any computer yet? Or are you just running with the live CD?
 
Here is a good site for getting started with Ubuntu. It also covers installing from the live CD in detail:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
 
If you plan to keep using the computer you mentioned in your first post, and if you can get Ubuntu installed on it and running ok, you would see a significant performance increase if you added more memory to the computer. The 512mb memory you have in that computer is (unfortunately) about the minimum amount of memory to run the Ubuntu desktop with any kind of decent performance. This is especially true when running off the live CD, since it runs entirely in memory. Upgrading the memory to 1GB would give you the best bang for your buck. More memory would be better if you plan to keep using the system into the future.
Adding more memory would also improve the performance of Windows XP as well, since 512mb is about the minimum for decent performance in XP also.
 
Thanks for the advice Tom. In fact, I plan to upgrade, rather replace my current system into a better one with latest processors and RAM. I should be able to do that
pretty soon and if it is going to be delayed, then I will definitely upgrade at least my RAM to improve performance of both Ubuntu and my Windows XP.
 
Like you said, I also burnt a 8.04 LTS LIVE CD from the same machine and tried to run at my machine. It passed the CD integrity check, but showed an error message
like "running at safe graphics mode" or something and presented me with the following options  CONFIGURE - CANCEL - CONTINUE. Nothing happened after Clicking "continue" and "configure" (the configure button gave me options to select the monitor type, resolution etc.) buttons.  But it went to a total BLACK BLANK screen after that.
Are there any reasons for that? As I updated earlier, my 9.10 live CD worked just fine
without any issues with the monitor or display.
 
Can you guide me in that? OR should I post a separate thread with its own title, I can
do that.
 
And with regards to permanently installing Ubuntu, I have seen 3 options (not 4 - because, I am yet to burn the Alternate CD from the machine that successfully burnt my other two LIVE CD's). That is, install from Windows XP - I get a pop-up when I load this CD into the drive while running XP and install from the desktop when Ubuntu LIVE CD is running and finally choosing the "install ubuntu" option from the LIVE CD menu. I am not sure which one would be good and easy for me to install.
 
Like I said before, I can spare a full 10 GB partition for running Ubuntu 9.10 permanently in my system. Also, I need a dual boot menu option after installation.
 
Can you give me the steps for that OR should I post this also as a separte thread.
 
Thanks again for all your help.
 
Regards,
Subbu.

---

### Post by phillw on 2009-11-25
Yay !! :D

You've been through the mill on this one. Glad you have a Good CD - The one I made for you is now sat awaiting anyone else who may need it.

For dual booting, a really good set of instructions can be found here -->  [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)   Don't worry about the references to earlier Ubuntu installations, the method of prepping your system is version independent.

10GB is a nice size to start with (I used that) -- 9GB of Ubuntu and 1GB of SWAP.

Some windows installations get the REAL hump when you resize partitions - So, I'd suggest shrinking the windows area and letting it get used to the fact it no longer rules the world (this can take a couple of reboots) BEFORE you proceed to install Ubuntu. A happy windows system just makes Grub2's life a whole lot easier when it is looking after Ubuntu and Win ;-)

As you have found, any of us will give you a helping hand on your journey to using Ubuntu. Give it a couple of months and you'll be querying how to shrink your Win area as you hand over day to day control over to Ubuntu. 

Now, just in case your booting system gets all confused - It won't happen if you follow the instructions but I do like to have a Plan B ... [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Remember you MUST take a backup of your data before you go slicing your hard disk - It has never failed on me, but if you do not have a backup then Murphy's Law will invoke itself & bite you in the bum.

Regards,

Phill.

---

### Post by tommcd on 2009-11-26
> **Subbu_09 said:**
> 
Like you said, I also burnt a 8.04 LTS LIVE CD ... but showed an error message like "running at safe graphics mode" ... 
Are there any reasons for that? ... my 9.10 live CD worked just fine
without any issues with the monitor or display. 

This is likely due to improvements in the driver your video card uses. I think the S3 Pro Savage uses the 
xserver-xorg-video-openchrome driver in Ubuntu since it is made by VIA. That driver is included in a standard Ubuntu install and should load automatically for you.
 > **Subbu_09 said:**
> 
And with regards to permanently installing Ubuntu, I have seen 3 options (not 4 - because, I am yet to burn the Alternate CD from the machine that successfully burnt my other two LIVE CD's). That is, install from Windows XP - I get a pop-up when I load this CD into the drive while running XP ... 
This is likely referring to **wubi**, which is a method of installing Ubuntu inside Windows XP. I would recommend not using that. Install Ubuntu the real way to a dedicated partition.
> **Subbu_09 said:**
> 
... and install from the desktop when Ubuntu LIVE CD is running and finally choosing the "install ubuntu" option from the LIVE CD menu. I am not sure which one would be good and easy for me to install. 
Installing from the live CD menu, and installing from the "install Ubuntu" icon from the running live CD will produce the same installer. The difference is that installing Ubuntu from the menu wont have the full Ubuntu desktop running. This would be a good option for you with only 512mb memory. See this guide from the site I linked to earlier:
 [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
> **Subbu_09 said:**
> 
Like I said before, I can spare a full 10 GB partition for running Ubuntu 9.10 permanently in my system. Also, I need a dual boot menu option after installation.
 
Since you have 4 partitions of 10GB each it may be difficult for you to tell them apart in the Ubuntu installer. Linux will not call them C,D,E, and F drives. They will be called /dev/sda1, /dev/sda2, etc. This is why I suggested deleting the F partition from Windows disk management utility first. It should be easy for you to identify free space on the drive as separate from the other partitions on them that you want to keep since it will be labled "unallocated space" or something like that.
Choose manual partitioning and setup 2 logical partitions: a 9GB root and a 1GB swap, then proceed with the install. This site covers dual booting in great detail:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

### Post by Bartender on 2009-11-26
I'd be keeping an eye out for a sale on a new DVD burner too.
Might as well get it out of there.  Know any geeks?  If someone doesn't have a spare drive to give you, DVD-RW's are incredibly cheap.
I remember paying over $100 for my first CD-RW drive.  Sheesh.

---

### Post by Subbu_09 on 2009-11-26
> **tommcd said:**
> This is likely due to improvements in the driver your video card uses. I think the S3 Pro Savage uses the 
xserver-xorg-video-openchrome driver in Ubuntu since it is made by VIA. That driver is included in a standard Ubuntu install and should load automatically for you.
 
This is likely referring to **wubi**, which is a method of installing Ubuntu inside Windows XP. I would recommend not using that. Install Ubuntu the real way to a dedicated partition.
 
Installing from the live CD menu, and installing from the "install Ubuntu" icon from the running live CD will produce the same installer. The difference is that installing Ubuntu from the menu wont have the full Ubuntu desktop running. This would be a good option for you with only 512mb memory. See this guide from the site I linked to earlier:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
Since you have 4 partitions of 10GB each it may be difficult for you to tell them apart in the Ubuntu installer. Linux will not call them C,D,E, and F drives. They will be called /dev/sda1, /dev/sda2, etc. This is why I suggested deleting the F partition from Windows disk management utility first. It should be easy for you to identify free space on the drive as separate from the other partitions on them that you want to keep since it will be labled "unallocated space" or something like that.
Choose manual partitioning and setup 2 logical partitions: a 9GB root and a 1GB swap, then proceed with the install. This site covers dual booting in great detail:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
 
Hi Tom,
 
For the video display issue with 8.04 LTS live desktop CD, then are you saying that, my system won't support booting into that live cd because of having an advanced
graphic card or driver? I thought 8.04 LTS should work with all systems as 9.10 may fail with some systems, like you said before. I do not have an issue with loading
the desktop for 9.10 version, however, I wanted to know if there is a way I can fix the issue, if any, OR change any display parameters from the screen that is presented to
me to make even 8.04 LTS also boot into my desktop? Please clarify.
 
And with regards to dedicating a separate partition and having a dedicated install
(not thru' wubi installer within the C drive in Windows), I too like the idea as I am more for performance of both the operating systems when I run them individually,
considering the lower hardware configuration I have in my machine. So, I would like
to try the option of installing ubuntu into one of the free partitions in my machine from the Live CD's boot menu. However, I wanted to clarify the following.
 
1. After using a separate partition for Ubuntu, will I still be able to get the dual-boot
menu for windows XP and Ubuntu 9.10?
 
2. My Windows free partition drive F is in FAT 32 file system. Should I format it and
simply delete it from windows so that Ubuntu can detect it during installation OR should
I change the File system to EXT2/EXT3/EXT4(?) that is supported by Linux OS's?
 
3. Also, without actually deleting it, for easy identification purposes, within Windows,
I can rename the free partition with 10 GB as something easily identifiable instead
of the standard E and F or New Volume. Like Ubuntu 9.0 OR Live Ubuntu etc., so that
when I use the Boot CD to install Ubuntu, I will be able to select the free drive I want
Ubuntu to be installed. Is this a good idea OR I should simply delete it and look for the
unpartitioned drive for Ubuntu to detect and install it?
 
4. Finally, the 9 GB for root and 1 GB swap you mentioned, can you please explain it a
bit more? Is the Root going to be used for All the programs I may installing when running Ubuntu? And what about this 1 GB swap partition? what is it going to be used
for? Is it for storing any temporary files OR will it double-up with my RAM/ Please clarify.
 
Thanks once again Tom for you suggestions.
 
Regards,
Subbu.

---

### Post by sandy8925 on 2009-11-26
Tip : Don't do anything else while burning the CD. Quit all extra applications and background programs, insert a fresh blank cd and burn it a medium speed (not a fast speed but not too slow - you can be slower if you want to). While it's burning don't use the comp. Just leave it alone and patiently wait for it to burn. That way you're not interfering with the burning process. You should do this especially on slower computers.

---

### Post by sandy8925 on 2009-11-26
If you're able to get it on a pendrive and boot from it then that will be great since it will work faster and install faster too. (I just installed mine this afternoon and it was damn fast while doing a clean install.)

---

### Post by tommcd on 2009-11-27
> **Subbu_09 said:**
> 
For the video display issue with 8.04 LTS live desktop CD, then are you saying that, my system won't support booting into that live cd because of having an advanced
graphic card or driver? 
What I meant was that there have likely been improvements to the openchrome driver in Ubuntu 9.10 compared to 8.04. If you get a better graphical display with 9.10 then I would use that. Ubuntu 9.10 will have newer versions of programs and some new features too.
 > **Subbu_09 said:**
> 
And with regards to dedicating a separate partition and having a dedicated install ...
1. After using a separate partition for Ubuntu, will I still be able to get the dual-boot
menu for windows XP and Ubuntu 9.10? 
 Yes, you should see options for booting Ubuntu or Windows when the grub menu loads. If you don't, then run:
```
sudo update-grub
```
from the terminal in Ubuntu to update the grub menu.
> **Subbu_09 said:**
> 
2. My Windows free partition drive F is in FAT 32 file system. Should I format it and
simply delete it from windows so that Ubuntu can detect it during installation OR should
I change the File system to EXT2/EXT3/EXT4(?) that is supported by Linux OS's? 
You could use **GParted** on the Ubuntu live CD to format the partition as ext4. That way it should be easy to tell the difference between the Windows NTFS partitions and the linux partition from the Ubuntu partitioning setup. I just suggested deleting the F partition to make it easy for you to pick the correct partition when you run manual partitioning in the Ubuntu install.
 
 > **Subbu_09 said:**
> 
3. Also, without actually deleting it, for easy identification purposes, within Windows,
I can rename the free partition with 10 GB as something easily identifiable ...
 Is this a good idea OR I should simply delete it and look for the
unpartitioned drive for Ubuntu to detect and install it?
 
Remeber, linux won't use the name you give the F partition in Windows. In linux the partitions are called: /dev/sda1, /dev/sda2, etc. But a deleted partition will be free space, so it will be easier for you to tell the difference.
> **Subbu_09 said:**
> 
4. Is the Root going to be used for All the programs I may installing when running Ubuntu? And what about this 1 GB swap partition? 

Yes, root is for all programs and system files. Your home partition will also be there for storing data. Ideally, you can have a separate home partition for your data. With only 10GB, you really don't have much room for that though.
Swap is like virtual memory in Windows. It uses some hard drive space to "swap out" stuff from memory. With 512mb memory you will need a swap partition.

---

### Post by Subbu_09 on 2009-11-27
> **sandy8925 said:**
> Tip : Don't do anything else while burning the CD. Quit all extra applications and background programs, insert a fresh blank cd and burn it a medium speed (not a fast speed but not too slow - you can be slower if you want to). While it's burning don't use the comp. Just leave it alone and patiently wait for it to burn. That way you're not interfering with the burning process. You should do this especially on slower computers..
 
Thanks for your tip. As I updated in the post before, I was able to finally get my Live CD burnt from another machine that has a good CD-RW drive with a perfect LENS and got my first LIVE Ubuntu 9.10 desktop a couple of days back.....
 
Cheers.

---

### Post by Subbu_09 on 2009-11-27
> **sandy8925 said:**
> If you're able to get it on a pendrive and boot from it then that will be great since it will work faster and install faster too. (I just installed mine this afternoon and it was damn fast while doing a clean install.)
 
Hi,
 
Do you mean to say that you booted from your PEN drive (USB) the LIVE version of Ubuntu desktop 9.10 version and from there, installed it on the same PEN
drive (OR installed into your hard disk drive)?. Please clarify.
 
If you say that you have installed it permanently on the PEN drive, then I would like to know the steps for that as well, as I have a 4 GB USB flash drive and I can install Ubuntu and other applications permanently on it and carry it with me wherever I go....
 
Thanks.

---

### Post by Subbu_09 on 2009-11-27
> **tommcd said:**
> What I meant was that there have likely been improvements to the openchrome driver in Ubuntu 9.10 compared to 8.04. If you get a better graphical display with 9.10 then I would use that. Ubuntu 9.10 will have newer versions of programs and some new features too.
 
Thanks. But, I was interested to know if I will be able to boot with my LIVE 8.04 LTS CD. Because, I want to see how the desktop looked at that time though, I have a working version of 9.10 Live CD. Is there anything I can do to boot into 8.04 LIVE CD?
especially, with the monitor issue I mentioned..
 
Yes, you should see options for booting Ubuntu or Windows when the grub menu loads. If you don't, then run:
```
sudo update-grub
```
from the terminal in Ubuntu to update the grub menu.
 
To run this command in a terminal, I should have Ubuntu running right?. But, when I don't see it under the boot menu, how can I run the command. Please pardon me if my question seems silly.
 
In other words, after I install Ubuntu permanently in one of the drives and reboot the system, I should be presented with the dual-boot menu with Win XP at the top and
Ubuntu next to it right? And if not, how can I boot into my Ubuntu. That is what I wanted to know. Because, I will not have the terminal available in Windows XP.......
 
You could use **GParted** on the Ubuntu live CD to format the partition as ext4. That way it should be easy to tell the difference between the Windows NTFS partitions and the linux partition from the Ubuntu partitioning setup. I just suggested deleting the F partition to make it easy for you to pick the correct partition when you run manual partitioning in the Ubuntu install.
 
I think I will go with the option of deleting the F drive and then installing Ubuntu and select manual partitioning during set up to avoid any confusions.
 
 
Remeber, linux won't use the name you give the F partition in Windows. In linux the partitions are called: /dev/sda1, /dev/sda2, etc. But a deleted partition will be free space, so it will be easier for you to tell the difference.
 
Okay thanks. By the way, after installing Ubuntu and when I am running Win XP, how will this F drive look like in Windows. Because I would have installed Ubuntu in it and
will the files that are compatible with windows can be accessed from my Win Xp?
 
Yes, root is for all programs and system files. Your home partition will also be there for storing data. Ideally, you can have a separate home partition for your data. With only 10GB, you really don't have much room for that though.
Swap is like virtual memory in Windows. It uses some hard drive space to "swap out" stuff from memory. With 512mb memory you will need a swap partition.
 
So, I should expect options to type (in GB or MB) to allocate for the Root / Home / Swap partitions during the manual partition selection steps in the Live CD?
 
Thanks.

---

### Post by Subbu_09 on 2009-11-27
> **tommcd said:**
> What I meant was that there have likely been improvements to the openchrome driver in Ubuntu 9.10 compared to 8.04. If you get a better graphical display with 9.10 then I would use that. Ubuntu 9.10 will have newer versions of programs and some new features too.
 
Yes, you should see options for booting Ubuntu or Windows when the grub menu loads. If you don't, then run:
```
sudo update-grub
```
from the terminal in Ubuntu to update the grub menu.
 
You could use **GParted** on the Ubuntu live CD to format the partition as ext4. That way it should be easy to tell the difference between the Windows NTFS partitions and the linux partition from the Ubuntu partitioning setup. I just suggested deleting the F partition to make it easy for you to pick the correct partition when you run manual partitioning in the Ubuntu install.
 
 
Remeber, linux won't use the name you give the F partition in Windows. In linux the partitions are called: /dev/sda1, /dev/sda2, etc. But a deleted partition will be free space, so it will be easier for you to tell the difference.
 
Yes, root is for all programs and system files. Your home partition will also be there for storing data. Ideally, you can have a separate home partition for your data. With only 10GB, you really don't have much room for that though.
Swap is like virtual memory in Windows. It uses some hard drive space to "swap out" stuff from memory. With 512mb memory you will need a swap partition.
 
> **Subbu_09 said:**
> So, I should expect options to type (in GB or MB) to allocate for the Root / Home / Swap partitions during the manual partition selection steps in the Live CD?
 
Thanks.
 
Hi Tom,
 
I guess there was an issue with my multi-quote response above. They are not appearing under different color to distinguish from your post. Please find my replies to your previous post inside of your thread above and update.
 
Thanks.

---

### Post by Subbu_09 on 2009-11-27
> **phillw said:**
> Yay !! :D
 
You've been through the mill on this one. Glad you have a Good CD - The one I made for you is now sat awaiting anyone else who may need it.
 
For dual booting, a really good set of instructions can be found here --> [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm) Don't worry about the references to earlier Ubuntu installations, the method of prepping your system is version independent.
 
10GB is a nice size to start with (I used that) -- 9GB of Ubuntu and 1GB of SWAP.
 
Some windows installations get the REAL hump when you resize partitions - So, I'd suggest shrinking the windows area and letting it get used to the fact it no longer rules the world (this can take a couple of reboots) BEFORE you proceed to install Ubuntu. A happy windows system just makes Grub2's life a whole lot easier when it is looking after Ubuntu and Win ;-)
 
As you have found, any of us will give you a helping hand on your journey to using Ubuntu. Give it a couple of months and you'll be querying how to shrink your Win area as you hand over day to day control over to Ubuntu. 
 
Now, just in case your booting system gets all confused - It won't happen if you follow the instructions but I do like to have a Plan B ... [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
Remember you MUST take a backup of your data before you go slicing your hard disk - It has never failed on me, but if you do not have a backup then Murphy's Law will invoke itself & bite you in the bum.
 
Regards,
 
Phill.
 
Hi Phill,
 
Thank you for your responses and I am sure your CD will be useful now for some one
who has the same issue as me and unable to get a LIVE CD working even after multiple attempts.
 
Now, with regards to me getting a permanent Ubuntu install on my computer,
I have seen mixed opinions on using a WUBI installer to install Ubuntu 9.10 inside my
Windows XP C drive and then see how it performs OR uninstall it if I don't like it
(which I don't think will be case) OR if I have problems with either these OS's AND installing it permanently on another dedicated parition for Ubuntu in the same hard disk? I am not able to decide one way or the other. Can you advise the right thing for a Linux starter like me?
 
With regards to resizing and shrinking partitions, I can spare one of the four 10 GB partitions I have for Windows XP. And if I can spare one such partition fully for Ubutnu, should I worry about RESIZING partitions OR SHRINKING my windows partition later? Please clarify.
 
I must admit that for a starter like me, there is actually too much stuff available on the internet along with the help I get from in this forum and that is kind of confusing me
some times. Because, I am not able to quickly decide and follow one advise or another.
 
And one question is, after installing Ubuntu and running windows XP, for any reason
if I want to use the partiition alloted for Ubuntu to be used once again for Windows,
then would I be able to get it back. LIke format it using Win XP format option
back to FAT 32 or NTFS file systems. I wanted to be sure about this before I proceed.
The main worry is not to lose a part of my hard disk because of something going
wrong with the partitiioning or installing of Ubuntu.
 
Thanks,
Subbu.

---

### Post by Bartender on 2009-11-27
> **Subbu_09 said:**
> With regards to resizing and shrinking partitions, I can spare one of the **four** 10 GB partitions I have for Windows XP. 

Well, I see a problem right there.  The maximum number of partitions you can stuff onto a HDD is 4 and 0, or 3 and 1.  That's 4 primary partitions and 0 extended partition, or 3 primary partitions and one extended.

However.  There's a trick to the above statement.  Once you've made an extended partition, you can create several logical partitions inside the extended partition.  Way I understand it, extended partitions came into being to address the "four primary partitions" limitation.

This is a concept that's really quite simple, but people struggle with it all the time until they get a picture in their heads.

So if you have four primary partitions (I'm guessing that's exactly what's going on) you need to get rid of at least one, preferably two, and create an extended partition in the open space.

When I first started partitioning, I tried to stick with primary partitions because I imagined that I understood those better.  Now I try to keep primary partitions to one, then build a big old extended partition that can house several logical partitions.

Think of an extended partition as a box.  Really, that's all it is.  An extended partition isn't formatted as NTFS or ext4.  It's just a box.  You can fill the box with logical partitions.  Logical partitions must be formatted with a file system, just like primary partitions.

Windows needs a primary partition to boot from.  The OS has to be installed to a primary partition or it won't function.  After that you're free to put everything else inside an extended partition.  Windows can *access* logical partitions inside an extended as long as they're NTFS or FAT.  

Linux is less fussy than Windows.  It can boot from a logical partition.

If you have four primary partitions, and you get rid of one of them, create an extended partition from that space and install Ubuntu.  The Ubuntu installer *may* be smart enuf to do that for you.  You'll know if it's not because it'll throw error messages.

---

### Post by Subbu_09 on 2009-11-27
> **Bartender said:**
> Well, I see a problem right there. The maximum number of partitions you can stuff onto a HDD is 4 and 0, or 3 and 1. That's 4 primary partitions and 0 extended partition, or 3 primary partitions and one extended.
 
However. There's a trick to the above statement. Once you've made an extended partition, you can create several logical partitions inside the extended partition. Way I understand it, extended partitions came into being to address the "four primary partitions" limitation.
 
This is a concept that's really quite simple, but people struggle with it all the time until they get a picture in their heads.
 
So if you have four primary partitions (I'm guessing that's exactly what's going on) you need to get rid of at least one, preferably two, and create an extended partition in the open space.
 
When I first started partitioning, I tried to stick with primary partitions because I imagined that I understood those better. Now I try to keep primary partitions to one, then build a big old extended partition that can house several logical partitions.
 
Think of an extended partition as a box. Really, that's all it is. An extended partition isn't formatted as NTFS or ext4. It's just a box. You can fill the box with logical partitions. Logical partitions must be formatted with a file system, just like primary partitions.
 
Windows needs a primary partition to boot from. The OS has to be installed to a primary partition or it won't function. After that you're free to put everything else inside an extended partition. Windows can *access* logical partitions inside an extended as long as they're NTFS or FAT. 
 
Linux is less fussy than Windows. It can boot from a logical partition.
 
If you have four primary partitions, and you get rid of one of them, create an extended partition from that space and install Ubuntu. The Ubuntu installer *may* be smart enuf to do that for you. You'll know if it's not because it'll throw error messages.
 
Hi,
 
I am not sure if my post was very clear. I do have only one primary partition and
1 extended partition, in which I have 3 logical partitions. So, I said totally 4 including those logical ones. Hope this is clear. So, like you said I should not be having any problems with using one of those logical partitions to permanently install Ubuntu along with Windows XP, which is in fact in the primary partition C: drive - making it a dual bootable system.
 
Anyway, thank you for shedding more lilght on partitions, primary, extended and logical drives. For convenience, most of us refer logical drives in extended partition also as one of the partition. Going forward, all should try to correct that so that we can be on the same platform when discussing issues OR offering solution.
 
Fine, with regards to your starting point about any disk can have only 4 primary partitions, assuming I o have 4 primary partiitions and have Windows XP running in one of them (C drive), won't I be able to install Ubuntu on any one of the 3 remaining
primary partitions? Becuase, like you said, Linux should be good enough run either
on Primary or in the logical drives of any extended partition right?
 
Please clarify.
 
Thanks.
Subbu

---

### Post by tommcd on 2009-11-28
> **Subbu_09 said:**
> 
Fine, with regards to your starting point about any disk can have only 4 primary partitions, assuming I o have 4 primary partiitions and have Windows XP running in one of them (C drive), won't I be able to install Ubuntu on any one of the 3 remaining
primary partitions? 

Yes you will. Since you will need to create 2 logical partitions (9GB root and 1GB swap) just delete the partition that you don't want (the 10GB F partition that you previously stated you wanted to use for Ubuntu). You can do this from Windows or from the partitioning part of the Ubuntu install.
Just choose manual partitioning when you get to that part of the install. Here is a very good guide to manual partitioning from the live CD:
[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

---

### Post by Subbu_09 on 2009-11-28
> **tommcd said:**
> Yes you will. Since you will need to create 2 logical partitions (9GB root and 1GB swap) just delete the partition that you don't want (the 10GB F partition that you previously stated you wanted to use for Ubuntu). You can do this from Windows or from the partitioning part of the Ubuntu install.
Just choose manual partitioning when you get to that part of the install. Here is a very good guide to manual partitioning from the live CD:
[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

Hi Tom,

Just to make myself clear that I do have only ONE Primary partition in my machine where Windows XP (in C: drive) is installed and I have ONE Extended partition, in which I have created 3 LOGICAL Partitions and their names are D: , E: , and F: . And what I meant was to allocate the F: drive for my Ubuntu permanent install from the LIVE CD with a dual boot for Windows XP. In this scenario, are you saying that I should definitely DELETE the F: drive, which is only one of the logical drives in my extended partition (and not one of the primary partitions), and then choose this unallocated space during manual parititioning of my Ubuntu install?

Please clarify. I want to be absolutely clear on this before I delete one of my LOGICAL drives in Windows XP.

Thanks.

---

### Post by Bartender on 2009-11-28
OK, sorry, Subbu -
I missed the part about your partitions.  I saw the comment about 4 and jumped to conclusions.
Yeah, as long as everything else is inside the extended "box" you just need to make some room by deleting or resizing.  If you can carve out some space, Ubuntu should even be able to auto-install if that's the way you want to go.

---

### Post by Subbu_09 on 2009-11-28
> **Bartender said:**
> OK, sorry, Subbu -
I missed the part about your partitions.  I saw the comment about 4 and jumped to conclusions.
Yeah, as long as everything else is inside the extended "box" you just need to make some room by deleting or resizing.  If you can carve out some space, Ubuntu should even be able to auto-install if that's the way you want to go.

Hi,

Thanks. 

My idea is, as I have just responded to Tom in this thread before, use one of my 3 logical drives with about 10 GB of free space, in the extended partition, to install Ubuntu.
Can I do that? For that can I just have that free space available and when installing Ubuntu from the LIVE CD, choose the manual partitioning and select this free space?

Also, I learnt from Tom that I should allocate 9 GB for root and 1 GB for swap. Can I select those options manually OR I should only select the SWAP and the rest will be automatically used for the ROOT. Since I do not have more than 10 GB of available space in that logical drive, Tom suggested not to try and create any HOME directory.

Finally, one question. Though I can spare a logical drive with 10 GB space for an exclusive install for Ubuntu, I also see that Ubuntu can be installed inside my Windows,
using the WUBI installer. I am little confused as to which one would be better, performance-wise, for both the operating systems when I run them separately. 

One point I seem to understand very clearly though is, if I am going to allow Ubuntu run within the Windows primary partition (my C: drive), then other than the option of uninstalling it later from the add/remove program menu, I won't be able to install OR use much of the software that Ubuntu freely supports. The reason being, it is installed, rather, sharing the drive space with Windows, where Windows will have its own applications installed. So, I may not enjoy the full features or performance of Ubuntu.
Is that correct?

OR for Linux and Ubuntu starters like me, the best advice would be to use the WUBI installer and have Ubuntu installed within Windows C drive. Wait and see how Ubuntu
performs OR see if there are any issues in any one of these OS, because of this Wubi installer. Then decide if I should choose to install Ubuntu in an exclusive drive - the 10 GB logical drive I can allocate - and dual boot from there.

Please advise as I want to get Ubuntu installed in my machine one way or the other and have the dual boot system with Windows xp. Because, I am tired of booting Ubuntu with the LIVE CD every time I want to and also due to the fact how limited OR some times freezing performance I see due to the limited 512 MB RAM I have.

Thanks for your suggestion.

Regards,
Subbu.

---

### Post by phillw on 2009-11-28
> **Subbu_09 said:**
> Hi,

Thanks. 

My idea is, as I have just responded to Tom in this thread before, use one of my 3 logical drives with about 10 GB of free space, in the extended partition, to install Ubuntu.
Can I do that? For that can I just have that free space available and when installing Ubuntu from the LIVE CD, choose the manual partitioning and select this free space?

Also, I learnt from Tom that I should allocate 9 GB for root and 1 GB for swap. Can I select those options manually OR I should only select the SWAP and the rest will be automatically used for the ROOT. Since I do not have more than 10 GB of available space in that logical drive, Tom suggested not to try and create any HOME directory.

Finally, one question. Though I can spare a logical drive with 10 GB space for an exclusive install for Ubuntu, I also see that Ubuntu can be installed inside my Windows,
using the WUBI installer. I am little confused as to which one would be better, performance-wise, for both the operating systems when I run them separately. 

One point I seem to understand very clearly though is, if I am going to allow Ubuntu run within the Windows primary partition (my C: drive), then other than the option of uninstalling it later from the add/remove program menu, I won't be able to install OR use much of the software that Ubuntu freely supports. The reason being, it is installed, rather, sharing the drive space with Windows, where Windows will have its own applications installed. So, I may not enjoy the full features or performance of Ubuntu.
Is that correct?

OR for Linux and Ubuntu starters like me, the best advice would be to use the WUBI installer and have Ubuntu installed within Windows C drive. Wait and see how Ubuntu
performs OR see if there are any issues in any one of these OS, because of this Wubi installer. Then decide if I should choose to install Ubuntu in an exclusive drive - the 10 GB logical drive I can allocate - and dual boot from there.

Please advise as I want to get Ubuntu installed in my machine one way or the other and have the dual boot system with Windows xp. Because, I am tired of booting Ubuntu with the LIVE CD every time I want to and also due to the fact how limited OR some times freezing performance I see due to the limited 512 MB RAM I have.

Thanks for your suggestion.

Regards,
Subbu.


Ahhhhh.... 512MB ram ....  Sorry, I didn't spot that one.  Tansferring data from Wubi to a Ubuntu area can be done at a later date. Xubuntu is good with small memory and 512 MB is plenty for it. As you'd be running Wubi from within windows, I'm not sure if windows will keep hold of some of your precious RAM. The LiveCD is best used for just doing a check to see if there are any immediate issues with netowrk / wireless audio and visual. Due the speed of CD's they're not going to give you a decent speed - especially with only 512MB. You can use a USB device, even if you cannot boot off a USB device via your BIOS. It will be a lot slower than an install, but a heck of a lot quicker than CD & you'll be able to save settings etc. on it.

xubuntu is happy with Low RAM (256 Mb is about the minumim) - I't also squeeze itself into 1,5GB of hard disk. It's over here --> [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

Phill.

---

### Post by Subbu_09 on 2009-11-28
> **phillw said:**
> Ahhhhh.... 512MB ram .... Sorry, I didn't spot that one. Tansferring data from Wubi to a Ubuntu area can be done at a later date. Xubuntu is good with small memory and 512 MB is plenty for it. As you'd be running Wubi from within windows, I'm not sure if windows will keep hold of some of your precious RAM. The LiveCD is best used for just doing a check to see if there are any immediate issues with netowrk / wireless audio and visual. Due the speed of CD's they're not going to give you a decent speed - especially with only 512MB. You can use a USB device, even if you cannot boot off a USB device via your BIOS. It will be a lot slower than an install, but a heck of a lot quicker than CD & you'll be able to save settings etc. on it.
 
xubuntu is happy with Low RAM (256 Mb is about the minumim) - I't also squeeze itself into 1,5GB of hard disk. It's over here --> [http://www.xubuntu.org/get](http://www.xubuntu.org/get)
 
Phill.
 
Hi Phill,
 
Are you saying that I can not have a stable running Ubuntu 9.10 either within my windows XP partition thru' WUBI OR thru' a dedicated 10 GB logical drive I can allocate for exclusively installing Ubuntu into it, by creating SWAP / ROOT / HOME partitions?
 
If the answer is yes, then that is NOT what I heard from some of the threads from this forum as well as the minimum hardware requirements for running Ubuntu. I only wanted to try Ubuntu 9.10 from the LIVE CD and have it running in my system on a permanent basis. I do understand that I have the lowest advised RAM and I plan to upgrade to 1 GB very soon. But, I guess that should not prevent me from installing Ubuntu in my system and I do not like to go for Xubuntu or other 100's of Linux falvors and versions that are available for free in the internet.
 
What I wanted to know now is, whether I would be able to use one of my logical drives
(in an extended partition) in Windows XP for installing Ubuntu? and whether I should delete that partition first from within Windows and then look to use it during installation of Ubuntu using the LIVE CD or without deleting that logical drive, I can install Ubuntu 9.10 on it using the LIVE CD. Also, what should I select when Ubuntu prompts me for the type of parition - either mark it as PRIMARY or LOGICAL. Because, the space I am going to use is actually a logical drive in my hard disk.
 
Hope I have made my plans clear and expect assistance to complete Ubuntu instalation.
 
Thanks,
Subbu.

---

### Post by Subbu_09 on 2009-12-02
Hi Phill,
 
Any suggestions for my request with regards to installing Ubuntu permanently in one of my Logical drives with Windows XP as the dual boot?
 
By the way, right now, I am trying to create a USB bootable flash drive for Ubuntu 9.10 and if I succeed, I guess I need not have to use the LIVE CD going forward and
I also have the option to save any changes to my desktop as it is said to be a persistent install. 
 
I will post the results shortly......
 
Regards,
Subbu.

---

### Post by Subbu_09 on 2009-12-03
Hi Phill,
 
I have issues with my Ubutnu Live USB install creation process as well. I have posted it on a separate thread. Can you please give your suggestion to fix that issue?
 
Thanks.

---

