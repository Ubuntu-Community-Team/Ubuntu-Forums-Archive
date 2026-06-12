---
title: "I want to upgrade from 18.04 to get to 21.04...what hurdles will confront me?"
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by Shobuz99 on 2021-10-19
Hi all

I want to upgrade my Ubuntu 18.04 LTS (64) to eventually get to 21.04 on my HP EliteBook 8460p.
I've been told that I should do it in steps, and I understand that.

1st I want to know if I have to go in small steps, like 18.04 LTS to 19.04 to 20.04 to 21.04, 
Or can I skip 19.04, and go to 20.04 and then 21.04? 

I've been an Ubuntu user since 2006 ver 6.10 and have upgraded to one whole LTS version in the past without many issues.
I've been told there are pros & cons to "skipping" versions now (with dependencies?).

I would also like to know what kind of issues I can possibly expect to see.

Of course, I will backup the existing 18.04 LTS before I do anything!

Thank you and I appreciate any help & firm advice.

Shobuz99

---

### Post by deadflowr on 2021-10-19
You can only go to 20.04 from 18.04.
And then you an only go to 21.04 from 20.04.
All other channels are now EOL and closed.
In a few weeks you might be able to jump from 20.04 to 22.04 when the update channel is in place and with using the development flag in the upgrade command.
> I would also like to know what kind of issues I can possibly expect to see.
You would have to read the Release Notes for each to determine what common known issues are faced during each versions upgrades.

---

### Post by Dennis N on 2021-10-19
I've upgraded from 18.04 LTS to 20.04 LTS on two machines in one step. Those were successful. 

Rules: 
1 - STS (short-term support) releases only upgrade to the following release  - regardless of whether it's an STS or LTS. They can't 'skip' an release.
2 - LTS releases can upgrade to **next** LTS, or the **first** supported STS.
Both your current version and target version for the upgrade must be still supported.

I believe you can possibly use "old-releases" repositories, and some here may advise how. You can ask.  I've never done it. 
 
If you want Ubuntu 21.10 with the newest gnome shell, you should do a new install.

---

### Post by ActionParsnip on 2021-10-19
I'd just upgrade to 20.04 then wait. 22.04 will be out in April next year (Codenamed "Jammy") and you can then upgrade direct from 20.04 to 22.04 as they Jammy is the next LTS from Focal (Ubuntu 20.04).

Personally I'd just wait for Jammy to come out. Buy a new SSD and install Jammy from USB. Feels like a new sweater. You can restore your user data from your backups

---

### Post by ActionParsnip on 2021-10-19
As with any large system change (Even going from 18.04 to 20.04) backup your data before starting then confirm you can restore the data on another system.

---

### Post by Shobuz99 on 2021-10-19
Thank you! deadflowr.

---

### Post by Shobuz99 on 2021-10-19
Thank you. Dennis N
I'll jump to 20.04 LTS and then wait for April to jump to 22.04 LTS.

---

### Post by grahammechanical on 2021-10-19
Open Software & Updates>Updates tab and set Notify me of new Ubuntu version to For Long Term Support versions and leave it there. In this way you can upgrade from 18.04 LTS to 20.04 LTS and then at the end of April 2022 upgrade further to 22.04 LTS. Stay on the Long Term Support versions.

Precautions? Back up any data you do not want to lose. Take the User Interface back to its default state as much as possible. Switch to using the open source video driver if you are at present using a proprietary video driver. If you are using applications installed through a PPA expect them not to work. May be they will. May be they wont. Expect the same thing for any application that was not installed through the Ubuntu software Center but by download from some web site. Update the OS before starting the Upgrade.

Regards

---

### Post by Shobuz99 on 2021-10-19
Thank you. ActionParsnip

I'll jump to 20.04 LTS and then wait for April to jump to 22.04 LTS.

I don't use the SSD. I ordered it with a 250 HDD with Windows 10.
I switched out the Windows 10 HDD and replaced it with my Ubuntu 18.04 250 HDD.

I WILL however try the USB version for install.
As always, I backup everything using Deja Dup that comes with the system. 
It works okay for me..

Thanks again
Shobuz99

---

### Post by Shobuz99 on 2021-10-19
Thank you grahmmechanical!
Advice accepted.

---

