---
title: "Sth has screwed my system!!!"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by ricpat51 on 2008-10-22
Please guys, I'm a newbie yet so be patient with me ok?!
The thing is, yesterday my system was totally ok I used it and everything was fine. But today when I turned my pc on everything is a complete mess. I don't know what happened. Fist, the sound card seems to be gone, as well the wireless card therefore the internet conection. Then, whenever I try to access these devices or everything else in my system I got a message saying that I'm not authorized to do those things and the worst is that, although I'm the system's admin, I can't login as root anymore unless I boot the system in recovery mode.
The only diferent thing I remember of having done yestarday was a system update that, actually I don't even record what was it. It just showed up the update icon in the desktop and done. There is a way of knowing which updates where these? Through a log, maybe? And if so, there is a way of fix my system again or will I have to re-intall it??? Please help me, as I've said I'm a complete newbie yet.

Thank you in advance and sorry for my English

Best regards to all of you

---

### Post by pebo on 2008-10-22
In a terminal type ```
sudo less /var/log/apt/term.log
```There was a kernel update the other day - look for anything unusual relating to the installation of it.
And don't apologise for your english - it's better than most of ours :)

---

### Post by Paul41 on 2008-10-22
This my help with your sudo problem.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by ricpat51 on 2008-10-22
Guys really thank you for your help and pebo thanks for your compliment man but I own most of my English to Google! ;)

Well, about the term.log, its last lines says:

```
Log started: 2008-10-20  19:42:40
(Lendo banco de dados ... 126985 arquivos e diretórios 

atualmente instalados.)
Removendo audacity ...
Removendo libflac++6 ...
Removendo vlc ...
Removendo vlc-plugin-pulse ...
Removendo vlc-nox ...
Removendo libvcdinfo0 ...
Removendo libiso9660-5 ...
Removendo libsdl-image1.2 ...
Removendo libtar ...
Removendo libvlc0 ...
Removendo libwxgtk2.6-0 ...
Removendo libwxbase2.6-0 ...
Removendo libxosd2 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-10-20  19:42:45

Log started: 2008-10-20  22:14:47
Selecionando pacote 

previamente não selecionado java-common.
(Lendo banco de dados ... 126332 arquivos e diretórios atualmente instalados.)
Descompactando java-common (de .../java-common_0.28ubuntu3_all.deb) ...
Selecionando pacote previamente não selecionado sun-java6-jre.
Descompactando sun-java6-jre (de .../sun-java6-jre_6-07-3ubuntu2_all.deb) ...
Selecionando pacote previamente não selecionado odbcinst1debian1.
Descompactando odbcinst1debian1 (de .../odbcinst1debian1_2.2.11-16build1_i386.deb) ...
Selecionando pacote previamente não selecionado unixodbc.
Descompactando unixodbc (de .../unixodbc_2.2.11-16build1_i386.deb) ...
Selecionando pacote previamente não selecionado sun-java6-bin.
Descompactando sun-java6-bin (de .../sun-java6-bin_6-07-3ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecionando pacote previamente não selecionado sun-java6-jdk.
Descompactando sun-java6-jdk (de .../sun-java6-jdk_6-07-3ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Instalando java-common (0.28ubuntu3) ...

Instalando odbcinst1debian1 (2.2.11-16build1) ...

Instalando unixodbc (2.2.11-16build1) ...

Instalando sun-java6-bin (6-07-3ubuntu2) ...

Instalando sun-java6-jre (6-07-3ubuntu2) ...

Instalando sun-java6-jdk (6-07-3ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-10-20  22:29:18

Log started: 2008-10-21  14:56:16
(Lendo banco de dados ... 

127728 arquivos e diretórios atualmente instalados.)
Preparando para substituir tzdata 2008h-0ubuntu0.8.04 (usando 

.../tzdata_2008h-0ubuntu0.8.04.1_all.deb) ...
Descompactando substituto tzdata ...
Instalando tzdata (2008h-0ubuntu0.8.04.1) ...

Current default timezone: 'America/Recife'
Local time is now:      Tue Oct 21 14:56:30 BRT 2008.
Universal Time is now:  Tue Oct 21 17:56:30 UTC 2008.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Lendo banco de dados ... 127731 arquivos e diretórios atualmente instalados.)
Preparando para substituir xkb-data 1.1~cvs.20080104.1-1ubuntu7 (usando 

.../xkb-data_1.1~cvs.20080104.1-1ubuntu8_all.deb) ...
Descompactando substituto xkb-data ...
Preparando para substituir gstreamer0.10-plugins-bad 0.10.6-5 (usando 

.../gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_i386.deb) ...
Descompactando substituto gstreamer0.10-plugins-bad ...
Instalando xkb-data (1.1~cvs.20080104.1-1ubuntu8) ...
Instalando gstreamer0.10-plugins-bad (0.10.6-5ubuntu0.1) ...
Log ended: 2008-10-21  14:56:34

```

Paul41, about what you mentioned, either in the sudoers as in the group file I'm set as admin group, so I don't think it would be the problem.
One more time thank you for your help guys, please let me know if you find something more.

best regards

---

