---
title: "Icon for updates in task bar don't appears..."
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by xingular on 2010-05-20
Hi!

Has Ubuntu a tray icon for updates when this are available?

In 9.10 and now in 10.04 when an update appears in Update Manager nothing appears in task bar. (Like Windows Update or Mint).

I have enabled the options for this in Update Manager Settings... (Search Updates daily) but... 

It's normal? Something wrong?

Many thanks.

---

### Post by plucky on 2010-05-20
> **xingular said:**
> Hi!

Has Ubuntu a tray icon for updates when this are available?

In 9.10 and now in 10.04 when an update appears in Update Manager nothing appears in task bar. (Like Windows Update or Mint).

I have enabled the options for this in Update Manager Settings... (Search Updates daily) but... 

It's normal? Something wrong?

Many thanks.

The behaviour of update manager was changed in Jaunty(from the release notes)

> Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

It will now put an Update Manager window in the window list every day for security related updates,and weekly for recommended updates.

Good Luck

---

### Post by xingular on 2010-05-20
Another person recommends me "update-notifier" in Synapitc. 

First I will try with gconftool -s --type bool /apps/update-notifier/auto_launch false

Later with update-notifier.

Stay tune :P and thanks.

---

