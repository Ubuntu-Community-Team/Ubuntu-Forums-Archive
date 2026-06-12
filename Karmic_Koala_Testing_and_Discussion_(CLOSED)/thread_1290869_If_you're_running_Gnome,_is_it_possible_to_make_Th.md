---
title: "If you're running Gnome, is it possible to make Thunar the default..."
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jim March on 2009-10-14
...instead of Nautilus?

Because using the -14 kernel and all the latest updates, Nautilus is flat unusable...crashes the instant you try and use it.  Go to Applications>Accessories>Thunar and all is well.

Is there a way to make Thunar control, say, the desktop icons as well?

Other than, of course, switching to XFCE/Xubuntu...

Sidenote: PCManfm is also borked.  It's "sorta usable" except it can't track what data file types go with which apps.  It'll try and load a PDF as a text file for example.  Not as badly hosed as "insta-freeze" Nautilus but still.  I've got LXDE as an alternate desktop and I have to use Thunar there too.

My graphics is Intel-based (965/x3100) if that matters.

---

### Post by woodbj on 2009-10-14
From my fav ubuntu blog [http://www.omgubuntu.co.uk/2009/10/try-thunar-sleek-lightweight-file.html](http://www.omgubuntu.co.uk/2009/10/try-thunar-sleek-lightweight-file.html)

> Installing Thunar does not remove Nautilus so feel free to try it and see if you prefer it.
Installation
You can install Thunar using Add/remove, Synaptic, Ubuntu Software Centre or  the good old fashion terminal: -

    * sudo apt-get install thunar

Once installed you can launch it from the Applciations > Accessories menu.
Setting it as default file manager
If you decide that you like using Thunar and would prefer to use it for browsing your files and folders, you can set it to be used instead of Nautilus.

Download this script and save it to your home directory
Make it executable

    * chmod +x defaultthunar

run the script

    * ./defaultthunar

Switching back
To revert back to nautilus as default file manager simply run the script again: -

    * ./defaultthunar

---

### Post by emarkay on 2009-10-14
Cool, Thunar has the "rename multiple files" feature I have loved so much in Windows.

---

### Post by Jim March on 2009-10-14
Cool.  But the actual script referred to isn't in the link you gave, it's at:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by Jim March on 2009-10-14
[FONT="Arial Black"][SIZE="7"][COLOR="Red"]DO NOT DO THIS SCRIPT IN KARMIC!  Huge heap of fail!!!!!!!![/COLOR][/SIZE][/FONT]

---

### Post by Joe_Bishop on 2009-10-14
Lol

---

### Post by darrenn on 2009-10-14
> DO NOT DO THIS SCRIPT IN KARMIC! Huge heap of fail!!!!!!!!

Then I would suggest switching to hardy for the time being. It works PERFECTLY with a acer 3680 extremely STABLE. Never CRASHES! Hardy is definitely one of the best releases ever.

---

### Post by emarkay on 2009-10-14
> **Jim March said:**
> .....HEAP Of ...... !!!!!

Um, if you are going to be so utterly obnoxious with your wording, text size and colour, could you at least explain WHY? 
Otherwise, please refrain from using drama; it's oh so annoying...  :)

---

### Post by joey-elijah on 2009-10-14
> **emarkay said:**
> Um, if you are going to be so utterly obnoxious with your wording, text size and colour, could you at least explain WHY? 
Otherwise, please refrain from using drama; it's oh so annoying...  :)

I agreee. I've used it in nothing but Karmic and i've never had an issue...

I don't mind people informing others of issues they have, but to assume just because something doesn't work for you then it won't work for anyone else gets boring (and isn't helpful!)

---

### Post by Jim March on 2009-10-14
Well for starters, every item in the "places" drop-down menu leads to a search window instead of a place :).

Then when I went to do "undo" (repeat the script) it locks up mid-way through.  Turns out it DOES put Nautilus back in before puking, which I didn't realize at the time I put the warning up.  I thought it was more important to get the warning out than to continue trying to unbork my machine - by all appearances, it was screwed up pretty bad.  Turns out not as bad as it appeared at the time, but...still, guaranteed, this script fails with Karmic.  I have no idea why or what's different in Karmic that would affect the script...

---

