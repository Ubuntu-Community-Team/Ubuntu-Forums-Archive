---
title: "Some annoyances in the 11.04 upgrade process"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by SeijiSensei on 2011-04-29
I'm posting this to suggest some improvements in the upgrade manager for future releases.  I had two machines running Kubuntu 10.10 with KDE 4.6.2 installed from backports.  I had the same experiences with both of them.

1)  ***The notification that the upgrade was available reappeared on my desktop much too frequently***.  Nor was there any way to tell the notifier to leave me alone for an extended period.  The notifier shouldn't appear more than once per hour, and it should have a button to disable or delay it.  I tried every possible thing I could find to disable the notifications in both KPackageKit and the Application and System Notification applet in System Settings.  I turned all the notifications off without success.

2)  ***The upgrade should use my repository preferences***.  I have a connection that maxes out at about 2.5 MByte/sec and have chosen a repository server that can sustain updates at that rate.  The upgrade appears to use some pre-designated server in the canonical.com domain which was clearly unable to handle the surge of traffic as thousands of machines updated worldwide.  If the problem is that the updates may not be available to all the repositories around the world, I'd suggest checking my preferred server for the upgrade before using some hard-coded alternative.

3)  ***The upgrader should defer any questions that the user must answer until the end of the upgrade process***.  One of my machines had three customized configuration files, e.g., /etc/ntp.conf, that prompted a query from the upgrader about whether I wanted to keep my custom file or install the new version.  In each case the entire installation process halted awaiting my answers.  This procedure makes it difficult to run an unattended upgrade.  The upgrade installer should place such questions in a queue and continue the upgrade process.  Require the user to answer the questions at the end of the process, then install the related packages at that time.

---

