---
title: "Dual booting ubuntu/win7 opinions"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by Jobbo256 on 2012-07-16
This thread doesn't have any problem questions or anything, I just need to know if this is a good idea or not. I have windows 7 on my laptop(for gaming, not really much else) and I recently dual booted it with the windows 8 preview just to test it out. But Microsoft, the geniuses they are, decided it would be best if windows 8 was set as the default operating system after installation, which conflicted with some previous modifications I had made with win7 and thus made win7 unbootable. I am thinking about wiping the windows 8 partition and installing Ubuntu 10.10 on it, because I just find Linux so much easier and less frustrating than windows. I'm choosing ubuntu because I really don't have the time for slackware, and I'm thinking about copying all my personal files from my win7 partition to the ubuntu one(while expanding the Ubuntu partition in the process) and just make it the only partition on my computer. Does this sound like a good idea to you guys, or should I just keep searching for ways to make windows 7 boot again?

---

### Post by darkod on 2012-07-16
There is nothing bad with the idea to use ubuntu as dual boot or as single OS. The end decision is up to you of course.

I would only recommend not to use 10.10 (it's already out of support) and instead try the latest 12.04 LTS.

The LTS means Long Term Support which in numbers means 5 years. So, you're good until April 2017. :)

---

### Post by drmrgd on 2012-07-16
That is almost exactly what I'm doing currently as well (although with Windows XP and Kubuntu).  I'm getting the parts for a new custom build this week, though, and will be upgrading my dual boot to Windows 7.  Just like you, I still need a stable gaming platform, and dual-booting Windows and Ubuntu covers everything very nicely!

---

### Post by Laiquendi on 2012-07-16
Same for me, Ubuntu 12.04 and Win7, works perfectly unless you want to look into ext4 from Windows ;)

---

### Post by TheFu on 2012-07-16
The main things I would recommend beyond what the other replies say is to put as much storage into logical partitions as possible.  Primary partitions are limited to 4 per HDD, but there is no real practical limit on the number of logical partitions a HDD can have.

I often will install 5+ different OSes on a single eSATA dock connected HDD inside a 10G partition for each.  My main desktop is only 13GB - though I keep all large data files on a different partition or on a network server.

Using eSATA means performance from that device is just as fast as with internal SATA HDDs, since it is a dock, swapping HDDs is trivial, and since most HDDs here are 500GB or larger, having 50 OSes isn't too difficult, though having so many does raise other challenges.  Most of the time, using KVM to virtualize an OS is more convenient, but for trying out desktops with graphics acceleration requirements demands a full boot test.

Partition management is a lost art and Microsoft isn't making it any easier with their upcoming UEFI mandate.

---

### Post by Frogs Hair on 2012-07-16
I need Win 7 for gaming and school at present . Dual booting was a breeze for me because I built my desktop computer and didn't have deal with OEM partitions which can make installation more difficult. 10.10 is no longer supported so you may want chose a supported release. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by bobmct on 2012-07-16
I used to use dual boot but for the past year I've simply installed ubuntu and then virtualbox (which allows the installation and running of one or more virtual machines).  I then created a new install within virtualbox of Windows 7 Enterprise and I can run them both concurrently.  Windows-only progs in the Windows window and *nix progs in the native.

Also I installed a Windows 7 theme onto my gnome desktop to make it look like Windows 7.  Why you might ask?  I wanted it all to look similar and no one is the wiser that I am running Linux as my primary OS.

Good luck  :grin:

---

### Post by Starfleet on 2012-07-16
Jobbo, I've just dual booted Ubuntu 12.04LTS with Win7 using this guide here. 

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/")

It was a breeze and the beauty of following this simple guide is that each operating system is protected against boot problems when big updates come in. Or at least, should be. And so far no problems and that's something that the default install for dual booting can't always guarantee. In other words you won't ever be in a situation where you cannot boot one or the other OS's if you follow the guide in the link. 

Good luck.

---

### Post by darkod on 2012-07-16
> **Starfleet said:**
> Jobbo, I've just dual booted Ubuntu 12.04LTS with Win7 using this guide here. 

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

