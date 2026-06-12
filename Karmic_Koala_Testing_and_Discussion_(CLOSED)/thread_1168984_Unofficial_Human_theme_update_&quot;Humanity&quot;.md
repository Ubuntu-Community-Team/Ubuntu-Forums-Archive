---
title: "Unofficial Human theme update: &quot;Humanity&quot;"
date: 2009-05-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by psyke83 on 2009-05-24
[COLOR="Blue"]**Update (03/Oct/09):** The Humanity theme has now reached version 1.0! The theme consists of a GTK (buttons and widgets) theme, and three Metacity window border themes (Glow, Glass and Smooth - see attached screenshots). 

Please note: the Humanity GTK theme will be identical to the final Human GTK theme, which is the default theme used by Ubuntu. However, the updated Metacity window borders may not be included in the default Human theme, due to time constraints and the [Beta Freeze]("https://wiki.ubuntu.com/BetaFreeze"). I have submitted a proposal to Canonical to make a freeze exception, but of course, there is no guarantee that they will be accepted.[/COLOR]

Hi,

Since I began work on Human-Murrine-Mod (which later became the official Human-Murrine, and finally Human theme), I felt somewhat limited by the Murrine engine's features. However, more recent versions of the Murrine engine have brought new features and opportunities, and have allowed me to get closer to my original vision for this theme.

Providing no bugs or problems are discovered, this should be considered the final version. Enjoy, and any feedback is appreciated!

