---
title: "Difference between a wubi and normal installation"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by GaryTheCat on 2010-08-10
I installed lucid using wubi to dual boot with vista - I'm just wondering if there's any advantage to be gained into going back into vista, un installing lucid, making the necessary partitions and reinstalling lucid 'properly'.

I use both OSs on a laptop so the power issue regarding fs vulnerability isn't that much of a concern.

Any views appreciated.

TIA

G

---

### Post by bcbc on 2010-08-10
> **GaryTheCat said:**
> I installed lucid using wubi to dual boot with vista - I'm just wondering if there's any advantage to be gained into going back into vista, un installing lucid, making the necessary partitions and reinstalling lucid 'properly'.

I use both OSs on a laptop so the power issue regarding fs vulnerability isn't that much of a concern.

Any views appreciated.

TIA

G
Wubi installs aren't just vulnerable to power failures. Any hard shutdown can result in corruption of the root disk. It is important to [avoid this if at all possible]("https://wiki.ubuntu.com/WubiGuide#How to reboot cleanly even when the keyboard/mouse are frozen").
The performance should also be faster on a direct install (although I haven't noticed a huge difference myself).
You can hibernate a direct install assuming you have the correct swap partition set up.
You're more likely to get expert help on a direct install, since wubi isn't used as much by longterm ubuntu users and many are unfamiliar with how it works. 

The benefits of wubi is that you don't have to worry about partitioning, so it's convenient for users that aren't comfortable doing this.
You can use it even if you've already used up four primary partitions on your drive.
It's pretty much a no-brainer to install (for most people it's smooth sailing, although you do see many people who have issues on the forums).

Generally, most people reckon wubi is a good way to figure out if you like ubuntu. One you've made up your mind, it's a good idea to install direct to partition (or [migrate your wubi]("http://ubuntuforums.org/showthread.php?t=1519354")). But there's no real rush - just backup important data (as you should anyway).

PS sometimes wubi is affected more when there are system updates and release upgrades. lately it's been impacted by grub, although this is getting better. Make sure you don't install the grub bootloader when you're using wubi and you'll be OK (the updates can be confusing sometimes).

---

### Post by GaryTheCat on 2010-08-11
Thanks for that - I do like ubuntu so I'm going to do a 'proper' installation and remove the wubi one.

Would vista and ubuntu need to be on the same physical harddrive?

Keep watching for posts saying I've trashed something lol

---

### Post by bcbc on 2010-08-11
> **GaryTheCat said:**
> Thanks for that - I do like ubuntu so I'm going to do a 'proper' installation and remove the wubi one.

Would vista and ubuntu need to be on the same physical harddrive?

Keep watching for posts saying I've trashed something lol

They don't have to be on the same harddrive. But take care where you put your grub bootloader, if you have more than one drive.

---

### Post by GaryTheCat on 2010-08-11
I think I've done a proper install of lucid (I had to because I'd managed to delete part of the FS when I was in vista).

I didn't run wubi in windows but booted from the live cd and installed like that.

In very simple terms, is what I have now a wubi installation or not?

---

### Post by bcbc on 2010-08-11
> **GaryTheCat said:**
> I think I've done a proper install of lucid (I had to because I'd managed to delete part of the FS when I was in vista).

I didn't run wubi in windows but booted from the live cd and installed like that.

In very simple terms, is what I have now a wubi installation or not?

It's not wubi.
(Wubi stands for windows-based ubuntu installer - you install it while running windows. It's harder to tell when you are booting the wubi ubuntu as essentially it looks identical, but you can check easily as the wubi-installed ubuntu runs off a virtual disk, so the /etc/fstab file references "/ubuntu/disks/root.disk" and you won't see this in a regular install).

---

### Post by TBABill on 2010-08-11
Now that you have a full install you can even keep Windows on its separate partition, but also run Virtualbox and run Windows "inside" of Ubuntu, much like you did with Ubuntu and Wubi. That way you can do all your Windows things with proprietary software if you have certain apps or programs you like to use and want to keep your Windows capability. And you can do so without a reboot to switch between Ubuntu and Windows.

---

### Post by navaneethan on 2010-08-11
Just wubi makes the job easy to you but it takes the problem,Normal installation makes the job hard and the system will be easy

---

### Post by bcbc on 2010-08-11
> **TBABill said:**
> Now that you have a full install you can even keep Windows on its separate partition, but also run Virtualbox and run Windows "inside" of Ubuntu, much like you did with Ubuntu and Wubi. That way you can do all your Windows things with proprietary software if you have certain apps or programs you like to use and want to keep your Windows capability. And you can do so without a reboot to switch between Ubuntu and Windows.

Just a minor correction :) Wubi is not like a virtual machine. As per the [faq]("http://wubi-installer.org/faq.php#internals")
> Is this running Ubuntu within a virtual environment or something similar?
No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition.

In fact after installing using wubi, you could boot ubuntu from the root.disk even without windows being present. (Not much point in doing this, but it's possible). 
You can even migrate a wubi install to a direct partition install using just a live CD and a root.disk (again not likely everyone's cup of tea).

---

### Post by oldefoxx on 2010-08-11
That is a proper correction regarding Wubi, but I've only done it once that way myself.  I could not see any inherent advantage in doing so, and in fact loss a few incidentals along the way, so I won't be doing it that way again.

The LiveCD method outdoes the Windows approach just by being able to load and run off a CD or DVD drive. If you don't have such a drive, then Wubi might make some sort of sense, but CD/DVD are almost indispensable unless you have found a way to manage by using a thumbdrive. With Windpws, it takes something like a Bart PE build using an XP install disk with at least SP2 added to get it up off a CD boot, and as incredible an effort as that was, there is very little that you can do at that point, whereas a LInux LiveCD is almost the whole monte just on its own.  I mean no real basis of comparison between them, and that is with any distro of Linux.

I would say with an almost certainty that the normal method really is quite superior.  There is always room for disagreement, or some circumstance that suggests going the other way, but in my book, LiveCD is way ahead.  The trial mode can even be used to make special provisions before or after the actual install, and that might be important once you really understand what is involved.  

Some would maintain the opposite is true, which is their right, just like the right to decide whom to vote for. The fact that they got even that wrong should tell you something, but it's not like them to ever own up to a bad decision, and they may even convince themselves otherwise by accepting excuses and efforts to pass blame on to parties long gone from the process and not there to respond.

But I won't go any farther than that in expressing myself.  It is, after all, just a general observation about man's nature that can be recognized and applies in all manner of circumstances.  It can help to know and recognize it when present, not that doing so really changes anything.  Bad decisions remain bad decisions and that alone remains a fact.  The only real advantage in knowing who was at fault is to prevent that from being a source of further bad decisions.  But unfortunately, life's comedy of errors shows we live with errors and accept bad decisions as a lifestyle to live by. You have to go beyond this life to find anything truly better.

---

### Post by GaryTheCat on 2010-08-12
Thank you so much for your guidance on this folks - all sorted :D

---

