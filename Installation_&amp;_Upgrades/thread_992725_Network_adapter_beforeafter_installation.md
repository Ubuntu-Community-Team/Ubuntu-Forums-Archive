---
title: "Network adapter before/after installation"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Scarlath on 2008-11-25
Hello!

I just installed Ubuntu 8.10 on my system (dual boot with Windows XP). When I tried it out in the Live CD I had access to my wireless usb network adapter and could surf the web with no problems whatsoever (out of the box), so today I went to install Ubuntu 8.10 on my system. There were no problem what so ever to do it, I might add ;)

However, after installation it seems that either my network adapter isn't recognized anymore or that it cannot pick up any signals, which is weird seeing as it worked both under the Live CD and under Windows XP (from which I'm writing this message).

My wireless usb adapter is a D-Link DWL-G122 (rev. C1) which I've read about that it should work out of the box, too. Is there some way I can "activate" it in Ubuntu? Would unplugging and replugging it during running Ubuntu work perhaps?

Thanks in advance!

ps. I didn't really know where to place this thread so I went ahead and put it in here, if it's the wrong board feel free to move it :)

EDIT: Oh, and I've got a few questions regarding other hardware too, for instance: 
1) My speakers work fine, but my I'm not getting any sound in the headset (both are connected at the same time, I tried by pressing "Test" in the sound-settings-thingy). Is there a way of solving this? I have some sort of Realtek sound card I believe. I'm afraid I do not know any more than that though.
2) Once I got my internet working, what graphics drivers should I use? I've got a nVIDIA GeForce 6200LE. It says that 177 is recommended, should I pick that one?

---

### Post by Scarlath on 2008-11-25
Forgot to mention that I kept it plugged in during installation (didn't run the installation through the live enviroment though but several days after I tried it out via the Live CD, so I wouldn't of known if it worked or not) seeing as I had to download extra language support (I didn't get this though :p)

EDIT: Oops, realised I should of had edited my post instead of making a new reply. Sorry!

---

### Post by manishtech on 2008-11-25
Am not sure whether this can be a way to find out the info about the usb one, but please post the output of these commands

> lsmod | grep -i ether

> lsmod | grep -i usb

---

### Post by Scarlath on 2008-11-25
Do you mean the command "lsusb"?

I did that one (meaning lsusb) and here's the output (bare with me, I had to scribble this down on a note by hand.. then typing it all out again here, so there might be typoes):

ludvig@ludvig-desktop:~$ lsusb
Bus 005 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]

There were more to it after that but nothing relevant to this (seeing as I have no other USB devices plugged in :P)

Ugh, one scary thing to add to it, once I rebooted into Windows, and got up my desktop - my computer restarted, which seemed weird (I was poking on the settings on my monitor which might have caused it but not sure.. either way, seems to be working fine now)

---

### Post by manishtech on 2008-11-26
By doing lsusb, it finds the name of the hardware device attached to USB ports.
By the above two commands, I just wanted to see whether the modules are loaded or not.

No! I didnt mean lsusb, but please post the output of those two commands. Just being recognized is not enough, the kernel modules should also be loaded.

---

### Post by Scarlath on 2008-11-26
Oh, okay, sorry.

Here are the outputs for the two commands:

```
ludvig@ludvig-desktop:~$ lsmod | grep -i ether
ludvig@ludvig-desktop:~$
```

```
ludvig@ludvig-desktop:~$ lsmod | grep -i usb
rt73usb 30464 0
crc_itu_t 10112 1 rt73usb
rt2x00usb 18816 1 rt73usb
rt2x00lib 36224 2 rt73usb,rt2x00usb
mac80211 216820 2 rt2x00usb,rt2x00li
usbcore 148848 5 rt73usb,rt2x00ubs,ehci_hcd,uhci_hcd
```

I might have typoed something seeing as I have to "transfer" this by hand from Ubuntu to Windows in order to post here so.. yeah :p

