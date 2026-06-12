---
title: "Intel 945GM display problem"
date: 2021-08-10
forum: Installation &amp; Upgrades
---

### Post by paulom52 on 2021-08-10
I have an old notebook with a Celeron 530 processor and an Intel 945GM display controller. I have installed Lubuntu 18.04.1 some time ago, but shortly after that an upgrade proved incompatible with the display controller. I had to reinstall Lubuntu and denied any upgrade after that. Now Lubuntu version is 20.04.2. Does anyone know if the incompatibility with Intel 945GM has been solved? Can I upgrade now?

---

### Post by tea for one on 2021-08-10
Firstly, you cannot upgrade in-situ from Lubuntu 18.04 to Lubuntu 20.04 due to the switch from LXDE to LXQT.

Have a look at the comments dated 29 April [https://lubuntu.me/blog/](https://lubuntu.me/blog/)

Secondly, is your device 32-bit or 64-bit?

Many distributions do not offer versions for 32-bit machines now.

---

### Post by guiverc on 2021-08-10
(*this is mostly the same info as tea for one provided)*

Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so Lubuntu 18.04 is EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

which mentioned the 3 years and support ending April-2021.

A Ubuntu Weekly Newsletter highlighted the EOL of flavors
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582))

You can use `ubuntu-support-status` to check out some of the *security consequences* on your actual system (*I've used it many times on Lubuntu's discourse, sometimes with explanation*)


A quick look at [https://ark.intel.com/content/www/us/en/ark/products/33100/intel-celeron-processor-530-1m-cache-1-73-ghz-533-mhz-fsb-socket-p.html](https://ark.intel.com/content/www/us/en/ark/products/33100/intel-celeron-processor-530-1m-cache-1-73-ghz-533-mhz-fsb-socket-p.html) indicates your CPU is capable of running *supported* releases of Lubuntu as I read it as *amd64* capable.

However the release notes for releases 18.10 and later contain a message like

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

Taken from [Lubuntu 20.04.2 releases notes]("https://lubuntu.me/focal-2-released/")

You can download the Lubuntu 20.04.2 media, write to thumb-drive and give it a *spin* on your actual hardware to see for yourself. Yes a *live* system won't give the best (nor *fastest*) experience, but it's the best way to see if you'll have issues. For details on how to do some of this, check out the [manual]("https://manual.lubuntu.me/lts/").

Lubuntu 20.04.2 & later media use the HWE kernel stack, ie. later kernels, so in your case if you have issues with 20.04.2 (or 20.04.3) I'd also likely test the Lubuntu 20.04 LTS (or 20.04.1 LTS) ISOs which use the GA kernel stack, being an older kernel some older hardware performs better than the later stack in HWE.  The GA stack doesn't change during the life of the product (GA remains on 5.4, where as 20.04.2 is 5.8, 20.04.3 on 5.11 etc)

[URL="https://lubuntu.me/focal-2-released/"]
[/URL]FYI: I have an `intel mobile 945gse integrated` in an asus eepc which was used to test Lubuntu releases up to *mid-*19.04 (or when *i386* was dropped, as my intel atom was *i386* only).  It was also used in testing 18.04 media up to the last [18.04.5]("https://lubuntu.me/bionic-5-released/") in August 2020.

---

### Post by paulom52 on 2021-08-10
Well, doing a fresh install is not a problem, I only use this notebook for accessing internet. I just would like to know if it would function after that. I'll try the live system suggestion, thank you.

---

### Post by monkeybrain20122 on 2021-08-11
Well these official eol dates aren't really as big a deal as they sound. If you are using a ubuntu LTS flavor 99% of your system will get 5 year support except for some components specific to the DE.

So Lubuntu 18.04 will be supported til 2023 except for the LXDE stuffs, but you can grab those from the[ LXLE ppa]("https://launchpad.net/~lxle/+archive/ubuntu/stable"). LXLE is a lubuntu respin  based only on LTS's and offers extended support so LXLE 18.04  (current release, 20.04 hasn't appeared yet) will be supported for 5 instead of 3 years, that means the ppa will be good til 2023. 

If I have really old hardware I wouldn't upgrade, just add the lxle ppa and leave it alone.

---

### Post by guiverc on 2021-08-11
@Monkeybrain20122

