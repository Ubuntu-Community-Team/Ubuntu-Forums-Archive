---
title: "Upgrading to Ubuntu 24.04"
date: 2024-09-13
forum: Installation &amp; Upgrades
---

### Post by richaq on 2024-09-13
I receintly installed ubuntu 23.04 on to a flash drive.  I tried to do this with destro 24.04 but didn't have enough system ram a successful instal.
When I went to upgrade the distro 23.04  I said that it not possible to  do so.
Is there any thing else I can do to work around this?

---

### Post by 1fallen on 2024-09-13
What are your Specs on the machine now?
```
inxi -Cm

```

---

### Post by Dennis N on 2024-09-13
> **richaq said:**
> I receintly installed ubuntu 23.04 on to a flash drive.  I tried to do this with destro 24.04 but didn't have enough system ram a successful instal.
When I went to upgrade the distro 23.04  I said that it not possible to  do so.
Is there any thing else I can do to work around this?

Run the command **do-release-upgrade -c** in your terminal to see if a new release is available. The result I got in 23.04 is
```
dmn@Tyana-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

New release '24.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
 
```

The last part says 24.04.1 LTS is available, but If you run the command **sudo do-release-upgrade**, it will not complete the job it promised. It stops with:

```
Checking package manager
Can not upgrade 
An upgrade from 'lunar' to 'noble' is not supported with this tool. 

```

The options are use the upgrade information link and follow the instructions, or do an new install.

---

### Post by guiverc on 2024-09-13
The expected upgrade path for a 23.04 or *lunar* system was to the next release, ie. to *mantic* or Ubuntu 23.10 ( [https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades) )

That *expected* and *fully supported* upgrade path however disappeared when 23.10 went EOL ( [https://fridge.ubuntu.com/2024/07/17/ubuntu-23-10-mantic-minotaur-reached-end-of-life-on-july-11-2024/](https://fridge.ubuntu.com/2024/07/17/ubuntu-23-10-mantic-minotaur-reached-end-of-life-on-july-11-2024/) ) which makes it much harder for 23.04 users now, as you've left it too long.

The upgrade you've now got is from an EOL release, covered in [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

ie. its more *manual* as you're *too late* for the expected path.

In future, take note of what you're running and when it reaches EOL.  Ubuntu 23.04 tells you it's the 2023-April release (23.04 *means *2024-April) with 9 months of *supported life*, so it ended April+9 months or [2024-Jan]("https://fridge.ubuntu.com/2024/01/26/ubuntu-23-04-lunar-lobster-reached-end-of-life-on-january-25-2024/") with the *upgrade* still available for six months after that date, before its the more manual upgrade you have now (*unless the next release is a LTS, 23.10 wasn't*)

Some systems allow for *non-destructive *re-install, I did one in QA yesterday; but you don't mention any details except release (23.04; no Server/Desktop/flavor detail)

---

