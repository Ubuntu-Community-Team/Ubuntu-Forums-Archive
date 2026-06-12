---
title: "busy box message after installation"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Allegheny on 2007-01-28
Hello everyone,

I am having a problem getting Ubuntu to start after installation - the machine posts, then grub loads and then I seen the Ubuntu logo with the status bar (status bar shows a hairs thickness of progress) - and that's as far as it goes.  After several long minutes the machine jumps to a busybox message:( 

The machine has a M2N32SLI-Deluxe Board (nVidia 590 chipset) with an AMD X2 4600, nVidia 7600 graphics (1 card - NO SLI), 2 GB or RAM, 8 SATA 400GB Seagate Drives, Audigy 4 Sound (onboard sound disabled).

I have installed the lates bios for the board 0904 - advanced features turned off (SLI, PEGLINK, NEW VISTA POWERMANAGEMENT THINGY)

The Ubuntu Live CD works fine.

I decided to try OpenSuSe 10.2 just to see if Linux would work on this board and OpenSuSe had no troubles installing and working properly.

I know OpenSuse 10.2 is using a newer Kernel than Ubuntu 6.10 - Maybe this is why OpenSuSe works and Ubuntu does not.

But I am hoping someone may have some ideas that I could try to get this thing to work with Ubuntu.

See the problem is... I'd really rather use Ubuntu :)

---

### Post by kuja on 2007-01-30
If you're feeling curious, you could try out Ubuntu Feisty. It isn't due for release for a while, but that would tell you if it works with your hardware eh? 

On a sidenote ...... that's a lot of hard disk space!

---

### Post by Digital Magi on 2007-01-30
I had a similar problem. The Edgy live CD worked fine but after installation ended up at busybox prompt. Same thing using the alternate install CD. Never could get it to work after several tries.  I searched these foums and found quite a few posts quoting the exact same busybox error message I got ("/bin/sh:can't access tty; job control turned off") so it isn't just you.

An install of 6.06 on the same machine went cleanly and is what I am using right now. Dunno if there is a fix yet. I am skipping Edgy for now as I can't get it to work and will try Feisty whenever it is released.

Funny that an older version works fine while the newer locked up.

---

### Post by Allegheny on 2007-01-30
Thanks, for your input....

I too have discovered that the older version 6.06 works????  It is strange, I know - but it does.

I have seen many posts regarding the busybox error as well and found no real solution.

However, yesterday evening I read a post on another forum (can't remember where I saw it) that stated with the newer nVidia chipsets and Edgy you have to 1.  Do a text only install and also disable ACPI support within Edgy.  That person went on to state that the problem exisits in all versions of linux & the newer nVidia chipsets.  I know the second statement is not true so, I have to question the reliabilty of the whole thing.  That being said - I may still give it a chance.

At work, I had similar problems with SuSe 10.1 - just could not get it to install.  Suse 10.0 worked and now so does 10.2.

My assumption is that it is a problem with the older (in computer years) kernal that hopefully will resolve itself with Feisty.  Either that or SuSe has figured somthing else out.

My next task is to try Feisty just to see if it works - but I worry about how many other new problems I will have using pre-released software.

Well, I am off to test Feisty :)

---

### Post by Allegheny on 2007-02-04
Yikes.... Feisty is even worse; won't even get through installation.  Just for kicks I have downloaded the weekly build of Debian and may give it a try.  It probably will not work either, leaving me with OpenSuse (the only one that seems to work right now on this board).  I guess this means it is not the linux kernal as Feisty has a newer kernal than OpenSuse 10.2.  I would and might try Fedora - but I am running out of time playing with all this and need to get this system working.

Note:  I am trying basic installs.  I am aware that some people post success with disabling ACPI - but I want a distribution that works without any handicaps.

I wonder, in the back of my head.... if these problems do not have something to do with the new DRM built into most of the newer hardware.  My motherboard has an option to disable "Vista Media Enhacements" under the power management features in the bios.  I keep this disabled.  It is odd though, with Novell's deal with Microsoft.... that their linux distribution is the only one that works with this board with no real trouble or configuration changes.  However, sound problems abound with this system and OpenSuSe.  Sound issues I have never had with Linux.

Maybe I should go back to paper and pencil.....

---