All of 'universe' repository (ie. not just Lubuntu, but all *flavors*) is now unsupported with no packages corrected if flaws are discovered unless they are in 'main', 'restricted' or 'multiverse'. 

LXLE has a lower security model which is why it can provide 5 years. 

One issue with LXDE is that GTK2 itself is un-patched upstream as it's EOL. GTK3 is now in *maintenance *mode, and GTK4 the *development* product.  It's been that way for some time; why Lubuntu followed the LXDE *devs* when the joined with Razor-Qt *devs* and created the then new LXQt desktop; ie. it's supported (*the GTK3 port idea was dropped as was blogged about years ago by PCMan as it was deemed too heavy*).

You can use `ubuntu-support-status` to view support status for packages; it'll detect not just LXDE packages as unsupported; but any packages found in 'universe'.

I doubt LXLE are patching everything else found in 'universe', but security is a decision we all must really decide for ourselves (*after all we know how we use our boxes; and can best assess the risks involved*).

---

### Post by monkeybrain20122 on 2021-08-11
> **guiverc said:**
> @Monkeybrain20122

All of 'universe' repository (ie. not just Lubuntu, but all *flavors*) is now unsupported with no packages corrected if flaws are discovered unless they are in 'main', 'restricted' or 'multiverse'. 



But isn't universe the same for all flavors as well as official Ubuntu?

---

### Post by guiverc on 2021-08-11
You can find out details of Ubuntu repositories here - [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

'universe' is the community support; which has ended for 18.04 as it came with 3 years of support (ie. 3 years assumed unless no LTS support was given; which applies too for many).

eg. if I quote from the initial [Ubuntu 18.04 fridge release notice]("https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/") you'll note

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. Ubuntu Studio will be  supported for 9 months. All the remaining flavours will be supported for  3 years.

Ubuntu Desktop, Ubuntu Server, and the products with 5 years of support do **not** include any packages from 'universe', which is why you'll note *numerous complaints* about packages being dropped from 'main' and going to 'universe' when it occurs (ie. no longer coming with 5 years of support, nor the higher security checks etc).  They are no longer supported by Canonical.

Yes it's still possible for the community to SRU and patch any 'universe' package, but the community instead concentrate on the *supported* releases (which currently are 20.04 LTS & 21.04 for the community).

Universe packages actually don't all come with 3 years either; ie. you need to check for each package as the support has a minimum of 9 months for 18.04 packages found in 'universe'.  That applied for example for packages put there by Lubuntu relating to LXQt (or what was called Lubuntu Next which was still a *teaser* at that time; first official launch was 18.10) as well as Ubuntu Studio 18.04.

Ubuntu Studio packages only came with 9 months of support for 18.04.  Ubuntu Studio did however provide [*extended support* via PPA]("https://ubuntustudio.org/2019/04/ubuntu-studio-18-04-extended-support/") but not through 'universe' packages (the PPA has since been deleted; but provided support until 29-April-2021).

'universe' package come with varied support; 3 years for LTS supported packages,  and nine months for the non-LTS packages.

Ubuntu provides the `ubuntu-support-status` command so you can check out your support on your actual installed system and whatever packages you have installed.

---

### Post by GhX6GZMB on 2021-08-11
I had the Intel graphics problem on an old notebook. See this thread:&nbsp;https://ubuntuforums.org/showthread.php?t=2130640&amp;page=23<br>Post #223<br><br><br>

---

### Post by GhX6GZMB on 2021-08-11
Hmm. Don't know what happened to the link. I got a "Forbidden" message and now it looks ugly. Sorry, hope you can decode it.

---

### Post by monkeybrain20122 on 2021-08-11
> **guiverc said:**
> (*this is mostly the same info as tea for one provided)*

Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so Lubuntu 18.04 is EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

which mentioned the 3 years and support ending April-2021.

A Ubuntu Weekly Newsletter highlighted the EOL of flavors
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582))

You can use `ubuntu-support-status` to check out some of the *security consequences* on your actual system (*I've used it many times on Lubuntu's discourse, sometimes with explanation*)


