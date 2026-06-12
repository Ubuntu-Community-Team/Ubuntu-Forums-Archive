---
title: "Can I use my alternate / text-based Ubuntu 9.10 CD as a Live CD without installing it"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Subbu_09 on 2009-11-15
Hello,
 
I am new to Linux.
 
By mistake, instead of downloading a desktop/Live CD, I downloaded a Alternate / Tex-based CD for an Intel machine. I do not want to waste time downloading a Live CD again. I want to try Ubunty 9.10 with the Alternate CD like a LIVE CD without actually installing it. How can I do that? I have already created the downloaded ISO image as a bootable CD and the CD boots. But, I do not see the option to "install ubuntu without altering my system" option at the top. It starts with the "Install Ubuntu"
in the menu list.
 
Are there any workarounds or shortcut methods to solve my problem. Should I need to download any other addtional files to make this ubuntu-alternate-i3d6.iso CD work?
 
This is a very urgent request as I am currently online and looking for advice.
 
Thanks for your help.
Subbu.

---

### Post by aysiu on 2009-11-15
You can't use the alterate CD as a live CD.

---

### Post by Subbu_09 on 2009-11-20
Hi,
 
Thank you for your response. I got an issue with my desktop LIVE CD as well.
 
I got my Ubuntu desktop LIVE CD burnt today and tried to boot my system with it.
I see the boot options where I can select "try ubuntu without changing my computer".
But, after clicking enter on that menu, nothing happens. My monitor goes to sleep and then system restarts. Once again, I am presented with the same screen. And when I click the option "Boot from my primary hard disk", I am able to boot in my WindowsXP

I do not know what is wrong with it? Is it something wrong with the ISO Image I burnt OR would there be any issues with the downloaded ISO file itself. I used a download manager software (in order to make sure that I am able to RESUME the download later, if the internet connection is slow or if it is lost for a while), GET RIGHT to download the ISO image.

And by the way, should one be downloading a 32-bit file OR a 64-bit file?
 
Can you please help to solve this issue.
 
thanks,
 
Cheers,
Subbu.

---

### Post by presence1960 on 2009-11-20
I would backtrack & start at square 1. 

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded? The hashes must match exactly or the iso is no good. If that is the case try using a torrent to download the iso.

Did you burn the iso as image to disk at no more than 4x-8x speed? If your burning software won't allow you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

When you boot the Live CD choose "check disk for defects" prior to installing Ubuntu.

You may want to look here also: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you have a 64 bit CPU I would say go with 64 bit.

If all else fails you can try the alternate text based installer, get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Subbu_09 on 2009-11-20
> **presence1960 said:**
> I would backtrack & start at square 1. 
 
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded? The hashes must match exactly or the iso is no good. If that is the case try using a torrent to download the iso.
 
Did you burn the iso as image to disk at no more than 4x-8x speed? If your burning software won't allow you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.
 
When you boot the Live CD choose "check disk for defects" prior to installing Ubuntu.
 
You may want to look here also: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
If you have a 64 bit CPU I would say go with 64 bit.
 
If all else fails you can try the alternate text based installer, get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")
 
Hi thanks for your response.
 
I did check the MD5 CHECK SUM utility and found the original to be the same with the ISO file I downloaded. So, that ruled out one issue. I will now check the burnt CD as well for its MD5 CHECKSUM values. I burnt the CD with 8x speed using my Nero burner and the CD is a brand new one. So, I guess there should not be any issues.
I will try that and let you know if I am able to figure out where the issue is. I only have a 34 bit PC, so the ISO file I have is the correct one I believe. I will also check the CD for defects.
 
I do not want to go for the TEXT based installer as I want to try Ubuntu with the LIVE CD first and then go for the permanent install, if I feel so.
 
thanks for your help.
 
Cheers,
Subbu.

---

### Post by Subbu_09 on 2009-11-21
> **Subbu_09 said:**
> Hi thanks for your response.
 
I did check the MD5 CHECK SUM utility and found the original to be the same with the ISO file I downloaded. So, that ruled out one issue. I will now check the burnt CD as well for its MD5 CHECKSUM values. I burnt the CD with 8x speed using my Nero burner and the CD is a brand new one. So, I guess there should not be any issues.
I will try that and let you know if I am able to figure out where the issue is. I only have a 34 bit PC, so the ISO file I have is the correct one I believe. I will also check the CD for defects.
 
I do not want to go for the TEXT based installer as I want to try Ubuntu with the LIVE CD first and then go for the permanent install, if I feel so.
 
thanks for your help.
 
