---
title: "Ubuntu won't boot after installation?"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by nclester on 2008-02-21
Alright, I had a thread going in the "Absolute Beginners" section but it kind of got jacked and my problem has evolved anyway. Time for a new thread. 

I am running a dual-boot machine, P4 2.93GHz CPU, 1GB DDR-2 RAM, NVIDIA GeForce 6200, Creative SB Audigy 4, 160 GB HD... 

My 160GB HD has three partitions, 100GB for Windows XP Pro SP3, 1GB for swap, and 59GB for Ubuntu.

This is my first dual-boot machine and I am a total Ubuntu noob, so bear with me. 

I tried to install Ubuntu(Gutsy) with the Live CD and didn't succeed. At all. So I tried to install using the Alternate CD, and the installation went smoothly. Or so I thought. 

After installing Ubuntu on my machine and re-booting, I selected Ubuntu 7.10 - generic from the GRUB menu. 

The very next screen I get stuck on, for hours at a time, it's totally frozen. The Ubuntu loading screen, and my loading bar never gets further then 1/4 full.

I'm not sure what to do, or what else to try? My memtest turned out to be fine, after about 2 hours of testing. I also tried to boot Ubuntu in recovery mode and that didn't work either. Windows XP Pro SP3 works just fine, along with GRUB. 

What can I do? I feel like I've exhausted every option, but I know thats not true. Any help is appreciated! Thanks

---

### Post by spiderbatdad on 2008-02-21
It sounds like you manually created the partitions. Where you say 59 GB for Ubuntu, does that include a root volume "/" or is it only an extended volume? Mine looks like this: 
I believe you specify to boot the root volume as well.

---

### Post by nclester on 2008-02-21
Spiderbatdad, I have no idea weather my 59GB includes a root volume or if it's extended only. I know the backslash was there when I partitioned that part of my drive. 

Since my last post, I have tried to re-install or even boot from the Live CD. With some luck : )

I stuck the Live CD to my machine, and added "apic=off and vga=775" subtract the quotations and the word and. I saw a screen like never before, the Live CD is working! That has to mean I have a hardware(GPU) problem, right? 

I'll let it go, re-install and re-format over my last Ubuntu installation, making sure my Linux partition includes a root volume(/)

Here is my drive partitioning. 

#1 Primary     99.6GB   B   K   ntfs          /media/sda1
#2 Primary   995.3MB        F   swap        swap
#3 Primary     59.4GB        K   ext3          /media/sda3

Is that right? Why isn't there a B in the #3 line? Doesn't that stand for bootable?

---

### Post by nclester on 2008-02-21
I ended up with an error _code when trying to boot up. It was in the "Looking for Hardware Drivers" section of the start-up. F*ck

Windows boots fine, grub works fine. Recovery mode lands me at the same error code.

---

### Post by spiderbatdad on 2008-02-21
I don't know if you have looked in your system bios for analog vga setting, perhaps in a config menu.
Have you tried guided resizing rather than manually setting the partitions...btw you need to defrag the windows partition before installing...:)

---

### Post by Partyboi2 on 2008-02-21
have you tried using apic=off and vga=775 again as the boot options?

---

### Post by dstew on 2008-02-22
> Here is my drive partitioning.

#1 Primary 99.6GB B K ntfs /media/sda1
#2 Primary 995.3MB F swap swap
#3 Primary 59.4GB K ext3 /media/sda3

Is that right? Why isn't there a B in the #3 line? Doesn't that stand for bootable?Your partitioning scheme lacks a root partition. Give partition #3 the mount point '/' (without the quotes of course). The "B" stands for bootable, but this is only required by the Windows boot loader. It scans the partition table for the B flag, and boots that partition. Grub uses a different scheme. It is tied in by addressing to the correct partition, and the boot flag is irrelevant.
EDIT: But if you are booting, you must have figured out that about the root mount point.

---

### Post by nclester on 2008-03-14
Wow, it's been way too long. I finally got the opportunity to work on my other machine, the one that still wont boot Ubuntu. I deleted the partition with Ubuntu on it, then I had to run my XP Boot disk, in order to run "fixmbr" in recovery mode. The damn thing kept giving me a Grub Error 22. That method fixed it. 

Now, I've re-installed (w/ a alternate CD, downloaded straight from Ubuntu's web-site) and re-partitioned my drive making sure to give partition #3 the mount point "/", without the quotations of course. 

