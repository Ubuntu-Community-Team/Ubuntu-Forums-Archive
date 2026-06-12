---
title: "How do I boot Ubuntu on an Intel Mac?"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Kevomiller on 2006-10-24
I have Mac OS X on an intel imac.

I downloaded Dapper, burned it to CD, and restarted.

Nothing.

Why?

This is suppose to be easy, right?

So, what's the problem?

---

### Post by deepwave on 2006-10-24
Your machine is probably booting directly to harddrive.  You need to change it to boot from CD.  Look into the BIOS settings.

It is easy.  But some assembly required. ;-)

---

### Post by Macario Muñoz on 2006-10-24
I suppose you downloaded the Mac (Power PC) desktop CD ISO, and then you burned it fine and then you put your imac to boot in CD. I'm I correct?

---

### Post by Kevomiller on 2006-10-24
No, I have an intel machine mac, so I downloaded the PC intel version.

How do I change it to boot from CD?

On OS X?

Come on guys, windows isnt the only thing out there, someone has to have some knowledge about macs.  

Jesus.

---

### Post by bigken on 2006-10-24
I think you hold C when booting not to sure

---

### Post by Kevomiller on 2006-10-24
There isnt an option to boot from disk.

In the menu, there is only boot from Hardrive, boot from network.

There is this "Target Disk" Thing, but its for hooking up to other computers.

Anyone know how to make it boot from disk?

---

### Post by bigken on 2006-10-24
take a look [here]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp") it might help

---

