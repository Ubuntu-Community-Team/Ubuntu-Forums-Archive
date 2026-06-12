---
title: "Empathy. Script to add adium themes."
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oraerk on 2009-10-21
Probably there will be a lot of people, wanting to add some themes on Empathy, cause standart is quite boring. The "official" way is quite uneasy and slow (download and unpack in a dir). Surely you can use the provided script ([http://gist.github.com/191499](http://gist.github.com/191499)) but it does not work when directories in a file contain spaces in their names. So I've modified the script and here it is. Works from firefox 3.5 quite well (tested on karmic beta).

What you should do:
1) Create a script named **adiumxtra-install** somewhere (i did it to **/usr/local/sbin/**). For that use your preferred editor (my is gedit).
```
gedit /usr/local/sbin/adiumxtra-install
```and paste the following into the file:
```
#!/bin/sh
# Adium theme AdiumMessageStyle installer for Empathy
# Originally © 2009 Antono Vasiljev
# Licensed under the same terms as Empathy
# http://antono.info/en/165-install-adium-themes-to-empathy
# Changed by Vertlo Oraerk (did not work with directories containing spaces in the names)

if [ -z $1 ]
then
    echo
    echo "Usage:"
    echo "`basename $0` adiumxtra://some.url.here/extra"
    echo
    exit 1
else
    TMPDIR=`mktemp --directory`
    XTRAURL=`echo $1 | sed -e "s/^adiumxtra:/http:/"`
    DEST="$HOME/.local/share/adium/message-styles/"
    if [ ! -d $DEST ]
    then
        mkdir -v -p $DEST
    fi

    cd $TMPDIR
    echo "Downloding extra..."
    wget --no-verbose -O xtra.zip $XTRAURL
    unzip -qq xtra.zip

    ls -d ./*.AdiumMessageStyle/ > themes_to_copy.lst
    num_bytes=`wc -c themes_to_copy.lst | sed 's# themes_to_copy.lst##'` 

    if [ $num_bytes = 0 ]
    then
        echo "No themes found in downloaded file"
    else
        while read line 
        do
            echo cp -r \'$line\' "$DEST" | sh
        done < themes_to_copy.lst
        echo
        echo "Theme $XTRAURL was succesfully installed to $DEST"
    fi
    rm xtra.zip
    rm -r $TMPDIR
fi
exit 0

```2) Now change permissions so that file could be executed and provide url handlers for gnome.
```
chmod 755 /usr/local/sbin/adiumxtra-install
gconftool-2 -t string -s /desktop/gnome/url-handlers/adiumxtra/command "/usr/local/sbin/adiumxtra-install %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/enabled true
gconftool-2 -t bool -s /desktop/gnome/url-handlers/adiumxtra/needs_terminal false
```3) That is all. Now go to _[COLOR=Navy]**[http://www.adiumxtras.com/index.php?a=search&cat_id=5](http://www.adiumxtras.com/index.php?a=search&cat_id=5)**[/COLOR]_. Now themes will be installed automagically when clicked on "Install" link. 
No you can change conversation theme in Empathy through menu [I]**Edit** -> **Preferences** -> [B]Themes

[/B][/I][CENTER]***The result of installing "Renkoo Naked" theme***

***[IMG]http://img27.imageshack.us/img27/2705/screenshotdm.png[/IMG]***

[/CENTER]
[B]Please, provide feedback here (in this thread). 
When you happen to get some bug, please provide link to the theme you wanted to install (for testing purposes).[/B]

---

### Post by zoroko on 2009-10-26
Hey, thanks for the script, it works just fine. but.... the themes are not showing up in empathy. 

They are in ~/.local/share/adium/message-styles but they just don't show up in empathy? any ideas?

---

### Post by JEdwardP on 2009-10-29
That's my biggest problem with Empathy, and why I'll be sticking with Pidgin. I choose an Admium theme I thought would make Empathy usable for me (it isn't usable by default, because the fonts can't be changed or resized---or if they can, I flat-out missed it).

When I install a theme according to directions on the Empathy site, however, it appears as a new theme choice, but never actually applies that theme when I select it.

Still, I'll be glad to try this script when and if the "theme recognition bug" is fixed, before make the final decision to uninstall Empathy (thus "breaking" Karmic's Ubuntu-desktop---I won't comment here on my disappointment at finding that any specific  IM client is now supposedly thought of as something so critical that the removal of which should be discouraged--and going back to Pidgin.)

---

### Post by FuturePilot on 2009-10-29
> **JEdwardP said:**
> That's my biggest problem with Empathy, and why I'll be sticking with Pidgin. I choose an Admium theme I thought would make Empathy usable for me (it isn't usable by default, because the fonts can't be changed or resized---or if they can, I flat-out missed it).

When I install a theme according to directions on the Empathy site, however, it appears as a new theme choice, but never actually applies that theme when I select it.

Still, I'll be glad to try this script when and if the "theme recognition bug" is fixed, before make the final decision to uninstall Empathy (thus "breaking" Karmic's Ubuntu-desktop---I won't comment here on my disappointment at finding that any specific  IM client is now supposedly thought of as something so critical that the removal of which should be discouraged--and going back to Pidgin.)

Have you tried restarting Empathy after selecting a different theme?

---

### Post by joey-elijah on 2009-10-29
Great script! Works fine for me with supported themes.

(list @ [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes) )

I hope you don't mind but i've shared this on my blog.

[http://www.omgubuntu.co.uk/2009/10/one-click-install-of-adium-themes-in.html](http://www.omgubuntu.co.uk/2009/10/one-click-install-of-adium-themes-in.html)

---

### Post by yanns on 2009-10-29
You need sometimes root rigths:

> **oraerk said:**
> 
```
gedit /usr/local/sbin/adiumxtra-install
```and paste the following into the file:
[/code]

should be:
```
gksudo gedit /usr/local/sbin/adiumxtra-install
```and paste the following into the file:
[/code]

> **oraerk said:**
> 
```
chmod 755 /usr/local/sbin/adiumxtra-install
```

should be:
```
sudo chmod 755 /usr/local/sbin/adiumxtra-install
```

Thank you for your script. It works for me.

---

