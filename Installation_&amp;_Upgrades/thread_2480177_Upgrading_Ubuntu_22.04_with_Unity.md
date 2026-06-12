---
title: "Upgrading Ubuntu 22.04 with Unity"
date: 2022-10-21
forum: Installation &amp; Upgrades
---

### Post by eindgebruiker on 2022-10-21
I'm running Ubuntu 22.04 with Unity (i.e. with the ubuntu-unity-desktop package from universe).

What will happen if I upgrade to 22.10? Will I get the Ubuntu Unity flavour? If so, what will happen to the gnome-shell package and Gnome apps, will they be removed?

(From the Ubunty Unity website: *You can now install Ubuntu Unity on an existing Ubuntu install by removing gnome-shell and other GNOME apps, and then installing the ubuntu-unity-desktop package*)

---

### Post by TheFu on 2022-10-21
Before doing any upgrade, you need a 100% know-you-can-restore backup, so try it.  Doing an OS upgrade without a backup is crazy. Don't do that.

---

### Post by QIII on 2022-10-21
One thing that will happen with 22.10 is that you will be moving to a release that has only 9 months of support because it is not an LTS.

---

### Post by mIk3_08 on 2022-10-23
> **eindgebruiker said:**
> I'm running Ubuntu 22.04 with Unity (i.e. with the ubuntu-unity-desktop package from universe).
What will happen if I upgrade to 22.10? Will I get the Ubuntu Unity flavour? If so, what will happen to the gnome-shell package and Gnome apps, will they be removed?
 I'd rather stay in LTS (Long Term Support) release than under short term development release. Its kinda crazy but If you want to take risk then have a back up. Regards and cheers.

---

### Post by guiverc on 2022-10-23
> **eindgebruiker said:**
> I'm running Ubuntu 22.04 with Unity (i.e. with the ubuntu-unity-desktop package from universe).

What will happen if I upgrade to 22.10? Will I get the Ubuntu Unity flavour? If so, what will happen to the gnome-shell package and Gnome apps, will they be removed?


If you *release-upgrade* from 22.04 to 22.10, then I would expect you to be running the *official* Ubuntu Unity 22.10 release.

ie. you'll upgrade from [https://packages.ubuntu.com/jammy/ubuntu-unity-desktop](https://packages.ubuntu.com/jammy/ubuntu-unity-desktop) where the package was an *official *Ubuntu *universe* package, alas not a *flavor* package, to [https://packages.ubuntu.com/kinetic/ubuntu-unity-desktop](https://packages.ubuntu.com/kinetic/ubuntu-unity-desktop) which is both an *official *Ubuntu *universe* packagethat is managed by an *official *Ubuntu *flavor* team; ie. Ubuntu Unity.

If you only want your system to be an *official* flavor, I'm not sure it's worth it, as your system currently is an *official* Ubuntu system (*assuming a Ubuntu install with `ubuntu-unity-desktop` added*), even if it's not an *official Ubuntu Unity* system[I].

[/I]Note:  Before Ubuntu Unity was official, some packages used were available in PPAs or 3rd party repositories (*managed by the then unofficial team*), if your system contained some of those you may have complications in the *release-upgrade*, but you'll have to check as I really don't know. At the time of becoming *approved to be* official, I am aware that the *unofficial testing ISO* contained packages that had to be (a) dropped having come from PPAs, or (b) the team  *upload* via SRU (*stable release update*) those packages to official repositories which the team started doing. 

 FYI:  PPAs are not really a problem; they allow you to use later software than may exist in official repositories, but they can produce problems come *release-upgrade* time, so the general rule of thumb is those 3rd party (PPA) packages should be removed prior to *release-upgrade*, then them re-added post *release-upgrade* if still required when you're on the later release. Also note many teams use them, Kubuntu provide newer packages via backports PPA, Lubuntu have one too, etc  (*ie. they are a useful tool involving a lot less work than upload/SRU*)

*this is my opinion only, I have no special knowledge as I've not looked at the packages involved, basing it on general knowledge with other package/flavors.*

---

