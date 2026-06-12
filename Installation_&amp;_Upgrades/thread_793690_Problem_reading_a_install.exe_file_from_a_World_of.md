---
title: "Problem reading a install.exe file from a World of Warcraft DVD"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by dualslash on 2008-05-14
I have World of Warcraft on a DVD. And when i try to open Installer.exe i get a message saying that there was no Installer.exe to access. Do I have to activate DVD playback to get this to work?

---

### Post by iaculallad on 2008-05-14
Windows executable do not normally run on Linux except when handled by an Emulator (i.e: WinE, Cedega). Try installing an emulator first before accessing your WoWCraft DVD.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Partyboi2 on 2008-05-14
.exe file extentions are for windows, linux does not use them, but in saying that you can use a program like wine to install some programs with .exe. You can install wine from add/remove.
[[COLOR=Red]http://www.winehq.org/[/COLOR]]("http://www.winehq.org/")

---

### Post by dualslash on 2008-05-14
Sorry forgot to mention that I am using Wine.

---

### Post by Partyboi2 on 2008-05-14
Here is a how-to for installing on ubuntu
[[COLOR=Blue]https://help.ubuntu.com/community/WorldofWarcraft[/COLOR]]("https://help.ubuntu.com/community/WorldofWarcraft")

---

### Post by dualslash on 2008-05-14
I followed the instructions and i get this error message 
" No installer data could be found. If this problem persists, please contact Blizzard Technical Support."

---

### Post by dualslash on 2008-05-14
I also get this message in the command window
" fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d32a8
fixme: ole: OleCreateStaticFromData (not shown), stub! "

---

### Post by mumurlen on 2008-05-27
Hi 

I had the same problem and this is how I have fixed it:

Umount the DVD and add edit following the following line in /etc/fstab

sudo gedit /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR="Red"]unhide[/COLOR],noauto,exec 0       0

The [COLOR="Red"]unhide[/COLOR] option does the trick...

The reason you don't see the install.exe is because is a windows hidden file not a classical linux .<filename name> hidden file.

Once you updated your fstab you can insert your WOW DVD and you will see all the files you were missing.

Good Luck

Mihai

---

### Post by init6 on 2008-07-02
Perfect.  Thanks mumurlen.  I was pulling my hair out.

---

### Post by Muzicar on 2008-07-02
I have problem too I have done everthing like in this guide [https://help.ubuntu.com/community/WorldofWarcraft,and](https://help.ubuntu.com/community/WorldofWarcraft,and) nothing happend.I have Wow on 4 cd's and they are in MDF file I have moun them in Acetoneiso and copy them in the folder that I made.Folder is called wow.In terminal I get this message: dobrivoj@Dragonforce-desktop:~$ cd / wow /
dobrivoj@Dragonforce-desktop:/$ wine Installer.exe
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
dobrivoj@Dragonforce-desktop:/$ 
but before in wineconfig I get this message:dobrivoj@Dragonforce-desktop:~$ winecfg
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer

Please guys help

---

### Post by Partyboi2 on 2008-07-02
> I have problem too I have done everthing like in this guide [https://help.ubuntu.com/community/WorldofWarcraft,and](https://help.ubuntu.com/community/WorldofWarcraft,and) nothing happend.I have Wow on 4 cd's and they are in MDF file I have moun them in Acetoneiso and copy them in the folder that I made.Folder is called wow.In terminal I get this message: dobrivoj@Dragonforce-desktop:~$ cd / wow /
dobrivoj@Dragonforce-desktop:/$ wine Installer.exe
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
dobrivoj@Dragonforce-desktop:/$ 
but before in wineconfig I get this message:dobrivoj@Dragonforce-desktop:~$ winecfg
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
Make sure you are in the correct directory [FONT=monospace]
[/FONT]```
cd /<path-to-directory>/
``` So if the Wow folder is on your Desktop
```
cd ~/Desktop/WOW_Install
```then[SIZE=2]
[/SIZE]```
wine Installer.exe
```

---

### Post by atowell on 2008-07-03
> **mumurlen said:**
> Hi 

I had the same problem and this is how I have fixed it:

Umount the DVD and add edit following the following line in /etc/fstab

sudo gedit /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR="Red"]unhide[/COLOR],noauto,exec 0       0

The [COLOR="Red"]unhide[/COLOR] option does the trick...

The reason you don't see the install.exe is because is a windows hidden file not a classical linux .<filename name> hidden file.

Once you updated your fstab you can insert your WOW DVD and you will see all the files you were missing.

Good Luck

Mihai

Thank you very much for this post! I was having problems finding the .exe, but the solution you posted worked like a charm.

---

### Post by curbsidesteak on 2008-07-14
I am a little late on this reply, but you just made me avoid going to a hospital for a mental break down. Thanks for your post.

---

### Post by Q-man on 2008-07-16
> **mumurlen said:**
> Hi 

I had the same problem and this is how I have fixed it:

Umount the DVD and add edit following the following line in /etc/fstab

sudo gedit /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR="Red"]unhide[/COLOR],noauto,exec 0       0

The [COLOR="Red"]unhide[/COLOR] option does the trick...

The reason you don't see the install.exe is because is a windows hidden file not a classical linux .<filename name> hidden file.

Once you updated your fstab you can insert your WOW DVD and you will see all the files you were missing.

Good Luck

Mihai

o my freakin god thank you so much!!!!! omg im like in awe right now. I've been lookin' for a full month on how to do this and almost destroyed my computer lol jk. thanx dude

---

