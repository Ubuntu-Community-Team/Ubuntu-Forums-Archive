---
title: "Installation problem with Hardy(initramfs)"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by svar1 on 2008-05-05
With the live cd, I was able to both boot Hardy  and also to use the installation menu on Windows(didn;'t finish because it was not clear what it was going to partition)
Now, I installed a new SATA disk and am trying to install Hardy on it. 
 (I already have a  dual boot Slack-Suse on the machine-no Windows of course)
The problem is I can neither  boot to Hardy, nor to any sort of installation menu. Instead I get a screen saying :BusyBox v1.1.3(DEbian 1.1.13....)
and a line
initramfs(106.97.5417]
ats2:SRST failed(errno=-16)

Any idea what this is about?
I get a linux shell, but not much in terms of installation

---

### Post by reyasuk on 2008-05-05
> **svar1 said:**
> With the live cd, I was able to both boot Hardy  and also to use the installation menu on Windows(didn;'t finish because it was not clear what it was going to partition)
Now, I installed a new SATA disk and am trying to install Hardy on it. 
 (I already have a  dual boot Slack-Suse on the machine-no Windows of course)
The problem is I can neither  boot to Hardy, nor to any sort of installation menu. Instead I get a screen saying :BusyBox v1.1.3(DEbian 1.1.13....)
and a line
initramfs(106.97.5417]
ats2:SRST failed(errno=-16)

Any idea what this is about?
I get a linux shell, but not much in terms of installation

I had all sorts of strange happenings whilst trying to install Hardy and eventually found that if I removed 1 gig of ram (I had 4 gigs working with Gutsy) it installed with no problems.
If anyone knows how I can add the extra gig of ram, I'd be interested to know as I'd rather have it in the machine than on the shelf! 
jen

---

### Post by svar1 on 2008-05-06
Meaning strange like this? In my case I have much less RAM.

---

### Post by ccacioppo on 2008-05-06
I had the same error on the live cd of 8.04.

Why would u sacrifrice ram for installing this?!?!!?

Let em fix it on their side!!!

---

### Post by Pumalite on 2008-05-06
Try the Alternate CD.

---

### Post by Rocky37 on 2008-05-06
> **ccacioppo said:**
> I had the same error on the live cd of 8.04.

Why would u sacrifrice ram for installing this?!?!!?

Let em fix it on their side!!!

I would love to see Ubuntu fix this problem too but have seen no movement in that direction during the past 2 weeks.  Not a word!!  I have looked through the bug reports but have found nothing.  It's not like this is a small problem judging from the number of posts here.

---

### Post by fixitdude on 2008-05-06
> **Rocky37 said:**
> I would love to see Ubuntu fix this problem too but have seen no movement in that direction during the past 2 weeks.  Not a word!!  I have looked through the bug reports but have found nothing.  It's not like this is a small problem judging from the number of posts here.Did you check to see if there is a bug report on the RAM issue? I don't have that much RAM installed, so you can give that stick to me and it won't be sitting on your shelf :)

If that much RAM is a problem, it's an important bug to fix.

Are you saying it still won't boot or something with 4G RAM *after* you installed hardy? I would think it's a installer only problem.

---

### Post by Rocky37 on 2008-05-06
> **Pumalite said:**
> Try the Alternate CD.

Have seen that past on allot -- and a number of replys that it didn't help!  I also tried 7.1 and 7.1 alt and 7.04 and 7.04 alt -- that only gave me and screwed up boot sector. 

I'm running a 4 year old home built with pentium 4 on a foxcomm FX4MR-ES motherboard, 4GB ram, an older sound blaster 5.1 Live and Radeon 7200 video card, seagate barracuda 250gb ,seagate 80gb and a maxtor 89gb ---- am thinking of replacing the audio and video cards and see if that helps.

---

### Post by Rocky37 on 2008-05-06
> **fixitdude said:**
> Did you check to see if there is a bug report on the RAM issue? I don't have that much RAM installed, so you can give that stick to me and it won't be sitting on your shelf :)

If that much RAM is a problem, it's an important bug to fix.

Are you saying it still won't boot or something with 4G RAM *after* you installed hardy? I would think it's a installer only problem.

No - I didn't check bug reports about "to much" ram.  Never gave it a thought nor had I seen it mentioned until today.  I only have 2gb's of ram in the puter - guess I should try removing a stick :lolflag:

---

### Post by Pumalite on 2008-05-06
32 bit recognizes only 2 GB. 64 bit has no problems with 4 GB. You can install 32 bit with a special kernel or boot parameter that I don't remember.

---

### Post by fixitdude on 2008-05-06
Sorry rocky, my reply was for reyasuk, oops.

I think Pumalite has a good point, and a lot of the kernels are compiled 64 bit only, so maybe the part where it detects that is messed up or they decided to drop 32 bit support? Haven't researched the issue.

Plus, if 32 bit is limited to 2GB then it shouldn't matter if you have more, it just doesn't use it I would think. But it's probably more like linux sees 4GB and decides to load itself into high RAM, which is a "bad address" on 32 bit so the CPU just halts.

Search google for linux boot commands that let you set the RAM limit.

---

### Post by Pumalite on 2008-05-06
This is worth reading:
[http://ubuntuforums.org/showthread.php?t=375853](http://ubuntuforums.org/showthread.php?t=375853)

---

### Post by svar1 on 2008-05-07
Sorry to see the discussion has  branched off.  My original post HAD nothing to DO WITH the 4GB limit. I can only wish I had that much memory.
 The problem is that alhough I have Slack 12 and Suse 9.3 on the same machine, the LiveCD can neither boot in demo mode, nor install anything. On the contrary, it can do both the above on a machine with Windows. In the CD, I see some .exe files, which I assume are Windows only. So my suspicion is: could the LiveCD be
 made under the assumption that one already has Windows installed? If so, is there some other way to install Hardy for those of us that do not have Windows?
Suppose I can get a shell from the liveCD. What commands do I need to run to install Hardy?

---

### Post by Pumalite on 2008-05-07
Download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, check CD for ingrity before install.

---

### Post by Rocky37 on 2008-05-08
> **svar1 said:**
> With the live cd, I was able to both boot Hardy  and also to use the installation menu on Windows(didn;'t finish because it was not clear what it was going to partition)
Now, I installed a new SATA disk and am trying to install Hardy on it. 
 (I already have a  dual boot Slack-Suse on the machine-no Windows of course)
The problem is I can neither  boot to Hardy, nor to any sort of installation menu. Instead I get a screen saying :BusyBox v1.1.3(DEbian 1.1.13....)
and a line
initramfs(106.97.5417]
ats2:SRST failed(errno=-16)

Any idea what this is about?
I get a linux shell, but not much in terms of installation

Getting back to the original post -- and I also have a few other posts in this thread -- we seem to have gotten nowhere, other than 2 gb of ram is cool and 4 isn't worth the expense.  Doesn't relate to the first post much.

To recap some --- I have installed Hardy to my laptop with a flawless effort -- and have to say I REALLY LOVE Hardy Heron!!  And so 'on to my desktop'.  Remember, I'm moving from Win XP and REALLY want to dump it -- the sooner the better.

My first attempt was to do an install from windows which went OK until the reboot.  On the reboot I went to the black screen with the cursor in the upper left and unable to boot to windows or ubuntu.  Had to reinstall windows at that point.
Since then any attempt to install Hardy has dumped me at the install screen.  The first install menu screen is covered with the language selection screen and all attempts to move from that screen end up back at the black screen.

All attempts have failed.  Including disconnecting all drives - excepting the cd and first boot drive.  Removed video card and moved the video to the MB connection -- same with the audio card -- all the usb's were disconnected.  Nothing was connected other than the video to the MB, one blank harddrive and the CD drive  ---  resulted once again with the black screen with white curser.

I have tried the the 8.04 alt iso, the gutsy 7.1 and 7.04 -- both alt iso and normal iso.  All dump me at the black screen with white curser.

This evening I once again tried to install Hardy from within windows. All went well until the reboot ------ that ended with the image below.  This is driving me nuts-------------

---

### Post by Rocky37 on 2008-05-08
Not a problem Fixit -- realizied after I posted that things had gotten turned around.

---

### Post by Rocky37 on 2008-05-08
It seems to me that I have a problem with the motherboard or the bios configuration but don't have a clue where to go from here.

At this point a pity party may be in order for this 71 year old person.  My first computer was a  IBM PC Jr so I have been around for a bit. 

 I want Hardy to work for me -- but Linux is new to me --------------- ](*,)

---

### Post by confused57 on 2008-05-08
> **Rocky37 said:**
> It seems to me that I have a problem with the motherboard or the bios configuration but don't have a clue where to go from here.

At this point a pity party may be in order for this 71 year old person.  My first computer was a  IBM PC Jr so I have been around for a bit. 

 I want Hardy to work for me -- but Linux is new to me --------------- ](*,)

May not help, but you could try various boot options:
[http://ubuntuforums.org/showthread.php?t=765195&page=7](http://ubuntuforums.org/showthread.php?t=765195&page=7)

---

### Post by svar1 on 2008-05-08
Quoting Pumalite:
"Download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
"


-That's exactly what I did


Follow this guide:
[https://help.ubuntu.com/community/Bu...8burn%29%7C%28](https://help.ubuntu.com/community/Bu...8burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, check CD for ingrity before install

-I did not check,  that, but I made the CD the same way I had done for Gutsy, with no problems
and: I CAN boot(even install from a Windows machine). It's just that I cannot do that from machines that do not have Windows. I see some .exes in the CD. ANyway, I'll try again

---

### Post by Pumalite on 2008-05-08
md5sum is vital if you want a good CD.

---

### Post by Rocky37 on 2008-05-08
Thanks for the suggestions.  I have tryed the various boot options too -- Have been following the related forums -- nothing has helped.

---

### Post by tofuconfetti on 2008-05-08
Are you using a USB keyboard and do you have USB legacy support activated in your BIOS?  As strange as that may sound, that has prevented me from getting two motherboards to boot.  At least, you could try that and see if it helps.

I have one MSI AMD64 system that won't boot that way.  I have a quadcore e6600 on an Intel socket 775 motherboard that won't boot with the legacy USB support and a USB keyboard plugged in.  I get booted out to the busybox prompt with initramfs failure.

---

### Post by Rocky37 on 2008-05-08
> **Rocky37 said:**
> Thanks for the suggestions.  I have tryed the various boot options too -- Have been following the related forums -- nothing has helped.

[SIZE="6"][COLOR="Red"]PROBLEM SOLVED!!!!!!
[/COLOR][/SIZE]
A few minutes on line with Dell and $319 later got me a new computer with ubuntu 7.1 installed -- a quick upgrade should have me hooked up with Hardy --- YES!!!!!  :guitar::popcorn:):P:rolleyes:

Couldn't have gotten a new motherboard, CPU,sound card and a video card for 300 bucks:lolflag:

---

### Post by tofuconfetti on 2008-05-08
That's one way to solve the problem :-)

---

### Post by Rocky37 on 2008-05-08
> **tofuconfetti said:**
> That's one way to solve the problem :-)
 
I thought so too -- more than one way to skin a cat  :lolflag:

---

### Post by svar1 on 2008-05-09
Pumalite,
the Md5s checks, I burnt at 4x and  all that's left is the integrity check, but I do not expect surprises. I'll burn it again.
The only funny thing I notice is that it is 699MB( but it lists it as 733 instead of 715 mill bytes), so maybe not all of it fit in a CD?

---

### Post by avkhatri on 2008-05-12
I hate this I'm having the same problem. Ubuntu is calling this an LTS? This is garbage

---

### Post by Pumalite on 2008-05-12
> **svar1 said:**
> Pumalite,
the Md5s checks, I burnt at 4x and  all that's left is the integrity check, but I do not expect surprises. I'll burn it again.
The only funny thing I notice is that it is 699MB( but it lists it as 733 instead of 715 mill bytes), so maybe not all of it fit in a CD?
I doubt ir. You can download ImgBurn if you have problems:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install it. Use a DVD if you need to. Go to Mode>ISO>Burn. Select 1x

---

### Post by svar1 on 2008-05-14
I did try ImgBurn(though Ubuntu recommends the  one I used originally), burned another CD and same results. No matter whether I choose fresh install, testing install or check disk for defects
 I get the same thing. I would try a dvd if I had a dvd burner.
Is it possible to copy the iso on a flash and try from there, or will this mean erasing everything on the flash ?

---

### Post by svar1 on 2008-05-14
Just a question: What if I install 7.10. Can I then do apt-get and do a full upgrade or  does not this work(I've never used Debian and apt-get before).

---

### Post by rorsino on 2008-05-14
I too have reinstalled 7.10 and tried to upgrade to 8.04.  no luck.  I tried 2 times.  I reinstalled 7.10 and did an upgrade from the GUI Update Manager... What did I get??  BusyBox...  So I re-installed 7.10 again then tried to upgrade from the terminal window using apt.  NO LUCK either....BusyBox again..    UGH

Im done trying until someone comes up with a solution.  An EASY solution.

I hate to say this but it is no wonder that LINUX will never see the mainstream users...

---

### Post by kororke on 2008-05-15
I received both Ubuntu 8.04 LTS and Kubuntu 8.04.
I had the "dump to busybox" problem with Ubuntu and anothe different problem with Kubuntu.
neither would install.
After reading all the thread on this subject, I was successful with both variants.
Incidentally the type of HD is not a factor
No1 Maxtor N256 (Kubuntu)
No2 Segate St310014ACE (Ubumtu)

I Formatted both HD to EXT3
I added all_generic_ide to the F6 commands.
Neither variants would install.
I re-formatted both HD to FAT32, and with the addition of the all_generic_ide both Ubuntu and Kubutu installed without a problem

kororke

---

### Post by svar1 on 2008-05-16
Maybe the problem is that I am trying to install Ubuntu on a sata partition formated to Reiser?

---

