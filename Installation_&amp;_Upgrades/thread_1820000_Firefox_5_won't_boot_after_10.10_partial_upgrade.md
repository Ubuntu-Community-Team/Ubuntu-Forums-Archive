---
title: "Firefox 5 won't boot after 10.10 partial upgrade"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by whistlerspa on 2011-08-07
Nothing happens at all and I can't locate the executable file

I use the 64bit edition of 10.10. Tried total removal and re-installation from Ubuntu Software center but no joy.

---

### Post by dino99 on 2011-08-07
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by whistlerspa on 2011-08-07
> **dino99 said:**
> [http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

Sorry but how are any of these links supposed to help as I can't see a reference to Firefox in any of them?

---

### Post by ~!geek!~ on 2011-08-07
> **whistlerspa said:**
> Nothing happens at all and I can't locate the executable file

I use the 64bit edition of 10.10. Tried total removal and re-installation from Ubuntu Software center but no joy.


You have already reinstalled firefox 5 so, now as a final check, you may try removing all the settings of firefox using  (firefox should not be running at all, you may crosscheck by killing firefox using system monitor, if its found running there):
> mv ~/.mozilla ~/mozillabackup
mozillabackup will be containing all the settings you had previously. You may restore it later.
Now try running firefox again. If you are successful, all you have to do is remove the last profile you were using in mozillabackup directory and restore the mozillabackup to .mozilla directory (Before this, remove the newly created .mozilla directory)


If you are not able to run firefox,
try purgin everything associated with firefox  using command >  sudo apt-get purge firefox and you may remove .mozilla directory in home directory and rename mozillabackup directory as .mozilla (see a dot is there).

---

### Post by lovinglinux on 2011-08-08
> **~!geek!~ said:**
> You have already reinstalled firefox 5 so, now as a final check, you may try removing all the settings of firefox using  (firefox should not be running at all, you may crosscheck by killing firefox using system monitor, if its found running there):

mozillabackup will be containing all the settings you had previously. You may restore it later.
Now try running firefox again. If you are successful, all you have to do is remove the last profile you were using in mozillabackup directory and restore the mozillabackup to .mozilla directory (Before this, remove the newly created .mozilla directory)

If you are not able to run firefox,
try purgin everything associated with firefox  using command  and you may remove .mozilla directory in home directory and rename mozillabackup directory as .mozilla (see a dot is there).

Before the removal of the ~/.mozilla folder, I would try starting Firefox in safe mode.

```
firefox -safe-mode
```

If safe mode works, then is probably an extension causing the problem. You can enable them one by one to check which one is causing the problem. I would particularly look at the *Global Menu Bar Integration* extension, that can prevent Firefox from starting.

If it doesn't work in safe mode, then try a clean profile. Instead of renaming the ~/.mozilla folder, which might have configuration files for other Mozilla applications, I would create a clean profile using the profile manager.

```
firefox -P
```

See these articles:

[http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)
[http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles](http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles)

---

### Post by whistlerspa on 2011-08-10
Thanks  - I tried the purge option first and this worked but I did lose all my bookmarks - is there an import bookmarks option that works? 

The 'Import' option locates nothing even though I also have Chrome installed.

---

### Post by lovinglinux on 2011-08-12
> **whistlerspa said:**
> Thanks  - I tried the purge option first and this worked but I did lose all my bookmarks - is there an import bookmarks option that works? 

The 'Import' option locates nothing even though I also have Chrome installed.

Close Firefox, browse the old profile folder, find the file *places.sqlite* in the profile folder, then copy to the new profile.

---

