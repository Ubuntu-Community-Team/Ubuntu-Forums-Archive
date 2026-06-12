---
title: "Problems after system upgrade in XUBUNTU"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by Karthik Murugan on 2013-02-19
I did the following in my computer :-
  [INDENT]   $sudo apt-get update
      $sudo apt-get upgrade
 [/INDENT]  After restarting the computer, I see the visuals of my Desktop  changed. Also, there is not even single folder icon in any drive. **Only the name of folder is being displayed and there is no icon**. In the panel, certain utilities have lost thier icons too.




  screenshot : [IMG]http://i.imgur.com/VjWFGiX.png[/IMG]


[URL="http://i.imgur.com/VjWFGiX.png"]
[/URL]
  In a window,the folder icons are not available.
  Also **in the left,the thumbnails of Desktop,Filesystem,Documents,Music,etc are not displayed**. 
  **In the right(panel), several utilities have the same default icon**(such as the terminal emulator,trash,Web browser,Mail Reader,Settings Manager)
  The thing is only the icons are not visible, but i can double-click  and open the folders. How can I get back those icons(like the default  yellow color folder icon) because it is annoying to see only the names  of folder displayed without any icon
  I **did only the upgrade thing i mentioned above, nothing else**.(did not tweak anything)

---

### Post by dino99 on 2013-02-20
its up to you to change the View settings from the menu  ;)

---

### Post by Hylas de Niall on 2013-02-20
12-04 or 12-10?

I updated my 12-04 last night and there were two instances when i was asked if i wanted to update or keep certain files. I opted to keep the originals as i'v read on here that it's the safest option. I had no problems. I believe the files were config ones.
If you opted to update them it might explain what happened to your setup.

HTH

---

### Post by s1baker on 2013-02-20
Could be your config files got scrambled. Happens to me all the time.

Try to logout,  ( ctrl+alt+f2 )
then in the console: 
```

rm -rf .cache/sessions
```


then ctrl+alt+f1 ( or ctrl+alt+f7, depending on distribution ) and login again.

I have to do this often.

---

