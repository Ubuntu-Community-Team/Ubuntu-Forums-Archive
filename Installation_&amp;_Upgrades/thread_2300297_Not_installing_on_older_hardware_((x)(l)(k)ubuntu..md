---
title: "Not installing on older hardware ((x)(l)(k)ubuntu/... etc, 14.04 or 15.10, 32-bit)"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by Jcj91 on 2015-10-24
Ok folks, I am certainly no regular on this forum, usually I manage quite well on my own or with answers already posted on this forum. Now, however, I've got myself good 'n stuck. I've googled and searched my head off, coming across pages on this forum, pages on Ubuntu Help, Linux forums, Debian forums and whatnot, but I haven't found the definitive solution to my problem. My guess is I must either be missing something really obvious, or this is something new.

I recently attempted installing Ubuntu GNOME 15.04 on my dad's old laptop, and 15.10 here on an old (2006-ish) computer at home which me and the flatmates use for basic household stuff . However, in both cases I ran into (seemingly) the same problem.

**Problem description**
Once having booted up from the startup disk and showing [this screen]("http://listthemout.com/wp-content/uploads/2011/04/install-ubuntu.png") I choose to proceed with either '*Try (X)(L)Ubuntu without installing*' or '*Install (X)(L)Ubuntu'*. No matter which of these options I choose, the screen goes black with the blinking cursor in the upper left, not responding to any keyboard input whatsoever.

[B]Additional info
[/B]- I usually create disks by *dd*'ing the .iso straight to the stick (e.g *dd if=imagefile.iso of=/dev/sdb*), which until now had always worked fine. For the sake of trying to stick to recommended methods I have tried using *startup-disk-creator* and *UNetbootin* for disk creation. I have even go so far as actually burning a physical startup DVD and booting from that. The result was all the same: black screen with blinking cursor, never entering the installer.

- Same across startup disks of Ubuntu, Lubuntu, Xubuntu and Ubuntu GNOME, all 32-bit (couldn't be bothered to try more).

- A [proposed solution]("http://askubuntu.com/questions/329704/syslinux-no-default-or-ui-configuration-directive-found") I came across was to rename the 'isolinux' folder and the 'isolinux.cfg' and 'isolinux.bin' files to 'syslinux', syslinux.cfg' and 'syslinux.bin'. Tried this, this did not fix it.

- I'm also having this problem with the Debian 8 startup disk (probably worth mentioning)

Any help with this will be greatly appreciated, as I have always considered enabling legacy hardware to be one of Linux's (and the Ubuntu family) major strengths.
[B]
Edit: conclusion and recommendations to others with a similar problem
[/B]As the symptoms on both machines were exactly the same, I thought I was dealing with the same problem on both machines, and thought this warranted one thread. I turned out to be wrong. Fixing a rogue BIOS setting on the old desktop machine (a CPU setting, can't remember which one) turned out to fix the problem.

As for the laptop I've come to conclude I was dealing with a mysterious hardware problem. As Debian happened to run and install just fine on that machine, I installed that instead (odd that Debian worked and *buntu didn't?). These are the further steps I've tried, and I recommend anyone facing a similar problem to investigate these:

- Verify integrity of the downloaded file with an MD5 checksum >> [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
- Try using the [minimal install ISO]("https://help.ubuntu.com/community/Installation/MinimalCD"), as it has a non-graphical interface for the installer (similar to Debian's non-graphical installer)
- If you're getting an [COLOR=#000000][FONT=courier new]Undefined video mode: 314[/FONT][/COLOR] error, then try adding any of the following kernel boot parameters: [FONT=courier new]nomodeset[/FONT] [FONT=courier new]vga=normal[/FONT] [FONT=courier new]acpi=off[/FONT] [FONT=courier new]noacpi nolacpi >> [/FONT][http://ubuntuforums.org/showthread.php?t=2043103](http://ubuntuforums.org/showthread.php?t=2043103)
- For some old Dell machines, there is a particular BIOS setting that might need to be adjusted, the [FONT=courier new]Video Buffer[/FONT] in [FONT=courier new]Integrated Devices[/FONT] from 1 MB to 8 MB: >> [http://forums.debian.net/viewtopic.php?f=17&t=62241](http://forums.debian.net/viewtopic.php?f=17&t=62241)

---

### Post by kurt18947 on 2015-10-24
I make no guarantee but this has worked for me on older machines.  How to accomplish this varies by distro but there is some means to edit the boot parameters. I've found appending "nomodeset" is often helpful if the blank screen is caused by a video incompatibility. There was one netbook where I had to add both "nomodeset" and "noapic".

---

### Post by Jcj91 on 2015-10-24
I caught on to this possibility too at some point. I tried nomodeset, and also vga=ask. The best this did for me was ask me which vga setting to choose from a list of defined vga settings, only to proceed into the black screen non the less :(

---

### Post by coldraven on 2015-10-24
To start at the beginning have you tried checking the checksums of the downloads?
Go here, select your version and then scroll down to see the MD5SUMS. (Also handy if you want to use the torrent option)
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)
Get the checksum like this, (use the tab button to autocomplete the filename)
```
md5sum your_download.iso
```
Ctrl+Shift+C to copy it, then while looking at the checksums in your browser do Ctrl+F and then Ctrl+V. 
If correct the checksum will be highlighted on the page.

---

### Post by Jcj91 on 2015-10-25
Went ahead and did the md5 checksum as you said, and it indeed turned out that the checksum for the particular Xubuntu image file I was using was in fact incorrect. I downloaded the image file again, now the md5 and even sha256sum were correct.

However, this did not change anything; it still proceeds to the black screen with the blinking cursor.

I forgot to mention in my earlier post that after a while (5 minutes or so) the black screen with the blinking cursor suddenly shows [text output]("http://i.imgur.com/RtkLWDB.jpg"). It refreshes this 4 or 5 times, then the screen goes completely black with even the blinking cursor gone.

---

### Post by sudodus on 2015-10-25
A computer from around 2006 might work better with a medium light flavour of Ubuntu, Xubuntu or Ubuntu MATE, or an ultra light flavour, Lubuntu. There are also indications that there are problems with the graphics.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It helps us give good advice. Otherwise we can only guess.

---

### Post by Jcj91 on 2015-10-25
OK, the computer that I have access to right now:

**Dell - Optiplex GX270**[I]

[SIZE=2]Intel Pentium 4
Clockspeed: 2.6 GHz
CPU Speed: compatible
Level 2 Cache: 512 KB integrated
hyperthreading disabled
Bus speed: 800 MHz
Processor 0 ID: F29

BIOS version: A04
service Tag: 7Y6N71J

1024 MB DDR SDRAM
400 MHz
System memory channel mode: dual
AGP Aperture: 64 MB

GPU: (onboard) Integrated Intel Extreme® Graphics 2. 

Networking: Intel® PRO Gigabit2 Network Connection with support for Remote Wake Up and Alert Standard Format (ASF 1.0).
[/SIZE][/I]
The other machine (the laptop) I don't know, as I don't have it here myself, but I can post them once I have access to it again. I do know that that machine has run Win 7 in the past.

---

### Post by sudodus on 2015-10-25
Pentium 4 is low end for today's linux, but it has horsepower enough for Lubuntu, Xubuntu and Ubuntu MATE. I would not try standard Ubuntu or Kubuntu.

1 GB RAM is plenty for Lubuntu, and enough for Xubuntu and Ubuntu MATE. Standard Ubuntu and Kubuntu need more RAM to run well. Some people may say something else, but this is my experience.

It may help with the old Intel graphics to try UXA acceleration according to this link

[Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

The Intel network should be no problem.

-o-

The following link may inspire you,

Post #126 [She isn't a 'powerhouse', and never will be; the P4 architecture is the biggest bottleneck now. But as a day-to-day laptop, I think this old lady is eminently usable.](http://ubuntuforums.org/showthread.php?t=2130640&page=7&p=13378479#post13378479)

See also the first *tutorial* post in that thread,

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by Jcj91 on 2015-10-25
Thanks for the extra info, but just to be clear here, my problem isn't the computer being slow, my problem is that **the installer sequence isn't starting at all**. We have had Xubuntu working on this particular machine in the past (the hard drive has since been reformatted, I'm trying to install it again), so I'm not convinced yet that this a hardware problem.

I've had a look at the [Lubuntu/AdvancedMethods#Old_Intel_graphics]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics") link about enabling UXA acceleration. It instructed me to manually create [FONT=courier new]/etc/X11/xorg.conf[/FONT] with specific entries. I guess that this assumes a system that's already installed and running, which is certainly not so in my case. With no better idea of my own I decided to see what would happen if I created this file in the .iso archive (where else?) and build the live volume from that, and then try again.

I'm sorry to say (and not suprised that) this did absolutely nothing as far as I can tell. The problem persists.
[B]
Update: seems I missed the whole thing about alternate installs on minimal CD images with non-graphical installs. I'm going to try that instead[/B]

---

### Post by sudodus on 2015-10-25
You may have better luck with a light-weight community 're-spin', based on Ubuntu 12.04 LTS, which is still supported (until April 2017). You can try ***Bento, Bodhi, LXLE***. The reason why these linux distros might work better is that the kernel and the drivers are older. Support for some old hardware is dropped in the newer versions.

Why re-spin and not Ubuntu itself? - Standard Ubuntu needs more 'horsepower' and RAM.

Why re-spin and not Lubuntu, Xubuntu, Ubuntu MATE? - Lubuntu and Xubuntu of version 12.04 have passed end of life. There was no Ubuntu MATE for that version. The closest alternative is to tweak Ubuntu according to the following link, and it is a real alternative alongside the community re-spins, if you can install and boot Ubuntu 12.04 LTS.

[PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by sudodus on 2015-10-25
> **Jcj91 said:**
> 
Update: seems I missed the whole thing about alternate installs on minimal CD images with non-graphical installs. I'm going to try that instead

This might be a good idea :-)

---

### Post by Jcj91 on 2015-10-25
I almost thought I was onto something, but alas.


I got the error [FONT=courier new]Undefined video mode: 314[/FONT]. It had happened before, but a menu would appear afterwards allowing me to choose from a list of video modes, the largest of which was 800 x 640. However, upon selecting that video mode, the dreaded black screen would appear; sometimes with the cursor, and sometimes without.


As this wasnt the first time this error had propped up (I hadn t thought anything of it before), I decided to investigate this. I came across this thread [here on the forum]("http://ubuntuforums.org/showthread.php?t=2043103"), and the solution posted there was to add [FONT=courier new]vga=norma[/FONT]l and [FONT=courier new]apci=off[/FONT] to the kernel bootline. I tried this, but it had not effect. Still, black screen.


I came across [a thread]("http://forums.debian.net/viewtopic.php?f=17&t=62241") on the Debian user forums, which led me to a change BIOS setting regarding the Integrated Devices: change the video buffer from 1 MB to 8 MB.


I was half expecting a miracle to happen. Alas, the only difference this seemed to make was more video modes with higher resolutions. No matter which one I select, it results in a black screen ...

---

### Post by sudodus on 2015-10-25
1. I suggest that you try something based on Ubuntu 12.04, as described in post #10.

2. If still no luck, try ***Knoppix***, which is known to be good at recognizing hardware.

3. If still no luck try ***Wary Puppy*** or ***TahrPup*** (two versions of Puppy Linux).

---

### Post by Jcj91 on 2015-10-25
Ok, good news and bad news.

The good news is, the installer is running!!!

The bad news is: I am starting to suspect that I am, in fact, dealing with a hardware problem.

The reason we wiped the old Xubuntu install was that it had become literally unworkably slow from one day to the next. The mouse was lagging its input by about half a second, and it took me a good 5 or 10 minutes or so just to get a soft shutdown started in a tty. We decided to wipe it and install new.

After getting yet another black screen (note: I had added the boot option [FONT=courier new]apci=off[/FONT]) I decided not to power the machine off, leave it be and do something else. After a while the screen suddenly turned white: it had loaded the first menu of the installation process! **It had just taken more than 15 minutes ...**

Apparently then, it is working now but it is *extremely* slow. It was already taking several seconds to load just one page of text outupt (ncurses), but I hadn't thought it would be *this* slow. My guess, therefore, is that there's something gone properly wrong with this computer and, considering its age and specs, I don't think it's worth spending more time and effort in getting it to work. Me and the flatmates will find us another machine.

This does not mean this thread is over as far as I'm concerned. I have yet to try all these steps I took on my dad's laptop, but that will have to wait a few days. I'll tell you once I've gotten there.

---

### Post by Jcj91 on 2015-11-01
Update: I can tell you that the particular laptop I'm attempting to install on is a Packard Bell EasyNote MH45 with an Intel Pentium Dual Core machine. I have managed to have a live version of Debian running on it, but so far I have had zero success with any of the buntu family.

Specs:
CPU: Intel Pentium Dual T3200, 2.0 GHz
GPU: Intel GMA 4500M
Mem: SODIMM DDR2, 4 GB
BIOS version: PBPE200N.PO7

---

### Post by sudodus on 2015-11-01
Yes, it is possible/likely that you are dealing with a hardware problem.

You are welcome to continue with this thread, but if you start with a new computer and get different problems, you have much better chances to get help, if you start a ***new thread*** with a good descriptive title.

---

### Post by Jcj91 on 2015-11-02
I would like to mention that the problem on the old desktop PC was fixed by changing a rogue BIOS setting (one the CPU settings, but I don't remember which one). As for the laptop, I just didn't have any luck with any of the buntus, and I had no idea how or whether I was going to find out how to fix the problem. However, Debian did run and install just fine, so I went with that (it even runs quite smoothly!).\

I've edited my first post with a summary of the steps tried and taken. Unless anyone else has any particularly bright ideas, I think this thread is good for closing.

---

### Post by sudodus on 2015-11-03
Thanks for sharing your solutions :-)

We mark threads as solved instead of closing them. Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Jcj91 on 2015-11-04
Done ;)

---

