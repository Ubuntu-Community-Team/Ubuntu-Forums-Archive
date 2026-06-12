---
title: "trouble after logout during upgrade"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by spoirier on 2012-06-12
As I had an ubuntu 11.10 and I installed the gnome-session-fallback to have a classical interface, I was in a session with this classical interface and pressed Ctrl-alt-F1 to login as root and run a do-release-upgrade.
However during the installation, in the last phase as things were being installed, I made the error to go back to the graphical interface (ctrl-alt-f7) and make a logout from the session.
This logout process failed as the system was being upgraded. After a cycle of automatic reattempts where I saw the screen repeatedly switching between graphical and text interface (that describing the logout process), the system finally blocked in a text interface of logout attempt description.
All what I could see moving was that any key including shift produced a code on the screen. But the hard disk was working, so I understood the upgrade was continuing.
After one hour wait to be sure it did all it could, I saw the hard disk was still and made a reboot (the power button induced a linux closing process).

After this I tried the system but the network did not work.
I rebooted in safe mode (twice, calling "network" each time), to do the repair packages function, and saw a message saying to do either apt-get update or some option that I do not remember well, something like --install-missing-packages but I could not find such an option (looking in man apt-get). and after doing apt-get update, the repair packages function no more said this comment.

Now network is working but a trouble remains : in the graphical interface that was involved in the logout, now many areas stay black in the up and down bars.
Also I have a very little window of ubuntu error : icon of ! in yellow explosion with name "Ubuntu", which after some manipulation does not react anymore, I cannot widen or close it (before being blocked it displayed a message that recalls me what I saw in the other computer that was due to the use of the classical interface, but which did not block).

Note that these up and down bars which I have here are wider than what was on another computer which has a more standard version of these bars ; this is because they were initially that wide before the upgrade. I wish to keep them wide as this. I have no clue how such a thing can normally be configured (as I was not the one configuring these computers before). I generally wish to know how to configure these bars.

Another problem (that was there since ubuntu 11) is that the grub menu does not display because of incompatibility with this screen : I had to just guess that it was there and that I had to press the downarrow and enter to get the safe mode.

---

### Post by spoirier on 2012-06-12
After many more tries I resolved some other problems : I finally found the systems settings item from the left menu, by which I could change the language back into English to be able to understand the interface, to finally discover that there was also a System Settings entry in the right menu but lower than I expected.
I also found that the contents of terminals was invisible (except menu) because it was black over black, and resolved this thanks to the page [http://www.addictivetips.com/ubuntu-linux-tips/changing-terminal-colors-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/changing-terminal-colors-in-ubuntu-linux/) by unchecking "Use colors from system theme".

I wanted to disable screensaver lock but there is no item "Screen" in System Settings. There is only "Appearance" (only to change the background image) and "Displays" to change the screen resolution). Is it normal if there is no item "Screen" in system settings ? I found  it mentioned in a help page about ubuntu 11.10, was it normally  suppressed by the upgrade to 12.04 ?
So following another help page I used the command

[FONT=Arial]gsettings set org.gnome.desktop.screensaver lock-enabled false[/FONT]

while another page told it another way : 

gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'

Is it the same ?
Last trouble is that the clock displayed on the top of the screen remains in Polish and did not switch to English - the editing interface of the clock switched to English but not the time itself (names of months and week days).

And as I said, all menu titles in the top bar remain black over black and only become readable when clicking over them.

---

### Post by spoirier on 2012-06-13
Still no clue how to correct the colors in the interface ?
Another aspect of this defect, was that in gedit, the tabs that navigate between several files of the same gedit window appeared black over black - but now they became normal, I don't know why and wonder if the defect will reoccur. Black zones with invisible text remain on the top bar: "applications" - "places" on the left, and username with chatting symbol on the right, that only become readable when clicking on them ; empty zone in the bottom remains black, which is a bit ugly. Firefox symbol on the bottom right also appears on black background surrounded by light grey,  that symbolize the contents of this desktop, while the symbols of other desktops on the left of it are just plain light grey.

Maybe I should post this in the Interface section of this forum ?

---

