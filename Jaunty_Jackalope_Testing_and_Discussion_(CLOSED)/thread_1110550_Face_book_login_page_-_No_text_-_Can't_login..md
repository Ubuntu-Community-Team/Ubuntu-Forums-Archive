---
title: "Face book login page - No text - Can't login."
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-03-29
Has anyone else got problems with facebook? My kids brought it to my attention that they can't use facebook with Jaunty. It works perfectly in Hardy and Intrepid.

Thanks

---

### Post by damis648 on 2009-03-29
Upgraded to Jaunty beta two days ago, no problems. Maybe if you could post a screenshot?

---

### Post by crjackson on 2009-03-29
added

---

### Post by FuturePilot on 2009-03-29
Wow that's really odd. It's fine here though. Maybe something wrong with your profile or one of your settings.

---

### Post by damis648 on 2009-03-29
> **FuturePilot said:**
> Wow that's really odd. It's fine here though. Maybe something wrong with your profile or one of your settings.

Yea... maybe try renaming your ~/.mozilla folder, see if a default config for firefox fixes it.

---

### Post by crjackson on 2009-03-29
> **damis648 said:**
> Yea... maybe try renaming your ~/.mozilla folder, see if a default config for firefox fixes it.

No it didn't change.  HOWEVER running firefox through terminal with gksu worked perfect.

Something is amiss...

---

### Post by damis648 on 2009-03-29
> **crjackson said:**
> No it didn't change.  HOWEVER running firefox through terminal with gksu worked perfect.

Something is amiss...

:-k:-k:-k
Wait... does root share your theme (is your current theme installed to /usr/share/themes or ~/.themes?)

---

### Post by crjackson on 2009-03-29
> **damis648 said:**
> :-k:-k:-k
Wait... does root share your theme (is your current theme installed to /usr/share/themes or ~/.themes?)

No, but I switched to the default Human Theme and it still did the same.

The theme is default but with custom window, icons, and color

Got to run for the night. I'll get on it tomorrow again.

---

### Post by crjackson on 2009-03-30
Okay, back looking for answers after a little sleep.

---

### Post by dBuster on 2009-03-30
Since it is working for me all I have is a stab in the dark...

Font size have anything to do with it?  Overriding the css from that page?

---

### Post by crjackson on 2009-03-30
> **dBuster said:**
> Since it is working for me all I have is a stab in the dark...

Font size have anything to do with it?  Overriding the css from that page?

how do you do that? Are you saying to set a fixed font?

---

### Post by dBuster on 2009-03-30
> **crjackson said:**
> how do you do that? Are you saying to set a fixed font?

Is it trying to use a system font that may be borked to 133.3333 font size?  I know that hosed me for a little bit.  Or even in FF the change font size option.  Could be the character encoding was changed also to a font that is not there... 

Just throwing things out there to check...

---

### Post by crjackson on 2009-03-30
> **dBuster said:**
> Is it trying to use a system font that may be borked to 133.3333 font size?  I know that hosed me for a little bit.  Or even in FF the change font size option.  Could be the character encoding was changed also to a font that is not there... 

Just throwing things out there to check...

So far nothing...  The fact that gksu firefox in a terminal seems to imply it's a user configuration, so I'm going to play with that tonight when I get home from work.

If messing with themes and extensions won't work, I'll make a new user profile and see if it's all good there.  I would like to know the culprit though.

---

### Post by dazzler on 2009-03-30
I havent got an answer but a friend of mine had this issue the other day, he was using firefox on a windows machine.

It did however load fine in ie, so i simply installed ietab extension and made it load facebook with explorers backend.

---

### Post by crjackson on 2009-03-30
> **dazzler said:**
> I havent got an answer but a friend of mine had this issue the other day, he was using firefox on a windows machine.

It did however load fine in ie, so i simply installed ietab extension and made it load facebook with explorers backend.

That's strange. It loads fine on Hardy, Intrepid, and Jaunty as root. I THINK the answer will be making a new user and moving everything over. I have no idea what caused this, but I'll report back after more testing.

---

### Post by crjackson on 2009-03-31
Well, changing themes didn't work. Making another user/profile didn't work. The only thing that works is running Firefox as root and I don't want to do this. If I can't get this sorted, it will be a deal breaker on the kids machines.

When the full release comes out, perhaps it will work fine.

---

### Post by crjackson on 2009-03-31
Okay, I think it's a font issue. How do I re-install all my fonts?

I found a drop down box on the site that seems to change the language and when a Chinese symbol was selected (nothing else would even show), all the missing text appeared but it was in Chinese writing.

Help...

---

### Post by zevans on 2009-03-31
> **crjackson said:**
> Okay, I think it's a font issue. How do I re-install all my fonts?


Lazy way is to look in synaptic for all the *-fonts-* packages you have and mark them all for reinstall.

If something works as root and not as a normal user that's a classic sign that there's a permissions problem somewhere...

BTW Konqueror for me won't work with Outlook Web Access pages - get my Inbox fine but when then I click to read a message, the pane goes blank. Facebook's alright though.

---

### Post by crjackson on 2009-03-31
> **zevans said:**
> Lazy way is to look in synaptic for all the *-fonts-* packages you have and mark them all for reinstall.

If something works as root and not as a normal user that's a classic sign that there's a permissions problem somewhere...

BTW Konqueror for me won't work with Outlook Web Access pages - get my Inbox fine but when then I click to read a message, the pane goes blank. Facebook's alright though.

GOOD CATCH! Permissions WAS the issue and it's working now.

I reset the permissions on the fonts folder recursively and now it's working fine.

Thanks...

---