Note: Although I have contacted Kenneth Wimer (Ubuntu's art lead) to inform him of this update, I have no idea if he'll be interested in considering it for Karmic as an update for the official theme. Therefore, I have provisionally renamed this theme "Humanity". 

[COLOR="Blue"]To install: Open GNOME's Appearance Preferences and click the Install button.[/COLOR]
[COLOR="Red"]Warning: This will install the theme into the user's account only, which means that applications with root privileges will not be themed correctly. This is not a bug - if you wish all applications to be themed, move the Humanity* folders from the ~/.themes folder to the /usr/share/themes folder, like so:
```
$ sudo mv ~/.themes/Humanity* /usr/share/themes/
```[/COLOR]
[SIZE="1"]**Bugs (affecting theme, not caused by theme):**
[LIST]
[*][problem with new scrollbar in Human theme - GtkRange::trough-border set to 2 (LP #422511)]("https://bugs.launchpad.net/bugs/422511")
[*]FIXED (in Humanity icons): [Various icons don't have a 16x16 icon size (LP #84931)]("https://bugs.launchpad.net/bugs/84931")
[*][Non-zero GtkRange::trough-border value produces strange boxes in Firefox (LP #327863)]("https://bugs.launchpad.net/libgtk/+bug/327863")
[*]FIXED: [Notification area of gnome-panel derives application icon size from theme's gtk-icon-sizes -> gtk-button definition incorrectly (LP #400371)]("https://bugs.launchpad.net/bugs/400371")
[/LIST][/SIZE][SIZE="1"]**Changelog**
v0.2 24/05/09 - First public release
v0.3 26/05/09 - Reversed & tweaked tab gradient
v0.4 26/05/09 - Adjusted tab gradient
v0.5 27/05/09 - Reduced scrollbar's trough border to 2
v0.6 30/05/09 - Tweaked tab gradient
v0.7 04/06/09 - Reversed tab gradient (again)
v0.8 24/06/09 - Final tweaks to tab gradient before official release
v0.9 12/07/09 - Small bugfix to notebook theming, button size set to 16x16 - equivalent to human-theme 0.29ubuntu1.
v1.0 03/10/09 - Major update with new colour scheme, including updated Metacity window border designs. Humanity GTK theme will eventually be used as the default Human GTK theme, but Metacity updates may not.
v1.1 15/10/09 - Fix inactive text selection colour, improved widget outline lighting.
v1.2 16/10/09 - Re-add Metacity themes, reduce Metacity border size & set default Metacity theme to Humanity-Smooth.[/SIZE]

---

### Post by Didius Falco on 2009-05-24
I like it! :KS  Thanks for sharing.

Regards,

Didius

---

### Post by rudenko_ruslan on 2009-05-24
Yeah, I like it too. Thanks psyke83 :)

---

### Post by vaibhav on 2009-05-24
Cool :) I like it!

---

### Post by Bou on 2009-05-25
Hi Psyke,

It's definitely a great theme. After using it for a while, I thins there are only two things where it can be improved:

-The selected tab looks a little too light, almost white. Could it be a bit darker?
-The scrollbars look really good, but its current looks make it difficult to guess where the button ends and where the bar starts. Is there any way to fix that?

---

### Post by psyke83 on 2009-05-25
> **Bou said:**
> Hi Psyke,

It's definitely a great theme. After using it for a while, I thins there are only two things where it can be improved:

-The selected tab looks a little too light, almost white. Could it be a bit darker?
-The scrollbars look really good, but its current looks make it difficult to guess where the button ends and where the bar starts. Is there any way to fix that?

I wanted the selected tab to stand out slightly, but I agree that perhaps it's a little too light at the moment. The problem is that when you darken the gradient for the selected tab, the unselected tabs are also affected, which causes their gradient to become a flat grey (similar to the current Human). I'll tweak this a little more later tonight and see if I can find a better compromise.

As for the scrollbar buttons, there are no real options to theme it differently, except to restore the buttons to the same way as in the official Human theme (and most other Murrine themes).

---

### Post by psyke83 on 2009-05-26
> **Bou said:**
> -The selected tab looks a little too light, almost white. Could it be a bit darker?


I lightened the gradient slightly, but it still looked a little too white. Reducing the gradient caused the tabs to look identical to the current Human...

This gave me an idea: what if I reversed the tab gradient, so that it's darker on top and lighter at the bottom? The results are v0.3, which I think is a definite improvement. Judge from real usage, as the screenshot doesn't do it justice.

---

### Post by rudenko_ruslan on 2009-05-26
I like this new tab gradient. Thanks to the author, and keep working on this theme :)

---

### Post by JohnJackson on 2009-05-26
Can the scroll bar be made slightly thinner? Otherwise I like it.

---

### Post by psyke83 on 2009-05-26
> **JohnJackson said:**
> Can the scroll bar be made slightly thinner? Otherwise I like it.

Because this theme has a trough border of 3 on the scrollbars (opposed to no border in the original Human), there are 6 less pixels available that are clickable. This can be a problem, especially if users are somewhat impaired when using a mouse, so I decided to make the scrollbar slightly thicker.

The theme currently uses a scrollbar of 14 pixels and trough border of 3 pixels.

Here's two screenshots:
1. Scrollbar of 14 pixels, trough border 2 pixels.
2. Scrollbar of 13 pixels, trough border 2 pixels.

I prefer the thickness of the first screenshot, but the trough border is less noticeable.

I don't like the second screenshot, as the scrollbar takes a little too much extra effort to click.

Any thoughts are appreciated...

---

### Post by ktp on 2009-05-26
> **psyke83 said:**
> 
Here's two screenshots:
1. Scrollbar of 14 pixels, trough border 2 pixels.
2. Scrollbar of 13 pixels, trough border 2 pixels.

I prefer the thickness of the first screenshot, but the trough border is less noticeable.

I don't like the second screenshot, as the scrollbar takes a little too much extra effort to click.

Any thoughts are appreciated...

My vote would be for "1. Scrollbar of 14 pixels, trough border 2 pixels."

---

### Post by psyke83 on 2009-05-26
> **ktp said:**
> My vote would be for "1. Scrollbar of 14 pixels, trough border 2 pixels."

Alright, I've made the change in v0.5. I don't think it's wise to reduce the size any more than this.

---

### Post by JohnJackson on 2009-05-27
I think that's better...

It's quite a subtle change so it's difficult to tell

Thanks

---

### Post by benjamimgois on 2009-05-28
That's very nice. Canonical should adopt it. Nice work.

---

### Post by benjamimgois on 2009-05-28
Why don't you move it to Gnome-look ? It could gain more visibility....

---

### Post by Gourgi on 2009-05-30
it looks cool!
i'm using it now 
thanks

---

### Post by ktp on 2009-05-30
> **psyke83 said:**
> Alright, I've made the change in v0.5. I don't think it's wise to reduce the size any more than this.

Thanks...are you going to see if changes are going to be merged into the "official" theme?

---

### Post by durand on 2009-05-30
Looks great!

---

### Post by taavikko on 2009-05-31
I'll start by complimenting, nice work.

Then I'll pursue with the rants,
when selecting an item on the menus (Apps -> Places -> System) (NM-Applet). Vertical padding is a bit excessive? Look at the signal strength
Is this (progress.bars) controlled by what rule in gtkrc ?

Icon sizes by default on menu could be a bit smaller
Open system->preferences and almost all vertical space is consumed
I've set them to 16. which gives nice compact menu.
Default is 24?

At least on devices with smaller resolutions, these wastes too much space.

just a few thoughts :)

---

### Post by psyke83 on 2009-05-31
> **taavikko said:**
> I'll start by complimenting, nice work.

Then I'll pursue with the rants,
when selecting an item on the menus (Apps -> Places -> System) (NM-Applet). Vertical padding is a bit excessive? Look at the signal strength
Is this (progress.bars) controlled by what rule in gtkrc ?

Icon sizes by default on menu could be a bit smaller
Open system->preferences and almost all vertical space is consumed
I've set them to 16. which gives nice compact menu.
Default is 24?

At least on devices with smaller resolutions, these wastes too much space.

just a few thoughts :)

The panel-menu size is set to 24 - the same as the original Ubuntulooks Human and Human Murine themes. I'm not changing that, otherwise the Human icons will get scaled (and will therefore look blurry).

Are you on a netbook? I'm not aware if the netbook flavour of Ubuntu uses a modified theme, but I'd be interested to see what it's like - perhaps I can make a netbook version of the theme for devices will smaller resolutions.

---

### Post by taavikko on 2009-05-31
> **psyke83 said:**
> The panel-menu size is set to 24 - the same as the original Ubuntulooks Human and Human Murine themes. I'm not changing that, otherwise the Human icons will get scaled (and will therefore look blurry).

Are you on a netbook? I'm not aware if the netbook flavour of Ubuntu uses a modified theme, but I'd be interested to see what it's like - perhaps I can make a netbook version of the theme for devices will smaller resolutions.

I didn't suggest to set icon size smaller, I just stated that they consume space excessively. At least on 1280x800 resolution. Issue get's worse when running even lower resolution.

Not everyone has FullHD displays...

theme should be somewhat scalable, but that's hard on current available techniques.

This isn't netbook, but I have one, which runned 9.04 alphas Gnome.
and default theme was unbearable. Not an UNR
Specially when menus get cluttered with entries, they need to scrolled down/up.

---

### Post by psyke83 on 2009-05-31
> **taavikko said:**
> I didn't suggest to set icon size smaller, I just stated that they consume space excessively. At least on 1280x800 resolution. Issue get's worse when running even lower resolution.

Not everyone has FullHD displays...

theme should be somewhat scalable, but that's hard on current available techniques.

This isn't netbook, but I have one, which runned 9.04 alphas Gnome.
and default theme was unbearable. Not an UNR
Specially when menus get cluttered with entries, they need to scrolled down/up.

I'm running on a 1024x768 resolution, so I know what you mean. In my opinion, it's an issue with GTK itself, as no theme engines seem capable of producing a compact theme. Humanity is about as compact as possible right now (without sacrificing usability).

If you want smaller icons, edit ~/.themes/Humanity/gtk-2.0/gtkrc, and change this line:

```
gtk-icon-sizes = "panel-menu=24,24"
```

To this:

```
gtk-icon-sizes="gtk-large-toolbar=16,16:panel-menu=16,16:panel=16,16:gtk-button=16,16:gtk-dialog=16,16:gtk-menu=16,16"
```

---

### Post by Starks on 2009-05-31
Psyke, your use of[FONT=monospace][FONT=Verdana] a [/FONT][/FONT]non-zero GtkRange::trough-border is breaking Firefox rendering.

[https://bugzilla.mozilla.org/show_bug.cgi?id=471789](https://bugzilla.mozilla.org/show_bug.cgi?id=471789)

---

### Post by psyke83 on 2009-05-31
> **Starks said:**
> Psyke, your use of[FONT=monospace][FONT=Verdana] a [/FONT][/FONT]non-zero GtkRange::trough-border is breaking Firefox rendering.

[https://bugzilla.mozilla.org/show_bug.cgi?id=471789](https://bugzilla.mozilla.org/show_bug.cgi?id=471789)

Yes, I noticed that but didn't know the bug reference. Thanks.

---

### Post by Vaun on 2009-06-19
psyke83,

Minor hacks to the theme.  I'm convinced a decent scrollbar can't be drawn within the murrine engine itself without being slow.  Pixmap allows for better creativity and design.  Let me know what you think?

Scrolling is also much faster using the pixmap engine. I may have to make the scrollbars a bit lighter due to my dark glassy screen.  I'll test it on a few other computers.

Very preliminary modification.  I am digging this theme a lot, so I will continue to hack on it.

---

### Post by soapytheclown on 2009-06-20
^^ Hey that looks awesome can you tell me what icons you're using aswell please :D

---

### Post by psyke83 on 2009-06-24
> **Vaun said:**
> psyke83,

Minor hacks to the theme.  I'm convinced a decent scrollbar can't be drawn within the murrine engine itself without being slow.  Pixmap allows for better creativity and design.  Let me know what you think?

Scrolling is also much faster using the pixmap engine. I may have to make the scrollbars a bit lighter due to my dark glassy screen.  I'll test it on a few other computers.

Very preliminary modification.  I am digging this theme a lot, so I will continue to hack on it.

Thanks for the hack. Your pixmap scrollbar doesn't seem to match the colour of the @selected_bg_color, so things look a little inconsistent. If you're trying to match the metacity colour, I wouldn't recommend it - the last e-mail I received from Kenneth Wimer indicated that the Human metacity was going to be dropped (though I don't know if that's the plan for Karmic or beyond). Otherwise it's nice.

Having said that, I won't be using pixmaps in this theme, as it is intended as an official update to Human (and the scrollbars may be reverted if Kenneth doesn't like them). You mentioned performance - what's wrong with murrine's scrollbar rendering speed? The pixmap engine is slower and uses more memory.

---

### Post by Vaun on 2009-06-24
Scrolling is slower.  The difference is almost negligible, but enough for more me to notice.  That is good news about the Human metacity as it is not very attractive.  Any help you need please let me know or or if you're going to push into a branch in Launchpad for bug testing, modifications, and such.

---

### Post by psyke83 on 2009-06-24
> **Vaun said:**
> Scrolling is slower.  The difference is almost negligible, but enough for more me to notice.  That is good news about the Human metacity as it is not very attractive.  Any help you need please let me know or or if you're going to push into a branch in Launchpad for bug testing, modifications, and such.

I'm not working directly in any of the bzr branches, but I've sent the updates to Ken. The official Human theme will be updated soon (it will be identical to v0.8 of this theme, and Human-Clearlooks will also have minor fixes to remove the old colour mixing hacks in the code).

I've been assured by Alexander Sack that the [scrollbar bug in Firefox]("https://bugs.launchpad.net/libgtk/+bug/327863") will be escalated (and hopefully fixed before release).

---

### Post by dixon on 2009-06-24
Hi,
I really like your changes to the human theme. I even started using your theme and I've never before used the human theme - I always switched to another after few days of trying to using it. 
But there're still two things, that should be better from my point of view. 

[LIST]
[*]I find UNR theme scroll bar little bit more appealing ( but I also like yours ) [[IMG]http://img395.imageshack.us/img395/9910/hpunroowriter.th.png[/IMG]]("http://img395.imageshack.us/i/hpunroowriter.png/")
[*]I just can't get used to the brown window border - it's better than in original theme, but for me it's still not there yet. The icons, the gtk controls everything is now more orange than brown, just the window border is ugly brown.
[/LIST]
I'm sorry I wish I can give you more productive feedback, but I really suck at design :(

EDIT: I've almost forgotten, some gnome panel theme/background would be awesome...

---

### Post by psyke83 on 2009-06-24
> **dixon said:**
> Hi,
I really like your changes to the human theme. I even started using your theme and I've never before used the human theme - I always switched to another after few days of trying to using it. 
But there're still two things, that should be better from my point of view. 

[LIST]
[*]I find UNR theme scroll bar little bit more appealing ( but I also like yours ) [[IMG]http://img395.imageshack.us/img395/9910/hpunroowriter.th.png[/IMG]]("http://img395.imageshack.us/i/hpunroowriter.png/")
[*]I just can't get used to the brown window border - it's better than in original theme, but for me it's still not there yet. The icons, the gtk controls everything is now more orange than brown, just the window border is ugly brown.
[/LIST]
I'm sorry I wish I can give you more productive feedback, but I really suck at design :(

EDIT: I've almost forgotten, some gnome panel theme/background would be awesome...

The UNR theme is not going to be changed (as least not by myself), so you won't see any changes there. Having a smaller scrollbar (as shown in your screenshot) seems more appropriate for the netbook theme, but not necessarily for the default theme.

The window border (i.e. Metacity theme) is separate from the GTK theme itself, and I wasn't really focusing on it. Besides, I believe that Kenneth is working on a new metacity theme; in fact, he was talking about integrating the Metacity border into the actual application window, so you can click and drag from almost anywhere within windows. I don't know much more about this, though.

I'm also bored of the brown window border, but earlier experiments changing the Human metacity theme to orange gave poor results (it created the impression of the theme being over-exposed).

---

### Post by Vaun on 2009-06-24
Working an idea for a newer metacity.  Let me know what you think.  Not sure of the buttons just yet, but over all the colors seem to integrate very well.  I need to test this overall theme on a few different computers with different screen sizes to see how it renders.

This looks fresh enough from the original Human theme without losing some of it's originality.  Just having some fun.

---

### Post by Bou on 2009-06-25
Psyke, there is one thing I don't quite like in Humanity: If you use its GTK theme and any other metacity theme, the title bar looks nothing like it should. If fact, if I'm not mistaken the current Humanity metacity theme is just Human, tweaked to look as it should.

I'm attaching a screenshot showing gnome-appearance-properties: see how only Humanity looks right, and the others have weird colours. Couldn't you change the GTK theme so that it will look good with other metacity themes?

---

### Post by Bou on 2009-06-25
> **Bou said:**
> I'm attaching a screenshot

Whoops, I forgot to actually attach it.

---

### Post by psyke83 on 2009-06-25
> **Bou said:**
> Psyke, there is one thing I don't quite like in Humanity: If you use its GTK theme and any other metacity theme, the title bar looks nothing like it should. If fact, if I'm not mistaken the current Humanity metacity theme is just Human, tweaked to look as it should.

I'm attaching a screenshot showing gnome-appearance-properties: see how only Humanity looks right, and the others have weird colours. Couldn't you change the GTK theme so that it will look good with other metacity themes?

The version of Human in Jaunty (and Karmic at this moment) is already "tweaked" - unfortunately, this means a lot of hacks in the GTK code, and many inconsistencies occur in applications as a result. 

Have you ever seen the the dark brown elements in the Evolution setup wizard? Have you seen the brown highlight colour around the selected theme in gnome-appearances-properties? Ever noticed that Banshee's coloured widgets look darker than they're supposed to? These are some examples of colouring inconsistencies due to the hacks in the GTK theme to makes the Metacity theme look correct (and they should all have the same colour as @selected_bg_color).

There is a less invasive "hack" that doesn't cause inconsistencies in the majority of applications, but it causes the theme preview to render inaccurately in gnome-appearances-properties and also causes Metacity theme's colours to render incorrectly when compiz is active (as gtk-window-decorator's Metacity emulation is not perfect).

Both workarounds present issues, but tweaking the colours in the Metacity theme itself avoids these other issues. Technically, there is nothing wrong with the preview of themes you see - the Metacity colours are supposed to derive from the theme's @selected_bg_color. Keep in mind that a) the Humanity Metacity will become the Human Metacity in the official update, and b) the Human Metacity theme may be replaced with something else entirely for Karmic.

---

### Post by Vaun on 2009-06-25
Here is what I came up with.  The metacity code needs some clean up, but overall it's working.  The scrollbars are round, dimesnional, with gradient.  The through details are a darker grey with added gradients, which is consistent with the notebook tab shade.  I have another version which uses a darker bg, but this color palette most resembles what Human is.  Let me know what you think?

The steppers need some work with OpenOffice, but this is  fairly typical when using custom pixmap scrollbar for an original look and feel.

---

### Post by moomex on 2009-07-11
Nice work ;) !!

I would change one thing though. The GtkButton size is freaking HUGE. I think it should be smaller.

**[SIZE="4"]Before[/SIZE]**
[IMG]http://yoyo.monash.edu.my/images/humanity-1.png[/IMG]

```
gtk-icon-sizes="panel-menu=24,24:gtk-button=16,16"
```
**[SIZE="4"]After[/SIZE]**
[IMG]http://yoyo.monash.edu.my/images/humanity-2.png[/IMG]

Windows Vista and Leopard have even smaller buttons and I don't hear anybody complaining about their small size or having trouble clicking on them. I hope this gets fixed by default.

---

### Post by rudenko_ruslan on 2009-07-11
+1 for smaller buttons! :)

---

### Post by psyke83 on 2009-07-11
> **moomex said:**
> Nice work ;) !!

I would change one thing though. The GtkButton size is freaking HUGE. I think it should be smaller.

I like it too. I've suggested the change to Kenneth, so we'll see what happens.

---

### Post by taavikko on 2009-07-11
> **psyke83 said:**
> I like it too. I've suggested the change to Kenneth, so we'll see what happens.

> **rudenko_ruslan said:**
> +1 for smaller buttons! :)

> **moomex said:**
> Nice work ;) !!

I would change one thing though. The GtkButton size is freaking HUGE. I think it should be smaller.


Windows Vista and Leopard have even smaller buttons and I don't hear anybody complaining about their small size or having trouble clicking on them. I hope this gets fixed by default.

This would make me happy aswell. tad smaller icons across the board would make it look slicker.

If I remember correctly, I mentioned it to you earlier psyke.

---

### Post by psyke83 on 2009-07-11
> **taavikko said:**
> This would make me happy aswell. tad smaller icons across the board would make it look slicker.

If I remember correctly, I mentioned it to you earlier psyke.

If I recall, you suggested smaller icons on menus. I wouldn't recommend that for the default theme, as it makes the 24px icons completely useless.

---

### Post by taavikko on 2009-07-11
> **psyke83 said:**
> If I recall, you suggested smaller icons on menus. I wouldn't recommend that for the default theme, as it makes the 24px icons completely useless.

then again, I have difficulties in remembering what I ate for breakfast...
But I'll put some blind faith in your words on that one.

Would the icons break if they were .svg?
Since the menus are too cluttered on pretty much stock install...
(I know how to remove/hide the excess cruft) But is this expected on average joe?

just asking...

---

### Post by moomex on 2009-07-11
The scrollbar is just NOT perfect. It could be improved a lot. Colored scrollbar steals attention and create inconsistency to websites when browsing using Firefox and this shouldn't be an option.
I tried to set "colorize_scrollbar" to FALSE in gtkrc file, but this makes the scrollbars almost invisible.

**A really good solution is bringing back the "old" human scrollbar style from ubuntulooks engine.** See the screenshot below:

[IMG]http://yoyo.monash.edu.my/images/humanity-scrollbar.png[/IMG]

---

### Post by psyke83 on 2009-07-11
> **moomex said:**
> The scrollbar is just NOT perfect. It could be improved a lot. Colored scrollbar steals attention and create inconsistency to websites when browsing using Firefox and this shouldn't be an option.
I tried to set "colorize_scrollbar" to FALSE in gtkrc file, but this makes the scrollbars almost invisible.

**A really good solution is bringing back the "old" human scrollbar style from ubuntulooks engine.** See the screenshot below:

This is something you should suggest to Andrea Cimitan (Cimi). The murrine scrollbar options are limited; you can't darken the background of the scrollbar area, for example.

The coloured scrollbar steals attention only because you're not accustomed to it. We also need to test a theme with a trough border >0 to ensure a certain bug is fixed in Firefox:

> <psyke83> asac: re bug #327863, do you think that this issue will get resolved in Karmic without upstream intervention?
<ubottu> Launchpad bug 327863 in murrine-themes "non-zero GtkRange::trough-border value produces strange boxes in Firefox" [Undecided,Invalid] [https://launchpad.net/bugs/327863](https://launchpad.net/bugs/327863)
<asac> psyke83: please dont hide it. I will escalate it
<asac> e.g. dont work around
<asac> if you know a workaround keep that in mind and maybe comment in the bug how that can be done, but hiding that now, will remove the pressure from us fixing it upstream
<psyke83> asac: I'm not going to add any hacks to the gtkrc, don't worry. I think that Ken Wimer may be apprehensive to use the theme update as-is if it exposes this bug...
<psyke83> asac: I would like for the theme to be pushed into the repository as-is, and having the bug exposed will encourage the bugfix to come quicker ;).
<psyke83> if it's not fixed by release, we can push an update to the theme that sets the trough border back to 0 (the current default for the older version of the theme)
<asac> psyke83: yes. thats what i would think is best. i will check with kwwii if you want
<psyke83> asac: I'll send him an excerpt of this log so he's kept informed
<psyke83> thanks for taking a look at this issue, I appreciate it
<asac> psyke83: yeah. ping me in case you have problems getting this theme update in
<psyke83> asac: will do, thanks

---

### Post by psyke83 on 2009-07-11
> **taavikko said:**
> then again, I have difficulties in remembering what I ate for breakfast...
But I'll put some blind faith in your words on that one.

Would the icons break if they were .svg?
Since the menus are too cluttered on pretty much stock install...
(I know how to remove/hide the excess cruft) But is this expected on average joe?

just asking...

I would disagree that the stock menus are cluttered - with exception to System/Preferences.

The icons won't break if they're SVG, but you have to remember that SVG icons scale very badly to low sizes (they become blurry and lose fine details).

There is a reason why most icon themes ship with SVG files *and* static sizes.

---

### Post by moomex on 2009-07-11
> **psyke83 said:**
> This is something you should suggest to Andrea Cimitan (Cimi). The murrine scrollbar options are limited; you can't darken the background of the scrollbar area, for example.

The coloured scrollbar steals attention only because you're not accustomed to it. We also need to test a theme with a trough border >0 to ensure a certain bug is fixed in Firefox:

There are two workarounds to solve this problem without messing with murrine engine. You can use ubuntulooks engine for GtkScrollbar GtkVScrollbar and GtkHScrollbar, and murrine engine for the rest. Or you can draw the scrollbars using pixmap engine.

---

### Post by psyke83 on 2009-07-11
> **moomex said:**
> There are two workarounds to solve this problem without messing with murrine engine. You can use ubuntulooks engine for GtkScrollbar GtkVScrollbar and GtkHScrollbar, and murrine engine for the rest. Or you can draw the scrollbars using pixmap engine.

Using multiple engines is not an option for a default theme - and besides, the ubuntulooks engine is no longer maintained (or installed by default). This is why the Human-Murrine theme was created in the first place.

As for pixmaps, they're not appropriate for a default theme either. Pixmaps increase memory usage and slows down rendering.

I recommend that you submit some suggestions to improve the theming options for the murrine scrollbar in the [appropriate place]("http://www.cimitan.com/murrine/features/overview").

---

### Post by plun on 2009-07-11
Well, "the same procedure as last time"

"Zzzzz"........I dont like the human theme  ;) Its stone-age  !!!

