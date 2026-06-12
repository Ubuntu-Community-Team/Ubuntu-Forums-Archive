---
title: "cheese preferences save location"
date: 2016-09-29
forum: MINT
---

### Post by Kevin McCready on 2016-09-29
There is no option in the preferences to change the location where files are saved.
Hoping someone can help. When I tried to find out where a config file might live I had no luck.
```

locate -i cheese
/usr/lib/libreoffice/share/gallery/www-back/cheese.jpg
/usr/share/app-install/desktop/cheese:cheese.desktop
/usr/share/app-install/desktop/cheese:org.gnome.Cheese.desktop
/usr/share/app-install/icons/cheese.png
/usr/share/cowsay/cows/cheese.cow
/usr/share/help-langpack/en_AU/ubuntu-help/app-cheese.page
/usr/share/help-langpack/en_CA/ubuntu-help/app-cheese.page
/usr/share/help-langpack/en_GB/ubuntu-help/app-cheese.page
/usr/share/icons/HighContrast/16x16/apps/cheese.png
/usr/share/icons/HighContrast/22x22/apps/cheese.png
/usr/share/icons/HighContrast/24x24/apps/cheese.png
/usr/share/icons/HighContrast/256x256/apps/cheese.png
/usr/share/icons/HighContrast/32x32/apps/cheese.png
/usr/share/icons/HighContrast/48x48/apps/cheese.png
/usr/share/icons/Mint-X/apps/16/cheese.png
/usr/share/icons/Mint-X/apps/22/cheese.png
/usr/share/icons/Mint-X/apps/24/cheese.png
/usr/share/icons/Mint-X/apps/32/cheese.png
/usr/share/icons/Mint-X/apps/48/cheese.png
/usr/share/icons/Mint-X/apps/96/cheese.svg
/usr/share/icons/Mint-Y/apps/16/cheese.png
/usr/share/icons/Mint-Y/apps/22/cheese.png
/usr/share/icons/Mint-Y/apps/24/cheese.png
/usr/share/icons/Mint-Y/apps/256/cheese.png
/usr/share/icons/Mint-Y/apps/32/cheese.png
/usr/share/icons/Mint-Y/apps/48/cheese.png
/usr/share/icons/Mint-Y/apps/64/cheese.png
/usr/share/icons/Mint-Y/apps/96/cheese.png
/usr/share/locale-langpack/en@shaw/LC_MESSAGES/cheese.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/cheese.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/cheese.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/cheese.mo


```

---

### Post by howefield on 2016-09-30
Thread moved to the "*MINT*" forum.

Not sure about Mint but Ubuntu doesn't have a cheese config file but rather a series of settings that can be found in the dconf configuration system.

org > gnome > cheese

---

### Post by Kevin McCready on 2016-10-02
Thanks for tip. I still couldn't find where it's hiding. Anyone?

---

### Post by howefield on 2016-10-02
If you haven't got dconf-editor installed you'd need to install it.

```
sudo apt install dconf-editor
```

---

### Post by Kevin McCready on 2016-10-02
Thanks. I installed dconf-editor and found cheese. Then I clicked on Next and it said:
file:///home/k/.cache/.fr-XpcaM3/cheese-3.17.1/src
which I think is a virtual directory.
So I'm still unable to change where it stores saved files. And I can't seem to change any values via the dconf-editor

---

### Post by howefield on 2016-10-03
> **Kevin McCready said:**
> And I can't seem to change any values via the dconf-editor

Left or right clicking on the values should give you a pop up allowing values to be changed.

---

### Post by Kevin McCready on 2016-10-05
Thanks for the tip of clicking in on the field. It opened up a grey box but I couldn't edit anything in the box.

---

### Post by howefield on 2016-10-06
Did you toggle the on/off switch - as per the image in post 6. Toggle the switch next to *Use Default Value* and the values should become editable.

---

### Post by Kevin McCready on 2016-10-06
Everything was greyed out. No options to toggle.

---

### Post by Kevin McCready on 2017-05-20
bump and how can I change the frame rate?

---

### Post by gordintoronto on 2017-05-20
When I run dconf-editor, I can go to org/gnome/cheese/photo-path
I toggle "Use default value" and enter "Pictures" as the Custom value.

Sure enough, Cheese saves images in my Pictures folder.

---

### Post by Kevin McCready on 2017-05-22
> **gordintoronto said:**
> When I run dconf-editor, I can go to org/gnome/cheese/photo-path
I toggle "Use default value" and enter "Pictures" as the Custom value.

