---
title: "Installing programs"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by 1sttimeuser on 2008-06-19
how do I install software?
I.E. 
Frostwire
Divx
Graboid

---

### Post by jonathan.gardner04 on 2008-06-19
I will tackle the I.E. 

** information pulled from [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

1) Open a terminal

2) Open /etc/apt/sources.list

 > sudo gedit /etc/apt/sources.list

3) Uncomment (or add) following lines:

 > deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

4) Add this line:

>  deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main[QUOTE]

5) Close gedit. Update and install wine and cabextract:

[QUOTE wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract[QUOTE]

6) Download IEs 4 Linux and install

[QUOTE] wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux 

Note for Dapper users: if you use ubuntu dapper, replace edgy with dapper on lines above. Note for Feisty users (7.04): if you use ubuntu Feisty, replace edgy with feisty in the lines above. Also replace gedit with kedit if running Kubuntu instead of Ubuntu.

For "Fiesty" K/Ubuntu Users (and 64-bit "Fiesty): [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by jonathan.gardner04 on 2008-06-19
For the Frostwire.  You can download the .deb from there website and run 

>  sudo dpkg -i /your/location/frostwire-xxxx.deb

---

### Post by Sef on 2008-06-19
> Also replace gedit with kedit if running Kubuntu instead of Ubuntu.

Also replace sudo with kdesu.

---

### Post by oldos2er on 2008-06-19
[quote=jonathan.gardner04;5218714]I will tackle the I.E. 

** information pulled from [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

1) Open a terminal

2) Open /etc/apt/sources.list

   Best to use the command gksudo gedit /etc/apt/sources.list, since gedit is a graphical application.

3) Uncomment (or add) following lines:

   Aren't the edgy repos offline now?

---

### Post by mick222 on 2008-06-19
frostwire is in the hardy repositories
get it with synaptic

---

### Post by 1sttimeuser on 2008-06-19
completely ignorant as to this whole linux (ubuntu) system.
tried the synaptic rout to no avail.
linux have online support where they take control of my system???
it's either that of I buy the manual.

---

### Post by oldos2er on 2008-06-19
No need to buy anything. See [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by xMoDx on 2008-10-22
> **jonathan.gardner04 said:**
> I will tackle the I.E. 

** information pulled from [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

1) Open a terminal

2) Open /etc/apt/sources.list

 

3) Uncomment (or add) following lines:

 

4) Add this line:

[QUOTE] deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main[QUOTE]

5) Close gedit. Update and install wine and cabextract:

[QUOTE wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract[QUOTE]

6) Download IEs 4 Linux and install



Note for Dapper users: if you use ubuntu dapper, replace edgy with dapper on lines above. Note for Feisty users (7.04): if you use ubuntu Feisty, replace edgy with feisty in the lines above. Also replace gedit with kedit if running Kubuntu instead of Ubuntu.

For "Fiesty" K/Ubuntu Users (and 64-bit "Fiesty): [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)



IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /home/mod/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   SCR56EN.CAB

  Downloading from macromedia.com:
   swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
  Installing IE 6
  Installing DCOM98
  Installing TTF Fonts
  Installing ActiveX MFC42
  Installing RICHED20
  Installing registry
  Finalizing
[ OK ]

Installing Flash Player 9
[B]  Extracting files
/home/mod/.ies4linux/downloads/swflash.cab: WARNING; file possibly truncated by 1552899 bytes.
/home/mod/.ies4linux/downloads/swflash.cab: no valid cabinets found
 An error occured when trying to cabextract some files.
[/B]


can you please help me with this error?

---

