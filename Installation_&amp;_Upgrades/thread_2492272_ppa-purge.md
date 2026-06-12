---
title: "ppa-purge"
date: 2023-11-05
forum: Installation &amp; Upgrades
---

### Post by geeky-1 on 2023-11-05
I got the below error when trying to upgrade from 18.04.6 LTS to 20.04 LTS. How do I find out what software I need to ppa-purge?

```
An unresolvable problem occurred while calculating the upgrade.

 This was likely caused by:
 * Unofficial software packages not provided by Ubuntu
Please use the tool 'ppa-purge' from the ppa-purge 
package to remove software from a Launchpad PPA and 
try the upgrade again.

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If you want to investigate this yourself the log files in '/var/log/dist-upgrade' will contain details about the upgrade. Specifically, look at 'main.log' and 'apt.log
```

---

### Post by MAFoElffen on 2023-11-06
Well, you should "disable" all PPA's during a release upgrade... That does not necessarily mean that you need to use ppa-purge to remove the ppa and whatever was installed by it... That all is dependent on your own research ad what you really want to do.

This is what I would do.

Start up "Software and Updates" > Second Tab-- Other Software > Uncheck all PPA's... Do your go-release-upgrade.

Either before the release upgrade, or after the successful Release Upgrade, decide whether you want or need what was installed from that PPA. You may have to visit that PPA page at Launchpad to see if it has packages built for the release you are upgrading to. If not, then that decision for no, is already made right?

Install ppa-purge.
```

sudo apt install -y ppa-purge

```
It is not installed as a default.

To use ppa-purge, those checkboxes need to be checked on that PPA, if just even temporarily. Copy down the PPA name. Then go to your terminal and do this in this format
```

sudo ppa-purge ppa:<ppa_name>
# Example:
sudo ppa-purge ppa:deadsnakes

```
That will then remove the ppa and uninstall anything that was installed from that PPA... That can be done, either before or after the release upgrade.

If you did decide to leave a PPA through the release upgrade (unchecked during it), then recheck the checkbox. then after that, do
```

sudo apt update
sudo apt upgrade

```
and those packages installed from that PPA will be upgraded.

Need any more information on that?

---

