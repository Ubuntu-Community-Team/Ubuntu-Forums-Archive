---
title: "Ububtu Ubunity and Ubuntu 22.04 LTS not recognizing video"
date: 2022-05-05
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-05-05
This pertains to my Dell Vostro 3500 laptop.  All Ubuutu versons from about 2015 trough 21.10 recogniized nVidia GeForce 310 hard and enabled me to install the correct driver.  22.04 LTS did not recognize the Broadcom wifi, but Ubuntu unity 22.04 (only OS) does.  Thus vdeo performance is poor.

So, how do I get Ubuntu Unity to recognize the nVidia hardware and firmware.  If Ubuntu Unity could find the nVidia hardware, the correct drive is in Synaptic.

Thank you,

John

---

### Post by guiverc on 2022-05-05
Ubuntu and all [*flavors* of Ubuntu]("https://ubuntu.com/download/flavours") are built on the same infrastructure, from the same Ubuntu repositories thus are known quantities as you can look up the *seed*s to see what makes it to the media for an install, plus *manifests* to see what's included, or what's not included of a finished product (*at install time options selected can cause only subsets of the manifest to install*).

Ubuntu Unity is a ***remix*** that is not an official Ubuntu product, thus the creators of it can include anything they like; from official Ubuntu packages, to 3rd party sources that cannot be included on Ubuntu ISOs. 

It's my understanding that *Ubuntu Unity* hopes to be an *official flavor*, which requires they have their last two releases using only using packages that can be included on Ubuntu ISOs, thus I'd expect their ISO to be identical to a Ubuntu ISO.

Ubuntu Desktop 22.04 LTS by default includes the HWE kernel stack, where as Ubuntu *flavors* default to the GA kernel stack (on 22.04 & 22.04.1 media), but at this stage that should make no difference (both HWE & GA are currently 5.15).

I don't know what the difference is, but if it was me I'd boot one, take notes of what's running, what is being used & included, then boot what you'd like to use & contrast what you see there & what is different. You don't need to install, but can explore *live* systems running on your hardware, and confirm details using the *manifest* files of what's included on the ISOs.

Ubuntu 22.04 LTS can also use a OEM kernel stack ie. if your hardware is detected during the boot process, a replacement OEM kernel will be used instead of default GA/HWE (*the ISO you're booting controls which of those is used*).  Lubuntu is one example of a Ubuntu ISO that doesn't include a OEM kernel; so it'll be a Ubuntu ISO that can't install with OEM kernel stack; maybe Ubuntu Unity ISO doesn't include OEM options like Lubuntu doesn't.

The significance of kernel stack; is what are commonly called *drivers* are actually kernel modules; thus using a different kernel will result in different kernel modules (aka. *drivers*) being used..  Ubuntu LTS offer three kernel choices; GA, HWE & available on some hardware OEM options; some ISOs allow you to select at install time which you'll use (eg. *Ubuntu Server ISOs using `subiquity` installer*), others the ISO used to install sets the default (*with some flavors offering a different stack choice to main Ubuntu, others the identical stack is used*).  The install just sets the default; as all can be changed post-install.

Ubuntu Unity being a *respin *or 3rd party ISO isn't limited to what Ubuntu and *flavors* are allowed to include (ie. no non-Ubuntu-repository or 3rd party software can be included on the ISOs), especially if they wish to remain a *respin* and not become a *flavor*.

---

### Post by cigtoxdoc on 2022-05-07
Unity is apparently run by those at [https://discourse.ruds.io/c/ubuntu-unity/5](https://discourse.ruds.io/c/ubuntu-unity/5) .  However, after creating login twiice with two different email addresses, I have never got confirming email to logon  on.  No way of contacting them by email.  Perhpas someone reading this thread can get the word to those in charge.

Thank you,

John

---

### Post by guiverc on 2022-05-07
> **cigtoxdoc said:**
> Unity is apparently run by those at [https://discourse.ruds.io/c/ubuntu-unity/5](https://discourse.ruds.io/c/ubuntu-unity/5) .  However, after creating login twiice with two different email addresses, I have never got confirming email to logon  on.  No way of contacting them by email.  Perhpas someone reading this thread can get the word to those in charge.

Thank you,

John

The site you provided is [Rudra's]("https://launchpad.net/~rs2009") private site; and if I wanted to speak with him, I'd personally do it via IRC if I saw him online, via telegram, or email. 

I'd also not go for a specific *developer* if you were seeking help on using the *remix*, but opt to use a means by which any of the team members could respond, not rely on a single person.

I'd possibly seek help via [https://t.me/ubuntuunitydiscuss](https://t.me/ubuntuunitydiscuss) as I see many Ubuntu Unity people active on telegram.

 Yes I mentioned IRC first earlier, but that was the specific *developer *(Rudra) you mentioned as I believe that's where I've spoken most with him, though none of our discussions related to Ubuntu Unity. If I had Unity questions, I'd use a site used/appropriate for the team. You'll find there links at [URL="https://ubuntuunity.org/"]https://ubuntuunity.org/

[/URL][addendum:]

I'll add some other links for Ubuntu Unity on telegram -

For Ubuntu Unity QA use [https://t.me/ubuntuunityqa](https://t.me/ubuntuunityqa)
For Ubuntu Unity Announcements use [https://t.me/ubuntuunityannouncements](https://t.me/ubuntuunityannouncements)
For Ubuntu Unity off-topic/general discussion use [https://t.me/ubuntuunityofftopic](https://t.me/ubuntuunityofftopic)

---

### Post by cigtoxdoc on 2022-05-08
Thank you very much for your suggestion.  I finally with a thrid email. got a confirmng emal from [https://discourse.ruds.io/](https://discourse.ruds.io/), and have posted question.  I have no experience with IRC.  My Samsung Galaxy S9+ would not let me scan the QR code for Telegram.  I tried one program from Google Play.  As soon as I stated using it , my cell phine wanted to install another QR scanner.

John

---

### Post by cigtoxdoc on 2022-05-08
The fix for this problem can be found at [https://askubuntu.com/questions/1403940/ubuntu-22-04-lts-and-elitebook-8440p-hangs-roughly-within-minute-of-login](https://askubuntu.com/questions/1403940/ubuntu-22-04-lts-and-elitebook-8440p-hangs-roughly-within-minute-of-login) .  This fix worked perfectly for my Dell Vostro 3500 running Ubuntu Unity 22.04.

John

---