---

### Post by psyke83 on 2009-07-11
> **plun said:**
> Well, "the same procedure as last time"

"Zzzzz"........I dont like the human theme  ;) Its stone-age  !!!

Talk to Mark Shuttleworth! ;) When I first offered to re-write Human(Ubuntulooks) with the Murrine engine, I was told (through degrees of separation) that is had to look *exactly* like the original theme, with as little deviation as possible. I did that...

The current theme has changed a little bit, but if I were to significantly change the look, it wouldn't have been accepted. It's a minor update with some visual tweaks, nothing more.

There are many excellent themes out there (Dust, Shiki-Colors, etc.). If you like none of them, then it's probably the limited GTK toolkit (and engines) that you hate.

---

### Post by plun on 2009-07-11
> **psyke83 said:**
> Talk to Mark Shuttleworth! ;) When I first offered to re-write Human(Ubuntulooks) with the Murrine engine, I was told (through degrees of separation) that is had to look *exactly* like the original theme, with as little deviation as possible. I did that...

The current theme has changed a little bit, but if it were significantly different, it wouldn't have been accepted. There are many good themes out there (Dust, Shiki-Colors, etc.). If you like none of them, then it's probably the limited GTK toolkit (and engines) that you hate.

Well, I define its as crap and nothing else !!!  Brownish crap...

No hard feelings, peace....;)

---

### Post by psyke83 on 2009-07-13
Hey folks,

As you may know, the Human theme has been updated in Kenneth Wimer's PPA (which will be released as an official update in the near future). In the latest version we have set the button icon size to 16,16px - see [comment #37]("http://ubuntuforums.org/showpost.php?p=7597314&postcount=37") for a comparison.

If you have any feedback on the theme, please share your thoughts, such as whether you feel that the smaller button icons are an improvement or regression.

Just keep something in mind: this is not a "new" theme - for now it's just a minor evolution of the Human theme. Furthermore, this is an update of the GTK theme alone - there are plans to change the Metacity decoration, but I'm not the one working on that.

---

### Post by ktp on 2009-07-13
> **psyke83 said:**
> Hey folks,

As you may know, the Human theme has been updated in Kenneth Wimer's PPA (which will be released as an official update in the near future). In the latest version we have set the button icon size to 16,16px - see [comment #37]("http://ubuntuforums.org/showpost.php?p=7597314&postcount=37") for a comparison.

If you have any feedback on the theme, please share your thoughts, such as whether you feel that the smaller button icons are an improvement or regression.

Just keep something in mind: this is not a "new" theme - for now it's just a minor evolution of the Human theme. Furthermore, this is an update of the GTK theme alone - there are plans to change the Metacity decoration, but I'm not the one working on that.

+1 for the smaller buttons.

---

### Post by amano on 2009-07-13
+1 for smaller buttons

---

### Post by perfectska04 on 2009-07-13
Transmission has a minor panel icon bug when 16px size buttons are used in GTK themes and the stock Transmission icons are used.

I filed the bug today, so hopefully someone will look at it if the next Human theme uses 16px buttons.

Issue report [here]("http://trac.transmissionbt.com/ticket/2274")

---

### Post by psyke83 on 2009-07-14
> **perfectska04 said:**
> Transmission has a minor panel icon bug when 16px size buttons are used in GTK themes and the stock Transmission icons are used.

I filed the bug today, so hopefully someone will look at it if the next Human theme uses 16px buttons.

Issue report [here]("http://trac.transmissionbt.com/ticket/2274")

Unfortunately, Transmission isn't the only culprit - gnome-power-manager has the same problem. If you're not using a laptop, go to System -> Preferences -> Power Management, General -> Always display an icon.

For curiosity's sake, I set 48,48 buttons and the offending notification icons are continuing to display with 16,16 size icons. We need to file a bug on launchpad, possibly against gnome-panel (as it may not be application-specific).

It seems that gnome-panel is rejecting the 22,22px or 24,24px icons because of the panel icon scaling algorithm being too strict. If you manually change your panel size from 24px to 26px, transmission and gnome-power-manager will display the 24,24px icons correctly.

---

### Post by moomex on 2009-07-14
In Human icon set, "gtk-ok.png" and "dialog-ok.png" don't have 16x16 icons. Hence, some apps (e.g Firefox) forced to display 24x24 icons which make the GtkButton in those apps very big.

This is a minor bug, and can be fixed within seconds. Simply create 16x16 icons for "gtk-ok.png" and "dialog-ok.png". Hence, there's no reason this fix not included by default.

---

### Post by perfectska04 on 2009-07-14
> **psyke83 said:**
> Unfortunately, Transmission isn't the only culprit - gnome-power-manager has the same problem. If you're not using a laptop, go to System -> Preferences -> Power Management, General -> Always display an icon.

For curiosity's sake, I set 48,48 buttons and the offending notification icons are continuing to display with 16,16 size icons. We need to file a bug on launchpad, possibly against gnome-panel (as it may not be application-specific).

It seems that gnome-panel is rejecting the 22,22px or 24,24px icons because of the panel icon scaling algorithm being too strict. If you manually change your panel size from 24px to 26px, transmission and gnome-power-manager will display the 24,24px icons correctly.

I just tried setting it to "Always display an icon" and it does seem to be affected as well. For Transmission, copying its icons from hicolor into your current icon set (keeping the same folder structure) fixes it for some unknown reason.

---

### Post by moomex on 2009-07-14
I just made little changes to this theme to use the ubuntulooks engine for scrollbars. Is it appropriate to post the modified one here ?

---

### Post by leptest on 2009-07-14
> **moomex said:**
> Nice work ;) !!

I would change one thing though. The GtkButton size is freaking HUGE. I think it should be smaller.

**[SIZE="4"]Before[/SIZE]**
[IMG]http://yoyo.monash.edu.my/images/humanity-1.png[/IMG]

```
gtk-icon-sizes="panel-menu=24,24:gtk-button=16,16"
```
**[SIZE="4"]After[/SIZE]**
[IMG]http://yoyo.monash.edu.my/images/humanity-2.png[/IMG]

Windows Vista and Leopard have even smaller buttons and I don't hear anybody complaining about their small size or having trouble clicking on them. I hope this gets fixed by default.

I vote for somewhere in between.

---

### Post by psyke83 on 2009-07-14
> **leptest said:**
> I vote for somewhere in between.

