---
title: "Consistent crashes in Firefox 49"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2016-09-26
After recent upgrades, Mozilla® Firefox® 49.0 has been extremely temperamental, and a new User Profile build did not help.  I captured the following from GNOME® Terminal; a start from the Profile Manager yielded the following:

```
Vector smash protection is enabled.
ExceptionHandler::GenerateDump cloned child 16951
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...
[Child 16807] ###!!! ABORT: Aborting on channel error.: file /build/firefox-h19o_O/firefox-49.0+build4/ipc/glue/MessageChannel.cpp, line 2052
[Child 16807] ###!!! ABORT: Aborting on channel error.: file /build/firefox-h19o_O/firefox-49.0+build4/ipc/glue/MessageChannel.cpp, line 2052
[NPAPI 16865] ###!!! ABORT: Aborting on channel error.: file /build/firefox-h19o_O/firefox-49.0+build4/ipc/glue/MessageChannel.cpp, line 2052
[NPAPI 16865] ###!!! ABORT: Aborting on channel error.: file /build/firefox-h19o_O/firefox-49.0+build4/ipc/glue/MessageChannel.cpp, line 2052

```
Does a Bug already exist here for Firefox 49 at Launchpad; and if so, at which number?

---

### Post by PaulW2U on 2016-09-26
I've not noticed any problems using Firefox 49 in Ubuntu 16.04.

