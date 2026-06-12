---
title: "empathy adium themes"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FraggedLocust on 2009-07-23
I had sworn I saw adium themes available for choosing on my other upgrade to karmic alpha 2. It seems that the alpha 3 version does not have the option in the dropdown box. Is this a bug or a problem with my install?

It has options for: Blue, Classic, Clean, and Simple. I for sure had seen Adium themes at one point, because I clicked it, which brought up a dialogue asking me for a theme.

---

### Post by Joe_Bishop on 2009-07-24
Now you should put your themes into ~/.local/share/adium/message-styles/, and they will be available through the common menu, as default themes are.

---

### Post by aamukahvi on 2009-07-24
You need to put the themes under your home (my memory fails me as to which folder exactly, probably ~/.empathy/themes/something). After that the new theme should be listed in the dropdown.

---

### Post by Staz on 2009-07-24
> **FraggedLocust said:**
> I had sworn I saw adium themes available for choosing on my other upgrade to karmic alpha 2. It seems that the alpha 3 version does not have the option in the dropdown box. Is this a bug or a problem with my install?

It has options for: Blue, Classic, Clean, and Simple. I for sure had seen Adium themes at one point, because I clicked it, which brought up a dialogue asking me for a theme.
The themes support is still here, the interface for selecting themes just have changed a bit.You need to put the theme in ~/.local/share/adium/message-styles/*.AdiumMessageStyle and it will be listed with the others themes.
See [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

---

### Post by keypox on 2009-08-02
> **Staz said:**
> The themes support is still here, the interface for selecting themes just have changed a bit.You need to put the theme in ~/.local/share/adium/message-styles/*.AdiumMessageStyle and it will be listed with the others themes.
See [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

there is no adium file in the share dir...

---

### Post by aamukahvi on 2009-08-02
> **keypox said:**
> there is no adium file in the share dir...

```
mkdir adium
```

---

### Post by kevindontenville on 2009-08-06
Joining in on the thread, in Jaunty, after making the directory structure as stated and adding themes, nothing shows up in Empathy under themes. Same 4 options, no adium option.

Cant seem to find much documentation on the themes other than the one mentioned above. Has something recently changed does anyone know?

---

### Post by keypox on 2009-08-06
> **aamukahvi said:**
> ```
mkdir adium
```

lol yeah that would fix that problem.  But i thought that it would already have the existing themes... anyone get themes to work?

Also it worked for me. Atleast i see the new themes thanks guys :)

---

### Post by Cuba71 on 2009-08-11
I'm running Empathy 2.27.90 and the instructions above work great.

---

### Post by Staz on 2009-08-11
> **keypox said:**
> lol yeah that would fix that problem.  But i thought that it would already have the existing themes... anyone get themes to work?

The default theme are in a system folder.

Theme works on my computer, I use renkoo which is quite elegant.

---

### Post by Numer0bis on 2009-08-16
> **kevindontenville said:**
> Joining in on the thread, in Jaunty, after making the directory structure as stated and adding themes, nothing shows up in Empathy under themes. Same 4 options, no adium option.

Cant seem to find much documentation on the themes other than the one mentioned above. Has something recently changed does anyone know?

I am experiencing the same issue. created the corresponding folder :

```
~/.local/share/adium/messages-style/
```

and I have installed those 3 themes:

Adium Matte.AdiumMessageStyle
renkoo.AdiumMessageStyle
renkooNaked.AdiumMessageStyle

However none of them show up in the theme selection menu :confused::confused:.

thanks for any help in advance

---

### Post by B Crowther on 2009-09-05
> **Numer0bis said:**
> I am experiencing the same issue. created the corresponding folder :

```
~/.local/share/adium/messages-style/
```

and I have installed those 3 themes:

Adium Matte.AdiumMessageStyle
renkoo.AdiumMessageStyle
renkooNaked.AdiumMessageStyle

However none of them show up in the theme selection menu :confused::confused:.

thanks for any help in advance

Yup, I have the same problem with Jaunty, even after this morning's latest upgrades, the Adium doesn't show on the themes.

But, this has worked for me:

Go to Applications>System Tools>Configuration Editor>apps>empathy>conversation

You should see the pathway to your Adium themes in there, if not right click on the pane and add a new key: mine is currently Name: adium_path, Value: /home/us/.local/share/adium/message-styles/adium_matte_5_3631_4987/Adium Matte.AdiumMessageStyle

Then change the value for "theme" to adium, and you should have it working again.

Don't open the "Themes" dialog in Preferences, or it will default immediately to one of the stock offerings, and you will have to go back to the Config Editor again!

Good luck, 
Bruce.

---

### Post by antono on 2009-09-22
Little helper script:
[http://antono.info/en/165-install-adium-themes-to-empathy](http://antono.info/en/165-install-adium-themes-to-empathy)

---

### Post by kestal on 2009-09-23
.... because we all know that people really wanna be dragged through burning hoops just to make things look pleasant. O_o.

Empathy has potential. But if it cant fully support adium themes (rather than a select few), it should have a different way to get/create proper themes in place. I'd gladly contribute regularly.

---

### Post by giacomo.c on 2009-09-27
From the empathy FAQ "Note that you will need Empathy 2.27.3 compiled with webkit support for Adium Themes to work."

9.04 seems to only have 2.26.1

sooo, I guess you can either change the themes the hard way, as posted above, or you can grab the source from live.gnome.org/empathy and try to figure that out.

edit:
actually you can add the Repo from [http://live.gnome.org/Empathy/Install](http://live.gnome.org/Empathy/Install) and just apt-get that ****.

---

### Post by Sand &amp; Mercury on 2009-09-28
What!? Empathy supports themes!?!?!?! OMG. <3.

---

### Post by oraerk on 2009-10-21
Antono's script does not work when there are spaces in names, i've rewritten the script, and written a small howto here:

[http://ubuntuforums.org/showthread.php?t=1297237](http://ubuntuforums.org/showthread.php?t=1297237)

---

