---
title: "Java problem with Ubuntu 10.04"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by Poadrim on 2010-07-22
Hi,

I have problem with java, in my Ubuntu 10.04 laptop. I need this to log on my web bank. When installed I get a [DONE] last but when I try to log on all I get is a [AUTHENTICATE FAIL] I tried different browser but NOGO.

Suggestions?

---

### Post by QIII on 2010-07-22
If you did not install Java as follows, uninstall it with the instructions given.

Go to System | Administration | Software Sources.

Click on the Other Software tab.

Check the Lucid Partner repository.

Allow your software sources to update
  
Close the window.

Open Synaptic (System | Administration | Synaptic Package Manager). 

Use the search functionality to find OpenJDK and IcedTea.  Uninstall them.  (This is contentious.  Remember that you can always reinstall them later.)

Use the search functionality to find "sun-java6".

Install the plugin (sun-java6-plugin, I believe).  For good measure, also install the JRE and the bin.

Close Synaptic.

Close Firefox if you have it open and then restart it.  In the navigation bar type

```
about:plugins
```to see if you have the plugin properly installed.


All of that notwithstanding, some bank websites will simply give you a digital gesture involving one finger and tell you they won't play with you if you are running Linux.

---

### Post by Poadrim on 2010-07-22
There we go! Thanks mate! Did not install the [sun-java6-plugin]

;)

---

