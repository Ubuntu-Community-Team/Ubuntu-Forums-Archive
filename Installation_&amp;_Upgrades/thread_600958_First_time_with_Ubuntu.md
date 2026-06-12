---
title: "First time with Ubuntu"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by handrew on 2007-11-02
So a friend said hey, let try Ubuntu! I said sure! I also said but I dont want to disturb my Vista install which is Raid 1 between 2 320gig frives, so I went out and bought a 3rd 320gig drive. I installed it and booted from Ubuntu CD 7.10 which I just downloaded. So it took me to a screen that gave me all the drives and I picked the one I just installed. It "seemed" to have installed Ubuntu on that drive, It left Vista alone and I entered the Bios boot menu on my HP and picked the new drive to boot from where Ubuntu was installed on. The screen came up with, are you ready for this?, Came up with "No Operating System foud". So thats my story! Hey, I thought Ubuntu was EZ as pie to install. What gives? I may just forget I tried this, its not there yet is it?

---

### Post by tact on 2007-11-03
> **handrew said:**
>  Hey, I thought Ubuntu was EZ as pie to install. What gives? I may just forget I tried this, its not there yet is it?

Its there.  Sadly you are not.  You just don't understand how to boot what you just installed.

I'd need to ask a few questions or make a few guesses to assist.  So here goes....

You fitted a new drive to your rig just install ubuntu on.  Very good.  Was it the only drive in the system (or the only drive enabled) in the system bios WHEN you installed ubuntu?   Cos thats the only way the bootloader will be installed on the same drive as you installed the rest of the ubuntu OS...  and thats the only way you will find a boot sector on that drive and boot that drive by selecting it in bios.

If there were other drives connected, your raid for example, when you chose to install ubuntu to a specific HDD it very likely installed its bootloader on the 1st boot drive.  (Have you tried to boot your vista since installing ubuntu?   hehehe...)

EDIT:  just re-read your note and see a comment that indicates all your other drives were connected when you installed ubuntu
Ok I note another comment indicating your vista seems undisturbed...  so where did you install grub?  Did you skip installing grub? (bootloader)

So respond with some more info if you really want help sorting out your inexperience with a new OS.  If you are just tlooking to insult ubuntu users and bait some flame hooks...  naaaahhh...  not interested.

hehehehe one last edit..  who said ubuntu is as easy as pie to install?  Thats not in the literature.  But is easier than linux has ever been to install, and I reckon easier than windows to install to a blank HDD...  but all that said - installing any OS is never a trivial task.

---

### Post by TRStealthX on 2007-11-03
> **handrew said:**
> So a friend said hey, let try Ubuntu! I said sure! I also said but I dont want to disturb my Vista install which is Raid 1 between 2 320gig frives, so I went out and bought a 3rd 320gig drive. I installed it and booted from Ubuntu CD 7.10 which I just downloaded. So it took me to a screen that gave me all the drives and I picked the one I just installed. It "seemed" to have installed Ubuntu on that drive, It left Vista alone and I entered the Bios boot menu on my HP and picked the new drive to boot from where Ubuntu was installed on. The screen came up with, are you ready for this?, Came up with "No Operating System foud". So thats my story! Hey, I thought Ubuntu was EZ as pie to install. What gives? I may just forget I tried this, its not there yet is it?

You may want to try 7.04 (Feisty) instead, 7.10 has been giving problems with some computers - so yea. Trust me, Ubuntu is very well worth it. I definitely recommend you giving it another try before taking a final decision.

---

### Post by tubasoldier on 2007-11-03
> **tact said:**
> Cos thats the only way the bootloader will be installed on the same drive as you installed the rest of the ubuntu OS... 

Not quite. your kind of wrong here. There is a window, (its been a while so I'm not sure exactly which one,) during the install. it is near the end and it gives you an overview of what you are going to do. there should be an "advanced" button in that window somewhere. That is where you can choose what drive to install your bootloader onto.
[URL="http://www.cyberciti.biz/faq/linux-partition-naming-convention-and-ide-drive-mappings/"]
sd0 is default if i remember correctly.
sda(0,0) is the same location.
sda(0,1) is the same disk, next partition
sda(1,0) next disk
sda(2,0) third disk.[/URL]

click on the above text to help you understand what i'm saying better. Its late and i'm sure my brain is not putting things together correctly. 

Good luck.

---

### Post by tact on 2007-11-03
> **tubasoldier said:**
> Not quite. your kind of wrong here. There is a window, (its been a while so I'm not sure exactly which one,) during the install. it is near the end and it gives you an overview of what you are going to do. there should be an "advanced" button in that window somewhere. That is where you can choose what drive to install your bootloader onto.
[URL="http://www.cyberciti.biz/faq/linux-partition-naming-convention-and-ide-drive-mappings/"]
sd0 is default if i remember correctly.
sda(0,0) is the same location.
sda(0,1) is the same disk, next partition
sda(1,0) next disk
sda(2,0) third disk.[/URL]

click on the above text to help you understand what i'm saying better. Its late and i'm sure my brain is not putting things together correctly. 

Good luck.

Yup tubasoldier you are right...   seems our friend the OP had said he used bios to "boot" the drive that he installed ubuntu onto - I was just trying to say that if the defaults were left the only why to be sure you could boot like that is if that installation drive was the only one installed at the time (otherwise it "may" be that the bootloader gets defaulted to some other drive seen as the first primary).

Guess I didnt word it clearly.

Because it is selectable (if you do the advanced thing) is why I asked "where did you install the bootloader then?"  :)

---

### Post by handrew on 2007-11-08
Well finally what I did was play it safe. I Bought a 3rd hard drive, 320gig, cheap, and installed it. I disconnected my Raid 1 drives which have vista on them mirrored. I installed Ubuntu 7.10 and the grub thingy. It booted up well and picked up most of the hardware. Not the Hauppauge WinTV HVR-1600 NTSC/ATSC Combo so you know :). Then I reconnected the raid drives and hit the escape key at startup of this HP computer. Got into the bios boot menu where it gives me a chose of which ard drive I want to boot from. So now I can boot Vista or Ubuntu and didn't do any funny stuff with the grub thinhy or the boot facility in Vista. Now I wait in a period of gestation for the gurus out there to write a full featured driver for the TV card and then I will install the add-0n MYTHubuntu. The future is promissing. My power apps still reside on Windows to be honest.

Cheers people!

Andrew

---

### Post by potentia on 2007-11-08
> **tact said:**
> So respond with some more info if you really want help sorting out your inexperience with a new OS.  If you are just tlooking to insult ubuntu users and bait some flame hooks...  naaaahhh...  not interested.


Why did you include this paragraph? "Insult" ... you guys are so sensitive. Why did you have to write a disclaimer like this? The OP'er was obviously the curious type.

I wonder how you survive in the real world.

---

### Post by handrew on 2007-11-08
Oh I wasn't taken aback by his suggestion that I was trying to insult the community. I was surprized to read it though! When power users read posts from people who only laid eyes on Ubuntu the night before and have never heard of Linux and try it and fail it is expected to get posts like the one I posted at the start of the thread. power users forget the day they first started with linux etc. Its a funny world we live in with all sorts of flexable and unflexable people in it. We carry on....

Now that I have it installed and its running I dont see many mature full featured programs to install. I'd love to see a Winamp-like program for starters. Am I restricted to drawing from the repositories for programs? Are there any commercial applications I can "buy" to install on Ubuntu? I'm willing to pay for a power app! How di I compile what is called a source? Will any source compile on his ubuntu? So many questions, but not bad for a guy who never heard of linux until 4 days ago huh?

---

