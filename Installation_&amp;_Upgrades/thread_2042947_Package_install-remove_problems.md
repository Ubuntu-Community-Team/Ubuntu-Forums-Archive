---
title: "Package install-remove problems"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by msdundar on 2012-08-15
Hello,

I'm quite unexperienced about Ubuntu, so thanks for your patience in advance :)

Last week, I tried to install RubyMine IDE. But it required OracleJDK package instead of OpenJDK. Fortunately I succeeded to install OracleJDK by reading lots of blog posts, user experiences etc.

Anyway the installation was a painful process and probably I have done some mistakes. Right now, I'm getting an repetitive error about OracleJDK whenever I try to install or remove a package. The packages which I tried to install or remove are not related with OracleJDK I think. This error message is just popping out from the history.

Here is the error message pasted to EverNote: [http://goo.gl/UaiP0](http://goo.gl/UaiP0)

Thanks in advance!

---

### Post by QIII on 2012-08-15
Would you please post the error inside code tags (by clicking the # symbol above the input box.)

Thanks.

---

### Post by Whovian on 2012-08-15
It seems you have dependency errors related to JDK 7. Try removing all of JDK 7 an than reinstalling it. 
Or follow this [article]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux")

(Sorry if this doesn't really help an my messages my vary cause  I'm having to use public computers atm.)

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> Would you please post the error inside code tags (by clicking the # symbol above the input box.)

Thanks.

Here it is. Kind of long message, that's why I pasted to EverNote.

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 291358 files and directories currently installed.)
Removing hamster-applet ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up oracle-java7-installer (7u5-0~webupd8~5) ...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-15 23:01:15--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) zmleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 balanlyor... balant kuruldu.
HTTP istei gnderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kayt yeri: `./cookie.txt'

     0K                                                      100%  807K=0,001s

2012-08-15 23:01:27 (807 KB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-15 23:01:27--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) zmleniyor... 77.67.21.231, 77.67.21.241
download.oracle.com (download.oracle.com)[77.67.21.231]:80 balanlyor... balant kuruldu.
HTTP istei gnderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-15 23:01:38--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) zmleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 balanlyor... balant kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine gvenlii gzard ederek balanmak iin `--no-check-certificate' seeneini kullann.
download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of netbeans:
 netbeans depends on openjdk-6-jdk | java6-sdk | java7-sdk; however:
  Package openjdk-6-jdk is not installed.
  Package oracle-java7-installer which provides openjdk-6-jdk is not configured yet.
  Package java6-sdk is not installed.
  Package oracle-java7-installer which provides java6-sdk is not configured yet.
  Package openjdk-6-jdk which provides java6-sdk is not installed.
  Package java7-sdk is not installed.
  Package oracle-java7-installer which provides java7-sdk is not configured yet.
dpkg: error processing netbeans (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 oracle-java7-installer
 netbeans
Error in function: 
Setting up oracle-java7-installer (7u5-0~webupd8~5) ...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-15 23:01:46--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) zmleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 balanlyor... balant kuruldu.
HTTP istei gnderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kayt yeri: `./cookie.txt'

     0K                                                      100% 13,8M=0s

2012-08-15 23:01:48 (13,8 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-15 23:01:48--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) zmleniyor... 77.67.21.231, 77.67.21.241
download.oracle.com (download.oracle.com)[77.67.21.231]:80 balanlyor... balant kuruldu.
HTTP istei gnderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-15 23:01:59--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) zmleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 balanlyor... balant kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine gvenlii gzard ederek balanmak iin `--no-check-certificate' seeneini kullann.
download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of netbeans:
 netbeans depends on openjdk-6-jdk | java6-sdk | java7-sdk; however:
  Package openjdk-6-jdk is not installed.
  Package oracle-java7-installer which provides openjdk-6-jdk is not configured yet.
  Package java6-sdk is not installed.
  Package oracle-java7-installer which provides java6-sdk is not configured yet.
  Package openjdk-6-jdk which provides java6-sdk is not installed.
  Package java7-sdk is not installed.
  Package oracle-java7-installer which provides java7-sdk is not configured yet.
dpkg: error processing netbeans (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by QIII on 2012-08-15
That article is fantastically more difficult than installing Oracle Java needs to be.  I would avoid it.

---

### Post by QIII on 2012-08-15
Can you tell me what instructions you were using to try to install Java?  Perhaps a URL?

Were you using instructions at Oracle's website?

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> Can you tell me what instructions you were using to try to install Java?  Perhaps a URL?

Were you using instructions at Oracle's website?

Yes sure, I followed these two articles:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

They are actually doing same thing but they both failed and made trouble for me, so I used both of them to learn.

---

### Post by QIII on 2012-08-15
They are actually different.  We'll have to do some cleanup in a minute.

What method were you using to install Netbeans?

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> They are actually different.  We'll have to do some cleanup in a minute.

What method were you using to install Netbeans?

I used Ubuntu Software Center to install Netbeans.

---

### Post by QIII on 2012-08-15
We need to try to get you back to a clean slate.  Be very careful because I am giving you the rm command, which deletes files permanently and immediately.

Do the following individually in order:

```
 
sudo apt-get purge netbeans
sudo apt-get install ppa-purge
sudo ppa-purge ppa:nilarimogard/webupd8
sudo ppa-purge ppa:webupd8team/java
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get clean
sudo apt-get update
```Post back the results of each command.

---

### Post by msdundar on 2012-08-15
I translated some parts to English to make things more clear

Command: sudo apt-get purge netbeans

Result:

```

Paket listeleri okunuyor... Bitti [Checking package dependencies. Done]    
Durum bilgisi okunuyor... Bitti [Checking state. Done.]
S&#305;ralanan paketler otomatik olarak kurulmu&#351;tu art&#305;k gerekli de&#287;iller: [Listed packages installed automaticly and we don't need them anymore]
  ubuntuone-couch libsqlite3-dev duplicity libreadline5 librsync1
Kald&#305;rmak için 'apt-get autoremove' komutunu kullan&#305;n [use that command to remove them]
A&#351;a&#287;&#305;daki paketler KALDIRILACAK: [These packages are going be removed]
  netbeans*
Yükseltilen: 0, Yeni Kurulan: 0, Kald&#305;r&#305;lacak: 1 [Will be removed] ve Yükseltilmeyecek: 1 [Will not be upgraded]
2 tam olarak kurulmad&#305; veya kald&#305;r&#305;lmad&#305;. [2 couldn't installed fully or couldn't removed]
Bu i&#351;lemden sonra 1.964 kB disk alan&#305; bo&#351;alacak.
Devam etmek istiyor musunuz [E/h]? [Yes/NO]
(Veritaban&#305; okunuyor... 291054 files and directories currently installed.)
netbeans kald&#305;r&#305;l&#305;yor ...
Purging configuration files for netbeans ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
oracle-java7-installer (7u5-0~webupd8~5) kuruluyor...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-16 01:07:12--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 4,95M=0s

2012-08-16 01:07:13 (4,95 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 01:07:13--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.18, 77.67.21.19
download.oracle.com (download.oracle.com)[77.67.21.18]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-16 01:07:14--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
Apport raporu yaz&#305;lmad&#305; çünkü zaten en yüksek rapor say&#305;s&#305;na ula&#351;&#305;ld&#305;
                                                                     &#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Command: sudo apt-get install ppa-purge
Result:

```
Paket listeleri okunuyor... Bitti
Ba&#287;&#305;ml&#305;l&#305;k a&#287;ac&#305; in&#351;a ediliyor.       
Durum bilgisi okunuyor... Bitti       
S&#305;ralanan paketler otomatik olarak kurulmu&#351;tu art&#305;k gerekli de&#287;iller:
  ubuntuone-couch libsqlite3-dev duplicity libreadline5 librsync1
Kald&#305;rmak için 'apt-get autoremove' komutunu kullan&#305;n
A&#351;a&#287;&#305;daki YEN&#304; paketler kurulacak:
  ppa-purge
Yükseltilen: 0, Yeni Kurulan: 1, Kald&#305;r&#305;lacak: 0 ve Yükseltilmeyecek: 1.
1 tam olarak kurulmad&#305; veya kald&#305;r&#305;lmad&#305;.
&#304;ndirilmesi gereken dosya boyutu 4.360 B
Bu i&#351;lemden sonra 57,3 kB ek disk alan&#305; kullan&#305;lacak.
Al&#305;n&#305;yor:1 http://tr.archive.ubuntu.com/ubuntu/ precise/universe ppa-purge all 0.2.8+bzr56 [4.360 B]
0sn'de 4.360 B al&#305;nd&#305; (12,3 kB/s)
Selecting previously unselected package ppa-purge.
(Veritaban&#305; okunuyor... 290959 files and directories currently installed.)
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
oracle-java7-installer (7u5-0~webupd8~5) kuruluyor...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-16 01:11:32--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 5,18M=0s

2012-08-16 01:11:33 (5,18 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 01:11:33--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.231, 77.67.21.241
download.oracle.com (download.oracle.com)[77.67.21.231]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-16 01:11:33--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
ppa-purge (0.2.8+bzr56) kuruluyor...
Apport raporu yaz&#305;lmad&#305; çünkü zaten en yüksek rapor say&#305;s&#305;na ula&#351;&#305;ld&#305;
                                                                     &#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Command: sudo ppa-purge ppa:nilarimogard/webupd8
Result:

```
Updating packages lists
PPA to be removed: nilarimogard webupd8
Package revert list generated:
 update-java/precise

Disabling nilarimogard PPA from 
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list
Updating packages lists
Paket listeleri okunuyor... Bitti
Ba&#287;&#305;ml&#305;l&#305;k a&#287;ac&#305; in&#351;a ediliyor.       
Durum bilgisi okunuyor... Bitti       
E: 'precise' da&#287;&#305;t&#305;m&#305;, 'update-java' için bulunamad&#305; [precise couldn't found for update-java]
"update-java" paketi için "precise" ar&#351;ivi bulunam&#305;yor
"update-java" paketi için "precise" ar&#351;ivi bulunam&#305;yor
A&#351;a&#287;&#305;daki paketler KALDIRILACAK: [these will be removed]
  duplicity{u} libreadline5{u} librsync1{u} libsqlite3-dev{u} 
  ubuntuone-couch{u} 
0 paket yükseltildi, 0 yeni kuruldu, 5 kald&#305;r&#305;ld&#305;, 1 [5 removed, 1 couldn't upgraded] yükseltilmedi.
Ar&#351;ivlerden 0 B veri al&#305;nacak. Paketler aç&#305;ld&#305;ktan sonra 2.757 kB serbest kalacak.
Devam etmek istiyor musunuz? [E/H/?] 
(Veritaban&#305; okunuyor... 290962 files and directories currently installed.)
duplicity kald&#305;r&#305;l&#305;yor ... [removing...]
libreadline5 kald&#305;r&#305;l&#305;yor ...
librsync1 kald&#305;r&#305;l&#305;yor ...
libsqlite3-dev kald&#305;r&#305;l&#305;yor ...
ubuntuone-couch kald&#305;r&#305;l&#305;yor ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
oracle-java7-installer (7u5-0~webupd8~5) kuruluyor... [installing]
Removing outdated cached downloads...
Downloading cookie...
--2012-08-16 01:14:12--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 4,97M=0s

2012-08-16 01:14:13 (4,97 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 01:14:13--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.231, 77.67.21.241
download.oracle.com (download.oracle.com)[77.67.21.231]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-16 01:14:13--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
Apport raporu yaz&#305;lmad&#305; çünkü zaten en yüksek rapor say&#305;s&#305;na ula&#351;&#305;ld&#305;
                                                                     &#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
Bir paketin kurulumu ba&#351;ar&#305;lamad&#305;. Geri al&#305;nmaya çal&#305;&#351;&#305;l&#305;yor:
oracle-java7-installer (7u5-0~webupd8~5) kuruluyor...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-16 01:14:14--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 6,13M=0s

2012-08-16 01:14:15 (6,13 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 01:14:15--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.231, 77.67.21.241
download.oracle.com (download.oracle.com)[77.67.21.231]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-16 01:14:15--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
&#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
                                      
Warning:  Something went wrong, packages may not have been reverted
```

I will continue.

---

### Post by msdundar on 2012-08-15
Command: sudo ppa-purge ppa:webupd8team/java
Result:

```
Updating packages lists
PPA to be removed: webupd8team java
Package revert list generated:
 oracle-java7-installer/precise

Disabling webupd8team PPA from 
/etc/apt/sources.list.d/webupd8team-java-precise.list
Updating packages lists
Paket listeleri okunuyor... Bitti
Ba&#287;&#305;ml&#305;l&#305;k a&#287;ac&#305; in&#351;a ediliyor.       
Durum bilgisi okunuyor... Bitti       
E: 'precise' da&#287;&#305;t&#305;m&#305;, 'oracle-java7-installer' için bulunamad&#305;
"oracle-java7-installer" paketi için "precise" ar&#351;ivi bulunam&#305;yor
"oracle-java7-installer" paketi için "precise" ar&#351;ivi bulunam&#305;yor
K&#305;smi kurulmu&#351; olan &#351;u paketler yap&#305;land&#305;r&#305;lacak:
  oracle-java7-installer 
Hiçbir paket kurulmayacak, yükseltilmeyecek ya da kald&#305;r&#305;lmayacak.
0 paket yükseltildi, 0 yeni kuruldu, 0 kald&#305;r&#305;ld&#305;, 0 yükseltilmedi.
Ar&#351;ivlerden 0 B veri al&#305;nacak. Paketler aç&#305;ld&#305;ktan sonra 0 B yer kullan&#305;lacak.
oracle-java7-installer (7u5-0~webupd8~5) kuruluyor...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-16 01:17:41--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.229, 91.189.89.228
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.229]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 3,78M=0s

2012-08-16 01:17:41 (3,78 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 01:17:41--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.18, 77.67.21.19
download.oracle.com (download.oracle.com)[77.67.21.18]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-16 01:17:42--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
Apport raporu yaz&#305;lmad&#305; çünkü zaten en yüksek rapor say&#305;s&#305;na ula&#351;&#305;ld&#305;
                                                                     &#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
Bir paketin kurulumu ba&#351;ar&#305;lamad&#305;. Geri al&#305;nmaya çal&#305;&#351;&#305;l&#305;yor:
oracle-java7-installer (7u5-0~webupd8~5) kuruluyor...
Removing outdated cached downloads...
Downloading cookie...
--2012-08-16 01:17:43--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.229, 91.189.89.228
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.229]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 6,45M=0s

2012-08-16 01:17:44 (6,45 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 01:17:44--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.19, 77.67.21.18
download.oracle.com (download.oracle.com)[77.67.21.19]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz [izleyen]
--2012-08-16 01:17:44--  https://edelivery.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
&#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
                                      
Warning:  Something went wrong, packages may not have been reverted
```

Command: sudo rm /var/lib/dpkg/info/oracle-java7-installer* 
Result: Done!

Command: sudo apt-get purge oracle-java7-installer*
Result:

```
Paket listeleri okunuyor... Bitti
Ba&#287;&#305;ml&#305;l&#305;k a&#287;ac&#305; in&#351;a ediliyor.       
Durum bilgisi okunuyor... Bitti       
Bilgi, 'oracle-java7-installer*' düzenli ifadesi için 'oracle-java7-installer' seçiliyor
A&#351;a&#287;&#305;daki paketler KALDIRILACAK:
  oracle-java7-installer*
Yükseltilen: 0, Yeni Kurulan: 0, Kald&#305;r&#305;lacak: 1 ve Yükseltilmeyecek: 0.
1 tam olarak kurulmad&#305; veya kald&#305;r&#305;lmad&#305;.
Bu i&#351;lemden sonra 86,0 kB disk alan&#305; bo&#351;alacak.
Devam etmek istiyor musunuz [E/h]? 
(Veritaban&#305; okunuyor... 
dpkg: uyar&#305;: `oracle-java7-installer' paketi için dosya listesi dosyas&#305; yok, olas&#305;l&#305;kla henüz pakete ait kurulmu&#351; dosya yok.
(Veritaban&#305; okunuyor... 290781 files and directories currently installed.)
oracle-java7-installer kald&#305;r&#305;l&#305;yor ...
```

Command: sudo rm /etc/apt/sources.list.d/*java*
Result: Done!

Command: sudo apt-get clean
Result : Done!

Command : sudo apt-get update
Result : Done!

---

### Post by QIII on 2012-08-15
OK.

Let's see if you get any errors here:

```
sudo apt-get upgrade
```

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> OK.

Let's see if you get any errors here:

```
sudo apt-get upgrade
```

Nop. It seems like the error fixed :) I didn't get any error message. Thanks a lot.

Actually I don't need NetBeans IDE because I'm only working on Ruby. So I though about RubyMine but it made the things so hard to deal with by asking about OracleJDK.

Right now I can start RubyMine and can run some simple snippets but some errors are flowing throught terminal, seems like related to Java. But it's still working. I'm not obsessed about RubyMine, if this software makes so much trouble I will try to find another IDE. The only reason I want to use it, I have free educational licence so I can use it for free :)

Thanks for your great interest and help again and again.

```
ask.java:113)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
	at java.lang.Thread.run(Thread.java:722)
Caused by: org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more
[ 174110]  ERROR - currency.PrioritizedFutureTask - JetBrains RubyMine 4.5.1  Build #RM-119.41 
[ 174110]  ERROR - currency.PrioritizedFutureTask - JDK: 1.7.0 
[ 174110]  ERROR - currency.PrioritizedFutureTask - VM: Java HotSpot(TM) Server VM 
[ 174110]  ERROR - currency.PrioritizedFutureTask - Vendor: Oracle Corporation 
[ 174110]  ERROR - currency.PrioritizedFutureTask - OS: Linux 
[ 174111]  ERROR - currency.PrioritizedFutureTask - Last Action: EditorBackSpace 
[ 174111]  ERROR - currency.PrioritizedFutureTask - Original exception:  
org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more

[ 174116]  ERROR - n.impl.GeneralHighlightingPass - Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
 
org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more

[ 174119]  ERROR - n.impl.GeneralHighlightingPass - JetBrains RubyMine 4.5.1  Build #RM-119.41 
[ 174119]  ERROR - n.impl.GeneralHighlightingPass - JDK: 1.7.0 
[ 174119]  ERROR - n.impl.GeneralHighlightingPass - VM: Java HotSpot(TM) Server VM 
[ 174119]  ERROR - n.impl.GeneralHighlightingPass - Vendor: Oracle Corporation 
[ 174119]  ERROR - n.impl.GeneralHighlightingPass - OS: Linux 
[ 174119]  ERROR - n.impl.GeneralHighlightingPass - Last Action: EditorBackSpace 
[ 174119]  ERROR - n.impl.GeneralHighlightingPass - Original exception:  
java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
[ 179322]  ERROR - aemon.impl.PassExecutorService - Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
 
org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more

[ 179322]  ERROR - aemon.impl.PassExecutorService - JetBrains RubyMine 4.5.1  Build #RM-119.41 
[ 179322]  ERROR - aemon.impl.PassExecutorService - JDK: 1.7.0 
[ 179323]  ERROR - aemon.impl.PassExecutorService - VM: Java HotSpot(TM) Server VM 
[ 179323]  ERROR - aemon.impl.PassExecutorService - Vendor: Oracle Corporation 
[ 179323]  ERROR - aemon.impl.PassExecutorService - OS: Linux 
[ 179323]  ERROR - aemon.impl.PassExecutorService - Last Action: Run 
[ 179323]  ERROR - aemon.impl.PassExecutorService - Original exception:  
java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
[ 179323]  ERROR - aemon.impl.PassExecutorService - Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
 
org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more

[ 179324]  ERROR - aemon.impl.PassExecutorService - JetBrains RubyMine 4.5.1  Build #RM-119.41 
[ 179324]  ERROR - aemon.impl.PassExecutorService - JDK: 1.7.0 
[ 179324]  ERROR - aemon.impl.PassExecutorService - VM: Java HotSpot(TM) Server VM 
[ 179324]  ERROR - aemon.impl.PassExecutorService - Vendor: Oracle Corporation 
[ 179324]  ERROR - aemon.impl.PassExecutorService - OS: Linux 
[ 179324]  ERROR - aemon.impl.PassExecutorService - Last Action: Run 
[ 179324]  ERROR - aemon.impl.PassExecutorService - Original exception:  
java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
[ 179325]  ERROR - currency.PrioritizedFutureTask - org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
 
java.util.concurrent.ExecutionException: org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.util.concurrent.FutureTask$Sync.innerGet(FutureTask.java:252)
	at java.util.concurrent.FutureTask.get(FutureTask.java:111)
	at com.intellij.concurrency.PrioritizedFutureTask.access$301(PrioritizedFutureTask.java:31)
	at com.intellij.concurrency.PrioritizedFutureTask$1.run(PrioritizedFutureTask.java:77)
	at com.intellij.concurrency.PrioritizedFutureTask.run(PrioritizedFutureTask.java:113)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
	at java.lang.Thread.run(Thread.java:722)
Caused by: org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more
[ 179326]  ERROR - currency.PrioritizedFutureTask - JetBrains RubyMine 4.5.1  Build #RM-119.41 
[ 179326]  ERROR - currency.PrioritizedFutureTask - JDK: 1.7.0 
[ 179326]  ERROR - currency.PrioritizedFutureTask - VM: Java HotSpot(TM) Server VM 
[ 179326]  ERROR - currency.PrioritizedFutureTask - Vendor: Oracle Corporation 
[ 179326]  ERROR - currency.PrioritizedFutureTask - OS: Linux 
[ 179326]  ERROR - currency.PrioritizedFutureTask - Last Action: Run 
[ 179326]  ERROR - currency.PrioritizedFutureTask - Original exception:  
org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more

[ 179332]  ERROR - n.impl.GeneralHighlightingPass - Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
 
org.jruby.exceptions.RaiseException: Native Exception: 'class java.lang.IllegalArgumentException'; Message: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES; StackTrace: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)
Caused by: java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	... 7 more

[ 179340]  ERROR - n.impl.GeneralHighlightingPass - JetBrains RubyMine 4.5.1  Build #RM-119.41 
[ 179340]  ERROR - n.impl.GeneralHighlightingPass - JDK: 1.7.0 
[ 179340]  ERROR - n.impl.GeneralHighlightingPass - VM: Java HotSpot(TM) Server VM 
[ 179340]  ERROR - n.impl.GeneralHighlightingPass - Vendor: Oracle Corporation 
[ 179340]  ERROR - n.impl.GeneralHighlightingPass - OS: Linux 
[ 179340]  ERROR - n.impl.GeneralHighlightingPass - Last Action: Run 
[ 179341]  ERROR - n.impl.GeneralHighlightingPass - Original exception:  
java.lang.IllegalArgumentException: No enum constant org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil.AssetsGroup.&#304;MAGES
	at java.lang.Enum.valueOf(Enum.java:236)
	at org.jetbrains.plugins.ruby.rails.codeInsight.sprockets.SprocketsUtil$AssetsGroup.valueOf(SprocketsUtil.java:69)
	at org.jetbrains.plugins.ruby.rails.codeInsight.paramDefs.AssetRefParam.<init>(AssetRefParam.java:53)
	at sun.reflect.GeneratedConstructorAccessor67.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:525)
	at org.jruby.javasupport.JavaConstructor.newInstanceDirect(JavaConstructor.java:243)

```

---

### Post by QIII on 2012-08-15
OK.  A review so far...

What we did is this:

We removed Netbeans, which needs Java to be installed first.

We installed a utility to purge a couple of PPAs you had added and then purged them.

We got rid of a file that contained info saying you had the installer lined up to be installed.

We deleted the installer package

We updated your sources list's "additional" references to get rid of Java.

We updated and cleaned up some housekeeping chores.

We got you system updated with any package updates.


Well, let's go through the process of installing Oracle Java. 

At this point you should still have OpenJDK installed.  Because OpenJDK 7 is the open source reference implementation of Oracle Java, it would be nice if we could always count on it.  Open source is best.

The problem is that many applications and websites do not recognize it, even though Oracle is heavily involved in its development.  It looks like your application is coughing on OpenJDK.

Are you ready to install Oracle Java 7 the*** easy ***way?

---

### Post by msdundar on 2012-08-15
Great explanation. I can understand many commands but things got dramatically confusing for me during my ex-OracleJDK installation try. I can see some software about OracleJDK and they seem installed on my software list. But not on Ubuntu Software Center. 

PrintScreen: [http://i48.tinypic.com/mlp9v.png](http://i48.tinypic.com/mlp9v.png)

And I'm ready for stable OracleJDK :)

---

### Post by QIII on 2012-08-15
Strangely enough, I am going to direct you back to one of the things you tried before, but this time from a clean start.

In the Java wiki in my signature, under the Oracle Java 7 section, in the "Command line methods" section under that, there is a link to webupd8.org called "Using webupd8.org's strikingly simple method".  You will probably recognize it.  It is the newest version and the one that would have worked just fine if you had found that one first.

Let me know how that goes.

---

### Post by msdundar on 2012-08-15
Command: sudo add-apt-repository ppa:webupd8team/java
Result: 
```
You are about to add the following PPA to your system:
 Oracle Java (JDK) Installer (automatically downloads and installs Oracle JDK7). There are no actual Java files in this PPA. More info: http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
 More info: https://launchpad.net/~webupd8team/+archive/java
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.gURLQMAXCq --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: EEA14886 anahtar&#305; keyserver.ubuntu.com sunucusunun hkp adresinden isteniyor
gpg: anahtar EEA14886: "Launchpad VLC" de&#287;i&#351;medi (Launchpad VLC didn't changed)
gpg: &#304;&#351;lenmi&#351; toplam miktar: 1 
gpg:              de&#287;i&#351;medi: 1 (didn't changed)

```

Command:
sudo apt-get install oracle-java7-installer

Result:

```
S&#305;ralanan paketler otomatik olarak kurulmu&#351;tu art&#305;k gerekli de&#287;iller:
  unity-lens-video libboost-serialization1.46.1 unity-scope-video-remote
  libunity-misc4 indicator-printers
Kald&#305;rmak için 'apt-get autoremove' komutunu kullan&#305;n
Önerilen paketler:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
A&#351;a&#287;&#305;daki YEN&#304; paketler kurulacak:
  oracle-java7-installer
Yükseltilen: 0, Yeni Kurulan: 1, Kald&#305;r&#305;lacak: 0 ve Yükseltilmeyecek: 28.
&#304;ndirilmesi gereken dosya boyutu 15,3 kB
Bu i&#351;lemden sonra 86,0 kB ek disk alan&#305; kullan&#305;lacak.
Al&#305;n&#305;yor:1 http://ppa.launchpad.net/webupd8team/java/ubuntu/ precise/main oracle-java7-installer all 7u6-0~webupd8~0 [15,3 kB]
0sn'de 15,3 kB al&#305;nd&#305; (36,7 kB/s)               
Paketler önyap&#305;land&#305;r&#305;l&#305;yor ...
Selecting previously unselected package oracle-java7-installer.
(Veritaban&#305; okunuyor... 290641 files and directories currently installed.)
Unpacking oracle-java7-installer (from .../oracle-java7-installer_7u6-0~webupd8~0_all.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
oracle-java7-installer (7u6-0~webupd8~0) kuruluyor...
Removing outdated cached downloads...
`jdk-7u5-linux-i586.tar.gz' silindi
Downloading cookie...
--2012-08-16 02:59:04--  http://launchpadlibrarian.net/98645053/cookie.txt
launchpadlibrarian.net (launchpadlibrarian.net) çözümleniyor... 91.189.89.228, 91.189.89.229
launchpadlibrarian.net (launchpadlibrarian.net)[91.189.89.228]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 200 OK
Uzunluk: 1053 (1,0K) [text/plain]
Kay&#305;t yeri: `./cookie.txt'

     0K                                                      100% 1,60M=0,001s

2012-08-16 02:59:04 (1,60 MB/s) - `./cookie.txt' kaydedildi [1053/1053]

Downloading Oracle Java 7...
--2012-08-16 02:59:04--  http://download.oracle.com/otn-pub/java/jdk/7u6-b24/jdk-7u6-linux-i586.tar.gz
download.oracle.com (download.oracle.com) çözümleniyor... 77.67.21.19, 77.67.21.18
download.oracle.com (download.oracle.com)[77.67.21.19]:80 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HTTP iste&#287;i gönderildi, cevap bekleniyor... 302 Moved Temporarily
Yer: https://edelivery.oracle.com/otn-pub/java/jdk/7u6-b24/jdk-7u6-linux-i586.tar.gz [izleyen]
--2012-08-16 02:59:05--  https://edelivery.oracle.com/otn-pub/java/jdk/7u6-b24/jdk-7u6-linux-i586.tar.gz
edelivery.oracle.com (edelivery.oracle.com) çözümleniyor... 23.14.138.174
edelivery.oracle.com (edelivery.oracle.com)[23.14.138.174]:443 ba&#287;lan&#305;l&#305;yor... ba&#287;lant&#305; kuruldu.
HATA: cannot verify edelivery.oracle.com's certificate, issued by `/C=US/O=Akamai Technologies Inc/CN=Akamai Subordinate CA 3':
  Unable to locally verify the issuer's authority.
edelivery.oracle.com adresine güvenli&#287;i gözard&#305; ederek ba&#287;lanmak için `--no-check-certificate' seçene&#287;ini kullan&#305;n.
download failed
Oracle JDK 7 is NOT installed.
dpkg: oracle-java7-installer (--configure) i&#351;leminde hata:
 installed post-installation script alt i&#351;lemi ç&#305;k&#305;&#351; durumunda hata döndürdü : 1
&#304;&#351;lem s&#305;ras&#305;nda hatalar bulundu:
 oracle-java7-installer
N: Ignoring file 'mozillateam-firefox-stable-natty.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'gnome3-team-gnome3-oneiric.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nilarimogard-webupd8-precise.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'mozillateam-firefox-stable-natty.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'gnome3-team-gnome3-oneiric.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nilarimogard-webupd8-precise.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Error again.

Command: java -version
Output:
```
java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) Server VM (build 21.0-b17, mixed mode)
```

---

### Post by QIII on 2012-08-15
Is download.oracle.com in your list of sources?  It looks like it is trying to control this.  I'm on the train on my cell phone on my way home from work, so I can't look at a computer right now.

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> Is download.oracle.com in your list of sources?  It looks like it is trying to control this.  I'm on the train on my cell phone on my way home from work, so I can't look at a computer right now.

I didn't do anything specifically about adding download.oracle.com to my sources. How can I check?

---

### Post by QIII on 2012-08-15
Don't worry about download.oracle.com.  I just checked.  That's coming from the webupd8 package and is normal.

I'm looking in to the error you are getting.

---

### Post by QIII on 2012-08-15
I think I recognize Turkish there (am I right?)

The problem is that a certificate is not being recognized.  I'm wondering if, since the certificate is issued in the US, there might be some issue with the certificate on your end legally.

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> I think I recognize Turkish there (am I right?)

The problem is that a certificate is not being recognized.  I'm wondering if, since the certificate is issued in the US, there might be some issue with the certificate on your end legally.

Yes it is Turkish :) I don't think it's related about country because I tried these steps in Sweden also and got same error.

---

### Post by QIII on 2012-08-15
Typically I wouldn't think so either, since a certificate in this case is just the two machines agreeing that the content is what it is advertised to be based on the certificate issuer's trustworthiness.

Same machine in both cases?

---

### Post by msdundar on 2012-08-15
> **QIII said:**
> Typically I wouldn't think so either, since a certificate in this case is just the two machines agreeing that the content is what it is advertised to be based on the certificate issuer's trustworthiness.

Same machine in both cases?

Yes same machine. I tried just 10 days ago in Sweden with same laptop :/

---

### Post by QIII on 2012-08-15
Could be as simple as a DNS cache entry.  A proxy or incorrect IP address.

Try issuing the following and then retrying the install:```
sudo apt-get install nscd
``````
sudo /etc/init.d/nscd restart
```

---

