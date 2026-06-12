---
title: "Uninstalling and Reinstalling Ubuntu"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by Farquharson on 2011-09-26
Hello all,

I recently upgraded my laptop to Windows 7 from Windows Vista, but I also had Ubuntu on Windows Vista. I am trying to uninstall Ubuntu from my D: drive, and re-download it to the C: drive. Yet, there is a problem.

I can still choose to boot to Ubuntu when I boot my laptop, but when I search for it in "Uninstall Programs" in Windows, neither it or Wubi is there. However, when I open "My Computer" and click on D: drive, both the Ubuntu icon and Wubi Uninstaller are there. 

When I click on Wubi Uninstaller, nothing happens. Is this due to my recent switch from Vista to 7? If anyone can help, I appreciate it!

- Far

---

### Post by LepeKaname on 2011-09-26
I guess you are right... from Windows Vista to Windows 7 the "setup" information was not imported. Does that only happened with wubi only or with any other application as well?

If you can boot into Ubuntu why do you want to reinstall it? 

My guess is that you may have 2 options:

1) reinstall Wubi and see if you can overwrite your old installation.
2) Delete manually your files in D: and search/remove anything at the registry. Then install again Ubuntu. I would recommend you to install it the normal way (giving ubuntu its own partition)... it is more convenient and IMHO is faster and more stable (but I may be wrong).

---

### Post by bcbc on 2011-09-26
Here're instructions to manually uninstall: [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

This will delete the current files/data/programs on the Wubi install you are uninstalling.

If you just want to move it there is a way to do that and save your current setup.

---

