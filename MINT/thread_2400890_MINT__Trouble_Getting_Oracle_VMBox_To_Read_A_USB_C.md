---
title: "MINT:  Trouble Getting Oracle VMBox To Read A USB CAC reader"
date: 2018-09-11
forum: MINT
---

### Post by tinker123 on 2018-09-11
I have one of the latest Mint versions on a very powerful computer just a few months old.

I have Oracle VMbox.

I have Windows 10 running in a virtual machine in Oracle VBBox.

I would like to work on my work computer from home.

My job requires a USB CAC ( Common Access Card, a smart card ) reader for this.

The set up directions for this are far easier on Windows than linux......hence my setting up of the virtual machine.

I had no problems getting an internet connection in Windows in the VM.  It was just there.


However, there was a point in the directions where the user is told to plug the USB CAC reader in and Windows would automatically get the appropriate drivers.   It didn't happen.  I check the update settings, it is supposed to happen.

I surfed around for a while on the issue and discovered I might have to configure Oracle VMBox to see the USB CAC reader first.

I found the options for this greyed out ( see attached screen shot ).

Any ideas of where I go from here?

Thanks either way

---

### Post by ajgreeny on 2018-09-11
What version of VBox did you install; I suggest the latest 5.2.18, and have you installed the Extension Pack [https://download.virtualbox.org/virtualbox/5.2.18/Oracle_VM_VirtualBox_Extension_Pack-5.2.18.vbox-extpack](https://download.virtualbox.org/virtualbox/5.2.18/Oracle_VM_VirtualBox_Extension_Pack-5.2.18.vbox-extpack) to get the Guest Additions of the same version, which may be all that is needed?

---

### Post by tinker123 on 2018-09-11
> **ajgreeny said:**
> What version of VBox did you install; I suggest the latest 5.2.18, and have you installed the Extension Pack [https://download.virtualbox.org/virtualbox/5.2.18/Oracle_VM_VirtualBox_Extension_Pack-5.2.18.vbox-extpack](https://download.virtualbox.org/virtualbox/5.2.18/Oracle_VM_VirtualBox_Extension_Pack-5.2.18.vbox-extpack) to get the Guest Additions of the same version, which may be all that is needed?

I have 5.1.38_Ubuntu r122592.

Its what is in the repository.   When I was in synaptic I saw the extension  pack for the same version and installed it.  Those USB options are no longer greyed out.

I don't know whether that will get the CAC reader going but I will give it a try.

Thanks much for the information.

---

