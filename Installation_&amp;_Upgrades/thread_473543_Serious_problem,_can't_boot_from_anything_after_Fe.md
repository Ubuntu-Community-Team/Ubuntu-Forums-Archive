---
title: "Serious problem, can't boot from anything after Feisty install."
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Martijn2 on 2007-06-14
Hi,
I've used Kubuntu Dapper Drake for a pretty long period (read: 1/2 weeks which is long for me) and decided to install the new Feisty Fawn disc which came by mail.
Kubuntu really let me down, I must say, at least in this version.
Dapper worked perfectly but Feisty immediately spewed out its first problems when I tried to connect with my WiFi card, for example.
I had to instal the Wireless Assistant for it to connect.
Anyway, it also gave me problems with GRUB, and I've been trying to restore the MBR for a while.
This didn't work out as expected and also plunged my Packard Bell EasyNote B3600 laptop in a unworkable state.
Every time I try to boot now, it says "Hard disk boot sector invalid. Press H to retry, any other key for floppy" :(
It won't let me boot from CD, nor let me enter the BIOS.

Any help? Or would I have to send it back to Packard Bell?
Thanks in advance!

---

### Post by Martijn2 on 2007-06-14
**bump**
I'm really desperate :(

---

### Post by linux noooob on 2007-06-14
well i really dont know but mabye you should re format the drive through a remote desktop to erase it and then try again

---

### Post by Herman on 2007-06-14
Hello Martijn2
>  It won't let me boot from CD, nor let me enter the BIOS.Why won't it let you boot up a Live CD and why won't it let you enter the BIOS?
You must have been able to do those things to have been able to run the LiveCD in the first place surely? ...and to install  Ubuntu.
Do you think a hardware problem may have occurred?
Regards, Herman :D

---

### Post by Martijn2 on 2007-06-15
Here's a video of the information that gets shown when you press F8 on my laptop: [link]("http://www.youtube.com/watch?v=xHKioiIQDSI").
A hardware failure couldn't have been the cause of this. It detects the HDD+CD and enables Smart.

---

### Post by Herman on 2007-06-15
Try removing the laptop battery completely from the laptop so that there is no power of any sort in the machine and then plug it back in again and see if that helps.
The idea is to clear your RAM modules. (to make sure they are empty).
Or try physically removing the memory modules and then  re-inserting them. Be aware of ESD if you decide to do that.

It's just something to try. 
Regards, Herman :D

---

### Post by Martijn2 on 2007-06-16
I tried the battery removal, but what is ESD? Waranty or something?
Also, could you give me a image of what notebook-RAM usually looks like?
Regards, Martijn2 ;)

---

