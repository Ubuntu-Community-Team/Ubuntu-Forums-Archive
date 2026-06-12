---
title: "Why did Software Update just get rid of my non-SNAP version of Firefox?"
date: 2022-06-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-06-21
Apparently, whoever is in charge of Software Updater doesn't think I should be using the non-SNAP version of Firefox.  Non-SNAP version is mission-critical for use of PDF Studio Pro.

How do I get back non-SNAP version and keep Software Updater from removing it?

Thank you,

John

---

### Post by oldfred on 2022-06-21
Did you run the extra commands to pin the priority order.

Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

sudo snap remove firefox
 sudo add-apt-repository ppa:mozillateam/ppa
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox

echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
sudo apt install firefox

---

### Post by cigtoxdoc on 2022-06-22
Thank you, oldfred.  I have been using the launchpad version of non-snap Firefox, so I had to rework your suggestion for the launchpad ppa.

I use the 2020 and 2021 versions of PDF Studio Pro for reading scientific journal articles as well as editing manuscripts.  The snap version of Firefox causes an error when it tries to open a downloaded version of a PDF file using PDF Studio Pro. (PDF Studio Pro is a non-free Linux equivalent of Adobe Acrobat DC)

So, the question remains: How do I keep Software Updater from trying to change my Firefox?

John

---

### Post by oldfred on 2022-06-22
It was my understanding that the priority setting controls that.
Did you run the echo command to create this?

```
[FONT=monospace][COLOR=#54ff54]**fred@z97-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/apt/preferences.d/mozilla-firefox [/COLOR]

Package: * 
Pin: release o=LP-PPA-mozillateam 
Pin-Priority: 1001

[/FONT]
```

---

### Post by cigtoxdoc on 2022-06-22
Thank you. apt.d preferences are set correctly for the launchpad non-snap Firefox.  John

---

### Post by VMC on 2022-06-22
Do you still have snap installed for other applications? I removed snap totally and have never had issue.
I use this link to install non-snap Firefox. 
[h=1][[SIZE=2]Install Firefox from Mozilla builds (For advanced users)[/SIZE]]("https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users")[/h]

---

### Post by cigtoxdoc on 2022-06-22
Thank you, VMC.  I removed snapd using synaptic.  I rebooted and everything still working.

---

