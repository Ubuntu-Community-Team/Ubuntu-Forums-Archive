---
title: "How do I get update-manager and synaptic to agree?"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by Dis-appointed on 2011-04-24
Is it possible to get them to show the same result.

update-manager says I need 315 files @ 302mb to download
synaptic says 315 @ 318mb (using "mark all upgrades" button, then going the summary via the apply button )

this is on a machine with a clean install of maverick without anything new installed/changed from the defaults. Are these the same 315 packages and is it just a discrepancy in the way they calculate the size?

I used "sudo apt-get dist-upgrade -s --print-uris > upgrade.txt" to get me the same 315 packages, but unfortunately it seems the simulation switch (-s) stops it from actually printing the uris (which would include the size info) so no help in trying to establish where/what the discrepancy is.

This is just the 1st step in me understanding the whole process so I can do what I outline in my long rambling post ([http://ubuntuforums.org/showthread.php?t=1736184](http://ubuntuforums.org/showthread.php?t=1736184)) Although the suggestion one person made will help resolve my issues. It doesn't help me to understand the process so I can achieve my other goals.

---

### Post by Paddy Landau on 2011-04-24
In Update Manager, use the Check button to update the list.
In Synaptic Package Manager, use the Reload button.

I imagine that the figures shown are not precise because of rounding calculations. It may also be that one calculates MiB and the other Mb. I really wouldn't worry about it.

---

### Post by Dis-appointed on 2011-04-24
> **Paddy Landau said:**
> In Update Manager, use the Check button to update the list.
In Synaptic Package Manager, use the Reload button.

I imagine that the figures shown are not precise because of rounding calculations. It may also be that one calculates MiB and the other Mb. I really wouldn't worry about it.

So I take it you're reasonable sure it's the same packages that they want to install/upgrade. Also that the apt-get option is a "dist-upgrade" and not just a "upgrade"?

---

### Post by Paddy Landau on 2011-04-24
Sorry, I missed that last bit.

A dist-upgrade will upgrade your package to the next distribution level, e.g. from 8.04 to 10.04 (or whatever the upgrade path is). A simple upgrade will keep your distribution intact, but update packages relevant to that package.

As far as I know, Synaptic Package Manager will only update the current distribution, not upgrade to the next one.

Update Manager, on the other hand, has two different buttons. Install Updates will stick to the current distribution, whereas a different button will upgrade to the next level.

If you want to upgrade to the next distribution, please first do a full update of all packages; back up all your data; reboot; and then upgrade.

---

### Post by Dis-appointed on 2011-04-29
Thanks for the info. And since the next release is out now. I get what you mean by a "different button will upgrade to the next level." :D And have since moved on with out worrying to much about the size differences.



However to clarify (or maybe muddy) what I was saying above.

update-manager and synaptic both wan't to upgrade 310 packages and installl 5 new ones. To get the same result with apt-get I had to specify the "dist-upgrade" not just "upgrade". apt-get -upgrade would not install the 5 new packages.

So it seems that "Distribution Upgrade" has different meanings depending on the context. I'd guess apt-get is somehow pegged to your current distribution. And that one of the software-sources settings changes that (and/or "the different button" supplied for an upgrade to the next release)

After a quick check now on 10.04  ... apt-get dist-upgrade only offers 9 packages for me to upgrade.
And 10.10 machine ... apt-get dist-upgrade has nothing to update
Both these are the same as what the respective update-managers say. (even though the other upgrade button is available )

---

