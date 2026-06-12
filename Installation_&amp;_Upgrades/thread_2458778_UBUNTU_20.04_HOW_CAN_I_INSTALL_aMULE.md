---
title: "UBUNTU 20.04 HOW CAN I INSTALL aMULE??"
date: 2021-03-03
forum: Installation &amp; Upgrades
---

### Post by alemanlatino on 2021-03-03
Dear Community. I have just installed Ubuntu 20.04. and cannot install aMule..I have tried all that is on the net, but without success.
Thank You for your help!

---

### Post by CelticWarrior on 2021-03-03
If you tried all that is on the net what exactly are you expecting from here?

Now, seriously, it should be as easy as downloading and installing all the required packages form a different yet close release, exactly as described [in this Spanish tutorial]("https://www.muylinux.com/2020/12/02/amule-ubuntu-20-04-lts/")  . Although not recommended, it should work.

---

### Post by pintasa on 2021-03-05
> **alemanlatino said:**
> Dear Community. I have just installed Ubuntu 20.04. and cannot install aMule..I have tried all that is on the net, but without success.
Thank You for your help!
Just a few days ago I was in the same situation and spent a lot of time until I finally succeeded. In a few days I will have to do it again. I thought I would remember what steps I did but my memory is terrible.  Basically I kind of remember two main phases: (1) was to download the installation file, tar or deb, I don't remember, and (2) was to use the correct terminal commands needed to install the software.  I am a total newbie so it was very complicated for me.

So, first step is to download the installation file and once you have it follow the right steps to install it.

You might also ask at [http://forum.amule.org/](http://forum.amule.org/)

Good luck!

---

### Post by Gnusboy on 2021-03-06
As my grampa used to say - If you can't take a hoof, don't stand behind the mule.

---

### Post by hajuestark on 2021-07-11
> **CelticWarrior said:**
> If you tried all that is on the net what exactly are you expecting from here?

Now, seriously, it should be as easy as downloading and installing all the required packages form a different yet close release, exactly as described [in this Spanish tutorial]("https://www.muylinux.com/2020/12/02/amule-ubuntu-20-04-lts/")  . Although not recommended, it should work.

Thanks a lot. I had the same Problem after upgrading my Ubuntu 19.10 Version to 20.04LTS. I tried first the tip from Thread [[How to install aMule on Ubuntu 20.04]("https://ubuntuforums.org/showthread.php?t=2441773")] but could not succeed, I became a lot of error messages:[INDENT]
[/INDENT]
```
$ sudo dpkg -i ./amule_2.3.3-1_amd64.deb

         Vormals nicht ausgewähltes Paket amule wird gewählt.

         (Lese Datenbank ... 718860 Dateien und Verzeichnisse sind derzeit installiert.)

         Vorbereitung zum Entpacken von ./amule_2.3.3-1_amd64.deb ...
         Entpacken von amule (1:2.3.3-1) ...
         dpkg: Abhängigkeitsprobleme verhindern Konfiguration von amule:
          amule hängt ab von libc6 (>= 2.33); aber:
           Version von libc6:amd64 auf dem System ist 2.31-0ubuntu9.2.
          amule hängt ab von libcrypto++8 (>= 8.4.0); aber:

           Paket libcrypto++8 ist nicht installiert.

          amule hängt ab von libwxbase3.0-0v5 (>= 3.0.5.1+dfsg); aber:
           Version von libwxbase3.0-0v5:amd64 auf dem System ist 3.0.4+dfsg-15build1.
          amule hängt ab von libwxgtk3.0-gtk3-0v5 (>= 3.0.5.1+dfsg); aber:
           Version von libwxgtk3.0-gtk3-0v5:amd64 auf dem System ist 3.0.4+dfsg-15build1.
         
         dpkg: Fehler beim Bearbeiten des Paketes amule (--install):

          Abhängigkeitsprobleme - verbleibt unkonfiguriert

         Trigger für gnome-menus (3.36.0-1ubuntu1) werden verarbeitet ...
         Trigger für desktop-file-utils (0.24-1ubuntu3) werden verarbeitet ...
         Trigger für mime-support (3.64ubuntu1) werden verarbeitet ...
         Trigger für hicolor-icon-theme (0.17-2) werden verarbeitet ...
         Trigger für man-db (2.9.1-1) werden verarbeitet ...
         Trigger für menu (2.1.47ubuntu4) werden verarbeitet ...

         Fehler traten auf beim Bearbeiten von:

          amule
...


```

So in the end I de installed all amule packets.

But the tip -- in the Spanish tutorial -- that Ubuntu 20.10 has functioning amule packets which work also on Ubuntu 20.04LTS was a very pleasing surprise ;-)
The used links on the web-page were:

[LIST]
[*][amule]("https://packages.ubuntu.com/groovy/amd64/amule/download") 
[*][amule-common]("https://packages.ubuntu.com/groovy/all/amule-common/download") 
[*][amule-utils]("https://packages.ubuntu.com/groovy/amd64/amule-utils/download") 
[*][amule-utils-gui]("https://packages.ubuntu.com/groovy/amd64/amule-utils-gui/download") 
[*][amule-daemon]("https://packages.ubuntu.com/groovy/amd64/amule-daemon/download") 
[*][libwxgtk]("https://packages.ubuntu.com/groovy/amd64/libwxgtk3.0-gtk3-0v5/download") 
[*][libwxbase]("https://packages.ubuntu.com/groovy/amd64/libwxbase3.0-0v5/download") 
[/LIST]

One more packet was recommended on installation:
[LIST]
[*][amule-gnome-support download]("https://packages.ubuntu.com/groovy/all/amule-gnome-support/download") 
[/LIST]

So I changed in an opened terminal window into the download directory and used the command:

```
$ sudo apt install ./amule*.deb ./libwxgtk*.deb ./libwxbase*.deb
```


 
Happy amule_ing [SIZE=2]:guitar:[/SIZE]

---