Anyway, [https://bugs.launchpad.net/ubuntu/+source/firefox/+bugs?orderby=-id&start=0](https://bugs.launchpad.net/ubuntu/+source/firefox/+bugs?orderby=-id&start=0) is a list of bugs reported on Launchpad against Firefox, sorted with the newest bugs first.

I'll leave you to peruse the list.  :)

---

### Post by bcschmerker on 2016-09-26
Noted, and already tagged onto [Bug 1612994](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1612994), as I have the same issue with 48.0 as with 49.0; doubtless the same line(s) of code in MessageChannel.cpp are involved.  The Mozilla® Crash Reporter had the following detail for one such crash, indicating a conflict between an unknown number of Extensions I routinely use and the E10S procedure(s):

```
Add-ons: %7B73a6fe31-595d-460b-a920-fcc0f8843232%7D:2.9.0.14,cipherfox%40mkfly:4.0.0,%7B1feca320-6b4d-11df-a08a-0800200c9a66%7D:2.18,%7Bf36c6cd1-da73-491d-b290-8fc9115bfa55%7D:3.0.9.1-signed.1-let-fixed.1-signed,CompactMenuCE%40Merci.chao:6.2.1,status4evar%40caligonstudios.com:2015.11.16.23.1-signed.1-let-fixed,%7B996bb709-9ff1-4b3e-a865-b5820fd84345%7D:1.2.3.1-signed.1-signed,%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:49.0,firefox%40ghostery.com:7.0.1.4,CSTBB%40NArisT2_Noia4dev:1.5.3beta3,e10srollout%40mozilla.org:1.3,firefox%40getpocket.com:1.0.4,webcompat%40mozilla.org:1.0,langpack-en-ZA%40firefox.mozilla.org:49.0,langpack-en-GB%40firefox.mozilla.org:49.0
AddonsShouldHaveBlockedE10s: 1
BuildID: 20160920074044
CrashTime: 1474906482
E10SCohort: disqualified-test
EMCheckCompatibility: true
Email: bcschmerker@yahoo.com
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1474609333
Notes: OpenGL: X.Org -- Gallium 0.4 on AMD RS780 (DRM 2.43.0, LLVM 3.8.0) -- 3.0 Mesa 11.2.0 -- texture_from_pixmap
FP(D000-L11000-W00000000-T0000) 
ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SafeMode: 0
SecondsSinceLastCrash: 224
StartupTime: 1474906261
TelemetryEnvironment: {"build":{"applicationId":"{ec8030f7-c20a-464f-9b0e-13a3a9e97384}","applicationName":"Firefox","architecture":"x86-64","buildId":"20160920074044","version":"49.0","vendor":"Mozilla","platformVersion":"49.0","xpcomAbi":"x86_64-gcc3","hotfixVersion":"20160826.01"},"partner":{"distributionId":"canonical","distributionVersion":"1.0","partnerId":null,"distributor":null,"distributorChannel":null,"partnerNames":["ubuntu "]},"system":{"memoryMB":3446,"virtualMaxMB":null,"cpu":{"count":2,"cores":2,"vendor":"AuthenticAMD","family":15,"model":107,"stepping":2,"l2cacheKB":512,"l3cacheKB":512,"speedMHz":null,"extensions":["hasMMX","hasSSE","hasSSE2","hasSSE3"]},"os":{"name":"Linux","version":"4.4.0-38-generic","locale":"en-US"},"hdd":{"profile":{"model":null,"revision":null},"binary":{"model":null,"revision":null},"system":{"model":null,"revision":null}},"gfx":{"D2DEnabled":null,"DWriteEnabled":null,"adapters":[{"description":"X.Org -- Gallium 0.4 on AMD RS780 (DRM 2.43.0, LLVM 3.8.0)","vendorID":"X.Org","deviceID":"Gallium 0.4 on AMD RS780 (DRM 2.43.0, LLVM 3.8.0)","subsysID":null,"RAM":null,"driver":null,"driverVersion":"3.0 Mesa 11.2.0","driverDate":null,"GPUActive":true}],"monitors":[],"features":{"compositor":"none"}}},"settings":{"blocklistEnabled":true,"e10sEnabled":false,"e10sCohort":"disqualified-test","telemetryEnabled":true,"locale":"en-US","update":{"channel":"release","enabled":true,"autoDownload":true},"userPrefs":{"browser.cache.disk.capacity":358400,"browser.newtabpage.enhanced":true,"browser.urlbar.userMadeSearchSuggestionsChoice":true,"dom.max_script_run_time":40,"layers.acceleration.disabled":true},"addonCompatibilityCheckEnabled":true,"isDefaultBrowser":false},"profile":{"creationDate":16765,"resetDate":17045},"addons":{"activeAddons":{"{73a6fe31-595d-460b-a920-fcc0f8843232}":{"blocklisted":false,"description":"Extra protection for your Firefox: NoScript allows JavaScript, Java (and other plugins) only for tru","name":"NoScript","userDisabled":false,"appDisabled":false,"version":"2.9.0.14","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17045,"updateDay":17045,"isSystem":false},"cipherfox@mkfly":{"blocklisted":false,"description":"Display the current SSL/TLS cipher and certificate chain","name":"CipherFox","userDisabled":false,"appDisabled":false,"version":"4.0.0","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17045,"updateDay":17045,"isSystem":false},"{1feca320-6b4d-11df-a08a-0800200c9a66}":{"blocklisted":false,"description":"Adds extension options dialogs to the Tools and Titlebar menus. Includes toolbar icon.","name":"Extension Options Menu","userDisabled":false,"appDisabled":false,"version":"2.18","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17045,"updateDay":17045,"isSystem":false},"{f36c6cd1-da73-491d-b290-8fc9115bfa55}":{"blocklisted":false,"description":"Professional Geo Add-on with security features and advanced network tools","name":"WorldIP","userDisabled":false,"appDisabled":false,"version":"3.0.9.1-signed.1-let-fixed.1-signed","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17045,"updateDay":17045,"isSystem":false},"CompactMenuCE@Merci.chao":{"blocklisted":false,"description":"Personalize your Firefox button.","name":"Personal Menu","userDisabled":false,"appDisabled":false,"version":"6.2.1","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17046,"updateDay":17046,"isSystem":false},"firefox@getpocket.com":{"blocklisted":false,"description":"When you find something you want to view later, put it in Pocket.","name":"Pocket","userDisabled":false,"appDisabled":false,"version":"1.0.4","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17010,"updateDay":17064,"isSystem":true},"webcompat@mozilla.org":{"blocklisted":false,"description":"Urgent post-release fixes for web compatibility.","name":"Web Compat","userDisabled":false,"appDisabled":false,"version":"1.0","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17064,"updateDay":17064,"isSystem":true},"e10srollout@mozilla.org":{"blocklisted":false,"description":"Staged rollout of Firefox multi-process feature.","name":"Multi-process staged rollout","userDisabled":false,"appDisabled":false,"version":"1.3","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17067,"updateDay":17067,"signedState":3,"isSystem":true},"status4evar@caligonstudios.com":{"blocklisted":false,"description":"Status widgets and progress indicators for Firefox 4+","name":"Status-4-Evar","userDisabled":false,"appDisabled":false,"version":"2015.11.16.23.1-signed.1-let-fixed","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17045,"updateDay":17070,"isSystem":false},"{996bb709-9ff1-4b3e-a865-b5820fd84345}":{"blocklisted":false,"description":"Adds a toolbar/statusbar button to enable and disable installed plugins","name":"Plugins Toggler","userDisabled":false,"appDisabled":false,"version":"1.2.3.1-signed.1-signed","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17070,"updateDay":17070,"isSystem":false},"firefox@ghostery.com":{"blocklisted":false,"description":"Protect your privacy. See who's tracking your web browsing with Ghostery.","name":"Ghostery","userDisabled":false,"appDisabled":false,"version":"7.0.1.4","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17070,"updateDay":17070,"isSystem":false},"CSTBB@NArisT2_Noia4dev":{"blocklisted":false,"description":"Classic toolbar button style for Firefox, Thunderbird and Seamonkey toolbars and other tweaks and se","name":"Classic Toolbar Buttons","userDisabled":false,"appDisabled":false,"version":"1.5.3beta3","scope":1,"type":"extension","foreignInstall":false,"hasBinaryComponents":false,"installDay":17046,"updateDay":17070,"isSystem":false}},"theme":{"id":"{972ce4c6-7e08-4474-a285-3208198ce6fd}","blocklisted":false,"description":"The default theme.","name":"Default","userDisabled":false,"appDisabled":false,"version":"49.0","scope":4,"foreignInstall":false,"hasBinaryComponents":false,"installDay":17010,"updateDay":17064},"activePlugins":[{"name":"Shockwave Flash","version":"11.2.202.635","description":"Shockwave Flash 11.2 r202","blocklisted":false,"disabled":false,"clicktoplay":false,"mimeTypes":["application/x-shockwave-flash","application/futuresplash"],"updateDay":17038}],"activeGMPlugins":{"gmp-gmpopenh264":{"version":"1.6","userDisabled":false,"applyBackgroundUpdates":1}},"activeExperiment":{},"persona":null}}
Theme: classic/1.0
Throttleable: 1
URL: http://www.sallyhansen.com/whats-new/in-the-news
UptimeTS: 221.5916338
Vendor: Mozilla
Version: 49.0
useragent_locale: en-US

```

---

### Post by bcschmerker on 2016-12-09
**Update:**  The problems were eventually traced to hardware:  The Hot Rod's Advanced Micro Devices® Athlon64® X2 5600+, which has served me through four LTS Dist-Upgrades, has finally hurled - bad memory manager.  As of 9 December 2016, I'm running with the same manufacturer's Athlon64® 3500+ until I have an upgrade CPU for the ASUS® CM1630-06, whose stock Athlon II® X2 220 (which has the same clocks as the recently-failed X2 5600+) has a greater load of Processes under Microsoft® Windows® 10 Build 1607 10.0.14393.451 than under Windows ® Se7en&#8482; Service Pack 1 6.1.7601.569; I estimate the Phenom II® X4 840 to have the reserves necessary.  The X2 220 should be well able to take up where the X2 5600+ left the rails....  [-o<

Considering the Bug tag no longer needed.

---