Cheers,
Subbu.
 
Hi,
 
I did choose the option in the Alternate CD to check the CD for defects and after some time, it returned a result as "CD integrity check failed". Does this mean that I have an issue with my CD-ROM? Because, I checked the MD5 CHECKSUM for the ISO file I downloaded and the one from Ubuntu website. Both matched.
 
So, what should I do now? Burn the ISO image on a different CD?
 
Also, after burning the CD (I am using Nero burner in Windows XP), How can I verify the MD5 CHECKSUM for this burnt CD? are there any tools available to do it in WinXP?
 
thanks for your help.
 
Cheers,
Subbu.

---

### Post by darkod on 2009-11-21
First see if the CD check of the LiveCD also fails or not.

At what moment exactly is it rebooting? Immediately after you press enter? Or the black background with white ubuntu logo shows for a short file and it reboots after that?

I am asking because I has similar situation, select Try ubuntu and the black screen with the white logo shows for a while, then it reboots. In my case it was video driver problem. It didn't like my integrated video card I guess.

---

### Post by Subbu_09 on 2009-11-21
> **darkod said:**
> First see if the CD check of the LiveCD also fails or not.
 
At what moment exactly is it rebooting? Immediately after you press enter? Or the black background with white ubuntu logo shows for a short file and it reboots after that?
 
I am asking because I has similar situation, select Try ubuntu and the black screen with the white logo shows for a while, then it reboots. In my case it was video driver problem. It didn't like my integrated video card I guess.
 
Hi,
 
Thanks for your response. I will try to burn the LIVE CD again with a different software and see if I am able to try the live cd without changing my system.
 
With regards to rebooting, it happens after I hit enter when the first option - try without changing my computer - option is highlighted in white. It does not show me any black screen or some thing. It simply switches the monitor off and then starts to reboot. Then presents me with the same menu. However, I noticed one thing when it boots into the CD, a timer starting at 29 S on the left of the Language selection screen runs. And it goes on decreasing, like 28, 27, 26 etc. However, I did not see this timer
with the Alternate CD. Is it how it will be for every one with the DESKTOP Live CD?
 
And if my new LIVE CD also fails after it passes the CD integrity check, I mean if my system reboots, then does it mean that I have the problem with my video card or driver. If that is the case, how can I fix that.
 
For your information, I have tried a month back with a Puppy Linux 4.31 Live CD and it booted without any issues. So, I am hoping that Ubuntu Linux should not have any issues with my video card or driver. I may be wrong as well.......
 
Thanks,
Subbu.

---

### Post by phillw on 2009-11-21
> **Subbu_09 said:**
> Hi,
 
Thanks for your response. I will try to burn the LIVE CD again with a different software and see if I am able to try the live cd without changing my system.
 
With regards to rebooting, it happens after I hit enter when the first option - try without changing my computer - option is highlighted in white. It does not show me any black screen or some thing. It simply switches the monitor off and then starts to reboot. Then presents me with the same menu. However, I noticed one thing when it boots into the CD, a timer starting at 29 S on the left of the Language selection screen runs. And it goes on decreasing, like 28, 27, 26 etc. However, I did not see this timer
with the Alternate CD. Is it how it will be for every one with the DESKTOP Live CD?
 
And if my new LIVE CD also fails after it passes the CD integrity check, I mean if my system reboots, then does it mean that I have the problem with my video card or driver. If that is the case, how can I fix that.
 
For your information, I have tried a month back with a Puppy Linux 4.31 Live CD and it booted without any issues. So, I am hoping that Ubuntu Linux should not have any issues with my video card or driver. I may be wrong as well.......
 
Thanks,
Subbu.

Until you have a CD that passes the integrity check - all efforts are doomed to end in tears. If you integrity check your puppy linux - it will pass - I know that without even checking ;-)

You MUST get a cd that passes integrity. Also, try cleaning the optical drive - the write LED may have a bit of a build up of dirt on it. Burning Data files requires far more accuracy than, say, music or video - 1 byte in the wrong place and it all collapses like a deck of cards. Use decent branded CD-R's and stay away from using CD-RW's. If you are switching over to a free source CD writing package - heck, burn at 2X or even 1X .. The extra time taken to burn is as nothing compared to the time wasted pulling your hair out with a corrupt CD.

If your computer supports booting from USB, then you could always try booting from a usb stick - they're pretty easy to make - you'll need 1GB minimum.

Phill.

---

### Post by Subbu_09 on 2009-11-21
> **phillw said:**
> Until you have a CD that passes the integrity check - all efforts are doomed to end in tears. If you integrity check your puppy linux - it will pass - I know that without even checking ;-)
 
