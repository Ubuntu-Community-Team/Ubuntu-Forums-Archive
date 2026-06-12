---
title: "LTS upgrade not recognized"
date: 2022-05-06
forum: Installation &amp; Upgrades
---

### Post by cam17 on 2022-05-06
I am currently running 20.04 but when I open software updater it does not report that a LTS new version is available even though I have software & updates set to notify me.I did receive an update on May -4-2022.
 What could the reason be for not notifying myself?

---

### Post by guiverc on 2022-05-06
Ubuntu 22.04 LTS has been released, but the upgrade path from 20.04 to 22.04 has **not** been opened.

- [https://fridge.ubuntu.com/2022/04/21/ubuntu-22-04-lts-jammy-jellyfish-released/](https://fridge.ubuntu.com/2022/04/21/ubuntu-22-04-lts-jammy-jellyfish-released/)

At initial release; no upgrade path is opened, with the release referring to the ISO release for new installs. It's common for the *release-upgrade* path from the prior release (21.10 in this case) to be opened the following week; that path is now opened.

The release announcement I provided said the following

> Users of Ubuntu 21.10 will soon be offered an automatic upgrade to  22.04. Users of 20.04 LTS will be offered the automatic upgrade when  22.04.1 LTS is released, which is scheduled for the 4th of August. For  further information about upgrading, see:

ie. it suggested rather clearly, your system won't see the upgrade before 4th August 022, and in my experience it may not appear until **after** that date.

If you want more; I wrote an answer on [askubuntu]("https://askubuntu.com/questions/1403610/22-04-is-suggested-on-ubuntus-website-but-not-in-the-repository/1403615#1403615") which gives some of the mechanics of how the *Ubuntu Release team* control the upgrade process.  When I wrote that answer, the upgrade path from 21.10 to 22.04 wasn't yet opened thus the wording I used; the meta files I refer to have changed & the upgrade path is open - thus if I wrote that answer today; my wording would be slightly different.

You can *force* the upgrade using `-d`, but I'd suggest waiting unless you absolutely need to upgrade; as the delay is there for a reason.

FYI:  The Ubuntu 22.04 LTS release was the final release in a *development cycle* that started with Ubuntu 20.10, through 21.04 & 21.10; ie. your 20.04 system is the end of the prior *development* cycle thus has a far more significant change - thus the delay to ensure *stability*.  Ubuntu 20.04's *development cycle* started with Ubuntu 18.10.

---

### Post by grahammechanical on 2022-05-06
The reason is that Canonical will not open the upgrade path until six months after 22.04 was released. By then it will be Ubuntu 22.04.1.

> If you use Ubuntu 20.04 LTS you will **not** be notified  about the Ubuntu 22.04 upgrade until late July/August 2022. This is when  the first point release in the Jammy cycle is due for release. This  short delay is a standard practice aimed at maximising stability (which  is what an LTS is all about, after all).

[https://www.omgubuntu.co.uk/2022/04/how-to-upgrade-to-ubuntu-22-04-lts](https://www.omgubuntu.co.uk/2022/04/how-to-upgrade-to-ubuntu-22-04-lts)

If you see guides to upgrade to 22.04 on the internet be careful about following the instructions. There are guides out there that were written before 22.04 was released and they give instructions for upgrading 20.04 to 22.04 development version. Those instructions will no longer work as 22.04 is no longer a development version. Ubuntu 22.10 is now the development version.

Regards

---

### Post by cam17 on 2022-05-07
I have.20.04.4 LTS and I still not sure I understand. Ubuntu has other **non** LTS versions which I presume new features are derived so I would expect the LT version to be available fairly immediate.

---

### Post by guiverc on 2022-05-07
You're missing the where the cycle starts. It starts with the first .10 release post-release, and ends with the LTS release.  The prior LTS is from the prior cycle; thus is a *significant* change and is thus *delayed* until it's deemed *safe to upgrade*

Ubuntu 20.04 LTS was the completion of the *development* cycle that started with Ubuntu 18.10, then 19.04, 19.10 and finally 20.04 LTS.

Ubuntu 22.04 LTS is the conclusion of the *development* cycle that started with Ubuntu 20.10, then 21.04, 21.10 and finally concludes with Ubuntu 22.04 LTS.

Ubuntu 20.04 LTS was the final product from the **prior*** development* cycle; thus is a very big change and is *delayed* in upgrades as has always occurred.  The upgrades from prior releases within the *development* cycle are always first, as they've a *comparatively minor* change (ie. *21.10 was the prior release within that development cycle* *thus less risky*).

You've got the bigger change; as you're using the last *development* cycle LTS; the LTS being the ***final*** release in the prior *development* cycle.

Ubuntu 22.10 *development *has already started; it's the **first step towards the next LTS** release, with the *'**fruits' *of that work eventually being released in Ubuntu 24.04 LTS almost two years from now. Ubuntu 22.10 only relates to 22.04 (*or the prior cycle*) in that it wasn't started from scratch, but starts from the 22.04 product & all changes that had *frozen* due to *freezes* upstream (*when jammy was being tested, nothing flowed prior to release*) that have started flooding through.

---

### Post by Impavidus on 2022-05-08
The changes from 20.04 to 22.04 are larger than from 21.10 to 22.04. More to go wrong in an upgrade, more to test and more to fix, so after releasing 22.04, it takes some time before the upgrade process is released. Further, it's assumed that users of 20.04 want stability most of all, not quick access to the latest software. After all, users of 20.04 have been using an LTS release for 18 months despite there being a more recent release available. If 20.04 was preferred over 20.10, 21.04 and 21.10 for its stability, then surely you aren't in a hurry to upgrade to 22.04 before the upgrade process has been properly tested and a significant number of bugs has been fixed in 22.04.

---

### Post by grahammechanical on 2022-05-08
The Ubuntu 22.04 LTS ISO image was released for download on the appointed day. Those who have the latest hardware might benefit from downloading and installing Ubuntu 22.04 LTS to gain access to the latest Linux hardware drivers. You have Ubuntu 20.4.4. I think that your system will soon download the Linux firmware (drivers) package that is in Ubuntu 22.04, If the system has not already done that. So, if you are looking for drivers that were not available when you first installed 20.04 it may be that you already have the best that Linux developers can offer at the present time.

Regards

---

