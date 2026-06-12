---
title: "Upgrading to new UBUNTU versions"
date: 2022-05-01
forum: Installation &amp; Upgrades
---

### Post by jooa0ky on 2022-05-01
Hey, so I've actually been using the 19LTS since like 2015 on my home desktop and everything works great... Seriously, I've experience no slow downs ever since I built this thing. Most other OS seem to start decaying after like the first year so this thing has been going strong.

At my personal desktop at my office, I do have the newest version 22LTS. Just wondering if I should upgrade my home one? I just have a lot of personal settings and etc saved on there I'm just so use to?

If I do the upgrade, does everything get wiped to brand new or would everything on there remain as is but I receive the functionality of the new version?

Thanks!

---

### Post by tea for one on 2022-05-01
> **jooa0ky said:**
>  I've actually been using the 19LTS since like 2015 on my home desktop 

Ubuntu version 19.04 or 19.10 were not LTS releases.
Can you pop this command in the terminal and post the output?
```
lsb_release -a
```

---

### Post by grahammechanical on 2022-05-01
If we are using Ubuntu 20.04 LTS then we will be able to do an online upgrade to Ubuntu 22.04 LTS in about 6 months time. Users of 20.04 should open Software & Updates>Updates tab and make sure that the panel "Notify me of a new Ubuntu version" is set to "For long term support versions." Then in due time the operating system will offer to upgrade to Ubuntu 22.04.

If you are using 19.04 or 19.10 then it will be very difficult to upgrade to the next Ubuntu release (20.04) because 19.04 and 19.10 have reached end of their support life. Once that happens upgrading to 20.04 becomes difficult. Better to backup your data and do a fresh install or either 20.04 or 22.04.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Regards

---

### Post by jooa0ky on 2022-05-01
> **tea for one said:**
> Ubuntu version 19.04 or 19.10 were not LTS releases.
Can you pop this command in the terminal and post the output?
```
lsb_release -a
```


Oh wow... I guess it was actually longer than that...

Description: Ubuntu 16.04.7 LTS

lol...

Just a little bit difficult since there's absolutely nothing wrong with the system at all. Could I just continue using as is, or has there been something really important and necessary in the in between versions since then in your opinion?

---

### Post by tea for one on 2022-05-01
> **jooa0ky said:**
> Description: Ubuntu 16.04.7 LTS 

Ubuntu 16.04 is now unsupported unless you have subscribed to Extended Security Maintenance (which is generally for business/enterprise users)

I would suggest that you download Ubuntu 22.04, create a bootable USB and try it out.
If all goes well, back up your data, install a supported OS and restore your data.

---

### Post by sudodus on 2022-05-01
I agree, that you should download Ubuntu 22.04, create a bootable USB and try it out.
If all goes well, back up your data, install a supported OS and restore your data.

Without support, there are no security updates, and your system is vulnerable to attacks via the internet.

---

### Post by TheFu on 2022-05-01
> **jooa0ky said:**
>  
If I do the upgrade, does everything get wiped to brand new or would everything on there remain as is but I receive the functionality of the new version?

Well, that's the issue isn't it?  Sometimes settings change between different software versions. Old settings become deprecated and don't work or don't work the same way they did before.  Sometimes old settings break things in new software.  Nobody here can guess what software you have, which settings you've changed, and I hate to say it, but since we are volunteers (not Canonical employees), I doubt anyone is willing to do the research to check every program, every setting, that you use. I'm not.  Plus, the desktop settings are stored inside all sorts of funky files inside your HOME.  

The best advice has been given above already.  16.04 standard support ended over a year ago. It is dangerous to use that OS on any network with other computers or over the internet. There are number of remove attacks against it and the software it runs which could have already provided someone a back door onto your system, into your LAN and onto other devices.

I don't know if I'd suggest 22.04 for people who care about stability. 20.04 still has 3 more yrs of support, provided you run the Gnome3 version.  The Xubuntu/Lubuntu/Kubuntu and most other DEs available from Canonical have 1 yr of support remaining, so you'll need to move to 22.04 **before** next April to stay supported if you don't use Gnome.

