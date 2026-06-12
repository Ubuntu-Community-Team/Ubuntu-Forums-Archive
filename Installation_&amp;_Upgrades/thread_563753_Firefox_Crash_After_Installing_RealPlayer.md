---
title: "Firefox Crash After Installing RealPlayer"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by jlw12 on 2007-09-30
I installed RealPlayer10Gold.bin in Ubuntu 7.04. Firefox had been working fine previously but now crashes when I open that up. I've tried uninstalling and reinstalling, but no success. Can anyone help me?

Thanks,
J

---

### Post by linuxwizard on 2007-09-30
Look down this page for Troubleshooting RealPlayer for Linux. Check over mightbe something that will help.
[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

Also have you installed any extensions or plugins that maybe conflicting with RealPlayer and/or Firefox.

---

### Post by jlw12 on 2007-10-01
Still no luck. Is there any way to completely remove Firefox and Real Player, including all extensions, then reinstalling Firefox (at this point I don't care much about Real). Even after uninstalling and reinstalling, when I open Firefox it asks whether I want to "restore session". So must not be completely uninstalling.

Thanks,
J

---

### Post by linuxwizard on 2007-10-01
to remove or disable extensions open Firefox > tools > addons > extensions > click on extension

to remove Firefox use Synaptic 

when Firefox crashes/closes than you reopen Firefox it asks to restore session meaning it will return to where you were at the time of the crash/close all windows/tabs location.

---

### Post by jlw12 on 2007-10-02
Still haven't been able to completely solve this problem. I removed previous Firefox installation. After reinstalling I found that if I run "firefox &" from a command line that will run. However, if I launch from   the panel it will die as before. I only have google and yahoo toolbars installed and don't seem to have any effect on this problem. Any other thoughts are appreciated.

Thanks,
J.

---

### Post by Gremlinzzz on 2007-10-02
uninstall realplayer go into home folder click view show hidden files delete realplayer folder then go into mozilla folder in the mozilla folder youll see firefox folder open it and delete everything inside.its old data from u using firefox

---

### Post by tgalati4 on 2007-10-02
Run firefox from the terminal and examine the error messages:

>firefox --debug

Sometimes firefox seems to hang because of an orphaned process.

>sudo killall firefox-bin

Then start it up again.  I have Real Player 10 installed on a Firefox 1.5 on Dapper and it seems to work.

---

### Post by jlw12 on 2007-10-04
I may have a clue on source of problem. When I start up Firefox from Panel or from a terminal command line when logged in as jlw12, that crashes. Debug message is "Bus error (core dumped). However, when I run from command line when logged in as root Firefox runs ok. Any other suggestions on how to resolve this?

Thanks,
jlw12

---

### Post by blackcp on 2007-10-04
> **jlw12 said:**
> I installed RealPlayer10Gold.bin in Ubuntu 7.04. Firefox had been working fine previously but now crashes when I open that up. I've tried uninstalling and reinstalling, but no success. Can anyone help me?

Thanks,
J

How do you install a program that's stored in a .bin file? I've tried and I don't know what program to use to open it.

---

### Post by jlw12 on 2007-10-05
To install a bin file follow these instructions: 
[http://ubuntuforums.org/showthread.php?t=233309](http://ubuntuforums.org/showthread.php?t=233309)

Does anyone have a solution how to run Firefox as user from the Panel. Right now I can only run from command line as root.

---

