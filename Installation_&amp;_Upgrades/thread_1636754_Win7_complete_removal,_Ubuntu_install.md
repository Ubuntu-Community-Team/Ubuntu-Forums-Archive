---
title: "Win7 complete removal, Ubuntu install"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by h34e0f on 2010-12-03
My computer had some nasty spyware/virus attacks recently and I have not managed to get it back to standard (very slow and buggy).  I was about to reinstall Win7 but have decided to take the plunge and switch entirely to Ubuntu instead of using a partition.  How can I completely blank my PC and install Ubuntu from scratch? Or does it have to run with windows as a base?  In that case I'd like to blank it completely still and reinstall windows first - to completely remove all the garbage from my system.  Thanks!

---

### Post by SpotHT on 2010-12-03
Reinstall Windows 7 by booting from its CD. During the installation, you will be given an option to format your hard drive partitions.  Format the partition containing your old Windows 7 OS, then proceed with the installation. You can then dual boot Windows 7 with Ubuntu smoothly as if you are installing a software.

---

### Post by sikander3786 on 2010-12-03
Welcome to the forums :-)

No Ubuntu is a complete operating system so it doesn't need Windows as a base. However it can be installed inside Windows for just testing purposes.

During the installer's partitioning step, you get an option to "Use entire disk". Choose that and whole of your HDD will be formatted and partitioned automatically as per Ubuntu needs.

Have you got an Ubuntu disc? You can also boot Ubuntu from a USB drive and use that as an installation media. Post back if you need help regarding that.

Feel free to ask whatever you need to know :-)

---

### Post by h34e0f on 2010-12-03
> **sikander3786 said:**
> Welcome to the forums :-)

No Ubuntu is a complete operating system so it doesn't need Windows as a base. However it can be installed inside Windows for just testing purposes.

During the installer's partitioning step, you get an option to "Use entire disk". Choose that and whole of your HDD will be formatted and partitioned automatically as per Ubuntu needs.

Have you got an Ubuntu disc? You can also boot Ubuntu from a USB drive and use that as an installation media. Post back if you need help regarding that.

Feel free to ask whatever you need to know :-)

Great thanks.

Yes just finished burning a CD.

Had a few thoughts - installing on a laptop, should i use desktop or netbook version? I presumed desktop...

Also if it completely formats the drive how do hardware drivers work - are they automatically picked up?

---

### Post by cogier on 2010-12-03
sikander3786 is correct. Just install Ubuntu and use the "Use entire disk" option. 

It is interesting that Microsoft has managed to influence people to such an extent that they believe that their computer will not work without it.

I have computers that have never seen Windows and they work so much better without it. It just takes time to learn a different way of doing things.

Take the plunge, you can always revert back to Windows as you have paid for the license. I suspect, though, if you give it time you wont want to.

Enjoy Open Source!

---

### Post by Slim Odds on 2010-12-03
> **h34e0f said:**
> Great thanks.

Yes just finished burning a CD.

Had a few thoughts - installing on a laptop, should i use desktop or netbook version? I presumed desktop...

Also if it completely formats the drive how do hardware drivers work - are they automatically picked up?

A) Don't use a netbook version unless you have a netbook
B) Ubuntu is linux and cannot use any Windows drivers anyway, if you select 'Use Entire Disk' it will know what to do

---

### Post by h34e0f on 2010-12-03
> **Slim Odds said:**
> A) Don't use a netbook version unless you have a netbook
B) Ubuntu is linux and cannot use any Windows drivers anyway, if you select 'Use Entire Disk' it will know what to do

This is what I figured. I was just thinking becuase laptops come with so many manufacturer loaded programmes that maybe parts would not work (for example the programmable buttons etc.)?

---

### Post by sikander3786 on 2010-12-03
Most of your queries have been answered already.

I see you have burnt an Ubuntu disc already. It was recommended to run a MD5SUM check on the image to save you troubles later. And also to burn the disc at the lowest possible speeds.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Anyhow as the disc is ready to be booted, instead of getting into that MD5SUM check, boot it. Hopefully there won't be any problems.

Good Luck for the install :-)

If you plan to install now or when ever, feel free to post any queries in this thread. We'll be keeping an eye on this ;-)

---

### Post by h34e0f on 2010-12-03
> **sikander3786 said:**
> Most of your queries have been answered already.

I see you have burnt an Ubuntu disc already. It was recommended to run a MD5SUM check on the image to save you troubles later. And also to burn the disc at the lowest possible speeds.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Anyhow as the disc is ready to be booted, instead of getting into that MD5SUM check, boot it. Hopefully there won't be any problems.

Good Luck for the install :-)

If you plan to install now or when ever, feel free to post any queries in this thread. We'll be keeping an eye on this ;-)

Thanks.

CDs are cheap as chips so I'll run a check and burn it again (may as well to be safe).

I'm sure I'll come back here moaning when I mess something up!

Thanks for teh advice.

---

### Post by h34e0f on 2010-12-03
I'd like to add a partition for Windows XP for various things such as games (Age of Empires LAN parties - we kick it old school) etc. to prevent issues.

Is this necessary? - Can Wine handle it etc.?

If so do I have to do it during initial setup or can I add it later on?

---

### Post by Quackers on 2010-12-03
If you are thinking of having a Windows system on in the future it would be slightly easier to take that plunge now, by re-installing Win 7 first. It can be more messy to do it afterwards.
If you go down that route you can then shrink the Win7 partition using the Windows Disk Management console (after defragging the drive) and create free space for Ubuntu that way. Then you can install Ubuntu in that free space by using the Ubuntu disc.
If you boot from the Ubuntu disc you can do 2 things. The first is to press F6 key during boot which will give you the option of checking the image for errors. The second thing is that you can choose to "try ubuntu" so that you will be aware of any hardware problems that may exist for you. 
Please also note that some of your hardware buttons eg Fn keys or brightness keys may not work in Ubuntu. Some of mine don't. But this is not a problem on mine.

