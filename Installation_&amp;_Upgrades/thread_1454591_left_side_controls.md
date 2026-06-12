---
title: "left side controls"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by mikecanada on 2010-04-14
I,ve installed Ubuntu 10.4 alapha one on three computers, on one desktop the window control buttons came out on the top left.

On the other desktop and lap top the window control buttons are where they always were on the top right.

Is there a way to switch the left side controls over to the right?

                        Thanks Mike

---

### Post by xXxBlender3DxXx on 2010-04-14
Try to search Google before you post a new thread ;)

Here is a tutorial to look at: [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")

It may be a bit time consuming, so instead you could try in Terminal:
```
sudo gconftool-2 --set /apps/metacity/general/button_layout --type string “menu:minimize,maximize,close,spacer”
```

---

### Post by Iowan on 2010-04-14
[Here]("http://ubuntuforums.org/showthread.php?t=1423076") is a thread you can check...

---

### Post by Sonsum on 2010-04-14
Here's another thread with links on the Ubuntu Tweak method (it's really easy)

[http://ubuntuforums.org/showthread.php?t=1454598](http://ubuntuforums.org/showthread.php?t=1454598)

---

### Post by bigsmitty64 on 2010-04-15
I think I can help you here,
open terminal, type, "gconf-editor" .  when it opens expand the "apps" folder, then scroll down to "metacity" expand that and click on "general. now in the right hand pane, look at the 8th line down. You can rearange the buttons there. Just move the :  to the other side. Plus you can basically rearange the buttons however you want!   Hope this helps.
Smitty

---

### Post by beta.tester on 2010-04-15
> **mikecanada said:**
> I,ve installed Ubuntu 10.4 alapha one on three computers, on one desktop the window control buttons came out on the top left.

On the other desktop and lap top the window control buttons are where they always were on the top right.

Is there a way to switch the left side controls over to the right?

                        Thanks Mike

Hi Mike

I use a utility called Ubuntu Tweak! It is great I have found and the latest version 5.3.1-lucid has an option where you determine where you want the buttons ie left or right hand side. It is simply a matter of ticking either left or right and it works :)

Hope this helps:

Keep on Ubuntuing   john

ps the site is:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by mikecanada on 2010-04-15
To all the great Ubuntu people who take the time to help over and over.                      Thanks

I just got Tweak and fix the controls,odd how the first install went left and the other two were normal.

                  The Best Forum Period, Cheers Mike

---