You MUST get a cd that passes integrity. Also, try cleaning the optical drive - the write LED may have a bit of a build up of dirt on it. Burning Data files requires far more accuracy than, say, music or video - 1 byte in the wrong place and it all collapses like a deck of cards. Use decent branded CD-R's and stay away from using CD-RW's. If you are switching over to a free source CD writing package - heck, burn at 2X or even 1X .. The extra time taken to burn is as nothing compared to the time wasted pulling your hair out with a corrupt CD.
 
If your computer supports booting from USB, then you could always try booting from a usb stick - they're pretty easy to make - you'll need 1GB minimum.
 
Phill.
 
Hi Phill,
 
Thanks again. I tried just now with a new brand of CD-R (Sony) and used the ISO Recorder and burnt the image at 4X speed. But no luck. The same issue. I am presented with the boot menu screen with all options and out of them, only the memory test and boot from primary partition work. Of course, the help keys F1.....
But, I am not able to try the other options and when I select them and press enter,
once again, my computer reboots......... Like I said before, I verified the MD5 check sum for my ISO file and it matches.
 
So, what next? Try burning the ISO file again with another software, another brand of CD-R and at another (Lower) speed? I am going crazy and like you said, I had no issues with the Puppy Linux LIVE CD. Why am I having these issues with Ubuntu?
Did any others have the same problem OR am I doing something wrong?
 
Thanks for your assistance.
 
Subbu.

---

### Post by Subbu_09 on 2009-11-22
> **phillw said:**
> Until you have a CD that passes the integrity check - all efforts are doomed to end in tears. If you integrity check your puppy linux - it will pass - I know that without even checking ;-)
 
You MUST get a cd that passes integrity. Also, try cleaning the optical drive - the write LED may have a bit of a build up of dirt on it. Burning Data files requires far more accuracy than, say, music or video - 1 byte in the wrong place and it all collapses like a deck of cards. Use decent branded CD-R's and stay away from using CD-RW's. If you are switching over to a free source CD writing package - heck, burn at 2X or even 1X .. The extra time taken to burn is as nothing compared to the time wasted pulling your hair out with a corrupt CD.
 
If your computer supports booting from USB, then you could always try booting from a usb stick - they're pretty easy to make - you'll need 1GB minimum.
 
Phill.
 
Hi Phill,
 
A quick question. Since my multiple attempts to burn a LIVE CD failed, I now plan to follow your advice of using an USB to boot. I have a 4 GB USB device. Please let me know how I can make a bootable Ubuntu 9.10 USB LIVE disk. And subsequently, can I choose to have a permanent installation on that USB stick itself?
 
Thanks.

---

### Post by Subbu_09 on 2009-11-24
Hi All,

Let me start with the word SUCCESS...........SUCCESS.........SUCCESS......... . as I was able to successfully use the LIVE CD now, at this very moment and in fact posting this update from my Live Ubuntu 9.10 desktop from the default Firefox browser........
If any one is wondering what made this work, it is simple. Like Tom and others suggested, there is an issue with my CD-RW drive, which is about 4 years old now and it is not capable of burning an ISO image any more into a CD-R. So, I burnt the ISO image from a different computer, that obviously has a different CD-RW drive and it worked wonders for me. In fact, I should say it was a simple solution in the end.

So, as we found in my case, there is nothing wrong with the brand of CD-R's I was using, or the ISO files I was using (because, they all passed the MD5 checksum test) and not with the computer hardware I am using (by the way, mine is a Intel 1.7 MHz celeron processor with 512 MB RAM, built about 5 years ago....) or the video driver, OR the CD- image burning software I was using (The CD that I was able to successfully LIVE boot was burnt from a Nero burner....). It is only the CD-RW drive that was the culprit. That made me go crazy and I burnt about 5 CD's with different makes, with different CD burning software and with different speeds (by the way, the one that is successful now was burnt at 8X speed, which is the lowest speed with Nero burner).

Anyway, it is a great experience figuring out where the issue finally was. So, I do not have to try the only other option, which is using my USB disk as a LIVE boot CD (which I would like to try little later though after going thru' what is actually there in Ubuntu 9.10).

Once again, thanks for every one who helped me with their bit and I would try installing Ubuntu permanently little later, either using the LIVE CD or the alternate and post any issues I may have separately at that time.

Thanks and thanks and thanks to all....

Regards,
Cheers.
Subbu.

P.S. I will mark this thread as SOLVED after hearing any comments from you guys today.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8381732") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8381732")

---

