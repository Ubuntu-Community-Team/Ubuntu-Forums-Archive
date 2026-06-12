---
title: "Installation questions, and UNetbootin"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by OttoDestruct on 2007-10-24
I'm trying to fix up an old dell Inspiron 1000, however, for some reason, the cd drive doesn't want to read the Ubuntu CD (I've tested the CD in other machines - its a good cd). The cd drive will work with other CD's.

I wanted to see if Ubuntu would even be very compatable before I began the process of backing data up and installing blindly, but seeing as I can't get the CD to work, I can't get into a live-session. Is there any way to do this without modifying my existing partitions, and without booting off the CD? (The bios unfortunately can't boot from a flash drive, already tried that).


I've been looking into Unetbootin as far as installation (this still doesnt solve wanting a live session). If I install Ubuntu with [UNetbootin](http://lubi.sourceforge.net/unetbootin.html), will it be possible either during the install to nuke the Windows partition, or after the install to delete the partition from within Ubuntu, and add the extra space?

---

### Post by taurus on 2007-10-24
Can you be a little more specific about not able to boot from the CD?  How much RAM does that old machine have?  Perhaps you should use the alternate CD to install it instead of the LiveCD (Desktop CD) if you don't have enough RAM.

Also, try to burn it at a slow speed like 4x since some old CD drives have problems reading a fast burn CD media.

---

### Post by OttoDestruct on 2007-10-24
The bios gives a "please insert bootable media in drive". and it can't be read when inserted while windows is running. I'll try out burning at 4x. I actually thought that might be a problem - I burned at 12x, but it still seems like a bit of a long shot.

---

### Post by taurus on 2007-10-24
> **OttoDestruct said:**
> The bios gives a "please insert bootable media in drive". _**and it can't be read when inserted while windows is running**_. I'll try out burning at 4x. I actually thought that might be a problem - I burned at 12x, but it still seems like a bit of a long shot.

I am a little confuse about that statement.  You try to boot from the CD so what does it have to do with Windows running?

I assume you did look in the BIOS to make sure you have CD-ROM as the first boot device.

---

### Post by OttoDestruct on 2007-10-24
When I'm running windows it can't read the CD. Theres no errors, it just spins, and explorer doesn't show that anything has even been inserted into the drive.

When I try to boot from the CD, it gives me the media error message.

The disk works - I've tested it in multiple machines. The drive works - I can insert other discs (commercial discs, or burned cdr/rw/dvdr) . The disc and the drive don't work together. Which is why I'm trying the first recommendation and burning at a slower speed.

Sorry for not being clear.

Burned at 12x
VVV

---

### Post by taurus on 2007-10-24
Yeah, how fast did you burn it?  See if you can boot from it with a slower burning CD, 4x.

---

### Post by OttoDestruct on 2007-10-24
Tried at 4x and it still isn't working either in windows or just trying to boot off of it.

I did, however, discover I was trying to use the wrong method from before to boot off of the flash drive. I tried a couple methods I found from google, but they give me "Error loading operating system".

---

### Post by taurus on 2007-10-24
You are saying that you cannot view the content of the CD even in Windows!  How did you burn it and which app did you use to burn it?

---

### Post by OttoDestruct on 2007-10-24
I can't view it in windows on the specific machine I'm trying to install it on. It works on other machines - I can view it / boot from it.

Burned at 4x, once with burn protection and finalized, once without burn protection and finalized, once with burn protection and not finalized, once without either. Four different CDs that worked in other systems but not the laptop.

Also, note in a previous post, I've already said, the drive works. It works with commercial CD's, other burned CDs (CDr/rw/DVDr). For some reason it isn't working with these discs though.

Which is why I'm trying to get the flash drive method to work, but thats not working either.

Sigh, I'm about to just go to windows, at least I can install it before it gives me problems, instead of having problems before it can even get installed.

---

### Post by OttoDestruct on 2007-10-24
Sigh. Trying this here since I haven't got one single useful reply from the Installation forum.

I'm trying install Feisty on a dell Inspiron 1000, however, for some reason, the cd drive doesn't want to read the Ubuntu CD. The cd is burned at 4x, I've tried all combinations of burn protection and finalization on and off: all with the same result that the laptop can't read the CD in windows (it justs sits and spins, and doesn't come up with any data on it, also, no errors actually appear), and I can't boot off of it. The drive works. I've tested it with commercial CDs, and burned CDs(r/rw/dvdr). The discs I burned work. I've tested them on a couple machines, and was able to enter live sessions on them, as well as read them from windows. For some reason though, the laptop apparently hates Linux and refuses to read them.

I wanted to run a live-session before I decided to mess with any of the existing stuff install Ubuntu. This is proving difficult without being able to read the CD, however. I've tried several methods booting from a flash drive, but each one of those keeps saying "Error loading operating system". So what do I do now? Installing from a network isn't an option - I don't have the time / resources to move the stuff around so that I could do that.

I considered trying [UNetbootin](http://lubi.sourceforge.net/unetbootin.html), but that gives me no way to go into a live-session as far as I can tell. Not happy with that. If I installed this way via windows - could I install off the hard drive as described, then delete the windows partition afterwards and add it to the linux partition - and would that screw up grub?

---

### Post by PmDematagoda on 2007-10-24
Can you see any data on the CD using Windows after you burn it?

---

### Post by OttoDestruct on 2007-10-25
> **PmDematagoda said:**
> Can you see any data on the CD using Windows after you burn it?

No, it doesn't show any data on the laptop (does with other computers). The laptop spins it up for a bit with an hourglass showing in explorer, then just quits and it doesn't show anything. I can click it and it just shows it as having no content.

---

### Post by OttoDestruct on 2007-10-25
Anyone out there?

---

### Post by OttoDestruct on 2007-10-25
Bumping hoping someone will actually help.

Edit: Woops wrong tab

---

### Post by OttoDestruct on 2007-10-25
Bumping again. Gee I just love how amazingly helpful the support for this OS is.... sigh.

---

### Post by OttoDestruct on 2007-10-25
Bumping. I find it hard to believe nobody knows anything.

---

### Post by OttoDestruct on 2007-10-25
Bumping, any ideas?

---

### Post by OttoDestruct on 2007-10-25
Posting this the third time seeing as the other two times (both in different forums), the only people to post never even read what I had typed.

Sigh. Trying this here since I haven't got one single useful reply from the Installation forum.

I'm trying install Feisty on a dell Inspiron 1000, however, for some reason, the cd drive doesn't want to read the Ubuntu CD. The cd is burned at 4x, I've tried all combinations of burn protection and finalization on and off: all with the same result that the laptop can't read the CD in windows (it justs sits and spins, and doesn't come up with any data on it, also, no errors actually appear), and I can't boot off of it. The drive works. I've tested it with commercial CDs, and burned CDs(r/rw/dvdr). The discs I burned work. I've tested them on a couple machines, and was able to enter live sessions on them, as well as read them from windows. For some reason though, the laptop apparently hates Linux and refuses to read them.

I wanted to run a live-session before I decided to mess with any of the existing stuff install Ubuntu. This is proving difficult without being able to read the CD, however. I've tried several methods booting from a flash drive, but each one of those keeps saying "Error loading operating system". So what do I do now? Installing from a network isn't an option - I don't have the time / resources to move the stuff around so that I could do that.

I considered trying [UNetbootin](http://lubi.sourceforge.net/unetbootin.html), but that gives me no way to go into a live-session as far as I can tell. Not happy with that. If I installed this way via windows - could I install off the hard drive as described, then delete the windows partition afterwards and add it to the linux partition - and would that screw up grub or fstab?

---

### Post by OttoDestruct on 2007-10-25
Bump.

---

### Post by swisscow on 2007-10-25
The obvious question is have you burnt it as an iso rather than a data cd? I believe (and I could be wrong because it's been a while) that Nero can do this. If you don't have it there is a windows application for free called ISO Recorder which will do the job.

Sorry if you already have this answer - I haven't read your other posts.

---

### Post by OttoDestruct on 2007-10-25
> **swisscow said:**
> The obvious question is have you burnt it as an iso rather than a data cd? I believe (and I could be wrong because it's been a while) that Nero can do this. If you don't have it there is a windows application for free called ISO Recorder which will do the job.

Sorry if you already have this answer - I haven't read your other posts.

Looks like you didn't bother reading this one either.

[quote=Ottodestruct]The discs I burned work. I've tested them on a couple machines, and was able to enter live sessions on them[/quote]

---

### Post by Henry Rayker on 2007-10-25
The OP said that he/she tried the disks in other computers and was able to load them up without a problem. (Unless I read wrong...) If that is the case, it is obviously something to do with your machine...

Going from there, have you made sure that the BIOS is set to boot from CD? Have you loaded ISO burned disks on the laptop before? I mean, a music cd will load up in some drives just fine (as will data burned on a disk) but those same drives will **** the bed when they're given an ISO type disk...

---

### Post by swisscow on 2007-10-25
> **OttoDestruct said:**
> Looks like you didn't bother reading this one either.

Actually read it all - just missed that bit. And as you obviously haven't got the good grace to appreciate trying to help I'll step aside and wish you the best of luck with your problem.

---

### Post by mramsey on 2007-10-25
Did you create your cd with that same drive?  If not could be a bad cd drive. Will it read any other cd's?  I have had this happen before.

---

### Post by Excalibre on 2007-10-25
Well, probably no one's answering because the question's sort of puzzling. You have a CD that works on every machine BUT your laptop, and you have a laptop that will read every CD BUT this one - is that correct? You've checked that it's set to boot from a CD before the hard drive, right? Have you tried burning a CD from a different batch? CD-Rs vary in quality and there's variation in what one drive or another is willing to read; real CDs, CD-Rs, and CD-RWs have somewhat different optical characteristics and different brands can differ as well. It's not a great answer but it's at least worth trying burning a different brand of CD-R and seeing if that helps.

---

### Post by OttoDestruct on 2007-10-25
> **swisscow]Actually read it all - just missed that bit. And as you obviously haven't got the good grace to appreciate trying to help I'll step aside and wish you the best of luck with your problem.[/quote]

I appreciate help when its useful. You offered no help though. I've posted this thread in three different sections now - and nobody has been helpful - in fact the only person to even reply gave me an answer like yours where they didn't even read what I had posted.

[QUOTE=Henry Rayker said:**
> The OP said that he/she tried the disks in other computers and was able to load them up without a problem. (Unless I read wrong...) If that is the case, it is obviously something to do with your machine...

Going from there, have you made sure that the BIOS is set to boot from CD? Have you loaded ISO burned disks on the laptop before? I mean, a music cd will load up in some drives just fine (as will data burned on a disk) but those same drives will **** the bed when they're given an ISO type disk...

Yes the bios is set. Yes I've loaded discs burned from ISO's before, using multiple types of media (cd/r/rw/dvdr). Windows won't see any data on the Ubuntu disc, and the bios won't boot from it. The discs work in multiple other machines, where I'm able to see the data on the disc inside windows, as well as boot from them into live-sessions.

[quote=mramsey]Did you create your cd with that same drive? If not could be a bad cd drive. Will it read any other cd's? I have had this happen before.[/quote]

Thanks for not reading my post, either. The drive isn't bad. Please go back and read the first post. I detailed that the drive isn't bad. To answer the other question that hasn't already been addressed - the drive isn't capable of burning CD's, I'm burning them on another machine.

---

### Post by OttoDestruct on 2007-10-25
> You have a CD that works on every machine BUT your laptop, and you have a laptop that will read every CD BUT this one - is that correct
Yes
> You've checked that it's set to boot from a CD before the hard drive, right?
Yes
>  Have you tried burning a CD from a different batch?
Yes. Different brand CD-R's, as well as a CD-RW.

---

### Post by voteforpedro36 on 2007-10-25
You could try the alternate installation CD.

Sorry if I'm no help...

---

### Post by OttoDestruct on 2007-10-25
> **voteforpedro36 said:**
> You could try the alternate installation CD.

Sorry if I'm no help...

I want to go into a live-session before I install. Can the alternate cd do that? Totally forgot about it.

---

### Post by Excalibre on 2007-10-25
Okay, then, you'll need a young priest and and old priest . . .

---

### Post by OttoDestruct on 2007-10-25
> **Excalibre said:**
> Okay, then, you'll need a young priest and and old priest . . .

What if its a Buddhist laptop? :)

---

### Post by voteforpedro36 on 2007-10-25
> **OttoDestruct said:**
> I want to go into a live-session before I install. Can the alternate cd do that? Totally forgot about it.


I'm not sure, I've personally never tried it.

Why do you want to go into a live session? You say you've done it on other computers, or is it just a hope-it-works-with-my-hardware situation?

---

### Post by OttoDestruct on 2007-10-25
> **voteforpedro36 said:**
> I'm not sure, I've personally never tried it.

Why do you want to go into a live session? You say you've done it on other computers, or is it just a hope-it-works-with-my-hardware situation?

Yep, hit the nail on the head. I realize running live will be slow compared to an actual install, but I would at least like to see how well the display, and such interact.

---

### Post by forestpixie on 2007-10-25
it'd peacefully do as you ask - but that doesn't seem to be working. Or have you been shouting at it :-k

Can't actually help with the problem - quite bizarre. The only thing I'd be able to suggest is either reporting it and asking the mods to move it to the abs beg - where people appear to look more frequently or posting there.

Sorry I can't be of more help :(

---

### Post by LowSky on 2007-10-25
is the iso data on your hard drive still?

use daemon tools and mount the iso and see if it can be read in windows

or use a program called md5sum to check the iso data

---

### Post by OttoDestruct on 2007-10-25
> **LowSky said:**
> is the iso data on your hard drive still?

use daemon tools and mount the iso and see if it can be read in windows

or use a program called md5sum to check the iso data

Read my first post.

---

### Post by OttoDestruct on 2007-10-25
Bump

---

### Post by rafkin on 2007-10-25
You might find it difficult to get help when you keep sh**ting on the people with the experience and good grace who try. I too am a noobie but would never react to the community the way you have. These are very helpful, and I might add busy people, taking time to try and correct your problem for you and you repay them with rudeness instead of thanking them for trying. Perhaps all the replies might not be useful but a thankyou is still needed. I do  not have the experince or knowledge to help with your problem but I would step aside if I did. All I can give is best of luck.

---

### Post by OttoDestruct on 2007-10-25
> **rafkin said:**
> You might find it difficult to get help when you keep sh**ting on the people with the experience and good grace who try. I too am a noobie but would never react to the community the way you have. These are very helpful, and I might add busy people, taking time to try and correct your problem for you and you repay them with rudeness instead of thanking them for trying. Perhaps all the replies might not be useful but a thankyou is still needed. I do  not have the experince or knowledge to help with your problem but I would step aside if I did. All I can give is best of luck.

Whats the point of trying if you aren't even going to do a job half-right, though? All it does is waste everyones time. The "help" they did offer clearly proved they hadn't even bothered to read the problem to begin with. Good intentions don't make you a saint.

---

### Post by mramsey on 2007-10-25
have you tried 6.06 or 7.04? it could be that the kernel in 7.10 does not agree with your hardware. 

perhaps you should start looking for a harware conflict with the kernel.  search for your laptop model in the forums to see if anyone else has the same issue.  

making multiple posts in the forums is frowned upon here.  if you are not getting responses it is probably because no one has an answer.  leaving replies that seem disrespectful to the people that attempt to help will likely leave you with no answers as well.  good luck with your issue.

---

### Post by OttoDestruct on 2007-10-25
> **mramsey said:**
> have you tried 6.06 or 7.04? it could be that the kernel in 7.10 does not agree with your hardware. 

perhaps you should start looking for a harware conflict with the kernel.  search for your laptop model in the forums to see if anyone else has the same issue.  

making multiple posts in the forums is frowned upon here.  if you are not getting responses it is probably because no one has an answer.  leaving replies that seem disrespectful to the people that attempt to help will likely leave you with no answers as well.  good luck with your issue.

Again, if you read the first post, youll see that I'm trying to use Feisty (7.04).

---

### Post by Incense on 2007-10-25
Do any other live CD distros run on this computer? You ruled out the disc already, so it's something with this computer. You can just bite the bullet and run the alt install CD. No it's not live, but you'll be able to install (text based). I have a dell over here that I can't run the live disc on, but the alt will install just fine. Although, it was able to run dapper live, but nothing else... so you could always give that a go. 

Good luck.

---

### Post by OttoDestruct on 2007-10-25
> **Incense said:**
> Do any other live CD distros run on this computer? You ruled out the disc already, so it's something with this computer. You can just bite the bullet and run the alt install CD. No it's not live, but you'll be able to install (text based). I have a dell over here that I can't run the live disc on, but the alt will install just fine. Although, it was able to run dapper live, but nothing else... so you could always give that a go. 

Good luck.

I'll give that a try.

---

### Post by bapoumba on 2007-10-27
> **OttoDestruct said:**
> I'm trying to fix up an old dell Inspiron 1000

> **taurus said:**
> Can you be a little more specific about not able to boot from the CD?  How much RAM does that old machine have?  Perhaps you should use the alternate CD to install it instead of the LiveCD (Desktop CD) if you don't have enough RAM..

Merged all the related threads here.
Having low specs laptops myself, please answer taurus's question. I know I have never been able to run a live cd on them. I always install from the alternate cd, not even the full desktop, just a minimal text-mode install, and work from there.

---

