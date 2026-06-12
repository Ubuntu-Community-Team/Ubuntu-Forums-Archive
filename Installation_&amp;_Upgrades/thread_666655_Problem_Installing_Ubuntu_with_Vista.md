---
title: "Problem Installing Ubuntu with Vista"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by JCoster on 2008-01-13
Hi there.

I have two discs- one with Vista Home Premium and one with Vista Business (for compatibility reasons which I won't go into...)

Basically, I've been running Gutsy on my Vaio laptop for about a month now and am starting to really into   

I therefore decided to install it over the Vista Business drive from the live CD.

However, after the installation I'm now presented it with the same Windows boot menu as I had previously, asking whether to boot Home Premium or Business.

I assumed that Gutsy installed GRUB and configured it automatically..?

I can't get into either of my vista installs either...

Any ideas?

Cheers.

JC

---

### Post by logos34 on 2008-01-13
Can you post you disk layout?  Boot from the ubuntu live cd (or maybe you're on it) and in a terminal run

sudo fdisk -l

Try [reinstalling Grub to the mbr of your boot disk]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by JCoster on 2008-01-13
Hmm that's interesting.

Running sudo fdisk -l gives me:
'Unable to seek on /dev/sda'

The GRUB fix didn't do anything either...

Cheers.

---

### Post by JCoster on 2008-01-14
Right.

I've decided to pretty much give up trying to sort out my windows install.

But whatever I do I can't seem to get Ubuntu to install.

I've tried installing it on every partition I have but I still get the same old Windows boot loader.

Any advice?  This is really starting to irritate me.

Cheers.

---

### Post by logos34 on 2008-01-14
Next thing to try is [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by JCoster on 2008-01-15
Ok so super grub disk didn't do anything for me.

I tried formatting both hard drives and reinstalling Vista.  That successfully installed and showed up as another option on the boot menu alongside Vista Home Premium and Business.  

So I installed Vista Boot Edit Pro or whatever it's called and removed these entries from the boot list.

Now I could boot straight into Vista without any boot menu.

I shut down Vista and ran the Ubuntu Live CD to install Ubuntu 7.10 on the other hard drive.

It successfully installed but after restart I do not even get a boot menu: just a black screen, and the HUD light on the PC case does nothing- doesn't flash and isn't illuminated and the processor is silent.

So I'm now pretty confused as to what the hell is going on.

I'm starting to think that the two disks may be in a RAID configuration by default...  Would this make a difference?  Is there a way to find out?

Any help is really appreciated here guys...

Cheers.

---

