---
title: "From Kubuntu revert to Ubuntu (Karmic Koala)"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by samgooi4189 on 2009-12-08
[SIZE=3]Hi, here is some tips to[/SIZE][COLOR=darkorange] **[SIZE=3]revert back to Ubuntu Gnome GUI from Kubuntu.[/SIZE]**[/COLOR]
[COLOR=darkorange][/COLOR] 
[SIZE=3]Today, I success upgrade to Kubuntu with KDE interface, but facing problem to start the OS, so I try to revert back to Ubuntu. It turn out to be successful.[/SIZE]
 
[SIZE=4][COLOR=indigo]Here is the steps:[/COLOR][/SIZE]
[SIZE=4][COLOR=indigo]*_1. When you stuck in dissorted screen after the Kubuntu icon, just press any to bypass the log-in, then proceed log-in by typing in your password._*[/COLOR][/SIZE]
[SIZE=4][COLOR=#4b0082]**[/COLOR][/SIZE] 
[SIZE=4][COLOR=indigo]*_2. Next go to synaptic manager and select the package "KDE Desktop Environment". Inside the package, mark the list of program that have the word "Kubuntu", then mark to complete removal, later click "apply"._*[/COLOR][/SIZE]
[SIZE=4][COLOR=#4b0082]**[/COLOR][/SIZE] 
[SIZE=4][COLOR=indigo]*_3. Then access into terminal, type "sudo apt-get install ubuntu-desktop"._*[/COLOR][/SIZE]
[SIZE=4][COLOR=#4b0082]**[/COLOR][/SIZE] 
[SIZE=4][COLOR=indigo]*_4. There will be a list of broken programs shown in the terminal. Proceed with typing "sudo apt-get autoremove"._*[/COLOR][/SIZE]
[SIZE=4][COLOR=#4b0082]**[/COLOR][/SIZE] 
[SIZE=4][COLOR=indigo]*_5. When the process running, the terminal will said one process still running and will as you permission to end it. Just select to end the process._*[/COLOR][/SIZE]
[SIZE=4][COLOR=#4b0082]**[/COLOR][/SIZE] 
[SIZE=4][COLOR=indigo]*_6. After all had done, you will get into a backscreen with command. you can either press your power once or press untll shut down. (press once you will see the ubuntu icon appear, press untill shut down also can.)_*[/COLOR][/SIZE]
[SIZE=4][COLOR=#4b0082]**[/COLOR][/SIZE] 
[SIZE=4][COLOR=indigo]*_7. On your computer, then you will see the Ubuntu icon. Yeah! You had done it._*[/COLOR][/SIZE]
 
[SIZE=2][COLOR=navy]**After reverting back to Ubuntu, you will still have KDE interface to switch, but it lost many of its icon. For Gnome (default), everythings works fine.**[/COLOR][/SIZE]
[SIZE=2][COLOR=navy][/COLOR][/SIZE] 
[SIZE=2][COLOR=navy]**I had successful to done this on my laptop Dell Latitude D620.**[/COLOR][/SIZE]
[SIZE=2][COLOR=navy]**If you facing proble trying Kubuntu and want to change back to Ubuntu, this will be the cure. Thanks!!!:D**[/COLOR][/SIZE]

---

### Post by zkriesse on 2009-12-08
Just so you know this should have been posted under the [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") Section not here.

---

