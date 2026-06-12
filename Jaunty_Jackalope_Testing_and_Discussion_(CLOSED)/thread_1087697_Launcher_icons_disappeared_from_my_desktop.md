---
title: "Launcher icons disappeared from my desktop"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PsychedelicReaction on 2009-03-05
Yesterday I created a launcher on the desktop for the recently launched Google Calendar offline but gnome didn't draw the proper icon, even if I select it manually from the proprieties window. I tried to create more launchers for other applications and all of them were affected by the same problem.
The strange thing is that the Gmail offline launcher i created some days ago has the icon show, as well as all the mounted drives.
Here it is a screenshoot of the situation.
Of course i run Jaunty up to date.

---

### Post by nyarnon on 2009-03-05
Rule of thumb NEVER EVER use spaces in path or filenames (not even on windows it will give you hurt sooner or later). See if you can get rid of them and try again.

---

### Post by PsychedelicReaction on 2009-03-05
> **nyarnon said:**
> Rule of thumb NEVER EVER use spaces in path or filenames (not even on windows it will give you hurt sooner or later). See if you can get rid of them and try again.

thanks for the advice (but i think you should talk to google about that file :P) howevere it's not the reason, i tried creating a Gimp launcher and it's not working too.

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gimp
Name[en_US]=Gimp
Exec=gimp
Name=Gimp
Icon=gimp
```

---

### Post by nyarnon on 2009-03-05
Created one for you have a look I think you should lose the country code with Icon probably your Locale doesn't fit.

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Name=GIMP Image Editor
GenericName=Image Editor
GenericName[ar]=&#1605;&#1581;&#1585;&#1585; &#1589;&#1608;&#1585;
GenericName[be]=&#1056;&#1101;&#1076;&#1072;&#1082;&#1090;&#1072;&#1088; &#1074;&#1110;&#1076;&#1072;&#1088;&#1099;&#1089;&#1072;&#1118;
GenericName[bg]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1085;&#1072; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103;
GenericName[ca]=Editor d'imatges
GenericName[ca@valencia]=Editor d'imatges
GenericName[cs]=Editor obrázk&#367;
GenericName[da]=Billedredigering
GenericName[de]=Bildeditor
GenericName[dz]=&#3906;&#3935;&#3956;&#3906;&#3942;&#3851;&#3926;&#3938;&#3993;&#3923;&#3851; &#3934;&#3956;&#3923;&#3851;&#3921;&#3906;&#3851;&#3924;&#3853;
GenericName[en_CA]=Image Editor
GenericName[en_GB]=Image Editor
GenericName[eo]=Bilada Redaktilo
GenericName[es]=Editor de imagen
GenericName[et]=Pildiredaktor
GenericName[eu]=Irudi-editorea
GenericName[fa]=&#1608;&#1740;&#1585;&#1575;&#1740;&#1588;&#1711;&#1585; &#1578;&#1589;&#1608;&#1740;&#1585;
GenericName[fi]=Kuvankäsittely
GenericName[fr]=Éditeur d'image
GenericName[gl]=Editor de imaxes
GenericName[gu]=&#2714;&#2751;&#2724;&#2765;&#2736; &#2744;&#2690;&#2730;&#2750;&#2726;&#2709;
GenericName[hu]=Képszerkeszt&#337;
GenericName[is]=Myndvinnsluforrit
GenericName[it]=Editor immagine
GenericName[ja]=&#30011;&#20687;&#12456;&#12487;&#12451;&#12479;
GenericName[ka]=&#4306;&#4304;&#4315;&#4317;&#4321;&#4304;&#4334;&#4323;&#4314;&#4308;&#4305;&#4308;&#4305;&#4312;&#4321; &#4320;&#4308;&#4307;&#4304;&#4325;&#4322;&#4317;&#4320;&#4312;
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6035;&#6071;&#6038;&#6035;&#6098;&#6034;&#8203;&#6042;&#6076;&#6036;&#6039;&#6070;&#6038;
GenericName[ko]=&#51060;&#48120;&#51648; &#54200;&#51665;&#44592;
GenericName[lt]=Paveiksl&#279;li&#371; rengykl&#279;
GenericName[lv]=Att&#275;la redaktors
GenericName[mk]=&#1059;&#1088;&#1077;&#1076;&#1085;&#1080;&#1082; &#1079;&#1072; &#1089;&#1083;&#1080;&#1082;&#1080;
GenericName[nb]=Bildebehandler
GenericName[ne]=&#2331;&#2357;&#2367; &#2360;&#2350;&#2381;&#2346;&#2366;&#2342;&#2325;
GenericName[nl]=Afbeeldingsbewerker
GenericName[nn]=Biletbehandlar
GenericName[pa]=&#2586;&#2623;&#2673;&#2596;&#2608; &#2576;&#2593;&#2624;&#2591;&#2608;
GenericName[pl]=Edytor obrazu
GenericName[pt]=Editor de Imagens
GenericName[pt_BR]=Editor de Imagens
GenericName[ro]=Editor de imagine
GenericName[ru]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1081;
GenericName[sk]=Editor obrázkov
GenericName[sl]=Urejevalnik slik
GenericName[sr]=&#1054;&#1073;&#1088;&#1072;&#1076;&#1072; &#1089;&#1083;&#1080;&#1082;&#1072;
GenericName[sr@latin]=Obrada slika
GenericName[sv]=Bildredigerare
GenericName[ta]=&#2986;&#3007;&#2990;&#3021;&#2986; &#2980;&#3007;&#2992;&#3009;&#2980;&#3021;&#2980;&#3007;
GenericName[th]=&#3605;&#3633;&#3623;&#3649;&#3585;&#3657;&#3652;&#3586;&#3616;&#3634;&#3614;
GenericName[tr]=Resim Düzenleyici
GenericName[tt]=Sürät Tözätkeç
GenericName[uk]=&#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1100;
GenericName[vi]=B&#7897; biên so&#7841;n &#7843;nh
GenericName[xh]=UmHleli woMfanekiso
GenericName[zh_CN]=&#22270;&#20687;&#32534;&#36753;&#22120;
GenericName[zh_HK]=&#22294;&#29255;&#32232;&#36655;&#22120;
GenericName[zh_TW]=&#22294;&#29255;&#32232;&#36655;&#22120;
Comment=Create images and edit photographs
Comment[ar]=&#1571;&#1606;&#1588;&#1574; &#1589;&#1608;&#1585;&#1575; &#1608;&#1581;&#1585;&#1617;&#1585; &#1604;&#1602;&#1591;&#1575;&#1578;
Comment[be]=&#1057;&#1090;&#1074;&#1072;&#1088;&#1101;&#1085;&#1100;&#1085;&#1077; &#1074;&#1110;&#1076;&#1072;&#1088;&#1099;&#1089;&#1072;&#1118; &#1110; &#1088;&#1101;&#1076;&#1072;&#1075;&#1072;&#1074;&#1072;&#1085;&#1100;&#1085;&#1077; &#1092;&#1072;&#1090;&#1072;&#1075;&#1088;&#1072;&#1092;&#1110;&#1081;
Comment[bg]=&#1057;&#1098;&#1079;&#1076;&#1072;&#1074;&#1072;&#1085;&#1077; &#1085;&#1072; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1103; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1094;&#1080;&#1103; &#1085;&#1072; &#1089;&#1085;&#1080;&#1084;&#1082;&#1080;
Comment[ca]=Creeu imatges i editeu fotografies
Comment[ca@valencia]=Creeu imatges i editeu fotografies
Comment[cs]=Vytvá&#345;et obrázky a upravovat fotografie
Comment[da]=Opret billeder og redigér fotografier
Comment[de]=Bilder erstellen und Fotografien bearbeiten
Comment[dz]=&#3906;&#3935;&#3956;&#3906;&#3942;&#3851;&#3926;&#3938;&#3993;&#3923;&#3851;&#3930;&#3956;&#3851; &#3906;&#3942;&#3938;&#3851;&#3926;&#3942;&#3984;&#4018;&#3956;&#3923;&#3851;&#3936;&#3926;&#3921;&#3851;&#3923;&#3954;&#3851;&#3921;&#3908;&#3851; &#3921;&#3924;&#3938;&#3851;&#3930;&#3956;&#3851;&#3934;&#3956;&#3923;&#3851;&#3921;&#3906;&#3851;&#3936;&#3926;&#3921;&#3853;
Comment[en_CA]=Create images and edit photographs
Comment[en_GB]=Create images and edit photographs
Comment[eo]=Kreu bildojn a&#365; redaktu fotojn
Comment[es]=Cree imágenes y edite fotografías
Comment[et]=Loo pilte ja redigeeri fotosid
Comment[eu]=Sortu irudiak eta editatu argazkiak
Comment[fi]=Luo kuvia ja muokkaa valokuvia
Comment[fr]=Créer des images et modifier des photographies
Comment[gl]=Crear imaxes e editar fotografías
Comment[gu]=&#2714;&#2751;&#2724;&#2765;&#2736;&#2763; &#2732;&#2728;&#2750;&#2741;&#2763; &#2693;&#2728;&#2759; &#2731;&#2763;&#2719;&#2750;&#2707;&#2734;&#2750;&#2690; &#2731;&#2759;&#2736;&#2731;&#2750;&#2736; &#2709;&#2736;&#2763;
Comment[hu]=Képek létrehozása és fotók szerkesztése
Comment[it]=Crea immagini o modifica fotografie
Comment[ja]=&#30011;&#20687;&#12398;&#20316;&#25104;&#12392;&#20889;&#30495;&#12398;&#32232;&#38598;&#12434;&#34892;&#12356;&#12414;&#12377;
Comment[km]=&#6036;&#6020;&#6098;&#6016;&#6078;&#6031;&#8203;&#6042;&#6076;&#6036;&#6039;&#6070;&#6038; &#6035;&#6071;&#6020; &#6016;&#6082;&#6047;&#6040;&#6098;&#6042;&#6077;&#6043;&#8203;&#6042;&#6076;&#6036;&#6032;&#6031;
Comment[ko]=&#51060;&#48120;&#51648;&#47484; &#47564;&#46308;&#44144;&#45208; &#49324;&#51652;&#51012; &#54200;&#51665;&#54633;&#45768;&#45796;.
Comment[lt]=Kurti paveiksl&#279;lius ir redaguoti fotografijas
Comment[lv]=Att&#275;lu vai fotogr&#257;fiju izveide un kori&#291;&#275;šana
Comment[mk]=&#1053;&#1072;&#1087;&#1088;&#1072;&#1074;&#1080; &#1089;&#1083;&#1080;&#1082;&#1080; &#1080; &#1091;&#1088;&#1077;&#1076;&#1080; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1080;
Comment[nb]=Lag bilder og rediger fotografier
Comment[ne]=&#2331;&#2357;&#2367; &#2360;&#2367;&#2352;&#2381;&#2332;&#2344;&#2366; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381; &#2352; &#2347;&#2379;&#2335;&#2379;&#2327;&#2381;&#2352;&#2366;&#2347; &#2360;&#2350;&#2381;&#2346;&#2366;&#2342;&#2344; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381;
Comment[nl]=Afbeeldingen of foto's aanmaken en bewerken
Comment[nn]=Lag teikningar eller rediger foto
Comment[pa]=&#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2579; &#2565;&#2596;&#2631; &#2596;&#2616;&#2613;&#2624;&#2608;&#2622;&#2562; &#2616;&#2635;&#2599;&#2635;
Comment[pl]=Program do tworzenia oraz obróbki obrazów i fotografii
Comment[pt]=Criar imagens e editar fotografias
Comment[pt_BR]=Crie e edite imagens ou fotografias
Comment[ro]=Creeaz&#259; imagini &#537;i editeaz&#259; fotografii
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1081; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1081;
Comment[sl]=Ustvari slike in uredi fotografije
Comment[sr]=&#1053;&#1072;&#1087;&#1088;&#1072;&#1074;&#1080;&#1090;&#1077; &#1089;&#1083;&#1080;&#1082;&#1077; &#1080; &#1091;&#1088;&#1077;&#1076;&#1080;&#1090;&#1077; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1112;&#1077;
Comment[sr@latin]=Napravite slike i uredite fotografije
Comment[sv]=Skapa bilder och redigera fotografier
Comment[ta]=&#2986;&#3007;&#2990;&#3021;&#2986;&#2969;&#3021;&#2965;&#2995;&#3016; &#2953;&#2992;&#3009;&#2997;&#3006;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2990;&#2993;&#3021;&#2993;&#3009;&#2990;&#3021; &#2986;&#2975;&#2969;&#3021;&#2965;&#2995;&#3016; &#2980;&#3007;&#2992;&#3009;&#2980;&#3021;&#2980;&#2997;&#3009;&#2990;&#3021;
Comment[tr]=Resim ya da foto&#287;raflar&#305; olu&#351;turun ve düzenleyin
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103; &#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1100; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1092;&#1086;&#1090;&#1086;&#1075;&#1088;&#1072;&#1092;&#1110;&#1081;
Comment[vi]=T&#7841;o và biên so&#7841;n &#7843;nh hay &#7843;nh ch&#7909;p
Comment[zh_CN]=&#21019;&#24314;&#22270;&#20687;&#25110;&#32534;&#36753;&#29031;&#29255;
Comment[zh_HK]=&#24314;&#31435;&#22294;&#20687;&#33287;&#32232;&#36655;&#29031;&#29255;
Comment[zh_TW]=&#24314;&#31435;&#22294;&#20687;&#33287;&#32232;&#36655;&#29031;&#29255;
Exec=gimp-2.6 %U
TryExec=gimp-2.6
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.6.5
X-GNOME-Bugzilla-OtherBinaries=gimp-2.6
StartupNotify=true
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/tiff;image/jpeg;image/x-psd;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;image/x-wmf;
X-Ubuntu-Gettext-Domain=gimp20

```

