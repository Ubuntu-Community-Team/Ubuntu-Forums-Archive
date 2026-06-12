---
title: "LIVE CD doesn't start after selecting the first option. But system restarts......"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Subbu_09 on 2009-11-20
Hi guys,
 
I got my Ubuntu desktop LIVE CD burnt today and tried to boot my system with it.
I see the boot options where I can select "try ubuntu without changing my computer".
But, after clicking enter on that menu, nothing happens. My monitor goes to sleep and then system restarts. Once again, I am presented with the same screen. And when I click the option "Boot from my primary hard disk", I am able to boot in my WindowsXP
 
I do not know what is wrong with it? Is it something wrong with the ISO Image I burnt OR would there be any issues with the downloaded ISO file itself. I used a download manager software (in order to make sure that I am able to RESUME the download later, if the internet connection is slow or if it is lost for a while), GET RIGHT to download the ISO image.
 
And by the way, should one be downloading a 32-bit file OR a 64-bit file?
 
Can some one help me please.........
 
Thanks.
Cheers
SUBBU.

---

### Post by phillw on 2009-11-20
> **Subbu_09 said:**
> Hi guys,
 
I got my Ubuntu desktop LIVE CD burnt today and tried to boot my system with it.
I see the boot options where I can select "try ubuntu without changing my computer".
But, after clicking enter on that menu, nothing happens. My monitor goes to sleep and then system restarts. Once again, I am presented with the same screen. And when I click the option "Boot from my primary hard disk", I am able to boot in my WindowsXP
 
I do not know what is wrong with it? Is it something wrong with the ISO Image I burnt OR would there be any issues with the downloaded ISO file itself. I used a download manager software (in order to make sure that I am able to RESUME the download later, if the internet connection is slow or if it is lost for a while), GET RIGHT to download the ISO image.
 
And by the way, should one be downloading a 32-bit file OR a 64-bit file?
 
Can some one help me please.........
 
Thanks.
Cheers
SUBBU.

Hi
It sounds like the cd is corrupt. This can be caused by :
1)  Bad ISO image  (checksum it - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) )
2) Burning the CD at too high a speed (Use 4X)
3)  The burnt cd being 'bad' - checksum it as in step 1

As to 32bit / 64nit - that depends on your computer - If you tell me what processor you have, I'll confirm 32 / 64 bit  (32 bit instal will work on 64 bit anyway - but not the other way round)

Regards,

Phill.

---

### Post by darkod on 2009-11-20
What video card do you have?
The same was happening to me with integrated Radeon HD3200, it seems the driver the live CD is trying to use has some issues with some Radeon cards.

---

### Post by Subbu_09 on 2009-11-20
> **phillw said:**
> Hi
It sounds like the cd is corrupt. This can be caused by :
1)  Bad ISO image  (checksum it - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) )
2) Burning the CD at too high a speed (Use 4X)
3)  The burnt cd being 'bad' - checksum it as in step 1

As to 32bit / 64nit - that depends on your computer - If you tell me what processor you have, I'll confirm 32 / 64 bit  (32 bit instal will work on 64 bit anyway - but not the other way round)

Regards,

Phill.
Hi Phil,
 
Thanks for your quick response. I did not do the MD5SUM on the ISO image as I did not know how to run the commands in a terminal. I use Windows XP and the command prompt does not suppor the commands to checksum the MD5 of the ISO image I downloaded. Can you help me on how I can run the Terminal and the commands to check the ISO image?
 
I did not burn the CD at high speed. I burnt at the 8X, which is the slowest option available in my Nero CD burning software.
 
Also, I do not think the CD-ROM disk is corrupt as it is a brand new one.
 
With regards to the processor, I use Intel Celeron 1.7GHz processor with 512 MB RAM.
 
Thanks again for your help Phil.
 
Cheers,
Subbu.

---

### Post by Subbu_09 on 2009-11-20
> **darkod said:**
> What video card do you have?
The same was happening to me with integrated Radeon HD3200, it seems the driver the live CD is trying to use has some issues with some Radeon cards.
Hi,
 
I think it is the S3 graphics card (in-built) on a Kobian motherboard. I am not very sure about that.
However, I tried a LIVE CD of Puppy Linux and it booted alright without any issues.... So, I am not sure whether the graphics card would be an issue with Ubuntu Linux. I will try to get it from my PC
for you tomorrow.
 
Thanks,
Subbu.

---

