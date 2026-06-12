---
title: "Ubuntu 6.06 boot stalls while loading hardware drivers"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by piponline on 2007-01-22
Hello all.

I'll start by saying that I'm a newbie: this is my first real attempt with Linux. I'm a windows xp user, but a tired one, very willing to try an alternative as long as it comes for free.

Before Ubuntu, all I ever did was a couple of very brief (but successful) runs with MandrakeMove, with a live cd I got somewhere. 
Also - I don't know if this is worth mentioning (have I already told you that I know nothing about linux?) - a few weeks ago I tried to boot with a "gparted" cd but it never worked: it stalled everytime.
Then I installed ALINEX ([www.alinex.org)](www.alinex.org)), a portuguese university distro, but I could never get it to boot. This distro's support & forum are too poor and that drove me to Ubuntu. I believe both distros are debian based, unless otherwise (for I'm a complete zero on this).

Back to Ubuntu.
Instalation was a big pain. I'll save you the details for I don't think they are relevant and I'll just say that it took me a few days and nights to get Ubuntu installed: first I tried Dapper, then Edgy and with neither one I managed to overcome their stalling tendency. Then I tried 6.06 alternate cd and it worked. 
So this is where I am, with Dapper installed but unfortunately not booting.

I have been around this forum, I've read many posts about similar problems, tried everything, boot parameters, unplugged all the usb devices, etc., but still nothing.

Here's a list of my hardware components:
-->Pentium 4 CPU 3.00GHz, 512 RAM
-->120GB disk partitioned as follows: 2 NTFS partitions for WXP, one ext3fs and a SWAP for Ubuntu
-->inboard C-Media AC97 Audio device
-->Creative Sound Blaster Live! series (WDM)
-->NVIDIA GeForce4 MX 440
-->Realtek RTL8139/810x Family Fast Ethernet NIC
-->LG DVDRAM GSA-4160B
-->PHILIPS CD-ROM PCCD048

And here's what's going on when I try to boot.

1 - if nothing is changed at boot, it goes graphically to the point where it is "Loading hardware drivers..." (after "Preparing restritecd drivers", "Starting basic networking" and "Starting Kernel event manager"). Then the progress bar stops and that's the end of that.

2 - editing boot options, I remove the 'quiet' and the 'splash' so that it goes like this 
"Kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro". 
I end up with a lot of verbose that stops with "Kernel panic - not syncing: fatal exception in interrupt".

3 - with the 'noapic' parameter the error was even more scary: 
"Sysenter_past_espx0x54/0x79
Code: [...three lines of numbers here]"
(don't forget I have no idea of what this is for, I try these parameters just like I would press F7 39 times if this forum had told me so).

4 - then I added the 'nolapic' parameter which stalled me here:
"Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected an Intel 865 chipset
agpgart: No pre-alloacted viedo memory detected
agpgart: AGP aperture is 128M @ 0xf0000000"

5 - At this point, I confess, I thought I was kind of understanding this stuff. So I gave it another go but this time with also the 'noagp' parameter. But nothing changed...

All other parameters that I tried didn't produce any change. These tests were also done with the Ubuntu recovery mode.

So, can anyone help, please? 

This is so confusing and frustating: if it installed (although after a lot of trouble) why doesn't it boot? I ended up with the same problem I encounter with the other distro (ALINEX). What is it with my hardware that causes the problem? It's just a regular pc...

Also I've read some frightening posts about people reporting cases where sometimes the machine boots ok and sometimes it doesn't!!! I'm getting affraid this is too time consuming for me.

For the time being, and while my problem with Ubuntu isn't solved, I'd like to know how can I change the default system that goes off with grub. Right now it's Ubuntu and I would like to change that to Windows XP.

I think I thought of me as a human before this. Right now, though, I feel like a dumb ***. And by the way my wife has looked at me in these last days, she's not thinking anything much different from that.

Thank you for all the help you can provide.

---

### Post by wpshooter on 2007-01-22
Piponline:

Here is my suggestion for you.

Find yourself another computer, an older one than you have described above, but if you already have another computer that is not be used use it.

Then try installing Ubuntu ONLY (no other O/S to be used on it), so you can sort of get a grip as to what you are doing.  In other words, try to learn how to walk before you try to run (and I am not say that in a derogitory way at all, just trying to help).

If you can find another computer, then go to this site and download and run the KILLDISK program on that computer so you can WIPE the hard drive clean and then attempt to install Ubuntu ONLY on it.

[http://www.killdisk.com/](http://www.killdisk.com/)

Make sure that when you are burning your Ubuntu ISO to your CD that you are burning at 4X or less.

Make sure that you are checking the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Run the memtest that is found on that same menu.

If you have problems getting started into the installation process try using the safe video mode parameter.

If that does not work then go back and download and burn the ALTERNATE (text based install) version of Ubuntu instead of the DESKTOP (live) version.

Let us know how things go.

Good luck.

---

### Post by piponline on 2007-01-23
wpshooter,

Thank you for answering although I won't follow your suggestion.

Come on, if I really need a new (or different) computer to ride Ubuntu then I don't want it after all.

On the other hand, perhaps I wasn't clear enough in the previous post: I did get it installed with the Alternate cd, so it's not (no longer) a problem with the installation but rather with the first boot.

Anymore ideas, please? Anyone?

Thank you.

---

### Post by piponline on 2007-01-24
Ok, I finally managed to boot! :D
The problem is definitely with the NVIDIA card: I went to BIOS set-up and disabled it (reverted to the onboard graphical card) and then tried to boot. An error related to x-server came up in a very messy graphical screen. Then I tried to boot from the cd and bingo! At last, a real taste of ubuntu!
After that I decided to reinstall the thing all over again just to save me the trouble of debugging the graphical problem occurring in the hard drive version.

And it worked. Now I can boot without a problem.

The only problem now is that I really want to use my NVIDIA card, of course. Tonight I’ll try to configure it properly following these instructions: 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

I’ll then update this post as it might be of help to others.

---

### Post by piponline on 2007-01-26
:guitar: 

Ok, problem solved!!!!
More info [[COLOR="Blue"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=346512").

---

