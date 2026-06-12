---
title: "No desktop UI after upgrading to 24.04.1 LTS"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by mimetown on 2024-10-11
Hi all! 

I recently upgraded to 24.04.1 from 22 something and following the upgrade I don't seem to have access to the desktop UI. The GRUB menu's there and I'm able to log in but I only have a full screen terminal window available. I'm able to cd into folders and everything's still there, just no desktop UI. 

It seems like a few other people in the forum and on Reddit were able to solve a similar issue by running sudo apt install --reinstall ubuntu-desktop but when I try that I get a lot of "failed to fetch" errors saying that there's a temporary failure resolving.

So I think this method MIGHT work if I'm able to connect to the internet via command line or resolve whatever network issues I'm having. In an attempt to do that I followed the steps in another post and ran sudo iwlist wlp3s0 s but got "Interface doesn't support scanning : Network is down" and running "sudo ifconfig wlp3s0 up" returns "sudo: ifconfig: command not found"

I'm not super sure where to go from here, or if trying to reinstall this way is even my best bet. Full disclosure, I'm an ultra newb!

---

### Post by hifron on 2024-10-12
try dhclient with cable

but OEM install or upgrade maybe detected:

[FONT=Ubuntu]GNOME Initial Setup is triggered when no existing user account is detected and can be configured by specifying oem mode in [/FONT][an autoinstall config]("https://github.com/canonical/ubuntu-desktop-provision/blob/main/docs/oem-provisioning-24_04_1.md")[FONT=Ubuntu]. This flow now has added Ubuntu branding for a more consistent experience, an optional EULA pdf view, machine hostname configuration and improved keyboard navigation.

source: [/FONT]https://discourse.ubuntu.com/t/ubuntu-desktop-s-24-10-dev-cycle-part-3-july-update/46337

---