There are lots of important changes between every LTS release. But there's a year overlap, so when the next LTS is released, we don't need to be in a hurry to drop the prior version regardless of the Ubuntu flavor we choose to run.  The support rules for desktops can be a bit complicated. I'm running mostly 18.04 servers, which are still getting patches and officially supported for another year, but I will need to move to 20.04 or 22.04 THIS year to stay on a supported release. Servers get 5 yrs of standard support, which meets my needs.  Servers don't have GUIs, so they aren't suitable for desktop people.

I need to move my 18.04 desktop to a newer release. Many packages on it have lost support, since Canonical only supports the core repo packages, not every package in every repo or PPA.  If I needed a solution soon, before July, then I'd install a 100% fresh 20.04, then restore my data from backups. I wouldn't bring old settings for that desktop, but that's mainly because I've been migrating settings forward for a number of releases over the last decade and it is time to start fresh.  I'm having an issue where Firefox has the wrong timezone in javascript - it is off by 1 hour.  Nowhere else is this problem happening. No other GUI program and not in any terminal time output either. Even starting firefox in 'safe mode' doesn't correct the problem.  It is time to start fresh and work my way through the 30 or so customizations I've made all over again.  I'm positive some aren't necessary anymore and some will definitely be needed.

There's no perfectly correct answer. Sorry.  You'll not know until you make an attempt.  If you do need to fall back to the current setup for any reason, you'll want excellent backups, but really falling back to 16.04 isn't an option to be considered.

---

### Post by guiverc on 2022-05-01
As already outlined, Ubuntu 16.04 LTS reached the *end of it's five years standard support life* at the end of April 2021.

If your machine is offline, that's not really a concern.  If online however, that is a big concern.

I'll provide a NOTICE about ESM & warning that the five years of 16.04 (*released in 2016-April thus the 16.04*) that maybe helpful

[https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

> Ubuntu announced its 16.04 (Xenial Xerus) release almost 5 years ago, on  April 21, 2016. As with the earlier LTS releases, Ubuntu committed to  ongoing security and critical fixes for a period of 5 years. The  standard support period is now nearing its end and Ubuntu 16.04 LTS will  transition to Extended Security Maintenance (ESM) on Friday, April  30th, 2021.

Users are encouraged to evaluate and upgrade to our latest 20.04 LTS  release via 18.04 LTS. The supported upgrade path from Ubuntu 16.04 LTS  is via Ubuntu 18.04 LTS. Instructions and caveats for the upgrades may  be found ...

If you're using ESM on your Ubuntu 16.04 system, then don't forget not the whole system is supported; and many packages that were provided initially via *deb* package are now only *supported* (ie. patched for security flaws) once converted to *snap* package.  See [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04) etc.

I would suggest taking notice of notices, and don't forget 16.04 tells you it was the 2016-April release (*easy given the year.month format of releases*) so just adding 5 to 2016 tells you it's EOL in 2021-April.  You can use the command

```
ubuntu-support-status
```

to view your security/support status on your existing system.

---

### Post by jooa0ky on 2022-05-02
> **guiverc said:**
> As already outlined, Ubuntu 16.04 LTS reached the *end of it's five years standard support life* at the end of April 2021.

If your machine is offline, that's not really a concern.  If online however, that is a big concern.

I'll provide a NOTICE about ESM & warning that the five years of 16.04 (*released in 2016-April thus the 16.04*) that maybe helpful

[https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)



If you're using ESM on your Ubuntu 16.04 system, then don't forget not the whole system is supported; and many packages that were provided initially via *deb* package are now only *supported* (ie. patched for security flaws) once converted to *snap* package.  See [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04) etc.

I would suggest taking notice of notices, and don't forget 16.04 tells you it was the 2016-April release (*easy given the year.month format of releases*) so just adding 5 to 2016 tells you it's EOL in 2021-April.  You can use the command

```
ubuntu-support-status
```

to view your security/support status on your existing system.


Thank you everyone, that was very helpful. It seems like the consensus is to switch due to security concerns but here is the last hurdle I suppose?

Ok, so this is going to sound ridiculous but my rig that is running the 16.04 is running on a barebones system from back in 2015... the CPU is actually a pentium G3258 lol...

BUT, this desktop outperforms EVERY SINGLE ONE of my computers in my office. All of my office computers are running on intel i5s... They all run slower than my 16.04 g3258...


Kind of wanted to just see how far I can take this before the whole thing croaks. Looking the minimum requirements...
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)