---

### Post by h34e0f on 2010-12-03
> **Quackers said:**
> If you are thinking of having a Windows system on in the future it would be slightly easier to take that plunge now, by re-installing Win 7 first. It can be more messy to do it afterwards.
If you go down that route you can then shrink the Win7 partition using the Windows Disk Management console (after defragging the drive) and create free space for Ubuntu that way. Then you can install Ubuntu in that free space by using the Ubuntu disc.
If you boot from the Ubuntu disc you can do 2 things. The first is to press F6 key during boot which will give you the option of checking the image for errors. The second thing is that you can choose to "try ubuntu" so that you will be aware of any hardware problems that may exist for you. 
Please also note that some of your hardware buttons eg Fn keys or brightness keys may not work in Ubuntu. Some of mine don't. But this is not a problem on mine.

i was mostly worried about my wireless button and the button to disable the keypad which I use a lot! Oh and of course the volume buttons.

Why is it better to install Windows first?

---

### Post by Quackers on 2010-12-03
Windows (especially later versions) can be fussy about being at the start of the hard drive. It thinks it's the bee's knees :-) and nothing else should take precedence over it. It's wrong of course :-)
People have managed to do it though so it's not usually a show stopper!

---

### Post by h34e0f on 2010-12-03
> **Quackers said:**
> Windows (especially later versions) can be fussy about being at the start of the hard drive. It thinks it's the bee's knees :-) and nothing else should take precedence over it. It's wrong of course :-)
People have managed to do it though so it's not usually a show stopper!

I was thinking XP or maybe even 98 (loved it!) as I'd only be using the Win partition for gaming and the games I play are all from the late 90s - early 00s

I love Win7 but only as a primary OS. Not much pont having it IMO if it's only for occasional use. Maybe even TinyXP (dont know much about it but heard it's fairly good for partitions etc.)?

If I go with an older Win like XP would it be easier to stick on at a later date? Or would you strongly recomend installing it first?

(I have Win 95, 98, XP (school edition ;)) and 7 on CD already so I have options)

---

### Post by dFlyer on 2010-12-03
I highly recommend you first boot off the live CD and test all your hardware first, to make sure you have all the correct linux drivers. If everything works off the live CD, than it should be okay to install ubuntu as your sole OS. Should you decide you want to dual boot than I would first install windows back on your hard drive leaving space for ubuntu. I always say an OS is a personal choice. I have not run windows for so long that I wouldn't even know how to install it or want to spend the time searching for drivers to install windows. A fresh install of ubuntu usually takes less than 30 minutes. The last time I remember install windows, it took all day and into most of the night. That was the basic XP system with drivers, updates and no other programs.

---

### Post by Quackers on 2010-12-03
With regard to the later installation of XP you are in the same boat as with Ubuntu. You would need to make sure that all your hardware has XP drivers available. As your system came with Win 7 and you know the hardware works it would be the safer option. If your hardware is of later type it is possible that XP drivers don't exist for some things.

---

### Post by h34e0f on 2010-12-03
> **Quackers said:**
> With regard to the later installation of XP you are in the same boat as with Ubuntu. You would need to make sure that all your hardware has XP drivers available. As your system came with Win 7 and you know the hardware works it would be the safer option. If your hardware is of later type it is possible that XP drivers don't exist for some things.

PC came with Vista but updated it to 7.

I'm only thinking about having Windows for gaming incase it wont work properly on Ubuntu... So if it's not necessary I won't bother.

I don't even do gaming just VERY occasionally (only when I'm home from Uni over summer/easter/christmas) with friends

---

### Post by Quackers on 2010-12-03
It's your machine, the choices are yours to make :-)
Personally I think Ubuntu rocks, but I'm not a gamer :-)

---

### Post by h34e0f on 2010-12-03
> **Quackers said:**
> It's your machine, the choices are yours to make :-)
Personally I think Ubuntu rocks, but I'm not a gamer :-)

As said before I'm not either. I've been wanting to do this for around a year so I'm just gonna do it and hope the games work, if not I can borrow a laptop or try to install win on top :) all my files are transferred to removable HDD (took an age!) so doing it now!

---

### Post by Quackers on 2010-12-03
Good luck and enjoy :-)

---

### Post by h34e0f on 2010-12-04
Well the install went well taking only 30 minutes and everything works great...

Apart from the fact I have no internet. Connected to the network fine but I can't work out why its not working properly...

---

### Post by Quackers on 2010-12-04
Try connecting an ethernet cable and run Additional drivers (from System > Admin) and see if drivers are available for your graphics card and wireless card.

---

### Post by h34e0f on 2010-12-04
Yeah Ive been trying to get hold of an Ethernet cable...

---

### Post by h34e0f on 2010-12-04
Found one and did the GFX driver and now my Wireless works?!

Took a bit of fiddling to get the Ethernet link to work so maybe that fixed it, or maybe the 180 odd updates :p

Thanks guys! Time to start exploring and playing!! My favourite bit :D

---

### Post by Quackers on 2010-12-04
Very nice :-)  Have fun!

---

### Post by sikander3786 on 2010-12-04
This community is wonderful, I have to say. When a member is away, some-one else jumps in and tries his best to help. As **Quackers** did here. Great help, widely appreciated!

Hope the OP enjoy their stay with Ubuntu and also, the forums :-)

---

### Post by h34e0f on 2010-12-04
Thanks! Everything is running great so far! :D

---