Thanks for all the help so far people, I appreciate it. 

But I'm still not able to boot, which sucks. What can I try?

---

### Post by nclester on 2008-03-15
bump

---

### Post by Pumalite on 2008-03-15
You have to give details and exact error messages for people to be able to help you.

---

### Post by nclester on 2008-03-17
Alright, after a few more days of procrastination, it's time to get you Ubuntu guru's some facts. 

Machine in question is a P4 2.93GHz, 1GB DDR2 RAM, NVIDIA GeForce 6200, Creative SB Audigy 4,  and 160 GB HD <---- anything else that needs to be disclosed, let me know! 

I'm running Windows XP SP3 just fine, but Ubuntu won't load. Grub also works fine, it's just Ubuntu. 

Now, I've tried the Live CD, no dice, not even an install. So I installed with the Alternate Disk and used F6 to add a few options. I removed the "quiet splash" and replaced it with "noapic" & "vga=775", and the installer ran perfectly, no snags. 

I went to boot the machine into Ubuntu's gorgeous GUI and nothing happened. It wont move passed the loading screen, see pictures. 

So, I decided to try to boot into recovery mode, and see if anything happens. 

I was given this message, "error_code+0x72/0x80" and my screen would not more, see pics. 

If I'm leaving any information that could be useful to the doctors out, let me know. I'm here all night. I'm determined to fix this nonsense. 

Thanks for any help, I've been trying to boot into Ubuntu for like 2-3 weeks with little or no luck.

---