It was a breeze and the beauty of following this simple guide is that each operating system is protected against boot problems when big updates come in. Or at least, should be. And so far no problems and that's something that the default install for dual booting can't always guarantee. In other words you won't ever be in a situation where you cannot boot one or the other OS's if you follow the guide in the link. 

Good luck.

I don't agree with that link and keeping the windows bootloader on the MBR. While it is true that any windows reinstallation will overwrite grub2 on the MBR, I don't see that as big issue (and no one should), because you can reinstall it back with only two simple commands.

On the other hand, forcing grub2 to install onto a partition instead of the MBR, can make grub2 break when there are updates for the package, and similar situations, which means even without totally reinstalling ubuntu. This is because grub2 doesn't fit on the Partition Boot Record and part of it needs to be put somewhere on the disk. During updates this location can change and the grub2 code on the PBR will keep looking at the old location, thus breaking grub2.

On top of that, I see no reason to insist on keeping the bootloader that can't boot both OSs by default (windows bootloader) on the MBR, while forcing the bootloader that can boot both OSs in an unnatural position.

---

### Post by Starfleet on 2012-07-16
Yes, I see where you are coming from Darkod. But I've got to say that when I first dual booted with 12.04 in the "conventional" way allowing Ubuntu to do it's own thing, the first set of big updates that came in for Ubuntu broke the installation and it wouldn't boot. This included a new kernel amongst other things. I fixed it easily but the next day a big update for Windows came in and that broke Windows and it wouldn't boot. As the machine was going down to Exeter University with a novice in these matters I decided to use the guide above to avoid as much trouble as possible. I can say that once it was installed, the same updates came in again and neither system was affected in any way and both booted easily. No problem. So far it's been perfect...although running for just a few weeks now. But I'll be monitoring the situation. If it turns out not to be as good as many are saying, I'll change it.

---

### Post by darkod on 2012-07-17
> **Starfleet said:**
> Yes, I see where you are coming from Darkod. But I've got to say that when I first dual booted with 12.04 in the "conventional" way allowing Ubuntu to do it's own thing, the first set of big updates that came in for Ubuntu broke the installation and it wouldn't boot. This included a new kernel amongst other things. I fixed it easily but the next day a big update for Windows came in and that broke Windows and it wouldn't boot. As the machine was going down to Exeter University with a novice in these matters I decided to use the guide above to avoid as much trouble as possible. I can say that once it was installed, the same updates came in again and neither system was affected in any way and both booted easily. No problem. So far it's been perfect...although running for just a few weeks now. But I'll be monitoring the situation. If it turns out not to be as good as many are saying, I'll change it.

You probably had other issues which went away when you reinstalled.
In ubuntu, updates can rarely break grub2 even if the package is getting updates too. If you are doing an upgrade to a more recent version, that can sometimes take a wrong turn.
In windows, also, updates shouldn't really touch the bootloader, especially the way the windows bootloader is set up. If there is some utility running in the background that doesn't like having a non-windows MBR (there was something like that few years back with HP and Dell but I think they are not doing it any more), that is also a different topic.

In any case, you should use what works best for you, but I just wanted to point out that the problems you had are not general and that link shouldn't be used as a general way to install.

I am dual booting win7 Ult with ubuntu on both my desktop and netbook, doing all updates in both OSs and it has never in 3 years (since I discovered ubuntu) touched my bootloader.

---

### Post by Starfleet on 2012-07-17
Darkod, thanks very much for your opinion on this. You have much greater knowleage than I do on this subject. As I say, so far everything is going ok on the machine I was talking about, and also one other that I did in the same way. Both high spec laptops dual booted with Win7 home prem. But me, I'm just not a Windows fan I'm afraid and can live without it just fine. What a pleasure Ubuntu is to use and I find it much more useful than my old Windows installations too.

Thanks...

Ian

---

### Post by Jobbo256 on 2012-08-18
Thank you everyone for your advice. I am currently using 11.10 (the reason I was using 10.10 was because that was one of my favourites and it still used gnome classic) I still need to fix my windows problems, but I am progressing. Thanks all.

---

