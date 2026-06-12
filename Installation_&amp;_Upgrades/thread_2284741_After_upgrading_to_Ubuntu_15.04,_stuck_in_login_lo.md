---
title: "After upgrading to Ubuntu 15.04, stuck in login loop"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by mateojonsonguynn on 2015-07-01
I recently upgraded to Ubuntu 15.04. On my first reboot, everything graphical was pretty much broken. I fixed this by switching graphics drivers from Noveau to nVidia-304-updates. The important part is: I was logged in automatically, without any trouble.
After I rebooted, the graphics worked properly, and I was taken to the login screen, where I typed in my credentials. The screen showed only my background for about 3 seconds, then black for 2, then returned me to the login screen. No errors whatsoever.

1. My OS: Ubuntu 15.04
2. What I expected to happen: I expected to login and see my desktop.
3. What actually happened: I logged in and instead of going to my desktop I was returned to the login screen with no errors or warnings of any kind.

Additional Notes:

- The mouse is fairly laggy on the login screen, not in latency but in framerate.
- The resolution is lower than it was on 14.10.
- The login screen shows my background in the back. (When I am selected.)
- I cannot login to the guest session, either.
- I can login to my user just fine through the virtual consoles (Ctrl + Alt + F1-F6). Everything works as expected there.
- I have tried:
-- Reinstalling Xorg
-- Reinstalling Unity
-- Rebooting (duh)
-- Reconfiguring lightdm
-- Deleting ~/.Xauthority
-- chowning ~/
-- sudo pam-auth-update --force (no options changed)
-- Tried appending "session required pam_loginuid.so" and "session required pam_systemd.so" to /etc/pam.d/lightdm
-- Tried sudo chmod a+wt /tmp 
-- Deleting ~/.ICEauthority
-- Reinstalled ubuntu-desktop
-- Tried sudo gpasswd -d [my user] nopasswdlogin (wasn't in it anyways)
 


It shows the same symptoms as this Launchpad bug [https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336), but none of the solutions work. How do I fix this?

---