Sure enough, Cheese saves images in my Pictures folder.

ta. see above. all boxes are greyed out for me. I've been through most of these files via the "locate" command but I don't have the skills to find a solution.

/usr/bin/cheese
/usr/lib/cheese
/usr/lib/cheese/gnome-camera-service
/usr/lib/i386-linux-gnu/libcheese-gtk.so.25
/usr/lib/i386-linux-gnu/libcheese-gtk.so.25.0.3
/usr/lib/i386-linux-gnu/libcheese.so.8
/usr/lib/i386-linux-gnu/libcheese.so.8.0.3
/usr/lib/libreoffice/share/gallery/www-back/cheese.jpg
/usr/share/app-install/desktop/cheese:cheese.desktop
/usr/share/app-install/desktop/cheese:org.gnome.Cheese.desktop
/usr/share/app-install/icons/cheese.png
/usr/share/applications/cheese.desktop
/usr/share/apport/package-hooks/source_cheese.py
/usr/share/cowsay/cows/cheese.cow
/usr/share/doc/cheese
/usr/share/doc/cheese-common
/usr/share/doc/libcheese-gtk25
/usr/share/doc/libcheese8
/usr/share/doc/cheese/AUTHORS
/usr/share/doc/cheese/NEWS.gz
/usr/share/doc/cheese/README
/usr/share/doc/cheese/changelog.Debian.gz
/usr/share/doc/cheese/copyright
/usr/share/doc/cheese-common/AUTHORS
/usr/share/doc/cheese-common/NEWS.gz
/usr/share/doc/cheese-common/README
/usr/share/doc/cheese-common/changelog.Debian.gz
/usr/share/doc/cheese-common/copyright
/usr/share/doc/libcheese-gtk25/AUTHORS
/usr/share/doc/libcheese-gtk25/NEWS.gz
/usr/share/doc/libcheese-gtk25/README
/usr/share/doc/libcheese-gtk25/changelog.Debian.gz
/usr/share/doc/libcheese-gtk25/copyright
/usr/share/doc/libcheese8/AUTHORS
/usr/share/doc/libcheese8/NEWS.gz
/usr/share/doc/libcheese8/README
/usr/share/doc/libcheese8/changelog.Debian.gz
/usr/share/doc/libcheese8/copyright
/usr/share/help/C/cheese
/usr/share/help/C/cheese/burst-mode.page
/usr/share/help/C/cheese/effects-apply.page
/usr/share/help/C/cheese/figures
/usr/share/help/C/cheese/index.page
/usr/share/help/C/cheese/introduction.page
/usr/share/help/C/cheese/legal.xml
/usr/share/help/C/cheese/photo-delete.page
/usr/share/help/C/cheese/photo-save.page
/usr/share/help/C/cheese/photo-take.page
/usr/share/help/C/cheese/photo-view.page
/usr/share/help/C/cheese/pref-countdown.page
/usr/share/help/C/cheese/pref-flash.page
/usr/share/help/C/cheese/pref-fullscreen.page
/usr/share/help/C/cheese/pref-image-properties.page
/usr/share/help/C/cheese/pref-resolution.page
/usr/share/help/C/cheese/video-record.page
/usr/share/help/C/cheese/figures/cheese-delete.png
/usr/share/help/C/cheese/figures/cheese-effects.png
/usr/share/help/C/cheese/figures/cheese-introduction.png
/usr/share/help/C/cheese/figures/cheese-record.png
/usr/share/help/C/cheese/figures/cheese-save.png
/usr/share/help/C/cheese/figures/cheese-take.png
/usr/share/help/C/cheese/figures/cheese.png
/usr/share/help/C/cheese/figures/effects.png
/usr/share/help/C/cheese/figures/image-properties.png
/usr/share/help/C/cheese/figures/settings.png
/usr/share/help/ca/cheese
/usr/share/help/ca/cheese/burst-mode.page
/usr/share/help/ca/cheese/effects-apply.page
/usr/share/help/ca/cheese/figures
/usr/share/help/ca/cheese/index.page
/usr/share/help/ca/cheese/introduction.page
/usr/share/help/ca/cheese/legal.xml
/usr/share/help/ca/cheese/photo-delete.page
/usr/share/help/ca/cheese/photo-save.page
/usr/share/help/ca/cheese/photo-take.page
/usr/share/help/ca/cheese/photo-view.page
/usr/share/help/ca/cheese/pref-countdown.page
/usr/share/help/ca/cheese/pref-flash.page
/usr/share/help/ca/cheese/pref-fullscreen.page
/usr/share/help/ca/cheese/pref-image-properties.page
/usr/share/help/ca/cheese/pref-resolution.page
/usr/share/help/ca/cheese/video-record.page
/usr/share/help/ca/cheese/figures/cheese-delete.png
/usr/share/help/ca/cheese/figures/cheese-effects.png
/usr/share/help/ca/cheese/figures/cheese-introduction.png
/usr/share/help/ca/cheese/figures/cheese-record.png
/usr/share/help/ca/cheese/figures/cheese-save.png
/usr/share/help/ca/cheese/figures/cheese-take.png
/usr/share/help/ca/cheese/figures/cheese.png
/usr/share/help/ca/cheese/figures/effects.png
/usr/share/help/ca/cheese/figures/image-properties.png
/usr/share/help/ca/cheese/figures/settings.png
/usr/share/help/cs/cheese
/usr/share/help/cs/cheese/burst-mode.page
/usr/share/help/cs/cheese/effects-apply.page
/usr/share/help/cs/cheese/figures
/usr/share/help/cs/cheese/index.page
/usr/share/help/cs/cheese/introduction.page
/usr/share/help/cs/cheese/legal.xml
/usr/share/help/cs/cheese/photo-delete.page
/usr/share/help/cs/cheese/photo-save.page
/usr/share/help/cs/cheese/photo-take.page
/usr/share/help/cs/cheese/photo-view.page
/usr/share/help/cs/cheese/pref-countdown.page
/usr/share/help/cs/cheese/pref-flash.page
/usr/share/help/cs/cheese/pref-fullscreen.page
/usr/share/help/cs/cheese/pref-image-properties.page
/usr/share/help/cs/cheese/pref-resolution.page
/usr/share/help/cs/cheese/video-record.page
/usr/share/help/cs/cheese/figures/cheese-delete.png
/usr/share/help/cs/cheese/figures/cheese-effects.png
/usr/share/help/cs/cheese/figures/cheese-introduction.png
/usr/share/help/cs/cheese/figures/cheese-record.png
/usr/share/help/cs/cheese/figures/cheese-save.png
/usr/share/help/cs/cheese/figures/cheese-take.png
/usr/share/help/cs/cheese/figures/cheese.png
/usr/share/help/cs/cheese/figures/effects.png
/usr/share/help/cs/cheese/figures/image-properties.png
/usr/share/help/cs/cheese/figures/settings.png
/usr/share/help/de/cheese
/usr/share/help/de/cheese/burst-mode.page
/usr/share/help/de/cheese/effects-apply.page
/usr/share/help/de/cheese/figures
/usr/share/help/de/cheese/index.page
/usr/share/help/de/cheese/introduction.page
/usr/share/help/de/cheese/legal.xml
/usr/share/help/de/cheese/photo-delete.page
/usr/share/help/de/cheese/photo-save.page
/usr/share/help/de/cheese/photo-take.page
/usr/share/help/de/cheese/photo-view.page
/usr/share/help/de/cheese/pref-countdown.page
/usr/share/help/de/cheese/pref-flash.page
/usr/share/help/de/cheese/pref-fullscreen.page
/usr/share/help/de/cheese/pref-image-properties.page
/usr/share/help/de/cheese/pref-resolution.page
/usr/share/help/de/cheese/video-record.page
/usr/share/help/de/cheese/figures/cheese-delete.png
/usr/share/help/de/cheese/figures/cheese-effects.png
/usr/share/help/de/cheese/figures/cheese-introduction.png
/usr/share/help/de/cheese/figures/cheese-record.png
/usr/share/help/de/cheese/figures/cheese-save.png
/usr/share/help/de/cheese/figures/cheese-take.png
/usr/share/help/de/cheese/figures/cheese.png
/usr/share/help/de/cheese/figures/effects.png
/usr/share/help/de/cheese/figures/image-properties.png
/usr/share/help/de/cheese/figures/settings.png
/usr/share/help/el/cheese
/usr/share/help/el/cheese/burst-mode.page
/usr/share/help/el/cheese/effects-apply.page
/usr/share/help/el/cheese/figures
/usr/share/help/el/cheese/index.page
/usr/share/help/el/cheese/introduction.page
/usr/share/help/el/cheese/legal.xml
/usr/share/help/el/cheese/photo-delete.page
/usr/share/help/el/cheese/photo-save.page
/usr/share/help/el/cheese/photo-take.page
/usr/share/help/el/cheese/photo-view.page
/usr/share/help/el/cheese/pref-countdown.page
/usr/share/help/el/cheese/pref-flash.page
/usr/share/help/el/cheese/pref-fullscreen.page
/usr/share/help/el/cheese/pref-image-properties.page
/usr/share/help/el/cheese/pref-resolution.page
/usr/share/help/el/cheese/video-record.page
/usr/share/help/el/cheese/figures/cheese-delete.png
/usr/share/help/el/cheese/figures/cheese-effects.png
/usr/share/help/el/cheese/figures/cheese-introduction.png
/usr/share/help/el/cheese/figures/cheese-record.png
/usr/share/help/el/cheese/figures/cheese-save.png
/usr/share/help/el/cheese/figures/cheese-take.png
/usr/share/help/el/cheese/figures/cheese.png
/usr/share/help/el/cheese/figures/effects.png
/usr/share/help/el/cheese/figures/image-properties.png
/usr/share/help/el/cheese/figures/settings.png
/usr/share/help/es/cheese
/usr/share/help/es/cheese/burst-mode.page
/usr/share/help/es/cheese/effects-apply.page
/usr/share/help/es/cheese/figures
/usr/share/help/es/cheese/index.page
/usr/share/help/es/cheese/introduction.page
/usr/share/help/es/cheese/legal.xml
/usr/share/help/es/cheese/photo-delete.page
/usr/share/help/es/cheese/photo-save.page
/usr/share/help/es/cheese/photo-take.page
/usr/share/help/es/cheese/photo-view.page
/usr/share/help/es/cheese/pref-countdown.page
/usr/share/help/es/cheese/pref-flash.page
/usr/share/help/es/cheese/pref-fullscreen.page
/usr/share/help/es/cheese/pref-image-properties.page
/usr/share/help/es/cheese/pref-resolution.page
/usr/share/help/es/cheese/video-record.page
/usr/share/help/es/cheese/figures/cheese-delete.png
/usr/share/help/es/cheese/figures/cheese-effects.png
/usr/share/help/es/cheese/figures/cheese-introduction.png
/usr/share/help/es/cheese/figures/cheese-record.png
/usr/share/help/es/cheese/figures/cheese-save.png
/usr/share/help/es/cheese/figures/cheese-take.png
/usr/share/help/es/cheese/figures/cheese.png
/usr/share/help/es/cheese/figures/effects.png
/usr/share/help/es/cheese/figures/image-properties.png
/usr/share/help/es/cheese/figures/settings.png
/usr/share/help/fi/cheese
/usr/share/help/fi/cheese/burst-mode.page
/usr/share/help/fi/cheese/effects-apply.page
/usr/share/help/fi/cheese/figures
/usr/share/help/fi/cheese/index.page
/usr/share/help/fi/cheese/introduction.page
/usr/share/help/fi/cheese/legal.xml
/usr/share/help/fi/cheese/photo-delete.page
/usr/share/help/fi/cheese/photo-save.page
/usr/share/help/fi/cheese/photo-take.page
/usr/share/help/fi/cheese/photo-view.page
/usr/share/help/fi/cheese/pref-countdown.page
/usr/share/help/fi/cheese/pref-flash.page
/usr/share/help/fi/cheese/pref-fullscreen.page
/usr/share/help/fi/cheese/pref-image-properties.page
/usr/share/help/fi/cheese/pref-resolution.page
/usr/share/help/fi/cheese/video-record.page
/usr/share/help/fi/cheese/figures/cheese-delete.png
/usr/share/help/fi/cheese/figures/cheese-effects.png
/usr/share/help/fi/cheese/figures/cheese-introduction.png
/usr/share/help/fi/cheese/figures/cheese-record.png
/usr/share/help/fi/cheese/figures/cheese-save.png
/usr/share/help/fi/cheese/figures/cheese-take.png
/usr/share/help/fi/cheese/figures/cheese.png
/usr/share/help/fi/cheese/figures/effects.png
/usr/share/help/fi/cheese/figures/image-properties.png
/usr/share/help/fi/cheese/figures/settings.png
/usr/share/help/fr/cheese
/usr/share/help/fr/cheese/burst-mode.page
/usr/share/help/fr/cheese/effects-apply.page
/usr/share/help/fr/cheese/figures
/usr/share/help/fr/cheese/index.page
/usr/share/help/fr/cheese/introduction.page
/usr/share/help/fr/cheese/legal.xml
/usr/share/help/fr/cheese/photo-delete.page
/usr/share/help/fr/cheese/photo-save.page
/usr/share/help/fr/cheese/photo-take.page
/usr/share/help/fr/cheese/photo-view.page
/usr/share/help/fr/cheese/pref-countdown.page
/usr/share/help/fr/cheese/pref-flash.page
/usr/share/help/fr/cheese/pref-fullscreen.page
/usr/share/help/fr/cheese/pref-image-properties.page
/usr/share/help/fr/cheese/pref-resolution.page
/usr/share/help/fr/cheese/video-record.page
/usr/share/help/fr/cheese/figures/cheese-delete.png
/usr/share/help/fr/cheese/figures/cheese-effects.png
/usr/share/help/fr/cheese/figures/cheese-introduction.png
/usr/share/help/fr/cheese/figures/cheese-record.png
/usr/share/help/fr/cheese/figures/cheese-save.png
/usr/share/help/fr/cheese/figures/cheese-take.png
/usr/share/help/fr/cheese/figures/cheese.png
/usr/share/help/fr/cheese/figures/effects.png
/usr/share/help/fr/cheese/figures/image-properties.png
/usr/share/help/fr/cheese/figures/settings.png
/usr/share/help/gl/cheese
/usr/share/help/gl/cheese/burst-mode.page
/usr/share/help/gl/cheese/effects-apply.page
/usr/share/help/gl/cheese/figures
/usr/share/help/gl/cheese/index.page
/usr/share/help/gl/cheese/introduction.page
/usr/share/help/gl/cheese/legal.xml
/usr/share/help/gl/cheese/photo-delete.page
/usr/share/help/gl/cheese/photo-save.page
/usr/share/help/gl/cheese/photo-take.page
/usr/share/help/gl/cheese/photo-view.page
/usr/share/help/gl/cheese/pref-countdown.page
/usr/share/help/gl/cheese/pref-flash.page
/usr/share/help/gl/cheese/pref-fullscreen.page
/usr/share/help/gl/cheese/pref-image-properties.page
/usr/share/help/gl/cheese/pref-resolution.page
/usr/share/help/gl/cheese/video-record.page
/usr/share/help/gl/cheese/figures/cheese-delete.png
/usr/share/help/gl/cheese/figures/cheese-effects.png
/usr/share/help/gl/cheese/figures/cheese-introduction.png
/usr/share/help/gl/cheese/figures/cheese-record.png
/usr/share/help/gl/cheese/figures/cheese-save.png
/usr/share/help/gl/cheese/figures/cheese-take.png
/usr/share/help/gl/cheese/figures/cheese.png
/usr/share/help/gl/cheese/figures/effects.png
/usr/share/help/gl/cheese/figures/image-properties.png
/usr/share/help/gl/cheese/figures/settings.png
/usr/share/help/hu/cheese
/usr/share/help/hu/cheese/burst-mode.page
/usr/share/help/hu/cheese/effects-apply.page
/usr/share/help/hu/cheese/figures
/usr/share/help/hu/cheese/index.page
/usr/share/help/hu/cheese/introduction.page
/usr/share/help/hu/cheese/legal.xml
/usr/share/help/hu/cheese/photo-delete.page
/usr/share/help/hu/cheese/photo-save.page
/usr/share/help/hu/cheese/photo-take.page
/usr/share/help/hu/cheese/photo-view.page
/usr/share/help/hu/cheese/pref-countdown.page
/usr/share/help/hu/cheese/pref-flash.page
/usr/share/help/hu/cheese/pref-fullscreen.page
/usr/share/help/hu/cheese/pref-image-properties.page
/usr/share/help/hu/cheese/pref-resolution.page
/usr/share/help/hu/cheese/video-record.page
/usr/share/help/hu/cheese/figures/cheese-delete.png
/usr/share/help/hu/cheese/figures/cheese-effects.png
/usr/share/help/hu/cheese/figures/cheese-introduction.png
/usr/share/help/hu/cheese/figures/cheese-record.png
/usr/share/help/hu/cheese/figures/cheese-save.png
/usr/share/help/hu/cheese/figures/cheese-take.png
/usr/share/help/hu/cheese/figures/cheese.png
/usr/share/help/hu/cheese/figures/effects.png
/usr/share/help/hu/cheese/figures/image-properties.png
/usr/share/help/hu/cheese/figures/settings.png
/usr/share/help/id/cheese
/usr/share/help/id/cheese/burst-mode.page
/usr/share/help/id/cheese/effects-apply.page
/usr/share/help/id/cheese/figures
/usr/share/help/id/cheese/index.page
/usr/share/help/id/cheese/introduction.page
/usr/share/help/id/cheese/legal.xml
/usr/share/help/id/cheese/photo-delete.page
/usr/share/help/id/cheese/photo-save.page
/usr/share/help/id/cheese/photo-take.page
/usr/share/help/id/cheese/photo-view.page
/usr/share/help/id/cheese/pref-countdown.page
/usr/share/help/id/cheese/pref-flash.page
/usr/share/help/id/cheese/pref-fullscreen.page
/usr/share/help/id/cheese/pref-image-properties.page
/usr/share/help/id/cheese/pref-resolution.page
/usr/share/help/id/cheese/video-record.page
/usr/share/help/id/cheese/figures/cheese-delete.png
/usr/share/help/id/cheese/figures/cheese-effects.png
/usr/share/help/id/cheese/figures/cheese-introduction.png
/usr/share/help/id/cheese/figures/cheese-record.png
/usr/share/help/id/cheese/figures/cheese-save.png
/usr/share/help/id/cheese/figures/cheese-take.png
/usr/share/help/id/cheese/figures/cheese.png
/usr/share/help/id/cheese/figures/effects.png
/usr/share/help/id/cheese/figures/image-properties.png
/usr/share/help/id/cheese/figures/settings.png
/usr/share/help/ko/cheese
/usr/share/help/ko/cheese/burst-mode.page
/usr/share/help/ko/cheese/effects-apply.page
/usr/share/help/ko/cheese/figures
/usr/share/help/ko/cheese/index.page
/usr/share/help/ko/cheese/introduction.page
/usr/share/help/ko/cheese/legal.xml
/usr/share/help/ko/cheese/photo-delete.page
/usr/share/help/ko/cheese/photo-save.page
/usr/share/help/ko/cheese/photo-take.page
/usr/share/help/ko/cheese/photo-view.page
/usr/share/help/ko/cheese/pref-countdown.page
/usr/share/help/ko/cheese/pref-flash.page
/usr/share/help/ko/cheese/pref-fullscreen.page
/usr/share/help/ko/cheese/pref-image-properties.page
/usr/share/help/ko/cheese/pref-resolution.page
/usr/share/help/ko/cheese/video-record.page
/usr/share/help/ko/cheese/figures/cheese-delete.png
/usr/share/help/ko/cheese/figures/cheese-effects.png
/usr/share/help/ko/cheese/figures/cheese-introduction.png
/usr/share/help/ko/cheese/figures/cheese-record.png
/usr/share/help/ko/cheese/figures/cheese-save.png
/usr/share/help/ko/cheese/figures/cheese-take.png
/usr/share/help/ko/cheese/figures/cheese.png
/usr/share/help/ko/cheese/figures/effects.png
/usr/share/help/ko/cheese/figures/image-properties.png
/usr/share/help/ko/cheese/figures/settings.png
/usr/share/help/pt_BR/cheese
/usr/share/help/pt_BR/cheese/burst-mode.page
/usr/share/help/pt_BR/cheese/effects-apply.page
/usr/share/help/pt_BR/cheese/figures
/usr/share/help/pt_BR/cheese/index.page
/usr/share/help/pt_BR/cheese/introduction.page
/usr/share/help/pt_BR/cheese/legal.xml
/usr/share/help/pt_BR/cheese/photo-delete.page
/usr/share/help/pt_BR/cheese/photo-save.page
/usr/share/help/pt_BR/cheese/photo-take.page
/usr/share/help/pt_BR/cheese/photo-view.page
/usr/share/help/pt_BR/cheese/pref-countdown.page
/usr/share/help/pt_BR/cheese/pref-flash.page
/usr/share/help/pt_BR/cheese/pref-fullscreen.page
/usr/share/help/pt_BR/cheese/pref-image-properties.page
/usr/share/help/pt_BR/cheese/pref-resolution.page
/usr/share/help/pt_BR/cheese/video-record.page
/usr/share/help/pt_BR/cheese/figures/cheese-delete.png
/usr/share/help/pt_BR/cheese/figures/cheese-effects.png
/usr/share/help/pt_BR/cheese/figures/cheese-introduction.png
/usr/share/help/pt_BR/cheese/figures/cheese-record.png
/usr/share/help/pt_BR/cheese/figures/cheese-save.png
/usr/share/help/pt_BR/cheese/figures/cheese-take.png
/usr/share/help/pt_BR/cheese/figures/cheese.png
/usr/share/help/pt_BR/cheese/figures/effects.png
/usr/share/help/pt_BR/cheese/figures/image-properties.png
/usr/share/help/pt_BR/cheese/figures/settings.png
/usr/share/help/ru/cheese
/usr/share/help/ru/cheese/burst-mode.page
/usr/share/help/ru/cheese/effects-apply.page
/usr/share/help/ru/cheese/figures
/usr/share/help/ru/cheese/index.page
/usr/share/help/ru/cheese/introduction.page
/usr/share/help/ru/cheese/legal.xml
/usr/share/help/ru/cheese/photo-delete.page
/usr/share/help/ru/cheese/photo-save.page
/usr/share/help/ru/cheese/photo-take.page
/usr/share/help/ru/cheese/photo-view.page
/usr/share/help/ru/cheese/pref-countdown.page
/usr/share/help/ru/cheese/pref-flash.page
/usr/share/help/ru/cheese/pref-fullscreen.page
/usr/share/help/ru/cheese/pref-image-properties.page
/usr/share/help/ru/cheese/pref-resolution.page
/usr/share/help/ru/cheese/video-record.page
/usr/share/help/ru/cheese/figures/cheese-delete.png
/usr/share/help/ru/cheese/figures/cheese-effects.png
/usr/share/help/ru/cheese/figures/cheese-introduction.png
/usr/share/help/ru/cheese/figures/cheese-record.png
/usr/share/help/ru/cheese/figures/cheese-save.png
/usr/share/help/ru/cheese/figures/cheese-take.png
/usr/share/help/ru/cheese/figures/cheese.png
/usr/share/help/ru/cheese/figures/effects.png
/usr/share/help/ru/cheese/figures/image-properties.png
/usr/share/help/ru/cheese/figures/settings.png
/usr/share/help/sl/cheese
/usr/share/help/sl/cheese/burst-mode.page
/usr/share/help/sl/cheese/effects-apply.page
/usr/share/help/sl/cheese/figures
/usr/share/help/sl/cheese/index.page
/usr/share/help/sl/cheese/introduction.page
/usr/share/help/sl/cheese/legal.xml
/usr/share/help/sl/cheese/photo-delete.page
/usr/share/help/sl/cheese/photo-save.page
/usr/share/help/sl/cheese/photo-take.page
/usr/share/help/sl/cheese/photo-view.page
/usr/share/help/sl/cheese/pref-countdown.page
/usr/share/help/sl/cheese/pref-flash.page
/usr/share/help/sl/cheese/pref-fullscreen.page
/usr/share/help/sl/cheese/pref-image-properties.page
/usr/share/help/sl/cheese/pref-resolution.page
/usr/share/help/sl/cheese/video-record.page
/usr/share/help/sl/cheese/figures/cheese-delete.png
/usr/share/help/sl/cheese/figures/cheese-effects.png
/usr/share/help/sl/cheese/figures/cheese-introduction.png
/usr/share/help/sl/cheese/figures/cheese-record.png
/usr/share/help/sl/cheese/figures/cheese-save.png
/usr/share/help/sl/cheese/figures/cheese-take.png
/usr/share/help/sl/cheese/figures/cheese.png
/usr/share/help/sl/cheese/figures/effects.png
/usr/share/help/sl/cheese/figures/image-properties.png
/usr/share/help/sl/cheese/figures/settings.png
/usr/share/help/zh_CN/cheese
/usr/share/help/zh_CN/cheese/burst-mode.page
/usr/share/help/zh_CN/cheese/effects-apply.page
/usr/share/help/zh_CN/cheese/figures
/usr/share/help/zh_CN/cheese/index.page
/usr/share/help/zh_CN/cheese/introduction.page
/usr/share/help/zh_CN/cheese/legal.xml
/usr/share/help/zh_CN/cheese/photo-delete.page
/usr/share/help/zh_CN/cheese/photo-save.page
/usr/share/help/zh_CN/cheese/photo-take.page
/usr/share/help/zh_CN/cheese/photo-view.page
/usr/share/help/zh_CN/cheese/pref-countdown.page
/usr/share/help/zh_CN/cheese/pref-flash.page
/usr/share/help/zh_CN/cheese/pref-fullscreen.page
/usr/share/help/zh_CN/cheese/pref-image-properties.page
/usr/share/help/zh_CN/cheese/pref-resolution.page
/usr/share/help/zh_CN/cheese/video-record.page
/usr/share/help/zh_CN/cheese/figures/cheese-delete.png
/usr/share/help/zh_CN/cheese/figures/cheese-effects.png
/usr/share/help/zh_CN/cheese/figures/cheese-introduction.png
/usr/share/help/zh_CN/cheese/figures/cheese-record.png
/usr/share/help/zh_CN/cheese/figures/cheese-save.png
/usr/share/help/zh_CN/cheese/figures/cheese-take.png
/usr/share/help/zh_CN/cheese/figures/cheese.png
/usr/share/help/zh_CN/cheese/figures/effects.png
/usr/share/help/zh_CN/cheese/figures/image-properties.png
/usr/share/help/zh_CN/cheese/figures/settings.png
/usr/share/help-langpack/en_AU/ubuntu-help/app-cheese.page
/usr/share/help-langpack/en_CA/ubuntu-help/app-cheese.page
/usr/share/help-langpack/en_GB/ubuntu-help/app-cheese.page
/usr/share/icons/HighContrast/16x16/apps/cheese.png
/usr/share/icons/HighContrast/22x22/apps/cheese.png
/usr/share/icons/HighContrast/24x24/apps/cheese.png
/usr/share/icons/HighContrast/256x256/apps/cheese.png
/usr/share/icons/HighContrast/32x32/apps/cheese.png
/usr/share/icons/HighContrast/48x48/apps/cheese.png
/usr/share/icons/Mint-X/apps/16/cheese.png
/usr/share/icons/Mint-X/apps/22/cheese.png
/usr/share/icons/Mint-X/apps/24/cheese.png
/usr/share/icons/Mint-X/apps/32/cheese.png
/usr/share/icons/Mint-X/apps/48/cheese.png
/usr/share/icons/Mint-X/apps/96/cheese.svg
/usr/share/icons/Mint-Y/apps/16/cheese.png
/usr/share/icons/Mint-Y/apps/22/cheese.png
/usr/share/icons/Mint-Y/apps/24/cheese.png
/usr/share/icons/Mint-Y/apps/256/cheese.png
/usr/share/icons/Mint-Y/apps/32/cheese.png
/usr/share/icons/Mint-Y/apps/48/cheese.png
/usr/share/icons/Mint-Y/apps/64/cheese.png
/usr/share/icons/Mint-Y/apps/96/cheese.png
/usr/share/icons/hicolor/16x16/apps/cheese.png
/usr/share/icons/hicolor/22x22/apps/cheese.png
/usr/share/icons/hicolor/24x24/apps/cheese.png
/usr/share/icons/hicolor/256x256/apps/cheese.png
/usr/share/icons/hicolor/32x32/apps/cheese.png
/usr/share/icons/hicolor/48x48/apps/cheese.png
/usr/share/icons/hicolor/symbolic/apps/cheese-symbolic.svg
/usr/share/locale-langpack/en@shaw/LC_MESSAGES/cheese.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/cheese.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/cheese.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/cheese.mo
/usr/share/man/man1/cheese.1.gz
/var/lib/dpkg/info/cheese-common.list
/var/lib/dpkg/info/cheese-common.md5sums
/var/lib/dpkg/info/cheese.list
/var/lib/dpkg/info/cheese.md5sums
/var/lib/dpkg/info/libcheese-gtk25:i386.list
/var/lib/dpkg/info/libcheese-gtk25:i386.md5sums
/var/lib/dpkg/info/libcheese-gtk25:i386.shlibs
/var/lib/dpkg/info/libcheese-gtk25:i386.symbols
/var/lib/dpkg/info/libcheese-gtk25:i386.triggers
/var/lib/dpkg/info/libcheese8:i386.list
/var/lib/dpkg/info/libcheese8:i386.md5sums
/var/lib/dpkg/info/libcheese8:i386.shlibs
/var/lib/dpkg/info/libcheese8:i386.symbols
/var/lib/dpkg/info/libcheese8:i386.triggers

---