### Post by nclester on 2008-03-17
[[IMG]http://img214.imageshack.us/img214/5372/dsc0053lp1.th.jpg[/IMG]](http://img214.imageshack.us/my.php?image=dsc0053lp1.jpg)

Only happens when I boot into regular Ubuntu, or at least try to. 

[[IMG]http://img209.imageshack.us/img209/8600/dsc0056is0.th.jpg[/IMG]](http://img209.imageshack.us/my.php?image=dsc0056is0.jpg)

Get this message when I boot, again, or try to boot, into Ubuntu recovery mode

---

### Post by Pumalite on 2008-03-17
Motherboard? Chipset?

---

### Post by nclester on 2008-03-17
My motherboard is an ASUS Goldfish3, and my chipset is an INtel i915P/i915G

Thanks Puma

---

### Post by Pumalite on 2008-03-18
I think your chipset is very new. Am I wrong?
Try a few boor parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Start with the most common, alone or in combinations:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by nclester on 2008-03-18
No, actually my chipset is old, it came installed with my machine, and I purchased it about 4 years ago. 

I'll run through those links, and attempt the boot parameters.

Thanks for the help.

---

### Post by Pumalite on 2008-03-18
Good luck. Thanks for the tip on the chipset

---

### Post by nclester on 2008-03-19
I tried editing the boot parameters, I deleted quiet splash and used noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791 all at once, and when I tried to boot it sounded like it was booting, but my screen was all black. 

Then I tried booting using these parameters, noapic nolapic acpi=off pci=noacpi pnpbios=off, and I received the same error as I normally get. 

Then I tried, noapic nolapic acpi=off pci=noacpi pnpbios=off vga=791 and my Logitech G15 keyboard lit up, normally it's not lit. My machine also sounded like it loaded something, and it was long enough to be an operating system if you know what I mean. 

I'll keep playing with these parameters, any more advice is greatly appreciated. 

Later on.

---

### Post by nclester on 2008-03-19
This time I tried using, noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317, and the thing nearly booted up. My monitor adjusted itself and jumped to attention, as did my keyboard and my machine sounded as if it loaded Ubuntu. It's got to be a video card driver issue. Right? Can I bypass it? How do you figure out what numbers go after vga=x, x being the unknown?

I'm bummed.

---

### Post by nclester on 2008-03-19
I tried a few more like, noapic nolapic acpi=off pci=noacpi pnpbios=off irqpoll vga=795, and I also tried plugging in my monitor to the on-board vga port. No luck.

---

### Post by mdkaneda55 on 2008-03-28
cool.. more people are having this wacky issue... i thought it was just me. i've been using ubuntu since '06 and this is driving me nuts.... here's my situation...

Trying to install Gutsy on my girlfriend's PC.. it's an old HP with a slow-mo Celeron in it. anywho, to make a long story short, This PC used to be my mom's until the folks upgraded.. and i had previously installed Ubuntu Dapper on it. The only things i've done to this PC are upgrade the Ram & add a NVidia GeForce video card (the Video card is PCI, its a crappy old HP w/ no AGP or PCI-E slots, so it was my only option).. 

anyways, i'm guessing the problem lies in the video card setup... i'll have to double check, but i think its a GeForce FX5500 (maybe 5200? not sure). I've used 3 different 'AGP' GeForce 5xxx cards in my machine and had no problems like this in any version of ubuntu... so it's a strange one.

it's not Gutsy Specific, i tried Gutsy, Fiesty, & Fiesty Server... using alternate install / dvd discs i got through all installations no problem, but it just wont boot past that same screen as the original poster is seeing. the live CD won't boot either. so i'm stumped.. but i'll read over this thread and see if i can make any sense of this. 

just wanted to add my story to this thread =) hope we can come up w/ something!

---

### Post by Pumalite on 2008-03-28
If all the boot parameters fail, you can try editing your menu.lst and changing 'quiet splash' for 'nosplash'

---

### Post by mdkaneda55 on 2008-03-28
I'm starting to get excited now... look what i found!!!!

[http://ubuntuforums.org/showthread.php?t=614893](http://ubuntuforums.org/showthread.php?t=614893)

read that, i'm gonna try this out tonight and post results.. i feel like im getting somewhere now. hehe. =) i love ubuntu forums, such a great community! =)

---

### Post by mdkaneda55 on 2008-03-28
worked like a charm. =) all i had to do was.. 

go into the bios setup, switch the default display back to "Onboard", hit F10 to Save & Exit.

then while the PC was rebooting, switch the vga cable to the onboard vga-out.

then ubuntu booted up for me just fine, but to use my nVidia GeForce video card again i had to blacklist the onboard video drivers like so:
```
sudo gedit /etc/modprobe.d/blacklist
```

of course u could use "vi" or whatever editor u wanna... and paste this at the end of the file...

```

#Blacklist onboard Intel drivers
blacklist agpgart
blacklist intel_agp

```

then save it, reboot.. go back to the bios and switch it back to PCI, then switch the cable back to my my video card's out.. and it was all good. =)

---

### Post by nclester on 2008-04-03
Dude, you rock. I've been battling this problem for like weeks, maybe even a month or so and now I feel like I'm getting somewhere. 

I tried to run Ubuntu using my VGA, but forgot to switch the BIOS settings. Now it's making it past the Ubuntu loading screen, but lags bad at the next screen. All I see is black. 

I'm going to boot into recovery, and see what I get. Then I'll go ahead and try some boot parameters if that doesn't give me an answer. 

I'm glad you figured out your machine mdkaneda55, I'll keep you posted on my trials. 

Thanks again everyone, I hope to have this POS up and running Ubuntu tonight : )

---

### Post by nclester on 2008-04-03
Okay, so I ran the recovery console and came to a CLI screen. 

This is the last line, and it allows me to add commands. 

root@Bessy:~#

I have no idea what to tell it to do. I tried using "boot" with nothing. 

Any advice?

---

### Post by mdkaneda55 on 2008-04-13
> **nclester said:**
> Okay, so I ran the recovery console and came to a CLI screen. 

This is the last line, and it allows me to add commands. 

root@Bessy:~#

I have no idea what to tell it to do. I tried using "boot" with nothing. 

Any advice?

sorry about the late reply, but here's what you gotta do.. when u boot into recovery mode, do this..
```
vi /etc/modprobe.d/blacklist
```
now your looking at the blacklist file in the VI editor, press down till u get to the bottom, press the letter i to type something, then type this in (you'll probably have to write it down now =)
```

#Blacklist onboard Intel drivers
blacklist agpgart
blacklist intel_agp

```
now when it looks exactly like that, press the ESC key, then type  " :qw " and press enter to write it to the file. a little hint using VI, if u highlight something and press X it'll delete it, its a pain to use when ur not familiar, but you'll get it. =)

now the next step is back at the prompt, type "reboot" to restart the computer, then fire up your BIOS settings again, switch back to PCI and save, switch your VGA cable back to your video card's vga-out, then you should be able to boot ubuntu normally (i hope!! worked for me)

hope that helps!!!

---

