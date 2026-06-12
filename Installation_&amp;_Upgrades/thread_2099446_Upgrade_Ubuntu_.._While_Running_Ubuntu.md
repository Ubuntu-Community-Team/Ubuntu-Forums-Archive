---
title: "Upgrade Ubuntu .. While Running Ubuntu?"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by Snowfox815 on 2012-12-29
[CENTER]I'm still a little new to the whole Linux dealieo.. But anyways I installed Ubuntu 12.04 and never really messed with it till now. Is it possible to just upgrade to 12.10 through the "Update Manager"?

Sure hope so,
*Snowfox*
;)
[/CENTER]

---

### Post by ibjsb4 on 2012-12-29
Yep

[https://help.ubuntu.com/community/QuantalUpgrades](https://help.ubuntu.com/community/QuantalUpgrades)

You do realize that 12o4 is an LTS (long term support) release and supported for 5 years and 12.10 is not.

---

### Post by monkeybrain2012 on 2012-12-29
> **Snowfox815 said:**
> [CENTER]I'm still a little new to the whole Linux dealieo.. But anyways I installed Ubuntu 12.04 and never really messed with it till now. Is it possible to just upgrade to 12.10 through the "Update Manager"?

Sure hope so,
*Snowfox*
;)
[/CENTER]

Yes, but I suggest a clean install instead unless you want to test the upgrade mechanism and file bugs. Upgrade takes a lot longer and it tends to problematic.

---

### Post by Mark Phelps on 2012-12-30
> **Snowfox815 said:**
> [CENTER]I'm still a little new to the whole Linux dealieo.. But anyways I installed Ubuntu 12.04 and never really messed with it till now. Is it possible to just upgrade to 12.10 through the "Update Manager"?

Sure hope so,
*Snowfox*
;)
[/CENTER]

Yes ... it is possible.

But, that said, you need to know that there is no "rollback" option, that is, if something goes terribly wrong with the upgrade, there is no way to restore the working 12.04 version.  Instead, you have to do a complete reinstall of 12.04 from scratch.

Which is one very good reason why you should always "TRY" a new version before forcing an upgrade.

---

### Post by grahammechanical on 2012-12-30
In Software Sources you will find a place where you can tell Update Manager to notify you of the next release of Ubuntu. At the moment it is most probably set to notify you of the next LTS release. If you change that to next Ubuntu release, then Update Manager will give you a button to click to start the upgrade.

Upgrades work best from one default version of Ubuntu to the next version. That is what they are designed to do. Problems occur, in my opinion, when the OS has been heavily modified. The developers have no way of knowing what modifications each of us have done. So, it is next to impossible for them to take evasive action to avoid problems. This is why we recommend a fresh install.

Regards.

P.S. make sure that Ubuntu is up to date with its updates before you start the upgrade. That is also recommended. And read the release notes:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop")

Look for Known Issues. One of them might apply to you.

> **Upgrading from Ubuntu 12.04 LTS**
To upgrade from Ubuntu 12.04 LTS on a desktop system

Open Software Sources.
Switch to the Updates tab and set Notify me of a new Ubuntu version to For any new version.
Run Update Manager
It should display the following message: "New distribution release '12.10' is available".
Click Upgrade and follow the on-screen instructions.

---

