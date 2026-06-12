---
title: "Grub isn't loading"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Mephy on 2008-02-18
Hi,

I installed Ubuntu on a secondary HD,

I have my Windows HD with 500 gig and my secondary with 300 gig.

I did the guided installation/partitioning (install on full hard disk), and everything seemed to work fine.

Then I rebooted to get off of the CD Mode, and I just boot right into Windows, no notification from Grub or anything.

Does anyone know why this happens?

Thanks

---

### Post by amohanty on 2008-02-18
You failed to install GRUB into MBR when prompted to do so (I usually use the alternate CD with the text installer so if the GUI version does not prompt you to, sorry!)

Nw you can use the liveCD and start the install and go to expert mode. You 'should' (have not used the GUI installer in a while) get a list of actions that the installer performs. Select 'Install boot loader/grub' and it should prompt you about installing it to MBR - say yes, after its done, exit the installer and you should be good to go.

HTH
AM

---

### Post by Mephy on 2008-02-18
Thanks for the help so far, I can't see a place where it asks me to install GRUB nor can I find 'expert mode', Should I just get the text installer instead?

Edit: Not that I really know what that is :-O

---

### Post by zvacet on 2008-02-18
When you boot your Cd press F1(it is help)and there you will find how to use expert mode.

---

### Post by amohanty on 2008-02-18
hmm I just looked at the graphical installer [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) and you are right there does not seem to be a place for grub. 

I think the CD should have the option of text installation, try that, at the language selection screen if you [http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu) if you press esc you will get to the main menu or select back at any of the later screens.

Then select bootloader/grub install and try that.

HTH
AM

---

### Post by Mephy on 2008-02-18
Thanks so far guys,

I booted from the CD again and went into the help screen, and I looked through it and couldn't find anything about expert mode.

And that second link that you posted isn't working for me.

I went into the Install mainscreen and hit esc and nothing hpapened (language screen).

---

### Post by amohanty on 2008-02-18
Well then back to the alternate cd it is. Let us know how it goes.

AM

---

### Post by Mephy on 2008-02-18
Sorry, What alternate CD?

---

### Post by Mephy on 2008-02-18
I have absolutely no clue how to fix this, and I've been searching for a while.

I don't really know anything about the installer or the 'text installer' or 'expert mode' or anything, but shouldn't it be fairly simple to install GRUB being that it's one of the major aspects of installing Ubuntu. Don't a lot of people dual-boot it? How come none of them have this problem?

Edit:

This is getting worse and worse, I tried to load into Windows (just by restarting) and when it turned on, it started to play the welcome music, then got stuck and sounded like a broken CD player. Then it automatically rebooted.

Then I tried to go back to the live CD for Ubuntu, and it only loaded the wallpaper with the Install icon and Examples icon, (no top or bottom menu).

I'm now in Safemode and this is the only thing that seems to work

Edit 2:

I just got a BSOD in Safe mode...

Could Ubuntu really have affected my Windows HD this much? Something's wrong. I haven't even changed anything since the installation!

---

### Post by confused57 on 2008-02-18
Here are a few methods to restore your Windows IPL(Initial Program Loader) to the mbr of your Windows drive:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Read some of the methods described in the link...if you have a Windows install cd(not a recovery cd), you can enter recovery mode by pressing "r", then use the command FIXMBR.  If you have access to another computer, Super Grub Disk can restore your mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Since you have 2 hard drives, when you install Ubuntu, set the drive you're installing Ubuntu to as the first hard drive booted in bios...near the end of the install, there is an "Advanced" button in the lower right portion of the screen that you can click...this will allow you to specify where to install grub(the default is hd0)...you can type in /dev/sdb, or however your Ubuntu drive is recognized by the installer.

This should install grub's IPL to the mbr of your Ubuntu drive...if you have problems booting Windows from grub, you can just set your bios to boot first to your Windows drive in order to boot Windows.

As mentioned, you can use the alternate install cd:
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

It might help to post what video card you're using.

---

### Post by Mephy on 2008-02-18
Ok, kinda funny cause I was in the middle of typing my thank you response and my computer rebooted :}.

Anyways, thanks so far, here's what I got so far:

I don't know why I didn't think about the boot priority but I just went into BIOS and changed it to have the Ubuntu HD boot first. All is fixed with GRUB now.