The Human icon theme has only 16, 22 and 24pt sized icons. Anything in-between will look very blurry (as SVG scaling isn't great for low point sizes).

---

### Post by yelo3 on 2009-07-14
Is it possible to differentiate the button icon size from the panel icon size? 16x16 in the panel is too low for my eyes

---

### Post by perfectska04 on 2009-07-14
> **psyke83 said:**
> The Human icon theme has only 16, 22 and 24pt sized icons. Anything in-between will look very blurry (as SVG scaling isn't great for low point sizes).

Agreed. For scaling down, SVG's are no different than pixmaps - the advantage comes from being able to scale up. However, in small sizes - the already thick borders will become even thicker - so SVG should ideally only be used for scaling up in the larger sizes. Everything smaller than 48px should be rendered to bitmaps for performance and the ability to cache icons.

---

### Post by trot2millah on 2009-07-14
Looks great, the least all of us can hope for is that it gets implemented into Karmic.  I also especially like the icon set and with some minor tweaking (not a fan of the power management icon personally) it has the potential to be an awesome default icon set.

---

### Post by perfectska04 on 2009-07-14
> **psyke83 said:**
> Unfortunately, Transmission isn't the only culprit - gnome-power-manager has the same problem. If you're not using a laptop, go to System -> Preferences -> Power Management, General -> Always display an icon.

For curiosity's sake, I set 48,48 buttons and the offending notification icons are continuing to display with 16,16 size icons. We need to file a bug on launchpad, possibly against gnome-panel (as it may not be application-specific).

It seems that gnome-panel is rejecting the 22,22px or 24,24px icons because of the panel icon scaling algorithm being too strict. If you manually change your panel size from 24px to 26px, transmission and gnome-power-manager will display the 24,24px icons correctly.

psyke, can you report the panel bug or should I?
I'm a little hesitant to file it against gnome-panel as having the icons in the current icon set instead of /hicolor fixes it for me, so perhaps there's some icon inheritance issue to be blamed rather than the panel, and it does seem to happen to only a certain few applications.

---

### Post by psyke83 on 2009-07-14
> **perfectska04 said:**
> psyke, can you report the panel bug or should I?
I'm a little hesitant to file it against gnome-panel as having the icons in the current icon set instead of /hicolor fixes it for me, so perhaps there's some icon inheritance issue to be blamed rather than the panel, and it does seem to happen to only a certain few applications.

Well, I think that it's a problem with the panel *and* those certain applications. If the panel width is set to 24px, the 22px icons should fit in the notification window. As I said, having a panel of 26px allows the 22px icons to be used properly, so it seems to be a scaling problem as well.

There's no harm in looking into the scaling algorithm of the notification area of the panel. I'll file a few bugs on launchpad (not upstream quite yet). We also need some 16px icons generated as mentioned by moomex.

---

### Post by lazka on 2009-07-14
> **psyke83 said:**
> 
It seems that gnome-panel is rejecting the 22,22px or 24,24px icons because of the panel icon scaling algorithm being too strict. If you manually change your panel size from 24px to 26px, transmission and gnome-power-manager will display the 24,24px icons correctly.

Icon sizes are handled by the app.. if you assign a too big icon it will get clipped.

If the panel size changes the apps have to scale it themselfs etc.. as far as I know.

---

### Post by perfectska04 on 2009-07-14
> **psyke83 said:**
> Well, I think that it's a problem with the panel *and* those certain applications. If the panel width is set to 24px, the 22px icons should fit in the notification window. As I said, having a panel of 26px allows the 22px icons to be used properly, so it seems to be a scaling problem as well.

There's no harm in looking into the scaling algorithm of the notification area of the panel. I'll file a few bugs on launchpad (not upstream quite yet). We also need some 16px icons generated as mentioned by moomex.

Would these work? They're the same from gnome-colors, and they're already made in all sizes.

---

### Post by plun on 2009-07-15
About the theme, just read [this]("http://derstandard.at/fs/1246541995003/Interview-Shuttleworth-about-GNOME-30---Whats-good-whats-missing-what-needs-work")

> **derStandard.at**: Same question, next year: Is there going to be a new theme for the next Ubuntu release?

**Shuttleworth**: Well I think it's better to stick with what you have until you have a clear vision on where you want to go, right? I know I've unfortunately said this before, so my credibility is wearing thin, we're starting to get into a position where I have more confidence in that we are able to do that and it will be an important part of future Ubuntu releas

So thats it......;)


Maybe more ideas can be taken from Duracell ??? , they are using brown for their branding in a very pleasant way.

[http://duracell.com/protect/default.asp](http://duracell.com/protect/default.asp)


--

---

### Post by vishalrao on 2009-07-15
duracell brown? i thot it was copper...

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> Would these work? They're the same from gnome-colors, and they're already made in all sizes.

We don't need to replace icons, we need to fix the problem of icon fallbacks not working.

I've opened bug [#400371]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/400371"), you may want to subscribe and keep an eye on developments there.

P.S. I've filed against gnome-panel, but it's possible that it'll get re-assigned. Better safe than sorry.

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> We don't need to replace icons, we need to fix the problem of icon fallbacks not working.

I've opened bug [#400371]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/400371"), you may want to subscribe and keep an eye on developments there.

P.S. I've filed against gnome-panel, but it's possible that it'll get re-assigned. Better safe than sorry.

Thanks, I've just subscribed. Hope this gets fixed, other operating systems use 16px icons in buttons with no user complaints - so there's really no need to have those "xbox huge" Clearlooks buttons.

BTW, does the 16px gtk buttons even work in XFCE or is something else required? I remember testing Xubuntu but the buttons were still the regular size, regardless of the theme.

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> Thanks, I've just subscribed. Hope this gets fixed, other operating systems use 16px icons in buttons with no user complaints - so there's really no need to have those "xbox huge" Clearlooks buttons.

BTW, does the 16px gtk buttons even work in XFCE or is something else required? I remember testing Xubuntu but the buttons were still the regular size, regardless of the theme.

I've added a comment to [bug #84931]("https://bugs.launchpad.net/bugs/84931") asking for the missing icons to be added; if you're aware of any other icons that require 16,16px versions, can you please post it there?

I'll be sure to nag Kenneth until he gets this done ;).

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> I've added a comment to [bug #84931]("https://bugs.launchpad.net/bugs/84931") asking for the missing icons to be added; if you're aware of any other icons that require 16,16px versions, can you please post it there?

I'll be sure to nag Kenneth until he gets this done ;).

Sure, I'll leave "Human" as my default for the next two days. If I come across any button looking blurry, I'll add to the list.

Edit: I'm not sure if it's a bug, but Human already has gtk-close in 16px - but the 12x12px icon is used instead. It looks a bit out of place with the rest of the 16px icons.

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> Sure, I'll leave "Human" as my default for the next two days. If I come across any button looking blurry, I'll add to the list.

Edit: I'm not sure if it's a bug, but Human already has gtk-close in 16px - but the 12x12px icon is used instead. It looks a bit out of place with the rest of the 16px icons.

Thanks, I appreciate it.

You won't see blurry icons, however. When a 16,16px icon isn't available, it displays a mixture of 16,16px and 24,24px icons (without scaling) - and all the buttons will be sized appropriate to the largest icon used (24,24px). See tsclient, for example.

Your GNOME-Colors set (and the Humanity set) isn't affected in the case of tsclient (as they have the gtk-ok.png and dialog-ok.png icons in the smaller size).

---

### Post by psyke83 on 2009-07-16
How odd... I'm no longer seeing the notification icon size issue!

I tried manually updating the icon caches (via update-icon-caches and gtk-update-icon-cache), perhaps this resolved the fallback issue...

---

### Post by perfectska04 on 2009-07-16
I just went through the roster of my installed applications and besides the previously noted icons and gtk-close, I couldn't find any more missing 16px button icons (I even went through menu-items just in case). I'll try from a live cd with the default install, perhaps that'll be more helpful.

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> How odd... I'm no longer seeing the notification icon size issue!

I tried manually updating the icon caches (via update-icon-caches and gtk-update-icon-cache), perhaps this resolved the fallback issue...

I routinely run gtk-update-icon-cache for everything in my /usr/share/icons folder, but it doesn't seem to fix the issue. What commands did you use, specifically?

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> I routinely run gtk-update-icon-cache for everything in my /usr/share/icons folder, but it doesn't seem to fix the issue. What commands did you use, specifically?

I'm not sure exactly which did the trick (I was randomly trying some combinations)...

```
conn@inspiron:~$ cat .bash_history  | grep update-icon
man gtk-update-icon-cache 
sudo gtk-update-icon-cache 
man gtk-update-icon-cache 
man gtk-update-icon-cache -v
sudo gtk-update-icon-cache -v
sudo update-icon-caches
sudo update-icon-caches /usr/share/icons/Human
sudo update-icon-caches /usr/share/icons/Human/index.theme 
man update-icon-caches 
sudo gtk-update-icon-cache 
sudo gtk-update-icon-cache /usr/share/themes/Human/index.theme 
sudo gtk-update-icon-cache /usr/share/themes/Human/
sudo update-icon-caches 
man update-icon-caches 
```

I also downgraded the human-icon-theme and then upgraded again (as I was trying to file a bug using ubuntu-bug, and it required a validated package).

I just forced a purge of the human-icon-theme, re-installed, logged out and back in, and the issue still appears to be fixed. I'm not sure why this is happening.

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> I'm not sure exactly which did the trick (I was randomly trying some combinations)...

```
conn@inspiron:~$ cat .bash_history  | grep update-icon
man gtk-update-icon-cache 
sudo gtk-update-icon-cache 
man gtk-update-icon-cache 
man gtk-update-icon-cache -v
sudo gtk-update-icon-cache -v
sudo update-icon-caches
sudo update-icon-caches /usr/share/icons/Human
sudo update-icon-caches /usr/share/icons/Human/index.theme 
man update-icon-caches 
sudo gtk-update-icon-cache 
sudo gtk-update-icon-cache /usr/share/themes/Human/index.theme 
sudo gtk-update-icon-cache /usr/share/themes/Human/
sudo update-icon-caches 
man update-icon-caches 
```

Just tried them all, but it still happens to me (at least testing with transmission) :(. Running them for /hicolor didn't do much either, do you happen to have copied any of the affected icons to your "Human" folder?

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> Just tried them all, but it still happens to me (at least testing with transmission) :(. Running them for /hicolor didn't do much either, do you happen to have copied any of the affected icons to your "Human" folder?

No...
```
conn@inspiron:~$ sudo updatedb
conn@inspiron:~$ locate transmission.png
/usr/share/app-install/icons/transmission.png
/usr/share/icons/gnome-colors-common/16x16/apps/transmission.png
/usr/share/icons/gnome-colors-common/22x22/apps/transmission.png
/usr/share/icons/gnome-colors-common/24x24/apps/transmission.png
/usr/share/icons/gnome-colors-common/32x32/apps/transmission.png
/usr/share/icons/hicolor/16x16/apps/transmission.png
/usr/share/icons/hicolor/22x22/apps/transmission.png
/usr/share/icons/hicolor/24x24/apps/transmission.png
/usr/share/icons/hicolor/32x32/apps/transmission.png
/usr/share/icons/hicolor/48x48/apps/transmission.png
/usr/share/pixmaps/transmission.png
```

I also deleted the "icon-theme.cache" files that were created, logged out and back in - no difference.

---

### Post by psyke83 on 2009-07-16
There was a gnome-panel update in Karmic today - though I don't see any relevant information in the changelog*, it could be the source of the fix. Ensure you're completely up-to-date (switch from the regional mirror if necessary)...

*It's a new upstream release, so the changelog is probably incomplete. Checking upstream now...

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> There was a gnome-panel update in Karmic today - though I don't see any relevant information in the changelog*, it could be the source of the fix. Ensure you're completely up-to-date (switch from the regional mirror if necessary)...

*It's a new upstream release, so the changelog is probably incomplete. Checking upstream now...

I'll test a daily-live in Virtualbox, I'm currently just testing from Jaunty - where the same bug exists.

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> I'll test a daily-live in Virtualbox, I'm currently just testing from Jaunty - where the same bug exists.

I wonder if anybody else that's reading this thread (and using Karmic) can confirm this in the meantime? The upstream changelog doesn't show the obvious fix.

Edit: no need, it's definitely because of the latest gnome-panel upgrade. I downgraded to [2.26.3-0ubuntu2]("https://launchpad.net/ubuntu/+source/gnome-panel/1:2.26.3-0ubuntu2/+build/1116406") and the issue re-appeared.

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> I wonder if anybody else that's reading this thread (and using Karmic) can confirm this in the meantime? The upstream changelog doesn't show the obvious fix.

Just tested a live-cd, updated gnome-panel - installed shiki (to test with 16px buttons) and after "sudo killall gnome-panel" both icons finally display properly, regadless of theme or icon set!

---

### Post by psyke83 on 2009-07-16
> **perfectska04 said:**
> Just tested a live-cd, updated gnome-panel - installed shiki (to test with 16px buttons) and after "sudo killall gnome-panel" both icons finally display properly, regadless of theme or icon set!

Thanks for the assistance in troubleshooting this bug. I can't believe it, though! As I was filing the bug, the gnome-panel upgrade was pending on my system and I didn't even check. What a waste ;).

However, I guess the bug can be useful to track against the Jaunty packages, since there are many Shiki users in Jaunty (and they may also want the Human update from Ken's PPA).

---

### Post by perfectska04 on 2009-07-16
> **psyke83 said:**
> Thanks for the assistance in troubleshooting this bug. I can't believe it, though! As I was filing the bug, the gnome-panel upgrade was pending on my system and I didn't even check. What a waste ;).

However, I guess the bug can be useful to track against the Jaunty packages, since there are many Shiki users in Jaunty (and they may also want the Human update from Ken's PPA).

Yes, not to mention that there are many other themes with the same settings. Then again, if it's already fixed for Karmic, I'll leave it to [whoever-is-in-charge]'s discretion - as it might be more appropriate to fix more outstanding issues at this time in the development cycle.

---

### Post by benjamimgois on 2009-08-10
Is 0.9 the last update of humanity ?

---

### Post by Fylk on 2009-08-21
I like the theme, kinda glad we're back to the sectioned bars for the progress and such.

---

### Post by Bou on 2009-09-01
Hi Psyke,

It seems Humanity is now used as the new official Human? Congrats, it does look good!

A small complaint though, when using custom colours all elements seem to look the same. They could use a little more variation. I'm attaching a screenshot as well as a quick mockup.

---

### Post by knn on 2009-09-01
I've opened a bug because of the scroll bar in Human/Humanity, and was directed to this topic. The bug is here: [https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/422511](https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/422511)

---

### Post by Bou on 2009-09-06
Also, Psyke, do you know why the app icon was removed in the titlebar's left end?

---

### Post by Starks on 2009-09-10
psyke, the trough-border issue has been resolved in the Firefox 3.6 alphas.

---

### Post by psyke83 on 2009-09-14
> **Bou said:**
> Hi Psyke,

It seems Humanity is now used as the new official Human? Congrats, it does look good!

A small complaint though, when using custom colours all elements seem to look the same. They could use a little more variation. I'm attaching a screenshot as well as a quick mockup.

I understand the need for variety, but if we were to selectively change the colours of widgets, your system would become inconsistent. For example, the older Human theme used to have a lighter orange for selected items on menus compared to checkbuttons or progress bars, but all kinds of unforseen events occurred. Applications which used custom widgets became inconsistent (e.g. Banshee), and certain widgets began to act strangely (for example, in Network Manager's applet, progress bar widgets are used to show signal strength, but due to limitations of GTK it is impossible to theme a progressbar within a menu - it will use the selected colour of menu items rather than what is defined for progressbars).

I sent a quick update to Kenneth that changes unfocused selected items to grey (previously it was changing to a slightly darker orange). This is not exactly what you asked for, but I'll do some experimenting to see if I can find a way to incorporate a little more variety when colouring widgets.

---

### Post by psyke83 on 2009-09-14
> **knn said:**
> I've opened a bug because of the scroll bar in Human/Humanity, and was directed to this topic. The bug is here: [https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/422511](https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/422511)

Thanks, I've subscribed. We can't fix* this in the gtkrc or Metacity theme code, I think. Either GTK itself or the Murrine GTK engine needs to be patched. I'll try to get a hold of Andrea Cimitan to see if he knows.

*By fix, I mean resolve the issue without setting the trough border back to 0.

---

### Post by psyke83 on 2009-09-14
> **Bou said:**
> Also, Psyke, do you know why the app icon was removed in the titlebar's left end?

I think that was changed by Kenneth (as I mentioned before, I didn't focus on updating the Metacity). I had thought that the Metacity theme was going to be replaced by something else, but I'm not sure what's going to happen now.

---

### Post by benjamimgois on 2009-09-27
So, this is not the official theme anymore ?!

---

### Post by psyke83 on 2009-09-27
> **benjamimgois said:**
> So, this is not the official theme anymore ?!

The thread isn't updated, that's all. The darker brown has been chosen as the selected background colour for the theme. After the beta freeze some more changes may happen.

Here's a screenshot of a work in progress - the metacity is lighter and the colours are slightly changed.

I'm also going to spend some time on the metacity to see if I can smoothen the window decoration edges.

---

### Post by psyke83 on 2009-09-28
Here's a preview of my first real attempt to update the Human metacity borders - notice that the outer frame is now different for focused and unfocused windows. I've sent to Ken and will hopefully hear if this update is appropriate for inclusion :).

---

### Post by 6205 on 2009-09-28
That brown Human modern metacity looks good, but bottom corners should be rounded for better look.

---

### Post by cyberkilla on 2009-09-28
> **6205 said:**
> That brown Human modern metacity looks good, but bottom corners should be rounded for better look.

I don't think the bottom should be rounded at all. It is harder to make the borders on the bottom look any good.

The Metacity theme looks great! Impressive colouring for focused windows. 

The only major thing that really stands out as needing a bit of tweaking is the title text. It looks like it could do with dropping down a bit, to make it look vertically centred. 

The concept of a drop-shadow might be better if you put it directly under the text. Presumably, this would have the effect of creating a small shadowy border around all of the text, giving it depth without elevating it a mile above the window:)

---

### Post by psyke83 on 2009-09-28
> **cyberkilla said:**
> I don't think the bottom should be rounded at all. It is harder to make the borders on the bottom look any good.

Yes, let's keep the squared bottom for now. Grey borders also look more aliased, so it also helps make the theme look more professional.

> 
The Metacity theme looks great! Impressive colouring for focused windows. 

The only major thing that really stands out as needing a bit of tweaking is the title text. It looks like it could do with dropping down a bit, to make it look vertically centred.

Fixed :). See attachment.

> The concept of a drop-shadow might be better if you put it directly under the text. Presumably, this would have the effect of creating a small shadowy border around all of the text, giving it depth without elevating it a mile above the window:)

I'm not entirely sure what you mean. At the moment, the shadow drops 1 pixel to the right and 1 pixel down. Do you mean to change the shadow so it drops only 1 pixel down?

---

### Post by Merk42 on 2009-09-28
So.. you're going for a blatant Windows 7 rip-off with those borders?

I don't mind the idea of a border, but that look with the dramatic color change a quarter the way down is just a copy.
[ATTACH]130076[/ATTACH]

---

### Post by psyke83 on 2009-09-28
> **Merk42 said:**
> So.. you're going for a blatant Windows 7 rip-off with those borders?

I don't mind the idea of a border, but that look with the dramatic color change a quarter the way down is just a copy.
[ATTACH]130076[/ATTACH]

;)

I doubt that Microsoft has filed a patent on a two-part gradient on window borders, if that's your concern. If you're annoyed that it's a copy, well then there's not much I can say to you. Just because somebody else did it first does not mean that nobody can ever re-implement the idea again, especially for something as trivial as a border.

Also, it's a logical extension of the gloss effect (which is quite common in Murrine's glass themes) and you can see the same effect on the actual button gradients (which precede Aero in Vista and Windows 7, by the way). Look at the division in the default wallpaper too.

