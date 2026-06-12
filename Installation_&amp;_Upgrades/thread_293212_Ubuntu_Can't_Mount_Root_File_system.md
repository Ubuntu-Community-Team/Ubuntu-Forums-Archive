---
title: "Ubuntu Can't Mount Root File system"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by Aidan1234 on 2006-11-04
I just built a computer. The only thing i loaded onto it is windows Vista. I want to install Ubuntu 6.06. When i put the CD in and Press Start or Install Ubuntu, it gets stuck on 'Mounting Root File System'  After about a minute or two it takes me to a prompt like window where i can type stuff.

Why Can't Ubuntu Mount the Root File System?

Should i type something in the Prompt thing? 

Computer Specs

Asus P5B DELUXE MOTHERBOARD

INTEL E6300 CORE 2 DUO

1 GB OF RAM

200GB SATA HARD DRIVE

Anybody else had this problem? Thanks

---

### Post by Sef on 2006-11-04
Did you download the CD?  If so did you do an md5sum?  

If it is a live CD, have you checked the disks on any other system?

Are you using the Live CD or the alternate CD?

---

### Post by Aidan1234 on 2006-11-05
I Downloaded the CD. Its the Live CD. I checked it on my other computers and it booted up fine.

---

### Post by Virtunate on 2006-11-08
I'm having this same problem. Last night it worked but for some reason, it's not working now.

---

### Post by Burglar on 2006-11-27
Hey!
I'm new to this OS and wanted to try it out but i stumbled upon the same problem as Aidan1234, so i wonder if you found a solution to the problem and if so, what did you do?

---

### Post by skale on 2006-11-27
I did not know Vista came out already.  Is it any good?

Anyway, I had the same problem with the LiveCD a while ago.  I downloaded the  alternate CD and it was fine.  

What it 'should' do is send you to this graphical installer of some sort (never tried it, so don't quote me).  The alternate CD has a fun blue cursed interface which takes you back to the eighties, but it does everything just fine.

---

### Post by Burglar on 2006-11-29
You wouldn't happen to have a link to that iso-file? I can't find my way around all the different versions :confused:

---

### Post by bapoumba on 2006-11-30
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download") ;)

---

### Post by Burglar on 2006-12-01
Thank you very much, lets pray this one works now :)

---

### Post by Aidan1234 on 2006-12-19
Hey guys. It's Aidan again. I pretty much just gave up and stuck with windows. The Vista thing was actually just the Release Candidate. I am going to try the alternate CD install. Thank you for your help and i will get back to you on what happens.

---

### Post by Aidan1234 on 2007-01-03
Hi. Aidan Again.

I Downloaded the alternate install CD, and it failed again. It said that it can't find the drivers for my optical drive. So, i went ahead and pulled a CD-R drive out of an old dell i have lying around and plugged it in, still nothing. Always gets stuck on the step called

Mounting Root File System.

I rly have no idea what's up with the thing.

---

### Post by rsambuca on 2007-01-03
Try entering 

ide=nodma

as a boot option.

---

### Post by Aidan1234 on 2007-01-03
I have Pictures of it Failing During Installation. 

Here THey are. They go in chronological order.

---

### Post by Aidan1234 on 2007-01-03
Where would i enter that? BIOS?

EDIT,

Ok, i typed ide-nodma

as a boot option, but still, nothing. 
It just says after a lot of text,

Kernel Panic................. and then a ways on....... Cannot Mount Root FS on unknown block (8,3)

I dont know anything about Linux Kernel, so idk whats wrong with it.

---

### Post by rsambuca on 2007-01-03
It's actually an equals sign, but I don't think that is the problem anyways.  I haven't seen this before.

---

### Post by Aidan1234 on 2007-01-03
Well thanks for your help anyway. I won't give up until i have Ubuntu.

I might try plugging my hard drive into another computer and then just Installing it on there.

Might work.

---

### Post by rsambuca on 2007-01-03
It looks like something with the chipset on the motherboard.  I found another thread where a guy loaded ubuntu somehow with a round-about.  Keep me posted and good luck!

[http://ubuntuforums.org/showthread.php?t=289320&highlight=Asus+P5B+DELUXE+MOTHERBOARD](http://ubuntuforums.org/showthread.php?t=289320&highlight=Asus+P5B+DELUXE+MOTHERBOARD)

---

### Post by Aidan1234 on 2007-01-05
I do have the same motherboard as the guy from that thread. I will see if it has any answers i need.

---

### Post by Aidan1234 on 2007-01-05
I downloaded the 6.10 Alternate Install CD, and tried that one. The install went fine and i now have a dual boot of Windows XP and Ubuntu 6.10 configured w/ GRUB

I still have a problem with Ubuntu though...
After it displays the Ubuntu Logo at startup (splash screen i think)  the screen goes black and i can't see anything. I am using a nvidia GeForce 7800 GT with a Dell 19 inch LCD monitor.

Anybody have any ideas as to why it just shows a Black screen? if so, how do i fix it.

Thanks a bunch.

---

### Post by Aidan1234 on 2007-01-06
Update.

Today i booted up ubuntu and actually got the login screen with my LCD monitor. i logged in, but then it just turned into the orange screen with black lines all around and a clump of white lines in the middle of the screen.

The Monitor and video card work great with Windows still.

so.. I plugged an old CRT monitor into my computer to see if that would make any difference in booting ubuntu. I got the same thing as i did with the LCD monitor. 

weird. Everything i have read points the LCD monitors to being the culprits. perhaps it is my video card?

nVidia geForce 7800GT w/ 256MB RAM

I hope it's not another problem with the motherboard again.

Post any ideas please.

---

### Post by Aidan1234 on 2007-01-10
I've got a plan. It just needs some perfecting. 

Two questions.

1. Can i install linux drivers for my video card **from a usb** during alternative installation? 

2. Can someone give me a link to the nVidia geForce 7800 GT drivers for Linux?

Thanks for your help.

---

### Post by coakley on 2007-01-10
I have the exact same problem with a shiny new Dell Optiplex 320N - yes I bought a Dell with no operating system except for the FreeDOS CD in the box. I have installed 6.06 on 8 other machine off the same CD but on the Dell it freezes at Mounting Root Partition. I then installed FreeDOS on the hard drive (which went just fine) to see if it made any difference, but it didn't.I have tried all the noapic nolapic acpi=off etc things I could think of but no luck.

Why?](*,)

---

### Post by Aidan1234 on 2007-01-12
I've got a plan. It just needs some perfecting.

Two questions.

1. Can i install linux drivers for my video card from a usb during alternative installation?

2. Can someone give me a link to the nVidia geForce 7800 GT drivers for Linux?

Thanks for your help.
Edit/Delete Message

---

