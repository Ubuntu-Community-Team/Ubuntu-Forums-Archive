---
title: "Indicator Applet Session-How to remove &quot;Chat&quot; icon next to Username?"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-21
Some of us aren't "chatty" and it's just clutter...

---

### Post by 23meg on 2010-03-21
Do you want to keep the username and the rest of the functionality, and just remove the icon?

---

### Post by tica vun on 2010-03-21
Yes, I"m wondering about this as well. The identi.ca client is great, but I"m not liking anyone who look at my monitor too see my user name.

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> Do you want to keep the username and the rest of the functionality, and just remove the icon?

Correct

Hmm, I betcha it's like the silly "envelope & speaker" (Indicator Applet) icon change: "Oh BTW, we changed how it works but didn't tell anyone except those "in the know".  

IMHO there needs to be ONE place where fundamental/obvious/interface/usability changes are noted here...

---

### Post by 23meg on 2010-03-21
I may be misunderstanding this, but if you're sure you just don't want the status icon displayed on the panel itself, but want the rest of the IM and broadcast features in the Me Menu, there's no practical way to do that, except perhaps removing the icon from the icon theme, or modifying the source.

If, on the other hand, you don't want *anything* to do with IM and broadcast, the applet should not display those features unless accounts are configured, as per [the specification]("https://wiki.ubuntu.com/MeMenu"). That it does at the moment is a bug.

And if all else fails, remove the indicator-me package, and add the "User Switcher" applet to your panel, and see if you like that.

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> 
If, on the other hand, you don't want *anything* to do with IM and broadcast, the applet should not display those features unless accounts are configured, as per [the specification]("https://wiki.ubuntu.com/MeMenu"). That it does at the moment is a bug.

Thanks 

Do you have a Bug# so I an subscribe? 

Yes, I have removed the unneeded packages in question and still see the icon.  
(Sorry, when you said "functionality" I presumed you meant of the username -  then I inferred you meant the IM programs too.)

---

### Post by 23meg on 2010-03-21
> **emarkay]Do you have a Bug# so I an subscribe? [/QUOTE]

[Bug #520932]("https://bugs.launchpad.net/ubuntu/+source/indicator-me/+bug/520932") covers the text field part, but the rest are written in the specification, so don't worry said:**
> Yes, I have removed the unneeded packages in question and still see the icon. 

You shouldn't, once the applet is reinitialized.

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> []("https://bugs.launchpad.net/ubuntu/+source/indicator-me/+bug/520932")You shouldn't, once the applet is reinitialized.

I think I removed all relevant packages...  But even after a reboot I get the following:

---

### Post by 23meg on 2010-03-21
Please post the output of ```
apt-cache policy indicator-me
```

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> Please post the output of ```
apt-cache policy indicator-me
```

indicator-me:
  Installed: 0.2.5-0ubuntu2
  Candidate: 0.2.5-0ubuntu2
  Version table:
 *** 0.2.5-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status

---

### Post by 23meg on 2010-03-21
You haven't removed the indicator-me package; remove it.

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> You haven't removed the indicator-me package; remove it.

"And if all else fails, remove the indicator-me package, and add the  "User Switcher" applet to your panel, and see if you like that." - I didn't think it got to that point, but therefore, I did this and well, OK, but now, how can I get my Username where it was - to the **right** of the date?  :)

Still a convoluted solution for what should be a simple problem - separate the Username form the Chatting Indicator...

---

### Post by 23meg on 2010-03-21
> **emarkay said:**
> "And if all else fails, remove the indicator-me package, and add the  "User Switcher" applet to your panel, and see if you like that." - I didn't think it got to that point, but therefore, I did this and well, OK, but now, how can I get my Username where it was - to the **right** of the date?  :)

Just middle-click and drag the applet to wherever you want. If any applets block it, make sure they aren't locked to the panel.

> **emarkay said:**
> Still a convoluted solution for what should be a simple problem - separate the Username form the Chatting Indicator...

As I said, it's planned that if you haven't configured any broadcast or IM accounts, the corresponding "chatting" parts shouldn't appear. You probably won't have to worry about this in the final release.

And since most of the functionality of the "User Switcher" applet is covered by indicator-session as well, why not just use that?

---

### Post by emarkay on 2010-03-21
> **23meg said:**
> Just middle-click and drag the applet to wherever you want. If any applets block it, make sure they aren't locked to the panel.
As I said, it's planned that if you haven't configured any broadcast or IM accounts, the corresponding "chatting" parts shouldn't appear. You probably won't have to worry about this in the final release.

Sorry to belabor this, but the "HP" icon for HPLIP, and the "Network Manager Applet" are to the left of the selectable, movable "Time Applet", but those two can not apparently be moved, and therefore I can't move them to the left, move the "Time Applet" or "jump" the "User Switch Applet" over them.  :(

Will let it go for now, and I am sure it will be resolved by RC time, too.

---

### Post by 23meg on 2010-03-21
> **emarkay said:**
> Sorry to belabor this, but the "HP" icon for HPLIP, and the "Network Manager Applet" are to the left of the selectable, movable "Time Applet", but those two can not apparently be moved, and therefore I can't move them to the left, move the "Time Applet" or "jump" the "User Switch Applet" over them.  :(

Right click the empty space slightly to the left of the left-most icon, and untick "Lock to Panel".

---

### Post by emarkay on 2010-03-22
Thanks!

However, in this display mode, one can not see** anything** between the icons.

See the enlarged screencap.

Also strange that the "HP" and "Network" icons are linked...   Again, I am sure there's a reason... :) 

Much appreciated!

---

### Post by 23meg on 2010-03-22
> **emarkay said:**
> Thanks!

However, in this display mode, one can not see** anything** between the icons.

See the enlarged screencap.

That's because the default theme renders notification area and indicator applet handles as invisible; it arguably results in a more visually pleasing effect with less clutter, but the downside is the reduced discoverability of moving things around. 

> **emarkay said:**
> Also strange that the "HP" and "Network" icons are linked...   Again, I am sure there's a reason... :) 

The reason is that they're both running in the notification area; that's the way the notification area has always worked.

---

