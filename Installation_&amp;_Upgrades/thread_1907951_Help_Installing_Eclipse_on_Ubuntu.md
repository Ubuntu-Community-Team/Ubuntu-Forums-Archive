---
title: "Help Installing Eclipse on Ubuntu"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2012-01-12
Hi!  (quick link just look at [COLOR="red"]Question:[/COLOR] for find out what you could comment to)

I am updating Eclipse to version: 3.7.1 I download it from [here]("http://www.eclipse.org/downloads/") (the classic one)

It gave a file name: eclipse-SDK-3.7.1-linux-gtk.tar.gz (which I download)

Now to what I did, I did a big of google up to find proper installation.
and I have found [here]("http://flurdy.com/docs/eclipse/install.html")The following steps:

[PHP]
tar xzf wtp-all-in-one-sdk-1.0-linux-gtk.tar.gz
 sudo mv eclipse /opt/eclipse cd /opt sudo chown -R root:root eclipse
(I didnt move it with this command but the same principle)
 sudo chmod -R +r eclipse
 sudo chmod +x `sudo find eclipse -type d`
[/PHP]

[COLOR="Red"]Question:[/COLOR] sudo chmod +x `sudo find eclipse -type d` (no sure about this)

And then:

Then create an eclipse executable in your path

```

sudo touch /usr/bin/eclipse  ([COLOR="Red"]question:[/COLOR] not sure what is doing here)
 sudo chmod 755 /usr/bin/eclipse
 sudoedit /usr/bin/eclipse

```

Sudoedit should have this content ([COLOR="red"]Question here[/COLOR]. I have not do it so far)

[PHP]
#!/bin/sh
 #export MOZILLA_FIVE_HOME="/usr/lib/mozilla/"
 export ECLIPSE_HOME="/opt/eclipse"

 $ECLIPSE_HOME/eclipse $*
[/PHP]

Then create a gnome menu item ([COLOR="red"]question[/COLOR] is this right?)

[PHP]
sudoedit /usr/share/applications/eclipse.desktop 
[/PHP]

With this contents

[PHP]
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
[/PHP]

And then I suppose to do this

[PHP]
/opt/eclipse/eclipse -clean
[/PHP]

Could you please comment on those steps (looking to see if they are right and possible security risk)?

I not sure what tough did a part I think the previous to that was pretty normal.

I have not done anything further because I could go the /opt/eclipse/ folder and double click on the launcher and it start ok so far!

Thanks for your help!

---

