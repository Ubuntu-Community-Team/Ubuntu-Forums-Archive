---
title: "I can't install Arduino in 16.04 LTS"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2019-06-03
I followed these guidelines:

[https://www.arduino.cc/en/Guide/Linux#toc3](https://www.arduino.cc/en/Guide/Linux#toc3)

but then in Terminal:
root@robert-linux:/home/robert/Downloads/arduino-1.8.9# ./install.sh
Adding desktop shortcut, menu item and file associations for Arduino IDE...

rm: cannot remove '/usr/local/bin/arduino': No such file or directory
Removing symlink failed. Hope that's OK. If not then rerun as root with sudo.
touch: cannot touch '/root/.local/share/applications/mimeapps.list': No such file or directory
/usr/bin/xdg-mime: 807: /usr/bin/xdg-mime: cannot create /root/.local/share/applications/mimeapps.list.new: Directory nonexistent

 done!
root@robert-linux:/home/robert/Downloads/arduino-1.8.9#

But when I type IDE in "Search your computer" and then click on the Arduino IDE icon, nothing happens, just the mars effect (slow blinking) of the icon and nothing else.

In Ubuntu Software I type Arduino but no option to install it appears.

---

### Post by Xian on 2019-06-04
Create \root\.local\share\applications\mimeapps.list empty file and directory structure manually. 

Then run the .\install.sh file as sudo or su.[COLOR=#555555][FONT=Roboto]

[/FONT][/COLOR]Arduino should now appear in your application menu.


The program will load if arduino is typed at command line.

---

