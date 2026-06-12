---
title: "No upgrade to Ubuntu 22.04 is shown in Update Manager"
date: 2022-04-24
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2022-04-24
Following the instructions [here]("https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start"), I start the update manager, look at the settings, they are all good, restart the update manager, and it doesn't show the upgrade being available in spite of the web site informing me that it is.  Grrrr.

Oh, and I'm running Ubuntu 21.10 now.

---

### Post by oldos2er on 2022-04-24
According to the [release notes]("https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668/1") the upgrade has been held back a couple days.

---

### Post by grahammechanical on 2022-04-24
Did you see this?

> **Upgrades to 22.04 LTS are currently not enabled (due a bug with  snapd and update-notifier) but will be in the next couple of days.**

[https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)

Personally, I would not take "couple of days" literally. I have been running 22.04 for much of its development period. There are always updates every day. But for several days before the release date there weren't any updates. It is now a few days since the release date and there are still not any updates. This is unusual. What it means I do not know.

Regards

---

### Post by Impavidus on 2022-04-24
It's normal that this takes a couple of days, maybe a week. Sometimes it takes quite a bit longer; I remember some versions back when it took over a month before the release upgrade was available.

Upgrades from 20.04 will have to wait even longer; don't expect them before end of July.

Relax, 21.10 still has 3 months of support left.

---

### Post by peyre on 2022-04-26
So is this why my Xubuntu machines don't offer upgrades to 22.04?  It's been close to a week since release; I can download ISOs and everything.  

If only I could upgrade using the ISOs, like I used to be able to do with the Alternate CDs.  I have tried adding the newly burned 22.04 DVD to my sources (using the Add Volume button in the Other Software tab).  It then says it has a 3.4MB update to the Ubuntu base, but when I tell it to Install Now, it insists I insert the DVD "into the drive '/media/cdrom/'".  I unmounted the disk and set the Disks utility to mount optical drives with Mount Point /media/cdrom/, but it still insists I insert the disk *where it's already inserted* and it won't go any farther.

---

### Post by irv on 2022-04-26
I did download the iso and made a USB boot disk and installed it on two laptops, but can't do the upgrade on my desktop. When I do a sudo update-manager from the prompt, it wants to upgrade my 20.04 to 21.10 because it doesn't see the 22.04 because it is still not out there. Will wait a while longer.

---

### Post by peyre on 2022-04-26
Thanks, Irv!  As long as I know it just isn't ready yet, it's all good.  I'll hang tight for now then.

---

### Post by sudodus on 2022-04-26
[This link](https://askubuntu.com/questions/1018033/ubuntu-development-version-how-to-participate-or-how-to-get-a-smooth-ride) may add some things to consider before deciding to upgrade to a new [LTS] release.

It was written some years ago, but applies to 22.04 LTS now. For example scroll down to the paragraph 'If you want a smooth ride'.

---

### Post by peyre on 2022-04-26
Thanks for the link.  My two laptops run the latest version so I can see and enjoy the latest, since rebuilding one of those wouldn't be a big task.  My desktop is my main computer though and rebuilding that *would* be a big hairy deal--so it runs the LTS.  I've actually been a bit anxious about the upcoming upgrade to 22.04, since my desktop has failed upgrades in the past (when I was tempted to install the latest version), and my video card may no longer be supported (it's an old NVidia card, but works fine for everything I need).

---

### Post by peyre on 2022-04-27
Ah, it's just offered me an upgrade.  I'll try it on one of my laptops.

Edit: Seems to have worked!

---

### Post by grahammechanical on 2022-04-27
> my video card may no longer be supported (it's an old NVidia card, but works fine for everything I need).

Revert to using the open source video driver. And make sure that you are logging to X.org. Ubuntu 22.04 should default to using Wayland but there seems to be a problem with Nvidia drivers.

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243)

[https://ubuntuforums.org/showthread.php?t=2473861](https://ubuntuforums.org/showthread.php?t=2473861)

I have no way of knowing if this is fixed as I am running on Intel graphics.

Regards

---

### Post by peyre on 2022-04-27
Oh, ugh, back to Nouveau?  That kept crashing my desktop, or summarily logging me out, at unpredictable moments.

Might be time to purchase a new video card soon--and probably an AMD this time.

---

### Post by guiverc on 2022-04-27
I'll provide a link to an answer I wrote on *askubu* on how `do-release-upgrade` works & the *metafiles* it uses that are controlled by the *Ubuntu Release* team to ensure existing Ubuntu users get keep a *stable* system.

[https://askubuntu.com/questions/1403610/22-04-is-suggested-on-ubuntus-website-but-not-in-the-repository/1403615#1403615](https://askubuntu.com/questions/1403610/22-04-is-suggested-on-ubuntus-website-but-not-in-the-repository/1403615#1403615)

It maybe helpful for background knowledge.

*Note:  the article was written just after release; and my wording assumed it was ~hours post-release... It's now the following week so I'd use different word if written today.*

---

