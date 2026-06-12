---
title: "Wubi uninstall left grub behind"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by orangenick on 2010-01-31
Hi all,

(related to Ubuntu 9.10 and Windows XP sp3)

I installed Wubi Ubuntu (gnome) through and had a quick play.  then I thought I'd try Kubuntu to see which I preferred so I uninstalled Wubi through Windows control panel and installed Wubi Kubuntu.

I decided I prefered the Gnome version and that I didn't want a Wubi install, but preferred a 'real' install so I removed Wubi again and installed Ubuntu directly from CD.

I have been using Ubuntu for several days now without any problems, until I went back to XP to check some settings.  What I found was:

Boot machine.
Grub menu with various Ubuntu versions and Windows XP Professional.

I select Windows XP Professional 

I get a second Grub menu offering Windows XP and Kubuntu.

I checked that Wubi had uninstalled and is no longer in the Add Remove Programs list.  Grub isn't in the list.

How do I remove the 2nd Grub menu and boot directly into Windows?

thanks for any help!

nick

---

### Post by NightwishFan on 2010-01-31
As a temporary option, you can disable the entry from within Windows.

[LIST=1]
[*]Boot into Xp and log in.
[*]In the start menu go to the "Run" dialog.
[*]Type "msconfig" (no quotes) and push enter.
[*]Find the boot options and uncheck the Kubuntu option.
[/LIST]

If there is a better solution, I am unsure.

---

### Post by darkod on 2010-01-31
If you are using XP just open C:\boot.ini (it might be a hidden file) and delete the lines for ubuntu. Be careful not to delete your XP boot line, just the wubi lines (not sure if there will be one or two from both wubi installs).

Unfortunately after removing wubi in XP the boot lines can stay sometimes in boot.ini.

---

### Post by orangenick on 2010-02-01
Thanks! I tried Darkod's answer and it worked perfectly.

I had to show system files from the folder options  menu to find the boot.ini and remove the read only setting...

Hopefully I won't need the winxp installation anymore ;-)

From further investigation I think the wubi site's instructions for removal (to use the add/remove programs...) are incorrect and may create this problem.  The preferred method seems to be through the uninstall program, but I haven't tried it.

Trying out with the live cd's might have been a better idea.

---

### Post by henrywm on 2010-04-10
How do I remove Ubuntu in msconfig? There is no option to uncheck it. I am not willing to edit my boot.ini. 

Even better, can I remove it completely? I could change the timeout in mscongig so that it becomes almost a non-issue, but I would prefer to remove it completely.

---

