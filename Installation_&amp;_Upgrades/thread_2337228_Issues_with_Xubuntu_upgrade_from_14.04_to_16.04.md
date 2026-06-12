---
title: "Issues with Xubuntu upgrade from 14.04 to 16.04"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by Randy_Bass on 2016-09-15
I've been running Xubuntu 14.04 for a few years now, and did my first LTS upgrade to 16.04 (kernel 14.4.0-34), and would like to share the issues that came up in the upgrade. On the whole, it went smoother than expected, although many hours were required to get my system back to a "comfortable" state again. Here are the problems and what I did, if anything, to rectify them:
    


[LIST=1]
[*][FONT=Liberation Sans]In    grub[/FONT][FONT=Liberation Sans]2[/FONT][FONT=Liberation Sans],    error message that lvmetad is not running [/FONT][FONT=Liberation Sans]yet[/FONT][FONT=Liberation Sans].    [/FONT][FONT=Liberation Sans]Using    direct activation during [/FONT][FONT=Liberation Sans]sysinit.    [/FONT][FONT=Liberation Sans]Attempts    to rectify [/FONT][FONT=Liberation Sans]using    solutions found online [/FONT][FONT=Liberation Sans]don't    work. [/FONT][FONT=Liberation Sans]Problems    has since solved itself, perhaps with a recent kernel update to 14.4.0-36?[/FONT]
[*]    [FONT=Liberation Sans]WIFI    no longer worked. I use a third party module (driver) for my USB NIC    (Realtek 8812au). I found out that it was rebuilt automatically and    installed on the current kernel, as it was supposed to do, but was    rebuilt with a previous kernel. I had to use dkms to remove the    previous module from the kernel, and then rebuild and reinstall it    with the current kernel, again with dkms. Then it happpened again    with kernel update from 16.4.0-34 to 16.4.0-36. I made a script file    to do this automatically the next time it happens, as it also    happened on a previous update (kernel 3.13.0-78), for which my    solution was to put the previous kernel 3.13.0-77 as my default in    grub2. In researching this, I found people who were giving up on    Ubuntu altogether because they couldn't get their WIFI working. It    was an insidious problem.[/FONT]
[*]    [FONT=Liberation Sans]Panel    launchers for scripts no longer work. Rectify by pointing launchers    to scripts with full directory on command line.[/FONT]
[*][FONT=Liberation Sans]Keyboard    mappings to scripts don't work. Rectify    by pointing launchers to scripts with full directory on command    line. However,    some keyboard remappings don't stick on reboot.[/FONT]
[*]    [FONT=Liberation Sans]Power    Management screensaver doesn't work. Rectify by installing    xscreensaver, set to desired time with blank screen.[/FONT]
[*]    [FONT=Liberation Sans]Lost    SSH &#8220;no-password&#8221; login to other computers on LAN. Rectify by    recopying RSA file to target computer.[/FONT]
[*]    [FONT=Liberation Sans]logname    utility no longer returns the name of the login user, and in fact    returns blank, which causes scripts relying on this utility to not    run correctly. No workaround. $USER and $LOGNAME don't work the same    way when using sudo. Alternative is to hard code the user's name    into code. I have since learned that I can use $HOME and strip off "/home/" to get my login name, which will be the same even when I use sudo root.[/FONT]
[*]    [FONT=Liberation Sans]Gparted    was uninstalled. Rectified by reinstalling.[/FONT]
[*]    [FONT=Liberation Sans]Font    size changed in some menus.[/FONT]
[*]    [FONT=Liberation Sans]In    Settings>Window Manager>Focus, The Focus Model radio button    &#8220;Click to Focus&#8221; is checked. However, focus will switch to    another window when the mouse cursor is positioned over an out-of-focus    window and the mouse scroll wheel is moved. Unable to rectify this change.[/FONT]
[*]    [FONT=Liberation Sans]In    Libreoffice Calc, some cells which reference text in other cells change case from sentence case to uppercase. This doesn't happen with all cells, just some. Unable to rectify. Very bizarre.[/FONT]
[*][FONT=Liberation Sans]EDIT: Let me add one more thing. I have my desktop environment set up with 9 workspaces. I save a session with Thunderbird, File Manager, and Terminal to start up automatically on boot, with Thunderbird in Workspace 1, and File Manager and Terminal both in workspace 3. With the upgrade to 16.04, they no longer come up in my desired workspaces. File Manager and Terminal come up in workspace 1, and Thunderbird come up in workspace 2. I have deleted saved sessions and recreated sessions several times, and changed between "Only on this workspace" and "Always on visible workspace", but nothing seems to get this to work the way I want it to. This worked so well with 14.04.[/FONT]
[/LIST]

---

