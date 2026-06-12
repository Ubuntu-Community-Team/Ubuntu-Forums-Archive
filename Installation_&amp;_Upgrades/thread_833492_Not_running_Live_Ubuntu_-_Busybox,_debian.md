---
title: "Not running Live Ubuntu - Busybox, debian?"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by GodsDead on 2008-06-18
hey all, iv had some experaince with Ubutnu, and i decided to duel boot today, so i downloaded and burnt an ISO of the latest Version today, all fine, booted up fine with the Ubuntu menu, clicked "Try ubuntu without any change to your computer" it runs the graphical loading bar, then instead of loading the Ubuntu OS it outputs like a shell;

```

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
enter 'help' for a list of built-in commands.
(initramfs)

```

I have attatched a photo.. not that it will show much different

I wanted to duel boot, but if i cant even load the livecd then, im not even gonna risk installing it as a Duel OS
Someone please help =]

---

### Post by avtolle on 2008-06-18
Presuming the md5sum of the iso checked out, as did the burn (given how far you got along), please try this to see if it will help: reboot, and hit F6 (as I recall) and add "all-generic-ide" at the end of the boot string (w/o the quotation marks, of course) and then press b to boot.

---

### Post by Pumalite on 2008-06-18
You can try to install with the Alternate CD. You probably need some Boot parameters. Try your luck and mettle:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788 all_generic_ide
To be tried one at the time or in different combinations until you hit the right one.
Good luck.

---

### Post by aggie75 on 2008-06-18
I got this same message when trying to install Ubuntu on my work computer.  Digging through the documentation, I found my problem to be my work computer hard drive was encrypted and the install will not work on an encrypted hard drive.  Is your drive encrypted?

---

### Post by GodsDead on 2008-06-19
I have no idea if my drive is encrypted, im running Vista Home Premium? if that helps?
on a Gig of ram & duel 3.2 ghz processors, so thats supported..
Its only with this distro its weird, although when i incert the disk into the tray while in vista, it should pop up with a menu shouldnt it? 
because i run the ISO by itself (without cd) and it gives me the option while in windows to insdtall Ubuntu as an application, though with the CD it dousnt?

But it boots fine?
im so confuzed :S

---

### Post by Pumalite on 2008-06-19
Boot from the Live CD or Alternate CD.

---

### Post by GodsDead on 2008-06-19
That the problem im getting at, i cant, as i get the error in my first post

---

### Post by ezramorris on 2008-06-19
Did you check the md5sum?

More info to check from windows here: [https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24](https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24)

---

### Post by Pumalite on 2008-06-19
Have you tried the boot parameters?

---

### Post by Westergaard on 2008-06-19
I'm having the same problem.  I get the same error when I try to boot into ubuntu.  I'm running vista on a laptop.  How can you know if your harddrive is encrypted?

---

### Post by mistergoomba on 2008-06-21
I have the same issue. It starts by saying I need to load with the noapic option. I've installed ubuntu using this disk and even this hard drive, but when I select "Install Ubuntu", I get this BusyBox prompt. Please help!

I've used the following lines to boot with:

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- 


file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- noapic


file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- noapic all-generic-ide

---

### Post by ezramorris on 2008-06-21
> **mistergoomba said:**
> I have the same issue. It starts by saying I need to load with the noapic option. I've installed ubuntu using this disk and even this hard drive, but when I select "Install Ubuntu", I get this BusyBox prompt. Please help!

I've used the following lines to boot with:

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- 


file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- noapic


file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- noapic all-generic-ide

Have you tried the boot options before the --? ;)

---

### Post by mistergoomba on 2008-06-21
I just switched my SATA type from IDE to RAID and am having the same issue. I'm stuck on the BusyBox initramfs prompt

---

### Post by ezramorris on 2008-06-21
did you try 
file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash noapic --
?
the -- at the end of the line means ignore anything after this.

---

### Post by mistergoomba on 2008-06-21
> **ezramorris said:**
> Have you tried the boot options before the --? ;)

i just tried that, and I got the prompt again

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash noapic all-generic-ide --

---

### Post by ezramorris on 2008-06-21
> **mistergoomba said:**
> i just tried that, and I got the prompt again

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash noapic all-generic-ide --

I had a little look around at what other people found. (Try them one at a time.
- Try adding irqpoll.
- Adding all_generic_ide (underscores not hypens). 
- Adding root=/dev/cdrom

If none of these work, remove splash and quiet and see if it says something interesting.

---

### Post by mistergoomba on 2008-06-21
no dice on those options, but i tried taking out the quiet and splash

the last 2 lines read:

[82.874959] ide-cd: cmd 0x5a timed out
[82.875023] hdc: lost interrupt

after a minute, i got:

[142.717415] ide-cd: cmd 0x5a timed out
[142.717476] hdc: lost interrupt
[142.717553] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[142.717852] Uniform CD-ROM driver Revision: 3.20

every minute or so thereafter, i get another hdc: lost interrupt

i'm gonna search around for some of these lines, but if this sparks something for you let me know.

thanks!

---

### Post by mistergoomba on 2008-06-21
looks like the boot parameter i was looking for was pci=noacpi

thanks again for all the help!

---

### Post by ezramorris on 2008-06-22
> **mistergoomba said:**
> looks like the boot parameter i was looking for was pci=noacpi

thanks again for all the help!

If all your hard disks and CD drives, etc work, then that's fine, but give them a check just in case.

If everything works OK, could you mark this thread as solved?

Thanks.

---

### Post by mistergoomba on 2008-06-22
everything is top notch, and i'm typing this on my new installation. thanks again!

** i didn't start the thread, so i probably won't be able to mark it solved

---

### Post by GodsDead on 2008-06-23
So, what do i need to type in to solve this issue? =]

