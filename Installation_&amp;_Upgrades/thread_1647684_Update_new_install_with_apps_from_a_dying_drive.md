---
title: "Update new install with apps from a dying drive?"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by SylentO on 2010-12-17
Any assistance would be greatly appreciated! I had an old laptop (POS) with Lucid installed. I was updating to Maverick via Update manager. Well, I had a feeling my HDD was failing but it finally bit the dust on me, and the laptop never booted up properly after the update... I then put together a new laptop with a new drive, I can connect my old drive via USB to the new Lappy, and pull any essential data over to the new system, my question is....
How do I import the list of apps I used to run into the new lappy, to have Aptitude or apt pull down and reload everything I "was" using? I figure there is a simple way, just not sure how to do it from a non-running distro via usb connection.... Any advice??

---

### Post by gmargo on 2010-12-17
All the data on what packages are installed is contained under the **/var/lib/dpkg/** directory.

It's all in the **status** file - every installed package has the word "installed" on it's Status: line.

However, it's probably easiest to just get the directory listing of the **/var/lib/dpkg/info/** directory.  Just look at all the files named *.list:
```

cd ..../var/lib/dpkg/info
ls *.list | sed 's/\.list$//'

```

---

### Post by SylentO on 2010-12-20
Thanks ever so greatly gmargo! That's exactly what I was needing.. Thank again, and happy holidays to you and yours.

---

