---
title: "Menu bars and panels lost after upgrade"
date: 2018-03-09
forum: Installation &amp; Upgrades
---

### Post by dany2 on 2018-03-09
I experienced the same problem.  The symptoms were:

[LIST=1]
[*]Launch bar or task bar on desktop 
[*]Able to start terminal from desktop menu (right mouse click and Open Terminal) but with no window decorations.  No moving or resizing of windows. 
[*]Able to start other applications from terminal.  Again no moving or resizing, but could change focus between then by clicking if the windows were not hidden as window order could not be changed. 
[/LIST]
These are similar to the symptoms when no window manager is running except I could change focus, which is not usually possible without a window manager.

I have a two seat setup with two accounts, so I was able to test various things.

One user who happens not to have root privileges was able to log in on either seats with no problems at all.  None of the symptoms described above were experienced.
The other user who does have root privileges experienced the problem on either seat.  I don't know if it is related to having the root privileges.

I tried several things including all of those described in this thread.  None of them worked.  Since only one account was experiencing the problem and on both seats, I really felt it was a permissions problem.

One interesting symptom is that ccsm showed that the unity plugin was disabled and there was no way to get ccsm to retain the setting after enabling it.  In fact all plugins were always disabled everytime I restarted ccsm.  However viewing the user database with dconf (dconf dump /org/compiz/) did show that I had various plugins enabled.  I even transferred the working account's /org/compiz/ settings over so they would be identical, then started ccsm and still it would see nothing enabled.

There was also a python KeyError with 'active_plugins' key not found at line 1041 of /usr/lib/python2.7/dist-packages/ccm/Pages.py (provided by compizconfig-settings-manager package).   So something looks broken there, probably in  /usr/lib/python2.7/dist-packages/compizconfig.x86_64-linux-gnu.so or possibly even in /usr/lib/x86_64-linux-gnu/libcompizconfig.so.0 from libcompizconfig0 package.

Anyway, after many fruitless attempts at identifying the problem, I gave up and restored to the following:

[TABLE="width: 500"]
[TR]
[TD][B]Package
[/B][/TD]
[TD][B]Broken version
[/B][/TD]
[TD]**Working version**[/TD]
[/TR]
[TR]
[TD]compiz[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]compiz-core[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]compiz-gnome[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]compiz-plugins-default[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]compizconfig-settings-manager[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]python-compizconfig[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]libcompizconfig0[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]libdecoration0[/TD]
[TD]1:0.9.12.3[/TD]
[TD]1:0.9.12.2[/TD]
[/TR]
[TR]
[TD]unity[/TD]
[TD]7.4.5[/TD]
[TD]7.4.0[/TD]
[/TR]
[TR]
[TD]libunity-core-6.0-9[/TD]
[TD]7.4.5[/TD]
[TD]7.4.0[/TD]
[/TR]
[TR]
[TD]session-shortcuts[/TD]
[TD]1.2[/TD]
[TD]1.2[/TD]
[/TR]
[TR]
[TD]unity-schemas[/TD]
[TD]7.4.5[/TD]
[TD]7.4.0[/TD]
[/TR]
[TR]
[TD]unity-services[/TD]
[TD]7.4.5[/TD]
[TD]7.4.0[/TD]
[/TR]
[/TABLE]

Note that session-shortcuts package did not change versions but it has a dependency on libunity-core-6.0-9 so I had to remove it when I removed libunity-core-6.0-9 and then re-install it.

I did the downgrades by first removing xenial-updates from my list of repositories.  That's just unticking "Recommended udpates (xenial-updates) in the Updates tab of the Software & Updates window found either in synaptic's Settings -> Repositories menu or under  Software & Updates in the System Settings app.

Then through synpatic, I removed all the compiz related packages (the ones with version 1:0.9.12.3), closed synaptic then restarted it and installed the 1:0.9.12.2 versions which it was then displaying as available for installation.

I then uninstalled the unity related packages (the ones with version 7.4.5), and without closing synaptic I tried to install the 7.4.0 versions but got an error doing so.  So I closed synaptic and installed through the command line with apt-get install which had no problem.  I also ran sudo apt-get install -f to make sure there were no problems left over, which there weren't.