---

### Post by manishtech on 2008-11-26
Hmm! The rt73usb module which is provided by default is broken. Its bad you are facing this problem. Linux does have wireless problems since the manufacturers dont release Linux drivers and free volunteers write down drivers by guessing and reverse-engineering. So its natural that is would not be perfect as expected.

To come over this problem, please go through this bug report. The steps to make it working is given in post 2 and post 3. I understand it would be cumberstone to do such work, but believe me, its fun doing all such things, though at beginning it looks weird. If you have any problems report back.
Bug Report: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264)

---

### Post by Scarlath on 2008-11-27
Hmm, indeed. How can it be broken if it worked flawlessly while using the LiveCD though? That's what I do not understand. It shouldn't be *that* complicated to get it working. 

And by the looks of it, to follow the instructions included in the bug report I'd have to have access to an internet connection... which I do not have under Ubuntu. I'd rather try an other solution for now (if any).

Can one somehow fix it via the LiveCD (as in perhaps copying a file from the CD to the harddrive (as they did in [this post]("http://pennsylvania.ubuntuforums.com/showpost.php?p=5971799&postcount=14"))?

---

### Post by manishtech on 2008-11-27
I think you hit the nail on the head. I think you should do the same.

Just keep a backup of the file you are replacing.

---

### Post by Scarlath on 2008-11-27
Okay, so that didn't really work. I booted off the LiveCD, mounted my /home partition but I couldn't figure out how to copy the file from one location to another. When I had chosen "copy" and went to e.g the documents folder the "Paste"-option was greyed out. It said "rt73.bin will be copied once you paste the file" or something along those lines. Perhaps I should try booting the operating system and then mounting the CD instead...

What's worst is that my connection *no longer works when using the live enviroment either*! So I doubt copying the file will do anything good anyway... I'm seriously scratching my head over this matter.

1. In live enviroment - network works perfectly.
2. Few days later I install - cannot even see any network in the network manager.
3. Today, in live enviroment - cannot see any networks here either.

What the hell is happening? I'm so confused. :(
Are you sure that it's not something really simple like a little box to click or a button to push? There must be something small (or not so small) thing that I've missed!
Perhaps I should post this in the Networking part of the forum?

---

### Post by manishtech on 2008-11-27
Actually you have to copy that file from the LiveCD installation to the partition where you have installed.

I suggest you to mount the / of installed ubuntu partition instead. Then in terminal type
gksudo nautilus

and then try to copy the file. I assume you have mounted / of ubuntu on /media/sdax
Now copy the file **/lib/firmware/RT73USB.bin** to [B]/media/sdax/lib/firmware/RT73USB.bin

[/B]Just take a backup of the original /media/sdax/lib/firmware/RT73USB.bin before copying

---

### Post by Scarlath on 2008-11-27
If I couldn't access the network when I booted off the Live CD again now though, would it really matter if I replaced the file?

What do you mean by that I have to "copy that file from the Live CD installation"... I have to select "Install"...? That doesn't seem to make sense. Also, why would I be able to copy the file to the root partition but not the home partition?

As I wrote in my last post, perhaps I should try the Network & Wireless board?

---

### Post by manishtech on 2008-11-27
Just give it a try. Am not 100% sure it would work, if that doesnt work, then you have to go the hard way.

As I pointed out the link in last page, at bugs.launchpad.net link

---

### Post by Scarlath on 2008-11-27
As before, I wasn't able to copy files to other locations. I just couldn't "paste". Besides, neither my installation nor Live CD (/lib/firmare/)seem to contain the file RT73USB.bin, only the RT73.bin.

I have decided to post this thread in the Network & Wireless board instead as I might get more help there than in this board seeing as this isn't really the correct place. If you'd like to continue to help me please post [here]("http://ubuntuforums.org/showthread.php?p=6263062#post6263062") instead.

---

