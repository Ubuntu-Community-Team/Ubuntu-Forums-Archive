---
title: "Dear Friend. I'm angry. SATA drive isn't picked up during Hardy install."
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2008-10-09
Okay, so I built a new rig. I have a 500GB SATA drive and an ASUS p5ql Pro motherboard.

In BIOS, the drive shows up.

In Ubuntu, it says no drives detected when I go to install.

I already have a 40 gb NTFS partition with XP Pro on it. So I know the drive is fine.

What can I do?

---

### Post by dabl on 2008-10-09
> **Roasted said:**
> 

What can I do?



Go into BIOS, and play with the modes for the SATA bus.  Try "AHCI" first.  Then "Legacy", if you have it.  :)

---

### Post by Roasted on 2008-10-09
Somebody else just told me to try AHCI. I did an internship at a school district earlier this year. We got in 400 Lenovo laptops. In order for the cloned laptops to boot, we needed to turn off AHCI and set them to "compatibility" mode. 

I even saw AHCI last night. But I ignored it due to my experience at my internship. I thought for sure if it didn't work there, it wouldn't work here with my computer.

AHH

---

### Post by Roasted on 2008-10-09
Okay, here's the scoop.

XP requires IDE mode to run.
Ubuntu requires AHCI to even see the hard drives to install.

We all know AHCI is finicky, and, kinda sucks.

So, my question is: Why is Ubuntu a bitch? I need XP and Ubuntu. Yet I can't run IDE and AHCI at the same time. Why can't Ubuntu run in IDE mode?

---

### Post by Dynamo_Joe on 2008-10-10
Hi Roasted, 

Read in another forum post is that if you want Windows and Ubuntu on the same machine, both have to be set to use AHCI during installation if you are using SATA drives. 

That means you may need to re-install windows with the BIOS set to AHCI first ...

Ubuntu can be installed on IDE drives ... it's just that you read real physical IDE drives ... it is a known issue (IDE emulation for SATA drives).

---

### Post by cariboo on 2008-10-10
ACHI is not finicky, it is Windows XP that can't deal with SATA drives. But then what do you expect from a 7 year old OS. :)

Jim

---

### Post by mikewhatever on 2008-10-10
> **Roasted said:**
> 

So, my question is: Why is Ubuntu a bitch? I need XP and Ubuntu. Yet I can't run IDE and AHCI at the same time. Why can't Ubuntu run in IDE mode?

Watch the language.

---

### Post by confused57 on 2008-10-10
Maybe this will help:
[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)

---

### Post by hyper_ch on 2008-10-10
you can slipstream sata drivers into XP or load them during the initial install routine (by pressing F5).

I think if you slipstream your xp cd with SP3 then sata drivers will also be included - but I'm not 100% sure on that.

---

### Post by Roasted on 2008-10-10
> **Dynamo_Joe said:**
> Hi Roasted, 

Read in another forum post is that if you want Windows and Ubuntu on the same machine, both have to be set to use AHCI during installation if you are using SATA drives. 

That means you may need to re-install windows with the BIOS set to AHCI first ...

Ubuntu can be installed on IDE drives ... it's just that you read real physical IDE drives ... it is a known issue (IDE emulation for SATA drives).

When I boot up with AHCI installed, XP Pro CD in the tray, and boot to it, it doesn't find my hard drive.

XP can't see anything in AHCI.
Ubuntu can't see anything in IDE Legacy.

I think both instances are stupid for not cross supporting one another. IDE has been around how long? And XP has been around how long? 

What can I do? I keep hearing people suggest what you said to me, install XP with AHCI first. But I can't install the OS if the OS can't find the hard drive.

---

### Post by Roasted on 2008-10-10
> **mikewhatever said:**
> watch the language.

lol?

---

