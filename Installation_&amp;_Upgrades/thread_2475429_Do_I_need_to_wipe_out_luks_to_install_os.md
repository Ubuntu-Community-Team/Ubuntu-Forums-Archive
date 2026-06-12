---
title: "Do I need to wipe out luks to install os?"
date: 2022-05-26
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2022-05-26
Friends--

Over the past week I have tried to install three different OSes to a couple of my old 32 bit machines: lubuntu, peppermintos, and xubuntu.

Both machines have prior ubuntu versions on them, in a luks/lvm environment.

I have used DVD disks (created via brasero) as well as thumb drives (created via startup disk creator). Only got one of them to actually boot up the lubuntu installer, and it said it could not mount the DVD (although I was installing via the usb drive). I even tried the usb stick on a 64 bit machine and got the same errors--this machine also has lvm/luks.

It seems that perhaps the luks environment is giving all of these installers difficulties.

So, do I have to completely wipe the disks to be able to install, or even to use a live disk? (I was hoping to preserve the luks setup and simply install the new os inside luks.)

Thanks!

---

### Post by GhX6GZMB on 2022-05-26
With a 32-bit machine you're in a bad spot.
All Ubuntu dialects are out.
I believe debian is still an option, but am not knowledgeable there.

---

### Post by dgermann on 2022-05-26
@ml9104--

Thanks. The versions of these OSes I have downloaded are all 32 bit versions.

Even so, a 64 bit machine was not able to open them. That makes me consider luks as the issue.

---

### Post by GhX6GZMB on 2022-05-26
OK.
So the Lubuntu version you have is 18.04 (LXDE desktop) or 18.10 (LXQt desktop).
The .iso is hopefully downloaded from the archives of lubuntu.me and NOT from lubuntu.net, which is a cybersquatter site.
Luks or no luks: it doesn't matter. You'll need to do a live boot with following install, including formatting (preferably ext4), luks is not the issue, a live boot should always work.

---

### Post by guiverc on 2022-05-26
The[ "*Erase disk*" option of the Lubuntu calamares installer]("https://manual.lubuntu.me/stable/_images/partitioning.png") will not care what was there before hand, just erase it & install a new system. LVM makes no difference.

Lubuntu only supports *amd64* now, and only 18.10 & 19.04 ISOs were generated with the `calamares` installer. 

 Releases prior to LXQt were available in two ISOs, the main ISO used the `ubiquity` installer which had no issues with LVM either as I recall just erasing whatever was there and creating a new partition table/file-system as the user selected.  

The *alternate* ISO used the *debian installer* which was more limited; but it was created for systems that had 768MB or less of RAM and couldn't run the *live* system and installer at the same time, back when Lubuntu supported machines with 256-768MB of RAM.  If using a machine with that limited resources, I'd likely be using terminal commands to erase & create new file-systems before hand, or run a *live* system & create the file-systems I wanted (using `gparted` etc if the box is capable of it), then just install into the pre-prepared disk/file-systems. I never had issues with either approach, but [18.04.5 was a long time ago]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/"), and the *alternate* ISO was never re-spun so you'll have to go back to 2018-April for QA-testing of that ISO which was a long time ago.

[Lubuntu 18.04 LTS is *end of life*]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") so please be aware of that; yes the packages you have that are in common with Ubuntu 18.04 LTS Desktop are still *supported* and receive *security fixes*, but that's not your whole system.  You can use

```
ubuntu-support-status
```

to confirm which packages on your system are still *supported* thus received security fixes, and which don't, but all LXDE components are EOL, so if flaws are detected you'll need to *patch* them yourself.

FYI:  I still have Lubuntu 18.04 LTS installed on a IBM Thinkpad t43 which I've used for [numerous pastes]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7") and examples; my own usage hasn't made me want to switch the box to Debian yet - but you decide on how you use your machine.  

I've never had issues removing a prior *file-system* regardless of what was on the drive (*be it LVM or other*) with working hardware - have you checked you have a reliable system?  If using *live* media, the media validated correctly etc.

---

### Post by dgermann on 2022-05-26
@ml9104

