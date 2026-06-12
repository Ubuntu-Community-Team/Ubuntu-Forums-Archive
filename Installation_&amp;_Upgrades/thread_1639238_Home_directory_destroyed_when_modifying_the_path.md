---
title: "Home directory destroyed when modifying the path"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by Barbidoux on 2010-12-06
Hello

I just had a big problem :

I installed Maverick in place of Lynx (not an upgrade because Lucid Lynx did not start anymore and I have the home directory on a different partition).

When ready, I go on the user and modify the path to the Home directory.

Good surprise : it can automatically change the owner of the files.

Click OK and then it ask if I want to replace new files with old files or old files with new files !!!
 
What the heck ? I don't want to replace anything, just modify the path to home directory !

Well, let's think : I just installed Maverick with a lot of new user files (which I don't care) and I have all my old files in the user partition. Well, then I have to replace the new files (created on sunday) with my old files (the newer were modified on saturday). So let's go fo replace the new files with the old one.

Well, that was the bad answer : Ubuntu just destroyed more than 100 Gb to replace it with an empty profile ! And to be sure I can not recover anything, it removed the user directory (not only emptying it) and re-created it. Even Ext3grep see nothing in this directory. Last backup was from July (we're in december) and the backup was the next step after this redirection.

Please find the one who put an horrible command just behind something that looked like a path redirection and tell him my story. I wish he will dream of monster every nights until he correct this trap !

And if someone have a good idea to return to saturday's state, you're welcome !

---

### Post by Barbidoux on 2010-12-09
Something I forgot :

After destroying my home directory, the current path in the user profile is still the original one.

Resume
1) You ask for a home path modification
2) It ask some not very clear questions
3) It destroy the data in the new path you gave
4) It still use his own original path (with nothing in it, the user were created in the OS installation 10 minutes ago)

Do someone can explain the good use of this functionnality ?

About my data, the great utility ext3grep found lot of files in Lost+Found directory. I just have to sort them because they are all in the same directory (about 89'000 files).

---

