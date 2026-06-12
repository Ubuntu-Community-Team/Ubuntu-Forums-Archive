---
title: "Gutsy Problems with Compiz"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by oneadvent on 2007-10-20
Ok, thats it. I give up. Someone smarter than me is gonna have to help now...

Heres whats wrong:

1. I went through gconf -editor to put the icons I want on the desktop, and to change the menu icon, but neither of them are done. (And yes I went back and double checked I had not lost my mind and un-checked the boxes.

2. Hibernate and resume don't work right. I can go to Hibernate and it goes right down, but when I try and come back up, after I put in my password, it doesn't work. (With Compiz running.) If I do not have Compiz working, it works great, but then when I try and re-enable it, it freezes it up again.

3. The icon is not there for Compiz even after I start it with fusion-icon command.

I just installed Gutsy Gibbon. Every one of these things worked with Feisty and Beryl.

Anyone that has any ideas, please let me know!

Thanks.

---

### Post by oneadvent on 2007-10-20
Ok, heres the update that I know everyone is sitting on the edge of there seat for. 

I changed the gconf-editor again and the icons went to the desktop. However, I noticed something:

I can't change any icons on the panel. I even killed it and restarted it.

Anyone got any ideas?

Thanks for hanging on my every word!

---

### Post by oneadvent on 2007-10-20
As I officially give up I filed a bug:

Bug #154750

---

### Post by oneadvent on 2007-10-20
Woohoo! I figured another part out. The panel was set to 24 pix and it if it is anything less than 26 pix the icon wont show up. 

I set it to 28 pix (I dunno why, so don't ask) and now the icon is there. Also I must have been in the wrong place in the gconf-editor because I went back in and tried again, and now it is good to go.

So now I am down to a problem with Compiz and Hibernating, but that is all workable. It is down to a little editing to fix that I'm sure...I read a thread on how to stop and start it on a Hibernation, but that wont work because if I do get it back up after Hibernation (by using metacity) and turn it back on, it still freezes up and just shows me the wallpaper.

If anyone is having a similar problem let me know if you have any ideas. Past that everything is up and running again. (I think)

Whew I should write a book....

---