### Post by phillw on 2009-11-20
Hi the celeron is 32 bit. the link I posted has the how-to for windows, after the linux, and mac ones... you just need to scroll down the page a little.

Regards,

Phill.

---

### Post by darkod on 2009-11-20
I have no idea how S3 cards are supported. One thing you could try, just as a test, is to download the 8.04 LTS 32bit version and see if the Try ubuntu option will work correctly. For me it worked, it was not rebooting the PC. But I installed 9.10 anyway and in text mode updated the video driver, it's working fine since. That's why I think it was only the driver.
You can find all releases of Ubuntu for download at:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Just try 8.04 LTS, don't install right away. See if it reboots the PC also. Then you can ask for advice are you losing on anything if you end up installing 8.04. I don't know that, I'm new to Ubuntu.

---

### Post by Subbu_09 on 2009-11-20
Thank you Phill. I did check the MD5 CHECKSUM URL before but I simply missed it out as I did not scroll down to see the Windows options. Thanks. I will try that and see if my ISO file is intact.
And is there anyway, I can burn at 4X speed, if that would cause the issue?
 
Thanks,
Subbu.

---

### Post by Subbu_09 on 2009-11-20
Thanks for that update. I will try with 8.04 LTS after exhausting other options with 9.10. By the way, I am also very new to Linux and Ubuntu (though I have tried Puppy Linux Live CD few times and worked on it). And I don't want to permanently install Ubuntu (irrespective of the version) before I know what it is like and how it works. Also, I already have Windows XP. So, even if I go for a Linux permanent install, then I have to go for a dual boot with Windows XP.
 
Cheers,
Subbu.

---

### Post by Subbu_09 on 2009-11-20
> **phillw said:**
> Hi the celeron is 32 bit. the link I posted has the how-to for windows, after the linux, and mac ones... you just need to scroll down the page a little.
 
Regards,
 
Phill.
 
 
Hi Phill,
 
I did go to the URL you mentioned, downloaded the program that will do MD5 CHECKSUM in Windows XP and fortunately, found both of them MATCH. So, one issue is off the way....... What next? How do I check the burnt CD image in Windows XP?
The name of the ISO file I downloaded is "ubuntu-9.10-desktop-i386.iso". I guess this is for the 32-bit PC's.
 
The URL shown below to verify the CD integrity can be done only with the Ubuntu Live CD.
 
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck#Verifying](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck#Verifying) the CD/DVD Integrity
 
Is there any way I can check the MD5 CHECK SUM on my Live CD in Windows XP?
 
thanks,
Subbu.

---

### Post by Subbu_09 on 2009-11-21
Hi All,

