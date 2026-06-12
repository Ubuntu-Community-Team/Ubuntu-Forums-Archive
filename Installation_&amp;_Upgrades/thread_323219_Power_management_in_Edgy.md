---
title: "Power management in Edgy"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by SnTholiday on 2006-12-21
Ever since the upgrade to Edgy I have had problems with power management and the
screensaver. The screensaver I don't really care about, but I do like the system to put the
monitor to sleep but this is not working. I know I can turn the monitor off myself, but sometimes I walk away from the computer and forget. Does anyone else have this problem or know what might be causing it? Both screesaver and power management worked fine in Dapper (except suspend/hibernate, this never worked). 

Thanks.

---

### Post by wpshooter on 2006-12-21
Are you saying that you want to screen to blank after a certain period of inactivity and it doesn't or are you saying that it goes blank in spite of the fact that you have the setting on NEVER and you don't want it to ?

---

### Post by SnTholiday on 2006-12-21
What happens is, I have the screensaver turned off. Under power managment I have the monitor set to go to sleep say after 30 mins. The problem is the monitor never turns off. The system should shut down the video to the monitor within the time I specify, but it doesn't. 

BTW, I am using gnome, not kde.

---

### Post by wpshooter on 2006-12-21
Well let me tell you what to try, see my next post.  Give me a few minutes to type it.

---

### Post by SnTholiday on 2006-12-21
Thanks.

---

### Post by wpshooter on 2006-12-21
First make sure that the automatic saving of SESSIONS changes IS MARKED in the sessions section.

Then go into the screen saver and turn it ON and set the slider to 2 minutes.

Then go into the power management and set the slider to 3 minutes.

Then let the computer set inactive and see if it will go into screensaver after 2 minutes and then wait for about another minute or so and see if the screen goes blank.

If the above happens then don't change anything at this point just restart/reboot the computer.

When you get back up to the desktop go into the screen saver and turn the screen saver to OFF but do NOT move the slider from the 2 minutes setting.

Then let the computer set idle for about 3 minutes and see if it will go blank.

If it does, then restart again and when you get back up to the desktop give it several trys to see if the power management functions after 3 mintues on inactivity.  Then set your slider to 30 minutes and you should be good to go.  Make sure you leave the slider in the screen saver on the 2 minutes mark and do NOT move it.

Good luck.

---

### Post by SnTholiday on 2006-12-21
Thanks a lot, I'll try it tonight and let you know.

---

### Post by SnTholiday on 2006-12-22
> First make sure that the automatic saving of SESSIONS changes IS MARKED in the sessions section.

Then go into the screen saver and turn it ON and set the slider to 2 minutes.

Then go into the power management and set the slider to 3 minutes.

Then let the computer set inactive and see if it will go into screensaver after 2 minutes and then wait for about another minute or so and see if the screen goes blank.

If the above happens then don't change anything at this point just restart/reboot the computer.

When you get back up to the desktop go into the screen saver and turn the screen saver to OFF but do NOT move the slider from the 2 minutes setting.

Then let the computer set idle for about 3 minutes and see if it will go blank.

If it does, then restart again and when you get back up to the desktop give it several trys to see if the power management functions after 3 mintues on inactivity. Then set your slider to 30 minutes and you should be good to go. Make sure you leave the slider in the screen saver on the 2 minutes mark and do NOT move it.

I did what you suggested last night and it seems to be working. The only thing I did differently is I decided to use the screensaver instead of turning it off (blank screen only). The automatic saving of sessions was NOT marked, so I marked it. This was probably the problem. 

Thanks for your help.

---

