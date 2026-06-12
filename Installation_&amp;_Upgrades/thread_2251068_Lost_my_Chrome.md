---
title: "Lost my Chrome"
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2014-11-01
I had the Chrome browser and its web apps working nicely with 12.04. Just installed 14.04 and held my breath, but everything is working -- except Chrome. It won't start. No error message. I installed again from the Chrome site and it gave a message that I must start it from the terminal. When I did (google-chrome-stable, I think) it said there was a library problem of some kind. Should I remove it and start all over and, if so, how? Thanks.

---

### Post by Lloydb39 on 2014-11-01
Update: I removed it. Reinstalled with software center and it ran from the terminal. However, it gave me this:
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[30511:30511:1101/194209:ERROR:sandbox_linux.cc(305)] InitializeSandbox() called with multiple threads in process gpu-process
[30471:30471:1101/194209:ERROR:background_mode_manager_aura.cc(14)] Not implemented reached in virtual void BackgroundModeManager::EnableLaunchOnStartup(bool)
[30471:30471:1101/194209:ERROR:desktop_window_tree_host_x11.cc(1547)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
[3,88389888:23:42:10.738201] Native Client module will be loaded at base address 0x00000c0900000000
[30471:30540:1101/194217:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
When I closed the terminal, Chrome crashed. It won't launch from the icon.

---

### Post by vasa1 on 2014-11-01
Somewhat related: [http://ubuntuforums.org/showthread.php?t=2251025](http://ubuntuforums.org/showthread.php?t=2251025)

---

### Post by john_burns2 on 2014-11-03
I had a similar problem 2 days ago too. Now solved and Google Chrome now works from the launcher. (someone's linked to my thread, but if you've already read it before I found the solution here's what I did)    > [COLOR=#000000] Apparently when I selected the "make Google Chrome my default browser" option, it creates three files. These are located in /local/share/applications. Selecting "show hidden files" reveals all the files in this location. Deleting every file that has the name Chrome in it and deleting these (and emptying the rubbish bin afterwards) makes Google Chrome start from the launcher correctly.[/COLOR]

Hope this helps.

---

