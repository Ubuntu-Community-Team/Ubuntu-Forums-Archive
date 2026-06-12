---
title: "Migrating Windows XP; Linux Mint XFCE, versions, upgrades and updates..."
date: 2014-02-05
forum: MINT
---

### Post by Z80A on 2014-02-05
Supporting friends and some seniors with their forthcoming XP migration I have been considering different paths for these somewhat older machines:

[LIST]
[*]L/Xubuntu (good release/upgrade support)
[*]Linux Mint XFCE (very intuitive and XP-like UX/UI)
[*]elementary OS (good looking, really...)
[/LIST]
[INDENT=7]...it’s all Ubuntu![/INDENT]

My concerns are very much of a practical nature related to daily use by "normal" people (you know what I mean - they don’t do *sudo*’s). To such people migrating from Windows XP due to the EoS/EoL, stability and predictability is important. As such long term support and automated updating/upgrading are important parameters and appears to be supported (to some extend) by the above. Being forced to re-install a new Linux version later this year is not good.

I know all of the distributions and I have as an experiment put Linux Mint XFCE 16 on an Acer Travelmate 2430 (Celeron, 1 Gbytes RAM) and it looks really good (and XP-like) and is very responsive - certainly the best result this far.

**Question 1: **Having been an Ubuntu user for years, I am quite used to a very seamless upgrade process. And even though I have promised myself to only go for LTS releases I have mostly taken any release upgrade offered. For the XP migrations I will be doing, I would like to disable these and only enable the LTS upgrades - something that is easily configured in Ubuntu. Can I do this in Linux Mint XFCE?

**Question 2: **If I choose to do the XP migrations with Linux Mint XFCE 16, can I expect to do a fairly straight forward upgrade (no re-install) during spring 2014? Or is Linux Mint XFCE 13 the right choice to avoid doing a re-install or complicated migration before 2017?

I could call Microsoft and ask them to give us another month or two with XP, and aim for Linux Mint XFCE 17 LTS, but I doubt they will align their life-cycle management with Linux roadmaps... ;) 
[B]
Question 3:[/B] Having migrated to Linux Mint XFCE and software updates are available, this is indicated in the taskbar and updating must be activated by the user (using password). Is there any way to automate this as an unattended background activity with minimal user intervention?

One concern I have with these XP users could be their use of Windows Live Gallery tools for organizing photos. I have no detailed understanding of how these tools manage, index or tag photos, but preferably all tagging should be kept and transferred into a similar tool on Linux. gThumb and Shotwell are both great tools, though working in quite different ways, but will be natural candidates on Linux.

**Question 4:** Anyone having any experience with migrating the photo content of Microsoft Live Gallery into Linux tools?

...surely I am not the only one looking into this over the next month or two. :|

---

### Post by TheFu on 2014-02-05
tl;dr - however, I migrated Mom (76 yrs old at the time) to Lubuntu years ago.  The trick was that she was already using Firefox, Thunderbird and most of the other daily-use software under Windows, so the OS change wasn't that big of a deal. She was scared, really, scared.  Then I showed her all the same software that she had been using for years.  

Firefox and Thunderbird are just a little different under Linux than Windows, but close enough.  THAT would be the first thing I started.  Switch them over TODAY.

Only at tax-time did she have issues, the main tax software doesn't run under Linux. Also I replaced her non-Linux supported Canon printer for a $50 Brother Laser and bought her a 8,000 page toner cartridge - she said that it would outlive her.  Sadly, that was true. She died last July. She was ready and it was time. 

I think Mint is too far off mainstream to be considered. Your love for Mint might not help them to search for answers.  Xubuntu is easy to search on the internet.  Ubuntu has lots of forum help too.  There is an LTS issue however. Lubuntu is NOT an LTS release - ever.  Only 18 months of support for the 10.04/12.04/14.04 releases. That is an issue.  I haven't looked up Xubuntu to know, definitely check for yourself.  Mint support is based on Ubuntu support, so perhaps it is the better choice?  Regardless, you need to deploy an OS with 5+ yrs of support. Too much, unnecessary, change freaks them out.

I do lots of photo gallery stuff, but always avoided everything online and everything from google, apple, microsoft. Sorry that I'm not much help.

So, I skimmed your text.  There are multiple update processes - I stay away from the "upgrade" term, since that is TBD by the users. The computer side and the human side.  

The computer side will include backing up data, wiping HDDs, reformatting and installing a completely new OS.  If they have UEFI computers, it will be a little more difficult.  Every "upgrade" as you are calling it, will be a little different.  A few printers won't work and will never work, but you'll have great remote access via ssh if you set it up. And with ssh running, you can run FreeNX for a remote desktop into each box (though I hardly ever needed it).  I also made a point to do fantastic remote backups for her critical data. That made her happy - oddly, the HDD never failed, but the compute did. Swapped in a new Core i7 and she up again. No reinstall of the OS needed, but we did have to deal with the network card changes manually. I love the LTS.