### Post by Herman on 2007-06-16
:D E.S.D. is short for "_E_lectro-_S_tatic _D_ischarge, it's just the static electricity we get when we notice sometimes when we touch a doorknob or something and a tiny spark jumps, ever noticed that? It's enough to ruin computer parts, you need to ground yourself to the computer frame first with one of those wrist straps and a wire to the computer before you touch anything inside any computer. Maybe just don't bother with it, removing you battery for a few seconds should have been enough.
My idea was to check to make sure your RAM was emptied. Your predicament reminded me of one time I was helping a friend of mine install Ubuntu and just as we finished down loading a huge amount of updates and the updates were ready to be installed to his hard disk, his monitor fell flat on his keyboard and pressed every key at once and turned his computer off. 
I'm not saying that's what happened to you, all I'm thinking is the symptoms are quite similar, we couldn't do anything, we couldn't boot a Live CD to see what was wrong, all we could get was the Grub menu.
So we ran the memtest86+ memory test, that was about the only thing that would work. It came up with an ugly red screen and printed out nothing but endless memory failures! :(
We figured that his RAM might have been full when the computer was shut down so suddenly and now there was no more room for any Linux kernel in it. (To boot something, like an operating system or a Live CD the kernel has to be loaded into the RAM, that's what booting is all about). SO we opened up the computer case and removed the RAM modules (to empty the RAM) and then put them back in again and everything magically worked again! :D
I have since been told that just removing the power from the computer will do the same thing, so you don't have to take your computer apart. That's why I suggested removing the laptop's battery might be worth a try.
If that didn't help I wouldn't bother removing the RAM yet for now. Maybe we can think of some other way to find out what;s wrong.... Hmmm.

---

### Post by Herman on 2007-06-16
>  Anyway, it also gave me problems with GRUB, and I've been trying to restore the MBR for a while.
This didn't work out as expected and also plunged my Packard Bell EasyNote B3600 laptop in a unworkable state.
Every time I try to boot now, it says "Hard disk boot sector invalid. Press H to retry, any other key for floppy" :sad:
It won't let me boot from CD, nor let me enter the BIOS.Hmmm....I can't imagine how trying to restore Grub the normal way would be likely to cause that much trouble. 
Can you give me any more clues please?
What method were you using tio try to restore Grub? Can you link me to the how-to? Was it a 'dd' command or something?
Okay, I can easily imagine you getting the message, "Hard disk boot sector invalid. Press H to retry, any other key for floppy". That's an easy one. Your MBR is erased or at least the aa55h bootable disk indicator at the bottom of the MBR is missing or corrupt. That should be easy to fix if you can at least boot a Live CD.
I can't understand why you can't boot a LiveCD or even get into the BIOS. That's not consistent with any other computer problems I have ever heard of except the story I just told you in my above post.
Can you tell me more?
More clues please! :D
Regards, Herman

"Entering Boot Menu, please wait..." is at the bottom of your monitor. Yeah, that's like an empty or corrupted boot sector, but why can't you boot a live CD or get into the BIOS? 
Have you read the instruction manual the came with your computer about how to access your BIOS? 
It is your computer isn't it? (Not a stolen one or anything like that?) You should be able to get into the BIOS if it's your computer.

---

### Post by Herman on 2007-06-16
Here are some links on how to get into your BIOS,

[http://support.packardbell.com/asia/item/index.php?pn=PB21B00061&g=1400](http://support.packardbell.com/asia/item/index.php?pn=PB21B00061&g=1400)

> Press the <F2> key during POST in order to access the BIOS Setup screens.

[ EasyNote B3 BIOS Screens]("http://support.packardbell.com/asia/item/index.php?i=instr_bios_cougar_a&ppn=PB21B00061")

---

### Post by Martijn2 on 2007-06-17
Firstly, thanks for your kind replies. I really apreciate it that you take the time to type all that.
I'll add answers after I read it more carefully ;)
Edit: I'll be done with my last exam this Tuesday, so I'll be able to write more details the day after (it's late in the afternoon).
Edit2: Here's another video of my laptop: [http://youtube.com/watch?v=dI63fPn4LOk](http://youtube.com/watch?v=dI63fPn4LOk)

---

### Post by Herman on 2007-06-17
[http://youtube.com/watch?v=dI63fPn4LOk](http://youtube.com/watch?v=dI63fPn4LOk) Wow! :confused: That is a puzzling one.
Sorry I couldn't help you fix it in time for your exams. I'll think this over for a while, right now I'm out of ideas, but thanks for that video clip, a picture saves a thousand words, and I guess a video clip shows a thousand pictures!  :D
Bye for now, 
Regards, Herman

---

### Post by Herman on 2007-06-18
Okay, I've been thinking things over and I'm back to thinking it seems more like a hardware problem, not a software problem.
It looks like your computer is getting stuck at the end of P.O.S.T. just before booting begins. The fastest way to track down problems like this is to stick to a set sequence of tests. One thing I have been reminded of a few times lately is to make sure the hardware is right first, before looking at the software. 
Here is a great link from Computer Hope.com that has helped me several times, [POST Troubleshooting Steps]("http://www.computerhope.com/issues/ch000607.htm")

You may need to take your computer to a computer repair shop and have it checked out professionally if you don't have the right tools and aren't an expert with computer hardware.
If you are a do-it-yourself type like me, following those steps in that link should help you. I realize that because it's a laptop some of those steps won't apply to you, so just skip the ones that don't apply.  Steps #4, 7 & 8 might apply to you.
Often I have been able to fix my own computers for free just by removing and cleaning parts and putting the same parts back in place again.  I have no choice, from where I live it would be a day's drive to someone else who can fix computers and home again. For most people it would probably be quicker and safer to have the job done professionally. Sometimes new parts are required. Computer parts can fail anytime the same way a light bulb can. Mostly computer hardware is pretty reliable but everything man made must fail eventually, it's just a question of time. If it is a hardware problem it wouldn't have anything to do with Ubuntu or Grub, it's probably just a co-incidence that it happened at the same time. 
Regards, Herman :D

---

### Post by crxvfr on 2007-06-18
Tried flashing the bios? Sounds corrupted.

---

### Post by Martijn2 on 2007-06-21
Thank you for your reply,
I think it might be a hardware failure aswel, though I can't do the steps described in the website you posted. Except for removing the RAM (which doesn't help, and I tried multiple ways of placing them), I can't find any cables related to the HDD and CD for example to disconnect them from the motherboard.

Another thing I read somewhere else in this forum (Installation & Upgrade) is that the Feisty disc outputs multiple I/O-errors during boot (live system that is), which happened to me, too. I didn't pay much attention to the messages, because a) they where quite cryptic and b) the system booted fine, anyway, and c) the setup software didn't throw any error .

And no worry about not being able to help me fix it for my exams, since you are not forced to help me and I got a Dell with XP that's working excellently (Firefox as the main browser ofcourse :P). Anyway, I think now could be the time to go to the shop I bought it and make use of the extra warranty I bought along with it. That warranty's usable to somewhere in 2008, still :)

Would you describe the cause of my problems as  being a technical failure?

---

### Post by Herman on 2007-06-21
>  Would you describe the cause of my problems as  being a technical failure? I guess so, that would pretty well cover almost any kind of failure though wouldn't it? :D 
 Whoever fixes your computer will probably follow a systematic testing procedure and run tests until they can determine exactly what  part is causing the problem. 
Normally, the easiest way to run tests would be the either disconnect things one a time and see what happens as the link describes. A laptop would be a bit harder, maybe they can use extension cables to plug it into other parts or swap parts one at a time for known good parts until it works.
> Another thing I read somewhere else in this forum (Installation & Upgrade) is that the Feisty disc outputs multiple I/O-errors during boot (live system that is), which happened to me, too. I didn't pay much attention to the messages, because a) they where quite cryptic and b) the system booted fine, anyway, and c) the setup software didn't throw any error .
Yes, if you remove the 'quiet splash' option from your GRUB menu.lst you would see lots of white text scrolling on a black monitor background as your computer boots up. Sometimes they can be a useful clue to help us solve booting problems, but you would need to be an expert to be able to understand most of what they are about. Many of those lines could look like alarming errors to someone who isn't used to seeing them, but they could be just a normal part of the booting process. 
You can look at those if you want by typing 'dmesg' into your terminal, but you are probably right to think that if you computer boots up okay it is alright to ignore all that, especially if you can't understand it. I can only understand a little of it.  ```
dmesg
```> I think now could be the time to go to the shop I bought it and make use of the extra warranty I bought along with it. That warranty's usable to somewhere in 2008, still Yes, I agree, it's definitely better to let the accredited technicians do their work if your computer is under warranty. Maybe it's a faullty part and the factory has had a bad run of them and they might even already know what's wrong without testing and they'll replace it for you for free. 
What happens a lot in factories that make things is they don't pay the guy that knows how to adjust the machine enough money (to keep the cost of your new computer down), so he quits and gets another job somewhere else and then a new guy has to learn how to adjust the machine that makes some computer part. So they have days when a lot of bad parts get made and  quality control rejects the bad ones so those get thrown away or recycled. Some might be borderline and quality control might have trouble deciding if they're okay or not, so they might pass some that are borderline. They'll work in your computer for a while and then fail. That's what warranty is all about. :D
Regards, Herman :D

---

### Post by benben on 2007-06-23
> **linux noooob said:**
> well i really dont know but mabye you should re format the drive through a remote desktop to erase it and then try again

Don't TRY AGAIN.  I lost four disks by banging my head against that grubby wall. Thanks to Bill Gates' win98 DOS I managed to get one of them back to put XP back on it in a fat32 partition. Before that success, I tried spFdisk, XFdisk, and several others. The docs say that it is easy to recover with FDISK/mbr, but that is NOT TRUE.

I then tried mbrtools and mbrworks to no avail. Finally, as a last resort, I booted a win98 rescue floppy and regained my one of my disks.

Sorry. I can't waste any more time with problems like these.

BenBen

---

### Post by Herman on 2007-06-23
> Don't TRY AGAIN. I lost four disks by banging my head against that grubby wall. Thanks to Bill Gates' win98 DOS I managed to get one of them back to put XP back on it in a fat32 partition. Before that success, I tried spFdisk, XFdisk, and several others. The docs say that it is easy to recover with FDISK/mbr, but that is NOT TRUE.
I then tried mbrtools and mbrworks to no avail. Finally, as a last resort, I booted a win98 rescue floppy and regained my one of my disks.
Sorry. I can't waste any more time with problems like these.
BenBenWhat nonsense! Grub does not do any damage at all to anyone's hard disk, it's just people who don't understand what they are doing who imagine so. 
This is your first post in Ubuntu Web Forums, you haven't even tried asking anyone for help and you obviously have no idea what you are doing.
Why don't you try asking nicely for help sometime when you calm down and are in a better mood. 
No-one can help you unless you ask for help and provide some information describing your problem, You are just being like a screaming baby who can't express himself so he screams loud and long to attract attention.
Please ask ask properly and someone will help you.

---

### Post by Martijn2 on 2007-06-23
I want to thank you for taking the time trying to help me out, Herman. I really appreciate it! :)
I'm going to take it to the shop today since I have a very busy week behind me, and haven't had time to take it sooner ;)
Anyway, if it can be repaired, I'll reinstall Dapper Drake and wait for the next LTS version to be released. That seems safer to me.

---

### Post by Herman on 2007-06-23
Thanks for your vote of confidence there, martijn2, and thanks for sticking with me. Yes, the LTS versions are the best for people who just want a reliable system to get their work or studying done with the least amount of excitement. You are wise.

I am very curious to find out what the problem with your laptop turns out to be. I fix a lot of old computers in my spare time and and I have Scott Mueller's book '[Upgading and Repairing PCs]("http://www.quepublishing.com/promotion/1626")', which I am studying and referring to a lot when I work on computers. I have made a desktop computer myself mostly out of new parts but with some  second hand parts too, to save money. I am quite interested in the hardware side of things as well as software.  
I have had my website "Illustrated Dual Boot', about how to use the Ubuntu 'Alternate CD installer' since not long after Ubuntu "Breezy Badger" was released. I have practiced installing Ubuntu so many times in the computers we have here that I have lost count. We have Three desktops, two laptops and a 'Book PC'.  I have also written and overwritten the IPLs for all kinds of boot loaders in all my hard disks MBRs and boot sectors more times than can be counted. GRUB, LiLo, NTFS, GAG, you name it, I've tested it and tried out every trick I can think of with each of them. I really don't think an operating system or a boot loader can hurt your hardware. At the most maybe they could affect your BIOS, but that seems unlikely to me, and I really doubt Ubuntu or GRUB would hurt anyone's hardware itself. 
I have read about people 'overclocking' their PCs, but that's something you need to study up on and do deliberately, it doesn't just happen by accident.

The MBR is made out of the same material as the rest of the hard disk and it can be written to and overwritten as many times as we like, 
Even the BIOS is easy to flash with a new program if that's corrupted somehow. It only takes about five minutes. The only reason I've ever had to do that was to try to get past the 33.7 GB hard drive limit or when the BIOS battery went flat on me.

If anybody would know if software can hurt hardware it should be me, I've tried out just about every bad thing that can be done to a computer. Sometimes when people have a problem I use my one of my own computers to simulate the same problem and then figure my way out of it again so I can tell them how to fix theirs. So far all my computers here are working fine no matter what I do to them. I even got my old 'PC Chips Book PC' (BKi810) working again yesterday with a 550W ATX power supply.  It's working great, I have installed Feisty in it now and it's fine.

Anyway, good luck with your  laptop, I hope whatever's wrong is cheap and quick to fix. Most PC problems are.
By for now, 
Regards, Herman :D

---

### Post by Crafty Kisses on 2007-06-23
> **Herman said:**
> Thanks for your vote of confidence there, martijn2, and thanks for sticking with me. Yes, the LTS versions are the best for people who just want a reliable system to get their work or studying done with the least amount of excitement. You are wise.

I am very curious to find out what the problem with your laptop turns out to be. I fix a lot of old computers in my spare time and and I have Scott Meuller's book 'Upgading and Repairing PCs', which I am studying and referring to a lot when I work on computers.
 I have made a desktop computer myself mostly out of new parts but with some  second hand parts too, to save money. I am quite interested in the hardware side of things as well as software.  
I have had my website "Illustrated Dual Boot', about how to use the Ubuntu 'Alternate CD installer' since not long after Ubuntu "Breezy Badger" was released. I have practiced installing Ubuntu so many times in the computers we have here that I have lost count. We have Three desktops, two laptops and a 'Book PC'.  I have also written and overwritten the IPLs for all kinds of boot loaders in all my hard disks MBRs and boot sectors more times than can be counted. GRUB, LiLo, NTFS, GAG, you name it, I've tested it and tried out every trick I can think of with each of them. I really don't think an operating system or a boot loader can hurt your hardware. At the most maybe they could affect your BIOS, but that seems unlikely to me, and I really doubt Ubuntu or GRUB would hurt anyone's hardware itself. 
I have read about people 'overclocking' their PCs, but that's something you need to study up on and do deliberately, it doesn't just happen by accident.

The MBR is made out of the same material as the rest of the hard disk and it can be written to and overwritten as many times as we like, 
Even the BIOS is easy to flash with a new program if that's corrupted somehow. It only takes about five minutes. The only reason I've ever had to do that was to try to get past the 33.7 GB hard drive limit or when the BIOS battery went flat on me.

If anybody would know if software can hurt hardware it should be me, I've tried out just about every bad thing that can be done to a computer. Sometimes when people have a problem I use my one of my own computers to simulate the same problem and then figure my way out of it again so I can tell them how to fix theirs. So far all my computers here are working fine no matter what I do to them. I even got my old 'PC Chips Book PC' (BKi810) working again yesterday with a 550W ATX power supply.  It's working great, I have installed Feisty in it now and it's fine.

Anyway, good luck with your  laptop, I hope whatever's wrong is cheap and quick to fix. Most PC problems are.
By for now, 
Regards, Herman :D

Ha, I'm curious too now. ;)

---

