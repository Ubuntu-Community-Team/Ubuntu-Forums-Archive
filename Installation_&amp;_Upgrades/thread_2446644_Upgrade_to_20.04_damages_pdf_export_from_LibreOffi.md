---
title: "Upgrade to 20.04 damages pdf export from LibreOffice"
date: 2020-07-04
forum: Installation &amp; Upgrades
---

### Post by jet-bundle on 2020-07-04
I have a couple of laptops, both of which can boot either Lubuntu 18.04 (4.15.0-109) or 20.04 (5.4.0-40). On both machines, if I boot into 20.04 and have a document in LibreOffice and export to a pdf file, the resulting output contains no text, although images are exported and are spaced as though the text were there. This was not a problem in 18.04.

As an experiment, installed the same downgraded version of LibreOffice on both systems, with the same result (no text exported when running 20.04, whereas text was exported when running 18.04).

I've reported this to LibreOffice Bugzilla, and received the following comment: "[COLOR=#ff0000]possibly only vcl:qt5 or Lubuntu build problem[/COLOR]". I've also found a comment online in [https://ask.libreoffice.org/en/question/252543/writer-export-to-pdf-has-no-text/](https://ask.libreoffice.org/en/question/252543/writer-export-to-pdf-has-no-text/) saying
```

Here's a workaround for the time being:[INDENT] env SAL_USE_VCLPLUGIN=gen libreoffice &
 [/INDENT]
or, as I also have kf5[INDENT] env SAL_USE_VCLPLUGIN=kf5 libreoffice &
 [/INDENT]
but qt5 (also installed) doesn't work
 

```
I guess that this is indeed a Lubuntu issue (rather than a LibreOffice issue). The first workaround does indeed allow text to be exported to pdf files (although it changes the layout of the LibreOffice window somewhat) but isn't really appropriate for a non-technical user.

I wonder if anyone has any other suggestions?

---

### Post by dino99 on 2020-07-04
Does not know which app is used by LO todo a pdf  export; if its an external app/lib, then it could be a version regression of it too.

---

### Post by SeijiSensei on 2020-07-04
Not a problem exporting documents to PDF from either Writer or Calc on Kubuntu 20.04.  Just did both those tasks over the past week.

---

### Post by jet-bundle on 2020-07-04
Here's an update.

This is a known problem with Lubuntu 20.04, see [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/):
> [B]
LibreOffice Exporting Documents as a PDF[/B]

 There is a [bug]("https://bugs.documentfoundation.org/show_bug.cgi?id=125234#c11")  where certain fonts do not render in exported PDF documents. As a  workaround, LibreOffice applications can be launched from the  commandline with the following environment variable SAL_VCL_QT5_USE_CAIRO=true. For example, to launch writer issue SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer.

However, the workaround suggested here (with Cairo) opens LibreOffice and allows new documents to be created and exported to pdf, but attempting to open existing documents either messes up the screen or else crashes entirely.

As noted, this was raised as a bug with LibreOffice back in May 2019, see [https://bugs.documentfoundation.org/show_bug.cgi?id=125234#c11](https://bugs.documentfoundation.org/show_bug.cgi?id=125234#c11):
> 
Description:

LO does not embedded fonts in a PDF file if the VCL backend qt5 is used in combination with the QPainter renderer. Using qt5 and cairo renderer embeds the fonts. The same happens if PDF is used as an intermediate format for printing.

Steps to Reproduce:
0, set VCL = qt5 and renderer = QPainter
1. Open writer
2. type some text in any font
3. export to PDF

So it seems that this is a qt5/cairo problem, arising when LibreOffice 6.x is used with Lubuntu 20.04 and the LXQt desktop. It would be nice if there was a way to launch LibreOffice with a suitable environment variable so that the problem didn't arise, but without having to open a terminal.

---

### Post by SeijiSensei on 2020-07-04
You should be able to edit the launcher for Writer to include the environment variable.  For instance in my (KDE) launcher for Writer I have the command line
```
libreoffice --writer %U
```
See if you can find the equivalent launcher in Lubuntu and replace the entry with
```
SAL_VCL_QT5_USE_CAIRO=true; libreoffice --writer %U
```

Alternatively, you might be able to declare the environment variable in your .bashrc. Use "nano ~/.bashrc" and add a line at the bottom of the file that reads
```
SAL_VCL_QT5_USE_CAIRO=true
```
Save the file, log out, and log back in. Any better?

---

### Post by jet-bundle on 2020-07-04
Not much luck, I'm afraid.

As I said above, setting [COLOR=#ff0000]SAL_VCL_QT5_USE_CAIRO=true [/COLOR]tends to crash LibreOffice when opening existing files (despite it being official advice); I get, when starting in a terminal window,
```

$ SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer
Icon theme "elementary" not found.
Application Error

```
On the other hand, [COLOR=#ff0000]SAL_USE_VCLPLUGIN=gen[/COLOR] works fine in a terminal window, but I haven't been able to get a launcher to work as suggested. I've copied the LibreOffice launcher to my desktop as an executable file [COLOR=#ff0000]libreoffice-startcenter.desktop[/COLOR], and this contains the line [COLOR=#ff0000]Exec=libreoffice %U[/COLOR], but editing it as suggested to [COLOR=#ff0000]Exec=[/COLOR][COLOR=#ff0000]SAL_USE_VCLPLUGIN=gen; libreoffice %U[/COLOR] gives an [COLOR=#ff0000]Invalid desktop entry file[/COLOR] error.

I've also tried editing .bashrc to include [COLOR=#ff0000]SAL_USE_VCLPLUGIN=gen [/COLOR](or. alternatively,  [COLOR=#ff0000]export[/COLOR] [COLOR=#ff0000]SAL_USE_VCLPLUGIN=gen[/COLOR] which gives a permanent local change in a terminal window) and rebooting, but this doesn't seem to have global effect. If, on the other hand, I try to set the variable in [COLOR=#ff0000]/etc/environment[/COLOR], then I see from issuing [COLOR=#ff0000]env[/COLOR] in a terminal window that the variable has been reset (I get [COLOR=#ff0000]SAL_USE_VCLPLUGIN=qt5[/COLOR]). 

Perhaps there's some other way to set the environment variable?

---

### Post by GhX6GZMB on 2020-07-04
I suspact a general font problem in Lubuntu. Check which fonts are installed (or rather: available) in 
```
/usr/share/fonts/truetype
/usr/share/fonts/opentype
```
Compare with which fonts are reported by, eg, LO Writer.

You might have to run
```
sudo fc-cache -f -v
```
to get them synchronized.

---

### Post by jet-bundle on 2020-07-05
Thanks. I tried synchronising fonts as suggested, but that made no difference.

---

### Post by jet-bundle on 2020-07-06
Here's an update.

I've been able to edit the launcher file for LibreOffice writer, which lives in /usr/share/applications as libreoffice-writer.desktop, replacing [COLOR=#ff0000]Exec=libreoffice --writer %U[/COLOR] by [COLOR=#ff0000]Exec=sh -c "SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer %U"[/COLOR] in the [Desktop Entry] section, and similarly replacing [COLOR=#ff0000]Exec=libreoffice --writer[/COLOR] by [COLOR=#ff0000]Exec=sh -c "SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer"[/COLOR] in the [Desktop Action NewDocument] section. Here is the edited file.
```

#
# This file is part of the LibreOffice project.
#
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.
#
# This file incorporates work covered by the following license notice:
#
#   Licensed to the Apache Software Foundation (ASF) under one or more
#   contributor license agreements. See the NOTICE file distributed
#   with this work for additional information regarding copyright
#   ownership. The ASF licenses this file to you under the Apache
#   License, Version 2.0 (the "License"); you may not use this file
#   except in compliance with the License. You may obtain a copy of
#   the License at http://www.apache.org/licenses/LICENSE-2.0 .
#
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-writer
Type=Application
Categories=Office;WordProcessor;
# Exec=libreoffice --writer %U
Exec=sh -c "SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer %U"
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;application/vnd.oasis.opendocument.text-master-template;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.writer.global;application/msword;application/vnd.ms-word;application/x-doc;application/x-hwp;application/rtf;text/rtf;application/vnd.wordperfect;application/wordperfect;application/vnd.lotus-wordpro;application/vnd.openxmlformats-officedocument.wordprocessingml.document;application/vnd.ms-word.document.macroEnabled.12;application/vnd.openxmlformats-officedocument.wordprocessingml.template;application/vnd.ms-word.template.macroEnabled.12;application/vnd.ms-works;application/vnd.stardivision.writer-global;application/x-extension-txt;application/x-t602;text/plain;application/vnd.oasis.opendocument.text-flat-xml;application/x-fictionbook+xml;application/macwriteii;application/x-aportisdoc;application/prs.plucker;application/vnd.palm;application/clarisworks;application/x-sony-bbeb;application/x-abiword;application/x-iwork-pages-sffpages;application/x-mswrite;application/x-starwriter;
Name=LibreOffice Writer
GenericName=Word Processor
GenericName[af]=Woordverwerker
GenericName[am]=&#4675;&#4619;&#4725; &#4635;&#4672;&#4755;&#4704;&#4650;&#4843;
GenericName[ar]=&#1605;&#1593;&#1575;&#1604;&#1580; &#1575;&#1604;&#1605;&#1587;&#1578;&#1606;&#1583;&#1575;&#1578;
GenericName[as]=Word &#2474;&#2509;&#2544;&#2458;&#2503;&#2459;&#2544;
GenericName[ast]=Procesador de testos
GenericName[be]=&#1058;&#1101;&#1082;&#1089;&#1090;&#1072;&#1074;&#1099; &#1087;&#1088;&#1072;&#1094;&#1101;&#1089;&#1072;&#1088;
GenericName[bg]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072;
GenericName[bn]=&#2451;&#2479;&#2492;&#2494;&#2480;&#2509;&#2465; &#2474;&#2509;&#2480;&#2488;&#2503;&#2488;&#2480;
GenericName[br]=Kewerier testenn
GenericName[bs]=Program za obradu teksta
GenericName[ca]=Processador de textos
GenericName[ca_valencia]=Processador de textos
GenericName[cs]=Textový procesor
GenericName[cy]=Prosesydd Geiriau
GenericName[da]=Tekstbehandling
GenericName[de]=Textverarbeitung
GenericName[dz]=Word Processor
GenericName[el]=&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#964;&#942;&#962; Word
GenericName[en]=Word Processor
GenericName[en_GB]=Word Processor
GenericName[en_ZA]=Word Processor
GenericName[eo]=Vortprocesilo
GenericName[es]=Procesador de texto
GenericName[et]=Tekstitöötlus
GenericName[eu]=Testu prozesatzailea
GenericName[fa]=&#1608;&#1575;&#1688;&#1607;*&#1662;&#1585;&#1583;&#1575;&#1586;
GenericName[fi]=Tekstinkäsittely
GenericName[fr]=Traitement de texte
GenericName[ga]=Próiseálaí Focal
GenericName[gd]=Giullachair teacsa
GenericName[gl]=Procesador de textos
GenericName[gu]=&#2741;&#2736;&#2765;&#2721; &#2730;&#2765;&#2736;&#2763;&#2744;&#2759;&#2744;&#2736;
GenericName[gug]=Procesador Moñe'&#7869;rãgui
GenericName[he]=&#1502;&#1506;&#1489;&#1491; &#1514;&#1502;&#1500;&#1497;&#1500;&#1497;&#1501;
GenericName[hi]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[hr]=Program za obradu teksta
GenericName[hu]=Szövegszerkeszt&#337;
GenericName[id]=Pengolah Kata
GenericName[is]=Ritvinnsluforrit
GenericName[it]=Elaboratore di testo
GenericName[ja]=&#12527;&#12540;&#12489;&#12503;&#12525;&#12475;&#12483;&#12469;
GenericName[ka]=Word Processor
GenericName[kk]=&#1052;&#1241;&#1090;&#1110;&#1085;&#1076;&#1110;&#1082; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089;&#1086;&#1088;
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6044;&#6070;&#6041;&#8203;&#6050;&#6031;&#6098;&#6032;&#6036;&#6033;
GenericName[kmr_Latn]=Kiryarê Peyvan
GenericName[kn]=&#3253;&#3248;&#3277;&#3233;&#3277; &#3242;&#3277;&#3248;&#3274;&#3256;&#3270;&#3256;&#3248;&#3277;
GenericName[ko]=&#50892;&#46300; &#54532;&#47196;&#49464;&#49436;
GenericName[lt]=Tekst&#371; rengykl&#279;
GenericName[lv]=Tekstapstr&#257;des programma
GenericName[mk]=&#1054;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072; &#1085;&#1072; &#1090;&#1077;&#1082;&#1089;&#1090;
GenericName[ml]=&#3381;&#3399;&#3376;&#3405;*&#3361;&#3405; &#3370;&#3405;&#3376;&#3402;&#3384;&#3384;&#3405;&#3384;&#3376;&#3405;*
GenericName[mn]=&#1042;&#1086;&#1088;&#1076; &#1073;&#1086;&#1083;&#1086;&#1074;&#1089;&#1088;&#1091;&#1091;&#1083;&#1072;&#1075;&#1095;
GenericName[mr]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[nb]=Skriveprogram
GenericName[ne]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[nl]=Tekstverwerker
GenericName[nn]=Teksthandsamar
GenericName[nr]=Word Processor
GenericName[nso]=Sebopi sa mantšu
GenericName[oc]=Tractament de tèxte
GenericName[om]=Hujeessaa Jecha
GenericName[or]=&#2870;&#2860;&#2893;&#2854; &#2872;&#2846;&#2893;&#2842;&#2878;&#2867;&#2837;
GenericName[pa_IN]=&#2613;&#2608;&#2593; &#2602;&#2608;&#2635;&#2616;&#2632;&#2616;&#2608;
GenericName[pl]=Procesor tekstu
GenericName[pt]=Processador de texto
GenericName[pt_BR]=Editor de texto
GenericName[ro]=Procesor de text
GenericName[ru]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1099;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089;&#1086;&#1088;
GenericName[rw]=Musesenguramagambo
GenericName[si]=&#3517;&#3538;&#3508;&#3538; &#3523;&#3482;&#3523;&#3505;&#3514;
GenericName[sk]=Textový procesor
GenericName[sl]=Urejevalnik besedila
GenericName[sr]=&#1059;&#1088;&#1077;&#1106;&#1080;&#1074;&#1072;&#1095; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;
GenericName[sr_Latn]=Ure&#273;iva&#269; teksta
GenericName[ss]=Word Processor
GenericName[st]=Word Processor
GenericName[sv]=Ordbehandlare
GenericName[szl]=Word Processor
GenericName[ta]=&#2970;&#3018;&#2993;&#3021;&#2970;&#3014;&#2991;&#2994;&#3007;
GenericName[te]=&#3125;&#3120;&#3149;&#3105;&#3149; &#3114;&#3149;&#3120;&#3134;&#3128;&#3142;&#3128;&#3120;&#3149;
GenericName[tg]=Word Processor
GenericName[th]=&#3650;&#3611;&#3619;&#3649;&#3585;&#3619;&#3617;&#3611;&#3619;&#3632;&#3617;&#3623;&#3621;&#3612;&#3621;&#3588;&#3635;
GenericName[tn]=Word Processor
GenericName[tr]=Kelime &#304;&#351;lemci
GenericName[ts]=Word Processor
GenericName[ug]=&#1610;&#1744;&#1586;&#1609;&#1602; &#1576;&#1609;&#1585; &#1578;&#1749;&#1585;&#1749;&#1662; &#1602;&#1609;&#1604;&#1609;&#1588;
GenericName[uk]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1080;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1086;&#1088;
GenericName[uz]=Matn protsessori
GenericName[ve]=Word Processor
GenericName[vi]=X&#7917; lý t&#7915;
GenericName[xh]=Word Processor
GenericName[zh_CN]=&#25991;&#23383;&#22788;&#29702;&#36719;&#20214;
GenericName[zh_TW]=&#25991;&#26360;&#34389;&#29702;&#22120;
GenericName[zu]=Word Processor
Comment=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[af]=Skep en redigeer teks en beelde in briewe, verslae, dokumente en webbladsye met Writer.
Comment[am]=&#4840; &#4675;&#4619;&#4725; &#4632;&#4923;&#4938;&#4843;&#4757; &#4704; &#4632;&#4896;&#4672;&#4637; &#4925;&#4609;&#4942;&#4733; &#4773;&#4755; &#4757;&#4853;&#4942;&#4733; &#4845;&#4941;&#4896;&#4649; &#4773;&#4755; &#4843;&#4653;&#4633; &#4704; &#4938;&#4848;&#4622;&#4733;: &#4632;&#4877;&#4616;&#4907;&#4814;&#4733;: &#4656;&#4752;&#4854;&#4733;: &#4773;&#4755; &#4853;&#4613;&#4648; &#4872;&#4926;&#4733;
Comment[ar]=&#1571;&#1606;&#1588;&#1574; &#1575;&#1604;&#1606;&#1589;&#1608;&#1589; &#1608;&#1575;&#1604;&#1589;&#1608;&#1585; &#1608;&#1581;&#1585;&#1585;&#1607;&#1575; &#1601;&#1610; &#1575;&#1604;&#1585;&#1587;&#1575;&#1574;&#1604;&#1548; &#1608;&#1575;&#1604;&#1578;&#1602;&#1575;&#1585;&#1610;&#1585;&#1548; &#1608;&#1575;&#1604;&#1605;&#1587;&#1578;&#1606;&#1583;&#1575;&#1578; &#1608;&#1589;&#1601;&#1581;&#1575;&#1578; &#1575;&#1604;&#1608;&#1616;&#1576; &#1576;&#1575;&#1587;&#1578;&#1582;&#1583;&#1575;&#1605; &#1585;&#1575;&#1610;&#1578;&#1585;.
Comment[as]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[ast]=Crea y edita testos y gráficos de cartes, informes, documentos y páxines Web usando Writer.
Comment[be]=&#1057;&#1090;&#1074;&#1072;&#1088;&#1072;&#1081;&#1094;&#1077; &#1110; &#1088;&#1101;&#1076;&#1072;&#1075;&#1091;&#1081;&#1094;&#1077; &#1090;&#1101;&#1082;&#1089;&#1090; &#1110; &#1075;&#1088;&#1072;&#1092;&#1110;&#1082;&#1091; &#1118; &#1083;&#1110;&#1089;&#1090;&#1072;&#1093;, &#1089;&#1087;&#1088;&#1072;&#1074;&#1072;&#1079;&#1076;&#1072;&#1095;&#1072;&#1093;, &#1076;&#1072;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1110; &#1089;&#1090;&#1072;&#1088;&#1086;&#1085;&#1082;&#1072;&#1093; &#1057;&#1077;&#1094;&#1110;&#1074;&#1072; &#1079; &#1076;&#1072;&#1087;&#1072;&#1084;&#1086;&#1075;&#1072;&#1102; Writer-&#1072;.
Comment[bg]=&#1057; Writer &#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1076;&#1072; &#1089;&#1098;&#1079;&#1076;&#1072;&#1074;&#1072;&#1090;&#1077; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1072;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103; &#1074; &#1087;&#1080;&#1089;&#1084;&#1072;, &#1086;&#1090;&#1095;&#1077;&#1090;&#1080;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1080; &#1080; &#1091;&#1077;&#1073;&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1080;.
Comment[bn]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[br]=Krouiñ hag embann testennoù ha skeudennoù evit lizhiri, danevelloù, teulioù ha pajennoù Web en ur ober gant Writer.
Comment[bs]=Pravite i mijenjajte tekst i grafiku u pismima, izvještajima, dokumentima i internet stranicama koriste&#263;i Pisac.
Comment[ca]=Creeu i editeu textos i imatges en cartes, informes, documents i pàgines web amb el Writer.
Comment[ca_valencia]=Creeu i editeu textos i imatges en cartes, informes, documents i pàgines web amb el Writer.
Comment[cs]=Writer umož&#328;uje vytvá&#345;et a upravovat text a grafiku v dopisech, sestavách, dokumentech a webových stránkách.
Comment[cy]=Creu a golygu testun a graffigau mewn llythyron, adroddiadau, dogfennau a thudalennau Gwe gyda Writer.
Comment[da]=Opret og rediger tekst og billeder i breve, rapporter, dokumenter og websider med Writer.
Comment[de]=Erstellen und Bearbeiten von Text und Bildern in Briefen, Berichten, Dokumenten und Webseiten – Writer macht's möglich.
Comment[dz]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[el]=&#916;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945; &#954;&#945;&#953; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965; &#954;&#945;&#953; &#949;&#953;&#954;&#972;&#957;&#969;&#957; &#963;&#949; &#949;&#960;&#953;&#963;&#964;&#959;&#955;&#941;&#962;, &#945;&#957;&#945;&#966;&#959;&#961;&#941;&#962;, &#941;&#947;&#947;&#961;&#945;&#966;&#945; &#954;&#945;&#953; &#953;&#963;&#964;&#959;&#963;&#949;&#955;&#943;&#948;&#949;&#962; &#956;&#949; &#964;&#951; &#967;&#961;&#942;&#963;&#951; &#964;&#959;&#965; Writer.
Comment[en]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[en_GB]=Create and edit text and images in letters, reports, documents and Web pages using Writer.
Comment[en_ZA]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[eo]=Krei kaj redakti tekston kaj grafika&#309;ojn en leteroj, raportoj, dokumentoj kaj TTT-pa&#285;oj per Verkilo.
Comment[es]=Cree y edite texto e imágenes en cartas, informes, documentos y páginas Web con Writer.
Comment[et]=Writer võimaldab luua ja redigeerida kirjade, aruannete, dokumentide ning veebilehtede teksti ja pilte.
Comment[eu]=Sortu eta editatu testua eta irudiak gutunetan, txostenetan, dokumentuetan eta web orrietan Writer erabiliz.
Comment[fa]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[fi]=Luo ja muokkaa tekstiä ja kuvia kirjeisiin, raportteihin, tekstiasiakirjoihin ja internet-sivuihin Writer-ohjelmalla.
Comment[fr]=Writer - Création et édition de textes et d'images pour courriers, rapports, documents et pages Web.
Comment[ga]=Cruthaigh téacs agus grafaicí i litreacha, tuairiscí, cáipéisí, agus leathanaigh Ghréasáin le Writer.
Comment[gd]=Cruthaich is deasaich teacsa is dealbhan ann an litrichean, aithisgean, sgrìobhainnean is duilleagan-lìn le Writer.
Comment[gl]=Cree e edite texto ou imaxes en cartas, informes, documentos e páxinas web usando Writer.
Comment[gu]=&#2738;&#2710;&#2750;&#2723; &#2726;&#2765;&#2726;&#2750;&#2736;&#2750; &#2730;&#2724;&#2765;&#2736;&#2763;, &#2693;&#2745;&#2759;&#2741;&#2750;&#2738;&#2763;, &#2726;&#2744;&#2765;&#2724;&#2750;&#2741;&#2759;&#2716;&#2763; &#2693;&#2728;&#2759; &#2741;&#2759;&#2732; &#2730;&#2750;&#2728;&#2750;&#2707;&#2734;&#2750;&#2690; &#2738;&#2710;&#2750;&#2723; &#2693;&#2728;&#2759; &#2714;&#2751;&#2724;&#2765;&#2736;&#2763; &#2732;&#2728;&#2750;&#2741;&#2763; &#2693;&#2728;&#2759; &#2744;&#2753;&#2712;&#2750;&#2736;&#2763;.
Comment[gug]=Rejapo ha edite moñe'&#7869;rã ha gráficos en cartas, informes, documentos ha togue Web reipuru jave Writer.
Comment[he]=&#1497;&#1510;&#1497;&#1512;&#1492; &#1493;&#1506;&#1512;&#1497;&#1499;&#1492; &#1513;&#1500; &#1496;&#1511;&#1505;&#1496; &#1493;&#1490;&#1512;&#1508;&#1497;&#1511;&#1492; &#1489;&#1502;&#1499;&#1514;&#1489;&#1497;&#1501;, &#1491;&#1493;&#1495;&#1493;&#1514;, &#1502;&#1505;&#1502;&#1499;&#1497;&#1501; &#1493;&#1491;&#1508;&#1497; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496; &#1489;&#1488;&#1502;&#1510;&#1506;&#1493;&#1514; Writer.
Comment[hi]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[hr]=Stvorite i uredite tekst i slike u pismima, izvještajima, dokumentima i internetskim stranicama koriste&#263;i Writer.
Comment[hu]=Levelek, jelentések, dokumentumok és weboldalak szövegének és képeinek létrehozása és szerkesztése a Writer használatával.
Comment[id]=Membuat dan menyunting teks dan gambar pada surat, laporan, dokumen, dan halaman Web menggunakan Writer.
Comment[is]=Búa til og breyta texta og myndefni í bréfum, skýrslum, skjölum og vefsíðum með því að nota Writer.
Comment[it]=Usando Writer puoi creare e modificare il testo e le immagini di lettere, rapporti, documenti e pagine web.
Comment[ja]=Writer &#12434;&#20351;&#29992;&#12375;&#12390;&#12289;&#12524;&#12479;&#12540;&#12289;&#12524;&#12509;&#12540;&#12488;&#12289;&#12489;&#12461;&#12517;&#12513;&#12531;&#12488;&#12362;&#12424;&#12403; Web &#12506;&#12540;&#12472;&#12398;&#12486;&#12461;&#12473;&#12488;&#12362;&#12424;&#12403;&#12452;&#12513;&#12540;&#12472;&#12434;&#20316;&#25104;&#12362;&#12424;&#12403;&#32232;&#38598;&#12375;&#12414;&#12377;&#12290;
Comment[ka]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[kk]=Writer &#1082;&#1257;&#1084;&#1077;&#1075;&#1110;&#1084;&#1077;&#1085; &#1093;&#1072;&#1090;&#1090;&#1072;&#1088;&#1076;&#1072;, &#1179;&#1201;&#1078;&#1072;&#1090;&#1090;&#1072;&#1088;&#1076;&#1072;, &#1077;&#1089;&#1077;&#1087;&#1090;&#1077;&#1084;&#1077;&#1083;&#1077;&#1088;&#1076;&#1077; &#1078;&#1241;&#1085;&#1077; &#1074;&#1077;&#1073;-&#1087;&#1072;&#1088;&#1072;&#1179;&#1090;&#1072;&#1088;&#1076;&#1072; &#1084;&#1241;&#1090;&#1110;&#1085;&#1076;&#1110; &#1078;&#1241;&#1085;&#1077; &#1089;&#1091;&#1088;&#1077;&#1090;&#1090;&#1077;&#1088;&#1076;&#1110; &#1078;&#1072;&#1089;&#1072;&#1091; &#1078;&#1241;&#1085;&#1077; &#1090;&#1199;&#1079;&#1077;&#1090;&#1091;&#1075;&#1077; &#1073;&#1086;&#1083;&#1072;&#1076;&#1099;.
Comment[km]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[kmr_Latn]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[kn]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[ko]=&#46972;&#51060;&#53552;&#47484; &#49324;&#50857;&#54616;&#50668; &#54200;&#51648;, &#48372;&#44256;&#49436;, &#47928;&#49436; &#48143; &#50937; &#54168;&#51060;&#51648;&#50640;&#49436; &#53581;&#49828;&#53944;&#50752; &#44536;&#47548;&#51012; &#47564;&#46308;&#44256; &#54200;&#51665;&#54624; &#49688; &#51080;&#49845;&#45768;&#45796;.
Comment[lt]=Tekst&#371; rengykle galima kurti laiškus, ataskaitas, kitus dokumentus ir tinklalapius, &#303;terpti &#303; juos paveikslus.
Comment[lv]=Veidot un redi&#291;&#275;t tekstu un att&#275;lus v&#275;stul&#275;s, atskait&#275;s, dokumentos un t&#299;mek&#316;a lap&#257;s, lietojot Writer.
Comment[mk]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[ml]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[mn]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[mr]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[nb]=Opprett og rediger tekst og bilder i brev, rapporter, dokumenter og nettsider ved å bruke Writer.
Comment[ne]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[nl]=Met Writer kunt u tekst en afbeeldingen in brieven, rapporten, documenten en webpagina's maken en bewerken.
Comment[nn]=Laga og redigera tekst og bilete i brev, rapportar, dokument og nettsider i Writer.
Comment[nr]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[nso]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[oc]=Writer - Creacion e edicion de tèxtes e d'imatges per corrièrs, rapòrts, documents e paginas Web.
Comment[om]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[or]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[pa_IN]=&#2608;&#2622;&#2567;&#2591;&#2608; &#2598;&#2624; &#2613;&#2608;&#2596;&#2635;&#2562; &#2598;&#2625;&#2566;&#2608;&#2622; &#2602;&#2673;&#2596;&#2608;&#2622;&#2562;, &#2608;&#2623;&#2602;&#2635;&#2608;&#2591;&#2622;&#2562;, &#2598;&#2616;&#2596;&#2622;&#2613;&#2631;&#2588;&#2620;&#2622;&#2562; &#2565;&#2596;&#2631; &#2613;&#2632;&#2673;&#2604; &#2616;&#2603;&#2620;&#2623;&#2566;&#2562; &#2613;&#2623;&#2673;&#2586; &#2591;&#2632;&#2581;&#2616;&#2591; &#2565;&#2596;&#2631; &#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2575; &#2565;&#2596;&#2631; &#2616;&#2635;&#2599;&#2631; &#2588;&#2622; &#2616;&#2581;&#2598;&#2631; &#2617;&#2600;&#2404;
Comment[pl]=Twórz i edytuj tekst oraz obrazy w listach, raportach, dokumentach i stronach internetowych za pomoc&#261; programu Writer.
Comment[pt]=Criar e editar texto e imagens em cartas, relatórios, documentos e páginas Web com o Writer.
Comment[pt_BR]=Crie e edite textos e figuras em cartas, relatórios, documentos e páginas da Web por meio do Writer.
Comment[ro]=Crea&#539;i &#537;i edita&#539;i textele &#537;i grafica din documente, scrisori, rapoarte &#537;i pagini web folosind Writer.
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; &#1080; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1081; &#1074; &#1087;&#1080;&#1089;&#1100;&#1084;&#1072;&#1093;, &#1086;&#1090;&#1095;&#1105;&#1090;&#1072;&#1093;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1080;&#1083;&#1080; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072;&#1093; &#1087;&#1088;&#1080; &#1087;&#1086;&#1084;&#1086;&#1097;&#1080; Writer.
Comment[rw]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[si]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[sk]=Writer umož&#328;uje vytvára&#357; a upravova&#357; text a grafiku v správach, dokumentoch a webových stránkach.
Comment[sl]=S programom Writer ustvarjajte in urejajte besedilo in slike v pismih, poro&#269;ilih, dokumentih in spletnih straneh.
Comment[sr]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[sr_Latn]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[ss]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[st]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[sv]=Skapa och redigera text och grafik i brev, rapporter, dokument och webbsidor med hjälp av Writer.
Comment[szl]=Tw&#333;rz i edytuj tekst we listach, reportach, dokumyntach i str&#333;nach www przi u&#380;yciu Writera.
Comment[ta]=&#2965;&#2975;&#3007;&#2980;&#2969;&#3021;&#2965;&#2995;&#3021;, &#2949;&#2993;&#3007;&#2965;&#3021;&#2965;&#3016;&#2965;&#2995;&#3021;, &#2950;&#2997;&#2979;&#2969;&#3021;&#2965;&#2995;&#3021;, &#2997;&#2994;&#3016;&#2986;&#3021;&#2986;&#2965;&#3021;&#2965;&#2969;&#3021;&#2965;&#2995;&#3021; &#2950;&#2965;&#3007;&#2991;&#2997;&#2993;&#3021;&#2993;&#3007;&#2985;&#3021; &#2953;&#2992;&#3016;, &#2986;&#3007;&#2990;&#3021;&#2986;&#2969;&#3021;&#2965;&#2995;&#3016; &#2953;&#2992;&#3009;&#2997;&#3006;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2980;&#3018;&#2965;&#3009;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2992;&#3016;&#2975;&#3021;&#2975;&#2992;&#3016;&#2986;&#3021; &#2986;&#2991;&#2985;&#3021;&#2986;&#2975;&#3009;&#2980;&#3021;&#2980;&#3009;&#2965;.
Comment[te]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[tg]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[th]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[tn]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[tr]=Writer kullanarak mektuplardaki metin ve grafikleri, rapor, belge ve Web sayfalar&#305; olu&#351;turun ve düzenleyin.
Comment[ts]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[ug]=Writer &#1574;&#1609;&#1588;&#1604;&#1609;&#1578;&#1609;&#1662; &#1582;&#1749;&#1578;-&#1670;&#1749;&#1603;&#1548; &#1583;&#1608;&#1603;&#1604;&#1575;&#1578;&#1548; &#1662;&#1736;&#1578;&#1736;&#1603; &#1739;&#1749; &#1578;&#1608;&#1585; &#1576;&#1749;&#1578;&#1578;&#1609;&#1603;&#1609; &#1578;&#1744;&#1603;&#1587;&#1578; &#1739;&#1749; &#1587;&#1736;&#1585;&#1749;&#1578;&#1604;&#1749;&#1585;&#1606;&#1609; &#1602;&#1735;&#1585;&#1735;&#1662; &#1578;&#1749;&#1726;&#1585;&#1609;&#1585;&#1604;&#1609;&#1711;&#1609;&#1604;&#1609; &#1576;&#1608;&#1604;&#1609;&#1583;&#1735;.
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1102;&#1081;&#1090;&#1077; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1081;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1090;&#1072; &#1075;&#1088;&#1072;&#1092;&#1110;&#1082;&#1091; &#1091; &#1083;&#1080;&#1089;&#1090;&#1072;&#1093;, &#1079;&#1074;&#1110;&#1090;&#1072;&#1093;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1090;&#1072; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1086;&#1088;&#1110;&#1085;&#1082;&#1072;&#1093; &#1079;&#1072; &#1076;&#1086;&#1087;&#1086;&#1084;&#1086;&#1075;&#1086;&#1102; Writer.
Comment[uz]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[ve]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[vi]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[xh]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
Comment[zh_CN]=&#20351;&#29992; Writer &#23545;&#20449;&#20989;&#12289;&#25253;&#21578;&#12289;&#25991;&#26723;&#20197;&#21450;&#32593;&#39029;&#20013;&#30340;&#25991;&#23383;&#21644;&#22270;&#20687;&#36827;&#34892;&#32534;&#36753;&#12290;
Comment[zh_TW]=&#20351;&#29992; Writer &#21487;&#20197;&#35069;&#20316;&#33287;&#32232;&#36655;&#26360;&#20449;&#12289;&#22577;&#21578;&#12289;&#25991;&#20214;&#21644;&#32178;&#38913;&#20013;&#30340;&#25991;&#23383;&#21644;&#24433;&#20687;&#12290;
Comment[zu]=Create and edit text and images in letters, reports, documents and Web pages by using Writer.
StartupNotify=true
X-GIO-NoFuse=true
Keywords=Text;Letter;Fax;Document;OpenDocument Text;Microsoft Word;Microsoft Works;Lotus WordPro;OpenOffice Writer;CV;odt;doc;docx;rtf;
InitialPreference=5
StartupWMClass=libreoffice-writer
X-KDE-Protocols=file,http,ftp,webdav,webdavs

Actions=NewDocument;
[Desktop Action NewDocument]
Name=New Document
Name[af]=Nuwe dokument
Name[am]=&#4768;&#4850;&#4661; &#4656;&#4752;&#4853;
Name[ar]=&#1605;&#1587;&#1578;&#1606;&#1583; &#1580;&#1583;&#1610;&#1583;
Name[as]=&#2472;&#2468;&#2497;&#2472; &#2470;&#2488;&#2509;&#2468;&#2494;&#2476;&#2503;&#2460;
Name[ast]=Documentu nuevu
Name[be]=&#1053;&#1086;&#1074;&#1099; &#1076;&#1072;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[bg]=&#1053;&#1086;&#1074; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[bn]=&#2472;&#2468;&#2497;&#2472; &#2472;&#2469;&#2495;
Name[br]=Teul nevez
Name[bs]=Novi dokument
Name[ca]=Document nou
Name[ca_valencia]=Document nou
Name[cs]=Nový dokument
Name[cy]=Dogfen Newydd
Name[da]=Nyt dokument
Name[de]=Neues Dokument
Name[dz]=&#3937;&#3954;&#3906;&#3851;&#3910;&#3851;&#3906;&#3942;&#3938;&#3924;&#3853;
Name[el]=&#925;&#941;&#959; &#941;&#947;&#947;&#961;&#945;&#966;&#959;
Name[en]=New Document
Name[en_GB]=New Document
Name[en_ZA]=New Document
Name[eo]=Nova dokumento
Name[es]=Documento nuevo
Name[et]=Uus dokument
Name[eu]=Dokumentu berria
Name[fa]=&#1662;&#1585;&#1608;&#1606;&#1583;&#1607; &#1580;&#1583;&#1740;&#1583;
Name[fi]=Uusi asiakirja
Name[fr]=Nouveau document
Name[ga]=Cáipéis Nua
Name[gd]=Sgrìobhainn ùr
Name[gl]=Novo documento
Name[gu]=&#2728;&#2741;&#2753;&#2690; &#2726;&#2744;&#2765;&#2724;&#2750;&#2741;&#2759;&#2716;
Name[gug]=Documento Pyahu
Name[he]=&#1502;&#1505;&#1502;&#1498; &#1495;&#1491;&#1513;
Name[hi]=&#2344;&#2351;&#2366; &#2342;&#2360;&#2381;&#2340;&#2366;&#2357;&#2375;&#2332;&#2364;
Name[hr]=Novi dokument
Name[hu]=Új dokumentum
Name[id]=Dokumen Baru
Name[is]=Nýtt skjal
Name[it]=Nuovo documento
Name[ja]=&#26032;&#35215;&#12398;&#25991;&#26360;&#12489;&#12461;&#12517;&#12513;&#12531;&#12488;
Name[ka]=~&#4304;&#4334;&#4304;&#4314;&#4312; &#4307;&#4317;&#4313;&#4323;&#4315;&#4308;&#4316;&#4322;&#4312;
Name[kk]=&#1178;&#1201;&#1078;&#1072;&#1090;&#1090;&#1099; &#1078;&#1072;&#1089;&#1072;&#1091;
Name[km]=&#6063;&#6016;&#6047;&#6070;&#6042;&#8203;&#6032;&#6098;&#6040;&#6072;
Name[kmr_Latn]=Belgeya Nû
Name[kn]=&#3257;&#3274;&#3256; &#3238;&#3256;&#3277;&#3236;&#3262;&#3253;&#3271;&#3228;&#3265;
Name[ko]=&#49352; &#47928;&#49436;
Name[lt]=Naujas dokumentas
Name[lv]=Jauns dokuments
Name[mk]=&#1053;&#1086;&#1074; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[ml]=&#3370;&#3393;&#3364;&#3391;&#3375; &#3376;&#3399;&#3350;
Name[mn]=&#1064;&#1080;&#1085;&#1101; &#1073;&#1072;&#1088;&#1080;&#1084;&#1090;
Name[mr]=&#2344;&#2357;&#2368;&#2344; &#2342;&#2360;&#2381;&#2340;&#2320;&#2357;&#2332;
Name[nb]=Nytt dokument
Name[ne]=&#2344;&#2351;&#2366;&#2305; &#2325;&#2366;&#2327;&#2332;&#2366;&#2340;
Name[nl]=Nieuw document
Name[nn]=Nytt dokument
Name[nr]=Umtlolo Omutjha
Name[nso]=Tokumente e mpsha
Name[oc]=Document novèl
Name[om]=Faayilii Haara
Name[or]=&#2856;&#2882;&#2822; &#2854;&#2866;&#2879;&#2866;
Name[pa_IN]=&#2600;&#2613;&#2622; &#2598;&#2616;&#2596;&#2622;&#2613;&#2631;&#2588;
Name[pl]=Nowy dokument
Name[pt]=Novo documento
Name[pt_BR]=Novo documento
Name[ro]=Document nou
Name[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1090;&#1100; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[rw]=Inyandiko Nshya
Name[si]=&#3505;&#3520; &#3517;&#3546;&#3483;&#3505;&#3514; (~N)
Name[sk]=Nový dokument
Name[sl]=Nov dokument
Name[sr]=&#1053;&#1086;&#1074;&#1080; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[sr_Latn]=Novi dokument
Name[ss]=Idokhumenti lensha
Name[st]=New Document
Name[sv]=Nytt dokument
Name[szl]=Nowy dokumynt
Name[ta]=&#2986;&#3009;&#2980;&#3007;&#2991; &#2950;&#2997;&#2979;&#2990;&#3021;
Name[te]=&#3093;&#3146;&#3108;&#3149;&#3108; &#3114;&#3108;&#3149;&#3120;&#3074;
Name[tg]=&#1202;&#1091;&#1207;&#1207;&#1072;&#1090;&#1080; &#1085;&#1072;&#1074;
Name[th]=&#3648;&#3629;&#3585;&#3626;&#3634;&#3619;&#3651;&#3627;&#3617;&#3656;
Name[tn]=New Document
Name[tr]=Yeni Belge
Name[ts]=Dokumente yintshwa
Name[ug]=&#1610;&#1744;&#1709;&#1609; &#1662;&#1736;&#1578;&#1736;&#1603;
Name[uk]=~&#1057;&#1090;&#1074;&#1086;&#1088;&#1080;&#1090;&#1080; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[uz]=New Document
Name[ve]=&#7740;i&#7749;walwa &#7740;iswa
Name[vi]=Tài li&#7879;u m&#7899;i
Name[xh]=Uxwebhu Olutsha
Name[zh_CN]=&#26032;&#24314;&#25991;&#26723;
Name[zh_TW]=&#26032;&#22686;&#25991;&#20214;
Name[zu]=Ushicilelo olusha
Icon=libreoffice-document-new
# Exec=libreoffice --writer
Exec=sh -c "SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer"

```
I then dragged a copy of this from the main menu (I don't know the correct name for this, it's the collection of links which pops up when you click the Lubuntu icon at the bottom left of the display) to the desktop; I made it executable and trusted it.

I can now open a blank Writer file by double-clicking on the launcher on the desktop, and if I add text to this file then it exports to pdf without any problem. If I want to open an existing .odt file, I can double-click on the file (in a file manager), and again the contents export successfully to pdf.

But this isn't completely satisfactory, for the following reasons.

[LIST=1]
[*]If I use the desktop launcher to open a blank file, and then use File > Recent documents to open an existing .odt file, then LibreOffice crashes. I can recover the document, and then I can export to pdf as before. 
[*]If I use the version of the launcher in the main menu to open a blank .odt file then I get an error message saying that ~/%U does not exist, even though this launcher is identical to the version of the launcher on the desktop (which successfully opens a blank file). 
[*]If I use the generic LibreOffice launcher in the main menu then I'm not using Cairo at all, and everything opens, but export to pdf loses text. 
[/LIST]
So this arrangement is probably still not appropriate for a non-technical user.

I don't know enough about how Lubuntu launches applications to make much further progress, and so would be grateful if anyone has any further advice.

---

### Post by ActionParsnip on 2020-07-06
Wait, what is the output of:
```

lsb_release -a; uname -a; apt-cache policy libreoffice

```
Thanks

---

### Post by jet-bundle on 2020-07-06
```

~$ lsb_release -a; uname -a; apt-cache policy libreoffice
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal
Linux Dell13-LUB 5.4.0-40-generic #44-Ubuntu SMP Tue Jun 23 00:01:04 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
libreoffice:
  Installed: (none)
  Candidate: 1:6.4.4-0ubuntu0.20.04.1
  Version table:
     1:6.4.4-0ubuntu0.20.04.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
     1:6.4.2-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
~$

```

---

### Post by GhX6GZMB on 2020-07-06
You know, thinking back I _did_ have a problem with LO after upgrading from 19.10 to 20.04. Don't remember exactly what it was, but it was glaring.
I did a reinstall of LO and then everything was fine.
I know, brute force, but it worked  :)

---

### Post by SeijiSensei on 2020-07-06
The current version still handles icons in Calc charts incorrectly. You can no longer change their shapes.

[https://ask.libreoffice.org/en/question/231971/changing-data-point-icon-in-spreadsheet-charts-not-working/](https://ask.libreoffice.org/en/question/231971/changing-data-point-icon-in-spreadsheet-charts-not-working/)

---

### Post by GhX6GZMB on 2020-07-06
> **SeijiSensei said:**
> The current version still handles icons in Calc charts incorrectly. You can no longer change their shapes.

[https://ask.libreoffice.org/en/question/231971/changing-data-point-icon-in-spreadsheet-charts-not-working/](https://ask.libreoffice.org/en/question/231971/changing-data-point-icon-in-spreadsheet-charts-not-working/)

???

---

### Post by jet-bundle on 2020-07-07
With respect, recent posts are diverging from the specific problem which I've raised in this thread.

There is a known problem with LibreOffice and Lubuntu 20.04, namely that text exported to a pdf file is not rendered; this is listed as a bug by LibreOffice, and is reported as a bug by Lubuntu. It is caused by the use of Qt5 in Lubuntu 20.04. It is not specific to LibreOffice 6.4; I have downloaded a 6.3 source on a dual-boot machine (18.04 ad 20.04) and the version compiled for 20.04 shows the problem whereas the version compiled for 18.04 does not.

There is a workaround, published by Lubuntu developers, involving the use of Cairo. The workaround is not perfect. I have been trying to set up a machine so that a non-technical user (who would  be unhappy using a terminal window) can export text to pdf from either new LO files or existing LO files, without crashing LO. I've had some success, but I have only a limited knowledge of the way in which applications are launched from the LXQt desktop, and so I'm looking for help to improve my imperfect solution.

Thanks in advance.

---

### Post by ActionParsnip on 2020-07-07
If you use a PDF Printer rather than the "Export to PDF" button, is it OK? This should be DE agnostic....

---

### Post by jet-bundle on 2020-07-07
Printing to pdf gives the same problem as exporting to pdf.

---

### Post by jet-bundle on 2020-07-07
I'm going to mark this as SOLVED because, after some further investigation, I have found another way round the problem.

Rather than modifying the launcher files to use Cairo, the problem can be avoided by replacing qt5 by gtk3 globally for the session. In Preferences > LXQt settings > Session settings, under Environment (advanced), I changed the value of SAL_USE_VCLPLUGIN from qt5 to gtk3. Then, after rebooting, LibreOffice was able to export to pdf successfully. (I also reverted the launcher files to their original versions, of course.)

---

### Post by ajgreeny on 2020-07-07
Another alternative to get a PDF is to use the print dialogue, but instead of printing to your local printer, use the ***Print to file*** option which I assume appears in all printer options irrespective of the make of printer and there choose PDF as file output..

---

### Post by jet-bundle on 2020-07-07
Thanks for the suggested alternative, but in fact printing to a file gave exactly the same problem as exporting directly to pdf. (In fact printing to paper didn't seem to work, either! But I didn't spend much time on this.)

---

### Post by Buovjaga on 2020-09-11
Lubuntu needs to switch away from defaulting to qt5. According to  LibreOffice developers, "using plain "qt5" VCL plugin in production is  something we don't recommend". Even the readme says it's "under  construction": [https://docs.libreoffice.org/vcl.html](https://docs.libreoffice.org/vcl.html)

---