I got a new brand of CD-R and used ISO Recorder and burnt the image at 4X speed.
I was hoping to see the LIVE Dekstop CD boot this time without any issues. But no luck. I could not even check the "check CD for defects" menu. I can only do the memory test and also "boot from primary partition" options. If I select and enter all other options, my system restarts. All the help menu items work though. I am still back to the same problem. Like I updated before I verified the MD5 CHECK SUM of the ISO image I downloaded (I downloaded it thru' a download manager - GetRight with multiple resume options, would that be a problem?) and the checksums matched.

So, what next should I try? Would the same LIVE CD work without any issues in some other computer?

Please help me.

Thanks,

Subbu.

---

### Post by darkod on 2009-11-21
Please be more specific. After you said you will also try with 8.04 LTS which CD are you talking about now?
Did you download and burn 8.04 LTS to try?

---

### Post by Subbu_09 on 2009-11-21
> **darkod said:**
> Please be more specific. After you said you will also try with 8.04 LTS which CD are you talking about now?
Did you download and burn 8.04 LTS to try?
 
The one I mentioned here is about 9.10 Karmic Koala Desktop LIVE CD and I am also downloading the 8.04 LTS desktop version to try that as well like you said and I will post the results after I try with that. 
 
And just to update, I have so far burnt  3 CD's using 3 different softwares on Windows XP (Nero, ISO Recorder and InfraRecorder at different speeds - 8X and 4X ). But none of them worked. All the CD's restart the system after I select one of the options that is "Try ubuntu without any changes", "Install ubuntu" and "Check CD for defects". The remaining options work  - that is the "Memory test" and the "boot with your primary partition" and also ALL the help menus.
 
So, I wonder where it could be wrong. Because, the MD5 CHECK SUM of the ISO image also match with the one from the Ubuntu site for the version I downloaded.
So, I am not sure where the issue may be. Will these CD's work in another computer?
I don't know...... Still keeping my fingers crossed and hoping to get next steps to resolve the issue with 9.10 LIVE CD.
 
Thanks again for your inputs.
 
Subbu.

---

### Post by darkod on 2009-11-21
It might be 9.10 doesn't like your hardware. Check with 8.04 LTS and post back.

---

### Post by Subbu_09 on 2009-11-22
> **darkod said:**
> It might be 9.10 doesn't like your hardware. Check with 8.04 LTS and post back.
 
Okay, I will try that and update. In the mean time, what about using an USB drive instead of a CD-R to boot into Ubutu 9.10? Is it possible? what are the steps to do that?
 
Thanks.

---

### Post by Subbu_09 on 2009-11-24
Hi All,

Let me start with the word SUCCESS...........SUCCESS.........SUCCESS......... . as I was able to successfully use the LIVE CD now, at this very moment and in fact posting this update from my Live Ubuntu 9.10 desktop from the default Firefox browser........
If any one is wondering what made this work, it is simple. Like Tom and others suggested, there is an issue with my CD-RW drive, which is about 4 years old now and it is not capable of burning an ISO image any more into a CD-R. So, I burnt the ISO image from a different computer, that obviously has a different CD-RW drive and it worked wonders for me. In fact, I should say it was a simple solution in the end.

So, as we found in my case, there is nothing wrong with the brand of CD-R's I was using, or the ISO files I was using (because, they all passed the MD5 checksum test) and not with the computer hardware I am using (by the way, mine is a Intel 1.7 MHz celeron processor with 512 MB RAM, built about 5 years ago....) or the video driver, OR the CD- image burning software I was using (The CD that I was able to successfully LIVE boot was burnt from a Nero burner....). It is only the CD-RW drive that was the culprit. That made me go crazy and I burnt about 5 CD's with different makes, with different CD burning software and with different speeds (by the way, the one that is successful now was burnt at 8X speed, which is the lowest speed with Nero burner).

Anyway, it is a great experience figuring out where the issue finally was. So, I do not have to try the only other option, which is using my USB disk as a LIVE boot CD (which I would like to try little later though after going thru' what is actually there in Ubuntu 9.10).

Once again, thanks for every one who helped me with their bit and to Phill who was even ready to ship a Live CD for me free of cost. I appreciate your gesture......

Thanks and thanks and thanks to all....

Regards,
Cheers.
Subbu.

P.S. I will mark this thread as SOLVED after hearing any comments from you guys today.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8381732") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8381732")

---

### Post by Subbu_09 on 2009-11-27
> **darkod said:**
> It might be 9.10 doesn't like your hardware. Check with 8.04 LTS and post back.
 
Hi,
 
I got a 8.04 LIVE CD burnt and was able to successfully do a CD check for errors.
However, when it went to the last step before loading up the desktop, it showed an error message like "safe graphics mode" and gave me options to CONFIGURE/CONTINUE/CANCEL. Selecting CONTINUE and CANCEL did not do anything neither if I click the CONFIGURE button and try to change the display parameters. The monitor looks blank/black with no further progress of the LIVE install.
I was able to successfully load into the Ubuntu desktop using the 9.10 LIVE CD without any issues.
 
Is there any fixes / solution for my display problem with the 8.10 LTS Live CD?
 
Thanks.
Subbu.

---

### Post by Subbu_09 on 2009-11-28
Hi All,
 
I was able to successfully boot with the LIVE 8.04 LTS today. I pressed F4 for modes and selected "low graphics mode" and then entered "Install Ubuntu without any changes to the computer" and it booted successfully. After booting, I changed my desktop resolution to make sure that it fits my screen. So, the issue is resolved.
 
Thanks for all your comments.

---

### Post by phillw on 2009-11-28
> **Subbu_09 said:**
> Hi All,

Let me start with the word SUCCESS...........SUCCESS.........SUCCESS......... . as I was able to successfully use the LIVE CD now, at this very moment and in fact posting this update from my Live Ubuntu 9.10 desktop from the default Firefox browser........
If any one is wondering what made this work, it is simple. Like Tom and others suggested, there is an issue with my CD-RW drive, which is about 4 years old now and it is not capable of burning an ISO image any more into a CD-R. So, I burnt the ISO image from a different computer, that obviously has a different CD-RW drive and it worked wonders for me. In fact, I should say it was a simple solution in the end.

So, as we found in my case, there is nothing wrong with the brand of CD-R's I was using, or the ISO files I was using (because, they all passed the MD5 checksum test) and not with the computer hardware I am using (by the way, mine is a Intel 1.7 MHz celeron processor with 512 MB RAM, built about 5 years ago....) or the video driver, OR the CD- image burning software I was using (The CD that I was able to successfully LIVE boot was burnt from a Nero burner....). It is only the CD-RW drive that was the culprit. That made me go crazy and I burnt about 5 CD's with different makes, with different CD burning software and with different speeds (by the way, the one that is successful now was burnt at 8X speed, which is the lowest speed with Nero burner).

Anyway, it is a great experience figuring out where the issue finally was. So, I do not have to try the only other option, which is using my USB disk as a LIVE boot CD (which I would like to try little later though after going thru' what is actually there in Ubuntu 9.10).

Once again, thanks for every one who helped me with their bit and to Phill who was even ready to ship a Live CD for me free of cost. I appreciate your gesture......

Thanks and thanks and thanks to all....

Regards,
Cheers.
Subbu.

P.S. I will mark this thread as SOLVED after hearing any comments from you guys today.
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8381732")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8381732")

As mentioned - You certainly went thru' wars in this install ... Tracking down problems with Kit is a night-mare. Trying someone elses computer for burning has come up good before. But, just g;lad you got a system working & everyone knows it was NOT that Ubuntu 'hated' you or your computer :D

Regards,

Phill.

---

### Post by Subbu_09 on 2009-11-29
> **phillw said:**
> As mentioned - You certainly went thru' wars in this install ... Tracking down problems with Kit is a night-mare. Trying someone elses computer for burning has come up good before. But, just g;lad you got a system working & everyone knows it was NOT that Ubuntu 'hated' you or your computer :D
 
Regards,
 
Phill.
 
Yes, Ubuntu worked just fine after I got the LIVE CD burnt from another machine and thanks for all your help.
 
Regards,
Subbu.

---

### Post by game fever on 2009-11-29
I have the same problem, except I ordered my CD (so it is not a CD problem). I have an ati radeon 9550. When I try to install ubuntu 9.10 the computer is working something and than it`s just goes to sleep. I have try almost everything. USB installation, older version7.10(also an ordered CD), also I tried all the options from the f6 menu(acpi off etc.), safe mode. I have no more ideas please help

---

### Post by Subbu_09 on 2009-11-30
> **game fever said:**
> I have the same problem, except I ordered my CD (so it is not a CD problem). I have an ati radeon 9550. When I try to install ubuntu 9.10 the computer is working something and than it`s just goes to sleep. I have try almost everything. USB installation, older version7.10(also an ordered CD), also I tried all the options from the f6 menu(acpi off etc.), safe mode. I have no more ideas please help
 
Hi,
 
Ordered CD's can also have problems, some times. They can even fail MD5 checksum
tests. So, I would advise to test the CD you have now in a different machine than your
computer and see if it works. If it doesn't work, then most likely the CD may have problems and if it works, then we should try to figure out what is the issue with your computer.
 
Alternately, try to change the dekstop screen resolutions when you are running your current OS in your machine - it should be to a lower resolution (like 800x600) from a higher one, if that is the case - and try to boot from the Ubuntu CD. Some times, if the
screen resolution is not supported by the OS for your graphics card / video monitor
configuration, then your screen may go blank by switching its power off automatically.
It has happened to me once in my Windows XP, when my monitor was changed from an LCD one with a higher resolution to a CRT one, which has a lower screen resolution. I had some tough time in figuring out what could be the problem, before
I got it resolved.
 
Hope this helps.
 
Regards,

---

### Post by game fever on 2009-11-30
I am sorry but I don`t quite understand what are you trying to explain. Should I change my resolution in win XP(current OS)just before I restart the computer to boot ubuntu?

---

### Post by Subbu_09 on 2009-12-02
> **game fever said:**
> I am sorry but I don`t quite understand what are you trying to explain. Should I change my resolution in win XP(current OS)just before I restart the computer to boot ubuntu?
 
 
Yes, change the screen resolution to a low graphics mode - like 800x600, save the changes and reboot the computer and try Ubuntu with the LIVE CD.
 
Alternately, like I suggested, did you try your Live CD with another machine to rule out any issues with the CD you received.
 
By the way, I received my official Ubuntu 9.10 LIVE CD yesterday and I was able to successfully boot with it without any issues. So, most of the CD's should work, I guess.
 
Regards.

---

