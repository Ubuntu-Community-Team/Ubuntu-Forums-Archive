---
title: "Upgrading DD to FF killed my keyboard?"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by cshake on 2007-07-03
This morning I decided to upgrade from my dapper installation to feisty, mainly for security updates (couldn't get the latest openssl out of repositories and it didn't let me remove it to install from source).
I use xubuntu, it's a headless box that I normally keep in the closet, and I run samba and apache servers on it and other network stuff. I logged in through ssh and upgraded it with the 'official' manual install instructions, and finally (after figuring out a few intermediate package errors) got all the  new packages installed.
apt-get tells me that I've got everything up to date (except gfortran) but I couldn't get my remote x11vnc server started again.

I pulled out the box and connected a keyboard mouse and monitor to it, and tried to boot the 2.6.20 kernel. It showed the new startup sequence, then died at an Xorg error (which I sorta expected) but all of a sudden the keyboard didn't work at all. I know it's plugged in, I used it to go through grub to select the kernel. I then tried to boot it to the recovery console with the 2.6.20 kernel and the keyboard still doesn't work at all, even num lock won't toggle the light. I then booted to an older kernel, got the xorg error again (because I had run envy to update the drivers to the newest kernel, so I knew it wouldn't work) and the keyboard worked, but then it wouldn't give me a command prompt to log in. Finally I got it booted to the recovery console of the older kernel, and see this:
```
* Setting up console font and keymap...
/usr/bin/ckbcomp: Can not find file "rules/xorg" in any known directory
```

What can I do to get it working again?

---

### Post by cshake on 2007-07-03
More details:
```
chris@Minotaur:~$ ls /usr/share/X11/xkb/rules/
base  base.lst  base.xml  README  sgi  sun  xfree98  xkb.dtd

```
Since no 'xorg' is there, I changed the "xorg" in my /etc/X11/xorg.conf to be "base", but still no working keyboard. It is PS/2, but I wouldn't expect that to be a problem.
```
[xorg.conf]
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "base"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection
```
I have since reinstalled most of the packages on the system, then booted the new kernel until the keyboard stops working, then logged in through ssh and gotten the x server to work correctly. Now when I turn on the computer with a monitor attached it shows the graphical xubuntu login screen after flashing the nvidia logo, which leaves me with a just as useless computer with no keyboard.

Does anyone have any idea how to make it recognise a local keyboard?

---

### Post by nmi on 2007-08-04
I had similar problems when upgrading Dapper directly to Feisty. In my case X.org refused to use the Finnish keyboard layout that I had set it to use when installing the system and defaulted to the US layout instead. I fixed this by creating symbolic links to the base files in /usr/share/X11/xkb/rules:
```

cd /usr/share/X11/xkb/rules
sudo ln -s base xorg
sudo ln -s base.lst xorg.lst
sudo ln -s base.xml xorg.xml

```
Then restart X (logout and hit CTRL-Alt-Backspace) or reboot.

Perhaps this will help with the console keyboard problem too.

---

