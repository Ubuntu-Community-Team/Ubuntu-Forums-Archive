---
title: "I have a HUGE problem. Please help..."
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2005-06-29
Well for starters when ever I select logout from the System menu I don't get the usual little dialog with choices to shutdown, restart, log out and all. The system just logs me out and seems to crash. The screen goes all nutty and lines appear at the bottom. And then I can't log out at all. Is there some sort of System Restore function for Ubuntu?

Secondly the system is now booting VERY slowly. It used to take a minute - now it's far worse. Any ideas?

Thirdly - every time I start the machine the session manager window along with Nautilus (Home folder) opens along with GAIM. Now I want GAIM to start when I start up the machine but I don't want to see the Session manager or Nautilus. Ideas? Easy fix?

Only programs I have TRIED to install lately are hotwayd at gotmail.

Please help - I might go nuts and reinstall Ubuntu or even worse - fall back to Windows!  :-?

---

### Post by deBaas on 2005-06-29
Please make a more suitable title next time. There ar many peole like you pleasing for help.

---

### Post by kona0197 on 2005-06-29
What do you suggest? I can change it. I just don't like the idea of having to use Windows again.  ;-)

Well I tried editing the tittle - no go. Sorry - I'm trying not to step on peoples toes.

---

### Post by mingus on 2005-06-30
You could try reinstalling or reconfiguring major pieces of the system, but given that this is essentially a fresh install, you're probably better off starting from scratch.

As you do that, take note of anything that doesn't seem to work right.  In the stage2 package installation & setup watch to be sure everything is there.  Also be sure to give yourself a root password, you may need it later.

Immediately after installation, get in a terminal and do:
$dmesg | more
and look for any errors.

Then do a test drive before anything else.  Try running a broad selection of apps from the menu.  Logout and back in a few times.  Note anything not working, exactly when along with any error messages.

---

### Post by kona0197 on 2005-06-30
Well I really didn't want to reinstall the system. I guess I may have to. 

I wish Ubuntu had a system restore function just like XP. That would come in handy. Mabye in time.

Anyone else have any suggestions?

---

### Post by mingus on 2005-06-30
[QUOTE=kona0197]Well I really didn't want to reinstall the system. I guess I may have to. 

I wish Ubuntu had a system restore function just like XP. That would come in handy. Mabye in time.

Anyone else have any suggestions?[/QUOTE]

You can try remedial steps like $sudo base-config which will take you through a reinstall of the basic software packages.  However, it sounds like you have pieces missing.  Others need to pitch in here - my exp is more with comm distros.

As far as a "system restore" function in XP, IMHO the more appropro comparison is a "repair install."  System Restore only restores the Registry and a few configuration files.  It is most useful for backing out an application installation or hardware setup that goes awry.  But if the base system gets whacked, MS will have you do a repair install.  I've done more than I care to remember - didn't you notice that I'm all wet and frowning?

---

### Post by hub on 2005-10-02
I am not sure it could be useful but have you try to use synaptic, enable more repositories (settings/repositories/ - at least updates) and reload the information packages.
then try to update the system (ctrl + G). it may detect some wrongly configured packages and reconfigure them well.
not sure that it gonna work but no harm to try.

---

### Post by Haegin on 2006-02-03
I have the logout problem and things - for me it also occurs when I change to a virtual terminal (ctrl+alt+1 etc) and I think it may be a driver problem as it seemed to start after I updated my graphics card drivers but it could also be related to the composite manager...

---