### Post by rfruth on 2006-10-24
My G3 iMac requires the "C" key be pressed as mentioned above, Intel Macs are the same 
[http://docs.info.apple.com/article.html?artnum=303124](http://docs.info.apple.com/article.html?artnum=303124) :)

---

### Post by meng on 2006-10-24
kevomiller, I don't know much about Macs, and I hope that everything works out so that you can see what Ubuntu has to offer. Whatever happens, though, try to keep your cool! Especially if you are asking for help.

For example, there's no point blaming Ubuntu for being difficult to install when neither it nor any other operating system can help the fact that booting a Mac from the CD drive depends on a little-publicized well-timed key press. I mean, Macs are supposed to be really simple and user-friendly right? Whoever heard of having to hold down the C key to boot from the CD drive? I mean, Jesus! :p

Or, we could forget about apportioning blame in a misguided attempt to make ourselves feel better, and just focus on how to solve the problem.

---

### Post by Kevomiller on 2006-10-24
I'm sorry, I'm just frustrated.

Do you just press the key and hold it down?

Or do you have to press it really quick and let go at the right time? lol.

I did the key press, and held it down while it restarted, and it booted into MAC OS X again.

I'm just trying to get it to work, it's been like two days.

---

### Post by dan828 on 2006-10-24
Yeah, just hold down c during the boot process until it becomes obvious it's booting from the CD.  Just installed edgy on my G4 Mini this way, and it should be the same on the Intel iMac.  :)

---

### Post by calx on 2006-10-24
Jesus? How dare you use that sort of language in here, take it into the [UCE forum]("http://www.ubuntuforums.org/forumdisplay.php?f=168") Kevo! 

Jesus indeed! 

> **Kevomiller said:**
> 
Come on guys, windows isnt the only thing out there, someone has to have some knowledge about macs.

Jesus.

---

### Post by Kevomiller on 2006-10-24
Eh, I'm Atheist.

I'm having a heck of a time with this Ubuntu.

I'll try to reboot a couple more times with the "C" thing, but I bet it doesnt work!

:(

---

### Post by dan828 on 2006-10-24
Well, if it doesn't either your Mac is defective (the boot from CD shortcut is a longstanding Mac shortcut which goes back a number of years) or the CD image you burned is defective.  Sorry that you're having such problems.  Stick with it though, it's well worth it.:)

---

### Post by Mimsy on 2006-10-24
Do you have access to another computer? If you do, try the CD there. If it doesn't work, then the CD is probably faulty somehow. Download and burn a new CD in the other computer, and make sure to burn it slowly. Then test that CD in this other computer and if it works, try it again in your Mac.

Kudos and props for still trying. I'd probably have given up if I were you...

/Mimsy

---

### Post by Kevomiller on 2006-10-24
I'm not gonna' give up.

I might try the boot CD on a windows machine.

I have no control over burn speed, it doesnt give an option.

I do the "C" thing and it wont work! lol. Grrr.

I have a 500GB drive, so my hope, if I like it, is to partition and have linux and mac, dual boot.

First, I have to get this to work. lol.

I got it off the unbuntu site thingy.

---

### Post by Kevomiller on 2006-10-24
Ok, this is really cool.

I put it in a windows machine, a really crappy windows machine, and it booted up!

So, what is up with an Intel Mac OS X not booting it?

I downloaded and burned the Desktop PC intel version.

It still wont boot on my computer tho, and it is disheartening.


:confused:

---

### Post by deepwave on 2006-10-24
> **Kevomiller said:**
> 
I have a 500GB drive, so my hope, if I like it, is to partition and have linux and mac, dual boot.

First, I have to get this to work. lol.

I got it off the unbuntu site thingy.

Sounds like a plan.  One thing you may want to do is check the MD5 sum of the ISO.  In the mirrors, there should be a .iso.md5 or .md5 file corresponding to your ISO.  Make sure your ISO's md5 matches the md5 in the .md5 file, before you reburn the ISO.

Good luck figuring out the booting sequence. And don't give up. ;-)

---

### Post by deepwave on 2006-10-24
Well since it boots on the Windows machine, then at least the CD is good.

Maybe you should try using BootCamp for the partitioning part.
[http://www.apple.com/macosx/bootcamp/]("http://www.apple.com/macosx/bootcamp/")

The installation and setup guide link looks helpful too.

---

### Post by Kevomiller on 2006-10-24
I'm downloading bootcamp now, but I still cant get Ubuntu to boot on my Mac, even when I hold down that stupid C button. lol.

Anyone have any reason why its not working?

Is it because I downloaded the PC Intel version?

How do you get Ubuntu on an inte imac? lol.

---

### Post by meng on 2006-10-24
Since you've been banging your head against a brick wall for 2 days, maybe it's a good time to pause and try again next week. Let the stress dissipate. Just a thought, I couldn't suggest anything more constructive.

From what I've read, it is the x86 version you need.

---

### Post by aysiu on 2006-10-24
I've modified the thread title to be more accurately descriptive, less provocative... and thus more likely to get actual help.

---

### Post by dan828 on 2006-10-24
This may be of help to you.

[http://www.planetisaac.com/articles/ubuntuinstall.html](http://www.planetisaac.com/articles/ubuntuinstall.html)

Looks like there are a few things that you need to do to get it up and going.

---

### Post by Kevomiller on 2006-10-24
Thank you, Master.

:) 

I'll get it working with your guys's help.

And then after, maybe I can help anyone else in the future that wants to do this on an intel mac.

---

### Post by Mimsy on 2006-10-25
> **Kevomiller said:**
> I'll get it working with your guys's help.

And then after, maybe I can help anyone else in the future that wants to do this on an intel mac.

You have been successfully assimilated :)

/Mimsy

---

### Post by Kevomiller on 2006-10-25
Thanks.

Still no such luck..lol.

:???:

---

### Post by la3875 on 2006-10-25
](*,) Hang in there Kevo! I'm looking for you to succeed on this subject, thus solidifying my decision to go back to Mac hardware/OS and keep using Ubuntu!

---

### Post by Kevomiller on 2006-10-25
Thank you for your support!

:D 

I will be working on it all night. 

heh.

No such luck yet.

---

### Post by omns on 2006-10-25
.

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
Ok, I did the hold down option thing and it brought me to a screen that had just my pic of my HD on it.

It was the only thing to click.

So what else am I suppose to do?

lol.


I think Im getting closer though.

---

### Post by Kevomiller on 2006-10-25
Those links are really handy, but Im not installing or partitioning just yet.

Right now I just want to get the boot disk to work.

I hit option, and it does take me to a blank screen with a pic of my Hardrive and an arrow.  If I hit the arrow it boots up Mac OS X.

How do I get it to boot from the disc? Grr. lol.

It's like, I cant even get started with it.  It's like buying a brand new video game and you cant even get it to work, or look at it. lol.

Anyways, this has to work.

I mean, c'mon.

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
Thank you!

I will try that.

It's frustrating, but I can't wait to get this goin'..

:)

---

### Post by Kevomiller on 2006-10-25
Ok, I tried that now.

I installed rEfit.

I cant drag efi folder to MacOS Disk because I dont have a macos disk.

I have a mac HD, is that ok?  Cause when i drag it to that, its already in there.

I type in what you said, and it says no such file or directory in the terminal window.

?

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
Yeah, I did that and it says its already in there.

I went to that link before too, and it just repeats what you said. lol.

it says I didnt put the file in the right place, if I get "No Such file or directory"

So it comes down to where do I put the efi folder?

If not the hard Disk, then where?

---

### Post by Kevomiller on 2006-10-25
Holy, crap!  I got it working.

Thanks, man.  I'm sorry I'm such a n00b. lol.

I'm learning so much tho, and its awesome.

Anyways, I got the boot legacy working where I get the choice to chose mac or linux, but it wont let me do anything in linux.

Something about a folder not being found and asks me if I have the lastest firmware?

Can you help?

---

### Post by Kevomiller on 2006-10-25
Ok, ok.

It says something about not finding my legacy folder.

That and then it asks me if I have the latest firmware update.

