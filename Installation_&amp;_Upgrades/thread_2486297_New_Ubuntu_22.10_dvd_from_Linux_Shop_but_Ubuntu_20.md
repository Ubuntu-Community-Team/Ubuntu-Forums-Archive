---
title: "New Ubuntu 22.10 dvd from Linux Shop but Ubuntu 20.10 doesn't see it?"
date: 2023-04-25
forum: Installation &amp; Upgrades
---

### Post by cheapodonuts on 2023-04-25
Literally as per title. I need to upgrade via dvd but nothing shows when I insert the disc. :(
 I know the dvd player works as I'm just watching Cannonball Run 2!
Thanks in advance for any assistance you guys! :D

---

### Post by ne29914 on 2023-04-25
You need to boot from the DVD. Apart from that: "Linux Shop"? Sounds fishy. You'd be better off downloading from ubuntu.com.

---

### Post by cheapodonuts on 2023-04-25
Ah, thanx for reminding me, I'd forgotten about booting, yes I'll have to change the startup to boot from the dvd.
 But Linux Shop have been around for ages. They have a huge number of distros on offer, on dvd and usb sticks. 
[https://thelinuxshop.co.uk](https://thelinuxshop.co.uk)

 As per my signature, I'm a permanent noob! &#55357;&#56833;

---

### Post by ne29914 on 2023-04-25
So why would you pay for something that's free to download (and always the latest version)?

---

### Post by cheapodonuts on 2023-04-26
I always used to download it, but I've realized in recent years that I lose my temper so quickly with things because of my severe tinnitus. It also screws up me trying to remember stuff. So I began using Linux Shop a few years ago as they aren't expensive.

---

### Post by Impavidus on 2023-04-27
22.10 only has 3 months of support left. Better use 23.04, the latest release, with 9 months of support left, or 22.04, the latest LTS release, with 4 years of standard support left.

BTW, 20.10 reached end of life 21 months ago.

---

### Post by guiverc on 2023-04-27
I would avoid using *optical* media on releases beyond 20.04.

Changes were made in 20.10 with the boot process, plus the media is scanned automatically to check for *checksum* errors, which is fine with *flash* media, but can take a *long* time on *optical* media. Depending on your hardware, the boot process can take up to 13 minutes, and installs >60 minutes, which is a long time without any visual clues appearing on screen (*the same install using flash media can take 1-3 mins & <8 minutes respectively where its far less of a problem*). USB *flash* drives are expected install media from 20.10 & later.  Yes *optical* media can still be used; but its slow & more problematic on some *older* hardware.

---

### Post by ne29914 on 2023-04-28
Corrupted post. Dunno what happened.

---

### Post by ne29914 on 2023-04-28
> **guiverc said:**
> I would avoid using *optical* media on releases beyond 20.04.

Changes were made in 20.10 with the boot process, plus the media is scanned automatically to check for *checksum* errors, which is fine with *flash* media, but can take a *long* time on *optical* media. Depending on your hardware, the boot process can take up to 13 minutes, and installs >60 minutes, which is a long time without any visual clues appearing on screen (*the same install using flash media can take 1-3 mins & <8 minutes respectively where its far less of a problem*). USB *flash* drives are expected install media from 20.10 & later.  Yes *optical* media can still be used; but its slow & more problematic on some *older* hardware.

I agree that thumb-drive boots/installs are ~4x faster than from a DVD. But from there our experiences diverge.
The latest functioning USB thumb drive I have is 20.04.1.
20.04.2...20.04.5 and 22.04 will NOT boot/install from a thumb drive.
But all mentioned versions WILL boot/install from a DVD without exception

Additionally, the DVD gives me audible feedback. If it spins up and starts clicking, "we have liftoff". If not, try again.
The thumb drive gives me no feedback at all.
So the options are:
1: live with a 4,,,5 min. live boot time (DVD).
2: look at a black screen for eternity (USB).

---

### Post by guiverc on 2023-04-28
> **ne29914 said:**
> I agree that thumb-drive boots/installs are ~4x faster than from a DVD. But from there our experiences diverge.
The latest functioning USB thumb drive I have is 20.04.1.
20.04.2...20.04.5 and 22.04 will NOT boot/install from a thumb drive.
But all mentioned versions WILL boot/install from a DVD without exception

Additionally, the DVD gives me audible feedback. If it spins up and starts clicking, "we have liftoff". If not, try again.
The thumb drive gives me no feedback at all.
So the options are:
1: live with a 4,,,5 min. live boot time (DVD).
2: look at a black screen for eternity (USB).

I am aware of some issues with firmware and booting live media (esp. 20.10 & later) on some devices, for a number of reasons.

I wrote about it here for Lubuntu - [https://discourse.lubuntu.me/t/slow-boot-times-of-lubuntu-22-04-lts-on-some-hardware/3280](https://discourse.lubuntu.me/t/slow-boot-times-of-lubuntu-22-04-lts-on-some-hardware/3280) as a means of documentation given the numerous issues I'd seen on support sites etc, and wanted something to point users to.

If you scan my linked example of a motion computing j3400, that box takes >11 minutes to boot a Ubuntu ISO of 22.04 for example; not mentioned in that post as that was on a Lubuntu web site, so I limited myself to talking about Lubuntu. If you scroll down, you'll note your ~5 min boot from DVD is also faster than a different Lenovo g560 box too from thumb-drive; and YES the modern thumb-drives usually don't give feedback, unless using some older thumb-drives that provide feedback via flashing-LED.

I'm involved with QA, though I don't do anywhere near as much as I did in the past, as I see less need (Lubuntu especially) & am spending my time on other Ubuntu tasks. I'm recorded as completing 90 lunar tests for example, though that number is far higher if you go back numerous releases (esp. before jammy).  As I perform that QA on about 25 boxes (with more hardware when I get access to them) I've seen a bit.

I have two boxes that Ubuntu is actually carrying patches to allow them to boot in fact (old HP hardware with unfixed firmware bugs); those patches alas have caused issues with newer uEFI hardware and as such I've been warned they risk being dropped.  There is much detail on slow booting in various bug reports, including loads of timing (my lubuntu post examples were just copied from bug & QA reports). FYI: We ensured we have a means to document how to boot the *old HP boxes* if/when the mentioned patches get dropped.

What I found interesting in the extra detail about releases you mentioned was the different stacks on what worked & what didn't

- Ubuntu 20.04 & 20.04.1 media used the 5.4 kernel & GA stack (post-install it would upgrade; Ubuntu Desktop defaulting to HWE, Ubuntu Server + Lubuntu/Xubuntu using GA) etc.

- All Ubuntu 20.04.2 & later media with desktop (Ubuntu Desktop and all *flavors*) used HWE thus for 20.04.2 that was the 5.8 kernel, 20.04.3 used the 5.11 kernel etc...  Only Ubuntu 20.04.2 server still used the GA kernel stack (5.4)..

I can't see how that would impact boot though, though of course there are other differences in the updated package beyond *kernel stack*, but most changes in ISO builds occur only between releases (*with 20.10 & later differing the most to earlier releases* *as effort is now made so all architectures boot the same for a given release; something that was optional for 20.04 & earlier*)

---

### Post by ne29914 on 2023-04-29
It could also have something to do with how my boot media was created. I don't remember how the 20.04.1 stick was done, but all subsequent ones were made using the default  "Startup Disk Creator".
The DVDs were made with "K3b" and all work. Same .ISOs for both media.

EDIT: just tried again. The thumb drive actually boots, but after the "Start Lubuntu" screen hangs. That's it. Dead.

---

### Post by ne29914 on 2023-04-30
Tried again using:
```
sudo dd bs=4M if=$HOME/Downloads/lubuntu-20.04.5-desktop-amd64.iso of=/dev/sdb conv=fdatasync status=progress
```
To create the USB thumb drive. Same result, the "Start Lubuntu" window is the BSOD.

Why do I get the feeling that there are developers "improving" things that worked perfectly before without reason? "If it ain't broke, don't fix it."

And yes, I'm a complainer. That's because I like Lubuntu and would like to keep working with it. And I'm asking for improvements/solutions.
Should silence descend, you've lost a user...

---

### Post by guiverc on 2023-04-30
[Updated 20.04.6 media is available]("https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/"), but isn't available for all *flavors* which includes Lubuntu.

As [Lubuntu 20.04 LTS is now *end of life*]("https://discourse.lubuntu.me/t/lubuntu-20-04-lts-is-end-of-life/4190"), it's *unsupported* as are all 20.04 *flavors*. The Lubuntu team decided it was unhelpful to update 20.04 media given it only had mere weeks left of supported life.

Your details as I've tried to indicate remind me of [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342) and like issues, where its just *slow* to boot & bugs are filed that it fails to boot; primarily as you make statements without the details that are essential (eg. timing). There are many such reports/bugs related to booting of media due to issues with boxes firmware. Ubuntu carries patches that help some boxes where bugs were filed by users of those machines, alas those patches can impair different boxes with different firmware.. with focus being given to the bugs reported whilst a release is in development.

I won't help any longer with  20.04 as it's EOL unless you're using Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, or Ubuntu Base which come with 5 years of *supported* life. They do have 20.04.6 media available. Ubuntu 20.04.6 media was required due to older media no longer being *bootable/installable* due to Secure-uEFI changes and *revoked *keys, but I suspect this isn't your issue - as that should impact DVD boots/installs equally.

There were changes on bootable media post 20.04 as Ubuntu is created for multiple architectures, and now effort is made to ensure all architectures boot the same regardless of you using *riscv64, arm64, armhf, amd64, ppc64el, s390x *etc.. ie. no specific instructions are required for your architecture; if you're using 22.04 LTS you do the same regardless on your *arm64* box as you do on your *riscv64* or *amd64* hardware. For those in corporate environments or anyone maintaining multiple architectures (*even those at home with amd64 PCs & some raspberry pis etc*) this is of huge benefit.

Lubuntu is an official Ubuntu *flavor*, thus our ISOs are created the same was as Ubuntu ISOs, using the same procedures on the same infrastructure, the only difference is we use different *seed* files (eg. [*lubuntu lunar*]("https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.lunar/desktop")) resulting in the different *flavor* on boot and different set of packages being installed.

---

### Post by ne29914 on 2023-05-01
Thanks.
I understand your point and accept it.
Concerning waiting on the "Start Lubuntu" blue screen: I admit I broke it off after half an hour. I couls have done 5 DVD live boots in that time. And waiting longer seemed pointless.
Like I said, 20.04.2 and onwards will not boot, but I can live with DVD boots instead.

---

