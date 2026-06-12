---
title: "Firefox Plugins don't work with version 3.6.x"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by jerremy-tamlin on 2010-07-27
My two favourite plugins for firefox are ImgLikeOpera and Net Usage Item, but these aren't always compatible with the latest version of Firefox.

I have no problem using an older version so you would think that this would be no problem but unfortunately older versions do not appear to be available from the Ubuntu repositories as both firefox-3.0 and firefox-3.5 are simply dummy packages that **BOTH** point to the one package firefox which is version 3.6.x in the Lucid repositories.

The following hack found [here http://www.techpavan.com/2009/07/17/firefox-addon-not-working-compatibility-hack-firefox-addons/]("http://www.techpavan.com/2009/07/17/firefox-addon-not-working-compatibility-hack-firefox-addons/") forces addons to run even if they are not officially compatible. ImgLikeOpera at lease seems to function fine.

**_Changing the indervidual plugin's install.rdf file._**
*Disabling the Addon Compatibility Check globally didn't work for me.* 

[LIST=1]
[*]Open the plugin.xpi file with file-roller or your archive program of choice.
```
file-roller ~/dnld/extensions/firefox/imglikeopera-0.6.17-fx.xpi
```
[*]Open install.rdf with gedit or your text editor of choice.
[*]Find the <em:maxVersion> tag and change it to the version of firefox you have "3.6.*"
```
        <em:maxVersion>3.6.*</em:maxVersion>

```
[*]Save the file and update the archive
[*]Reinstall the plugin and restart firefox.
[/LIST]

So far this has worked for me on Ubuntu Lucid. Time will tell ;)

---

### Post by jerremy-tamlin on 2010-07-28
It is also possible to edit the install.rdf file of already installed plugins (ie one's that weren't saved somewhere before they were installed.)

To do so simply edit the install.rdf file directly.
```
gedit ~/.mozilla/firefox/1t51d6pg.default/extensions/imglikeopera@imfo.ru/install.rdf
```
and change the <em:maxVersion> as specified above.
:p

---

