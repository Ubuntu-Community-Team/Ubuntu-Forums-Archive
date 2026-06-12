---
title: "How to remove duplicate entries from the &quot;open with&quot;-dialog?"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dominator86 on 2009-09-23
Hello!

I have the problem that Gnome's "open with"-dialog gets crowded with duplicate entries.

I'm posting in the Karmic forum because I didn't observe this behaviour in Jaunty.

Does anyone know how to remove the duplicate entries and how to prevent the dialog from getting crowded again?

---

### Post by dinxter on 2009-09-23
right click on file, choose properties, go to open with tab
should change things for all files of that type

---

### Post by Dominator86 on 2009-09-23
I don't really understand how that should solve my problem with the duplicate entries.

---

### Post by dinxter on 2009-09-23
> **Dominator86 said:**
> I don't really understand how that should solve my problem with the duplicate entries.
apologies, your absolutely right, i got the wrong end of the stick there

---

### Post by sisco311 on 2009-09-23
never mind

---

### Post by MacUntu on 2009-09-23
Best guess: you get an entry for every link, so if you have linked jpg, gif, and png to Gimp you'll have three Gimps in there. If that's the case it's a bug and should be fixed.

---

### Post by dinxter on 2009-09-23
seems to be an issue with multiple entries with the same names but running different parameters, i dont know how to remove them unfortunately, apart from deleting lots of things that shouldnt be deleted

---

### Post by Dominator86 on 2009-09-23
> **MacUntu said:**
> Best guess: you get an entry for every link, so if you have linked jpg, gif, and png to Gimp you'll have three Gimps in there. If that's the case it's a bug and should be fixed.

I don't know how to find the cause for this.
From the default Ubuntu applications only Brasero and the Remote Desktop Viewer(don't know the english name) seem to be affected for now.

The biggest problem is wine because it seems to create multiple entries for every application I install.
I'm using the wine1.2 package from the repositories.

---

### Post by dinxter on 2009-09-23
you could fiddle with multiple entries in 
~/.local/share/applications 
i suppose
at least right-click->open-with can be edited to suit so its not so bad, maybe not ideal though

---

### Post by Dominator86 on 2009-09-23
> **dinxter said:**
> you could fiddle with multiple entries in 
~/.local/share/applications 
i suppose
at least right-click->open-with can be edited to suit so its not so bad, maybe not ideal though

Thanks! That did the trick for me!
The directory was full with entries related to wine.

I found the other duplicate entries in /usr/share/applications but they indeed differ in case of parameters, it's just that they are labelled the same.
Maybe that should be changed to prevent misunderstandings.

It could also be a problem with the localization.

---

### Post by dinxter on 2009-09-23
it does seem a little strange that you can choose from a whole host of similarly named open-with-other entries with no clue as to what the different parameters they use is

---

### Post by Dominator86 on 2009-09-23
I think the "open with"-dialog shows the wrong strings.

Here the two Brasero entries as an example:
```

[Desktop Entry]
Name=Brasero
GenericName=Disc Burner
Comment=Create and copy CDs and DVDs
Categories=GNOME;AudioVideo;DiscBurning;
MimeType=application/x-cd-image;application/x-cdrdao-toc;application/x-cue;application/x-toc;audio/x-scpls;audio/x-ms-asx;audio/x-mp3-playlist;audio/x-mpegurl;application/x-brasero;
Exec=brasero %U
Icon=brasero
StartupNotify=true
Terminal=false
Type=Application
X-GNOME-FullName=Brasero Disc Burner
<bunch of localized strings...>

```

```

[Desktop Entry]
Name=Brasero
GenericName=Disc Copier
Comment=Copy CDs and DVDs
Exec=brasero -c %u
Icon=brasero
MimeType=x-content/audio-cdda;x-content/video-dvd;x-content/video-vcd;x-content/video-svcd;x-content/image-picturecd;
StartupNotify=true
Terminal=false
Type=Application
NoDisplay=true
OnlyShowIn=GNOME;
X-GNOME-FullName=Brasero Disc Copier
<bunch of localized strings...>

```

So the dialog always shows "Name" instead of "X-GNOME-FullName" or the localized strings.

IIRC it showed the localized strings in Jaunty. Can anyone confirm this?

Btw, how can I mark this thread as solved?

---

### Post by bruno9779 on 2009-09-23
I have the same issue in Jaunty.
and i recall having it in Intrepid too

---

### Post by sisco311 on 2009-09-23
> **Dominator86 said:**
> 
Btw, how can I mark this thread as solved?

Thread Tools -> Mark this thread as solved.

(see the link in my signature)

---

### Post by dinxter on 2009-09-23
hmmm....

gnome-panel (1:2.27.92-0ubuntu1) karmic; urgency=low

  * New upstream version:
    Panel
    - Use display name instead of name for menu items
      This implies we now support the X-GNOME-FullName key.

---

### Post by Dominator86 on 2009-09-23
So, is this behaviour wanted or should we consider this a bug?


> **sisco311 said:**
> Thread Tools -> Mark this thread as solved.

(see the link in my signature)

Thanks!

---

### Post by dinxter on 2009-09-23
i take it this is nautilus thats in control of open-with?

---

### Post by dinxter on 2009-09-23
i see from 
[http://live.gnome.org/GnomeGoals/CorrectDesktopFiles](http://live.gnome.org/GnomeGoals/CorrectDesktopFiles)
that nautilus is still on the todo list, maybe that'll sort the problem once they've worked through that

---

### Post by Dominator86 on 2009-09-23
> **dinxter said:**
> i take it this is nautilus thats in control of open-with?

[s]I don't know.[/s]
Edit: Yes, it's Nautilus.

It's strange that X-GNOME-FullName wasn't used in first place.

---

### Post by dinxter on 2009-09-23
[https://bugzilla.gnome.org/show_bug.cgi?id=588975](https://bugzilla.gnome.org/show_bug.cgi?id=588975)
seems like the relevant gnome bug, i think whats being done is designed to fix exactly the situation described here, i think....

---

### Post by Dominator86 on 2009-09-23
> **dinxter said:**
> [https://bugzilla.gnome.org/show_bug.cgi?id=588975](https://bugzilla.gnome.org/show_bug.cgi?id=588975)
seems like the relevant gnome bug, i think whats being done is designed to fix exactly the situation described here, i think....

For me it seems more like a specification of how desktop files should look like.

Edit: All the files in /usr/share/applications already implement X-GNOME-FullName, but it's not used by the dialog.

---

### Post by dinxter on 2009-09-23
looks like libgnome-desktop-2-11 only supports Name and Generic name at the moment, i guess itll require X-GNOME-FullName (or  FullName) support before this works properly, if i'm right in thinking that nautilus uses this lib for .desktop file processing. its too late in the day to be sure i'm paying enough attention to the screen :) 

[EDIT] The fact I just edited over my last entry instead of posting a new one by mistake shows you its too late in the day, i better go for a coffee...

---

