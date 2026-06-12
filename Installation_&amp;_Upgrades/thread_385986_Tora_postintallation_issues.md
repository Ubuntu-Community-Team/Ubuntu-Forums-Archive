---
title: "Tora: postintallation issues"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by marianom on 2007-03-16
Following [this thread]("http://www.ubuntuforums.org/showthread.php?t=189381") I was able to install tora with support for both Postgre and Oracle. However, now I'm facing two new problems:

1- I originally installed tora from synaptic (where I found out it has no oracle support) and make the menu entry in Applications->Programming. I then downloaded the source code and prior to install it I uninstalled the one previously installed. I then updated the menu entry and when I click it, it's still using the old tora (I repeat: I unistalled it). I even make a desktop entry with no luck.
Here's the file:

```
[Desktop Entry]
Categories=Database;Office;Development;KDE;Qt
Comment=A graphical toolkit for database administration and development
Comment[de]=Grafisches Toolkit zur Administration und Entwicklung von Datenbanken
Comment[es_AR]=A graphical toolkit for database administration and development
Comment[fr]=Une boite à outil graphique pour l'administration et le développement de base de données
Encoding=UTF-8
Exec=/usr/local/tora/bin/tora
Icon=/usr/local/tora/icons/tora.xpm
Icon[es_AR]=/usr/local/tora/icons/tora.xpm
MimeType=application/x-tora
Name=TOra
Name[es_AR]=TOra
NoDisplay=false
Terminal=false
Type=Application
X-KDE-StartupNotify=true

```

As you can see it's pointing to /usr/local/tora/bin/tora (where the correct version exists) but if I call it from the command line directly:
```
./usr/local/tora/bin/tora
``` 
it uses the new version (with oracle support) but using the desktop launcher or the menu launcher it uses the old tora (without oracle support). Did I mention I uninstall it?
Anyone can suggest a way to make it behaviour the right way?

2- After installing the oracle-supported version, I'm getting notices that a new version exists in the repos. Via synaptic I forced my existing version as the right one but I'm still getting the notice. Can anyone suggest a way to make this notice dissapear?

Thanks in advance.

---

### Post by KeighleHawk on 2007-03-20
I can't really answer your questions per se, but I have the following observations from my install:

1.  I found I could not actually run tora directly.  It was not picking up my environment variables properly.  Not sure why.  I had to create a small shell script and call that from the menu Launcher. (reference this link [http://www.ubuntuforums.org/showthread.php?t=362470&highlight=tora](http://www.ubuntuforums.org/showthread.php?t=362470&highlight=tora))

2.  Someone else mentioned "locking" the compiled version as the correct one.  Not sure if that is what you meant by setting yours as the "correct" one.

---

### Post by marianom on 2007-03-20
Hi again.
yeah, that's what I did but the update icon is still there looking at me, every day and every night and I think it's smiling at me.... :)
Anyway, thanks for the tip.

---

### Post by KeighleHawk on 2007-03-20
well, I guess you could cheat like I seem to have.  When I compiled it, I let configure do mostly default stuff not realizing it would actually install in a different directory.  So I actually have both installed so I am not seeing the update button :-)

---

