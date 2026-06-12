---
title: "OPen Office 3 Install"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2008-10-14
I downloaded the files and it has file named update that is supposedly the file that starts the upgrade but it does not work.It gives you the option to run in terminal but the screen just flashes and nothing happens.What am I doing wrong? I tried in the terminal sudo update but that does not work either.

Thanks,

---

### Post by sonicb00m on 2008-10-14
I uninstalled the old one then did a dpkg -i *.deb in the OO folder and then ran the desktop one and it worked perfectly.

---

### Post by DJ_Peng on 2008-10-14
You can also check out [Tom Dryer's tutorial]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/") for upgrading OpenOffice.org to the new version 3 release.

---

### Post by 1/0 on 2008-10-14
Downloaded it via the torrent. 2 Mb/s Not bad. 8-)

---

### Post by tqprvn on 2008-10-15
> **DJ_Peng said:**
> You can also check out [Tom Dryer's tutorial]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/") for upgrading OpenOffice.org to the new version 3 release.
I estimate this to be approximately nine feet over my head. :( Damn it feels crap to be a newbie.

Looks like it won't be in Intrepid (which seems to be getting less appealing by the day).  How long til OO3 shows up in the main repositories and I can just Synaptic it?

---

### Post by 1/0 on 2008-10-15
> **tqprvn said:**
> I estimate this to be approximately nine feet over my head. :( Damn it feels crap to be a newbie.

Looks like it won't be in Intrepid (which seems to be getting less appealing by the day).  How long til OO3 shows up in the main repositories and I can just Synaptic it?

Its not that difficult actually. All you have to do is:

1) Download the compressed file from the [downloads page](http://download.openoffice.org/index.html). The torrent was damn fast!

2) Open a terminal (next steps are all in the same terminal window) and go to the directory containing the downloaded file, often Desktop.

```
cd Desktop
```

3) Extract the file check the name.

```
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

4) Enter the DEBS directory in the decompressed directory (check that its the correct name).

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS
```

5) Install Openoffice.

```
sudo dpkg -i *.deb
```

That's it. If you'd like to remove the old Openoffice do the following in terminal:

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

If you've removed the old Openoffice, you can install the package that contains the menu options (Not otherwise as you'll remove the links to the old Openoffice):

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

I've done all steps so I don't know if Ooo3 turns up in the menu if you have both versions installed. In worst case type "/opt/openoffice.org3/program/soffice" in terminal.

Installation went really smooth for me. No problems at all. So my suggestion is to give it a try. You can always go back to the "stable" version. Just copy paste but make sure the names are the same. "ls" will list the files in the path. If you get any problems. Make a post or PM me.

---

### Post by tqprvn on 2008-10-15
Thanks for this, am downloading now.  I'll see how I go.  I am a terminal avoider generally.

> If you've removed the old Openoffice, you can install the package that contains the menu optionsWhat does this mean? What menu options?

---

### Post by tqprvn on 2008-10-15
nvm - found the fix.

---

### Post by run1206 on 2008-10-15
I had a few times where i was getting runtime errors, but after i restarted my comp, all is well now.

edit: i see you had the same problems as i did.  restart your computer and try to run Openoffice again, worked for me; got rid of the crash reports. let us know if it works.

---

### Post by tqprvn on 2008-10-16
ya i found the fix (deleting .openoffice folder from home)....started it up again, re-profiled myself (since importing old profiles seems to be the root of all evil) and it is fine now.

seems faster than 2.4.  Working on a preso at the moment.

---

### Post by 1/0 on 2008-10-16
> **tqprvn said:**
> Thanks for this, am downloading now.  I'll see how I go.  I am a terminal avoider generally.

What does this mean? What menu options?

I'm not sure but I think it means the ooo links in the programs menu.

---

### Post by tqprvn on 2008-10-21
hmm.  New problem on one of the machines I have OO3-ed.

This one seems to have removed the file associations from OO.

eg - double click on a word doc, and it is trying to open it in Evince (which then fails).

Can right click and do the open-with -> writer thing, but how do I set it as the default application to open documents?

edit - ahh there it is under Properties...

---

### Post by run1206 on 2008-10-26
> **tqprvn said:**
> ya i found the fix (deleting .openoffice folder from home)....started it up again, re-profiled myself (since importing old profiles seems to be the root of all evil) and it is fine now.

seems faster than 2.4.  Working on a preso at the moment.

i have two folders (one is .openoffice.org and the other is openoffice.org2)
i'm wondering which one to delete cuz even while restarting after install, i'm still having the unexpected errors) :(

---

### Post by susanpenter on 2008-10-26
I'm having similar problems.  My update does nothing I havent got a .openoffice file in my home file and I did a search for it and it came back negative.  OO 2.4 is running on my system so it must be somewhere!

---

### Post by run1206 on 2008-10-26
> **susanpenter said:**
> I'm having similar problems.  My update does nothing I havent got a .openoffice file in my home file and I did a search for it and it came back negative.  OO 2.4 is running on my system so it must be somewhere!

did you install Oo3.0 yet?
i had a .openoffice folder in my home folder.  try Ctrl+H when viewing your home folder.

edit: i figured out it was the .openoffice folder i have to delete, in a termial, run this code...

```
cd ~
```
```
sudo rm -R .openoffice
```

i assume this was the profile folder for openoffice.  after the install and after this previous removal, i was prompted to re-enter my profile.  I didn't chose to transfer and entered the info manually.   Then open office worked for me.

---

### Post by susanpenter on 2008-10-26
OK the openoffice2 file was there which I have now deleated and the update will still not work.  I followed the instructions on the previous page and the terminal seemed to be installing it but it is nowhere to be found when I search the pc?

---

### Post by benjoseph on 2008-10-29
> **1/0 said:**
> Its not that difficult actually. All you have to do is:

1) Download the compressed file from the [downloads page](http://download.openoffice.org/index.html). The torrent was damn fast!

2) Open a terminal (next steps are all in the same terminal window) and go to the directory containing the downloaded file, often Desktop.

