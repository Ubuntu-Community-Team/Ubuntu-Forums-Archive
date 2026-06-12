---
title: "Edgy 64bit boot, and other problems"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by tedrampart on 2006-11-21
so I just bought a new laptop tonight, and was all excited to see how 6.10 would work on an AMD X2.  I currently have it installed on my toshiba celeron laptop, and it runs great no worries (except my laptops hardware quickly dying but thats another issue which I don't care about).  

this is my laptop: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00777553&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00777553&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)
(posted the link to save time)

I used the alternate AMD64 version of 6.10

the install went mad fast.  

the problem was after I rebooted.  I got to the Ubuntu Flash Screen (which was greyscale?? thats not right!), where it hung when the progress bar was hardly filled in.  I rebooted, to recovery mode, where it hung again.  so I rebooted again, but this time it hung with a little more progress. 

eventually after 10 restarts it booted up. (hasn't since though..)

once in there I had another problem, the screen resolution was set at 1024x768, even though I set it to 1280x800 in the install.  I couldn't change this to a higher reso later either.

after that I fooled around with the wifi settings to get them work, but had to dash to work.  so I put it on suspend.  after opening it again, black screen, had to restart.. but this time same issue on the flash screen.

I'm going to try reinstalling with either a different disc, and maybe even off the livecd as I read on here that some people had success with it.

I'm asking this now, because I've been reading and haven't found an answer to suit my somewhat newbie dilema.. and I'm hoping I can save a few discs and time downloading images when I get home.. ](*,) 

help please!
Thanks

---

### Post by tedrampart on 2006-11-22
okay so I've tried about 6 other discs.. some of them the same version just burnt to a different disc.  but others are the 386 live and alternate 6.10, and the dvd of the amd64 6.10, and now I'm about to try the dapper version of amd64..

I got the furthest with the amd64 edgy, but used the 'noapic'

however once I got in, and installed all the updates and new nvidia drivers I couldn't boot up.  I could hear audio, but no visuals. the video is Geforce Go 6150 if that helps.. 

I tried booting into recovery, but it halted at 'Starting Kernel event manager' and won't go further than that.

anyone at all?  I spent 6 hours yesterday and 2 already today on this.  I really don't knw what to do!

EDIT - so I got into recovery by adding 'noapic' to the bootup.  but now I need to get the nvidia drivers working.

---

### Post by tedrampart on 2006-11-22
okay.. so I reverted back to an older xorg.conf file, and then followed this howto for the nvidia drivers.. and it worked perfectly..

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

everything is running fine, though I don't have wireless setup yet.. Broadcom will be the death of me..

---

### Post by teaker1s on 2006-11-23
> **tedrampart said:**
> okay.. so I reverted back to an older xorg.conf file, and then followed this howto for the nvidia drivers.. and it worked perfectly..

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

everything is running fine, though I don't have wireless setup yet.. Broadcom will be the death of me..

I have broadcom 4311 this works if you can't get ndiswapper to work
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

### Post by dmery on 2006-11-24
Hi Tedrampart,
I bought a notebook HP media center dv6140us, dual core AMD Turion64, 2 giga ram, nvidia graphic card and sata HDD 120 giga. I read that you installed Edgy on HP dv.... and all is ok
I have some questions:
How can you install your Grub ? Because I read there are some problems with media center startup from windows and then you need to install Ubuntu in a especial way. How you can solve this point ?
If you can help me, I would appreciate it.
regards,
dmery

---

### Post by teaker1s on 2006-11-26
> **dmery said:**
> Hi Tedrampart,
I bought a notebook HP media center dv6140us, dual core AMD Turion64, 2 giga ram, nvidia graphic card and sata HDD 120 giga. I read that you installed Edgy on HP dv.... and all is ok
I have some questions:
How can you install your Grub ? Because I read there are some problems with media center startup from windows and then you need to install Ubuntu in a especial way. How you can solve this point ?
If you can help me, I would appreciate it.
regards,
dmery

I have the dv6116eu I used the live install and also the alternate install as this has deb packages you may require if you run into problems,grub and xp playing nice-main issue I read about and can't find how to solve is boot/shutdown erratic

---

### Post by dmery on 2006-11-26
I have the dv6116eu I used the live install and also the alternate install as this has deb packages you may require if you run into problems,grub and xp playing nice-main issue I read about and can't find how to solve is boot/shutdown erratic
__________________

Thanks for answering. Can you tell me where you read about grub and xp hp media center ? Because I want to use Ubuntu Edgy (I am Linux user from 2002) but I want to preserve media center features.
Thanks again for yor answer and your help, I appreciate it.
Regards,
dmery

---

### Post by tedrampart on 2006-11-27
sorry, I didn't check back on this very quicky.. 

as far as booting, I totally wiped the drive clean, and had no intention on running a dual boot, therefore grub worked fine.  I did however need to ad "noapic" into the command line.. and if something goes wrong and I need to get into recovery, I have to add it everytime as well.. 

the live cd's never really worked for me though.. one did at one point, but I can't remember which disc it was.. I tried everything from dapper to edgy, 386, amd64..

I thought with adding "noapic" to the bootup, I'd lose wireless, or sound.. the only thing I lost was the headphone jack.. which when I tried applying the patch, everything went back to square one.. which I had to have my linux guru of a brother do for me...

---

### Post by teaker1s on 2006-11-27
the quickest and simple way is to use "gparted" google it and download and burn image or burn iso depending on your burning prog-as it's a point and click gui to repartition xp free space. you will need to defrag and scan disc in xp before attempting to resize the hard drive. 

alter boot option to boot cd/dvd drive and gparted

when you have resized the hard drive the 64bit live install will install on the "[COLOR="Black"]**largest free space**[/COLOR]" it's important to select the largest free space as this is the space that we created by using gparted.
what will happen is ubuntu will remove the master boot record and install grub which now boots and gives a choice of ubuntu or xp.

Important when you first reboot after this you must let xp scan the disc-**do not, I repeat do not cancel**-this is required to avoid blue screen of death


if I leave mine it boots linux,if I select xp within 9 seconds it boots xp-I think I found a walkthru when I did mine I'll look for it for you

---

