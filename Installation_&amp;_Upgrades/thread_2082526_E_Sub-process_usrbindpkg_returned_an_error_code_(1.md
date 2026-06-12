---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by jah2007 on 2012-11-09
I cant install or uppdate anything on my system 12.04 I get the error...



joel@Joel-PC:~$ sudo apt-get install -f
[sudo] password for joel: 
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Korrigerar beroenden.... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  kde-l10n-sv language-pack-kde-sv-base language-pack-kde-zh-hans-base
  calligra-l10n-engb calligra-l10n-sv calligra-l10n-zhcn language-pack-kde-en
  kde-l10n-engb language-pack-kde-sv language-pack-zh-hans-base kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans language-pack-kde-en-base
Använd "apt-get autoremove" för att ta bort dem.
Följande ytterligare paket kommer att installeras:
  libqt4-xmlpatterns
Följande paket kommer att uppgraderas:
  libqt4-xmlpatterns
1 att uppgradera, 0 att nyinstallera, 0 att ta bort och 22 att inte uppgradera.
15 är inte helt installerade eller borttagna.
Behöver hämta 0 B/1 033 kB arkiv.
Efter denna åtgärd kommer ytterligare 0 B utrymme användas på disken.
Vill du fortsätta [J/n]? J
dpkg: fel vid hantering av libqt4-xmlpatterns (--configure):
 libqt4-xmlpatterns:amd64 4:4.8.1-0ubuntu4.2 cannot be configured because libqt4-xmlpatterns:i386 is in a different version (4:4.8.1-0ubuntu4.3)
dpkg: fel vid hantering av libqt4-xmlpatterns:i386 (--configure):
 libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4.3 cannot be configured because libqt4-xmlpatterns:amd64 is in a different version (4:4.8.1-0ubuntu4.2)
dpkg: beroendeproblem förhindrar konfigurering av libqt4-declarative:i386:
 libqt4-declarative:i386 är beroende av libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-xmlpatterns:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-declarative:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-declarative:
 libqt4-declarative är beroende av libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3), men:
  Versionen av libqt4-xmlpatterns på systemet är 4:4.8.1-0ubuntu4.2.
dpkg: fel vid hantering av libqt4-declarative (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqtgui4:i386:
 libqtgui4:i386 är beroende av libqt4-declarative (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-declarative:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqtgui4:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar koIngen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                                                              Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                         Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
    Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                               Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
          Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                                     nfigurering av libqtgui4:
 libqtgui4 är beroende av libqt4-declarative (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-declarative har inte konfigurerats ännu.
dpkg: fel vid hantering av libqtgui4 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-designer:
 libqt4-designer är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-designer (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-designer:i386:
 libqt4-designer:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-designer:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-opengl:
 libqt4-opengl är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-opengl (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-opengl:i386:
 libqt4-opengl:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-opengl:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-qt3support:
 libqt4-qt3support är beroende av libqt4-designer (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-designer har inte konfigurerats ännu.
 libqt4-qt3support är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-qt3support (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-qt3support:i386:
 libqt4-qt3support:i386 är beroende av libqt4-designer (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-designer:i386 har inte konfigurerats ännu.
 libqt4-qt3support:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-qt3support:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-scripttools:i386:
 libqt4-scripttools:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-scripttools:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-svg:
 libqt4-svg är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-svg (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-svg:i386:
 libqt4-svg:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-svg:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
Fel uppstod vid hantering:
 libqt4-xmlpatterns
 libqt4-xmlpatterns:i386
 libqt4-declarative:i386
 libqt4-declarative
 libqtgui4:i386
 libqtgui4
 libqt4-designer
 libqt4-designer:i386
 libqt4-opengl
 libqt4-opengl:i386
 libqt4-qt3support
 libqt4-qt3support:i386
 libqt4-scripttools:i386
 libqt4-svg
 libqt4-svg:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by teward on 2012-11-09
Didn't you [just post to Ask Ubuntu about this]("http://askubuntu.com/questions/215144/e-sub-process-usr-bin-dpkg-returned-an-error-code-1")?

It helps to have your stuff posted in english, by the way...  so that other users who can't read your language can understand this

---

### Post by jah2007 on 2012-11-09
> **Lord of Time said:**
> Didn't you [just post to Ask Ubuntu about this]("http://askubuntu.com/questions/215144/e-sub-process-usr-bin-dpkg-returned-an-error-code-1")?

It helps to have your stuff posted in english, by the way...  so that other users who can't read your language can understand this (google translate sucks btw)

How can i translate it then?

---

### Post by jah2007 on 2012-11-09
installArchives() failed: dpkg: error processing libqt4-xmlpatterns (--configure):
 libqt4-xmlpatterns:amd64 4:4.8.1-0ubuntu4.2 cannot be configured because libqt4-xmlpatterns:i386 is in a different version (4:4.8.1-0ubuntu4.3)
dpkg: error processing libqt4-xmlpatterns:i386 (--configure):
 libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4.3 cannot be configured because libqt4-xmlpatterns:amd64 is in a different version (4:4.8.1-0ubuntu4.2)
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declarative:i386 depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-xmlpatterns:i386 is not configured yet.
dpkg: error processing libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3); however:
  Version of libqt4-xmlpatterns on system is 4:4.8.1-0ubuntu4.2.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-declarative:i386 is not configured yet.
dpkg: error processing libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
 libqtgui4 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-declarative is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:i386:
 libqt4-designer:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-designer:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:i386:
 libqt4-opengl:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-opengl:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:i386:
 libqt4-qt3support:i386 depends on libqt4-designer (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-designer:i386 is not configured yet.
 libqt4-qt3support:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-qt3support:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-scripttools:i386:
 libqt4-scripttools:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-scripttools:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:i386:
 libqt4-svg:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-svg:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-xmlpatterns
 libqt4-xmlpatterns:i386
 libqt4-declarative:i386
 libqt4-declarative
 libqtgui4:i386
 libqtgui4
 libqt4-designer
 libqt4-designer:i386
 libqt4-opengl
 libqt4-opengl:i386
 libqt4-qt3support
 libqt4-qt3support:i386
 libqt4-scripttools:i386
 libqt4-svg
 libqt4-svg:i386
Error in function: 
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3); however:
  Version of libqt4-xmlpatterns on system is 4:4.8.1-0ubuntu4.2.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libqt4-xmlpatterns (--configure):
 libqt4-xmlpatterns:amd64 4:4.8.1-0ubuntu4.2 cannot be configured because libqt4-xmlpatterns:i386 is in a different version (4:4.8.1-0ubuntu4.3)
dpkg: error processing libqt4-xmlpatterns:i386 (--configure):
 libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4.3 cannot be configured because libqt4-xmlpatterns:amd64 is in a different version (4:4.8.1-0ubuntu4.2)
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-declarative is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declarative:i386 depends on libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-xmlpatterns:i386 is not configured yet.
dpkg: error processing libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on libqt4-declarative (= 4:4.8.1-0ubuntu4.3); however:
  Package libqt4-declarative:i386 is not configured yet.
dpkg: error processing libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:i386:
 libqt4-svg:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-svg:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:i386:
 libqt4-opengl:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-opengl:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:i386:

---

### Post by mörgæs on 2012-11-10
Closing the thread. Please don't double-post.

---