I originally set a single gradient which also looks nice, but I thought I would show off the "inspired" version to see how people react. As far as I know, nobody has ever tried this in a Metacity theme (of which the theming community has somewhat stagnated in the past few years).

---

### Post by froggyswamp on 2009-09-28
> **psyke83 said:**
> 
Just because somebody else did it first does not mean that nobody can ever re-implement the idea again, 

(a bit offtopic)
Agree, also, I hope rather sooner then later corporations would understand there's no such thing as original idea in the first place, but then it would abolish patents hence it won't happen any time soon.

---

### Post by Merk42 on 2009-09-28
> **psyke83 said:**
> ;)Just because somebody else did it first does not mean that nobody can ever re-implement the idea again,

> **froggyswamp said:**
> (a bit offtopic)
Agree, also, I hope rather sooner then later corporations would understand there's no such thing as original idea in the first place, but then it would abolish patents hence it won't happen any time soon.

Riiight, but when Microsoft copies from Linux (or Apple) for something then they're all evil. 	:rolleyes:


What was the other gradient you had psyke83?

Maybe make the frame the sort of grey as the buttons, but the active window the darker grey that a button is when it is pressed down?

---

### Post by shafin on 2009-09-28
> **psyke83 said:**
> The thread isn't updated, that's all. The darker brown has been chosen as the selected background colour for the theme. After the beta freeze some more changes may happen.

Here's a screenshot of a work in progress - the metacity is lighter and the colours are slightly changed.

I'm also going to spend some time on the metacity to see if I can smoothen the window decoration edges.
What about the progress bars? New progress bars debuted here looked better than the old striped one's. I see they have made a comeback here. Do you plan to change the progress bars to better match the last orange theme?

---

### Post by psyke83 on 2009-09-28
> **shafin said:**
> What about the progress bars? New progress bars debuted here looked better than the old striped one's. I see they have made a comeback here. Do you plan to change the progress bars to better match the last orange theme?

The "new" progress bars from the orange version of the theme didn't translate well to the new darker brown selection colour. I'm going to play  around with the GTK theme soon to try and improve things a bit, as soon as I clear everything with Microsoft's lawyers... :P

---

### Post by psyke83 on 2009-09-28
> **Merk42 said:**
> Riiight, but when Microsoft copies from Linux (or Apple) for something then they're all evil. 	:rolleyes:


What was the other gradient you had psyke83?

Maybe make the frame the sort of grey as the buttons, but the active window the darker grey that a button is when it is pressed down?

Imagine that instead of the two gradients, there is just one, from the top to bottom. That was the original gradient. It looks fine, but emulating gloss helps it to fit with the other glassy elements such as the titlebar, buttons and to a lesser degree, the GTK theme.

---

### Post by Merk42 on 2009-09-28
> **psyke83 said:**
> Imagine that instead of the two gradients, there is just one, from the top to bottom. That was the original gradient. It looks fine, but emulating gloss helps it to fit with the other glassy elements such as the titlebar, buttons and to a lesser degree, the GTK theme.

I see the titlebar is glossy, but isn't the border adding a second gloss and therefore the whole windows gloss seems odd?
The buttons seem pretty matte to me.  Not FLAT mind you, I see the gradient.

Also I never meant that you'd get sued by Microsoft; just called unoriginal by anyone familiar with Windows.

---

### Post by psyke83 on 2009-09-28
> **Merk42 said:**
> I see the titlebar is glossy, but isn't the border adding a second gloss and therefore the whole windows gloss seems odd?
The buttons seem pretty matte to me.  Not FLAT mind you, I see the gradient.

Also I never meant that you'd get sued by Microsoft; just called unoriginal by anyone familiar with Windows.

The buttons are fairly matte at the moment, but an update will slightly increase the gloss (this is necessary especially for coloured widgets including the progressbar and scrollbars, due to the dark selection colour). It's a bit of a balancing act (as many don't appreciate overt gloss, as seen in most Murrine GTK themes).

I understand your criticism about originality - if it concerns you so much, suggest something more original, then. Make a mockup and show us. It's quite difficult to have an inspired, original thought with regards to UI appearance (appearance, not functionality - I'm not a programmer).

---

### Post by shafin on 2009-09-28
Originality aside, they look quite nice. Care to make an unofficial preview release here?

---

### Post by psyke83 on 2009-09-28
> **shafin said:**
> Originality aside, they look quite nice. Care to make an unofficial preview release here?

Here you go.

---

### Post by shafin on 2009-09-28
Thanks a lot. It looks nicer than the current metacity theme. I'm definitely going to use this even if it doesn't get the nod.

---

### Post by psyke83 on 2009-09-28
Another testing update with smaller window borders and a new background colour.

Note that some more changes may take place, such as changing the scrollbar back to grey (a darker grey than the background, to make it a little more distinct against the scrollbar background). Ken's messing with it for now :)

