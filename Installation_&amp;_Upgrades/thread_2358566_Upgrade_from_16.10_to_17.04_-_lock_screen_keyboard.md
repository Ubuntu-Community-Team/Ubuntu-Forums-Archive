---
title: "Upgrade from 16.10 to 17.04 - lock screen keyboard layout can't be switched to US"
date: 2017-04-14
forum: Installation &amp; Upgrades
---

### Post by Stefan383 on 2017-04-14
I upgraded from 16.04 -> 16.10 and then to 17.04. Basically everything works fine. Except of lock screen (login screen). I had US and SK layouts in the system before the upgrade and it worked properly. Default layout is set to US and this layout works properly in the lock screen. I am able to switch keyboard layout in the lock screen via the indicator or via shortcut L Alt+ Shift. But now in Ubuntu 17.04 lock screen uses only SK keyboard layout. Even if I switch to SK-US or vice versa, still I can enter password only with SK layout. I even tried uninstalling SK layout and keep only the US one. Still lock screen uses only SK layout. 

What is interesting -> if I use Ctrl+Alt+L for locking the screen in already logged in session, then the keyboard works properly - I can use even US layout for entering password. But when I want to switch the user or when the computer boots up, then again only SK layout can be used. 

Any ideas why such behavior?

---

### Post by Stefan383 on 2017-04-14
OK, I found similar issue here - [https://askubuntu.com/questions/328952/how-do-i-change-the-login-managers-keyboard-layout](https://askubuntu.com/questions/328952/how-do-i-change-the-login-managers-keyboard-layout)
They mentioned there /etc/default/keyboard config file. First I changed XKBLAYOUT="sk" to XKBLAYOUT="us" in the file, and tested it (without rebooting if PC). It did not work. Then I completely moved /etc/default/keyboard to /etc/default/keyboard.orig and also rebooted the PC (most likely even switching XKBLAYOUT="sk" to XKBLAYOUT="us" and reboot afterwards would do the trick also).
Now I have US layout working in the lock screen. This is OK for me as I want to have US layout there, but even switching to different layouts I have defined does not affect the lockscreen's layout and you still type with US layout.

So perhaps a bug in the upgrade process. I do not know how to report this issue as the ubuntu-bug needs a package name and I do not know which package name is this related to.

---

### Post by Stefan383 on 2017-04-14
OK, so I reverted /etc/default/keyboard.orig back to /etc/default/keyboard.orig and changed XKBLAYOUT="sk" to XKBLAYOUT="us" there and rebooted the pc. I can login using us layout now. But again switching to different layout via the indicator does not affect the layout which is used. So basically the issue is, when you boot into the login screen, you can use only the layout defined in /etc/default/keyboard.
Once you are logged in and use Ctrl+Alt+L for locking the screen, then you can choose whatever layout you have defined and it works.

---

### Post by mt410 on 2017-04-21
I have the same problem with a clean installation of Ubuntu 17.04 (No upgrade)
When I boot I get login screen and can only use one keyboard layout (US), when I change to another installed keyboard layout (BE) it still uses US layout for the login screen.
One I am logged in I can use both keyboard layouts (US, BE), when I lock the screen and have the login view again I can also use both keyboard layouts (US, BE)

---

### Post by Stefan383 on 2017-04-21
> **mt410 said:**
> I have the same problem with a clean installation of Ubuntu 17.04 (No upgrade)
When I boot I get login screen and can only use one keyboard layout (US), when I change to another installed keyboard layout (BE) it still uses US layout for the login screen.
One I am logged in I can use both keyboard layouts (US, BE), when I lock the screen and have the login view again I can also use both keyboard layouts (US, BE)

Hi,
please comment it in the raised bug -> [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1682918](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1682918)
It looks nobody works on the bug, so maybe it will help.

---

### Post by agb-ukr on 2017-08-13
And this also, possibly
[https://bugs.launchpad.net/unity/+bug/1286910](https://bugs.launchpad.net/unity/+bug/1286910)

---

