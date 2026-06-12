---
title: "Ubuntu Installation Experience."
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by kpprem@gmail.com on 2006-07-26
Ubuntu Installation Experience.

1. Got the Live CD
2. Put the CD and rebooted by windows XP PC
3. System booted from Live CD with no issues.
4. Ubuntu did its work for 20 minutes and launched the desktop. Not bad. 
5. Played around little bit. Impressed me in simplicity and look and feel
6. Before clicking the install button, Browsed some forums and read some reviews.
Note: Common Issues in Ubuntu 6.06
- Not able to configure wireless connection
- Wireless connections are getting dropped during reboot/hybernate/network switching 
- Not good fonts
- Display Issues(?) (I may not agree issue. Ubuntu is configured my display with no issue)

7. After few searches, Ubuntu itched me to click the install button.
8. OK Good bye windows XP. I like to try some thing new and simply. Good bye blue color.
9. Clicked the install button, Ubuntu did its work for 30 mins with few questions like name, computer name, password, time zone, partition. Not bad. Actually I felt comfortable. (Note: Make sure your laptop is connected to Internet thro' wired connection)
10. Installation went fine. Rebooted the PC and logged in. Nice intro music. 
11. Most are fine. 
12. Issues -

Issue 1:  I have max of 1024*768 resolution in my thinkpad. The default font is too big. Reduced the font size. Still does not look good. (Its a issue for me. May be its OK for others)

Issue 2: Not able to reach Internet thro' Wireless connection

Issue 3: I am in web development business. So I need web development software like java-jre, flash plugin, Internet Explorer, eclipse, good text editor, graphics tool, web server, a database etc....

13. Decided to solve the issues. 

14. Went to System -> Administration -> Update Manager. Ubuntu did its work for 30 mins and updated the OS.

15. Still my issues are exist.

16. Searched forums.

17. Decided to install Microsoft fonts and Tahoma fonts (We have to appreciate Microsoft here. They did a good job in fonts. I liked the fonts in windows XP. They are good in LCD screens)

18. [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) Went to this URL. They have almost everything listed here for ubuntu.

19. They have a utility for ubuntu which installs basic plugins, codecs etc.

20. Decided to try that out.

21. Open a terminal (Application -> Accessories -> Terminal) and paste below lines

wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz)
tar -zxf easyubuntu-3.021.tar.gz
cd easyubuntu
sudo python easyubuntu.in

22. Follow the instructions in popped window. It took some install all. Actually it installed

1. Flash Plugin
2. JRE for Firefox
3. Video/Audio Codecs.
4. RAR utitlity
5. Microsoft corefonts

etc

23. Microsoft core fonts wont come with Tahoma font.
24. To install Tahoma, I did this.
Copied tahoma.ttf and tahomabd.ttf from windows PC to my ubuntu desktop and run the below commands.

sudo cp *.ttf  /usr/share/fonts/myfonts 
sudo fc-cache -f -v 

25. System - > Preferences -> Font. I did all the new fonts used to come with Microsoft. Selected Tahoma and set it.

26. Now Ubuntu looks the way i wanted. I closed issue #1

27. I am working issue #2 and issue #3

28. I will update those soon.

Note: The above are my experience.  I tried it in IBM ThinkPad T42 2378 R4U. 

Prem Ponniah
posted: Jul 25 2006

---

### Post by djheadley on 2006-07-26
Great log!  I wish more people would take as much time and effort in getting things right as you did.  Welcome to the forums!

---

### Post by Mindflux on 2006-07-26
I keep seeing reference to the LiveCD made. However I see nowhere to get the LiveCD? Is it part of the desktop ISO?  If so? where. When I boot it it mentions nothing about a Live Ubuntu setup.

---

### Post by kpprem@gmail.com on 2006-07-27
You are right. Live CD - An ISO Install image of ubuntu installation. You can download and burn it. (No success for me). or order it in shipit.ubuntu.com or simply spend $10 and get this month's linux user magazine from newsstand. It comes with ubuntu 6.06. You can get the magazine in Banes&nobles in US and sure about other part of world.

