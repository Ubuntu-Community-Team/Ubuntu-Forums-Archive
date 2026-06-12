---
title: "Can I Mount Windows Striped Volume?"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by timbellomo on 2008-06-21
Hi All,

I've been looking around to see if I can mount my Windows Striped Volume (created under "Disk Management," not BIOS 'fakeraid') in Ubuntu.

I ran across a post that seemed to indicate I could mount the striped volume without much issues - so I backed up the most important stuff, wiped out Windows, and loaded up Hardy.  After battling (and losing) with my onboard VIA Rhine Ethernet controller, I decided to take on the striped volume.

Turns out, I totally misread the post - they were referring to a BIOS initiated "fakeraid," not a Windows "dynamic disk striped volume."  **So the question is:**

Is there a way to mount the Windows striped volume?  Or do I have to reinstall Windows, backup the striped volume completely, and then recreate the striped array with my BIOS util- wiping out the existing data- then subsequently configure it in Ubuntu with dmraid?

Run on much?  Sorry guys.  Let me know what you think.

Thanks,
Tim

---

