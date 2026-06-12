---
title: "help for . rar files &amp; 7zip"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by ozanuzay on 2010-09-29
hello,
i installed the 7zip and ACE for .rar files. 
But when i want to open a .rar file. 
computer uses the archive manager. But it fails. i could not open the .rar files..

i could not find the 7zip :S 
i clicked the right from mouse etc ... i could not

---

### Post by kerry_s on 2010-09-29
install "ubuntu-restricted-extras" & you will get everything you need.

---

### Post by 5PUTN|K on 2010-09-29
right click on the .rar file select properties than click on the open with tab and select the one u want to use as ur default application for .rar files if the application u want isnt there click on the add button and add it from the list of applications if u cant find it on the list add the comand manually or you could use the terminal command for that application to extract your files here[URL="http://www.google.com/search?client=ubuntu&channel=fs&q=7zip&ie=utf-8&oe=utf-8#hl=en&expIds=17259,24472,26095,26562,26751,52728&sugexp=ldymls&xhr=t&q=ACE+terminal+commands+for+extracting+.rar+files+on+ubuntu&cp=3&pf=p&sclient=psy&aq=f&aqi=&aql=&oq=ACE+terminal+commands+for+extracting+.rar+files+on+ubuntu&gs_rfai=&pbx=1&fp=fb415daea57b0c54"] let me google that for you
[/URL]

---

### Post by kerry_s on 2010-09-29
> **5PUTN|K said:**
> right click on the .rar file select properties than click on the open with tab and select the one u want to use as ur default application for .rar files if the application u want isnt there click on the add button and add it from the list of applications if u cant find it on the list add the comand manually or you could use the terminal command for that application to extract your files here[URL="http://www.google.com/search?client=ubuntu&channel=fs&q=7zip&ie=utf-8&oe=utf-8#hl=en&expIds=17259,24472,26095,26562,26751,52728&sugexp=ldymls&xhr=t&q=ACE+terminal+commands+for+extracting+.rar+files+on+ubuntu&cp=3&pf=p&sclient=psy&aq=f&aqi=&aql=&oq=ACE+terminal+commands+for+extracting+.rar+files+on+ubuntu&gs_rfai=&pbx=1&fp=fb415daea57b0c54"] let me google that for you
[/URL]


no he just needs unrar, but if he installs "ubuntu-restricted-extras" he'll get that & everything else he needs for the future, so he won't have any more problems, be it codecs, java, fonts, etc...

---

### Post by DavePlummer on 2010-09-29
Install packages p7zip-full and p7zip-rar. File Roller, the GNOME archive manager, will then have all it needs to correctly handle .rar files.

---

### Post by ozanuzay on 2010-09-29
thanks all of you
i can open the files, 
but also i cant open the setup.exe's ...
i tried to open with wine , there was an error

blocked: wine/unix

The file '/home/ozan/.cache/.fr-BRYbY0/DOOM95.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by kerry_s on 2010-09-29
right click the doom.exe-> properties-> permissions
check the executable box

---

### Post by DavePlummer on 2010-10-02
For ozanuzay:

Many Windows setup.exe files are not standards-based self-extracting archives. Therefore, the archiving tools will be unable to open them.

---