I don't play any video games or do any heavy graphics processing, if I were to build a new desktop, what would be your barebones minimum pc parts?
I'm mostly just on the chrome browser to be quite honest. Blogging here and there but nothing graphics intensive.

---

### Post by Impavidus on 2022-05-02
I'm on an Intel i5-2410M from 2011, roughly similar to your CPU, and it works really well with Xubuntu 21.10. Don't worry about that CPU (although a light flavour may be better). Make sure you've got enough memory though. I've got 8GB.

Saying "just on the Chrome browser" is a bit misleading. It's one of the heaviest applications around. Much heavier than word processors, spreadsheet programs, image viewers etc.

---

### Post by TheFu on 2022-05-02
I have a G3258 that was recently retired to allow an upgrade what would let me retire 2 systems, not just one.  It is a fine desktop CPU and in 2015, it was a FANTASTIC value.  My system build around it was $126.  That's for the CPU, MB, and 8G of RAM.  I reused everything else.  

If the G3258 still meets your needs, I wouldn't change. We are on the cusp of the most expensive parts getting cheaper just now, while some other parts are going to become more expensive if you move the the next generation (DDR5 RAM).

I'm a fan of Ryzen CPUs.  Some of those come with quite excellent iGPUs, which will actually do light gaming and have built-in Linux support from 22.04.
Intel has some impressive mid-range CPUs too.

There is a huge difference in upgrade paths between Intel motherboards and AMD motherboards.  AMD keeps their sockets useful for 4-6 yrs and multiple lines of CPUs are compatible.  I know the Ryzen 2xxx - 5xxx series CPUs all work fine on an Asus B450 AM4 motherboard.  I have a 2600 CPU that for around $200 can almost double performance. If I want to spend more, even more performance is possible.  The low-end Ryzens like the 3100 are pretty impressive too, but harder to find and don't have an iGPU.  If you have a GPU already, that might not be important.  At one point, I remember seeing the 3100 for $79!  I should have bought it and built a system, but I needed a bit more performance for my VM workloads.  The 5600G is $180 now almost everywhere. I think it is the best value Ryzen today. I have one, but I paid $250 last fall for it, which was a deal at the time.

With Intel motherboards, the sockets change every 1-2 years, so CPU compatibility disappears much quicker.  That means that most Intel CPU upgrades will require swapping out the motherboard too - which is usually about $80-$150 more than the CPU alone.  Intel Core i5 and Core i3 CPUs really are very impressive, if the pricing is right.  

Every month or so, I used to create a chart in a spreadsheet showing the passmark vs $price for 4 and 6 core Desktop CPUs by Intel and AMD. Most of the time, the line is straight, with a few higher and lower bumps ... which I think of as market pricing mistakes.  I'd do some research on the lower-bump CPUs to decide if the difference made sense or not.

Just something to consider.  If you never upgrade CPUs and go for new hardware all the time, those considerations don't matter.

You don't need to be in a hurry. Take your time. You can shop for a few months and watch the deal websites for extra low prices.

Next year, all new computers/motherboard will be using DDR5. We've been on DDR4 the last 4-ish years.  This is forced obsolescence for very little improvement. For about another year, DDR4 RAM will be cheap (relatively), then it will be 'used' DDR4 RAM and prices will start going up for new.

---

