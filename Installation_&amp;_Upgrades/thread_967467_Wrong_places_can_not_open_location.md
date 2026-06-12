---
title: "Wrong places can not open location"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by snappy46 on 2008-11-02
Hi,

I had this weird problems since I upgraded to 8.10. On the places menu all my shortcut places (Home folder, Desktop, pictures, documents, pictures etc.. won't open correctly.  Somehow all those shortcut try to lauch an application that has been removed on my system as opposed to the nautilus file manager.

I receive the following error: Could not open location 'file:///home/xxxxx/Documents' Failed to execute child process "lindvd" (No such file or directory).

Obviously when I click on the places menu and any of those shortcut for some strange reason it want to lauch the program "lindvd" which is no longer on my computer instead of the nautilus file manager.

The funny thing is that if I click on the my computer shortcut in the places menu it work fine and launch nautilus and open the my computer folder as it should. Also if I have nautilus open and click any of those shortcut (Desktop, Home folder, documents etc...) on the left bar it also open properly.

This is what I tried so far:
1) I open nautilus and deleted the folders on the left bar that I could (documents, pictures, videos, Music) I was not able to remove the Desktop or Home folder in the left bar of nautilus. This remove those shortcut from the places menu on top.  I then recreated them using nautilus but I still get the same result when I use the places menu.

2) I decided to delete them and not to worry about them but every time I log back in those shortcut are back in the places menu and of course they still point to the wrong application.

Is there a configuration file that I can edit manually to correct the shortcut.  Any help will be appreciated 

Thanks.

---

### Post by scragar on 2008-11-02
[http://ubuntuforums.org/showthread.php?t=963277](http://ubuntuforums.org/showthread.php?t=963277) <-- this question has already been answered.

Let me know how you go anyway(you can do it on the command line using the 7th post, but I think that requires you to log out and in again to take effect(I could be wrong, I've never tried it)).

---

### Post by snappy46 on 2008-11-02
Thanks a lot!

That was almost too easy I feel pretty stupid now! Apparently I can not perform a proper search either.

Have a good day.

---

