---
title: "Unable to upgrade to Hirsute as invalid signature"
date: 2021-05-14
forum: Installation &amp; Upgrades
---

### Post by Automat2 on 2021-05-14
Hello,

I am trying to upgrade to Hirsute from Groovy via GUI and am unable to do so.

The installation process stops and shows the message below.

I have followed the steps from this [thread]("https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey") and installed y-ppa-manager -it discovered that I had one invalid ppa and two duplicate ones, but still find the message again.

[PHP]W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., W:GPG error: https://packages.riot.im/debian default InRelease: The following signatures were invalid: EXPKEYSIG C2850B265AC085BD riot.im packages <packages@riot.im>, E:The repository 'https://packages.riot.im/debian default InRelease' is not signed.[/PHP]

Please could somebody help me to upgrade to Hirsute or should I download the new version from the Ubuntu website and start from there?

Thank you kindly.

---

### Post by ajgreeny on 2021-05-14
It is usually important to disable, or better remove all PPAs before attempting an upgrade from version to version, and then add the PPA repos you need again after the upgrade.

I am fairly sure that the ppa:webupd8team has been completely discontinued so will no longer be of any use (unless it has been re-established recently) so I suggest that you forget that for now, remove any PPAs you have in groovy, upgrade by whatever means you wish.
Once upgraded see if the PPAs you previously used are available for hirsute and enable them if you need to.

I'm not sure if upgrades are being offered yet in the settings of the **software and upgrades** utility as I always clean install, and I run only LTS versions except for some VMs I have installed simply to check progress of the intermediate versions.

---

### Post by grahammechanical on 2021-05-14
I suggest that you uninstall the element desktop app and remove that riot.im repository from your sources.list file and then try to update. And reinstall Element desktop afterwards. You may find that riot.im does not yet have a version of element desktop for Ubuntu 21.04 and may wish to wait a bit longer on 20.10.

Regards

---

### Post by Automat2 on 2021-05-15
Thanks.

---