### Post by jooa0ky on 2022-05-02
Pretty envious of your $126 build, if I recall correctly, mine came in at right around ~$300 at the time.

I started with windows and then moved onto a macbook but when that croaked I decided to give ubuntu a try since I didn't need to purchase a windows OS. Gotta say that was the best decision I've ever made.

I guess I don't really upgrade CPUs since I'm still using the same one from 2015 lol.


Overall, its been like 7 years and I could justify a completely new hardware but I'm still really curious as to for how long can this thing keep running. Maybe I'll keep it on the side as a case study lol.

I think I'll give the Ryzen a try... the gpu pricing still seems a bit ridiculous.

---

### Post by jooa0ky on 2022-05-02
> **Impavidus said:**
> I'm on an Intel i5-2410M from 2011, roughly similar to your CPU, and it works really well with Xubuntu 21.10. Don't worry about that CPU (although a light flavour may be better). Make sure you've got enough memory though. I've got 8GB.

Saying "just on the Chrome browser" is a bit misleading. It's one of the heaviest applications around. Much heavier than word processors, spreadsheet programs, image viewers etc.


You're still running the same exact system from 2011?! Did you upgrade any hardware in between?

Noted on the chrome being a resource hog.

---

### Post by TheFu on 2022-05-02
> **jooa0ky said:**
> Pretty envious of your $126 build, if I recall correctly, mine came in at right around ~$300 at the time.

The CPU+MB was $100 as a bundle.  The MB is crap and the UEFI part never worked.  Booted with legacy BIOS which works fine.\
$26 for the RAM.  I didn't include tax ... that would be $134 all in. Didn't mean to mis-lead.  And I reused prior stuff ... case, PSU, storage, cables, everything.

I have a Core i5-750 from 2010 still running. It will be retired once I can figure out how to move the storage to a different box.  The place I'd like to put it already has ... 11 disks, so there isn't any more room there.  The other system which might accept it only has 6 SATA ports, but the I need to connect 8 MORE disks.  All these connections need to be eSATA or SATA or SAS.

I have a laptop with a Core i5-2xxx something. It is very slow, but the only system with a physical Windows install. It is heavy, slow, thick. The Radeon GPU can have issues at boot and sometimes a key will get stuck depressed and 100K repeats will show up "somewhere".  I have 1 virtual machine with Windows - that gets used for finance software and nothing else. It was a Windows7 Media Center to record TV for years, but some programs demand direct hardware access (video editors and HW recorders like the Haupauge 1515), so I keep the laptop around. The VM 7MC would refuse to playback any videos. MSFT check the GPU and if it was not a real GPU, it refused to even attempt to play any video. Of course, VLC on that same Windows VM could play all the files just fine. The laptop hasn't been booted in at least 3 months.  

I have some older systems (system really means components) that could be needed for specific hardware support like 5.25 inch floppy drives and SCSI ports and a parallel port for an old tape drive (QIC-250). By now, I'd expect all those tapes to have corruption, but someday I might want to fire up DesqView/X, right?  

I really need to see if OS/2 Warp will load into a VM. I bet it will fly even without access to a real GPU.

---

### Post by Impavidus on 2022-05-03
> **jooa0ky said:**
> You're still running the same exact system from 2011?! Did you upgrade any hardware in between?

I increased RAM from 3GB to 8GB and replaced the mouse after the left button broke. Other than that, still the original hardware.

---

### Post by jooa0ky on 2022-05-04
> **Impavidus said:**
> I increased RAM from 3GB to 8GB and replaced the mouse after the left button broke. Other than that, still the original hardware.

That's inspiring... I think I'm going to just find a way to back up all of my settings and just do the OS upgrade. I want to see if mine can last as long because so far I've found no faults with it...

As was stated in previous posts, I cannot upgrade from 16 to the newest. Do I just do a complete wipe going fresh with the newest LTS?

Or is it still possible to do the ugprade from

16LTS ~> 18 LTS ~> 20 LTS ~> 22 LTS

Definitely way slower but is it possible?