---

### Post by NCLI on 2009-09-28
"Appearance" says that I can't "move folder over folder" when I try to add the second version, even after deleting the first one. Where does it store themes?

---

### Post by JohnJackson on 2009-09-28
> **NCLI said:**
> "Appearance" says that I can't "move folder over folder" when I try to add the second version, even after deleting the first one. Where does it store themes?

~/.themes

---

### Post by psyke83 on 2009-09-28
Yes - delete the older theme from ~/.themes/ before updating.

---

### Post by NCLI on 2009-09-28
Thanks a lot. :D

I think I prefer the first one for now though. MS is on to something there, very glassy.

---

### Post by JohnJackson on 2009-09-28
Is it possible to add a small bit of padding in between the border and the icons under places? They are almost touching and it makes my eyes hurt :P

Edit: Perhaps so it lines up with the toggle location bar button?

---

### Post by Bou on 2009-09-28
> **psyke83 said:**
> Another testing update with smaller window borders and a new background colour.

I'm not sure yet, but I think I like the thicker borders a bit better, the effect is more noticeable. I'll have to use one and the other alternatively to be sure, tho :D

The gray background is definitely too intense for me, the brown one makes everything in warm tones and well, a bit monotone.

> **psyke83 said:**
> Note that some more changes may take place, such as changing the scrollbar back to grey (a darker grey than the background

That would be great.

---

### Post by psyke83 on 2009-09-28
> **NCLI said:**
> Thanks a lot. :D

I think I prefer the first one for now though. MS is on to something there, very glassy.

I prefer it too, but I don't get to make the decisions :).

---

### Post by perfectska04 on 2009-09-28
I REALLY like the humanity-testing metacity. It's borders are a bit thick, but I can brush that off to personal preference.

However, there seem to be two things that are somewhat buggy:

1. Notice how the side borders suddenly go from a light tone to a much darker color. This doesn't seem to happen in your screenshot preview.

2. This is more of a general Human-metacity issue, as it has been present forever. Buttons should have a minimum size set up. Otherwise, changing the font size to 8 or other smaller sizes makes the buttons rather small and look cramped in there.

I am testing this in Ubuntu Jaunty, for reference. I've also attached a screenshot to demonstrate these minor issues.

Other than that, good job! Human looks more beautiful than ever.

---

### Post by psyke83 on 2009-09-28
> **perfectska04 said:**
> I REALLY like the humanity-testing metacity. It's borders are a bit thick, but I can brush that off to personal preference.

However, there seem to be two things that are somewhat buggy:

1. Notice how the side borders suddenly go from a light tone to a much darker color. This doesn't seem to happen in your screenshot preview.

That was intentional (similar to Windows Aero, as some pointed out), but changed to a smooth gradient in -testing2. I think you installed the older version.

> 2. This is more of a general Human-metacity issue, as it has been present forever. Buttons should have a minimum size set up. Otherwise, changing the font size to 8 or other smaller sizes makes the buttons rather small and look cramped in there.

I think this is because the button details are actually .png files (which aren't scaled). As for setting a minimum size, do you know any Metacity themes which enforce a minimum size? The code in the theme to enforce the minimum size doesn't appear to work correctly.

---

### Post by perfectska04 on 2009-09-28
> **psyke83 said:**
> That was intentional (similar to Windows Aero, as some pointed out), but changed to a smooth gradient in -testing2. I think you installed the older version.



I'll take a look at this issue.

I might have downloaded the wrong version, I'll try getting the latest file.

Also, thanks for taking a look at #2.

---

### Post by perfectska04 on 2009-09-28
> **psyke83 said:**
> I think this is because the button details are actually .png files (which aren't scaled). As for setting a minimum size, do you know any Metacity themes which enforce a minimum size? The code in the theme to enforce the minimum size doesn't appear to work correctly.

On Shiki, I use code to enforce a minimum size and it works rather well. However, I just tried to apply it to human-testing but the line in-between the menubar and metacity seems to disappear.

I'll try some other values and I'll let you know if I can manage get around it.

---

### Post by psyke83 on 2009-09-28
> **perfectska04 said:**
> I might have downloaded the wrong version, I'll try getting the latest file.

Also, thanks for taking a look at #2.

No problem, but I wasn't being flippant. If you know any Metacity themes which work at a small font size, I want to see them in order to plagiarize the appropriate code ;).

This is the relevant part of the Human Metacity:
```
<!-- button minimum size -->
<constant name="Bmin" value="7"/>
<!-- button inside padding -->
<constant name="Bpad" value="8"/>
```

Changing these values seems to have no effect, at least on my system.

---

### Post by psyke83 on 2009-09-28
> **perfectska04 said:**
> On Shiki, I use code to enforce a minimum size and it works rather well. However, I just tried to apply it to human-testing but the line in-between the menubar and metacity seems to disappear.

I'll try some other values and I'll let you know if I can manage get around it.

Thanks, if you can get it working I'll be sure to make sure it's included.

---

### Post by perfectska04 on 2009-09-28
> **psyke83 said:**
> Thanks, if you can get it working I'll be sure to make sure it's included.

The following seems to work as far as the buttons go, they're always centered and look at their intended size regardless of font size. However, as I mentioned earlier - the top line between menu/metacity is missing. This can probably be fixed by editing the placement of this line elsewhere in the metacity. After that, perhaps shifting the title a pixel or two to ensure it's centered in height with respect to buttons would fix the issue.

Also, another suggestion might be to shift the "circle" menu icon a bit to the left and more centered, as to keep it the same distance from the border and relative in height to the window management buttons in the right and the title.

```
<frame_geometry name="normal" rounded_top_left="true" rounded_top_right="true" rounded_bottom_left="false" rounded_bottom_right="false">
  <distance name="left_width" value="6"/>
  <distance name="right_width" value="6"/>
  <distance name="bottom_height" value="6"/>
  <distance name="left_titlebar_edge" value="4"/>
  <distance name="right_titlebar_edge" value="4"/>
  <distance name="button_width" value="24"/>
  <distance name="button_height" value="24"/>
  <distance name="title_vertical_pad" value="3"/>
  <border name="title_border" left="2" right="2" top="2" bottom="2"/>
  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>
```

---

### Post by psyke83 on 2009-09-28
> **perfectska04 said:**
> The following seems to work as far as the buttons go, they're always centered and look at their intended size regardless of font size. However, as I mentioned earlier - the top line between menu/metacity is missing. This can probably be fixed by editing the placement of this line elsewhere in the metacity. After that, perhaps shifting the title a pixel or two to ensure it's centered in height with respect to buttons would fix the issue.

Thanks for looking into it. The relevant parts were:```
  <distance name="button_width" value="24"/>
  <distance name="button_height" value="24"/>
```

This works for lower text sizes, but when you use large text, the icons remain statically sized. This is not ideal. With this in mind I don't think it's appropriate to include this code, sorry.

Ken has taken over and will now make some final tweaks (the background and scrollbar colours). Because of the beta freeze, more changes aren't possible as they need to ship something stable.

For the future, we should check into this issue further and see if we can properly assign dynamic limits (upper and lower), rather than statically limiting button sizes.

> Also, another suggestion might be to shift the "circle" menu icon a bit to the left and more centered, as to keep it the same distance from the border and relative in height to the window management buttons in the right and the title.

Ken worked on the circle, and I believe this is the effect he desired. If you actually click on the circle, you can see the checkmarks on the context menu roughly align, so it's probably ok.

---

### Post by 6205 on 2009-09-28
This metacity is nice, but i'm gettin' tired from old Human caption buttons. Maybe you could give them some facelifting :) Attaching mockups for inspiration...

---

### Post by Joe_Bishop on 2009-09-28
> **6205 said:**
> This metacity is nice, but i'm gettin' tired from old Human caption buttons. Maybe you could give them some facelifting :) Attaching mockup for inspiration...
Hm, very nice

---

### Post by shafin on 2009-09-28
If you can convince Ken to accept the first metacity that would be great. To me, that metacity really looks much better. Right now, I've just mixed it with your new GTK. I see there is a panel_small png file present in the GTK folder. Is it going to be used? The brown does not look too good on the panel, the older grey looked better. What about going for a dark panel like dust?

---

### Post by psyke83 on 2009-09-28
> **shafin said:**
> If you can convince Ken to accept the first metacity that would be great. To me, that metacity really looks much better. Right now, I've just mixed it with your new GTK. I see there is a panel_small png file present in the GTK folder. Is it going to be used? The brown does not look too good on the panel, the older grey looked better. What about going for a dark panel like dust?

I'll twist some arms, we'll see. No big changes will be allowed after the beta release, and I wouldn't have enough money to mount a legal defense if necessary... just kidding (I hope!) ;).

If the worst comes to the worst and it's not included by the beta or final release, I'll upload a version of the Humanity theme with the first version of the Metacity theme (or perhaps with both versions) included.

---

### Post by psyke83 on 2009-09-28
> **6205 said:**
> This metacity is nice, but i'm gettin' tired from old Human caption buttons. Maybe you could give them some facelifting :) Attaching mockups for inspiration...

Thanks for the mockup! I'm taking a break until I hear from Ken, so I don't think any further changes will make it in time for the beta freeze. You may see changes to the buttons and other parts of the theme through the unofficial Humanity theme after the final release of Karmic, perhaps.

---

### Post by benjamimgois on 2009-09-28
> **6205 said:**
> This metacity is nice, but i'm gettin' tired from old Human caption buttons. Maybe you could give them some facelifting :) Attaching mockups for inspiration...

That's very nice. I like your mockup.

---

### Post by Regenweald on 2009-09-28
> **6205 said:**
> This metacity is nice, but i'm gettin' tired from old Human caption buttons. Maybe you could give them some facelifting :) Attaching mockups for inspiration...

I also find these very nice, but maybe with square corners also ? Until the engines can do proper rounding i tend to stick to clean square corners. 

My current combo is kind of mixed and matched: Humanity icons, Human Controls, Glider Borders, custom colour selection. Kudos to Psyke for a very clean and pleasing control set.

---

### Post by Gourgi on 2009-09-28
> **psyke83 said:**
> Here's a preview of my first real attempt to update the Human metacity borders - notice that the outer frame is now different for focused and unfocused windows. I've sent to Ken and will hopefully hear if this update is appropriate for inclusion :).

nice work!
Congrats psyke83 :popcorn:

---

### Post by cyberkilla on 2009-09-29
> **6205 said:**
> This metacity is nice, but i'm gettin' tired from old Human caption buttons. Maybe you could give them some facelifting :) Attaching mockups for inspiration...

Those actually look nice. I like the one that groups minimize/maximize. Might be nice if the close button was elongated slightly. It would make it a better target for the mouse.

And heaven forbid we get accused of copying Windows! Why do we need to be unique and original for every single UI change? The glossy borders are a very nice touch. I like them a lot. Shiny is the flavour of the month.

With regards to the title text... Instead of having the drop-shadow down to the bottom-right, what would it look like if the shadow was directly below the text?

What I mean is, if the text is drawn at (5,5), the shadow would be at (5,5) too. I'm not sure what it would look like, but in my head, it would put a shadow around the entire title.

```

#########
# Title # <-shadow
#########

```

By the way, thank you for putting a bit of effort in with this. I had assumed that the "art team" was going to work on the theme, but that doesn't seem to be the case (unless you're part of the art team:)).

---

### Post by 6205 on 2009-09-29
Added two more mockups, with less rounded buttons, moved to the metacity border like in Fedora..

---

### Post by hansrolo on 2009-09-29
Hi 6205,

I think Google Chrome's window buttons have something to them with a slightly wider 'close' button. See: [http://www.altafsayani.com/wp-content/uploads/2008/09/google-chrome-screen.jpg](http://www.altafsayani.com/wp-content/uploads/2008/09/google-chrome-screen.jpg)

