---
title: "Filezilla and 13.10 will not open."
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by gwill83419 on 2013-11-11
13.10 will not open filezilla onto the screen. The icon comes up in the Top Left-hand corner and the option to quit is there.
As an alternative, 'Bare FTP' works but is not as good.
My 13.04 machine and Filezilla work well.

Any suggestions Please.

Graham.

---

### Post by anjithkp on 2013-12-05
Me too facing this problem. Somebody please help.

---

### Post by marcel-i on 2014-01-05
Same problem here. Installed Filezilla through Ubuntu Software center, version 3.7.3. Removed it, and reinstalled, rebooted, no luck. 
Help is appreciated.

When starting with the --debug-startup flag, i get this:
2014-01-05 14:27:04 211 CFileZillaApp::CFileZillaApp()
2014-01-05 14:27:04 229 CFileZillaApp::OnInit()
2014-01-05 14:27:04 229 CFileZillaApp::ProcessCommandLine
2014-01-05 14:27:04 229 CFileZillaApp::LoadLocales
2014-01-05 14:27:04 245 InitDefaultsDir
2014-01-05 14:27:04 246 CFileZillaApp::LoadResourceFiles
2014-01-05 14:27:04 989 CFileZillaApp::CheckExistsFzstp
2014-01-05 14:27:05 013 CMainFrame::CMainFrame
2014-01-05 14:27:05 018 CMainFrame::CreateMenus
2014-01-05 14:27:05 026 CMainFrame::CreateToolBar
2014-01-05 14:27:05 037 CMainFrame::CreateQuickconnectBar
2014-01-05 14:27:05 534 CContextControl::CreateTab
2014-01-05 14:27:05 534 CContextControl::CreateContextControls
2014-01-05 14:27:05 538 CLocalTreeView::CLocalTreeView
2014-01-05 14:27:05 539 CLocalListView::CLocalListView

---

### Post by devine.steve on 2014-01-05
Seems to work for me. When you use alt-tab to cycle thru open programs does it open then?

---

### Post by gwill83419 on 2014-01-07
Hi and happy new year.
HaHa, something has changed over the Christmas period, it now works. It certainly did not just before the holiday.
I can only assume that the latest kernel changes or other software upgrades have solved this problem.

Anyway thanks for getting back to me (now all I need is to get the BisonCam working, Hmm).

Graham.

---

### Post by gwill83419 on 2014-01-07
P.S.  Solved?

---

### Post by posta-7 on 2014-06-22
I have a similar problem with FIlezilla 3.7.3 and Ubuntu 13.10.
Since a few days Filezilla seems not to be starting.
I removed it and installed it back.
Same result. Click on the left bar, and nothing happens.
Open a command window, typed "Filezilla" and the window hangs.
Opened the dash, typed "Filezilla", click on the icon, nothing.
THen after a few minutes, don't ask me how and why, three Filezilla windows opened, together.
Like something prevented them to start at soon.
Now, if I close filezilla and open it again, it starts immediately.
So, I can say that there is a delay, minutes.
Other programs they seem to start immediately, with no delay.
It seems to be something related with Filezilla.

---