A quick look at [https://ark.intel.com/content/www/us/en/ark/products/33100/intel-celeron-processor-530-1m-cache-1-73-ghz-533-mhz-fsb-socket-p.html](https://ark.intel.com/content/www/us/en/ark/products/33100/intel-celeron-processor-530-1m-cache-1-73-ghz-533-mhz-fsb-socket-p.html) indicates your CPU is capable of running *supported* releases of Lubuntu as I read it as *amd64* capable.

However the release notes for releases 18.10 and later contain a message like



Taken from [Lubuntu 20.04.2 releases notes]("https://lubuntu.me/focal-2-released/")

You can download the Lubuntu 20.04.2 media, write to thumb-drive and give it a *spin* on your actual hardware to see for yourself. Yes a *live* system won't give the best (nor *fastest*) experience, but it's the best way to see if you'll have issues. For details on how to do some of this, check out the [manual]("https://manual.lubuntu.me/lts/").

Lubuntu 20.04.2 & later media use the HWE kernel stack, ie. later kernels, so in your case if you have issues with 20.04.2 (or 20.04.3) I'd also likely test the Lubuntu 20.04 LTS (or 20.04.1 LTS) ISOs which use the GA kernel stack, being an older kernel some older hardware performs better than the later stack in HWE.  The GA stack doesn't change during the life of the product (GA remains on 5.4, where as 20.04.2 is 5.8, 20.04.3 on 5.11 etc)

[URL="https://lubuntu.me/focal-2-released/"]
[/URL]FYI: I have an `intel mobile 945gse integrated` in an asus eepc which was used to test Lubuntu releases up to *mid-*19.04 (or when *i386* was dropped, as my intel atom was *i386* only).  It was also used in testing 18.04 media up to the last [18.04.5]("https://lubuntu.me/bionic-5-released/") in August 2020.

Yes, I know all that. But still I don't get the fuss. Official Ubuntu LTS and all the flavors share the same servers and universe, no? So if a package is dropped it will not be available to all and if it is unmaintained it will be unmaintained for all, no?  So basically this will affect the flavour but not official Ubuntu only if the package is specific to it and installed before its support expired and now no more updates are available, correct? Though I suppose you can install an xfce or lxde session on official Ubuntu for some reasons like x2go or some games which cannot handle desktop composting well, so now you also have unmaintained software, no?

So for OP that means the lxde stuffs will not be supported at this point by Canonical but if lxle offers support through its ppa I don't see what the problem would be. Now if you don't trust the lxle team that is a different story (and you may be right in that, I have tried to set up lxle on a friend's old computer and I find they add a lot of ppa by default e.g vlc. I don't like that, I use ppas but I add them myself and I know how to keep track of them, but that belongs to another thread.)

I think you can switch the kernel stack if needed, it gets kernel from same repo and it wouldn't ban you because you use a flavor, or you can grab it from mainline. OP's computer probably won't survive for another 2 years and may not like newer software stack (and from what I read the lxqt stuffs are kind of bloated and buggy, but this is from hearsay, I don't use it)  so if it works just do minimal maintenance instead of upgrading and risk breaking it. To upgrade something that old would be like telling a 99 year old man to do a major surgery to improve circulation so it will prevent some future, unspecific health hazard.

Just is my 2 cents. For myself I wouldn't use 18.04 beyond this point even though it is maintained. The software is just too old for my liking.

---

### Post by guiverc on 2021-08-12
> **monkeybrain20122 said:**
> Official Ubuntu LTS and all the flavors share the same servers and universe, no?

Yes the repositories are the same for all, but all 5 year supported release do **not** have the 'universe' (community) repository enabled, so for them to get shorter life packages on their systems, they have to take the step of enabling that repository.

All *flavors* that come with the shorter life-spans only come with 'universe' enabled.

It's a choice users have to decide for themselves.  I've seen many support queries from enterprise users who can get exactly what they want for their servers, but it's found in 'universe' but they don't want the maintenance/security hassle of enabling it.

Myself, as I still have x86 (32-bit) hardware I still use 18.04 & *flavors*; as I don't see the benefit of moving to a supported Debian system (*I love Debian, having been a Debian user far longer than Ubuntu*), but I made the decision that they way I use those boxes is not a security risk.


