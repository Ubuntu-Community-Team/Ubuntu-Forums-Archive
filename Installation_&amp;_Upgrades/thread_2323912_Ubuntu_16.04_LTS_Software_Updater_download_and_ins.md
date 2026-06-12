---
title: "Ubuntu 16.04 LTS: Software Updater download and install update without permission"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2016-05-09
I notice my Ubuntu 16.04 LTS Software Updater is downloading and installing updates without my permission on several occasion even thought it is setup to only "Display Immediately" the updates. 
How do I rectify this problem? I want Software Updater to only display the updates to me and only to download and install the updates on my command.

Pls advice me what to do. Thanks.

---

### Post by QDR06VV9 on 2016-05-09
Have a look Here [https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)

---

### Post by grahammechanical on 2016-05-09
Before software Updater can display a notification that there are updates available it has to go online and access the software repositories and compare the package list on the machine with the package list on the server to see what has been upgraded. That process causes a fair bit of router activity.

Are you sure you are not seeing Software Updater performing its regular check for updates? If you do not want Software Updater to do even that task then, go to System Settings>Software & Updates>Updates tab and change "Automatically check for updates" to "Never."

Regards.

---

