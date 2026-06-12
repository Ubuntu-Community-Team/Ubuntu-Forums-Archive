---
title: "Installation failures, USB and hard drive"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by tege on 2007-03-13
I have made my 3rd attempt at installing Ubuntu, this time waiting got things to mature about one year.  My main purpose of this last attempt was to get a USB-flash based system working.  I chose Ubuntu since it was suppose to "actually work".

Unfortunately, on my Athlon64 system, the i386 6.10 install hangs, semi-reproducibly.  On the USB stick, it hung after about 1 hour, with 62% done.  The last 50 minutes saw a progress from 61% to 62%.  This hour the USB stick was being written to intensively.  (It was in fact apparently killed by this, with too many writes to the same place.)

I then tried installing to the hard drive.  Twice.  The first attempt hung after 50%.  Error messages started scrolling on a tty (Ctrl-Alt-F2) but the install screen was simply locked.  These errors told me that hdc couldn't be accessed.

The 2nd time, the installation worked much better.  :-)  It hung after a whole 65%.  Then things slowed down, with the load again going up with no limit.  The last load value I saw was load 37.

The hardware does not seem to have any problems with other systems.  The system runs FreeBSD without a hitch.  I also had a CentOS 4.3 system running on it until yesterday.  To be sure the hardware is OK, I reinstalled CentOS after the Ubuntu failures.

Is this the maturity level to expect from Ubuntu, or could I expect it to install on a modern PC?  There seem to be a lot of untold knowledge in the Linux community, about what things are broken, and how to work around them.  Perhaps nobody uses the GUI install, but circumvents it somehow. and instead uses an install that really works.

PS. Please don't lecture me about not running a i386 system on a 64-bit system. I do that piece of sillyness quite intensionally.

Torbjorn

---

### Post by tcpip4lyfe on 2007-03-13
Im not sure I understand your question correctly.  I use ubuntu on a 64bit system in 32 bit mode and I had no problems installing it.  I would try removing the USB stick when you are trying to installing ubuntu to your main hard drive.  Hopefully it will install correctly then.  Once you get ubuntu installed and updated you should just be able to plug in the stick and an icon will pop up on your desktop.  If it doesn't, plug in your stick and open a console and:

dmesg | tail

To show you what /dev the stick is using.  Then:

mkdir /mnt/pen
mount -t (file system type: ex. ext3 or ntfs) /dev/sd# /mnt/pen

Where # is the sd device picked up in dmesg (ex. /dev/sda1)

---

### Post by tege on 2007-03-13
I did remove my USB stick attempting to install to the hard drive.  (It was actually killed by then.)

Did you actually use the install CD, and the graphical install?

---

### Post by dannyboy79 on 2007-03-13
i would suggest using the alternate install cd, it's text based. also, try to add possible boot options to your kernel line, like noapci or apic = no . or do I have these backward? these are boot options that will sometimes help freezing startups and the alt install cd will usually help installers that keep crashing before it's done. good luck

---

### Post by tege on 2007-03-13
The "alternate" install iso seemed better, but it too, fails.

The "Select and Install" step failed after about 15 minutes.   With Alt-F4 I switch to a console with some more detailed error messages, but the start of it has scrolled off the top.

This is utterly frustrating.  (1) No installation instruction can be found at the Ubuntu site. (2) The installs leave basically no choices (so I guess install instructions might not be needed...).  (3) In spite of this lack of possibilities that could cause problems, it fails in very basic ways.  (4) It doesn't present the actual error to the user, so it cannot be properly reported and fixed.

Torbjorn

---

### Post by dannyboy79 on 2007-03-13
what are your hardware specs? can you boot to a live cd. if so, then do a lspci -v and note down all your hardware and post it back. there already be a bug report for this. what version are you trying to install?

what about trying the server install and then installing your window manager afterwards?

---

### Post by tege on 2007-03-13
It is a very plain system, without more hardware then needed for basic hacking tasks.

mbd: Gigabyte GA-K8NF-9 (Nvidia chips, including built-in ethernet)
cpu: AMD Athlon 64 3500+
disk: some sata disk of 80 GB 
CD: NEC ND-3550A CD-RW DVD-RW IDE (strapped to "master")
frame buffer: Unknown brand, circuit is ATI radeon X300, PCIe
No other PCI or PCIe cards or other hardware attached.

I decided to ignore the installation error, and the installation program was completely happy to let me do that.  So I installed a grub boot loader, and rebooted.  The system seems to work, although it is barely useful, without any compiler, make, linker, etc, etc.  I know how to fix that!

(I tried to attach lspci output, but I cannot get attachments to work on this forum.  (Or perhaps I have attached it five times, but I just don't see them.)

---

### Post by dannyboy79 on 2007-03-13
well this is silly, what error was it the whole time. you made it sound like the installers were failing to even work or that they froze. so which installer finally worked and what was the error so others can get by this issue as well. glad to see that you're good to go now!

---

### Post by tege on 2007-03-13
Yes, "I made it sound" like they failed, and my first post explains how they failed.  They indeed froze, twice with load skyrocketing, the other time with a slowly scrolling screen of errors.

Your advice about using the "alternative" iso image helped, since that installer didn't freeze, it failed without really saying what failed.  But since the systems still responded, and since the installer actually allowed me to ignore the failure, I could finish up the incomplete installation.

I wouldn't say that the last "installer finally worked", to use your words.  That is a bit too generous.  Does a car work if it needs to be pushed in order to get anywhere?  :-)

I am very grateful for your help.  I wish I can somehow help somebody that wish to fix the installers, but since the installers keep us in the dark of where they were, and what was the actually failing operations, it seems difficult to supply useful information to the developers.

I am a GNU hacker since long, but a FreeBSD user.  It is a pity that the GNU/Linux distributions are still so immature, when it comes to robustness.

---

### Post by dannyboy79 on 2007-03-13
> **tege said:**
>  it failed without really saying what failed.  But since the systems still responded, and since the installer actually allowed me to ignore the failure, I could finish up the incomplete installation.
what actually occured to make you believe that the installer "failed"? after the installer finishes, it asks that you remove the cd and then hit return and it will restart and boot into your new install, when you say the installer allowed you to ignore the failure, again can you explain this? If it's incomplete, than that is surely something you can inform the developers of isn't it? If you're simply saying that a compiler and other dev tools weren't included by default than I have to inform you that this isn't a failure, this is the default. i am not saying is a good thing, I am merely saying that ubuntu doesn't have the build-essential package installed by default and this is not a failure. otherwise, whatever was missing should be documented into a bug if these packages were specifically suppose to be in the ubuntu install. i am glad you got it working.

---

