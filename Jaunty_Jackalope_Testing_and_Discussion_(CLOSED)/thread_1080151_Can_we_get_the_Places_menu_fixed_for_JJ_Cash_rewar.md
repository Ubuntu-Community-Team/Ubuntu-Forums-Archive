---
title: "Can we get the Places menu fixed for JJ? Cash reward*."
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-02-25
The places menu is a long-running usability bug. If you have more than five (I think) items in either the bookmarks or drives section, they will truncate into separate levels. [See screenshot and my accompanying rant]("http://www.thepcspy.com/read/my_issues_with_linux_et_al") (first item).

*I know this is a Gnome issue* but there's been a bug entry logged against it since 2007 (there might be earlier duplicates that I haven't seen) and nothing appears to have been done about it.

I also realise this is here for good reason. Nobody wants a scrolling places menu (well they might, I'm not sure having never seen it)

[SIZE="5"]**What am I suggesting?**[/SIZE]

How about we start by increasing the silly-hard-coded truncation limit to ~8 items? Quick patch. Easily done. Easily tested on various resolutions. Why? Because 5 items is an insanely low expectation for a power-user.

The second way to make things nicer would be to move that hard-coded value out into the open. Make it a gconf-editable value.

Then there's the clever way. It must be possible to detect if a menu is larger than the screen height (or the scrolling-panels wouldn't exist) - so why don't we do that? Detect to see if it's too tall, then see what could be truncated, and truncate it. (Or just use a scroller; it might not be that bad.)

[SIZE="5"]***The reward**[/SIZE]

This silly little bug has irked me for too long. If you can get a patch out and magically accepted into Ubuntu's gnome-panel version (or both upstream and in ubuntu - ie something that I'll be able to use without having to recompile gnome here every week), I'll donate £30 to a charity of your choice.

And if you wake up in cold sweats about this bug, but like me can't contribute to its fix programmatically, I invite you to add your bounty.

---

### Post by BobCFC on 2009-02-25
This used to bother me.  Funny I just read a blog post about how to patch it in my RSS feeds [http://blogs.linux.org.bd/?p=24387](http://blogs.linux.org.bd/?p=24387)

Haven't tried it yet because I'm running Jaunty so packages are getting replaced every day. Basically you just change one line and rebuild the panel.

> Linux Blog Aggregator
Howto Display more than 5 bookmarks in gnome-panel &#8220;Places&#8221; menu
February 22nd, 2009 by admin

1) Open Terminal

2a) Install apt-build

sudo apt-get update
sudo apt-get install apt-build

2b) Configure apt-build:

* Optimization level: Medium
* Add apt-build repository to sources.list: Yes
* Architecture: SELECT YOUR ARCHITECTURE

3) Install files required to build gnome-panel from source and download the source

sudo apt-get build-dep gnome-panel
sudo apt-build source gnome-panel

4) Navigate to the downloaded gnome-panel source folder and open the menu items file

cd /var/cache/apt-build/build/gnome-panel-*
sudo gedit gnome-panel/panel-menu-items.c

5) Set the the maximum number of bookmarks to display before placing them in the Bookmarks submenu

Find the line:
PHP Code:
if (g_slist_length (add_bookmarks) <= MAX_ITEMS_OR_SUBMENU) {
and replace it with:
PHP Code:
if (g_slist_length (add_bookmarks) <= 20) {
Save the file.

6) Install the modified gnome-panel and restart it

sudo ./configure
sudo make
sudo make install
killall gnome-panel

---

### Post by MacUntu on 2009-02-25
Too many entries would only confuse people. :lolflag:

---

### Post by klange on 2009-02-25
Here's another fix we need: Show the right icons from the current set for folders on the places menu.
I manually fixed this on my laptop a while back by copying some icons to the right paths.

---

### Post by olskar on 2009-02-25
> **WindowsSucks said:**
> Here's another fix we need: Show the right icons from the current set for folders on the places menu.
I manually fixed this on my laptop a while back by copying some icons to the right paths.

Isn't that a bug with the iconset being used rather then Ubuntu/Gnome?

---

### Post by klange on 2009-02-25
> **olskar said:**
> Isn't that a bug with the iconset being used rather then Ubuntu/Gnome?
No, it's a bug with the Places menu looking for non-standard icons.

---

### Post by olskar on 2009-02-25
> **WindowsSucks said:**
> No, it's a bug with the Places menu looking for non-standard icons.

I see, can you tell me how you worked around it? Suffering from it too :(

---

### Post by klange on 2009-02-25
> **olskar said:**
> I see, can you tell me how you worked around it? Suffering from it too :(

I created about 10 different symlinks for the new names in the theme I use. Check the 'gnome' theme for the right names.

---

### Post by OliW on 2009-02-25
> **BobCFC said:**
> This used to bother me.  Funny I just read a blog post about how to patch it in my RSS feeds [http://blogs.linux.org.bd/?p=24387](http://blogs.linux.org.bd/?p=24387)

Haven't tried it yet because I'm running Jaunty so packages are getting replaced every day. Basically you just change one line and rebuild the panel.

That's my point. I know the code is stupidly simple to edit... So why can't we have a sensible number applied and kept as an Ubuntu patch? Or move the infernal variable to gconf to allow people to set their own limits?

---

