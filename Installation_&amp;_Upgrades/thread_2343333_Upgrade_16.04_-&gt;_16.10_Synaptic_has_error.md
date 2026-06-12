---
title: "Upgrade 16.04 -&gt; 16.10 Synaptic has error"
date: 2016-11-15
forum: Installation &amp; Upgrades
---

### Post by Arlen_B_Taylor on 2016-11-15
After doing an upgrade via Muon Discover from 16.04 to 16.10, Synaptic won't open properly.  The error is:

E: The value 'xenial' is invalid for APT:  Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

---

### Post by wildmanne39 on 2016-11-15
Please try:
```
sudo apt clean
```
let us know if it works please.

---

### Post by Arlen_B_Taylor on 2016-11-15
Done, it still has the same error.

---

### Post by wildmanne39 on 2016-11-15
Please do:
```
sudo cat /root/.synaptic/synaptic.conf
```
paste it here by clicking new reply then above the window you click on # and put the information in between the two code boxes ```

```
Thanks

---

### Post by Arlen_B_Taylor on 2016-11-15
```

arlen@Dumbledore:~$ sudo cat /root/.synaptic/synaptic.conf
[sudo] password for arlen: 
Synaptic::ViewMode "3";
Synaptic::showWelcomeDialog "0";
Synaptic::vpanedPos "520";
Synaptic::hpanedPos "205";
Synaptic::windowWidth "1507";
Synaptic::windowHeight "808";
Synaptic::windowX "330";
Synaptic::windowY "85";
Synaptic::ToolbarState "2";
Synaptic::Maximized "0";
Synaptic::Install-Recommends "1";
Synaptic::closeZvt "true";
Synaptic::update "";
Synaptic::update::last "1471914734";
Synaptic::update::type "0";
Synaptic::ShowAllPkgInfoInMain "false";
Synaptic::AskRelated "true";
Synaptic::OneClickOnStatusActions "false";
Synaptic::delAction "3";
Synaptic::upgradeType "1";
Synaptic::undoStackSize "20";
Synaptic::UseTerminal "false";
Synaptic::AskQuitOnProceed "false";
Synaptic::useUserFont "0";
Synaptic::useUserTerminalFont "0";
Synaptic::statusColumnPos "0";
Synaptic::statusColumnVisible "1";
Synaptic::supportedColumnPos "1";
Synaptic::supportedColumnVisible "1";
Synaptic::nameColumnPos "2";
Synaptic::nameColumnVisible "1";
Synaptic::sectionColumnPos "3";
Synaptic::sectionColumnVisible "0";
Synaptic::componentColumnPos "4";
Synaptic::componentColumnVisible "0";
Synaptic::instVerColumnPos "5";
Synaptic::instVerColumnVisible "1";
Synaptic::availVerColumnPos "6";
Synaptic::availVerColumnVisible "1";
Synaptic::instSizeColumnPos "7";
Synaptic::instSizeColumnVisible "1";
Synaptic::downloadSizeColumnPos "8";
Synaptic::downloadSizeColumnVisible "0";
Synaptic::descrColumnPos "9";
Synaptic::descrColumnVisible "1";
Synaptic::color-install "rgb(138,226,52)";
Synaptic::color-reinstall "rgb(78,154,6)";
Synaptic::color-upgrade "rgb(252,233,79)";
Synaptic::color-downgrade "rgb(173,127,168)";
Synaptic::color-remove "rgb(239,41,41)";
Synaptic::color-purge "rgb(164,0,0)";
Synaptic::color-available "";
Synaptic::color-available-locked "rgb(164,0,0)";
Synaptic::color-installed-updated "";
Synaptic::color-installed-outdated "";
Synaptic::color-installed-locked "rgb(164,0,0)";
Synaptic::color-broken "";
Synaptic::color-new "";
Synaptic::UseStatusColors "true";
Synaptic::CleanCache "false";
Synaptic::AutoCleanCache "true";
Synaptic::delHistory "-1";
Synaptic::useProxy "0";
Synaptic::httpProxy "";
Synaptic::httpProxyPort "3128";
Synaptic::ftpProxy "";
Synaptic::ftpProxyPort "3128";
Synaptic::noProxy "";
Synaptic::DefaultDistro "xenial";


```

---

### Post by wildmanne39 on 2016-11-15
Change ```
Synaptic::DefaultDistro "xenial";
```
To:
```
Synaptic::DefaultDistro "Yakkety";
```
by running:
```
sudo -H gedit /root/.synaptic/synaptic.conf
```
The line is at the bottom of the screen.

After you make the change save,close gedit and reboot.
Thanks

---

### Post by howefield on 2016-11-15
Or even..

```
sudo -H gedit /root/.synaptic/synaptic.conf
```

---

### Post by wildmanne39 on 2016-11-15
Nap time.
Thanks

---

### Post by Arlen_B_Taylor on 2016-11-15
Problem solved. Thank you.

---

### Post by wildmanne39 on 2016-11-15
Your welcome! Please use thread tools at the top of the page to mark the thread solved!
Enjoy!

---

