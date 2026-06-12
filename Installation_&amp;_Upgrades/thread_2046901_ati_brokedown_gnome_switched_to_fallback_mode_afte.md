---
title: "ati brokedown/ gnome switched to fallback mode after update."
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by boogiemax on 2012-08-23
hey guys, i hope you can help me out. i'm using ubuntu since about 4-5 years now and i like it a lot, but now i have a problem.
i've often ****** up with compiz n stuff, but i could aways reset gnome and/or the fglrx driver by a few terminal-codes.
first of all: radeon hd 6870 2gb. 
yesterday evening, right before going to sleep, i let ubuntu update to .29 . When i booted this morning: fallback mode. classic view on things. i loved the old style ambiance, but wtf, gnome 3.4x is just delicious with some user themes and a few tweaks.. i don't want zo miss that.
the main problem is, that since i've booted it today, i can't even uninstall the ati drivers by step-by-step tuts like ```
sudo sh /usr/share/ati/fglrx-uninstall.sh   sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*


``````

fglrxinfo gives me a X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```      [COLOR=White]         / 
[COLOR=Black]When i try to uninstall the driver, it says ```
 sh ./fglrx-uninstall.sh 
```[/COLOR]
[/COLOR] help a [COLOR=White][COLOR=Black]bro[/COLOR][/COLOR] out !
           [COLOR=White]/     /[/COLOR]

---

