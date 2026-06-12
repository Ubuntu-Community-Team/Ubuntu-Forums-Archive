---
title: "Graphics Card Problem"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by Sabih on 2005-04-13
How do i get around the problem that Ubuntu isn't detecting my Graphics Card (Radeon 9200) when installing..  I successfully installed Ubuntu, however when all the files were unpacking in the commandline, i got an error that x-serv wouldnt load the GUI and now im stuck in the command prompt

---

### Post by Sabih on 2005-04-13
This is the screen where i get upto, before i cop the error for xerver.org

[IMG]http://mrbass.org/linux/ubuntu/install/017unpackingpackagaes.png[/IMG] 



this is the screen that i want to get to so i can continue with the installation

[IMG]http://mrbass.org/linux/ubuntu/install/018xorgconfig.png[/IMG]

---

### Post by Sabih on 2005-04-13
is there someway i can manually get into xserver-xorg and write some text line in to make it detect my graphics card??!!

both suse 9.2 and mandrake 10.1 detected my graphics card without any trouble.. only this installation is troubling me..

---

### Post by graabein on 2005-04-14
[QUOTE=Sabih]is there someway i can manually get into xserver-xorg and write some text line in to make it detect my graphics card??!!

both suse 9.2 and mandrake 10.1 detected my graphics card without any trouble.. only this installation is troubling me..[/QUOTE]
 sudo gedit /etc/X11/xorg.conf

---