---

### Post by PsychedelicReaction on 2009-03-05
Im italian but im using ubuntu in english.

however also your launcher doesn't show the icon, thanks for the try.

---

### Post by nyarnon on 2009-03-05
does it launch gimp?

---

### Post by nyarnon on 2009-03-05
Hmmm looks like we have a bug here, just did an update and lost my icons too starting a *.desktop file now returns with a message that the starter is not trusted? Hmm looks like it needs the execute bit set to return to normal. Could you try that?

---

### Post by PsychedelicReaction on 2009-03-05
yes same here, i didn't notice the alert. after clicking "Launch anyway" and "Mark as Trusted" the program starts (but still no icon).

now ubuntu has the uac too :D

---

### Post by nyarnon on 2009-03-05
Ok then thats probably a different issue. Your gimp is one of the repository?

---

### Post by PsychedelicReaction on 2009-03-05
yes, it should be the ubuntu repository package

---

### Post by nyarnon on 2009-03-06
Could you check if the files mentioned in synaptic are all there especially the icon? What are the user/permisions for the icon?

---

### Post by uBeer on 2009-03-06
Read this:
[http://www.cyberciti.biz/tips/debunking-the-linux-is-virus-free-myth.html](http://www.cyberciti.biz/tips/debunking-the-linux-is-virus-free-myth.html)

I think this is a step to fix this security issue.

---

### Post by chrisccoulson on 2009-03-06
uBeer is correct. This is a patch that was recently applied specifically in response to that article, which got quite a lot of coverage on Slashdot (or a site like that).

---

### Post by nyarnon on 2009-03-06
Yes I remember the article, didn't give it much attention though because IMHO this has more to do with the original art of hacking (social engineering) then with viruses. The warning on top of this forum about malicious commands spells it out. No way you will ever be able to stop that except by educating people.

That said, of course any action that hardens the security of Linux is worth every effort. This is a very good one indeed. As a launcher is very well to be seen as an executable and should therefore IMHO need executable rights before being executed.

---

### Post by PsychedelicReaction on 2009-03-07
> **nyarnon said:**
> Could you check if the files mentioned in synaptic are all there especially the icon? What are the user/permisions for the icon?

sorry but which files do u mean?

some icons i'm using have read and write permissions for all, and are not displayed.

---

### Post by nyarnon on 2009-03-07
If you installed through app or synaptic you should be able to see a list of installed files in synaptic. If not you can set it through settings. Cant give you the exact path becouse I'm on a Dutch distro. As to your question for help with your xorg.conf. There are several online apps that can generate one for you.

---

### Post by PsychedelicReaction on 2009-03-08
sorry but im noy getting the point, i didn't require any help regarding xorg.conf ^_^

however, you mean this list? 

```
/.
/usr
/usr/share
/usr/share/pixmaps
/usr/share/pixmaps/gimp.xpm
/usr/share/applications
/usr/share/applications/gimp.desktop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/gimp-2.6.1.gz
/usr/share/doc
/usr/share/doc/gimp
/usr/share/doc/gimp/README.MIDI
/usr/share/doc/gimp/Wilber.xcf.gz
/usr/share/doc/gimp/Wilber.xcf.gz.README
/usr/share/doc/gimp/Wilber_Construction_Kit.xcf.gz
/usr/share/doc/gimp/copyright
/usr/share/menu
/usr/share/menu/gimp
/usr/share/python-support
/usr/share/python-support/gimp.dirs
/usr/bin
/usr/bin/gimp-2.6
/usr/bin/gimp-console-2.6
/usr/lib
/usr/lib/gimp
/usr/lib/gimp/2.0
/usr/lib/gimp/2.0/environ
/usr/lib/gimp/2.0/environ/default.env
/usr/lib/gimp/2.0/environ/pygimp.env
/usr/lib/gimp/2.0/modules
/usr/lib/gimp/2.0/modules/libcolor-selector-cmyk.so
/usr/lib/gimp/2.0/modules/libcolor-selector-cmyk.la
/usr/lib/gimp/2.0/modules/libcolor-selector-water.so
/usr/lib/gimp/2.0/modules/libcolor-selector-water.la
/usr/lib/gimp/2.0/modules/libcolor-selector-wheel.so
/usr/lib/gimp/2.0/modules/libcolor-selector-wheel.la
/usr/lib/gimp/2.0/modules/libdisplay-filter-color-blind.so
/usr/lib/gimp/2.0/modules/libdisplay-filter-color-blind.la
/usr/lib/gimp/2.0/modules/libdisplay-filter-gamma.so
/usr/lib/gimp/2.0/modules/libdisplay-filter-gamma.la
/usr/lib/gimp/2.0/modules/libdisplay-filter-high-contrast.so
/usr/lib/gimp/2.0/modules/libdisplay-filter-high-contrast.la
/usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so
/usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.la
/usr/lib/gimp/2.0/modules/libdisplay-filter-proof.so
/usr/lib/gimp/2.0/modules/libdisplay-filter-proof.la
/usr/lib/gimp/2.0/modules/libcontroller-midi.so
/usr/lib/gimp/2.0/modules/libcontroller-midi.la
/usr/lib/gimp/2.0/modules/libcontroller-linux-input.so
/usr/lib/gimp/2.0/modules/libcontroller-linux-input.la
/usr/lib/gimp/2.0/interpreters
/usr/lib/gimp/2.0/interpreters/default.interp
/usr/lib/gimp/2.0/interpreters/pygimp.interp
/usr/lib/gimp/2.0/plug-ins
/usr/lib/gimp/2.0/plug-ins/script-fu
/usr/lib/gimp/2.0/plug-ins/pyconsole.py
/usr/lib/gimp/2.0/plug-ins/colorxhtml.py
/usr/lib/gimp/2.0/plug-ins/foggify.py
/usr/lib/gimp/2.0/plug-ins/palette-offset.py
/usr/lib/gimp/2.0/plug-ins/palette-sort.py
/usr/lib/gimp/2.0/plug-ins/palette-to-gradient.py
/usr/lib/gimp/2.0/plug-ins/py-slice.py
/usr/lib/gimp/2.0/plug-ins/python-console.py
/usr/lib/gimp/2.0/plug-ins/python-eval.py
/usr/lib/gimp/2.0/plug-ins/color-rotate
/usr/lib/gimp/2.0/plug-ins/file-bmp
/usr/lib/gimp/2.0/plug-ins/file-faxg3
/usr/lib/gimp/2.0/plug-ins/file-fits
/usr/lib/gimp/2.0/plug-ins/file-fli
/usr/lib/gimp/2.0/plug-ins/file-ico
/usr/lib/gimp/2.0/plug-ins/file-jpeg
/usr/lib/gimp/2.0/plug-ins/file-psd-load
/usr/lib/gimp/2.0/plug-ins/file-psd-save
/usr/lib/gimp/2.0/plug-ins/file-sgi
/usr/lib/gimp/2.0/plug-ins/file-uri
/usr/lib/gimp/2.0/plug-ins/file-xjt
/usr/lib/gimp/2.0/plug-ins/flame
/usr/lib/gimp/2.0/plug-ins/fractal-explorer
/usr/lib/gimp/2.0/plug-ins/gfig
/usr/lib/gimp/2.0/plug-ins/gimpressionist
/usr/lib/gimp/2.0/plug-ins/gradient-flare
/usr/lib/gimp/2.0/plug-ins/help
/usr/lib/gimp/2.0/plug-ins/ifs-compose
/usr/lib/gimp/2.0/plug-ins/imagemap
/usr/lib/gimp/2.0/plug-ins/lighting
/usr/lib/gimp/2.0/plug-ins/map-object
/usr/lib/gimp/2.0/plug-ins/maze
/usr/lib/gimp/2.0/plug-ins/metadata
/usr/lib/gimp/2.0/plug-ins/pagecurl
/usr/lib/gimp/2.0/plug-ins/print
/usr/lib/gimp/2.0/plug-ins/selection-to-path
/usr/lib/gimp/2.0/plug-ins/alien-map
/usr/lib/gimp/2.0/plug-ins/align-layers
/usr/lib/gimp/2.0/plug-ins/animation-optimize
/usr/lib/gimp/2.0/plug-ins/animation-play
/usr/lib/gimp/2.0/plug-ins/antialias
/usr/lib/gimp/2.0/plug-ins/apply-canvas
/usr/lib/gimp/2.0/plug-ins/blinds
/usr/lib/gimp/2.0/plug-ins/blur
/usr/lib/gimp/2.0/plug-ins/blur-gauss
/usr/lib/gimp/2.0/plug-ins/blur-gauss-selective
/usr/lib/gimp/2.0/plug-ins/blur-motion
/usr/lib/gimp/2.0/plug-ins/border-average
/usr/lib/gimp/2.0/plug-ins/bump-map
/usr/lib/gimp/2.0/plug-ins/cartoon
/usr/lib/gimp/2.0/plug-ins/channel-mixer
/usr/lib/gimp/2.0/plug-ins/checkerboard
/usr/lib/gimp/2.0/plug-ins/cml-explorer
/usr/lib/gimp/2.0/plug-ins/color-cube-analyze
/usr/lib/gimp/2.0/plug-ins/color-enhance
/usr/lib/gimp/2.0/plug-ins/color-exchange
/usr/lib/gimp/2.0/plug-ins/color-to-alpha
/usr/lib/gimp/2.0/plug-ins/colorify
/usr/lib/gimp/2.0/plug-ins/colormap-remap
/usr/lib/gimp/2.0/plug-ins/compose
/usr/lib/gimp/2.0/plug-ins/contrast-normalize
/usr/lib/gimp/2.0/plug-ins/contrast-retinex
/usr/lib/gimp/2.0/plug-ins/contrast-stretch
/usr/lib/gimp/2.0/plug-ins/contrast-stretch-hsv
/usr/lib/gimp/2.0/plug-ins/convolution-matrix
/usr/lib/gimp/2.0/plug-ins/crop-auto
/usr/lib/gimp/2.0/plug-ins/crop-zealous
/usr/lib/gimp/2.0/plug-ins/cubism
/usr/lib/gimp/2.0/plug-ins/curve-bend
/usr/lib/gimp/2.0/plug-ins/decompose
/usr/lib/gimp/2.0/plug-ins/deinterlace
/usr/lib/gimp/2.0/plug-ins/depth-merge
/usr/lib/gimp/2.0/plug-ins/despeckle
/usr/lib/gimp/2.0/plug-ins/destripe
/usr/lib/gimp/2.0/plug-ins/diffraction
/usr/lib/gimp/2.0/plug-ins/displace
/usr/lib/gimp/2.0/plug-ins/edge
/usr/lib/gimp/2.0/plug-ins/edge-dog
/usr/lib/gimp/2.0/plug-ins/edge-laplace
/usr/lib/gimp/2.0/plug-ins/edge-neon
/usr/lib/gimp/2.0/plug-ins/edge-sobel
/usr/lib/gimp/2.0/plug-ins/emboss
/usr/lib/gimp/2.0/plug-ins/engrave
/usr/lib/gimp/2.0/plug-ins/file-aa
/usr/lib/gimp/2.0/plug-ins/file-cel
/usr/lib/gimp/2.0/plug-ins/file-compressor
/usr/lib/gimp/2.0/plug-ins/file-csource
/usr/lib/gimp/2.0/plug-ins/file-desktop-link
/usr/lib/gimp/2.0/plug-ins/file-dicom
/usr/lib/gimp/2.0/plug-ins/file-gbr
/usr/lib/gimp/2.0/plug-ins/file-gif-load
/usr/lib/gimp/2.0/plug-ins/file-gif-save
/usr/lib/gimp/2.0/plug-ins/file-gih
/usr/lib/gimp/2.0/plug-ins/file-glob
/usr/lib/gimp/2.0/plug-ins/file-header
/usr/lib/gimp/2.0/plug-ins/file-html-table
/usr/lib/gimp/2.0/plug-ins/file-mng
/usr/lib/gimp/2.0/plug-ins/file-pat
/usr/lib/gimp/2.0/plug-ins/file-pcx
/usr/lib/gimp/2.0/plug-ins/file-pdf
/usr/lib/gimp/2.0/plug-ins/file-pix
/usr/lib/gimp/2.0/plug-ins/file-png
/usr/lib/gimp/2.0/plug-ins/file-pnm
/usr/lib/gimp/2.0/plug-ins/file-ps
/usr/lib/gimp/2.0/plug-ins/file-psp
/usr/lib/gimp/2.0/plug-ins/file-raw
/usr/lib/gimp/2.0/plug-ins/file-sunras
/usr/lib/gimp/2.0/plug-ins/file-svg
/usr/lib/gimp/2.0/plug-ins/file-tga
/usr/lib/gimp/2.0/plug-ins/file-tiff-load
/usr/lib/gimp/2.0/plug-ins/file-tiff-save
/usr/lib/gimp/2.0/plug-ins/file-wmf
/usr/lib/gimp/2.0/plug-ins/file-xbm
/usr/lib/gimp/2.0/plug-ins/file-xpm
/usr/lib/gimp/2.0/plug-ins/file-xwd
/usr/lib/gimp/2.0/plug-ins/film
/usr/lib/gimp/2.0/plug-ins/filter-pack
/usr/lib/gimp/2.0/plug-ins/fractal-trace
/usr/lib/gimp/2.0/plug-ins/gee
/usr/lib/gimp/2.0/plug-ins/gee-zoom
/usr/lib/gimp/2.0/plug-ins/gradient-map
/usr/lib/gimp/2.0/plug-ins/grid
/usr/lib/gimp/2.0/plug-ins/guillotine
/usr/lib/gimp/2.0/plug-ins/hot
/usr/lib/gimp/2.0/plug-ins/illusion
/usr/lib/gimp/2.0/plug-ins/iwarp
/usr/lib/gimp/2.0/plug-ins/jigsaw
/usr/lib/gimp/2.0/plug-ins/lcms
/usr/lib/gimp/2.0/plug-ins/lens-apply
/usr/lib/gimp/2.0/plug-ins/lens-distortion
/usr/lib/gimp/2.0/plug-ins/lens-flare
/usr/lib/gimp/2.0/plug-ins/mail
/usr/lib/gimp/2.0/plug-ins/max-rgb
/usr/lib/gimp/2.0/plug-ins/mosaic
/usr/lib/gimp/2.0/plug-ins/newsprint
/usr/lib/gimp/2.0/plug-ins/nl-filter
/usr/lib/gimp/2.0/plug-ins/noise-hsv
/usr/lib/gimp/2.0/plug-ins/noise-randomize
/usr/lib/gimp/2.0/plug-ins/noise-rgb
/usr/lib/gimp/2.0/plug-ins/noise-solid
/usr/lib/gimp/2.0/plug-ins/noise-spread
/usr/lib/gimp/2.0/plug-ins/nova
/usr/lib/gimp/2.0/plug-ins/oilify
/usr/lib/gimp/2.0/plug-ins/photocopy
/usr/lib/gimp/2.0/plug-ins/pixelize
/usr/lib/gimp/2.0/plug-ins/plasma
/usr/lib/gimp/2.0/plug-ins/plugin-browser
/usr/lib/gimp/2.0/plug-ins/polar-coords
/usr/lib/gimp/2.0/plug-ins/procedure-browser
/usr/lib/gimp/2.0/plug-ins/qbist
/usr/lib/gimp/2.0/plug-ins/red-eye-removal
/usr/lib/gimp/2.0/plug-ins/ripple
/usr/lib/gimp/2.0/plug-ins/rotate
/usr/lib/gimp/2.0/plug-ins/sample-colorize
/usr/lib/gimp/2.0/plug-ins/screenshot
/usr/lib/gimp/2.0/plug-ins/semi-flatten
/usr/lib/gimp/2.0/plug-ins/sharpen
/usr/lib/gimp/2.0/plug-ins/shift
/usr/lib/gimp/2.0/plug-ins/sinus
/usr/lib/gimp/2.0/plug-ins/smooth-palette
/usr/lib/gimp/2.0/plug-ins/softglow
/usr/lib/gimp/2.0/plug-ins/sparkle
/usr/lib/gimp/2.0/plug-ins/sphere-designer
/usr/lib/gimp/2.0/plug-ins/threshold-alpha
/usr/lib/gimp/2.0/plug-ins/tile
/usr/lib/gimp/2.0/plug-ins/tile-glass
/usr/lib/gimp/2.0/plug-ins/tile-paper
/usr/lib/gimp/2.0/plug-ins/tile-seamless
/usr/lib/gimp/2.0/plug-ins/tile-small
/usr/lib/gimp/2.0/plug-ins/unit-editor
/usr/lib/gimp/2.0/plug-ins/unsharp-mask
/usr/lib/gimp/2.0/plug-ins/value-invert
/usr/lib/gimp/2.0/plug-ins/value-propagate
/usr/lib/gimp/2.0/plug-ins/van-gogh-lic
/usr/lib/gimp/2.0/plug-ins/video
/usr/lib/gimp/2.0/plug-ins/warp
/usr/lib/gimp/2.0/plug-ins/waves
/usr/lib/gimp/2.0/plug-ins/web-browser
/usr/lib/gimp/2.0/plug-ins/whirl-pinch
/usr/lib/gimp/2.0/plug-ins/wind
/usr/lib/gimp/2.0/python
/usr/lib/gimp/2.0/python/pygimp-logo.png
/usr/lib/gimp/2.0/python/gimp.so
/usr/lib/gimp/2.0/python/gimp.la
/usr/lib/gimp/2.0/python/_gimpenums.so
/usr/lib/gimp/2.0/python/_gimpenums.la
/usr/lib/gimp/2.0/python/gimpcolor.so
/usr/lib/gimp/2.0/python/gimpcolor.la
/usr/lib/gimp/2.0/python/_gimpui.so
/usr/lib/gimp/2.0/python/_gimpui.la
/usr/lib/gimp/2.0/python/gimpthumb.so
/usr/lib/gimp/2.0/python/gimpthumb.la
/usr/lib/gimp/2.0/python/gimpenums.py
/usr/lib/gimp/2.0/python/gimpfu.py
/usr/lib/gimp/2.0/python/gimpplugin.py
/usr/lib/gimp/2.0/python/gimpshelf.py
/usr/lib/gimp/2.0/python/gimpui.py
/usr/share/man/man1/gimp.1.gz
/usr/share/man/man1/gimp-console.1.gz
/usr/share/man/man1/gimp-console-2.6.1.gz
/usr/share/doc/gimp/README
/usr/share/doc/gimp/README.Debian
/usr/share/doc/gimp/NEWS.gz
/usr/share/doc/gimp/NEWS.Debian.gz
/usr/share/doc/gimp/AUTHORS.gz
/usr/share/doc/gimp/changelog.Debian.gz
/usr/bin/gimp
/usr/bin/gimp-console


```

---

### Post by nyarnon on 2009-03-08
Yes OK now open Nautilus and go to /usr/share/applications, Does the gimp.desktop there show the icon?

---

### Post by PsychedelicReaction on 2009-03-08
yes it does, i checked all the icons that are not shown on the desktop and they all exist in the proper path.

---

### Post by nyarnon on 2009-03-09
Now copy this launcher to your desktop and see if it still shows the icon

---

### Post by PsychedelicReaction on 2009-03-10
yes with copy and paste it shows the icon, as well as with drag and drop from the menu. the problem sill remains with the launchers created on the desktop, with every icon i choose (also for example icons in my home directory).

---

### Post by nyarnon on 2009-03-10
Hmm could be a number of problems then. Ah wait a minute I just created a launcher and I think I just have found your problem. After creating the launcher did you mark it as executable? I'm gonna file a bugreport on that one.

Please confirm: [https://bugs.launchpad.net/ubuntu/+bug/340425](https://bugs.launchpad.net/ubuntu/+bug/340425)

---

### Post by PsychedelicReaction on 2009-03-10
Here it is the problem. No, ubuntu doesn't mark the launcher as executable, after doing it manually the icon comes back.

---

### Post by nyarnon on 2009-03-10
Ok please mark it confirmed in the bugreport.

---

### Post by PsychedelicReaction on 2009-03-10
done, thank you!

---

### Post by nyarnon on 2009-03-10
Your welcome.

---

