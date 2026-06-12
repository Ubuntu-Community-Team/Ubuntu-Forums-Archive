---
title: "not getting prompt to upgrade to 13.10"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by draftpeppin on 2013-10-31
Hi,

I have two laptops running Ubuntu.  One gave me a prompt to upgrade to 13.10.  The other one still hasn't.  Currently runs 13.04.  In the Updater, I do have it set to notify me of updates daily, and also to notify me of ALL upgrades, not just LTS.

Any ideas?

Thanks,

Steve

---

### Post by warp99 on 2013-10-31
The prompt is broken in some systems, bug report has already been issued. I had to upgrade at the terminal.

```
sudo do-release-upgrade
```

---

### Post by draftpeppin on 2013-11-01
> **warp99 said:**
> The prompt is broken in some systems, bug report has already been issued. I had to upgrade at the terminal.

```
sudo do-release-upgrade
```

Thanks warp99.  I didn't know what search terms to use so I didn't know this was out there.  Didn't have any luck finding the info.  I'll be patient.

Steve

---

### Post by craig10x on 2013-11-02
Are you running only one ubuntu? if so, if you burn a disc of 13.10, and run it, the installer should give you the option to UPGRADE to 13.10 (in addition to the normal option to wipe out 13.04 and replace with 13.10)...try that! (works for me every time i have used it)...it's much faster and much more reliable then using either the software updater or terminal methods of upgrading...

---

### Post by vegan.philosophy on 2013-11-02
I also have not got any prompt to upgrade to saucy via software updater in spite of updating my system regularly. I will try to install saucy by downloading its image and burning it to DVD. A web page has recommended following commands to upgrade via terminal :

[B]sudo apt-get update && sudo apt-get dist-upgrade

[/B]sudo update-manager -d

Reference : [http://www.unixmen.com/upgrade-ubuntu-13-04-raring-ubuntu-13-10-saucy-salamander/](http://www.unixmen.com/upgrade-ubuntu-13-04-raring-ubuntu-13-10-saucy-salamander/)

Suggestion : Create a back-up of your files before upgrading Ubuntu.

---

