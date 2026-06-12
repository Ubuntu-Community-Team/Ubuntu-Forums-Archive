---
title: "Ubuntu doesn't work with Gigabyte EP45-DQ6 motherboard!"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Gp. on 2010-12-14
Hi all,
I want to start using Ubuntu again but I gave up ages ago trying to get it to work with my Gigabyte EP45-DQ6 motherboard.

I cant run from disc and I can't install.

If I try to run it just takes me to a black screen with blinking cursor and that's all it does.

If I try to install, basically the same.

I can't get anywhere doing anything, so where do I start?

How can I get it working on my system?

By the way, this is with the latest Ubuntu.

No, it's not a corrupt download or burn. I tried to download and burn, didn't work.
I ordered a free cd, it did the same.

This is an issue that is NOT related to the disc or the download of Ubuntu.

---

### Post by oldfred on 2010-12-14
It may not be the motherboard, but there are some BIOS settings that may need to be reviewed.

Most of the issues are related to video issues.

I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

I just saved a list of comment on BIOS issues, review to see if any apply.
Some issues on booting install:
BIOS settings need USB mouse & keyboard
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker

---

### Post by Gp. on 2010-12-17
Hi, thanks for your reply.

I have tried everything for hours on end to get it working and only ONE thing works.

If I disable "Onboard SATA/IDE Device", Ubuntu will boot perfectly normal.

The problem with this is, I have an IDE disc drive I require.

If I disable the Onboard SATA/IDE Device, all my Sata devices still work "Hard drives etc.." but the IDE disc drive is no longer detected because of that option being disabled.

I'm begging for anyone to help me somehow resolve this issue, I REALLY want to be using Ubuntu! :(

---

