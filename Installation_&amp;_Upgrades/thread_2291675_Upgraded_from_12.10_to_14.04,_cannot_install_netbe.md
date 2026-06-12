---
title: "Upgraded from 12.10 to 14.04, cannot install netbeans, jdk, installer GUI not seen."
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by paul226 on 2015-08-22
Hi,
I recently upgraded from Ubuntu 12.10 to 14.04 using the upgrade option (not erase and install) in the installation CD. 
Tried installing netbeans IDE for PHP.
Did the the following things.
Downloaded jdk netbeans bundle (jdk-8u60-nb-8_0_2-linux-x64)
Did the following commands at the terminal from the 'Downloads' folder where these files are located.
[B]
chmod +x jdk-8u60-nb-8_0_2-linux-x64.sh
 ./jdk-8u60-nb-8_0_2-linux-x64.sh[/B]Tried with sudo command as well
[B]sudo chmod +x jdk-8u60-nb-8_0_2-linux-x64.sh
 sudo ./jdk-8u60-nb-8_0_2-linux-x64.sh[/B]Netbeans for only use as PHP ide, jdk is not required. So tried **'netbeans-8.0.2-php-linux'** in place of the jdk-netbeans bundle option above.Result
In all the cases, the installer GUI wizard does not show. However the wizard icon does showup on the (unity desktop) sidebar. The terminal screen shot is shown below.

[IMG]http://i61.tinypic.com/i5mzaf.png[/IMG]

This screen just remains like that. 

One more thing I noticed is that the **rhythmbox** also does not show a GUI when a song is played. The icon just appears in the sidebar. Is it like that by default? I am able to use terminal commands to play, pause etc.

I am a newbie to Ubuntu and Linux. Pls excuse if the question appears amateurish.

Any help is much appreciated.

Rgds,
Paul

---

### Post by efflandt on 2015-08-22
I would not know anything about Oracle Java because I think the only thing I use java for is minecraft and Ubuntu's openjdk-7-jre package works fine for that. If you had a ppa for Oracle Java in 12.10 and did not ppa-purge that before upgrading to 14.04, something lingering from the old ppa might be interfering.

If you click on the **speaker** icon in right of top bar you can click on the word **Rhythmbox** to open its gui. If you close (X) the gui while it is playing, it does not even show up on the Unity bar, but there are controls for it in the speaker icon. When changing songs it briefly flashes an indicator of that.

Something I had not noticed before is that there are now also controls for VLC (if you have that installed) in the speaker icon.

---