> **monkeybrain20122 said:**
> 
OP's computer probably won't survive for another 2 years and may not like newer software stack (and from what I read the lxqt stuffs are kind of bloated and buggy, but this is from hearsay, I don't use it)  so if it works just do minimal maintenance instead of upgrading and risk breaking it.


I used to love using MATE on the x86 hardware I still use, but at 16.04 Ubuntu-MATE (now GTK3 instead of GTK2) was just too slow on pentium M processors (ie. really old hardware) and I switched to LXDE or XFCE only for x86 pentium M. I had no interest in GNOME, Unity even in 16.04 even on the more powerful pentium D testbox. 

Up to 18.04 XFCE/Xfce was still okay as the GTK2/GTK3 port still had a way to go, it was slowing and LXDE started to noticeably outperform XFCE on pentium M boxes.  I also QA-test using Pentium 4 & D, and on the pentium D (dual core pentium 4; early x86 only) XFCE was still usable.

Lubuntu 18.10 & 19.04 using LXQt far outperformed Xubuntu on the same pentium M boxes in my experience; in fact I feared the drop in performance that I first saw with MATE when it ported from GTK2 to GTK3 and was seeing in XFCE as it progressed. Alas LXQt remained very fast, and no it was not buggy in my opinion (parts had limitations as it wasn't as *mature* as other desktops; but that wasn't bugs just things it didn't yet do).

On the pentium D (x86 only) I also upgraded to *eoan* so I could experience Xfce that was then said to be fully GTK3 compliant, and whilst usable; it was no longer *fun* to use as this box too noticed slow down like the less powerful pentium 4 & M processors.  If I had to use it I would have though.  LXQt however was really good.  Soon Canonical switched off the package builds for *i386 *so the box was falling behind; but my i386 box still did one SRU verification for *eoan* before its packages fell behind :)

The only place where I found LXQt bloated is, given it's Qt5, was where users keep sticking to using GTK3 apps thus have both Qt5 & GTK3 libraries/toolkits in RAM (in this case; using a desktop that shared apps with the chosen apps makes more sense).  My x86 box had two desktops installed (*if not more*), Xfce if I'll be using GTK3 apps, and LXQt if I wanted speed & better performance for browsing etc.  The switch of libs from GTK2 to Qt5 was only an issue if the user refused to switch apps; thus 'bloat' was a user caused issue  (*my opinion; is based on LXQt 0.13 & higher; I wasn't interested much in it before then*).

I disagree LXQt is bloated, it uses the same Qt5 as KDE, but does not require KF5 that KDE does. It's the fastest *flavor* on my main box, which is a 2009 dell desktop (c2q as pre-dates the i-series of intel cpus). It outperforms XFCE in my opinion (*though I have XFCE installed too; it was my preferred desktop before I was asked to join the Lubuntu team*)

---

### Post by monkeybrain20122 on 2021-08-12
> **guiverc said:**
> Yes the repositories are the same for all, but all 5 year supported release do **not** have the 'universe' (community) repository enabled, so for them to get shorter life packages on their systems, they have to take the step of enabling that repository.

All *flavors* that come with the shorter life-spans only come with 'universe' enabled.

It's a choice users have to decide for themselves.  I've seen many support queries from enterprise users who can get exactly what they want for their servers, but it's found in 'universe' but they don't want the maintenance/security hassle of enabling it.

Myself, as I still have x86 (32-bit) hardware I still use 18.04 & *flavors*; as I don't see the benefit of moving to a supported Debian system (*I love Debian, having been a Debian user far longer than Ubuntu*), but I made the decision that they way I use those boxes is not a security risk.


Fair enough. but OP didn't say he is an enterprise user so that is probably irrelevant. Enterprises typically only install software that is essential for work and keep them very old for "stability" so you have enterprises such as banks which are still using Windows 7 (or XP?) and they probably purchase extended support from the vendor (MS in the case of Windows, Canonical in case of Ubuntu) I think the normal users' use cases are very different. It would be hard not to enable universe and multiverse for normal users since many useful things will be missing. I checked the Ubuntu wiki(?) All it says about universe and multiverse is that these are community supported rather than Canonical supported. That is the case whether ubuntu release has reach eol or not, So even if I install from universe and multiverse now on Ubuntu 21.04 the packages are still not supported by Canonical.  But that is not the concern for most users I think. If you use distros like Debian then really the whole thing is "community support", doesn't make it less secure. I think implicit in the idea of "open source" is that we actually trust the vigilance of "the community" more than any single company so "community support" shouldn't be a bad thing.

As for LXQT, I defer to your opinion. As I said I never use it, let alone doing detailed benchmarking and QA,  my info is from hearsay. Thanks for pointing it out. I am a unity fan, different strokes for different folks. ;)

---

