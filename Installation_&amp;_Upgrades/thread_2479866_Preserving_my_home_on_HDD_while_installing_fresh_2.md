---
title: "Preserving my /home on HDD while installing fresh 22.04 on SSD"
date: 2022-10-11
forum: Installation &amp; Upgrades
---

### Post by jim-ruxton on 2022-10-11
I need to reinstall 22.04 on a dual boot machine (Windows and Ubuntu)  currently my Ubuntu system is on a partition on my SSD and my /home is on a partition on my HDD. Will I be able to preserve my /home on the HDD while installing a new 22.04 over a corrupted system on the SSD. How do I point the new install of 22.04 to /home on the HDD?

Thanks

---

### Post by guiverc on 2022-10-11
You didn't specify if you're asking about a Ubuntu Desktop 22.04 LTS re-install, or Ubuntu Server 22.04 LTS re-install.

Both `ubiquity` and `calamares` installer ISOs allow you to re-install without losing your existing data. In `ubiquity` it's using the *Something Else* option, with it called *Manual Partitioning* with the `calamares` installer used by two desktop *flavors*.  You just re-use the partition(s) you want & ensure you don't select **format **as it's the format (*for clean installs*) that causes loss of prior data.

You can in fact re-install a release (*assuming Desktop system*) and have it not touch your user data, plus have to re-install the *manually installed* packages (*ie. those packages you'd added from Ubuntu repositories post-install*) automatically if the exist in Ubuntu repositories for the re-installed system & internet is available during the install too.  I use that weekly to re-install a system as part of QA (*Quality Assurance*) procedures instead of perform normal system upgrades on the box I'm using now, as it achieves (*due to re-install*) the package upgrade (*where dailies are still being produced, ie. 22.04.2 is what I'd use, I can't do it any longer with 20.04 though as dailies have stopped now 20.04.5 has been released*), my *manually installed* packages get auto-reinstalled, and no data files are lost. I'll provide a link [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") where it's referred to as "*Install using existing partition*" as part of Lubuntu's QA; but it works with all Ubuntu Desktop & *flavors* (*using installers I mentioned; not yet for canary*).

How you do it will vary on installer; and you didn't specify which you'll use. The basic installer for a desktop system is `ubiquity`, but the 22.04 default installer for server is `subiquity`. Ubuntu *flavors* can also use `calamares`. Alternate (*testing*) ISOs existed with the *canary desktop installer* but I'd avoid using that (*that would be hard to find, if it still exists*).  For Ubuntu 22.04 LTS Desktop use the "*Something else*" option, re-use the partition & **do not format***.*

---

### Post by jim-ruxton on 2022-10-11
Thanks this information was very helpful.. The only way I got back to a working system was a fresh install. I was able to save my home partition using the advice above.

---