### Post by hyper_ch on 2008-10-10
have a read at my posts here: [http://ubuntuforums.org/showthread.php?t=943302](http://ubuntuforums.org/showthread.php?t=943302)

---

### Post by Roasted on 2008-10-10
> **hyper_ch said:**
> you can slipstream sata drivers into XP or load them during the initial install routine (by pressing F5).

I think if you slipstream your xp cd with SP3 then sata drivers will also be included - but I'm not 100% sure on that.

Yeah, I've heard that too. I have SP3 on my flash drive, and I have a laptop I can work with while I try to figure out what's up with my system.

What's the easiest way to slipstream SP3 to an XP Pro SP2 install? We all know SP3 will be too big for a floppy disc. What are my options then? I've heard a rumor that XP doesn't support USB connectivity for slipstreaming, but I'm not sure on that.

Also, what exactly is slipstreaming? Is that just hitting your F5/F6 (I've heard both) option before you boot up to the main install screen on XP and pulling the drivers through some type of external media?

---

### Post by hyper_ch on 2008-10-10
use nLite... it's really simple...

slipstreaming is (1) taking a windows install cd (2) extract its content to a harddisk (3) alter default stuff like username, password, timezones, keyboard layout, languages,..... for automated installations AND also remove and add drivers / service packs... (4) combine that all to a new install cd/dvd (5) boot with that modified version

I bet you got a few drivers to install... video drive, audio driver, wifi driver, .... you could integrate most (if not all) into a slipstreamed installation disc

---

### Post by Roasted on 2008-10-10
Oh, all right. So to start, slipstreaming is actually a 2 step process (making the install essentially twice as long) but later on it's a quicker way of doing things. Right? That sounds interesting.

So basically I have to do this.

Enable IDE Legacy mode, boot to fresh copy of XP, make the changes I want (drivers, SATA drivers, etc) and install nLite and basically, nLite that entire "image" to a new CD... to which it'll become XP + additives.

Am I on the right path?

---

### Post by hyper_ch on 2008-10-10
no, you first install a windows (somehow)... then you get nLite and remaster your windows install cd by adding service pack 3 and sata drivers... then you use that new install cd to make an insstall with ahci mode or wahtever it's called

---

### Post by Therion on 2008-10-10
IF you get this figured out [let me know](http://ubuntuforums.org/showthread.php?t=914515)?  

It baffled me when I was still dual-booting with XP (I've since given up) and I never was able to get all my drives recognized by both OS'es.  And frankly, I don't think it's related the presence of the SATA drivers on install.  I have and use an nLite Slipstreamed Windows XP install disc that contains SP3.  

Good luck and if you figure it out, drop me a line?

---

### Post by hyper_ch on 2008-10-10
as said, I'm not sure if SP3 contains sata drivers... I think it does... but to be sure go to your mainboards manufacturer and download the sata drives from there and also slipstream them.

---

### Post by Therion on 2008-10-10
> **hyper_ch said:**
> as said, I'm not sure if SP3 contains sata drivers... I think it does... 
SP2 is where MS finally got wise to the SATA drivers thing.  Might as well slipstream SP3 though, no reason not to.

---

### Post by Roasted on 2008-10-10
> **hyper_ch said:**
> no, you first install a windows (somehow)... then you get nLite and remaster your windows install cd by adding service pack 3 and sata drivers... then you use that new install cd to make an insstall with ahci mode or wahtever it's called

That's what I said. :P 

I can only install Windows via IDE Legacy mode. That's my only option. And since right now I have a base XP install (but I can only boot to it with IDE Legacy mode enabled) then I guess I could boot into that and install everything I need (SP3, drivers, etc) and nLite that exact copy.

So basically what it comes down to is this. I will be creating my own personal modified Windows XP Professional installation CD, personalized for my exact computer. After I obtain this CD, I need to format XP (the pre installed one I already have in) and install via my newly made CD. 

Then, switch BIOS to AHCI. Right?

---

### Post by hyper_ch on 2008-10-10
yes, that's right :) I guess I misunderstood you before

---

### Post by Roasted on 2008-10-10
I don't understand something.

Old system:

AMD 3000+ 1.8GHz S939 CPU
MSI K8N Neo-4 Platinum motherboard
2gb DDR 400 RAM

New system: 

Intel Q8200 Quad Core 2.33ghz LGA775
ASUS P5QL Pro Motherboard
4gb DDR2 800 RAM

In my old system, I ran a 250gb SATA drive. I had XP + Ubuntu on it. I never EVER set anything in BIOS. It just always worked from the get-go.

In my old system, I upgraded from a 250gb SATA drive to a 500gb SATA drive. I had XP + Ubuntu on it. I never EVER had any problems with it on my old system.

That 500gb SATA drive I spoke about directly above is the exact same SATA drive I am using now, on my new system.

If it's true that
-Ubuntu does not support IDE Legacy on SATA drives.
-Windows XP does not support AHCI by default.

How in the #@$&*((*@*(#* did I get it to work before without touching anything??

---

### Post by hyper_ch on 2008-10-10
you had XP preinstalled probably with sata drives and also a recovery partition with it.

---

### Post by cariboo on 2008-10-10
I think it really depends on you XP install disk. I had XP and Ubuntu installed on a sata drive with out having any problems. I have an OEM XP SP2 CD, didn't need to update it to SP3 for it to work. If you're having problems with XP maybe it time to update to a more modern OS.

Jim

---

### Post by Roasted on 2008-10-10
I used the same XP CD before as I did today. 

Also - I slipstreamed service pack 3, along with the SATA drivers into an ISO image made by nLite. I used nero in Windows to burn it as an image.

I just booted up to it.

Windows still doesn't have a damn clue what hard drives I got. This is unreal.

---

### Post by hyper_ch on 2008-10-11
that sux :(

---

### Post by raygj on 2008-10-11
> **Roasted said:**
> I don't understand something.

Old system:

AMD 3000+ 1.8GHz S939 CPU
MSI K8N Neo-4 Platinum motherboard
2gb DDR 400 RAM

New system: 

Intel Q8200 Quad Core 2.33ghz LGA775
ASUS P5QL Pro Motherboard
4gb DDR2 800 RAM

In my old system, I ran a 250gb SATA drive. I had XP + Ubuntu on it. I never EVER set anything in BIOS. It just always worked from the get-go.

In my old system, I upgraded from a 250gb SATA drive to a 500gb SATA drive. I had XP + Ubuntu on it. I never EVER had any problems with it on my old system.

That 500gb SATA drive I spoke about directly above is the exact same SATA drive I am using now, on my new system.

If it's true that
-Ubuntu does not support IDE Legacy on SATA drives.
-Windows XP does not support AHCI by default.

How in the #@$&*((*@*(#* did I get it to work before without touching anything??

****

the easiest solution (which I took) is to :-
1) If MSWINDOWs is already installed please skip to part 2) otherwise  install mswindows on your new disk using IDE mode(bios sata setting)
2) boot into mswindows and follow the INSTRUCTIONS IN THE MS KNOWLEDGE BASE IN THE FOLLOWING LINK ([http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976))
[http://support.microsoft.com/kb/922976]("http://support.microsoft.com/kb/922976")
3)after completing the above links instructions close down mswindows and reset sata mode to AHCI in bios 
4)reboot and test that mswindows starts correctly in AHCI mode. 
5) reboot and install UBUNTU with alternative live CD in TEXT MODE INSTALLER
6)Dual booting OK I was very happy with this Solution.
regards ray