Next: I boot into Ubuntu, and I get an update note and update drivers note, so I click them both and they both close, then I boot into Firefox, and everything's still working. Then I try to come to ubuntuforums.org, and the screen goes black. Then I get a few lines in a command prompt thing (full screen), I forget exactly what they were but it looked something like this (i think 4 lines):
................................[OK]
................................[OK]
Checking Battery Life        [OK]
................................[OK]

That screen flickers a few times, then I go to this like weird blue screen with a border of all random characters and it says something like:
...has restarted 6 times in the past 90 seconds. This probably means something is bad. Trying to restart in 2 minutes.
Then there was an OK button but I couldn't click it or hit enter or anything.

So that was Ubuntu, I press the retsart button and try booting into Windows. everything worked and I was surprised. Then I click the Firefox icon, and it immediately goes to the "Send Error Report", "Don't Send" screen. I tried starting Firefox a few times and the same thing happened

So I try loading internet explorer. That works, and I come here. I started typing my thank-you and was going to tell you about the issues up to this point, and my computer restarts. Then I try loading into Windows again, and once again, it freezes at the welcome music and restarts.

Now I'm on my other computer cause the other one is a disaster!

What's going on? :{ I feel like it's either the HD (would make sense) or the video card (not sure why, but I have a feeling it has something to do with this, but booting isn't the problem anymore, it's running).

---

### Post by confused57 on 2008-02-18
Yes, it does sound like some kind of hardware, or possibly overheating problem?  I probably couldn't really advise you to try anything you haven't already thought of...maybe going into bios and checking something like "PC Health/Monitoring" for temps, fan speeds, etc.  I don't know anything about laptops, but maybe open it & blow out any dust with compressed air?

---

### Post by Mephy on 2008-02-18
I'm not on a laptop, I hadn't had any troubles until now with my temps, here's my stuff:

500 gig samsung
300 gig samsung (ubuntu)
core2duo e6300 @ 1.8ghz
2 gb crucial ballistix ddr2 800
video: Radeon x1800GTO 256MB GDDR3

Edit:
oh and a nice Zalman heatsink (not the crappy heatsink that comes with all intel cpus):

and my CPU temp is 23C. (I don't think it's the CPU ;} )

i don't know how to find the GPU temps without running an app, and I can't run any apps because I can't run windows..

---

### Post by Mephy on 2008-02-18
By some miracle, I got my comp running and SpeedFan loaded, and all my temps are either have the little blue arrow for nice and cool, or the check mark for good temperature..

I'm gunna run TAT to see if it's my CPU, wish me luck!

OK, ran it. Temps went up to around 50C for the cores and like 40 or so for the CPU.. No crash, it's not the CPU.

My GPU temp is 40C  (i think. I'm guessing Temp 1 is my GPU on speedfan because  when i did TAT it didn't really go up, and TAT is strictly CPU)

---

### Post by confused57 on 2008-02-18
> **Mephy said:**
> I'm not on a laptop, I hadn't had any troubles until now with my temps, here's my stuff:

500 gig samsung
300 gig samsung (ubuntu)
core2duo e6300 @ 1.8ghz
2 gb crucial ballistix ddr2 800
video: Radeon x1800GTO 256MB GDDR3

Edit:
oh and a nice Zalman heatsink (not the crappy heatsink that comes with all intel cpus):

and my CPU temp is 23C. (I don't think it's the CPU ;} )

i don't know how to find the GPU temps without running an app, and I can't run any apps because I can't run windows..
Don't ask me how I assumed you were using a laptop, everyone knows what assuming does.
You have a very nice system and definitely not an overheating problem.  You might want to start a new thread in the "Hardware & Laptops" section of the forum, describing your problem & provide a link to this thread.  Hopefully someone more experienced with computer hardware  problems will be able to help you.
Good luck.

---

### Post by Mephy on 2008-02-18
Thanks a lot for your help,

Everything seems to be working fine again actually, I'm in Windows, on Firefox for about 5 mins now and no crashes yet, I'll try Ubuntu and if it crashes i'll go make a thread in the other forum.

+Thanks again for all your help

---

### Post by Mephy on 2008-02-18
Yep, everything's working fine now, maybe during the installation something got hot, and it just needed a few mins to cool down, because I was restarting the whole time before, then I shut it off and used the other computer and when I came back it was fine.

Thanks everyone

---

### Post by confused57 on 2008-02-18
Glad to help & that it's working...thought I may be able to help a little with booting problems, not so much for hardware problems.   Enjoy your dual boot.

---

