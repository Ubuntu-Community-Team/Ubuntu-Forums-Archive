---
title: "Enabling Backports causes &quot;Partial upgrade&quot; message"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by zaffod on 2008-09-01
Hi All. 

I'm running Gutsy on and AMD64 and recently enabled backports in synaptic. I was hoping to get recent releases of apps like avidemux and amarok via the repos. 

After enabling backports and clicking the update notification icon, I get a message saying:

 "Not all updates can be installed. Run a partial upgrade to install as many updates as possible."

Does any one know why this occurs and if it is stable / safe to do this partial upgrade?

I had an issue doing a dist upgrade from feisty to gutsy and ended up having to reinstall from scratch. I don't want to this again, not right now anyway. 

Any opinions or ideas?

---

### Post by Cheesehead on 2008-09-01
Honestly, if you need a reliable system for work or school, then *disable* backports.

If you enable backports, if you want bleeding-edge, you must be prepared to make decisions like this. Where are you willing to accept risk?

Look through the list of upgrades. What else depends on them? Then decide if you want the upgrade.

You can still get upgrades...but you have to choose them carefully, enable backports - upgrade - disable backports.

---

### Post by zaffod on 2008-09-01
Fair enough Cheesehead. But I want a stable system where i can use the latest versions of applications. 

Example: 
Virtualbox has been updated since Sun bought them, but the Gutsy repos still use the old Innotek version. 
In this case, I was able to uninstall the old version from Synaptic and install the latest deb file from Sun. 

But I could **not** do this with Avidemux. Their latest deb file (for hardy) failed to install due to failed dependencies. eg, libcairo2 failed as a dep even though it is installed (confirmed from Synaptic). 

This issue may occur with other apps. 

SO, how can I keep a stable system yet use recent apps?

Do I have to do a dist-upgrade each time? That's painful!

I don't recall redhat having this problem - is it a debian thing?

---

### Post by Cheesehead on 2008-09-02
You can't have both 'a stable system' and 'the latest versions'. Updating to the latest versions will compromise your stability.

The best compromise is the every-six-month dist-upgrade when the entire distro is updated.

If you want to upgrade more often, then enable backports for one day, upgrade, then disable backports again. But you will need to resolve these dependency issues yourself (backports is unsupported).

As long as you have plenty of free time and skill at taking notes on your actions, you can always *try* the upgraded dependency, and see if anything breaks that you care about. You can always revert to the older version.

Or you can run two partitions, 'stable' and 'testing'. Keep your work and play separate.

---

### Post by Oldsoldier2003 on 2008-09-02
> **zaffod said:**
> Fair enough Cheesehead. But I want a stable system where i can use the latest versions of applications. 

Example: 
Virtualbox has been updated since Sun bought them, but the Gutsy repos still use the old Innotek version. 
In this case, I was able to uninstall the old version from Synaptic and install the latest deb file from Sun. 

But I could **not** do this with Avidemux. Their latest deb file (for hardy) failed to install due to failed dependencies. eg, libcairo2 failed as a dep even though it is installed (confirmed from Synaptic). 

This issue may occur with other apps. 

SO, how can I keep a stable system yet use recent apps?

Do I have to do a dist-upgrade each time? That's painful!

I don't recall redhat having this problem - is it a debian thing?

Read [this]("https://wiki.ubuntu.com/StableReleaseUpdates") for an explanation of why the repos are locked. If you want the latest versions you can always compile them from source. Backports is an option as well, though like it has been said before you could experience issues by enabling the backports repo.

---

### Post by zaffod on 2008-09-02
Thanks guys, I understand the issue better now, but I still think that we *should* be able to use any app version independent of the OS version. Perhaps that's just my old Windows mentallity. 

Anyway, can you kickstart on how to > "run two partitions, 'stable' and 'testing'. Keep your work and play separate."? I'm willing to try this for testing.

Maybe just a link or a highlevel description on how this would work / be set up?

---

