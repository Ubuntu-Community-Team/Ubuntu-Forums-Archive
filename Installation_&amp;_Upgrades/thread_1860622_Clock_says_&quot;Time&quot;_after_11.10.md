---
title: "Clock says &quot;Time&quot; after 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2011-10-14
I just upgraded to 11.10 and over in the place in the menu bar where the time should be displayed, it just says "Time". If I click on that, I can choose Time & Date Settings... and that dialog shows the correct time. Also, in the "Clock" tab, "Show a clock in the menubar" is checked. So what's wrong?

---

### Post by shochatd on 2011-10-15
No solution yet. I just wanted to add that I tried creating a brand new account to see if the problem was caused by faulty migration of home directory files. But in the new account, it still just says "Time" where the actual time should be. I take it nobody else is having this problem?
-- David

---

### Post by NeilInCanadia on 2011-10-15
I have precisely the same problem.

---

### Post by shochatd on 2011-10-15
Do you have an indicator menu for switching keyboard layouts? I do, and I was wondering if there might be some conflict between it and the rest of the indicator stuff (not enough room?). For me, it's the left-most indicator menu, just to the left of the one that looks like an envelope (for "messaging" I guess).

---

### Post by NeilInCanadia on 2011-10-15
I do, but I doubt that's the problem (and I think it was there in 11.4 for me).

---

### Post by NeilInCanadia on 2011-10-15
I'm also unable to change some of the time settings (the "unlock" button to switch to root is greyed out). Might be related?

---

### Post by shochatd on 2011-10-15
Where are the time settings you are referring to? The only dialog I've found has no unlock button (it's user-specific). I'm still suspicious of the keyboard layout switcher. After all, you and I are the only ones in this forum reporting the problem and we both have that. And I'm guessing that the majority of Ubuntu users do not. I was trying to figure out how to disable it when I saw your post.

---

### Post by shochatd on 2011-10-15
I take it back about the keyboard-switching indicator menu. That is user-specifc: I tried logging in as another user and that menu was not there. But the problem of the indicator (menu bar) clock just saying "Time" WAS there.

---

### Post by ebelhaire on 2011-10-16
The update suppresses the file /etc/timezone and this is at the origin of the problem of "Time" display. The file can be restored with the command : [INDENT]sudo dpkg-reconfigure tzdata
[/INDENT]It solved the problem for me. 

Eric

---

### Post by NeilInCanadia on 2011-10-16
Great, fixed it for me too! Thanks.

---

### Post by shochatd on 2011-10-16
Bingo! That solved the problem. Marked this thread Solved.
Thank you!
-- David

---

### Post by shochatd on 2011-10-16
I'm just curious about one thing: How is it that through all this the "Time & Date Settings" dialog displayed the correct time, as did xclock? Both apparently knew my correct time zone.

---

