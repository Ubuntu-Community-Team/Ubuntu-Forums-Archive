---
title: "Missing Icons In Menu Bar"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-02-26
Installed Alpha 3. All wen flawlessly (dual booting with Vista), though I'm missing icons in the menu bar. I remember there was an option of some sort under *appearance preferences* in Karmic to add the icons missing. How is this done in Lucid?

[IMG]http://i49.tinypic.com/2r7apmw.jpg[/IMG]

---

### Post by kansasnoob on 2010-02-26
Look at the **Re-Enable Button Icons In Gnome 2.28** section of this:

[http://www.omgubuntu.co.uk/2009/10/missing-system-icons-ubuntu-karmic.html](http://www.omgubuntu.co.uk/2009/10/missing-system-icons-ubuntu-karmic.html)

The Gnome devs removed the Interface tab from Appearance Preferences.

---

### Post by ankspo71 on 2010-02-26
Hi,
The option is in the gnome configuration editor.
Press Alt+F2 and type '  gconf-editor  '
Then when it opens,  navigate to:
/desktop/gnome/interface/menus_have_icons  
Check the box to enable it.

---

### Post by Uncle Spellbinder on 2010-02-26
Thanks for the info guys. 

Seems odd to remove an easy way to add the icons. Seems they should be there by default. Why include some, but not all the icons? Odd, if you ask me.

---

### Post by Robin Nixon on 2010-02-26
> **ankspo71 said:**
> Hi,
The option is in the gnome configuration editor.
Press Alt+F2 and type '  gconf-editor  '
Then when it opens,  navigate to:
/desktop/gnome/interface/menus_have_icons  
Check the box to enable it.

That did the trick!

---

### Post by joey-elijah on 2010-02-26
> **Uncle Spellbinder said:**
> Thanks for the info guys. 

Seems odd to remove an easy way to add the icons. Seems they should be there by default. Why include some, but not all the icons? Odd, if you ask me.

The reasons behind the decision are quite a thorny issue atm. The GNOME devs say this on the matter: -

> Discussed many times. *[regarding the missing icons]*  We should remove the interface tab.  Basically everthing  there is a user experience design cop-out.  It only belongs in a  tweak UI tool &#8211; but only if someone cares enough to write one.

I won't go into the rest here as it's slightly off topic but i blogged about it yesterday @ [http://www.omgubuntu.co.uk/2010/02/missing-menu-icons-what-are-gnome.html](http://www.omgubuntu.co.uk/2010/02/missing-menu-icons-what-are-gnome.html)

Out of 1,115 votes in our poll on the removal, 84% of people would prefer having the option to re-enable all icons in menus kept where it was.

---

### Post by ranch hand on 2010-02-26
And then there are folks like me that wonder why there are still some icons there and can't figure out how to get rid of them.

There has to be a better way, or at least a complete way to handle this so that the religious folks that like to worship things on their menu can do so and agnostics, like me, can do with out the benefits of menu religion.

And, as was said by Uncle Spellbinder, it really is silly to leave some and remove the rest.  The command should leave them all there or remove all of them.  Anything else, such as the current case, is just irritating to everyone.

---

### Post by andrewabc on 2010-02-26
This is going to be a disaster. I wonder how many threads will be created after final release of people asking where the menu icons are, and why some have them and others don't.

Stupidest idea ever. Either remove all, or keep all. Most importantly make a simple option to enable or disable them.

Nope, has to be done most difficult way possible, no simple option, and only some icons showing. wtf?

So they eventually want no icons in menus? Just text?

Dunno about others but I associate icons moreso than text. Easier to see/recognize. similar to avatars on forums. I can identify a user by their avatar, quicker than reading their username.

Yet another usability tweak I have to remember.
I assume they still have the stupid 60 second shutdown timer?

---

### Post by Uncle Spellbinder on 2010-02-26
> **andrewabc said:**
> This is going to be a disaster. I wonder how many threads will be created after final release of people asking where the menu icons are, and why some have them and others don't.

Stupidest idea ever. Either remove all, or keep all. Most importantly make a simple option to enable or disable them.

100% spot on.

---

### Post by kulight on 2010-03-04
thank you for the solution...(works great)

did any one opened a bug for this annoying situation?

---

### Post by NetJonte on 2010-03-06
They should add back the icons as default. Not only does the icons allow us to faster recognize menu items and buttons without reading the text, but this is totally crucial for people who have trouble reading and for children who still haven't learn to read (yes, they use computers too).

No other OS I have heard of have removed the icons. Might so be that GNOME have had more icons than most other, but removing them all together is just plain stupid.

Thanks for the instructions of how to add them back. Now I'm able to use NoScript's menu again. And I seriously hope they do something about this.

---

### Post by mpt on 2010-03-06
> **NetJonte said:**
> No other OS I have heard of have removed the icons.

I’m surprised that you’ve never heard of Windows, Mac OS X, or Fedora. Each of those OSes has menus with about as few icons in them as Ubuntu now has. (The main exception to this used to be Microsoft Office on Windows, but that doesn’t even have a menu bar any more. Microsoft Office on Mac has [always]("http://www.odbc.net/images/screens/ms/excel.gif") had [mostly-iconless menus]("http://www.vletter.com/graphics/insert_in_excelMac.gif").)

It is true that Windows and Mac OS X haven’t “removed” “the” icons, because they never had “the” icons in the first place. But Fedora has cut back in exactly the same way that Ubuntu has. (I assume Debian has too, but I haven’t tried it myself.)

> *Might so be that GNOME have had more icons than most other, but removing them all together is just plain stupid.*

What gave you the false impression that we’re removing them altogether?

---

### Post by NetJonte on 2010-03-07
> **mpt said:**
> 
I’m surprised that you’ve never heard of Windows, Mac OS X, or Fedora. Each of those OSes has menus with about as few icons in them as Ubuntu now has.


My Windows 7 definitely got menu icons and so did XP. And Fedora is also based on GNOME so they should be affected by the same problem/feature as Ubuntu is now.

> **mpt said:**
> 
What gave you the false impression that we’re removing them altogether?

Like even NoScript and CookieSafe extensions in Firefox lost its icons.

---

### Post by mpt on 2010-03-07
> **NetJonte said:**
> My Windows 7 definitely got menu icons and so did XP.

Sure, about as much as Ubuntu does now. (Maybe a bit more, in poorer-designed software. We’re lucky with Gnome at the moment that we can share design guidelines more easily than Windows application vendors do.)

> And Fedora is also based on GNOME so they should be affected by the same problem/feature as Ubuntu is now.

Exactly.

> *Like even NoScript and CookieSafe extensions in Firefox lost its icons.*

None of NoScript’s or CookieSafe’s menu items fall into the category of items that should have icons. But other items do — for example most of the items in the “Bookmarks” menu in Epiphany or Firefox, the “Open With” submenu and the “Places” menu in Nautilus, and the Me menu in Ubuntu.

---

### Post by NetJonte on 2010-03-08
Ok. Is there anywhere I can read a good explanation why the icons where removed by default and what the real advantages of doing so is compared to the disadvantages?

From what I read it only seems to be about saving space in the GUI, and because someone think that either all menus got icons (which is pretty much impossible) or none (except bookmarks and the like).

I am still used to using the icons do identify menu items and OK/Cancel/Save buttons and the like. It is faster than reading the text (I'm reading slow by the way).

> **mpt said:**
> 
None of NoScript&#8217;s or CookieSafe&#8217;s menu items fall into the category of items that should have icons.


According to the new design goals you are probably right. I was just thinking that they shouldn't have been removed because it was third-party applications (rather plugins).

---

### Post by mpt on 2010-03-08
> **NetJonte said:**
> Ok. Is there anywhere I can read a good explanation why the icons where removed by default and what the real advantages of doing so is compared to the disadvantages?

The main writeup at the moment is [from Andreas Nilsson]("http://www.andreasn.se/blog/?p=103"), though it doesn’t go into much detail. There will be updated Human Interface Guidelines soon too.

> *From what I read it only seems to be about saving space in the GUI*

Partly that, but mostly about about becoming more elegant.

> *I am still used to using the icons do identify menu items and OK/Cancel/Save buttons and the like. It is faster than reading the text (I'm reading slow by the way).*

There are a few other things we can do to help you there. One is making sure that the default button (like “OK” or “Save”) looks quite different from the others. Another is improving the font (the new Ubuntu font will hopefully be easier to read). Another is shortening labels when possible (e.g. using “Discard” instead of “Close Without Saving”).

---

### Post by cyberkilla on 2010-03-09
Personally, I'm liking the less bloated menus. It makes sense to me. What does NOT make sense is that you used to be able to disabled them ALL. Now, you can only disable some of them, yet the check box doesn't explain that.

---

### Post by NetJonte on 2010-03-09
Thanks for the answer mpt.

I'm starting to see now why they was removed and how things are going to be done instead. GNOME and Ubuntu have always had a good easy-to-use interface so although I can't really support this design decision until I see the final results I guess it will turn out good.

---

