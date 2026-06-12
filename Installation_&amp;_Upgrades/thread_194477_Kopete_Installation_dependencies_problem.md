---
title: "Kopete Installation dependencies problem"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-06-11
I downloaded the source package of kopete 0.12 from kopete.kde.org, and I extract it to /tmp, and I do ./configure (/tmp/kopete-0.12.0) however, I encounter this message.

-
You have disabled or you are missing required librairies required to compile Jabber Jingle voice support.
Jingle is a new Jabber standard that define a signaling protocol via XMPP for peer-to-peer applications.
Jingle audio is compatible with Google Talk voice offering.

Required Jingle dependencies are listed on this page:
[http://wiki.kde.org/tiki-index.php?page=Kopete+Jabber+Jingle](http://wiki.kde.org/tiki-index.php?page=Kopete+Jabber+Jingle)

You're missing OpenSLP, or the OpenSLP devel package.
Browsing in krfb and krdc will not be possible.
If you want browsing support in krfb, you should consider
installing it.
Have a look at [http://www.openslp.org/](http://www.openslp.org/) or find a binary
package for your platform.


You're missing the XMMS libraries, or the libxmms development package.
Without libxmms Kopete's NowListening plugin won't be able to talk to
the XMMS music player. If you want Kopete's NowListening plugin to
support XMMS, have a look at [http://www.xmms.org/](http://www.xmms.org/) or find a
binary package for your system.
--

I wasnt able to browse to [http://wiki.kde.org/tiki-index.php?page=Kopete+Jabber+Jingle](http://wiki.kde.org/tiki-index.php?page=Kopete+Jabber+Jingle), it says they having problem on mysql or cant connect. and I already installed the libxmms-ruby, I dont have the libxmms-dev. 

Im very sorry but this is my first time doing installation using the source package, which I really want to learn how to install this way, installaling with .deb would be very easy, guess its time for me to learn to install in other way.

Any help here would be highly appreciated. 

Thanks so much in advance.

---

### Post by pelle.k on 2006-06-11
Is there a reason the kopete package in kubuntu doesn't fit you?

---

### Post by firephoto on 2006-06-12
Along with the needed packages to build kde stuff on ubuntu, I only had to compile and install ortp-0.7.1, then kopete compiled fine, all the rest of the deps I installed via adept.

Then I did a:
./configure --prefix=`kde-config --prefix` --enable-jingle
make
sudo make install

The openslp and xmms messages are just leftovers from kdenetwork I think, nothing to worry about really.

Voice works for about a minute then I'm not heard anymore. Not sure what the problem is, works ok on my gentoo install with the usual freezes with failed voice connects. Not sure what's ended up being different on kubuntu.

---

### Post by wizzkid on 2006-06-12
where can i get the ortp-0.7.1? :)  i cant find it on adept.

also, it took me 10mins or so when i type make, is that normail? all i can see is bunch of text...

Thanks.

---

### Post by firephoto on 2006-06-12
You can get it here.
[http://linphone.org/ortp/sources/ortp-0.7.1.tar.gz](http://linphone.org/ortp/sources/ortp-0.7.1.tar.gz)

10 minutes for 'make' on kopete is pretty good btw. ;)

---

### Post by wizzkid on 2006-06-12
Thanks.. :) I successfully installed the kopete 0.12.0 source package :) unfortunately, there is no voice chat for yahoo :(

thanks a lot :)

---

### Post by carla on 2007-03-08
> **firephoto said:**
> You can get it here.
[http://linphone.org/ortp/sources/ortp-0.7.1.tar.gz](http://linphone.org/ortp/sources/ortp-0.7.1.tar.gz)

Just to update this info, in case anyone needs it now:

current links:
[code info of ortp]("http://linphone.org/index.php/v2/code_review/ortp")
[latest sources at savannah.nongnu.org]("http://download.savannah.nongnu.org/releases/linphone/ortp/sources/")

---

### Post by chikko on 2007-04-07
i'm trying to build kopete 0.12.2 from source (with the emoticon patch in it).
the ./configure went well (the openSPL was missing but i understood it's not a big deal) but after about 15 seconds from the begining of 'make' i get these lines:

```

'
Making all in avdevice
make[4]: Entering directory `/home/chikko/programs/kopete-0.12.2/kopete/libkopete/avdevice'
if /bin/bash ../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DKDE_NO_COMPAT -DQT_NO_COMPAT -DQT_NO_CAST_ASCII -DQT_NO_ASCII_CAST -I../../../kopete/libkopete -I../../../kopete/libkopete -I../../../kopete/libkopete/avdevice -I../../../kopete/libkopete/ui -I../../../kopete/libkopete/ui -I../../../kopete/libkopete/private -I../../../kopete/libkopete/ui -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT -D_FILE_OFFSET_BITS=64  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT videodevice.lo -MD -MP -MF ".deps/videodevice.Tpo" -c -o videodevice.lo videodevice.cpp; \
        then mv -f ".deps/videodevice.Tpo" ".deps/videodevice.Plo"; else rm -f ".deps/videodevice.Tpo"; exit 1; fi
/usr/include/linux/videodev2.h:708: error: '__s64' does not name a type
videodevice.cpp: In member function 'int Kopete::AV::VideoDevice::selectInput(int)':
videodevice.cpp:752: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'int Kopete::AV::VideoDevice::setInputParameters()':
videodevice.cpp:798: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::getBrightness()':
videodevice.cpp:1294: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::setBrightness(float)':
videodevice.cpp:1317: warning: converting to '__u16' from 'float'
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::getContrast()':
videodevice.cpp:1332: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::setContrast(float)':
videodevice.cpp:1355: warning: converting to '__u16' from 'float'
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::getSaturation()':
videodevice.cpp:1370: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::setSaturation(float)':
videodevice.cpp:1393: warning: converting to '__u16' from 'float'
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::getWhiteness()':
videodevice.cpp:1408: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::setWhiteness(float)':
videodevice.cpp:1431: warning: converting to '__u16' from 'float'
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::getHue()':
videodevice.cpp:1446: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'float Kopete::AV::VideoDevice::setHue(float)':
videodevice.cpp:1469: warning: converting to '__u16' from 'float'
videodevice.cpp: In member function 'bool Kopete::AV::VideoDevice::getAutoBrightnessContrast()':
videodevice.cpp:1485: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'bool Kopete::AV::VideoDevice::setAutoBrightnessContrast(bool)':
videodevice.cpp:1494: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'bool Kopete::AV::VideoDevice::getAutoColorCorrection()':
videodevice.cpp:1506: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'bool Kopete::AV::VideoDevice::setAutoColorCorrection(bool)':
videodevice.cpp:1515: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'bool Kopete::AV::VideoDevice::getImageAsMirror()':
videodevice.cpp:1526: warning: comparison between signed and unsigned integer expressions
videodevice.cpp: In member function 'bool Kopete::AV::VideoDevice::setImageAsMirror(bool)':
videodevice.cpp:1535: warning: comparison between signed and unsigned integer expressions
make[4]: *** [videodevice.lo] 1 &#1492;&#1500;&#1511;&#1514;
make[4]: Leaving directory `/home/chikko/programs/kopete-0.12.2/kopete/libkopete/avdevice'
make[3]: *** [all-recursive] 1 &#1492;&#1500;&#1511;&#1514;
make[3]: Leaving directory `/home/chikko/programs/kopete-0.12.2/kopete/libkopete'
make[2]: *** [all-recursive] 1 &#1492;&#1500;&#1511;&#1514;
make[2]: Leaving directory `/home/chikko/programs/kopete-0.12.2/kopete'
make[1]: *** [all-recursive] 1 &#1492;&#1500;&#1511;&#1514;
make[1]: Leaving directory `/home/chikko/programs/kopete-0.12.2'
make: *** [all] 2 &#1492;&#1500;&#1511;&#1514;
chikko@fistuk:~/programs/kopete-0.12.2$     

```

what might be the problem here..?  :(

thanks! :)

btw:
&#1514;&#1511;&#1500;&#1492; - means error.

---

