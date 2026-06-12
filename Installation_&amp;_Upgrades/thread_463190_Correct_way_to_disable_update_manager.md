---
title: "Correct way to disable update manager?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by phidia on 2007-06-03
I did a search on this and found this [http://ubuntuforums.org/showthread.php?t=93988](http://ubuntuforums.org/showthread.php?t=93988) it's for an earlier release though so is it ok to use > sudo apt-get remove update-notifier as a means to disable the update manager? I'm using feisty fawn/7.04. TIA

---

### Post by wpshooter on 2007-06-03
Well, if it works in Feisty like it does Edgy, try just unchecking the automatic updates box in internet updates under software sources.

---

### Post by phidia on 2007-06-03
> **wpshooter said:**
> Well, if it works in Feisty like it does Edgy, try just unchecking the automatic updates box in internet updates under software sources.

Thanks I tried that but the update manger is still there in the upper panel-saying there are updates available.

---

### Post by wpshooter on 2007-06-03
Try installing the ones that are currently there. Then reboot.  Then change the parameter by unchecking the box (of course make sure that you **DO** have the button marked to save session changes automatically under sessions) and then reboot again.

P.S. - Personally, I like having the notice up there, why would you not want to see it.  Because it is there does not mean that you have to install the updates.

---

### Post by phidia on 2007-06-03
I do appreciate the help, and (1) I'm on a dial up connection (2) my system is working ok, with the exception of ff crashing-I use epiphany now, so I really would rather not do anymore updates, I don't want the ones that are showing now. 
You are right though I can just ignore the icon _or_ I can try to remove the notifications per the link I referanced earlier. Thanks :)

---

### Post by misfitpierce on 2007-06-03
Under syanptic package manager you can just disable auto looking for updates and should solve your problem.

---

### Post by Sepero on 2007-09-11
Since you're on dialup, you'll probably want to disable automatic download of updates:
System -> Administration -> Software Sources
Updates (tab)
heck for Updates [uncheck]
Close

If you want to disable just the update notifier for one user and not others:
System -> Preferences -> Sessions
Startup Programs (tab)
Update Notifier [uncheck]
Close

---

### Post by rsambuca on 2007-09-11
As a kludge, you could also just comment out your sources.list so it doesn't look for any updates.

---