### Post by Impavidus on 2021-10-20
> **Dennis N said:**
> LTS releases can upgrade to **next** LTS, or the **next** STS.

It appears this rule was changed some time ago. Now it is: LTS releases can upgrade to the next LTS or to the next **supported** release. As 20.10 is no longer supported, 20.04 can upgrade to 21.04. As upgrades to the next LTS are only opened about 3 months after release, which is when the STS before that reaches end of life, the rule can even be stated as: Every release allows upgrades to the next supported release. So, currently you can go from 18.04 to 20.04, from 20.04 to 21.04 and from 21.04 to 21.10. When a release reaches end of life, it's upgrade path gets frozen, even if the upgrade target goes end of life too.

You can expect the upgrade from 20.04 to 22.04 in July 2022.

---

### Post by Dennis N on 2021-10-20
> It appears this rule was changed some time ago. Now it is: LTS releases can upgrade to the next LTS or to the next **supported** release.
It does say this in the line after the one you quoted. Please reread:
> LTS releases can upgrade to next LTS, or the next STS.
Both your current version and target version for the upgrade must be still supported.


---

### Post by Impavidus on 2021-10-21
Maybe you intended the same thing as I, but I interpreted it differently. To me, your statement reads as: "From an LTS release, you can upgrade to the next STS release as long as that's supported. When that STS release reaches end of life, no upgrade is available until the upgrade to the next LTS release is offered." My statement is: "From an LTS release, you can upgrade to the next STS release as long as that's supported. When that STS release reaches end of life, the upgrade target changes to the STS release after that."

---

### Post by guiverc on 2021-10-21
FYI:

As already stated; the two intended & fully-supported release steps are

(1) via every release
(2) from one LTS (eg. 18.04) to the next LTS **after** the .1 has been released; ie. 20.04.1 is out.

So you need to wait longer than after 22.04 is released, but a few months after that when 22.04.1 has been released the *gates* will open for upgrade (without the `-d` option already mentioned).


Also note:  You can upgrade from one LTS (eg. 20.04), to the next *non-EOL* release. Given 20.10 is EOL, and you can't upgrade to it, thus the upgrade tool will allow you to *release-upgrade* to the next non-LTS which currently is 21.04 (*which was mentioned as being possible*).  That is outside of *fully-supported* upgrade paths, however it is CI (*continuous integration)* tested, and there is a QA *testcase* for it, though only a fraction of the QA-testing effort goes into it, thus it's usually not advised.  This option was offered to you (ie. 20.04 to 21.04 currently, 20.04 to 21.10 soon), so whilst its possible and supported; it's more problematic than upgrade via all releases, or LTS to next LTS.

Refer [https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906](https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906) for schedule..   No 20.04.1 date is listed, but it'll come months later ([6 August for 20.04.1]("https://fridge.ubuntu.com/2020/08/06/ubuntu-20-04-1-lts-released/")), ie. it's not April without using the `-d` or development option.

You can *upgrade via re-install*, which is great for desktops. It's a *testcase* for Lubuntu which I love, as it allows me to switch from testing one release, to another & have my *favorite *music player (*not installed by default*) & music ready to go as I evaluate the re-install  (and I can QA-test *hirsute* (21.04), *focal* (or 20.04.3 most recently), *impish* (21.10) & back to *focal* etc.. It's not perfect (*QA-tested only with Ubuntu repository software, and with some jumps, eg. prior to 20.04 Qt4 & python2 software was removed due EOL* *means error messages can be expected for some packages that users find disconcerting*) but I still love it.

fyi:  I may have used it in QA-tested with [18.04.6 ]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/")recently, but I was testing *bionic* much for that release as *flavors* had already reached EOL with *bionic*.

---

### Post by Dennis N on 2021-10-21
> **Impavidus said:**
> Maybe you intended the same thing as I, but I interpreted it differently...."

You are right. You can skip over a STS release when starting with the LTS. So I see my 20.04 is offering a direct upgrade to 21.04, but not to 21.10 - even though 21.10 is also supported. I assume when 21.04 is EOL, it will offer 20.04 direct upgrade to 21.10. Very nice.

I edited the original rule 2 in post 3 with "next" replaced by "first supported"

Thank you for the updated information. Some of us are still stuck in the past.

---

