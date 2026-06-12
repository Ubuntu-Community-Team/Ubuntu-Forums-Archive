---
title: "update manager and apt-get fail after Hardy upgrade"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by calodar on 2008-04-30
I tried to run the Hardy upgrade, and it finished fetching files and installing them, but then said that due to an error it would not proceed with the upgrade and that my computer would be restored back to the way it was. But upon restart the computer I was running hardy with no apparent problems until today when updat manager and apt-get both give me this error:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing libsasl2-modules-gssapi-mit (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

How can I fix this?

---

### Post by El King on 2008-04-30
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
maybe this cud help

---

### Post by calodar on 2008-04-30
Sadly, I can't even attempt some of those tips because apt-get won't even run due to the above error. The stuff I could do didn't help anything.

---

### Post by El King on 2008-04-30
Maybe the cache is small, u can try to fix it with this:
```
sudo gedit /etc/apt/apt.conf
```
add the following line
```
APT::Cache-Limit "8388608";
```

Also try that:
```
sudo apt-get -f install
```

```
sudo apt-get clean
sudo apt-get update
```

If above fails, try this
```

sudo cd /var/lib/dpkg
sudo cp status status-bkp
sudo cp status-old status
```

---