Thanks. I downloaded from [https://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](https://cdimage.ubuntu.com/lubuntu/releases/18.04/release/) which seems legit to me, but I will redownload from lubuntu.me.

@ guiverc

I think however I did the alternate so that might be the issue with lubuntu. I will switch to the main iso.

Please tell me if I am interpreting your post correctly: I ought to be able to leave my lvm/luks set up as is, and simply install the new OS inside that? And the installer should handle that for me, without my worrying about unlocking the disk before running the installer?

Thanks!

---

### Post by guiverc on 2022-05-26
If it came from cdimage.ubuntu.com it'll be an official ISO created by Ubuntu infrastructure.

lubuntu.[net] isn't related to the Lubuntu/Ubuntu project, but was used by the Lubuntu team until they had a web site of their own; and usually didn't offer downloads directly; but linked to the main Canonical ubuntu.com site for downloads.  We have no control over anything on non-Ubuntu/non-Lubuntu sites.

If you're using LVM because of encryption; be aware that current methods differ to what was used in releases long since gone/EOL (ie. pre-18.04). As Lubuntu 18.04 LTS is EOL I won't provide support for it, however I did do QA-test installs of Xubuntu 22.04 LTS & Lubuntu 22.04 LTS onto encrypted drives which were setup/installed using older no-longer default encryption methods and all that was required was to add the required package on to the *live* system before I started the installer (*so it could cope with it*). I'm mentioning Xubuntu as it uses the `ubiquity` installer same as Lubuntu 18.04 LTS used (*excluding alternate ISO; Lubuntu now uses only `calamares`*).  The package was added as the older encryption system is no longer used (*by default*); thus the ISOs don't include the required package to deal with it.  I won't & really can't advise with *debian installer* as I don't use it often enough

---

### Post by dgermann on 2022-05-26
@ guiverc

Thank you. I think I am understanding. These luks/lvm were set up under 18.04.

"all that was required was to add the required package on to the live system before I started the installer (so it could cope with it)" What is the process to do that, if you please?

Thanks!

---

### Post by guiverc on 2022-05-27
If luks/lvm was setup on 18.04 then **unless** you added packages in order to set it up, you'll have everything you need already.

An example of packages I was thinking of include partition encryption provided by `ecryptfs-utils` which from memory was default on 17.10 (*artful*) and earlier, but it's not provided by default any longer on ISOs thus won't be found for example on current *kinetic* daily - [https://cdimage.ubuntu.com/lubuntu/daily-live/current/kinetic-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/daily-live/current/kinetic-desktop-amd64.manifest)

I don't recall well differences between the *alternate *and *primary* 18.04 ISO (*for Lubuntu, as we don't support 18.04 any longer*), however I do know no *flavor* was involved in the last release of [Ubuntu 18.04.6]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") as we were all EOL already, thus we don't have *patches* for *boothole vulnerability* etc, which can create an issue in that installed systems can receive upgrades/fixes, but re-installation of *patched* systems is impossible as you need 18.04.6 media for which no *flavor* provided due to EOL. This is ***unlikely*** your issue though if you're using a *i386 *box in my opinion.  (*if it was the issue which I don't believe it is, you'd get around this via a Ubuntu Server 18.04.6 install, then changing that into the flavor like Lubuntu you really want*)

FYI:  The *kinetic* daily was used only because it was easy/known to me,  a *patched **bionic *(18.04.6) manifest can be viewed here - [https://releases.ubuntu.com/18.04/ubuntu-18.04.6-desktop-amd64.manifest](https://releases.ubuntu.com/18.04/ubuntu-18.04.6-desktop-amd64.manifest)

---

### Post by dgermann on 2022-05-27
@guiverc

Thanks! Now I get it (I think).

Will play with it a bit and report back.

---

### Post by guiverc on 2022-05-27
re: *boothole vulnerability* & 18.04 media

If that was your issue, your hardware would be refusing to boot any Ubuntu 18.04.5 LTS (*or older*) media as it's signed key is now *expired/invalid* due to the *vulnerability being discovered. *This revoked *key* is  why 18.04.6 media was produced; ie. so there was *bionic* media that will boot on *fully-patched* hardware.  

*Boothole vulnerability *is not your issue *in my opinion*, or your issue relates to *installation*, and not booting of the media itself (*which would be the issue if your issue was boothole related I believe*). 

 I provided the detail as example of issues with *EOL* systems, of which there may be others too.  We (*Lubuntu*) stopped monitoring issues with *bionic* (18.04) when it reached EOL (*for flavors*); I'm aware of some like boothole due to other team (Ubuntu News) involvements.

---

### Post by dgermann on 2022-05-28
@guiverc

Thanks! I will look do some searches on boothole vulnerability and look for 18.04.6 versions. Since one of those I tried was peppermintos, I wonder if that would be my issue. Unclear how hardware becomes fully patched; it sounds like a term that applies to software.

Thanks!

---

### Post by guiverc on 2022-05-29
The boothole vulnerability relates to grub (*booting*) & uEFI, and most *i386* hardware is BIOS/*legacy* and doesn't use any uEFI so has no capacity to store the detail; and even if *i386* had uEFI it'll be earlier versions that didn't use the Secure/security modes.

uEFI compatibility requires the machine be made with a set of signatures which an OS can update (*think firmware update maybe*), thus when the vulnerability was discovered, the impacted systems were given time to produce new media; upgrades go out (*to installed OSes/systems*) that will cause the older keys to become revoked, meaning those systems will prevent booting of the older media as it doesn't have a *valid* key.  A security measure to prevent booting what maybe *compromised/dangerous *media.

I'm betting your hardware has no capacity to store that detail given it's 32-bit; ie. no reserved *flash* memory reserved for keys, thus it won't be impacted by it. I suspect it'll still boot 18.04 thru 18.04.6 media not doing any key validation. High end equipment started moving to 64-bit before uEFI was common place (esp. on *x86*), so 32-bit implies to me it was *consumer* grade and not *high-end* (esp. servers) which tended to get the better/latest security features.

I've done no QA-testing of uEFI on 32-bit hardware; and cannot think of any equipment I used with Lubuntu that was *i386* that was capable of storing uEFI keys either given they were used in Secure-Boot-uEFI only.

---

### Post by dgermann on 2022-05-29
@guiverc

Thanks, that will save me having to research boothole.

The machines involved are a System76 gazv4 from 2007. and a generic box from 2006. I doubt they have uefi. But the 2015 generic box 64bit almost certainly has it, which may explain why that box would not boot this thumb drive.

I have things I need to do today at least which will keep me away from trying different things. One I want to try is a puppylinux in both of these machines and another, to see if I can get anything to boot!

Thanks for helping, guiverc!

---