Perhaps you could add another mock-up trying this out? I love what you're doing so far.

Hans

---

### Post by hansrolo on 2009-09-29
Following on from my last post... I'm sure you're aware of this, but it's nice how Chrome's maximize button changes with window states. 

I'm not sure what the current technical limitations we're working with are, but this image shows Chrome's button rollovers. There's a tiny fade in/fade out which is very slick.

Hope this helps. :)

---

### Post by 6205 on 2009-09-29
> **hansrolo said:**
> Hi 6205,

I think Google Chrome's window buttons have something to them with a slightly wider 'close' button. See: [http://www.altafsayani.com/wp-content/uploads/2008/09/google-chrome-screen.jpg](http://www.altafsayani.com/wp-content/uploads/2008/09/google-chrome-screen.jpg)

Perhaps you could add another mock-up trying this out? I love what you're doing so far.

Hans

Creating mockups is easy. I could spend a whole day like this :)
But it does not mean that artwork team will use them. I have done them just for their inspiration. My favorite is mockup4

---

### Post by hansrolo on 2009-09-29
Sorry, I was trying to get you to do my dirty work! Here's an attempt to blend one of your excellent mockups with what I like from the Chrome buttons to show you what I was talking about.

---

### Post by 6205 on 2009-09-29
> **hansrolo said:**
> Sorry, I was trying to get you to do my dirty work! Here's an attempt to blend one of your excellent mockups with what I like from the Chrome buttons to show you what I was talking about.

you see, it's easy to do it.. looking good, but reminds me too much windows. fedora 10 has good buttons and therefore mockups 3+4 are my favorite. but i don't know how to create a metacity theme :( playing with GIMP can anybody..

Something like this look great [http://gnome-look.org/content/show.php/Royale+VSQ?content=112448](http://gnome-look.org/content/show.php/Royale+VSQ?content=112448)
Now imagine that in those brown colors and it's perfect :)

---

### Post by Tibuda on 2009-09-29
> **hansrolo said:**
> Sorry, I was trying to get you to do my dirty work! Here's an attempt to blend one of your excellent mockups with what I like from the Chrome buttons to show you what I was talking about.

Chromium have replaced those buttons with buttons that don't mimic Vista buttons.

---

### Post by psyke83 on 2009-09-29
> **6205 said:**
> you see, it's easy to do it.. looking good, but reminds me too much windows. fedora 10 has good buttons and therefore mockups 3+4 are my favorite. but i don't know how to create a metacity theme :( playing with GIMP can anybody..

Something like this look great [http://gnome-look.org/content/show.php/Royale+VSQ?content=112448](http://gnome-look.org/content/show.php/Royale+VSQ?content=112448)
Now imagine that in those brown colors and it's perfect :)

[Here's]("http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html") a guide. It may look a bit complicated, but once you actually experiment, it's not so bad.

Thanks for all the mockups - I like your mockup 4 in particular. I'm going to see if I can implement something similar in the theme, but as I said, it's probably too late for further changes :(.

---

### Post by NCLI on 2009-09-29
Do your best, it would be awesome :guitar:

---

### Post by Merk42 on 2009-09-29
All of this makes me really want to create a theme.
Please do not take that as "Humanity sucks so much, if I want something done right I have to do it myself", take it as "you have inspired me".

I just can't believe there's no GUI program for making themes, and I doubt that will change for GTK+3

---

### Post by 6205 on 2009-09-29
mmm...i've added maximized version to mockup4.. now if somebody would create it please :)

on windows there was excellent stylebuilder for creating XP msstyles.. something like that on gnome would be great. btw.. what is widget factory ? something similar ?

---

### Post by psyke83 on 2009-09-29
> **6205 said:**
> mmm...i've added maximized version to mockup4.. now if somebody would create it please :)

on windows there was excellent stylebuilder for creating XP msstyles.. something like that on gnome would be great. btw.. what is widget factory ? something similar ?

What you can do is look at the existing buttons in the Human metacity. Extract the contents of the archive, and navigate to the metacity-1 folder.

You'll see that the button details are actually .png files. I suggest that you ignore the button placement and outline, and try to create the button details (i.e. the minimize/maximize/close icons).

Once you have the new icons, it's not too difficult to adjust the actual placement of buttons and their outline, in the actual theme code.

---

### Post by psyke83 on 2009-09-29
Ok folks, just to let you know (and to avoid possible disappointment)...

Due to beta freeze and the lack of time, the new Metacity may not be used for the official theme - instead, the old version will be used (that's quite dark), with some tweaks to the buttons. The GTK update from -testing2 will be included, but it was deemed necessary to disable the coloured scrollbar.

Further changes may be allowed after the beta freeze, but if that doesn't happen, I'll package the Humanity theme separately and make it available from this thread, with the choice of the "glassy" metacity border included :).

---

### Post by 6205 on 2009-09-29
mmm :)

---

### Post by Merk42 on 2009-09-29
> **psyke83 said:**
> Ok folks, just to let you know (and to avoid possible disappointment)...

Due to beta freeze and the lack of time, the new Metacity may not be used for the official theme - instead, the old version will be used (that's quite dark), with some tweaks to the buttons. The GTK update from -testing2 will be included, but it was deemed necessary to disable the coloured scrollbar.

Further changes may be allowed after the beta freeze, but if that doesn't happen, I'll package the Humanity theme separately and make it available from this thread, with the choice of the "glassy" metacity border included :).

So we are definitely getting Humanity, it just may be an earlier version?

---

### Post by psyke83 on 2009-09-29
> **Merk42 said:**
> So we are definitely getting Humanity, it just may be an earlier version?

The GTK theme is the same as -testing2, but the scrollbar is now grey (darker than the background), with no trough. The colour change was Canonical's decision, and the trough removal (scrollbar's surrounding border) is due to [two]("https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/422511") [bugs]("https://bugs.launchpad.net/libgtk/+bug/327863"), one of which reduces usability for some users.

I was hoping that these bugs would be addressed in time for release, or at least the theme would stay as it was in order to maintain steady pressure for the bugs to be fixed soon.

As for the Metacity, there seemed to be some concern that the window border was lighter than the GTK selection colour (which is true, but didn't seem like a big problem to me).

---

### Post by 6205 on 2009-09-29
Could you please post screenshots with current version of GTK theme with metacity? (for loosers like me, currently without Ubuntu installed :) thanks... 
ama ready for objective, constructive critcs :)

---

### Post by benjamimgois on 2009-09-29
I guess the first thread should be updated with the latest Humanity changes and screenshots.

---

### Post by Bou on 2009-09-30
Psyke, I've got a couple requests and a couple screenshots in order to make myself clear:

-Could you try using a dark border around letters in the titlebar, instead of a drop shadow? Just to see how it would look.

-Could you make the scrollbar's handle dark gray, and or give it square corners / some dots or stripes in the middle? The current one just looks like a brown blob to me, whatever that could bring to mind. It is the only part of the current gtk theme I haven't been able to get used to.

Please see how the clearlooks theme does those.

---

### Post by Squonk07 on 2009-09-30
> **psyke83 said:**
> Here's a preview of my first real attempt to update the Human metacity borders - notice that the outer frame is now different for focused and unfocused windows. I've sent to Ken and will hopefully hear if this update is appropriate for inclusion :).

I like the gradients on the sides. Reminds me a little of the old Breezy Badger look. I look forward to trying out the final version of this, even if it doesn't make it into the final build of Karmic by default.

---

### Post by cyberkilla on 2009-09-30
> **Bou said:**
> Psyke, I've got a couple requests and a couple screenshots in order to make myself clear:

-Could you try using a dark border around letters in the titlebar, instead of a drop shadow? Just to see how it would look.

-Could you make the scrollbar's handle dark gray, and or give it square corners / some dots or stripes in the middle? The current one just looks like a brown blob to me, whatever that could bring to mind. It is the only part of the current gtk theme I haven't been able to get used to.

Please see how the clearlooks theme does those.

That's what I meant! The border around the title text. Thanks for explaining it better than myself:P

---

### Post by psyke83 on 2009-09-30
> **Bou said:**
> Psyke, I've got a couple requests and a couple screenshots in order to make myself clear:

-Could you try using a dark border around letters in the titlebar, instead of a drop shadow? Just to see how it would look.

Yes, I'll give that a try.

> -Could you make the scrollbar's handle dark gray, and or give it square corners / some dots or stripes in the middle? The current one just looks like a brown blob to me, whatever that could bring to mind. It is the only part of the current gtk theme I haven't been able to get used to.

Please see how the clearlooks theme does those.

The official GTK theme currently looks exactly like -testing2, except the background is slightly tweaked, and has grey scrollbars (shaded to 80% of the background colour); I think you'll like it.

I'm currently tinkering with the Metacity to create a few styles, then I'm going to submit these styles (with screenshots) as a proposal to the DUX team, to see if they would be interested in using any of them.

I'll take into account the feedback from all you folks :).

---

### Post by psyke83 on 2009-09-30
Oh, and the scrollbar trough border will remain in the official theme, thanks to all the folks who have helped with fixing the related bugs :).

---

### Post by screaminj3sus on 2009-09-30
Humanity looks SO much better.

---

### Post by psyke83 on 2009-09-30
Here's a selection of the Metacity proposals I've submitted. The differences are related to the gradient of the surrounding border.

No matter which gets selected, or none at all, I'll make these available in unofficial form. My favourites are proposals 3 and 5. As always, any comments would be appreciated!

P.S. I didn't have time to change the text drop shadow.

---

### Post by shafin on 2009-09-30
No 2 and No 5 looks best to me.

---

### Post by Joe_Bishop on 2009-09-30
Vista style button placement sucks. I prefer chromium-like style (similar to human).

---

### Post by Merk42 on 2009-09-30
Shame 1 and 2 aren't in the same exact location as 3, 4 and 5.
I think I like 1 though, and well you know how I feel about 5.

Maybe part of the hard thing about trying to see what looks good is the title bar? Given its gradient it's like a slight bulge.  Perhaps figuring out the sides would be best done if you did a simple, possibly isometric, sketch of how you picture the entire window to be.

---

### Post by garba on 2009-09-30
just wanted to say thanks to psyke for his great work, it looks damn sweet :) as does the new icon set imo

---

### Post by 6205 on 2009-09-30
I like #1

---

### Post by mrdoob on 2009-09-30
#2 or #3

---

### Post by NCLI on 2009-09-30
2 & 5.

---

### Post by Bou on 2009-09-30
> **Merk42 said:**
> Maybe part of the hard thing about trying to see what looks good is the title bar? Given its gradient it's like a slight bulge.  Perhaps figuring out the sides would be best done if you did a simple, possibly isometric, sketch of how you picture the entire window to be.

My thoughts exactly.

---

### Post by benjamimgois on 2009-09-30
I like #3 . Maybe we should make a poll...

---

### Post by cyberkilla on 2009-09-30
I have been using a theme called "Radial". It is for Emerald, but that's not the point. It has nice min/max/close buttons, gloss on the title bar, plus an example showing title text with a dark border surrounding it.

If it is useful, great. If not, it doesn't matter. I appologise for the terrible screenshot. I've changed my theme again (because I'm a lunatic) so I had to butcher an old screenshot:)

The GTK theme is "glossy", which fits in very well (although you don't get much of a look at it in the screenshot).

---

### Post by cyberkilla on 2009-09-30
> **psyke83 said:**
> Here's a selection of the Metacity proposals I've submitted. The differences are related to the gradient of the surrounding border.

No matter which gets selected, or none at all, I'll make these available in unofficial form. My favourites are proposals 3 and 5. As always, any comments would be appreciated!

P.S. I didn't have time to change the text drop shadow.

Looks like #5 for me:)

---

### Post by Eestlane on 2009-09-30
I would say 1, 2 or 3, because I've never liked the gradient type on fifth even on Vista.

---

### Post by Eestlane on 2009-09-30
I edited one of your ideas in Photoshop. So here's my vision. I don't know if it's possible exactly like that in coding or not, though.

---

### Post by Sand &amp; Mercury on 2009-09-30
Prefer #1 best. 

I think they could all benefit too, from a thinner border.

---

### Post by psyke83 on 2009-10-03
Ok folks,

I'm attaching the Humanity theme v1.0, which includes some of the Metacity designs proposed. As far as I know, the GTK theme will be the same as the official Human GTK theme (which is not yet up-to-date in our repositories), but the Metacity updates may not be included in the default theme.

Once installed, you can click on the "Customize" button for the theme, click the Window Border tab, and choose between three different border types (Glow, Glass and Smooth).

Enjoy!

---

### Post by woodbj on 2009-10-03
> **psyke83 said:**
> Ok folks,

I'm attaching the Humanity theme v1.0, which includes some of the Metacity designs proposed. As far as I know, the GTK theme will be the same as the official Human GTK theme (which is not yet up-to-date in our repositories), but the Metacity updates may not be included in the default theme.

Once installed, you can click on the "Customize" button for the theme, click the Window Border tab, and choose between three different border types (Glow, Glass and Smooth).

Enjoy!
Love IT

---

### Post by benjamimgois on 2009-10-03
Very nice psyke. Just one doubt, the Theme color will be the "Chocolate brown" present on beta or will be this new "brown" of humanity 1.0 ?

---

### Post by psyke83 on 2009-10-03
> **benjamimgois said:**
> Very nice psyke. Just one doubt, the Theme color will be the "Chocolate brown" present on beta or will be this new "brown" of humanity 1.0 ?

As far as I know, the GTK theme you have in the Humanity 1.0 archive will be identical to Human. The new colour scheme and grey scrollbars were selected by Kenneth Wimer. I expect the next update to the "human-theme" package in the repository will contain this update.

However, I'm a little confused to which "chocolate brown" you're referring to. The only change between Human and Humanity (with respect to colours) is the background colour - Humanity's background colour is less grey.

---

### Post by benjamimgois on 2009-10-04
> **psyke83 said:**
> As far as I know, the GTK theme you have in the Humanity 1.0 archive will be identical to Human. The new colour scheme and grey scrollbars were selected by Kenneth Wimer. I expect the next update to the "human-theme" package in the repository will contain this update.

However, I'm a little confused to which "chocolate brown" you're referring to. The only change between Human and Humanity (with respect to colours) is the background colour - Humanity's background colour is less grey.

Well, the window borders colors look diferent to me.

---

### Post by psyke83 on 2009-10-04
> **benjamimgois said:**
> Well, the window borders colors look diferent to me.

Ah, I see.

Window borders = Metacity, not GTK.

As I mentioned, the Metacity update may not become part of the official theme.

---

### Post by benjamimgois on 2009-10-04
> **psyke83 said:**
> Ah, I see.

Window borders = Metacity, not GTK.

As I mentioned, the Metacity update may not become part of the official theme.

Ops. Sorry... Nice work anyway. I'm using humanity 1.0 theme by default now.

---

### Post by Joe_Bishop on 2009-10-05
May be made the same as in the chromium (see the attachment)? I like its border width more than current humanity.

---

### Post by oboedad55 on 2009-10-05
> **Joe_Bishop said:**
> May be made the same as in the chromium (see the attachment)? I like its border width more than current humanity.

If that's the chromium browser, how were you able to change the color scheme? I've still got this sort of electric blue thing going on.

---

### Post by Merk42 on 2009-10-05
> **oboedad55 said:**
> If that's the chromium browser, how were you able to change the color scheme? I've still got this sort of electric blue thing going on.

Go to the wrench, then options, "Set to GTK+ Theme"

---

### Post by oboedad55 on 2009-10-05
> **Merk42 said:**
> Go to the wrench, then options, "Set to GTK+ Theme"

Beautiful, thanks much. That's a little better looking!

---

### Post by Nickedynick on 2009-10-05
Not sure about the colour of the scrollbars (seems too similar to the background for me), but this is much nicer than the new Human. Good work! :)

---

### Post by 6205 on 2009-10-05
Very nice this new Humanity theme. IMO it should be default in Karmic..

---

### Post by Starks on 2009-10-05
Rotation works.

Panel-fitting doesn't...
```
eric@kingfisher:~/mplayer$ xrandr --output LVDS --set PANEL_FITTING full_aspect
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26

```

---

### Post by benjamimgois on 2009-10-08
Seens that Human-theme 0.35 already have the new Humanity updates.

---

### Post by psyke83 on 2009-10-08
> **benjamimgois said:**
> Seens that Human-theme 0.35 already have the new Humanity updates.

The GTK part yes, Metacity no.

---

### Post by 6205 on 2009-10-08
I am not sure about Humanity 1.0 GTK theme.. I thing it should be a bit more brighter. Metacity is OK, very nice, best version is "smooth" because it looks great with Compiz shadows, but GTK should be more brighter, or maybe it needs to decrease saturation a bit..

---

### Post by psyke83 on 2009-10-08
> **6205 said:**
> I am not sure about Humanity 1.0 GTK theme.. I thing it should be a bit more brighter. Metacity is OK, very nice, best version is "smooth" because it looks great with Compiz shadows, but GTK should be more brighter, or maybe it needs to decrease saturation a bit..

Can you suggest a better colour scheme? Remember, this theme is compatible with the Color Picker (Appearances -> Customize -> Colors).

Note that any changes from this point on will remain unofficial... ;).

---

### Post by 6205 on 2009-10-09
I am not sure, i think it's OK after some time using it :)

---

### Post by benjamimgois on 2009-10-09
Psyke, any news from the Metacity update ? or it's too late for such a major theme modification?

---

### Post by psyke83 on 2009-10-09
> **benjamimgois said:**
> Psyke, any news from the Metacity update ? or it's too late for such a major theme modification?

I haven't heard anything, and it's probably too late. I'll let you know if there's any news.

The human-theme package has received some updates (to fix text selection background, and to change the scrollbars), which makes Humanity v1.0 slightly outdated. You can mix the Human controls and Humanity window borders via the "Customize" button of Appearances Preferences to have the best of both worlds.

---

### Post by psyke83 on 2009-10-15
Updated to v1.1 - some small fixes to the GTK theme and widget outlines are improved, particularly dark elements.

Here's screenshots to illustrate the change - you can grab the update from the first post, as always.

Enjoy!

P.S. This update (and the new Metacity designs) will most likely not be included in the default Human theme. There is a slight chance for an update after release, but there are no guarantees.

---

### Post by benjamimgois on 2009-10-15
> **psyke83 said:**
> Updated to v1.1 - some small fixes to the GTK theme and widget outlines are improved, particularly dark elements.

Here's screenshots to illustrate the change - you can grab the update from the first post, as always.

Enjoy!

P.S. This update (and the new Metacity designs) will most likely not be included in the default Human theme. There is a slight chance for an update after release, but there are no guarantees.

Nice Psyke, i give a try with humanity 1.1 plus the actual default metacity color in human theme(chocolate), and it doesn't look good. The Brown is to much dark. The lighter brown that you choose makes the borders looks better. I really would like to see Humanity as the default human-theme.

---

### Post by psyke83 on 2009-10-15
> **benjamimgois said:**
> Nice Psyke, i give a try with humanity 1.1 plus the actual default metacity color in human theme(chocolate), and it doesn't look good. The Brown is to much dark. The lighter brown that you choose makes the borders looks better. I really would like to see Humanity as the default human-theme.

I agree.

Off topic, but the temperature on your screenshot seems quite high. If you have a laptop you may want to open it and remove the evil dust-bunnies ;).

