---
title: "OpenVPN on Ubuntu 9.10 Server 32-bit"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by rickatnight11 on 2010-01-06
I am trying to set up an OpenVPN server on a machine running Ubuntu 9.10 Server 32-bit by following these instructions:  [https://help.ubuntu.com/9.10/serverguide/C/openvpn.html](https://help.ubuntu.com/9.10/serverguide/C/openvpn.html)

The installation of the **openvpn** package went smoothly, but I'm seeing some inconsistencies in the above guide's certificates section.  It says to copy the */usr/share/doc/openvpn/examples/easy-rsa/2.0/* to */etc/openvpn/*, which I have done, but then it says to edit */etc/openvpn/easy-rsa/vars*.  If one followed the guide, that file wouldn't exist.  I assumed it meant to edit the variables in  */etc/openvpn/2.0/vars*, which I did, but moving onto the next step of running *source vars* gives me problems:

[LIST]
[*]Running *[FONT="Courier New"]source vars[/FONT]* gives me: ***NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/2.0/keys***
[*]Continuing on with the guide and running *[FONT="Courier New"]./clean-all[/FONT]* gives me: ***mkdir: cannot create directory `/etc/openvpn/2.0/keys': Permission denied***
[/LIST]

At this point I know something's wrong.  Am I doing something incorrectly, or is it possible that running the 32-bit version of Ubuntu Server is causing this?

Thanks!

---

### Post by stlsaint on 2010-01-06
you have permission issue than you need to be using sudo for commands that give no permission error, and i dont see running server in 32-bit as being an issue...i have done many atimes myself. try using this guide if the one you have is inconsistent.
[OPENVPN ]("https://help.ubuntu.com/community/OpenVPN")

---

### Post by rickatnight11 on 2010-01-06
I should have mentioned that I tried using "sudo" with each of the commands in the configuration step.  "sudo" doesn't work with the "source" command for some reason, and all of the following commands require that the "source" command complete successfully.

---

