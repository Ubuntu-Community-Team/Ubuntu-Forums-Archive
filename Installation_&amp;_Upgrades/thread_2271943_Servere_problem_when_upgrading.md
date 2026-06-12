---
title: "Servere problem when upgrading"
date: 2015-04-02
forum: Installation &amp; Upgrades
---

### Post by mateojonsonguynn on 2015-04-02
Hey everybody,
I have been using Ubuntu for a while now (over a half a year) on two computers. On one of them, my desktop, a message recently popped up saying something about how I could perform a partial update. I thought it was referring to my installed software, not Ubuntu itself! I accepted and typed in my password. All of a sudden, I realized that meant a partial update from Ubuntu 14.04 Trusty Tahr to 14.10 Utopic Unicorn. Since it said "partial", I was immediately worried. It only got worse when I saw that every file that looked like it was part of the kernal (linuximage) couldn't install. It said something about grub and gave me the message:

error: Cannot read/write '/dev/sda': Input/output error

Or something along those lines, even though I think that was exactly what it said.
Everything else, including libraries, seemed to install fine.
I was then asked to reboot. I did so. The first thing I was was Ubuntu 14.04. Wait- shouldn't that be 14.10? Then there was a message saying, "System Program Problem detected". I dismissed this because I got this message on startup before I upgraded. I was then just greeted by a black screen for about 15 minutes. All of a sudden the desktop appeared, but it was extremely glitched. And laggy. I had to wait 2 minutes before my click on the wifi bar registered. (I just did that as a test, no problem with my wifi.) The only thing that worked was my mouse, and even that glitched when I clicked. I tried restarting lightdm but it crashed the computer, as far as I can tell. (Yes, I know lightdm is the display manager, but I mean I waited 15 minutes after it stopped and nothing had changed.) I tried restarting my computer. I was greeted by the same System Program Problem message and my mouse. I dismissed the message, but this time, the desktop didn't show up. I've kept it running for about 10 minutes and as of right now, as I am writing this message, the desktop still hasn't appeared.

Just so you know, here is some background on my computer.
I had it in storage for a few years. When I took it out again, the hard drive was fried. by a miracle, I was able to get Windows running on the fried drive, but every time i didn't use the computer for more than a week the drive would fry itself again. I reinstalled Windows twice after that, and then tried Ubuntu. I am happy to say it worked like a charm and I have not had a problem with it for over 1/4 of a year. Until now. **TL;DR The hard drive is fried but it still works fine- but only when I use Linux.**
I recently, not liking Linux's appearance, installed two themes and one icon pack using Noobslab and Unity Tweak Tool. They were the 14.04 version, and I didn't disable them before restarting. [B]TL;DR 2 Themes and an icon pack from 14.04 are being used.

[/B]
Can anyone help?

P.S. Wiping my drive and reinstalling is _NOT_ an option. (Unless you guys can tell me how to safely backup it.)

[B][I][U][SIZE=5]THIS THREAD IS NOW MARKED SOLVED. THANK YOU FORUMS!
[/SIZE][/U][/I][/B][I][SIZE=5][SIZE=2]
[/SIZE][/SIZE][/I]

---

### Post by mateojonsonguynn on 2015-04-03
Bump.

---

### Post by Impavidus on 2015-04-03
Partial upgrades refer to your installed software, not to the Ubuntu release. They happen when there are updates available, but not all of them can be installed because some dependencies of the new package versions are still missing. It happens because of server glitches and PPAs. Best is to find out why you can only do a partial upgrade. If you use the official repos or well-maintained PPAs, you can usually do a complete upgrade within days.

An input/output error on /dev/sda refers to some kind of low level error, usually hardware, like a broken hard drive or a loose connector. So that's consistent with your fried hard drive. Linux uses drive space in a different manner than Windows. Maybe Windows always tried using the fried part of the drive within a week, but Linux only tried so after three months.

In any case, there is no software way to fix a broken drive, so better get a new one. And try to rescue any important files still present on the drive,

---

### Post by mateojonsonguynn on 2015-04-03
Thanks, but I have a question-
I tried to copy the files from the drive to another drive using an Ubuntu LiveUSB. I had transferred about 7/8ths of the files, but then I got a kernel panic and the computer crashed. I tried restarting but I cannot mount the other drive- even using a force mount as root. Any ideas?
I already copied most of my personal files so I don't need to copy more files.

Additional info (about the original drive, not the one referred to as "the other drive"):
I can get the Ubuntu Desktop at will, but it is still slow as ****--- to the point it is still unusable. I fixed the icon glitch, though.
I booted it in text console mode and it works perfectly.
It is not a hardware compatibility issue with 14.10- I booted it off a LiveUSB and it runs fine.

---

### Post by d-cosner on 2015-04-03
I experienced similar problems myself today trying to use some old hard drives to get another system going. You might be able to recover more data by letting the drive cool off. It's time to replace the drive though...

---

### Post by mateojonsonguynn on 2015-04-03
I don't have the money to replace the drive.
Also, I know that only 6 blocks on the disk are corrupted, so i think I can work around them for the time being.
I just need to know why my backup disk won't mount.

EDIT: Should I start a new thread?

---

### Post by mateojonsonguynn on 2015-04-03
Ok, I fixed the unmountable other drive. (thank god for ntfs-3g!)
I also fixed my hard drive (a fsck and badsectors check showed that it was not fried, it** only** had *40* bad sectors... heh heh heh... [SIZE=1]i need a new hard drive[/SIZE])
I am marking this as solved.

---

