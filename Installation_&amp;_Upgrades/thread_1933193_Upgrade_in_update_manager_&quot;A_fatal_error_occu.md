---
title: "Upgrade in update manager: &quot;A fatal error occurred&quot;"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by Kirus on 2012-02-28
Greetings everyone!

When trying to upgrade my Kubuntu system from 10.04 to 10.10, I get the following error (i've attached the suggested log files). Is it a known bug? Is there a sollution?

Thanks in advance.

K


-- message ----
A fatal error occurred

Please report this as a bug (if you haven't already) and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade has aborted.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.


 Traceback (most recent call last):

  File "/tmp/tmp4UtdNa/maverick", line 7, in <module>
    sys.exit(main())

  File "/tmp/tmp4UtdNa/DistUpgradeMain.py", line 158, in main
    if app.run():

  File "/tmp/tmp4UtdNa/DistUpgradeController.py", line 1616, in run
    return self.fullUpgrade()

  File "/tmp/tmp4UtdNa/DistUpgradeController.py", line 1534, in fullUpgrade
    if not self.updateSourcesList():

  File "/tmp/tmp4UtdNa/DistUpgradeController.py", line 664, in updateSourcesList
    if not self.rewriteSourcesList(mirror_check=True):

  File "/tmp/tmp4UtdNa/DistUpgradeController.py", line 486, in rewriteSourcesList
    distro.get_sources(self.sources)

  File "/tmp/tmp4UtdNa/distro.py", line 103, in get_sources
    source.template.official == True and

AttributeError: 'Template' object has no attribute 'official'

[ATTACH]213434[/ATTACH]

[ATTACH]213435[/ATTACH]

---

### Post by LinuxFan999 on 2012-02-28
upgrading through the update manager is not recommended. Burn a CD of the version of Ubuntu you want to upgrade too. Then, back up your data and do a clean install with the CD you burned.

Kubuntu 10.10 will be supported for only 2 more months, so I would recommend going to 11.04.

---

