---
title: "Installing Ubuntu on ex-school laptop"
date: 2016-02-19
forum: Installation &amp; Upgrades
---

### Post by Scrollin on 2016-02-19
Hello everyone.

Here's just a little rant about the situation...

Basically I graduated from school last year and inherited the school-issued Win 7 machine. The administration refused to remove all their bloatware and install a clean copy of Win 7, because the scheme whereby students rented laptops from the school at an astronomical price ($150/year for 4 years) was discontinued after basically being considered a failed experiment. (The students who didn't want to pay were horribly disadvantaged by not having a school-issued laptop, because until 2 years ago no other devices besides the school-issued ones were allowed to connect to the network) So ultimately, I could either give the notebook back to them for no compensation, or pocket it and never speak with them again. Pretty obvious which one was the better choice.

Anyway... On to the actual problem.

I'm currently trying to install Ubuntu and I'm a bit stuck as to how I could do it. The Win 7 machine I'm trying to install it on has no CD/DVD drive, and the BIOS is passworded so I don't see how I could change it to boot from a USB. I figure somehow it's possible to get around all this, but for about an hour or so I've been trying to think of how I can do this, and nothing really comes to mind, since I'm not the most experienced at it all. What I really would like to do is totally remove everything from this harddrive, and remain only with Ubuntu.

If that's possible, please let me know how I could do that. Otherwise I think using wubi to install Ubuntu through Win *should *work fine and meet my needs if nothing else is possible. Although I've never used wubi before, and don't even know what the state of it is like now.

Thanks.

---

### Post by uRock on 2016-02-19
Have you looked into resetting the BIOS for your model laptop?

---

### Post by hakuna_matata on 2016-02-20
> **Scrollin said:**
> Although I've never used wubi before, and don't even know what the state of it is like now.

The latest official maintainance was in [URL="http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/files"]2014.
[/URL]The latest official action of a Wubi maintainer was to remove it from isos. see [URL="https://bugs.launchpad.net/wubi/+bug/1471344/comments/7"]here

[/URL]This has the undesirable side effect that older Wubi versions work better than newer ones and Wubi user keep their old Wubi versions with outdated Ubuntu versions as long as possible. There are alternates, of course, even if a standard install is not possible. e.g. a virtual machine. 

But there are also drawbacks: 
[LIST]
[*]On older machines a virtual machine is significant slower than a Wubi installed Ubuntu. 
[*]Generally, a virtual machine needs a host system and if the host system is Windows, you have to run Windows before running the virtual machine with Ubuntu. A Wubi installed Ubuntu runs without Windows, too. The Windows program Wubi only runs during the first part of installation. 
[*]Virtual machines work with every linux distro. Wubi only works for Ubuntu and official flavours. Maybe an advantage for a lot of users, but a disadvantage for Ubuntu fans...... 
[/LIST]

So maybe, there is also an interesting community project for you with newer Wubi releases: see [URL="https://github.com/hakuna-m/wubiuefi/wiki"]here

[/URL]> **Scrollin said:**
> What I really would like to do is totally remove everything from this harddrive, and remain only with Ubuntu.

Maybe a solution is to disassemble the laptop for disconnecting the hard disk and connect it as external drive with another computer, then install Ubuntu on this hard disk and finally, assemble and connect it again in the laptop.

---

### Post by Bucky Ball on 2016-02-20
Welcome. Pull the battery out and unplug all USB devices. Press the power button down for thirty seconds or more. Plug in a power cable and reboot into the BIOS. Any luck? 

On a desktop you would take the coin battery out or short the jumpers, which is what you can also do in a laptop I believe, but would have no idea how to get to the coin battery or the jumpers on a laptop.

And did I hear Wubi??? What's that??? Kidding. Forget Wubi. Long gone and you won't get support for it. Never intended as a permanent solution in the first place, more as a 'Try Ubuntu', which is pointless as you can do that from install media now (even a USB if you could boot one :))

Thought: Know anyone with an external DVD they could bring around? I have a cheap USB one and that works fine. You can install Ubuntu without a USB or DVD, but heck of a learning curve and perhaps MUCH easier to get it happening this way if possible before even glancing there ...

---

### Post by coldraven on 2016-02-20
Options:
1) Somehow reset the BIOS or pay someone to do it.
2) Take out the HDD, borrow a USB DVD drive and see it it defaults to booting from DVD. I'm not sure of next step but something might be possible :(
(maybe hot plug the HDD?)
3) Sell it and buy another netbook that is not password protected. I picked up a mint condition one for about $50. YMMV

---

### Post by grahammechanical on 2016-02-20
My suggestion?

Go to the manufacturer's web site and see if you can download a PDF copy of the motherboard user guide.

The user guide for my motherboard says this:

> If you forget you BIOS password, you can clear it by erasing the CMOS Real Time Clock (RTC) RAM. See section "2.6 Jumpers" for information on how to erase the RTC RAM

Get a copy of the motherboard user guide.

Regards

---

### Post by Bucky Ball on 2016-02-20
> **grahammechanical said:**
> My suggestion?

Go to the manufacturer's web site and see if you can download a PDF copy of the motherboard user guide.

The user guide for my motherboard says this:



Get a copy of the motherboard user guide.

Regards

User on a laptop. As I mentioned previously, don't know how feasible taking out the coin battery or shorting the jumpers is on a laptop. Straightforward on a desktop. You'd need the laptop manual definitely if embarking on it and, depending on the laptop, I'm imagining it would be fairly straightforward or a pain to get to either. Might get lucky, but clearing the CMOS would do the trick. No more password.

---

### Post by Scrollin on 2016-02-21
> **hakuna_matata said:**
> Maybe a solution is to disassemble the laptop for disconnecting the hard disk and connect it as external drive with another computer, then install Ubuntu on this hard disk and finally, assemble and connect it again in the laptop.

Definitely the best solution for me. Thanks to everyone for all the help though. I didn't even thinking about clearing the CMOS at first, but after it was mentioned I did take a look at the internals and immediately noticed that the CMOS was not removable. So basically resetting the BIOS is a no-go, but an inaccessible BIOS is a small price to pay under these circumstances, and I don't care enough to change that. Basically just popped the harddrive out, put it into my desktop and formatted it all. Currently installing from a USB bootdisk as I write this, since I made one yesterday before realizing it wouldn't work.

Luckily I had a spare SATA connector... although for some weird reason my PC would not boot if I had the laptop drive plugged in. Though it booted fine without the laptop drive plugged in, and plugging it while the computer was loaded into the operating system worked fine.

Thanks again guys, hopefully everything will go well with this now.

---

### Post by justen_m on 2016-02-21
Search the web for options aboujt resetting the BIOS. The last computer I worked on, if I pulled a jumper from the MB, it would clear the BIOS password. Another jumper, if connected, would reload the BIOS from ROM on the motherboard.

Yeah, too late to help. Sounds like you've got thing working? Albeit a bit more work than anyone would have liked.

---