### Post by Gp. on 2010-12-17
Anyone? :(

---

### Post by oldfred on 2010-12-17
Not familiar with your particular motherboard. My Gigabyte has several settings for sets of ports.

Is there some IDE compatibility setting that by turning off the IDE would do the same thing? Or does the IDE drive have the jumper in the wrong place? Master/Slave or cable select only with newer 80 wire cable?

We have a lot of users with mixed SATA & IDE drives. The biggest issue is usually the IDE drive promotes itself to sda.

---

### Post by cascade9 on 2010-12-18
The PATA ports are run by the 'GIGABYTE2 SATA controller' (I know) and AFAIK its a jmicron controller, possibly with some mods done by gigabyte. 

If there was an intel PATA controller, you wouldnt have any issues, but intel removed the PATA controller on the the P45 chipset (and all since IIRC)

[http://www.intel.com/products/desktop/chipsets/p45/p45-overview.htm](http://www.intel.com/products/desktop/chipsets/p45/p45-overview.htm)

---

### Post by Gp. on 2010-12-19
I'm unable to set any compatibility for IDE.

The drive is set with master/slave jumper pin and it's set correctly.

What else can I do?

---

### Post by CharlesA on 2010-12-19
If the IDE drive isn't even being seen, I'd suggest taking a look at the manual, to make sure the BIOS settings are correct.

You can find it and some other goodies here: [http://gigabyte.com/products/product-page.aspx?pid=2831&dl=1#ov](http://gigabyte.com/products/product-page.aspx?pid=2831&dl=1#ov)

---

### Post by Gp. on 2010-12-19
> **CharlesA said:**
> If the IDE drive isn't even being seen, I'd suggest taking a look at the manual, to make sure the BIOS settings are correct.

You can find it and some other goodies here: [http://gigabyte.com/products/product-page.aspx?pid=2831&dl=1#ov](http://gigabyte.com/products/product-page.aspx?pid=2831&dl=1#ov)

Dude, just thought I'd mention (sorry if I didn't make it clear before), the drive IS SEEN but it's not seen when I disable onboard SATA/IDE device, as I described above.

Pretty much meaning if I want to use Ubuntu I can't use that IDE drive inside of it. There must be a way past this bug/problem.

---

### Post by CharlesA on 2010-12-19
I haven't run into any problems with booting with IDE drives connected, however, it still sounds like a problem in the BIOS - how is it set now?

---

### Post by Gp. on 2010-12-19
> **CharlesA said:**
> I haven't run into any problems with booting with IDE drives connected, however, it still sounds like a problem in the BIOS - how is it set now?

I've made posts a long time ago about this issue and it was pretty much agreed that it's some sort of Kernel bug.

I have tried every single setting in conjunction with every other setting on different bios revisions. I've upgraded bios, downgraded, nothing has made a difference. 

It all comes down to that one setting "Onboard SATA/IDE device" enable or disable. Disabled? Ubuntu works. Enabled? Ubuntu just goes to a black screen with blinking white cursor, and it never goes anywhere else. I've tried different methods of boot from the live cd nomodeset etc.. and none of those have made a difference to the issue.

Now what?

---

### Post by CharlesA on 2010-12-19
> **Gp. said:**
> I've made posts a long time ago about this issue and it was pretty much agreed that it's some sort of Kernel bug.

I found your [other thread]("http://ubuntuforums.org/showthread.php?t=1484513").

Have you already tried resetting the BIOS to factory default?

Could be that Ubuntu just doesn't like your hardware. Just curious, but have you tried booting a Debian livecd?

---

### Post by Gp. on 2010-12-19
lol, you'll have to trust me when I say I've tried everything.

Including yes, BIOS factory reset. It automatically resets to default when you flash anyway.

I also went nuts a while back and tried a heap of other distros. All seemed to have the same or similar issue.

I get that Ubuntu doesn't like my hardware, but why? That's ****. How can I help the revolution if the revolution doesn't let me? lol

---

### Post by CharlesA on 2010-12-19
That's nuts.

Just curious, but does it let you boot into Ubuntu if you disconnect the IDE hard drive (and leaving the IDE port enabled)?

---

### Post by cascade9 on 2010-12-20
Old, but might still be helpful- 

> Annoying thing (filed already a bug upstream) is that ahci driver is a bit confused during boot about disk drives that do not exist. GA-EP45-DQ6 has ICH10R and JMB363. The ahci-driver handles both. But the JMB363 has SiI5723 chips connected to its SATA channels. If a SiI5723 does not have drives connected to it, ahci thinks that the SATA channel on JMB363 is slow to respond and does retry-timeout cycles. I did not test disabling the JMB363 as my PATA DVD is on it too. The cheaper P45 boards do not have SiI5723 chips, so they do not have the issue. Anyway, you do not reboot a server very often, so the annoyance is rare.

[http://www.centos.org/modules/newbb/print.php?form=1&topic_id=15617&forum=37&order=ASC&start=0](http://www.centos.org/modules/newbb/print.php?form=1&topic_id=15617&forum=37&order=ASC&start=0)

Seems like if you hook a SATA drive up one to the GIGABYTE SATA2 ports it migth work. 

If it doesnt...is it really worth the aggravation over a PATA HDD you could probably replace for $50 or less?

---

### Post by Jonners59 on 2010-12-20
Ah hah, dear old Giga...

About 2 years ago when I started to look in to Ubuntu, I kicked off on the server  version, only to stop almost as soon as I started due, mostly to my own inabilities....  I had trumendous issues installing to Giga motherboards.  So I contacted them directly to be told that they do not test to anything but Microsoft, and Linux is of no interest.  I do not recall the exact words, but it was less than flattery.  At the time I reported on the server forum to warn others as the error messages I was getting were quite common.

Maybe of no use and may have changed since, but interesting to me.

PS.  I am mostly Giga boards and I get loads of issues, as OldFred will no doubt testify.

---

### Post by Gp. on 2010-12-20
> **cascade9 said:**
> Old, but might still be helpful- 



[http://www.centos.org/modules/newbb/print.php?form=1&topic_id=15617&forum=37&order=ASC&start=0](http://www.centos.org/modules/newbb/print.php?form=1&topic_id=15617&forum=37&order=ASC&start=0)

Seems like if you hook a SATA drive up one to the GIGABYTE SATA2 ports it migth work. 

If it doesnt...is it really worth the aggravation over a PATA HDD you could probably replace for $50 or less?

The Pata is a DVD drive not a HDD and I could replace it but the last thing I want to do is go and have to replace perfectly working hardware just because Ubuntu doesn't like it, you get me?


Is there anything I can do at all or am I just going to have to deal with no Linux until I buy a new system in a few years.

---

### Post by CharlesA on 2010-12-20
> **Gp. said:**
> The Pata is a DVD drive not a HDD and I could replace it but the last thing I want to do is go and have to replace perfectly working hardware just because Ubuntu doesn't like it, you get me?

If you don't want to replace the problematic hardware, then you'd just have to deal with it. I understand not wanting to replace something that still works fine, but if it's causing a load of frustration, then it would be easier to replace it and save yourself a load of aggravation.

My set up is a little bit different, but the mobo in my server is a [Gigabyte EP45-UD3R]("http://www.gigabyte.com/products/product-page.aspx?pid=3013#sp") (same storage chipset), and it works perfectly, but that may be because I don't have any PATA devices attached to it.

---

### Post by Gp. on 2010-12-20
> **CharlesA said:**
> That's nuts.

Just curious, but does it let you boot into Ubuntu if you disconnect the IDE hard drive (and leaving the IDE port enabled)?

I just tried disconnecting the IDE drive but keeping the option enabled and ubuntu didn't boot. Same problem.

Linux/Ubuntu doesn't like something about this motherboard.

---

### Post by CharlesA on 2010-12-20
> **Gp. said:**
> I just tried disconnecting the IDE drive but keeping the option enabled and ubuntu didn't boot. Same problem.

Linux/Ubuntu doesn't like something about this motherboard.

Well on my system, I have the SATA ports set for ACHI and the SATA/IDE ports disabled, with no PATA devices hooked up.

As you said earlier, it boots fine with the IDE port disabled.

---

### Post by Gp. on 2010-12-20
> **CharlesA said:**
> Well on my system, I have the SATA ports set for ACHI and the SATA/IDE ports disabled, with no PATA devices hooked up.

As you said earlier, it boots fine without the PATA device hooked up.

No lol Perhaps you misunderstood, what I actually said was it boots when I disable that option in the bios. Whether the device is plugged in or not is irrelevant (as per my last post) as the issue is to do with that bios option and ultimately I guess the motherboard.

---

### Post by CharlesA on 2010-12-20
> **Gp. said:**
> No lol Perhaps you misunderstood, what I actually said was it boots when I disable that option in the bios. Whether the device is plugged in or not is irrelevant (as per my last post) as the issue is to do with that bios option and ultimately I guess the motherboard.
Reworded my post. :)

In any case, it's either a BIOS or chipset bug, it seems.

---

### Post by Gp. on 2010-12-20
> **CharlesA said:**
> Reworded my post. :)

In any case, it's either a BIOS or chipset bug, it seems.

Lol :D

Hmm, how do I file this or get around it? I need to know the next step otherwise I give up on all this stuff and maybe I'll try again in the future when I get a new system. This is the last chance Gigabyte gets from me, I've had many a problem with this board not just this. Asus was always good to me :tongue:

---

### Post by CharlesA on 2010-12-20
> **Gp. said:**
> 
Hmm, how do I file this or get around it? I need to know the next step otherwise I give up on all this stuff and maybe I'll try again in the future when I get a new system. This is the last chance Gigabyte gets from me, I've had many a problem with this board not just this. Asus was always good to me :tongue:

I'm not sure how you'd submit a hardware/bios bug, as it would be something the manufacturer would have to fix.

If the work around is getting a new optical drive (and disabled the PATA port), that's probably the easiest way to do it.

If you don't want to do that, then wait until you get a new machine. ;)

---

### Post by cascade9 on 2010-12-21
> **Gp. said:**
> The Pata is a DVD drive not a HDD and I could replace it but the last thing I want to do is go and have to replace perfectly working hardware just because Ubuntu doesn't like it, you get me?

Is there anything I can do at all or am I just going to have to deal with no Linux until I buy a new system in a few years.

I understand the fustration of having to replace working hardware. But its not worth worrying about over $20-25.

BTW, did you actually try what was suggested in the quote I put in my post? (ie, connect a SATA drive to one of the gigabyte SATA2 ports)

---

