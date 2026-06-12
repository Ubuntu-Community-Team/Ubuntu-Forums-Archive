---
title: "System problems after installing hardware upgrade in 12.04"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2014-10-09
**EDIT: Refer to the last post by me (davy jones) in the thread. It contains a summary of my entire problem and what I need help with.**

I absent mindedly clicked on the 'install new hardware' link in Update Manager and this has caused some major problems with my system even though there was no such warning during installation.

First, on startup, there is a Grub screen in which I have to manually select whether I want to boot into my OS or not which wasn't there earlier. Also, clicking restart has become useless because the system begins to reboot but then stops at a black screen and I have to manually shut it down by pressing the power button.

Second, while booting, I get a message saying that my system is running in low graphics mode and gives me some options to either log in once with low graphics or reconfigure them. The latter doesn't work, so I just select the first (my login screen is also different - the layout is different, my wallpaper doesn't show etc)

After logging in, when I try to start AMD Catalyst Control Centre, it says that no graphics driver is installed.

Also, I get messages saying that there is no space left in the /boot folder (or maybe the boot partition?)

I need an immediate solution to these problems. Thanks.

---

### Post by kc1di on 2014-10-09
It sounds like you've corrupted your AMD driver
Try [this page]("http://askubuntu.com/questions/450394/amd-catalyst-installation") and reinstall it.

---

### Post by davy jones on 2014-10-09
Thanks for the quick reply.

Actually, purging flgrx took care of most of the problems I was facing. Now, I don't have an AMD driver. I tried to install the latest proprietary driver, but apparently I'm missing some dependencies and I can't figure out what those are. This is not all that urgent because based on the battery consumption, it seems that my system has preserved the switchable graphics settings I selected in Catalyst Control Centre, but I would like to install the new driver anyway. Otherwise, I don't generally have heavy graphics usage.

The bigger problem is probably the message that says that the boot partition has no space left. I don't know if it's because of this or not, but my system is taking longer to boot now. How do I fix this?

---

### Post by kc1di on 2014-10-09
Some will disagree with me, but I find the system cleaner in Ubuntu Tweak to works very well 
it will clean out any old kernels and other junk that should give you added space.  I suspect that when things were not working right
it generated may log files that are filling up the partition. 
you can get ubuntu-tweak[ here ]("http://ubuntu-tweak.com/")

---

### Post by davy jones on 2014-10-10
I did a clean-up using Ubuntu Tweak and now the system won't boot at all. It gets stuck either on a completely blank screen or a screen which says "could not write bytes: Broken pipe". I am really annoyed with Ubuntu right now. I know I should've checked the repercussions of installing a hardware upgrade but it is also quite ridiculous that there was no warning while I did it. There's only so much they can leave to the user because not everyone is an expert.

This is officially a code red situation. Please help ASAP.

---

### Post by kc1di on 2014-10-10
[Go here ]("https://help.ubuntu.com/community/Boot-Repair")and download and run boot repair see if it restores your boot options.

You may also want to think about a re-install.  and I would use 14.04 if it were me. 
Let's go back to the beginning and find some information from you.
What is the machine your installing on. Is it dual boot with windows. How much ram, CPU, Video Card type. Etc Give us as much info as possible. 
and we will see what we can do to get you up and running with a good desktop.

If you have important data that need to be recovered , use the live DVD. and copy the files to an external media , DVD , Usb Drive -etc.

This isn't a WUBI install is it. if it is then I would do a regular install and not bother with WUBI.

---

### Post by davy jones on 2014-10-10
I tried to boot with a live CD but even that didn't work. It was the same disc with which I installed Ubuntu so I doubt that this is happening because it wasn't burned properly.

I have Dell Inspiron 3521 which came with Windows 8 pre-installed. The BIOS version is A05. It has 4 GB RAM. The system has dual graphics - integrated Intel(R) HD 4000 and a Radeon HD 8700 - total of 2 GB. It is a 64 bits system. It is not a WUBI install.

I can't seem to remember how exactly I installed Ubuntu because right now I can't find any option that would let me boot from the DVD drive. Ubuntu boots from Legacy and Windows from UEFI. In UEFI, there is no option to boot from the DVD drive. In Legacy, it gives me three options - Network, Hard Drive, DVD drive (in that order), but there is no option to change the order. If I select the DVD drive, click enter, save changes, and exit, it still boots from the hard drive and ends up getting stuck on the screen I mentioned.