It's like putting a puzzle together. lol.

I get to one point, and then it gives me another clue.

"Firmware" - "Legacy Folder".

My two next clues.

---

### Post by Kevomiller on 2006-10-25
Actually, it's legacy loader.

Hmm.

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
Mac OS X 10.4.8


Frustrating. heh.

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
What should I look for on software update?

My mac is like two months old, and I updated everything once.

I know you are, just bare with me.

I dunno what's wrong.

It's frustrating.  Something about Cant find Legacy Loader and it asks me if I need a Firmware update.

I can look for a particular update, but usually it just wants to update iweb, imove HD or somethign that I dont even wanna use.

It did try to update java.. I dunno.

---

### Post by Kevomiller on 2006-10-25
Oh, and refit works fine.

Just when I click on The Linux Penguin, it takes me to a screen that says it cant find the Legacy Loader.

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
I'm just sittin' here, eating apple sauce

and watching Core Rhythms infomercial on TVguide channel at 5:30AM waiting for Buffy the Vampire slayer to come on..

Praying for a miracle.

I need a hail mary here.

---

### Post by Kevomiller on 2006-10-25
Yeah, I think I'll wait on Edgy, this isnt working.

When is it coming out?

I need to read on it.

---

### Post by omns on 2006-10-25
.

---

### Post by Kevomiller on 2006-10-25
Oh, so it comes out Thursday.

I can wait for that.

I'm still gonna' try to at least check out ubuntu until then.

You know, at first I just wanted to look at it, and I cant even do that. 

I learned about it on Cnet, and he was like "It's so easy"!

lol.

You know what, he lied!

lol.

---

### Post by Kevomiller on 2006-10-25
Thank you for your help.

Strangely enough, I was messin around and it wont even let me use bootcamp assistant.

Guess what it says, "You need to update your firmware before you can use bootcame assistant.

So, right above bootcamp assitant is my firmware updated.  Wow!  What a relief!

So, I click on it, and what does it say?  "Your firmware is up-to-date" 

So, what the hell does all of this mean?

I have no idea.

---

### Post by Kevomiller on 2006-10-25
Ok, got it goin!

I just had to update my Firmware!

To be honest, if I wouldnt have been persistant, I would've never found the update.

It took about an hour searching on apple's site for it.

Anyways, thanks!

---

### Post by sgmorr on 2006-10-26
Kevo,

I'm just reading along out of curiosity. I have a PPC iMac G4 myself. So what's the word on Intel Macs? Do you use Ubuntu for Intel or Ubuntu for PPC?

By the way, to boot a Mac from a CD do the following:
Insert CD, go to the Apple menu and choose Restart, hold the C key down as soon as you hear the startup gong, you may release C when you can tell for sure that the booting process is underway.

Good luck!

---

### Post by Kevomiller on 2006-10-26
I got it working already, awhile back.

I downloaded the intel pc version.

You guys need to updatae that "C" key thing!  It's wrong!

You dont hit "C", you hit the "Option" key.

Also, it still doesnt work on my mac unless you install rEfit or Bootcamp.

There is no way to boot it from a CD on an intel Imac unless you have rEfit or Bootcamp.

The option or c keys dont work for it.

Anyways,

I got it all working after hours of trying, and my assessment is that Linux is too much trouble for its worth.

Maybe in 5 years, it'll be ready for the regular joe to use, but right now you still need an MIT degree.

Take care, and thanks for the help!

---

### Post by linuxvt on 2006-10-28
Thanks to all who posted to this thread. Less than an hour after reading your suggestions I am posting from 6.10 on a Intel Mac.
I downloaded Bootcamp from Apple, followed the Apple instructions, inserted the Ubuntu live CD when prompted for a Windows install disk, and here I am.

Thank you, Thank you, Thank you!

---

### Post by cvmostert on 2006-10-31
> **Kevomiller said:**
> Holy, crap!  I got it working.

Thanks, man.  I'm sorry I'm such a n00b. lol.

I'm learning so much tho, and its awesome.

Anyways, I got the boot legacy working where I get the choice to chose mac or linux, but it wont let me do anything in linux.

Something about a folder not being found and asks me if I have the lastest firmware?

Can you help?

Great! Congratz! Now you can write a short HOWTO: boot into IntelMAC with Ubuntu.

I already have a friend who wants to do what you did.

Keep up the good work!

edit; i see you alrady did... sad that id does not do the job for you... see you back later then.

---

### Post by Sebhelyesfarku on 2006-10-31
> **Kevomiller said:**
> I got it working already, awhile back.

There is no way to boot it from a CD on an intel Imac unless you have rEfit or Bootcamp.

I got it all working after hours of trying, and my assessment is that Linux is too much trouble for its worth.

Maybe in 5 years, it'll be ready for the regular joe to use, but right now you still need an MIT degree.


