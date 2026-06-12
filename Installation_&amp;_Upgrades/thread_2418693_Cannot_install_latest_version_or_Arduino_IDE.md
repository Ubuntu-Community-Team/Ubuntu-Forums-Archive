---
title: "Cannot install latest version or Arduino IDE"
date: 2019-05-09
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2019-05-09
Hi:

My Linux version is Ubuntu 12.04 LTS.

After installing Arduino from the Software Center, I noticed it is version 1.0. I then uninstalled it.

From the Arduino site, I downloaded arduino-1.8.9-linux64.tar.xz, extracted its contents, folder arduino-1.8.9.

In Terminal, went to the folder,
 chmod +x install.sh
sudo ./install.sh

this is what I get:
[sudo] password for robert: 
Adding desktop shortcut, menu item and file associations for Arduino IDE...
rm: cannot remove `/usr/local/bin/arduino': No such file or directory
Removing symlink failed. Hope that's OK. If not then rerun as root with sudo.

rm: cannot remove `/usr/local/bin/arduino': No such file or directory
Removing symlink failed. Hope that's OK. If not then rerun as root with sudo.


Note that '/home/robert/.local/share' is not in the search path
set by the XDG_DATA_HOME and XDG_DATA_DIRS
environment variables, so applications may not
be able to find it until you set them. The
directories currently searched are:

- /root/.local/share
- /usr/local/share/
- /usr/share/

 done!
robert@robert-linux:~/Downloads/arduino-1.8.9$ ^C
robert@robert-linux:~/Downloads/arduino-1.8.9$ 


a desktop icon appears as a blank page with a lock, its name being
arduino-arduinoide.desktop

if I try to run it, I get
 There was an error launching the application.

I have no other option than ./uninstall.sh
and then download Arduino 1.0 from the software center.

I'd appreciate any help,

Robert
So I cannot upgrade to a newer version.

---

### Post by coffeecat on 2019-05-09
> **rva1945 said:**
> 
So I cannot upgrade to a newer version.

Do you mean a newer version of Ubuntu or a newer version of arduino?

Your Ubuntu 12.04 is hopelessly out of date, having passed end of life over 2 years ago. Install a supported version of Ubuntu and you will be able to get a later version of arduino from the repositories.

---

### Post by rva1945 on 2019-05-10
I meant the latest version of Arduino IDE.

If the issue is related to the out of data Ubuntu version, I will have to upgrade it.

It is a dual boot system (Ubuntu and W7). Will the GRUB be affected?

Which is the best option for upgrading to a newer Ubuntu version?

---

