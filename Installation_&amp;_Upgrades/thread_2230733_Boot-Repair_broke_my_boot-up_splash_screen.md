---
title: "Boot-Repair broke my boot-up splash screen"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by SkOrPn on 2014-06-20
Woohoo finally got this dual boot thing working.

After successfully installing both Windows 8.1 and Ubuntu 14.04 in a FakeRAID mdadm environment which was one of the most nerve racking, soul searching, day wasting tasks I have ever faced, lol, I have FINALLY got it working. I read everything I could find, every how-to, every guide, and used much of what I was reading and much of what is in the Ubuntu documents to figure out on my own what was going on with Boot-Repair. Apparently Boot-Repair is just not mature enough to fully support the combination of Windows and Ubuntu on the same hard drives, within the same RAID array. Or, its just not mature enough to be properly used with RAID in general. All week it has constantly spit out incorrect copy/paste codes for the terminal, and all week I have had to figure out what it was doing wrong, fixing it and/or getting it wrong myself. Trial and error and massive amounts of perseverance = SUCCESS!

Well, today I figured out what Boot-Repair, and many of these guides and documents were missing and I fixed it myself. However, I have one last problem I hope someone here can help me solve, and yet another Boot-Repair induced symptom that occurred only after using it to fix this last and finally successful attempt at a raided dual boot config. I now have an annoyingly long line of text that flashes across the screen so fast it can not be read. Before using Boot-Repair it just booted directly to the desktop without any ugly text, and I think it did it much faster too. Below is a YT video of the text and a screenshot of my grub file.

[IMG]http://i.imgur.com/Be6oh4ul.png[/IMG]

I tried changing the grub code from

```
GRUB_CMDLINE_LINUX_DEFAULT="whateverwasherebefore"
```

 to

```
GRUB_CMDLINE_LINUX_DEFAULT="splash"
```

like you are supposed to do when you do not want to see text at boot, but that did nothing for me of course. Can someone tell me what this is and how to edit Grub to not show this text at boot time? Please

Here's the video of the text, maybe you recognize it? I do not think it is a normal boot sequence that is going on, I actually think it is repairing something each time I boot Ubuntu, but maybe that assumption is wrong. Windows boots perfectly though.

(Sorry about the loud vacuum cleaner in the background) 
[http://youtu.be/L-nOf4Ysggo](http://youtu.be/L-nOf4Ysggo) 

EDIT: I had one more thought, maybe now that I have Ubuntu actually running, maybe I should try Boot-Repair inside this working install? Instead of a Live Session?

Thank you again
Rod

---

### Post by oldfred on 2014-06-20
Its quiet splash as default.

 gksudo gedit /etc/default/grub

> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Glad you finally worked out the details. Since you now know some of the issues, it would be good to post the solutions so others can use them.

---

### Post by SkOrPn on 2014-06-20
Thanks oldfred, yeah I am happy about it to. I read that quiet splash was only for non dual boot configs. Did I read wrong? I did another boot repair and it restored the previous wrong setup and I still have the long line of text as it boots. Below is the code I now have thanks to Boot-Repair. I guess boot-repair just hates me. lol

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomdmonddf nomdmonisw"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by oldfred on 2014-06-20
Not sure why anyone would think quiet splash has anything to do with dual boot or not.

It is just the parameters that hide the booting which is also in dmesg log file and the splash screen.

Lots of info on grub in your system:
 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'

      
>  GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

---

### Post by SkOrPn on 2014-06-21
Well I just now noticed this during boot now. The quiet splash worked but I am still getting this weird message now. And it still boots and runs fine, but not quite as quick as it was.

[IMG]http://i.imgur.com/oIlwbZtl.png[/IMG]


All of this just from using Boot-Repair as the Ubuntu help Wiki suggests. I tried checking out Webmin to see if mdadm was working properly but it says I do not have a raid array. Not sure how that is possible, so I guess I got to start yet another thread to figure out what this is. Do you know what this warning is oldfred?

---

### Post by SkOrPn on 2014-06-21
OK, oldfred I managed to fix it myself. I just purged mdadm completely from the system. I wish I could run mdadm but this ubuntu install refuses to use it. In webmin it tells me that I have no mdadm or raid setups, yet in the Disk Utilty it tells me both my disks are members of IMSM and when I benchmark it, it is averaging 550 MB/s which is only possible if the RAID is working as it should.

After purging mdadm I no longer have the error messages at boot and it boots up nice and fast. Shut down (with all lights off) is only 3 seconds which is amazing to me... Although Windows feels much faster the actual data transfer is not much faster at all, so I am happy that I can at least do some real dual-boot work in Ubuntu now instead of that VM stuff I was doing for the last 5 years or so. Time to stop worrying and get finished with some much needed customizing. Oh, and I am going to get a hardware raid card as soon as I can because everywhere I look people keep saying that fakeraid is bad for Ubuntu, which is strange because its very nice for Windows. lol

Now I have to find a way to take my favorite wallpaper from the Linux Mint iso and put it on my Ubuntu desktop, LOL...

Thank you for all your help and everything you do for these forums.

Best Regards
Rod

---

