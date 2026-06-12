---
title: "Possible problem with flash plugin update in 16.04"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by uli9 on 2016-05-12
Software updater showed a Adobe flash plugin update. I did that. Was then asked to reboot. After that everything seemed fine, no messages.
Then I started an app with gksu in terminal. All of a sudden some text appears in the terminal:

1463085977937    addons.update-checker    WARN    Update manifest for [email]e10srollout@mozilla.org[/email] did not contain an updates property
1463085978016    addons.update-checker    WARN    Update manifest for [email]firefox@getpocket.com[/email] did not contain an updates property
1463085978101    addons.update-checker    WARN    Update manifest for {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
1463085978241    addons.update-checker    WARN    Update manifest for [email]ubufox@ubuntu.com[/email] did not contain an updates property
1463085981969    addons.xpi    ERROR    Failed to clean updated system add-ons directories.: Unix error 2 during operation DirectoryIterator.prototype.next on file /root/.mozilla/firefox/9egkwca3.default/features (No such file or directory) ((unknown module)) No traceback available
1463085990120    addons.xpi    ERROR    Attempted to load bootstrap scope from missing directory /root/.mozilla/firefox/9egkwca3.default/extensions/firefox-hotfix@mozilla.org.xpi
1463085990120    addons.xpi    WARN    Add-on [email]firefox-hotfix@mozilla.org[/email] is missing bootstrap method shutdown
1463085990123    addons.manager    WARN    Exception calling callback: [Exception... "Component returned failure code: 0x80520006 (NS_ERROR_FILE_TARGET_DOES_NOT_EXIST) [nsIFile.isDirectory]"  nsresult: "0x80520006 (NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)"  location: "JS frame :: resource://gre/modules/addons/XPIProvider.jsm :: getURIForResourceInFile :: line 1506"  data: no] Stack trace: getURIForResourceInFile()@resource://gre/modules/addons/XPIProvider.jsm:1506 < this.XPIProvider.callBootstrapMethod()@resource://gre/modules/addons/XPIProvider.jsm:4668 < this.XPIProvider.uninstallAddon()@resource://gre/modules/addons/XPIProvider.jsm:4921 < AddonWrapper.prototype.uninstall()@resource://gre/modules/addons/XPIProvider.jsm:7129 < uninstallHotfix/<()@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///root/.mozilla/firefox/9egkwca3.default/extensions/firefox-hotfix@mozilla.org.xpi!/bootstrap.js:78 < safeCall()@resource://gre/modules/AddonManager.jsm:179 < makeSafe/<()@resource://gre/modules/AddonManager.jsm:195 < Handler.prototype.process()@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:933 < this.PromiseWalker.walkerLoop()@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:812 < this.PromiseWalker.scheduleWalkerLoop/<()@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:746
1463086090082    addons.xpi    WARN    Add-on [email]firefox-hotfix@mozilla.org[/email] is missing bootstrap method shutdown

Question 1: Why did it appear in the terminal?

Question(s) 2: Should I do something? What does it all mean, Powers?

---

### Post by uli9 on 2016-05-13
(..., Basil.)

Anyone have an idea what was happening with the update?

---

### Post by SL0ltMJGyh on 2016-05-13
I had this issue before- what I did was I removed it with apt and then reinstalled it using apt-get install flashplugin-installer. Make sure you have the universe repository enabled and you run apt-get update first so you can reinstall it. Let me know if it works!

---

### Post by uli9 on 2016-05-13
I will try that next. But I am not sure there is a problem. What does the message in the terminal actually mean? And why did it show up while I was doing something totally different? I did not do updates through terminal, but with the GUI.
Synaptic tells me I have the latest version: flashplugin-installer 11.2.202.621ubuntu0.16.04.1.
Firefox tells me it's up to date.
I just tried it on some website and it works.
I don't really have a problem (I think?). I just want to understand what was happening in the terminal. I am still some sort of a noob, even after years of Linux....

---