Meh, why would Linux be the trouble if you've bought a PC crippled by Apple that can't boot an ISO CD properly? You asked for the trouble bending over to Apple...

---

### Post by fyrefly07 on 2006-11-02
I'm still trying to get Ubuntu on my Mac Pro.  Dunno if I should be using the 64 bit version or not...

---

### Post by omns on 2006-11-03
.

---

### Post by cooperaa on 2006-11-29
[nothing]

---

### Post by u0014 on 2006-12-27
As soon as you power it on, you hold it (C key) down until you you see the CD booting... (Ubuntu option screen comes up) also I am not if you can use try using the Option key (ALT) hold it down as soon as you power on your machine until you the boot options (of course you must have a bootable CD in the drive in order to see it in the options menu)

I don't know if Ubuntu 6.10 is going to work on an Intel apple since they don't have a BIOS they use something called EFI, I believe and it does not replace the BIOS in a PC. I know that Ubuntu 6.06 does not work right off CD you first have to install a package on your Mac operating system. For more info visit: [http://bin-false.org/?p=17]("http://bin-false.org/?p=17")

I did read some where that Ubuntu 6.10 installation works like in any PC. Just boot from the CD. 

Be aware that if you install Ubuntu and plan to keep your Mac installation you may have to manually add an entry to the grub configuration to make your Mac OS show up in the grub menu. Meaning if this does not work your Mac OS wont be accessible.

---

### Post by u0014 on 2006-12-27
As soon as you power it on, you hold it (C key) down until you you see the CD booting... (Ubuntu option screen comes up) also I am not if you can use try using the Option key (ALT) hold it down as soon as you power on your machine until you the boot options (of course you must have a bootable CD in the drive in order to see it in the options menu)

I don't know if Ubuntu 6.10 is going to work on an Intel apple since they don't have a BIOS they use something called EFI, I believe and it does not replace the BIOS in a PC. I know that Ubuntu 6.06 does not work right off CD you first have to install a package on your Mac operating system. For more info visit: [http://bin-false.org/?p=17](http://bin-false.org/?p=17)

I did read some where that Ubuntu 6.10 installation works like in any PC. Just boot from the CD.

Be aware that if you install Ubuntu and plan to keep your Mac installation you may have to manually add an entry to the grub configuration to make your Mac OS show up in the grub menu. Meaning if this does not work your Mac OS wont be accessible.
Edit/Delete Message

---

### Post by u0014 on 2006-12-27
As soon as you power it on, you hold it (C key) down until you you see the CD booting... (Ubuntu option screen comes up) also I am not if you can use try using the Option key (ALT) hold it down as soon as you power on your machine until you the boot options (of course you must have a bootable CD in the drive in order to see it in the options menu)

I don't know if Ubuntu 6.10 is going to work on an Intel apple since they don't have a BIOS they use something called EFI, I believe and it does not replace the BIOS in a PC. I know that Ubuntu 6.06 does not work right off CD you first have to install a package on your Mac operating system. For more info visit: [http://bin-false.org/?p=17](http://bin-false.org/?p=17)

I did read some where that Ubuntu 6.10 installation works like in any PC. Just boot from the CD.

Be aware that if you install Ubuntu and plan to keep your Mac installation you may have to manually add an entry to the grub configuration to make your Mac OS show up in the grub menu. Meaning if this does not work your Mac OS wont be accessible.
Edit/Delete Message

---

### Post by Terry Jones on 2007-01-06
How get an Intel based Mac to boot a  live CD. 

1. Boot into OS X.  

2. Insert the live CD into the CD/DVD drive.  

3. Restart the computer.

4. While restarting the computer hold down the ALT /OPTION key. It is to the second key to the left of the space bar. 

5. Press the ALT/OPTION  key until you see the following
    A. Grey screen
    B. Apple logo 
    C. Icons of harddrive. Each hard drive will represent  a partition. that has a  an       operation systen that can be booted.
    D. An icon of a CD. This icon represents the live CD. The CD will be labled windows. Dont ask me why the lable is wrong.

5.If YOU DO NOT SEE THE ICONS REPEATE STEPS 1-5.

6. Using the arrows on the keyboard select the icon of the CD.

7 Press enter. The Live CD will now boot.

  
TO return return to OS X.

1. Exit the live CD.

2. Remove Live CD From CD/DVD Drive. 

3. Restart the computer.

4. While restarting the computer hold down the ALT /OPTION It is to the second key to the left of the space bar. 

5. Press the ALT/ OPTION key until you see the following.
    A. Grey screen
    B. Apple logo 
    C. Icons of harddrive.

6. Using the arrows on the keyboard select the icon of the Macontash HD.

6. Boot Into Mac OS X.

7. If necessary to remove the live CD from the CD/DVD drive press the EJECT key. It is located at the top of the keyboard on the first row next to the F12 function key.

---

