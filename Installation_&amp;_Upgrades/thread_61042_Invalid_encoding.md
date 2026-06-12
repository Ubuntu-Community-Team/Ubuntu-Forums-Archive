---
title: "Invalid encoding"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by DarkRider on 2005-08-30
Hello,
After installation Ubuntu does not recognize my old openoffice documents. In the name of the document all special characters have been replaced by ? (e.g. Lääke = L??ke (invalid encoding) ). If I try to rename document it is not usable. If I try to open it I get following error msg: Error loading dodiment file:/// etc. document doesnt exist.

I have Installed Language packs for EN, FI (Finnish).

Any help highly appreciated !

---

### Post by burlap on 2005-08-30
Try creating additional locale with finnish iso encoding (Hoary defaults to UTF). 
```
sudo dpkg-reconfigure locales
```
After creating the new locale, log out and change session language (You should have something like Finnish (ISO) and Finnish (UTF)). 

At least it worked for me with Polish...

---

### Post by DarkRider on 2005-08-30
Edit: Figured out that sudo can be run in terminal. Then I selected fi_FI ISO-8859-1, next it is asking about default locale. And I selected none, Logged out and selected new language and I got following error message: Language fi_FI does not exist. Using system default. 
What to do now ?

---

### Post by burlap on 2005-08-30
So, I have forgotten about choosing default language...

Run again
```
sudo dpkg-reconfigure locales
```

Select fi_FI (not UTF) as default. 

Log out and change language again. 

To see all your locales, in a terminal (non-root - do not use root terminal unless you REALLY need to, sudo will do for most purposes) run: 
```
locale -a
```

What interface lanuage do you normally have? If it is English you should also check for Finnish language packs in Synaptic (System --> Administration --> Synaptic Package Manager) - find "language" or "fi" in package names or "Finnish" in package names and descriptions. 

I remember it was mess with languages after upgrading from Warty... Only the second update (on a second computer) was better, when I already knew to install language packs...

And: I can't guarantee it will work. For me and Polish switching from UTF back to iso made it better, but still there are files that do not open (in some apps): the only thing left is to rename them.

---

### Post by DarkRider on 2005-08-30
Done all above steps but same problem still exists.  locale -a gives:
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB
en_GB.iso88591
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
fi_FI
fi_FI@euro
fi_FI.iso88591
fi_FI.iso885915@euro
fi_FI.utf8
finnish
POSIX
sv_FI
sv_FI@euro
sv_FI.iso88591
sv_FI.iso885915@euro
sv_FI.utf8
sv_SE.utf8

I have defaulted sv_FI.iso885915@euro and also checked that FI language packages are installed from Synaptic Packetr MGr. 

I am using normally EN language.

No errors anymore when loggin in.

Next ?

---

### Post by burlap on 2005-08-30
Running out of ideas...

One of the most frustrating problems: worked fine under Warty is broke under Hoary (and you may substitute those with any distros).

Are those files located on fat/ntfs or in other words windows drives?

For expample, I have this problem: I get a file by email, it includes Polish letters. It works fine under linux. I save it to a floppy (fat filesystem). Under windows it does not work... 

Also, the app that has most problems is openoffice (the same file is opened fine in abiword, while openoffice can't handle it). The problem, as far as I know, is that it does not handle UTF-8 encoded filenames properly (or it seems so). Openoffice 1.9.121 opens those files without problems (well, it is still some riks to use it: you could try downloading breezy live cd and checking if openoffice there has the same problems. Of course, breezy is coming only in October).

I am sorry, I coulnd't really help...

---

### Post by DarkRider on 2005-08-30
Actually you helped a lot !  :grin: 

So now if I create new file in OpenOffice with scandic chars in filename it works correctly. It does not work correctly with OpenOffice documents created earlier with windows version of Open Office (I burend them to CD before installed UBUNTU). Is there anything I can do to save those docs ?

---

### Post by burlap on 2005-08-30
[quote=DarkRider]Actually you helped a lot ![/quote]
I'm really happy. 

[quote=DarkRider]Is there anything I can do to save those docs ?[/quote]
1. Check the files under windows. If they work, rename, burn again. (Many disadvantages including using windows).
2. Check if mounting with specific encoding works. I have never tried, try searching the forums (starting [there](http://www.ubuntuforums.org/search.php?searchid=1560154))
3. Try recoding filenames instead of renaming (install "recode" and "recode-doc" packages and use maunal/ doc files). Again, never tried myself (renaming works so I don't bother).

Hint: to use a manual, run in the terminal:
```
man recode
```
(You can substitue "recode" with any command). Man pages are also included in gnome help system, but I don't know if it's complete...

Good luck!

---