---

### Post by Roasted on 2008-10-11
I got it to work. I was able to get XP running in AHCI mode.

What I did was, I used nLite to create a custom install disk. I went on the ASUS web site and downloaded the SATA driver and slipstreamed it to the install. Some of you are probably like, wtf, he was complaining about doing that earlier and it didn't work.

Thing was, the SATA driver didn't work. But there's a storage manager driver under Utilities on the ASUS web site which has the AHCI drivers I needed. WHY it was under Utilities instead of SATA, I have no idea. Poor organization, in my opinion.

But currently I am running XP Pro and Ubuntu Hardy 64 bit in AHCI mode just fine. Only thing is, I found out some information about my P5Q motherboard. Something about the controller causes Ubuntu to only run in AHCI mode, which is fine with me. Secondly, the onboard LAN isn't recognized. I've tried to dig up some drivers, but I get a bunch of littered posts with people having the same adapter on their Eee PC asking the same questions I am.

I can't seem to find a driver for it, so I'm thinking about copping out and buying a PCI card for it. Kind of sucks and aggrevates me, but ahh... ASUS DOES have a listing of their Linux supported boards, and from what I read the P5Q isn't one of them. Only drawbacks to it being fully supported is the LAN driver and it requiring AHCI to run.

I guess running in AHCI isn't a bad thing, after all, it's pretty much wave of the future, isn't it? 

Unless somebody can tell me how to install the Atheros AR8121 drivers for Ubuntu 64, I'll be heading out to Circuit City soon to grab a cheap PCI LAN card.

---

### Post by qwertymodo on 2008-10-14
any luck running ubuntu in IDE Legacy mode with the all_generic_ide boot parameter?

---

### Post by Roasted on 2008-10-14
> **qwertymodo said:**
> any luck running ubuntu in IDE Legacy mode with the all_generic_ide boot parameter?

Could you be a little more descriptive on how I would do this to see if it works?

---

### Post by norsgaard on 2008-10-14
I had the same problem but got the HD showing up in 8.04 by adding the line "irqpoll all_generic_ide" to the grub boot parameters. 

Probably what qwerty was talking about too.

And just to clarify, I was talking about running Ubuntu in IDE with a dual XP boot.

---

### Post by Roasted on 2008-10-14
I'm not thinking it was an OS problem, though. I used the same copy of Ubuntu on my new rig as I did my old rig. I googled a bit and read a review about somebody having problems with the P5 ASUS motherboard, saying that it is not "fully" compatible in Linux, however it runs in AHCI mode just fine. So basically, it sounds like it's a limitation of the motherboard that prevents my ability to run Ubuntu in IDE mode. Which, I really don't need IDE mode. I was just trying to find an option to get both OS's to work... either both on IDE or both on AHCI. 

After reading more about AHCI, it sounds like it's more along the lines of what the future is bringing anyway. And since it's a new rig, and they're all SATA drives, I figured... why not? 

So... I'm happy I got it to run in AHCI mode... XP that is. Ubuntu (as I said above) already worked with AHCI. 

:guitar:

---

### Post by qwertymodo on 2008-10-17
Ok, if you haven't installed Ubuntu yet, from the CD's Grub menu highlight the option to install but before you hit enter first hit f6 and you'll see a list of your boot parameters, then just add

all_generic_ide

to that line then hit enter.  If you've already installed it you have to highlight the first Ubuntu boot option (your normal option), and click 'e' then highlight kernel in the next menu and click 'e' again and type it there, then boot.  To make this permanent you'll have to manually add it to your menu.lst file in the grub directory.  If you do this you can switch your SATA drives back to IDE mode to play nice with XP.

---