On the human side, there will be confusion, fear and stares. Maybe crying. Eventually, they will either accept the new OS or stop using the computer completely. Mom accepted it when she knew that I would/could help even from 3 states away.

You are asking all sorts of Mint-specific questions here, on an Ubuntu-centric forum.  Perhaps asking these over at the Mint forums would be a good idea?

---

### Post by buzzingrobot on 2014-02-05
1.  I've found most Windows users have little or no familiarity with virtual desktops.  Some, in fact, find them annoying and confusing. In any case, they usually seem to get along without them just fine.  With that in mind, look at Cinnamon on Linux Mint 16.  To my eye, it relies less on an assumption of familiarity with virtual desktops.  The desktops are there, but not emphasized.  I think it's easier to use by going with the minimize-to-panel notion common in Windows.  

2.  I think Mint 16 is, overall a solid release and your best bet. Mint 17 will be an LTS based on 14.04.  Plan on coming back and upgrading everyone to that in several months.

3. Make sure they understand that once XP is off their machines, there is no going back.  Even if you did a clean XP install, the updates won't be available.

---

### Post by mastablasta on 2014-02-06
i agree with TheFu - having them use good opensource under windows is the first step.

next Linux mint upgrades by reinstall. you backup all data and do a system reinstall. they do not encourage upgrade process as ubuntu does. Though it is possibel to do it.

XFCE is same in Xubuntu you just need to spend a few minutes moving the panels arround.

finally i used Kubuntu to do the move. They already used opensource before on windows (firefox, thunderbird and a few others). Kubuntu (KDE) has a few options besides default menu. there is the classic menu (which looks like XP menu), then there is also homerun kicker which kind of looks like the newer windows mixed with XP. there are a few others like homerun, netbook plasma, plasma touch... but they are not. anyway the older user is satisfied with it. no issues so far. we replaced a few proprietary programmes with good opensource alternatives. skype has linux version so all is good. same goes for flash (to watch videos). they had HP printer and it was recognised out of the box.

i also installed Kubuntu on an older mashcine with 1 Gb ram. works well&fast. i turned off most special effects.

if maschine is older i suggest Xubuntu

---

### Post by maxweis1 on 2014-06-05
BTW, Lubuntu 14.04 is a LTS release, for 3 years.

---

### Post by robin7 on 2014-06-05
Upgrading in Mint is high-risk at best.  Even Mint's most ardent fanboys recommend a fresh install rather than trying to upgrade.  Another issue is that Xubuntu 14.04 can handle secure boot, while it's upcoming Mint counterpart (and the already-released Cinnamon and Mate versions) cannot. All future Mint releases (other than the Debian Edition) are to be based on LTS editions of Ubuntu only.

---

### Post by rewyllys on 2014-06-05
> **robin7 said:**
> . . . . All future Mint releases (other than the Debian Edition) are to be based on LTS editions of Ubuntu only.
What is the basis for your assertion concerning future Mint releases?  I don't recall seeing such a comment on the Linux Mint Website, so if I missed it, I'd like to be updated.

---

### Post by TheFu on 2014-06-05
> **rewyllys said:**
> What is the basis for your assertion concerning future Mint releases?  I don't recall seeing such a comment on the Linux Mint Website, so if I missed it, I'd like to be updated.

Actually, I'd read this somewhere too. Don't know where or why.  Googled this: "linux mint based on LTS only" which returned many "news articles" 
> Linux Mint founder Clement Lefebvre announced an important decision taken on the Mint release cycles. Starting immediately with Linux Mint 17 “Qiana”, the Ubuntu-based operating system will be based only on the LTS releases. 

[I like his decision]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release") for desktops.

---

### Post by monkeybrain20122 on 2014-06-05
> **TheFu said:**
>   There is an LTS issue however. Lubuntu is NOT an LTS release - ever.  Only 18 months of support for the 10.04/12.04/14.04 releases. 

Lubuntu 14.04 is a LTS, but also exceptional buggy. I have just migrated two XP laptops. The first choice was Lubuntu, but having encountered many bugs I wiped it and installed Xubuntu instead. I haven't noticed any difference in performance but Xubu is certainly less buggy. The default choice of Ubuntu Software Centre for package managing doesn't make a lot of sense for a 'light' distro so I installed synaptic and gdebi instead.

---

### Post by rewyllys on 2014-06-05
Thanks to TheFu's quote beginning with "Linux Mint founder Clement Lefebvre . . .", I succeeded in tracking down Clem's comment.

In writing about [New Features in Linux Mint 17 Cinnamon]("http://www.linuxmint.com/rel_qiana_cinnamon_whatsnew.php#lts"), Clem said: 

> LTS strategy[INDENT]Linux Mint 17 will receive security updates until 2019.


Until 2016, future versions of Linux Mint will use the same package base as Linux Mint 17, making it trivial for people to upgrade.


Until 2016, the development team won't start working on a new base and will be fully focused on this one.[/INDENT]


This clarifies the policy for me and, I hope, for other interested users of Linux Mint.  To me, it's an attractive policy and a further reason for my planning to continue using Mint.

---

