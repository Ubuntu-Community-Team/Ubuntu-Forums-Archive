---
title: "E: gtk-engines-eazel: installation problems"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by leeley on 2006-10-10
:confused: I have been running Dapper 6.06 LTS since it was in Alpha stage and never have had a problem. The MondaySeptember 25th I installed Edgy Eft Beta and everything went \\:D/ great:D not a problem what so ever. (This was a upgrade not a new install) Saturday October 7th when it went out and got an update it came back with this,
E: gtk-engines-eazel: subprocess post-installation script returned error exit status 2.
Any help would be aprecietated

Leeley[-o<

---

### Post by jerrybme on 2006-10-27
I just did a dist-upgrade from Dapper last night. I've got the same error. Although so far everything seems top be working. 

I tried removing it an reinstalling but continue with same error.

---

### Post by Jerim on 2006-10-27
I upgraded and my wireless disappeared. I am walking through the steps to set the wireless back up, and when I try to "sudo apt-get ndis-wrapper" it gives me this:

Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)

I went to the package manager, and tried reinstalling anything with eazel in the name, but all I get is:

E: gtk-engines-eazel: subprocess post-installation script returned error exit status 2

---

### Post by installer on 2006-10-29
This is an issue with me as well!

---

### Post by jamier on 2006-10-31
I'm having the same problem. Any help? :confused:

---

### Post by whitecrow on 2006-11-02
Okay, I have the same problem after a PACKAGE MANAGER UPGRADE from a fully updated dapper to edgy. I, too, tried to remove and re-install  gtk-engines-eazel with no success.  However, I have found that none of the  updated edgy programs (I don't know about the system files) have installed.  I don't have Firefox 2 or Tomboy, for instance.  The programs were downloaded but did not install.  When I try to install ANY software, I get the error about the gtk engine.  I wanted to try an upgrade rather than a clean install because upgrades seem to test the system more.  I suspect there is some conflict here but I don't have any clue as to what it might be.  Suggestions or do I simply have to clean install?

Whitecrow


> **Jerim said:**
> I upgraded and my wireless disappeared. I am walking through the steps to set the wireless back up, and when I try to "sudo apt-get ndis-wrapper" it gives me this:

Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)

I went to the package manager, and tried reinstalling anything with eazel in the name, but all I get is:

E: gtk-engines-eazel: subprocess post-installation script returned error exit status 2

---

### Post by whitecrow on 2006-11-04
Regarding the gtk-engines-eazel problem, I see that an Edgy bug report has been filed on this.  Perhaps no one has addressed the issue in this thread because everyone solved it.  However, I wanted to note that although I had removed and re-installed this gtk engine, I had not simply removed it from my system.  In preparation for this, I removed the Crux theme, which seemed to be associated with this engine.  Then, I removed gtk-engines-eazel using package manager. I rebooted and then found that all my applications were of the proper version and working fine.  I was also able to download, install and otherwise manipulate software.  The problem seems to be fixed but of course I no longer have access that particular theme.  I'm not bothered by this.  Any ideas what happened?

---

### Post by jamier on 2006-11-14
I'm still having problems with this. I can't update at all. Tried removing crux as well, nothing working. Any other ideas anyone?

Thank you!

---

### Post by jerrybme on 2006-11-15
I finally gave up, backed up my home directories and did a clean install. Drastic but I got tired on not being able to resolve the issue.

Cheers & good luck

---