---

### Post by sudodus on 2022-05-04
> **jooa0ky said:**
> As was stated in previous posts, I cannot upgrade from 16 to the newest. Do I just do a complete wipe going fresh with the newest LTS?

Or is it still possible to do the ugprade from

16LTS ~> 18 LTS ~> 20 LTS ~> 22 LTS

Definitely way slower but is it possible?

I would definitely recommend a fresh installation.

If you are extremely lucky all 3 upgrades will succeed, but my experience is that there will be a few problems, that you might be able to solve, but there might also be some problem, that is too difficult to solve within reasonable time and effort.

A bonus with a fresh installation is that you add only extra tools, if/when you need them. That way you will get rid of a lot of old cruft, that you don't need. Of course you should also copy your personal data files from the backup. But this process is much faster and provides a better result. Believe me, I have tested both methods (release upgrading and fresh installation).

---

### Post by TheFu on 2022-05-04
I'm with sudodus' recommendation.  Every new LTS leaves cruft that the next LTS either has to use or ignore, but it won't be deleted, so when there ARE issues, which config files should be changed .... the ones from 12.04 or 16.04 or 20.04?  For example, the way that DNS resolution is handled has changed with each of those releases.  Network setups changed in 18.04, but the 16.04 version was retained, if an upgrade.  So the 18.04 system will have both the old and new configs.
[B][U]
It is time for a fresh install.[/U][/B]

Definitely copy your personal files and settings off. Bringing the files back should be fine.  For the settings, I'd be more cautious and bring them to a different userid on the system, try them out there, before moving them into the normal, main, userid.

BTW, I'm in a similar boat.  My desktop has been upgraded from 10.04. About 2 months after I installed 20.04, I was seeing all sorts of issues that I was able to trace back to incompatible personal settings.  Only my account was impacted. Everything worked fine on other accounts.  So I moved my personal data to a new account and selectively moved personal settings from the old account to the new one. That took a few months, since I didn't just sit down and run the 50 programs I use and figure out all the settings.  Firefox is the worst, since I have about 30 settings in their about:config DB that have no GUI view.  After I got all the settings migrated, I disabled the old account (left it there for a few months) while I really used the new account looking for issues.  Then it was time to make acnt1 --> acnt1-old and acnt2 --> acnt1.  Not something I'd suggest for GUI-only users, but not hard at all if you understand how users, groups, and file permissions work.

After all of that, I still had the cruft from all the prior LTS upgrades, so I wiped the system and did a fresh install of 20.04, this time the point was to clean up the system-wide cruft.  I have excellent backups (daily, versioned, 'pulled') which can be referenced to setup a new system like a prior one in about 45 minutes total. Because it was just a desktop, I didn't need to setup any 'server' processes besides monitoring, which was already working and a few firewall rules.  I did have to purge about 20 things that Canonical thinks we all need, which we don't - or I don't.  There are some core services that I choose different than what Canonical installs by default.  I purge a few systemd- addons like resolved, timesyncd, avahi, and replace them with a text file or chrony or nothing. Stuff like that. Most people just don't care.  I got tired of dns issues and incorrect time sync and runaway CPU from avahi, so those are all purged. .... along with nano. ;)

BTW, in 22.04, the firewall used can be either iptables-based or nftables-based. I get the feeling iptables will be completely deprecated in 24.04, but I don't know.  ufw can create either iptables or nftables rules, I understand.

---

### Post by jooa0ky on 2022-05-05
Thank you for all of the help everyone! Based on all of the responses.
- I will do a fresh install with 22.04
- I will actually keep the same hardware because some of you have inspired me that it could last even longer than what I anticipated.

---

### Post by TheFu on 2022-05-05
If this is SOLVED, please use the Thread Tools button at the top-right to mark it that way. Only the OP can do it.  There was some excellent information in this thread that would be good for others to find too.

Always remember, Linux is multi-user and it is trivial to have multiple user logins. Use those for trying new things out without harming your current account settings.

---

