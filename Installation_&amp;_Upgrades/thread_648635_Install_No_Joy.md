---
title: "Install No Joy"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by carnut on 2007-12-23
This is crazy.  I decided to try Ubuntu on some of my boxes running Solaris and Windows.  Three boxes later and still not a single working copy of Ubuntu.  Two systems drop to bash while another fails to boot after loading.

I've gone through every boot tweak I could find with no luck, and my hardware's typical IBM/Dell gear.  I'm glad I didn't risk my one SUSE box.  Ubuntu seems to look good from the screen captures, but who wants to spend hours and hours tying to get it to boot?

What gives with the install issues?  I found several posts with the same general symptoms using the 7.x Live CD.

---

### Post by PmDematagoda on 2007-12-23
What is the VGA card you have?

---

### Post by bluetick on 2007-12-23
When I did the install, I got an error that I didn't have permissions to a config file in my home directory. I logged in as root at that bash prompt, did a chown, and all was joyous. 

Sound anything like what you got? I'm hazy on the details now, but it's probably enough to go on. 

Tick

---

### Post by carnut on 2007-12-23
> **PmDematagoda said:**
> What is the VGA card you have?The One IBM has the planar video (on-board) S3.  The other IBM has a four head Color Graphics card (not sure of model), and the dell has an ATI Radeon 9600.  None are amazing boxes, they were serving up CDs & DVDs.  I bought a ReadyNAS server, so the old boxes are ready for distro hell.

---

### Post by carnut on 2007-12-23
> **bluetick said:**
> When I did the install, I got an error that I didn't have permissions to a config file in my home directory. I logged in as root at that bash prompt, did a chown, and all was joyous. 

Sound anything like what you got? I'm hazy on the details now, but it's probably enough to go on. 

Tick
No, I have full rights.  It has to be something with the hardware.  I select install and it drops to bash saying it can't mount the CD/filesystem.  One post said to force the root to the CD, but that didn't help.  I also tried an IDE workaround posted for an install issue that matched mine exactly, still no.

Ahh maybe it's time to try newer hardware.  I'm just shocked that Server 2003 and Solaris 10 ran fine on the boxes but not Ubuntu.

---

### Post by tgalati4 on 2007-12-23
Did your run the Check CD and compare the checksums?  Perhaps you have a bad install disk.  Did you burn it at 4X or was it a commercially-pressed disk?

---

### Post by carnut on 2007-12-23
> **tgalati4 said:**
> Did your run the Check CD and compare the checksums?  Perhaps you have a bad install disk.  Did you burn it at 4X or was it a commercially-pressed disk?I downloaded and burned the image twice, and it's the same drive I burned the Solaris I've just finished reloading.

After the two copies failed, I ran the 'Check CD' option, but even then the CD could not be found (identical to the install issue).  From bash I can see and list the CD's contents, but the installer can't find it.

---

### Post by Partyboi2 on 2007-12-24
Have you tried installing using the alternate cd?
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by carnut on 2007-12-24
> **Partyboi2 said:**
> Have you tried installing using the alternate cd?
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)No I did not.  I saw that brought up while looking for a resolution to my problem, but I don't understand its usage besides it being text based.  I'll sure give it a shot.  After install do you still end up with the same Ubuntu features?

Thanks...

---

### Post by carnut on 2007-12-24
Before trying a new CD, I yanked a newer box.  The install went fine.  For the fun of it, I also ran the DreamLinux Live CD.  Wow wow wow, is that thing amazing.

Anyway, maybe I'll try to get U up on another box or just pass for now.  It's hard to justify the time when it's just for fun, and I have development projects out the but to finish.

Still, an install should install or tell you why it fails.  If we've gone full circle back to the days of the first SlackWare releases, god save us all - lol.

---

### Post by tgalati4 on 2007-12-24
The standard Ubuntu Live CD needs 256 MB of RAM (or 128 MB + 128 MB of swap) to run properly.  Anything less is painful or it will just hang.  I think the Alternate Installer disk runs in 128 MB of RAM and tends to work better with older hardware.  

Yes, you get the same resulting Ubuntu with either installation method.

---

### Post by carnut on 2007-12-24
> **tgalati4 said:**
> The standard Ubuntu Live CD needs 256 MB of RAM (or 128 MB + 128 MB of swap) to run properly.  Anything less is painful or it will just hang.  I think the Alternate Installer disk runs in 128 MB of RAM and tends to work better with older hardware.  

Yes, you get the same resulting Ubuntu with either installation method.Thanks for the reply.  Even my oldest machines have 1GB or better, but by using a slightly newer machine, I was in business.  After the initial updates Compiz was broken, but I found the answer on the forum (guess every answer is here if you look - lol).

I can't believe the speed of the GUI.  Even with every feature enabled, it smokes.  Also, the group doing the compiz stuff do kick but work; and, whoever wrote the compiz-settings utility saved me tons of time with all the settings.

Now I'll get a good C++ environment up and I'll be golden.

A thank you to all for the help.

---