So I now don't have xenial-updates as a source of updates, but I'll keep an eye out for announcements when this problem is fixed so I can re-enable it.

I hope someone or even to analyse the problem quicker.

Cheers
Dan

---

### Post by xcesarfrancox on 2018-03-09
Try this:

```
rm -rf ~/.cache
```

---

### Post by gertwildeboer on 2018-03-09
UPDATE: just tried the last option in this thread once again, but this time it fixed the problem after reboot, thanks xcesarfrancox

I'm having exactly the same problem. I've tried all fixes I could find on the internet so far but nothing works!!!, my ubuntu laptop has become useless, pleas help.....
 Is there a way to roll-back the latest updates ? or can I restore the 16.04 installation without losing my data?

---

### Post by xcesarfrancox on 2018-03-09
> **gertwildeboer said:**
> I'm having exactly the same problem. I've tried all fixes I could find on the internet so far but nothing works!!!, my ubuntu laptop has become useless, pleas help.....
 Is there a way to roll-back the latest updates ? or can I restore the 16.04 installation without losing my data?

Have you tried my proposed solution? I was able to restore my desktop without losing any data or configurations/customizations.

---

### Post by QIII on 2018-03-09
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2386528](https://ubuntuforums.org/showthread.php?t=2386528)

Please do not hijack the threads of other users.  It is inconsiderate of them and generates confusion for those attempting to help.

Thanks.

---

### Post by deadflowr on 2018-03-09
Anyone report these packages as broken?
They won't fix what they do not know is broken.
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

All work fine for me.
And probably work fine for most users.

Seems though that the OP has a rather unique setup, running multi-seats and all.
Not sure where that fits into the scheme of things.

---

### Post by dany2 on 2018-03-10
Thanks for the suggestion xcesarfrancox.

One of the things I tried, was to rename ~/.config, ~/.local and ~/.cache.  I did not delete them.  I then logged out and logged back in and sure enough all these were recreated but my symptoms remained.

I did not try to reboot so that may have been my mistake which the OP over in [https://ubuntuforums.org/showthread.php?t=2386528&page=3](https://ubuntuforums.org/showthread.php?t=2386528&page=3) indicates worked for her.  And I tried all of them at the same time so that may also have been a mistake.

I'll give your suggestion a go and report back.

---

### Post by dany2 on 2018-03-10
> **QIII said:**
> Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2386528](https://ubuntuforums.org/showthread.php?t=2386528)

Please do not hijack the threads of other users.  It is inconsiderate of them and generates confusion for those attempting to help.

Thanks.

Could you explain why adding my experience and solution with the same symptoms to that thread considered hijacking?  Doesn't having two threads for the same issue make it more difficult for people to find solutions?

Also, your expansion of my original "HTH" in the last sentence to "I hope" is missing "this helps", and why is your edit marked with reason "implied profanity"?

Thanks.

---

### Post by burnsmicro2 on 2018-03-10
Finally a solution that worked for me, from [https://askubuntu.com/questions/811552/no-launcher-and-menu-bar-on-ubuntu-16-04](https://askubuntu.com/questions/811552/no-launcher-and-menu-bar-on-ubuntu-16-04)

mv ~/.cache/compizconfig-1 ~/.cache/compizconfig-renamed
shutdown -r 0

---

### Post by dany2 on 2018-03-10
> **burnsmicro2 said:**
> Finally a solution that worked for me, from [https://askubuntu.com/questions/811552/no-launcher-and-menu-bar-on-ubuntu-16-04](https://askubuntu.com/questions/811552/no-launcher-and-menu-bar-on-ubuntu-16-04)

mv ~/.cache/compizconfig-1 ~/.cache/compizconfig-renamed
shutdown -r 0

I tried that one too, but again, my mistake was not to reboot.  So rebooting seems to be important ... sigh

---

### Post by dany2 on 2018-03-10
I went to try xcesarfrancox's suggestion , so first I re-added xenial-updates as a source of updates.  This allowed me to see the new compiz related packages.  I then installed these and rebooted and ...

... it just worked this time, on both accounts on both seats.  No rm -fr ~/.cache necessary, no renaming of ~/.cache/compizconfig-1

I am back to working with the latest versions of the compiz related packages.

Thank you all for your help on this and apologies for wasting anyone's time.

Cheers
Dan

---

