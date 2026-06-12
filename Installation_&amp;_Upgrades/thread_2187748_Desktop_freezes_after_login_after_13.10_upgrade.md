---
title: "Desktop freezes after login after 13.10 upgrade"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by atomicspin on 2013-11-13
The screen comes up for me to login and once I put in my password, it just freezes at the desktop.  I can still CTRL+Alt+F1 to get to a terminal but the GUI just doesn't work.  

Thanks in advance.

---

### Post by Toz on 2013-11-16
Try clearing your sessions cache. Before you log in:

1. Go to to the first console (Ctrl+Alt+F1)
2. Log in to the text console
3. Run the following commands:
```
cd .cache
rm -rf sessions
```
4. Go back to the gui login screen (Ctrl+Alt+F7)
5. Try logging in again.

---

### Post by dupond2 on 2013-11-22
I am having a similar issue with ubuntu 13.04, after entering my password in the login screen, no desktop and icons appeared and the screen stay frozen. I can still use a terminal to launch GUI. I tried what was recommended (clearing the session cache before logging in) but this did not solve my issue.

Thanks for your help.

---

### Post by Toz on 2013-11-22
> **dupond2 said:**
> I am having a similar issue with ubuntu 13.04, after entering my password in the login screen, no desktop and icons appeared and the screen stay frozen. I can still use a terminal to launch GUI. I tried what was recommended (clearing the session cache before logging in) but this did not solve my issue.

Thanks for your help.
Hello dupond2 and welcome to the forums.

This fix only works with Xubuntu (a flavour of Ubuntu). According to your post, you're running Ubuntu. It might be best to create new thread specific to your issue to get the proper recommendations for your setup.

---

### Post by paulprobert on 2014-02-11
> **atomicspin said:**
> The screen comes up for me to login and once I put in my password, it just freezes at the desktop.  I can still CTRL+Alt+F1 to get to a terminal but the GUI just doesn't work.  

Thanks in advance.

I just had this exact problem.  Note that if I logged in as guest everything would work fine.  Solution was:
log in to tty2 using ctrl-alt-f2, then do "rm -rf ~/.config/xfce4/xfconf"

HTH

---

### Post by Toz on 2014-02-12
> **paulprobert said:**
> I just had this exact problem.  Note that if I logged in as guest everything would work fine.  Solution was:
log in to tty2 using ctrl-alt-f2, then do "rm -rf ~/.config/xfce4/xfconf"

HTH

Please note that this will delete most of your Xfce configuration settings, and my not be a desired side effect. The fix from post #2 is the preferred fix because it clears out any corruption in the saved sessions cache (a common cause for this issue). This method from post #2 will delete any previous saved sessions, but will not delete any configuration settings. And for completeness sake, in Xubuntu 13.10 and newer, a "Clear Saved Sessions" option now exists in Settings Manager -> Session and Startup -> Sessions, that performs the same function.

---

### Post by mark-slugbug on 2014-03-10
After deleting a bunch of files I was able to narrow the problem down for me to being this specific file causing the problem. 

> $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/display.xml


If you don't want to delete all your xfce4 settings, you can try just deleting this file and restarting. I've also found this solution on other forums once I knew what to search for.

---

