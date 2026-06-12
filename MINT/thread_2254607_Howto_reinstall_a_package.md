---
title: "Howto reinstall a package"
date: 2014-11-28
forum: MINT
---

### Post by birddawg on 2014-11-28
Hi all,
I'm a newbie so please be patient with me.  I have MInt running and everything is working swimmingly with one exception.  I installed privoxy, edited a config file. In the process,  accidentally removed a file and i dont know which.  So, via the software manager, I removed privoxy.  It removed everything but some config files and templates directory.  I reinstalled it, or so I thought, but nothing else gets added to that directory.  
Whats going on here? What am I doing wrong?

---

### Post by howefield on 2014-11-28
Thread moved.

---

### Post by rewyllys on 2014-11-28
My recommendation is to use the Synaptic Package Manager. 

 Open the SPM and have it search for "privoxy".  When privoxy has been found, choose "Mark for Complete Removal" and then Apply your choice.

When the SPM has finished "completely removing" privoxy, choose privoxy again, but this time choose "Mark for Installation", and then Apply your choice.

---

### Post by deadflowr on 2014-11-28
How were you editing the file?
Did you open the file manager as root and then edit the file, and also delete the other?
If so, it's possible the file still exists on the system, but is now inside root's home folder's hidden trash folder.
The system should have a folder like /usr, called /root.
You can only access that folder if you are running root, so get root to open.
Then the trick is to enable the file manager to show hidden files/folders.
(Typically ctrl +h works, but I don't know which file manager, or mint variant you are using.)
Then you should see a folder for .local, then share, and Trash inside it.
It should, if anything is in there, list Info, Files, and Expunged.
Look in Files.
If this what happened, as I am only speculating, you can copy/move the file back into it's original folder, where ever that may be.

Again this is only speculation, but seeing as to the fact you deleted one file while working on another, makes seem likely you had the file manager open.
Of course it is also speculation that the files needed to be edited with root...
I would think that if you simply had deleted a normal file, one that you were editing from within your home folder, that you would have looked in your trash folder to retrieve it.

Hope it helps.

---

### Post by birddawg on 2014-11-29
I used the SPM and did exactly as you suggested.  Comes back the same.  A "init.d" directory and the files beneath it are are one of the things I know is missing.

---

### Post by birddawg on 2014-11-30
Thanks everyone.  I appreciate your help.  Like I said at the top of the post, I'm a newbie.  The file structure threw me.  The init.d is in the usr dir.  Anyhow, I got privoxy installed and configured and running the way it should.  Now, ad free web surfing.
Cheers

---

### Post by rewyllys on 2014-12-01
> **birddawg said:**
> Thanks everyone.  I appreciate your help.  Like I said at the top of the post, I'm a newbie.  The file structure threw me.  The init.d is in the usr dir.  Anyhow, I got privoxy installed and configured and running the way it should.  Now, ad free web surfing.
Cheers
Congratulations on figuring out the problem!

---