I was going to upgrade to 14.04 from Update Manager once I made sure that my settings and data wouldn't be affected, but now I just need my system to boot.

I'm going to try to run boot repair from a disc. I just want to check how to burn the disc in Windows since I haven't done it before. Recommended software, which options to select, etc. Thanks for the help.

---

### Post by davy jones on 2014-10-10
EDIT: I managed to boot from a Boot Repair disc and it basically made me remove GRUB from Legacy and install it in EFI.

This is what the bootinfo was before it did its thing -
[http://paste.ubuntu.com/8533672/](http://paste.ubuntu.com/8533672/)

And this is what it was after -
[http://paste.ubuntu.com/8533762/](http://paste.ubuntu.com/8533762/)

Whatever it did, did not work, because the exact same thing is still happening. Now since I have to boot in UEFI, the GRUB screen shows up every time.

---

### Post by davy jones on 2014-10-10
Unless there is another solution (or even if there is), I think my only choice is to install 14.04. But I need detailed, step-by-step instructions on how to go about doing this in my current situation, which is that I have a dual boot with Windows 8 and Ubuntu 12.04, both booting in UEFI, but Ubuntu is not booting. So I need to know whether 14.04 will use the same mount point or not. I also need to know how to install it, because there doesn't seem to be an option to boot from the DVD drive in UEFI. I would also need to back up my data, and if possible I would like my settings and applications to remain unchanged. I know this is a tall ask, but I thought it might be possible, since upgrading to 14.04 from Update Manager claimed to leave your settings unchanged, and I have a lot of different settings here and there along with several apps and it's a real pain to get them all back manually (which is why I like to install LTS versions and just leave them be for as long as possible).

I know it might be frustrating and painstaking to give very detailed instructions, but I would really, really appreciate it. More importantly, I need it.

---

### Post by davy jones on 2014-10-11
**I'm summing up my entire problem here so that anyone can read only this one post and guide me on what to do next.**

I have Dell Inspiron 3521 which came with Windows 8 pre-installed. The BIOS version is A05. It has 4 GB RAM. The system has dual graphics - integrated Intel(R) HD 4000 and a Radeon HD 8700 - total of 2 GB. It is a 64 bits system. I installed 12.04 in it which used to boot in Legacy. It is not a WUBI install.

A few days ago, I clicked on the 'upgrade hardware support' option in Update Manager. This screwed up my system. The graphics driver, flgrx, no longer worked, and my boot partition became completely full. I managed to purge flgrx but wasn't able to reinstall it properly. I did a clean-up using Ubuntu Tweak, so that it would clear up the boot partition. After I did that, Ubuntu just would not boot. It would get stuck on a screen that says "could not write bytes: Broken pipe".

I booted from a Boot Repair disc which basically made me remove GRUB from Legacy and install it in EFI. This is what the bootinfo was before it did its thing -
[[COLOR=#dd4814]http://paste.ubuntu.com/8533672/[/COLOR]]("http://paste.ubuntu.com/8533672/")

 And this is what it was after -
[[COLOR=#dd4814]http://paste.ubuntu.com/8533762/[/COLOR]]("http://paste.ubuntu.com/8533762/")

Whatever it did, did not work, because the exact same thing is still happening. Now since I have to boot in UEFI, the GRUB screen shows up every time.

Now I think my only choice is to install 14.04, but I need detailed, step-by-step instructions on how to go about doing this in my current situation, which is summed up above. I need to know whether 14.04 will use the same mount point or not. I also need to know how to install it, because there doesn't seem to be an option to boot from the DVD drive in UEFI. I would also need to back up my data, and if possible I would like my settings and applications to remain unchanged. I know this is a tall ask, but I thought it might be possible, since upgrading to 14.04 from Update Manager claimed to leave your settings unchanged, and I have a lot of different settings here and there along with several apps and it's a real pain to get them all back manually (which is why I like to install LTS versions and just leave them be for as long as possible).

Quick help with detailed instructions would be highly appreciated. Thanks in advance.

EDIT: I'm hoping that the delay in replying is because someone is trying to figure out what the problem is and how exactly to solve it. If not, then please do, because this is extremely urgent.

---