```
cd Desktop
```

3) Extract the file check the name.

```
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

4) Enter the DEBS directory in the decompressed directory (check that its the correct name).

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS
```

5) Install Openoffice.

```
sudo dpkg -i *.deb
```

That's it. If you'd like to remove the old Openoffice do the following in terminal:

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

If you've removed the old Openoffice, you can install the package that contains the menu options (Not otherwise as you'll remove the links to the old Openoffice):

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

I've done all steps so I don't know if Ooo3 turns up in the menu if you have both versions installed. In worst case type "/opt/openoffice.org3/program/soffice" in terminal.

Installation went really smooth for me. No problems at all. So my suggestion is to give it a try. You can always go back to the "stable" version. Just copy paste but make sure the names are the same. "ls" will list the files in the path. If you get any problems. Make a post or PM me.

Thank you very much for your help. I have struggled unsuccessfully to install Open Office 3 for a week. I have even bought the CD but it would not install, finally I came along with your suggestion. WORKS FANTASTIC, T H  A N K  Y O U V E R Y M U C H.

---

### Post by run1206 on 2008-10-29
odd...when i downloaded OpenOffice, it was in .rpm form; i had to use alien to convert them to .deb files :?

---

### Post by DJ_Peng on 2008-10-30
Go to the OOo download page and click the Get more platforms and languages link. You can select a DEB package there. OOo really should show two download links for Linux users, one for RPMs and one for DEBs since not everyone runs Red Hat.

---

### Post by zika on 2008-10-30
why dont' You try:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

---

### Post by benjoseph on 2008-11-01
tqprvn I am benjoseph, I have encounter a problem. I have upgraded to 8.10, but the installation for technical problem stopped half-way through. I reverted back to 8.4 and I tried to upgrade Open Office to 3.0 using your suggestion that worked fine few days a go, but this time the same commands in Terminal would not work. I followed exactly the same procedure without results. Can you game me some suggestions.

Thank you very much.God bless you.

---

### Post by VastOne on 2008-11-25
1/0

Followed your simple approach and got it working perfectly.  Thank you!

VastOne

> **1/0 said:**
> Its not that difficult actually. All you have to do is:

1) Download the compressed file from the [downloads page](http://download.openoffice.org/index.html). The torrent was damn fast!

2) Open a terminal (next steps are all in the same terminal window) and go to the directory containing the downloaded file, often Desktop.

```
cd Desktop
```

3) Extract the file check the name.

```
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

4) Enter the DEBS directory in the decompressed directory (check that its the correct name).

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS
```

5) Install Openoffice.

```
sudo dpkg -i *.deb
```

That's it. If you'd like to remove the old Openoffice do the following in terminal:

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

If you've removed the old Openoffice, you can install the package that contains the menu options (Not otherwise as you'll remove the links to the old Openoffice):

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

I've done all steps so I don't know if Ooo3 turns up in the menu if you have both versions installed. In worst case type "/opt/openoffice.org3/program/soffice" in terminal.

Installation went really smooth for me. No problems at all. So my suggestion is to give it a try. You can always go back to the "stable" version. Just copy paste but make sure the names are the same. "ls" will list the files in the path. If you get any problems. Make a post or PM me.

---

### Post by VastOne on 2008-11-25
FYI... I tried this one before I did the 1/0 one in this thread and it did not work for me...

> **zika said:**
> why dont' You try:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

---

### Post by loveandequality on 2008-12-16
> **1/0 said:**
> Its not that difficult actually. All you have to do is:

1) Download the compressed file from the [downloads page](http://download.openoffice.org/index.html). The torrent was damn fast!

2) Open a terminal (next steps are all in the same terminal window) and go to the directory containing the downloaded file, often Desktop.

```
cd Desktop
```

3) Extract the file check the name.

```
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

4) Enter the DEBS directory in the decompressed directory (check that its the correct name).

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS
```

5) Install Openoffice.

```
sudo dpkg -i *.deb
```

That's it. If you'd like to remove the old Openoffice do the following in terminal:

```
sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

If you've removed the old Openoffice, you can install the package that contains the menu options (Not otherwise as you'll remove the links to the old Openoffice):

```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```

I've done all steps so I don't know if Ooo3 turns up in the menu if you have both versions installed. In worst case type "/opt/openoffice.org3/program/soffice" in terminal.

Installation went really smooth for me. No problems at all. So my suggestion is to give it a try. You can always go back to the "stable" version. Just copy paste but make sure the names are the same. "ls" will list the files in the path. If you get any problems. Make a post or PM me.

Thank you very much this help me a lot because i alredy try some other one and i fail to install it. This wa simple i dont know why noobs like me think Linux is hard is pretty easy. I love the open source comunity i been a user for less than a month.:KS:popcorn:

---