---

### Post by 6205 on 2009-10-15
> **benjamimgois said:**
> I really would like to see Humanity as the default human-theme.

Just give me somebody the e-mails of responsible peoples and i will arange that :)

---

### Post by 6205 on 2009-10-15
> **psyke83 said:**
> updated to v1.1 - some small fixes to the gtk theme and widget outlines are improved, particularly dark elements

SUPR! :) btw, do you think it could look better with W7 like soft list-view headers?
[http://windowsteamblog.com/cfs-filesystemfile.ashx/__key/CommunityServer.Components.PostAttachments/00.00.50.26.86/userprofile1.jpg](http://windowsteamblog.com/cfs-filesystemfile.ashx/__key/CommunityServer.Components.PostAttachments/00.00.50.26.86/userprofile1.jpg)

but in humanity colors of course :|

---

### Post by benjamimgois on 2009-10-15
> **psyke83 said:**
> I agree.

Off topic, but the temperature on your screenshot seems quite high. If you have a laptop you may want to open it and remove the evil dust-bunnies ;).

hauhauhauh... That's a good tip, but this laptop have this temperature level since a bought it. It's a compact model from Philips(13 inches screen), so i thought that it was normal. Anyway i'll take a look.

---

### Post by benjamimgois on 2009-10-15
I just observed one thing, when using the system update the progress bar use the wrong color with Humanity 1.1. Look at screenshots with the comparison with original human theme.

---

### Post by psyke83 on 2009-10-15
> **benjamimgois said:**
> I just observed one thing, when using the system update the progress bar use the wrong color with Humanity 1.1. Look at screenshots with the comparison with original human theme.

The theme is installed to ~/.themes/, which is only available to applications running with your user's credentials. The update manager uses root privileges, therefore you need to move the theme to /usr/share/themes. The specific instructions are in the first post.

---

### Post by psyke83 on 2009-10-15
How would you folks feel if the Metacity border was reduced by 1 pixel on each side? Screenshot attached.

---

### Post by Regenweald on 2009-10-15
> **psyke83 said:**
> How would you folks feel if the Metacity border was reduced by 1 pixel on each side? Screenshot attached.
I'd feel good.

---

### Post by QQi on 2009-10-16
Humanity v1.1 missing Metacity theme ?

---

### Post by psyke83 on 2009-10-16
> **QQi said:**
> Humanity v1.1 missing Metacity theme ?

Yep. Fixed in v1.2.

---

### Post by PiotrekS on 2009-10-16
New theme sucks :/ It's ****-like theme... I hate bronze...

---

### Post by 6205 on 2009-10-16
**[COLOR="DarkRed"]Can somebody please make a pool? If we want have current Human theme or replace it by default by full Humanity theme (Metacity+GTK+icons) IMO it should be changed to Humanity before RCgets released. It's not too late if many people will support this change. YES WE CAN :)))[/COLOR]**

---

### Post by Podex on 2009-10-16
Making a poll on this forum won't change anything I think. Maybe make a FFe bug report, or have you already done that psyke83?

---

### Post by benjamimgois on 2009-10-16
Great, Humanity Theme is becoming very pleasant on the eyes. Common canonical, one last update !

---

### Post by 6205 on 2009-10-23
I have small problem with this theme, trash applet have cropped icon. [https://bugs.launchpad.net/humanity/+bug/455846](https://bugs.launchpad.net/humanity/+bug/455846)

It is related to GTK theme, or icon theme Humanity?

---

### Post by psyke83 on 2009-10-24
> **6205 said:**
> I have small problem with this theme, trash applet have cropped icon. [https://bugs.launchpad.net/humanity/+bug/455846](https://bugs.launchpad.net/humanity/+bug/455846)

It is related to GTK theme, or icon theme Humanity?

I don't see any cropping on my system or the screenshot you posted to the bug report...

None of the panel theming has changed, so if there is a bug, it's with the Humanity icons (not associated with me), or the gnome-panel.

---

### Post by 6205 on 2009-10-24
If you look very closely at trash applet, bottom 1 pixel from icon is cutoff. Even better visible it is when you adjust panel height to 25pixels when is icon fully visible. Hard to say what causes this, but bug remains open..

---

