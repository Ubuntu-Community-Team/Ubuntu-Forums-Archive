---
title: "Dual boot problem with 4 partitions on HP Pavilion dm4"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-10-05
Have an HP Pavilion dm4 i3 laptop with Windows 7.
I want to dual boot it with Ubuntu 12.04. 

Problem is that HP laptop HDD already has 4 partitions:
1. System partition.....199MB
2. C-Drive with W7.....582GB
3. Recovery partition...13.85GB
4. HP Tools partition...104MB

When I try to create an Ubuntu partition, it becomes Unallocated and dead/useless. Therefore I can't install Ubuntu as a dual boot system.

Did a little checking and it seems you can't create more than 4 partitions on a HDD. I know there are ways around this but I can't remember what needs be done.

Can someone help me out here?

Was thinking of deleting the #4 HP Tools partition but fear it may be linked somehow to the Recovery partition causing a possible problem in the future if W7 needs to be recovered.

---

### Post by darkod on 2012-10-06
It's not linked and you can delete it. You have also other options, like opening the recovery software in windows and making a set of recovery DVDs. After that you can also delete the recovery partition and use that space. If you ever need a factory restore you can use the DVDs.

That's what I would do since those 14GB will just stay wasted sitting there and hardly ever be used. By deleting that partition you can use that space too.

If you use the manual partitioning during the ubuntu installation don't forgte to create the partitions as logical, not primary.

---

### Post by cybrsaylr on 2012-10-06
darkod thanks.

I deleted the small #4 HP Tools partition.

Decided to keep #3 Recovery partition because when I went to make the 2 W7 recovery discs, HP reported that operation was already done on 2/2/12 and they only allow this to be done once! Maybe he misplaced his recovery discs.

Anyways, 12.04 Live CD is now installing system nicely as I am familiar with.

Hope all goes well.

---

### Post by cybrsaylr on 2012-10-07
A little followup.

12.04 installed in 17 minutes.
Then a couple minutes later got the 'update' alert saying 421 updates were available, in spite of checking off for updates to be done on initial installation. This has happened before on another laptop and PC recently. Well that took 18 minutes to complete, then 12.04 was good to go.

Then it was just a matter on installing some favorite apps & programs and so far all is running A-OK.

A couple things I noticed.
1. When this i3 laptop is plugged into my HDTV to make it a 'super-smart' HDTV this laptop screen turns off and goes black on bootup. Same thing happens whenever laptop is booted up on its own into Ubuntu! To light up the screen for Ubuntu, I have to hit F3 Key and screen lights right up. Windows 7 does not have this issue and screen never goes off when booting into Win7. First time this has happened. Other laptops  plugged into this HDTV, their screen monitor remains on and never goes off. 
Is there any fix for this?

2. Rhythmbox is the default play on 12.04 and I like it but is there any way to disable this so Audacious or even Movie Player can be used to first open music files because both open faster than Rhythmbox and are easier to clear out? Rhythmbox saves all your music files while the other two don't.

3. Had some problems yesterday with 12.04 not recognizing any thumb flash drives that were plugged into any of the laptop's 3 usb ports! Tried it several times with no luck. But those usb ports worked fine when the nano receiver for a wireless mouse was plugged in. Anyways today when I tried again to use those thumb drives, 12.04 recognized them straightaway! Isn't technology grand....lol. Have no idea why they didn't work yesterday but work fine today.

---

### Post by cybrsaylr on 2012-10-10
A little follow up since it's sort of related.

A couple days ago Ubuntu disk utility reported a HHD failure was imminent on my Dell i7. The next day Dell reported the same on boot up saying to hit F2 for more info. Went into Windows 7 and M$ didn't report this for a good day and a half after Ubuntu! BTW 11.04 gave out a very detailed 'test results tech report' on what was going on.....failed sectors and such. 

Nice job Ubuntu! 
Was really surprised and disgusted the OEM <3 year old 1TB Seagate HDD was going! Decided to save all files needed before a total failure.


Got this replacement [128GB Kingston SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139950") because prices have been dropping on the SSD.

Decided to do a clean install of 12.04 and not bother with Windows 7 and was impressed with the performance of this SSD which is not rated as the fastest but the price was right!
The only tweak I did before installing 12.04, was go to the Dell website and upgrade BIOS to the latest version which Dell recommends. 
Took 9 minutes to install 12.04 then 8 minutes to download and install the 171MB of 421 updates! Then is was good to go!

It is noticeably faster than the Seagate HDD that is failing.
12.04 boots up in 20 seconds and shutdown is 4 seconds.
With the Seagate drive it used to boot up in 35 seconds and shutdown in 6 seconds, so there is some improvement with this SSD.

Things load much faster and surfing is snappier on the www.

Just hope this SSD lasts.
Today 5 minutes after booting up, disk utility sent me a report this new SSD was 'failing' due to high temps....85 degrees F! Then a few minutes later disk utility reversed itself and now reports SSD is 'healthy' but the temp is now 97 degrees F! Have no idea what is going on. But all other disk utility test results are A-OK at this point in time.

12.04 is nice but am still trying to find a way to stop Rhythmbox from being the default player. 
Went into System settings > Details > Default Applications > Music and clicked on VLC to be the new default player but Rhythmbox still opens every time a music file is clicked on!
What do you need to do to switch from  Rhythmbox to something else?

---

### Post by ALinuxWindowsBalance on 2012-10-10
Delete the HP tools. You can re-install that from the stuff on HP's web site.
Try re-sizing the W7 down to 500 GB.
And use LVM because the swap partition will slow Windows down(it tries to use it as ReadyBoost or whatever)
Plus, LVM is faster, especially if you use ReiserFS.

---

### Post by ALinuxWindowsBalance on 2012-10-10
> **cybrsaylr said:**
>  12.04 not recognizing any thumb flash drives that were plugged into any of the laptop's 3 usb ports! Tried it several times with no luck. But those usb ports worked fine when the nano receiver for a wireless mouse was plugged in. Anyways today when I tried again to use those thumb drives, 12.04 recognized them straightaway! Isn't technology grand....lol. Have no idea why they didn't work yesterday but work fine today.

**Probably just needed a reboot.** The kernel does that to me too if i'm doing something heavy on RAM and CPU (Minecraft Client and Minecraft Server)
A Resource Allocation problem.

---

### Post by cybrsaylr on 2012-10-10
> **ALinuxWindowsBalance said:**
> Delete the HP tools. You can re-install that from the stuff on HP's web site.
Deleted HP tools then did a straight dual boot and both OSs run fine.

> **ALinuxWindowsBalance said:**
> **Probably just needed a reboot.** 
Yeah figured it was just something as simple as that....lol

---

### Post by ALinuxWindowsBalance on 2012-10-10
As long as you're fine :3

---

### Post by SHULTZIE on 2013-03-13
Hi [**[COLOR=#000000]cybrsaylr[/COLOR]**]("http://ubuntuforums.org/member.php?u=589378"),  
Did you ever get a solution to the laptop screen not running when you have the second monitor attached? 
I've been into the tools fuction but just can't get it to make the correct adjustment. The tools (System settings/displays) will see the two monitors if I uncheck the "mirror displays" box and I can play with the resolutions for the laptop screen but the screen stays dark.

I realize I need to start a new thread on this (and I will) but this is part of my research to see if the solution is common or has been found.  Thanks to all for helping this newbie to ubuntu.

---

