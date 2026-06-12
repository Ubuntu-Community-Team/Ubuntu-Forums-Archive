---
title: "HowTo Nice Japanese Fonts (Kanji) in Ubuntu 15.10."
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by vilwarin on 2015-12-14
Here's a small 9-step HowTo for everyone having trouble setting up Ubuntu to display nice Japanese fonts.

Thanks to lots of great people that helped me put these things together.

**1. Activate stuff in Language Settings**
[LIST]
[*]Start Language Support
[*]Select Japanese language
[*]Select IBUS as input method
[/LIST]

**2. Get Windows Fonts**
Get yourself a Windows CD/DVD and mount it at /mnt/windowsxp-cdrom
then:
```

sudo apt-get install cabextract
sudo mkdir -p /usr/local/share/fonts/truetype
cd /usr/local/share/fonts/truetype
find /mnt/windowsxp-cdrom/ | grep -Ei 'MS(MINCHO|GOTHIC).TT_' | sudo xargs cabextract

```

**3. Get mikachan**
A question of taste. In my oppinion one of the best fonts for displaying Japanese. You can also use the Windows fonts or any other of your taste.
If so please replace mikachan by your choice hereafter.
```

sudo apt-get install ttf-mikachan

```

**4. Edit/Create /etc/fonts/conf.avail/69-language-selector-ja-jp.conf**
Ubuntu now works with a font-selector that allows to set fonts and other settings specific for a language.
Create your own one, or use or edit mine:
[HTML]
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <!-- Japanese (ja) -->
    <match target="pattern">

		<test name="lang" compare="contains">
            <string>ja</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>mikachan-P</string>
            <string>&#65325;&#65331; &#26126;&#26397;</string>
        </edit>
    </match>

    <match target="font">
        <test name="family" compare="contains">
            <string>&#65325;&#65331; &#26126;&#26397;</string>
        </test>
        <test name="pixelsize" compare="less_eq">
            <double>18</double>
        </test>
        <edit name="hintstyle" mode="assign">
            <const>hintnone</const>
        </edit>
        <edit name="embeddedbitmap">
             <bool>false</bool>
        </edit>
    </match>
    <match target="font">
        <test name="family" compare="contains">
            <string>mikachan-P</string>
        </test>
        <test name="pixelsize" compare="less_eq">
            <double>18</double>
        </test>
        <edit name="hintstyle" mode="assign">
            <const>hintnone</const>
        </edit>
        <edit name="embeddedbitmap">
             <bool>false</bool>
        </edit>
    </match>
    <!-- Japanese (ja) ends -->
</fontconfig>
[/HTML]

THEN remove other languague selectors (symlinks)
and add a symlink to the currently edited/created one
```

sudo rm /etc/fonts/conf.d/69-language-selector*
sudo ln -s /etc/fonts/conf.avail/69-language-selector-ja-jp.conf /etc/fonts/conf.d

```

**5. Edit/Create /etc/fonts/local.conf**
Again create one by yourself or copy/edit mine

[HTML]
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <include ignore_missing="yes" >/var/lib/defoma/fontconfig.d/fonts.conf</include>

    <!-- uncomment below to enable bitmapped fonts -->
    <!--
        <dir>/usr/X11R6/lib/X11/fonts</dir>
    -->

    <!-- enable subpixel rendering -->
    <match target="font">
        <test qual="all" name="rgba">
            <const>unknown</const>
        </test>
        <edit name="rgba" mode="assign"><const>rgb</const></edit>
    </match>

    <!-- autohinter -->
    <match target="font">
        <edit name="autohint" mode="assign">
            <bool>false</bool>
        </edit>
    </match>

    <match target="font" >
        <edit mode="assign" name="embeddedbitmap" >
            <bool>false</bool>
        </edit>
    </match>

    <dir>/usr/local/share/fonts</dir>
    <dir>/usr/share/fonts</dir>

    <dir>/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType</dir>
    <dir>/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID</dir>

    <!--
        Now we set up some replacement preferences.  They are used in order
        through a fallback mechanism if the specified font lacks a particular
        character.  I've put Japanese fonts first so that Japanese will
        generally have the correct glyphs.  If an application doesn't specify
        an Asian font and uses Chinese, for example, it will come out looking
        strange.

        You can also put in fonts for other languages
    -->

<alias>
 <family>serif</family>
 <prefer>
 <family>Ubuntu</family>
 <family>mikachan-P</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>DejaVu Serif</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>
 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>Ubuntu</family>
 <family>mikachan-P</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>
<alias>
 <family>monospace</family>
 <prefer>
 <family>Ubuntu</family>
 <family>mikachan-P</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans Mono</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>
</fontconfig>
[/HTML]

**6. Get Gnome Advanced-Settings**
```

sudo apt-get install gnome-tweak-tool

```

Set Smoothing to “Subpixel (LCDs)”.
Set Hinting to “None”.

**7. Firefox**
  Edit->Preferences: Content -> Fonts -> Adanced. Choose mikachan-P

**8. IBus**
Start Ubuntu "Text Entry"
Set default Font to mikachan-P

**9 Update font cache**
```
sudo fc-cache -f -v
```


Good Luck!

---

