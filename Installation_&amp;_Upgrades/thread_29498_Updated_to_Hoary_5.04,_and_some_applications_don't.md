---
title: "Updated to Hoary 5.04, and some applications don't work"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by galder on 2005-04-24
Hello everybody,

I have upgraded my 4.50 Ubuntu to 5.04. My problem comes because when I try to open a Mp3 file with xmms, it does not work. I have the same problem with my Mozilla Thunderbird. It starts but never works, and a message appears telling me that the application does not respond, and if I want to force it to close.

Thank you very much in advance.

Best regards,

Galder

---

### Post by alastair on 2005-04-24
What plugins are installed for XMMS? i.e.

dpkg -l "*xmms*"

I have :

ii  xmms-mad     0.7-1     mp3 input plugin for xmms based on libmad

---

### Post by galder on 2005-04-25
Hi friend,

When I'm back at home, I will take a look and tell you the plugins I have instaled. I think I installed one, in order to listen to the wma microsoft files. It could be the problem? I will write at night.

Thank you in advance.

Galder

---

### Post by galder on 2005-04-25
This is what appears ... dpkg -l "*xmms*"

un  alsa-xmms      <batez>        (ez dago azalapen eskuragarririk)
ii  xmms           1.2.10-2ubuntu Versatile X audio player that looks like Win
ii  xmms-dev       1.2.10-2ubuntu XMMS development static library and header f
un  xmms-modplug   <batez>        (ez dago azalapen eskuragarririk)
un  xmms-vorbis    <batez>        (ez dago azalapen eskuragarririk)

ez dago azalapen eskuragarririk (There is no explanations)

dpkg -l "*thunderbird*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Izena                     Bertsioa                  Azalpena
+++-=========================-=========================-==================================================================
ii  mozilla-thunderbird       1.0.2-1                   Mozilla Thunderbird standalone mail client
ii  mozilla-thunderbird-enigm 0.90.2-1                  Enigmail - GPG support for Mozilla Thunderbird
un  mozilla-thunderbird-inspe <batez>                   (ez dago azalapen eskuragarririk)
un  mozilla-thunderbird-offli <batez>                   (ez dago azalapen eskuragarririk)
un  mozilla-thunderbird-typea <batez>                   (ez dago azalapen eskuragarririk)

Thank you in advance

---

### Post by alastair on 2005-04-25
So .... you need to install MP3 support.

See :

[http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)
[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

I think "xmms-mad" is in "universe".

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=galder] I have the same problem with my Mozilla Thunderbird. It starts but never works, and a message appears telling me that the application does not respond, and if I want to force it to close.

[/QUOTE]

Try unistalling Thunderbird then resinstalling it.

---

