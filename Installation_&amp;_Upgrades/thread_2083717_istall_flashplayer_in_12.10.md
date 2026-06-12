---
title: "istall flashplayer in 12.10"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by foddle on 2012-11-13
Have been trying to install flashplayer in 12.10 and not having alot of luck. i would thank any help i can get. i am new and trying to get things going.

---

### Post by darkod on 2012-11-13
I use one very simple procedure that some people don't like but it works 100% for me. Don't install anything from repository, Software Centre, etc, ignore that.

If you already tried I suggest you remove the software you installed (but only that one).

Go to the Adobe website and download the linux version for flash player. Unpack the .tar.gz file somewhere in your Home folder for example.

From those files, you will need just the one called something like libflashplayer.so. Open your Home folder, hit Ctrl + H to show the hidden folders, and open the .mozilla folder. In there I think there should be firefox folder. Open it, and if the plugins folder doesn't exist inside, create it.

Then simply copy the libflashplayer.so into .mozilla/firefox/plugins, restart Firefox if it was open during the copy, and it should work fine.

That way you can also control which version flash player you have since it will not update automatically. New versions often have issues, and you can copy the new version libflashplayer.so when you are sure it's working.
This way it's also easy to "downgrade" if you keep in one folder all the older libflashplayer.so versions. Simply copy the older version in the plugins folder, and you have the older version of flash right away.

---

### Post by foddle on 2012-11-20
took me awhile to get around to this. If you can make it more simple it would probably help. i did not have alot of luck and its probably due to lack of knowing. have taken everything out and will try again.

---