---

### Post by avtolle on 2008-06-23
Don't know the specific answer for you. Pumalite gave you a good listing of things to try. The first one to try is "all_generic_ide" (w/o the quotes) before the -- at the end of the boot line you see when you press F6.

---

### Post by mistergoomba on 2008-06-23
> **GodsDead said:**
> So, what do i need to type in to solve this issue? =]

here is the original boot line:

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

i had to add in the noapic parameter before the --

then i tried each of the following independently after noapic:
irqpoll.
all_generic_ide
root=/dev/cdrom
pci=noacpi

it was pci=noacpi that worked for me. my suggestion if you cant get it working is to try getting rid of quiet and splash as ezramorris suggested and then posting or searching for the output

---

### Post by ezramorris on 2008-06-23
> **GodsDead said:**
> So, what do i need to type in to solve this issue? =]

Try each option from this thread in turn, and if none of them work, try removing quiet and splash, and letting us know the output.

> ** i didn't start the thread, so i probably won't be able to mark it solved 

doh ](*,)

---

### Post by mistergoomba on 2008-07-05
> **ezramorris said:**
> If all your hard disks and CD drives, etc work, then that's fine, but give them a check just in case.

If everything works OK, could you mark this thread as solved?

Thanks.

After you sent me this, I verified that my CD/DVD drive worked. However, I hadn't tried it with a DVD yet. Now, when I try to load any DVD, I get 'cannot read from resource' from the built in movie player. Any suggestions? The pci=noacpi option is what helped me work around a CD/DVD drive error that I was getting on boot when I removed the quiet and splash options.

---

### Post by ezramorris on 2008-07-05
> **mistergoomba said:**
> After you sent me this, I verified that my CD/DVD drive worked. However, I hadn't tried it with a DVD yet. Now, when I try to load any DVD, I get 'cannot read from resource' from the built in movie player. Any suggestions? The pci=noacpi option is what helped me work around a CD/DVD drive error that I was getting on boot when I removed the quiet and splash options.

I'd be surprised if you could read CDs but not DVDs, so have you tried burning or reading a data DVD?

If you can, it is more likely to be codec problems rather than hardware. Also, did movie player give any more details on the error?

[COLOR="Red"]Edit: [/COLOR]If all that works, try a video DVD which is not copy protected.

---

### Post by mistergoomba on 2008-07-05
> **ezramorris said:**
> I'd be surprised if you could read CDs but not DVDs, so have you tried burning or reading a data DVD?

If you can, it is more likely to be codec problems rather than hardware. Also, did movie player give any more details on the error?

[COLOR="Red"]Edit: [/COLOR]If all that works, try a video DVD which is not copy protected.

You're right. I was able to browse the DVDs I tried watching, and browse data DVDs. I tried playing the video with the movie player which only said 'Cannot read from resource', and with VLC (heard was a great ripping program), which gave no error, just wouldn't play.

[COLOR="Red"]Edit:[/COLOR] I just tried Acid Rip which allowed me to select the tracks and subtitles I wanted to rip, however froze when I chose 'preview'

---

### Post by ezramorris on 2008-07-06
> **mistergoomba said:**
> You're right. I was able to browse the DVDs I tried watching, and browse data DVDs. I tried playing the video with the movie player which only said 'Cannot read from resource', and with VLC (heard was a great ripping program), which gave no error, just wouldn't play.

[COLOR="Red"]Edit:[/COLOR] I just tried Acid Rip which allowed me to select the tracks and subtitles I wanted to rip, however froze when I chose 'preview'

Make sure you have libdvdcss installed and configured correctly:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mistergoomba on 2008-07-06
> **ezramorris said:**
> Make sure you have libdvdcss installed and configured correctly:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

perfecto! thanks again!

---

### Post by ezramorris on 2008-07-06
> **mistergoomba said:**
> perfecto! thanks again!

No problem.

@GodsDead:
Any progress for you?

---

### Post by GodsDead on 2008-07-19
You wouldnt belive it, i downlaoded the ISO again, used the recommened Burning Programme, with a new brand of writable disk, and used a slow speed to burn the ISO, and no problems! im writing this post Via the live disk =p

One problem though, my bottom bars floating 3/4 down the screeen, instead of the bottom 0_o iv tryed changing the resolution but no luck, any ideas?

---

### Post by ezramorris on 2008-07-19
> **GodsDead said:**
> One problem though, my bottom bars floating 3/4 down the screeen, instead of the bottom 0_o iv tryed changing the resolution but no luck, any ideas?

You could try moving the bottom panel (I assume that's what you mean) to one of the sides, then right click it and add a new panel.

If the new one appears in the right place, then either copy or recreate the applets. Then you can delete the old panel.

If this doesn't work, let us know what video card you are using. I have seen this when doing dual desktop with monitors of different resolutions.

Hope this helps.

---

### Post by lucaspace on 2009-03-15
Hi guys,
first of all i'm sorry for my not-perfect english..
If can help, i want to report you my experience.

In a friend's desktop-pc problem was damaged drives (2 optical, 1 hdd).
Any live-CD won't boot.. so i tryed to attach a new optical drive and everyting works well.
So, probably my friend has got current problem in his house..

So try to attach another optical drive to boot! ;-)


Bye.

---

