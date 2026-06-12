---
title: "[SOLVED] Firefox add ons not being uninstalled (8.04)"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by dopple on 2008-05-26
Hi. I have recently upgraded to 8.04 and decided to uninstall firefox 3 and install firefox 2. None of my plugins were working so I did a complete removal and then reinstalled but to no avail.
When I try to uninstall the add ons I get an error (also when trying to "enable add onns")
Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

Error: uncaught exception: [Exception... "'[JavaScript Error: "installLocation has no properties" {file: "file:///usr/lib/firefox/components/nsExtensionManager.js" line: 3938}]' when calling method: [nsIExtensionManager::uninstallItem]"  nsresult: "0x80570021 (NS_ERROR_XPC_JAVASCRIPT_ERROR_WITH_DETAILS)"  location: "JS frame :: chrome://mozapps/content/extensions/extensions.js :: anonymous :: line 1696"  data: yes]

---

### Post by dopple on 2008-05-27
bump

---

### Post by Bubba64 on 2008-05-27
> **dopple said:**
> Hi. I have recently upgraded to 8.04 and decided to uninstall firefox 3 and install firefox 2. None of my plugins were working so I did a complete removal and then reinstalled but to no avail.
When I try to uninstall the add ons I get an error (also when trying to "enable add onns")
Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

Error: uncaught exception: [Exception... "'[JavaScript Error: "installLocation has no properties" {file: "file:///usr/lib/firefox/components/nsExtensionManager.js" line: 3938}]' when calling method: [nsIExtensionManager::uninstallItem]"  nsresult: "0x80570021 (NS_ERROR_XPC_JAVASCRIPT_ERROR_WITH_DETAILS)"  location: "JS frame :: chrome://mozapps/content/extensions/extensions.js :: anonymous :: line 1696"  data: yes]

Nightly tester tolls in the add ons of Mozilla will enable the plugins that are not working, install it then open add ons and click button on the bottom of the drop down.

---

### Post by dopple on 2008-05-27
Thanks Bubba. I'll check that out tonight!

---

### Post by CameO73 on 2008-05-27
It looks like your Firefox profile is corrupted. The best way to fix this, would be to use the [Profile Manager](http://kb.mozillazine.org/Profile_Manager).

In short, this means:

[LIST]
[*]Close all Firefox windows
[*][Alt]-[F2] and type **firefox -profilemanager**
[*]This will open the Profile Manager
[*]Use the 'Create'-button to create a new profile
[*](You could optionally delete the other profile)
[/LIST]
Good luck!

---

### Post by dopple on 2008-05-27
Thanks for all the help. I'll try creating a new profile and if I have no luck there I'll try using the Nightly Tester Tools add on (If I can install it).

---

### Post by Bubba64 on 2008-05-27
> **dopple said:**
> Thanks for all the help. I'll try creating a new profile and if I have no luck there I'll try using the Nightly Tester Tools add on (If I can install it).

A new profile may not keep your bookmarks or the plugins, but I am not sure, here is a link to NTL.
[https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools](https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools)

---

### Post by CameO73 on 2008-05-27
The bookmark problem can be easily solved by using the [Foxmarks]("http://www.foxmarks.com/") extension. This won't help you now, but it can help you backup and share bookmarks with multiple setups.

You could look for a **bookmarks.html** file in your old profile folder (something like ~/.mozilla/firefox/<some code>/bookmarks.html) which can be imported in FF2.

---

### Post by dopple on 2008-05-27
I use very few plugins and I only use google toolbars bookmarks so the new profile should be fine. I don't mind re-installing HTMLValidator and Stumble Upon.

---

### Post by dopple on 2008-05-27
Creating a new profile worked. I had to use firefox-2 -profilemanager as the "firefox" alias in Hardy is for Firefox v3.
Thanks

---

