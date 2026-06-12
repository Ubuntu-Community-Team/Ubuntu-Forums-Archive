---
title: "VirtualBox Extension Installation Problem"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by vplobanov on 2014-03-27
When trying to install the expansion pack I keep getting this error: Failed to install the Extension Pack **/home/.../Oracle_VM_VirtualBox_Extension_Pack-4-3-8-92456.vbox-extpack**.VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=0000000000000000 ErrInfo='Helper version mismatch - expected 0x10001 got 0x10000'.
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]ExtPackManager[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}[/TD]
[/TR]
[/TABLE]

I have tried rebooting. Then I reinstalled, and rebooted again. I received the same error message now as in the beginning. I have the guest additions expansion downloaded as well. Earlier I had this expansion pack working, and 2 USBs were connected (which was my main goal). I then downloaded the guest connection so as to enable an easy file sharing system between the guest and host.

Alternatively, is it possible, without the virtualbox extension, to create a shared folder between a linux host and windiows guest?

Thanks!

---

### Post by ajgreeny on 2014-03-27
What version of VB are you using at the moment?  There have been two very recent updates from 4.3.8 to 4.3.10, so your extension package may be too old for your version of VB.

As to your final question, I am sure you must have the guest additions installed in the guest to share folders and clipboard, no matter what the host and guest may be.

Go to the VB website download page [Downloads &#8211; Oracle VM VirtualBox]("https://www.virtualbox.org/wiki/Downloads") and check out your guest additions version, then download again if you need to.

---