---

### Post by kpprem@gmail.com on 2006-07-27
29. I am back !

30. Man ! It took me 4 hours to figure out my wireless connection configuration. (Note: My current wireless connection is secured/wpa key based)

31. Go to Add/Remove and remove Network Manager package.

32. Get teh firmware for wireless hardware. In my case wireless card is inbuilt. Findout wireless driver name. You can find your by typing " lspci" in command prompt . Take the last line in the output. Im my case its "Intel Corporation PRO/Wireless 2200BG" . Did a search for "Intel Corporation PRO/Wireless 2200BG Linux Driver" in google. Got this site [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php). Download the latest firmware. (ipw2200-fw-3.0.tgz)

33. Extract the file in your desktop. Using terminal window, Go to the directory and do sudo cp * /lib/firmware

34. Go to Add/Remove. Search for network manager and install Network Manager package.

35. Reboot your PC.

36. You should see the Network Manager icon in your system tray. Click on the icon. It lists all the wireless connections available in your neighbourhood.

37. Select yours. Enter wireless connection name and your wpa-key. Connect. It may ask your password for confirmation.

38. When I remove wire connection, It automatically connected to wireless connection. After reboot, it connected wired connection by default. Removed wired connection and rebooted. This time it connected to my wireless connection.

39. Resolved issue #2. 

40. Issue #3

41. Installing JDK
Download JDK 5.0 Update 7 ([http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp))
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jdk-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2sdk1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java
java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

42. I have to install apache web server, php, eclipse and internet explorer.

43. I will post those later.

---

### Post by kpprem@gmail.com on 2006-07-30
44. Installing eClipse (Easy one got it from [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html) Thanks to the Author)



Extract the eclipse download and move to opt.
tar xzf wtp-all-in-one-sdk-1.0-linux-gtk.tar.gz
sudo mv eclipse /opt/eclipse cd /opt sudo chown -R root:root eclipse
sudo chmod -R +r eclipse
sudo chmod +x `sudo find eclipse -type d`

Then create an eclipse executable in your path
sudo touch /usr/bin/eclipse
sudo chmod 755 /usr/bin/eclipse
sudoedit /usr/bin/eclipse

With this contents
#!/bin/sh
#export MOZILLA_FIVE_HOME="/usr/lib/mozilla/"
export ECLIPSE_HOME="/opt/eclipse"

$ECLIPSE_HOME/eclipse $*

Then create a gnome menu item
sudoedit /usr/share/applications/eclipse.desktop

With this contents
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse IDE
Exec=eclipse
Icon=/opt/eclipse/icon.xpm
Terminal=false
Type=Application
Categories=GNOME;Application;Development;
StartupNotify=true
Configure

You now have a working eclipse. But run this command first to initialise the set up.
/opt/eclipse/eclipse -clean

Then from here on you can run from the menu item applications/programming/eclipse

---

### Post by kpprem@gmail.com on 2006-07-31
45. Installing Internet Explorer. Need WINE package to IE in linux.

You can install WINE from synatic package manager. GO SPM -> Settings ->  Repositories - > Click Add -> Check Community maitained.

Click reload in SPM and search for WINE in SPM. Install WINE.

Now to install IE...
wget  [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0beta7.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0beta7.tar.gz)
tar -xzvf ies4linux-2.0beta7.tar.gz
cd ies4linux-2.0beta7
./ies4linux

46. Solved all my issues in ubuntu. Started using it. Copied all data back to harddisk from CDs. 

47. Running ubuntu last 3 days with out Microsoft Windows.

48. So far its OK. May be I am missing some Microsoft windows user friendly ness or May be I need spend more time on ubuntu to get used it.  I been using windows from 1992 onwards. 2000 and XP are stable. XP is user friendly. I dont see much advantage in ubuntu in comparison with XP. But i will stay with ubuntu for some time and see.

What ubuntu need:
1. A good file explorer with tree view. 
2. Good fonts for low resolutions. Atleast for 1024*768.
3. More Themes/skins to keep the people.

---

